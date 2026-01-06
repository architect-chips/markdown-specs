

# PAC it up: Towards Pointer Integrity using ARM Pointer Authentication\*

Hans Liljestrånd

Aalto University, Finland  
Huawei Technologies Oy, Finland  
hans.liljestrånd@aalto.fi

Thomas Nyman

Aalto University, Finland  
thomas.nyman@aalto.fi

Kui Wang

Huawei Technologies Oy, Finland  
Tampere University of Technology, Finland  
wang.kuil@huawei.com

Carlos Chinea Perez

Huawei Technologies Oy, Finland  
carlos.chinea.perez@huawei.com

Jan-Erik Ekberg

Huawei Technologies Oy, Finland  
Aalto University, Finland  
jan.erik.ekberg@huawei.com

N. Asokan

Aalto University, Finland  
asokan@acm.org

## Abstract

Run-time attacks against programs written in memory-unsafe programming languages (e.g., C and C++) remain a prominent threat against computer systems. The prevalence of techniques like return-oriented programming (ROP) in attacking real-world systems has prompted major processor manufacturers to design hardware-based countermeasures against specific classes of run-time attacks. An example is the recently added support for *pointer authentication* (PA) in the ARMv8-A processor architecture, commonly used in devices like smartphones. PA is a low-cost technique to authenticate pointers so as to resist memory vulnerabilities. It has been shown to enable practical protection against memory vulnerabilities that corrupt return addresses or function pointers. However, so far, PA has received very little attention as a general purpose protection mechanism to harden software against various classes of memory attacks.

In this paper, we use PA to build novel defenses against various classes of run-time attacks, including the first PA-based mechanism for data pointer integrity. We present PARTS, an instrumentation framework that integrates our PA-based defenses into the LLVM compiler and the GNU/Linux operating system and show, via systematic evaluation, that PARTS provides better protection than current solutions at a reasonable performance overhead.

## 1 Introduction

Memory corruption vulnerabilities, such as buffer overflows, continue to be a prominent threat against modern software applications written in memory-unsafe programming languages, like C and C++. These vulnerabilities can be exploited to overwrite data in program memory. By overwriting control data, such as code pointers and return addresses, attackers can redirect execution to attacker-chosen locations. *Return-oriented programming* (ROP) [35] is a well known technique that allows the attacker to leverage

corrupted control-data and pre-existing code sequences to construct powerful (Turing-complete) attacks without the need to inject code into the victim program. By overwriting non-control data, such as variables used for decision making, attackers can also influence program behavior without breaking the program’s *control-flow integrity* (CFI) [1]. Such attacks can cause the program to leak sensitive data or escalate attacker privileges. Recent work has shown that non-control-data attacks can also be generalized to achieve Turing-completeness. Such *data-oriented programming* (DOP) attacks [16] are difficult to defend against, and are an appealing attack technique for future run-time exploitation.

Software defenses against run-time attacks can offer strong security guarantees, but their usefulness is limited by high performance overhead, or requiring significant changes to system software architecture. Consequently, deployed solutions (e.g., Microsoft EMET [26]) trade off security for performance. Various hardware-assisted defenses in the research literature [15, 42, 41, 14, 38, 40, 28, 32] can drastically improve the efficiency of attack detection, but the majority of such defenses are unlikely to ever be deployed as they require invasive changes to the underlying processor architecture. However, the prevalence of advanced attack techniques (e.g., ROP) in modern run-time exploitation has prompted major processor vendors to integrate security primitives into their processor designs to thwart specific attacks efficiently [17, 29, 31]. Recent additions to the ARMv8-A architecture [3] include new instructions for *pointer authentication* (PA). PA uses cryptographic message authentication codes (MACs), referred to as *pointer authentication codes* (PACs), to protect the integrity of pointers. However, PA is vulnerable to *pointer reuse* attacks where an authenticated pointer is substituted with another [31]. Practical PA-based defenses must minimize the scope of such substitution.

**Goals and Contributions** In this work, we further the security analysis of ARMv8-A PA by categorizing pointer

Extended version of this article is available as a technical report [24].

reuse attacks, and show that PA enables practical defenses against several classes of run-time attacks. We propose an enhanced scheme for *pointer signing* that enforces *pointer integrity* for all code and data pointers. We also propose *run-time type safety* which constrains pointer substitution attacks by ensuring the pointer is of the correct type. Pointer signing and run-time type safety are effective against both control-flow and data-oriented attacks. Finally, we design and implement *Pointer Authentication Run-Time Safety* (PARTS), a compiler instrumentation framework that leverages PA to realize our proposed defenses. We evaluate the security and practicality of PARTS to demonstrate its effectiveness against memory corruption attacks. Our main contributions are:

- *Analysis*: A categorization and analysis of pointer reuse and other attacks against ARMv8-A pointer authentication (Section 3).
- *Design*: A scheme for using *pointer integrity* to systematically defend against control-flow and data-oriented attacks, and *run-time type safety*, a scheme for guaranteeing safety for data and code pointers at run-time (Section 5).
- *Implementation*: PARTS, a compiler instrumentation framework that uses PA to realize data pointer, code pointer, and return address signing (Section 6).
- *Evaluation*: Systematic analysis of PARTS showing that it has a reasonable performance overhead (< 0.5% average overhead for code-pointer and return address signing, 19.5% average overhead for data-pointer signing in nbench-byte (Section 7)) and provides better security guarantees than fully-precise static CFI (9).

We make the source code of PARTS publicly available at <https://github.com/pointer-authentication>.

## 2 Background

### 2.1 Run-time attacks

Programs written in memory-unsafe languages are prone to memory errors like buffer-overflows, use-after-free errors and format string vulnerabilities [39]. Traditional approaches for exploiting such errors by corrupting program code have been rendered largely ineffective by the widespread deployment of measures like data execution prevention (DEP). This has given rise to two new attack classes: *control-flow attacks* and *data-oriented attacks* [11].

#### 2.1.1 Control-flow attacks (on ARM)

Control-flow attacks exploit memory errors to hijack program execution by overwriting code pointers (function return addresses or function pointers). Corrupting a code pointer can cause a control-flow transfer to anywhere in executable memory. Corrupting the return address of a function can be

used for ROP attacks, which are feasible on several architectures, including ARM [19].

ARM processors, similar to other RISC processor designs, have a dedicated Link Register (LR) that stores the return address. LR is typically set during a function call by the Branch with Link (b1) instruction. An attacker cannot directly influence the value of LR, as it is unlikely for a program to contain instructions for directly modifying it. However, nested function calls require the return address of a function to be stored on the stack before the next function call replaces the LR value. While the return address is stored on the stack, an attacker can use a memory error to modify it to subsequently redirect the control flow on function return. On both x86 and ARM, it is possible to perform ROP attacks without the use of return instructions. Such attacks are collectively referred to as *jump-oriented programming* (JOP) [9].

Control-flow integrity (CFI) [1] is a prominent defense technique against control-flow attacks. The goal of CFI is to allow all the control flows present in a program's control-flow graph (CFG), while rejecting other flows. Widely deployed CFI solutions are less precise than state-of-the-art solutions presented in scientific literature.

#### 2.1.2 Data-oriented attacks

In contrast to control-flow attacks, *data-oriented attacks* can influence program behavior without the need to modify code pointers. Instead, they corrupt variables that influence the program's decision making, or leak sensitive information from program memory. Such attacks are called *non-control-data attacks*. Chen et al [11] demonstrated a variety of non-control-data attacks for forging user credentials, changing security critical configuration parameters, bypassing security checks, and escalating privileges. Recent work on DOP [16] showed that non-control-data corruption can also enable expressive attacks without compromising control-flow integrity. DOP may compromise the input of individual program operations and chain together a chosen sequence of operations to achieve the intended functionality.

A data-oriented attack can in principle corrupt arbitrary program objects, but corrupting data pointers is often the preferred attack vector [12]. In Chen et al.'s attack against the GHTTPD web server [11], a stack buffer overflow is used to corrupt a data pointer used in input string validation in order to bypass security checks on the input under the attacker's control. Data pointers are also routinely corrupted in heap exploitation. For instance, the "*House of Spirit*" attack on Glibc<sup>1</sup>, involves corrupting a pointer returned by malloc() to trick subsequent malloc() calls into returning attacker controlled memory chunks. The DOP attacks in [16] also involve the corruption of pointers as a means to control which data is processed by vulnerable code.

<sup>1</sup>Team Shellphish repository of educational heap exploitation techniques: <https://github.com/shellphish/how2heap>

![Figure 1: Diagram illustrating the creation of a Pointer Authentication Code (PAC). The top diagram shows a Pointer structure divided into a pacia pointer, modifier, and address. The bottom diagram shows the resulting PAC structure, where the PAC is calculated using the PA-key and a keyed MAC over the pointer address and modifier.](ad04aa6cb9e7fb36bb7a91e817e2d314_img.jpg)

Figure 1: Diagram illustrating the creation of a Pointer Authentication Code (PAC). The top diagram shows a Pointer structure divided into a pacia pointer, modifier, and address. The bottom diagram shows the resulting PAC structure, where the PAC is calculated using the PA-key and a keyed MAC over the pointer address and modifier.

Figure 1: The PAC is created using key-specific PA instructions (*pacia*) and is a keyed MAC calculated over the pointer address and a modifier.

### 2.2 ARM Pointer Authentication

ARMv8.3-A includes a new feature called *pointer authentication* (PA). PA is intended for checking the integrity of pointers with minimal size and performance impact. It is available when the processor executes in 64-bit ARM state (AArch64). PA adds instructions for creating and authenticating *pointer authentication codes* (PACs). The PAC is a tweakable message authentication code (MAC) calculated over the pointer value and a 64-bit *modifier* as the tweak (Figure 1). Different combinations of key and modifier pairs allow domain separation among different classes of authenticated pointers. This prevents authenticated pointer values from being arbitrarily interchangeable with one another.

The idea of using of MACs to protect pointers at run-time is not new. *Cryptographic CFI* (CCFI) [25] uses MACs to protect control-flow data such as return addresses, function pointers, and vtable pointers. Unlike ARMv8-A PA, CCFI uses hardware-accelerated AES for speeding up MAC calculation. Run-time software checks are needed to compare the calculated MAC to a reference value. PA, on the other hand, uses either QARMA [5] or a manufacturer-specific MAC, and performs the MAC comparison in hardware.

64-bit ARM processors only use part of the 64-bit address space for virtual addresses (Figure 2). The PAC is stored in the remaining unused bits of the pointer. On a default AArch64 Linux kernel configuration with 39 bit addresses and without address tagging [3, D4.1.4], the PAC size is 24 bits. However, depending on the memory addressing scheme and whether address tagging is used, the size of the PAC is between 3 and 31 bits [31]. Security implications of the PAC size are discussed in Section 9.

PA provides five different keys for PAC generation: two for code pointers, two for data pointers, and one for generic use. The keys are stored in hardware registers configured to be accessible only from a higher privilege level: e.g., the kernel maintains the keys for a user space process, generating keys for each process at process `exec`. The keys remain constant throughout the process lifetime, whereas the modifier is given in an instruction-specific register operand on each PAC creation and authentication (i.e., MAC verification). Thus it can be used to describe the run-time context in

![Figure 2: Pointer layout on a 64-bit ARM. The 64-bit pointer is divided into 63 bits (PAC), 55 bits (PAC), va.size, and 0. The 63 bits are labeled 'tag / reserved' and 'upper/lower bit'. The 55 bits are labeled 'PAC' and 'reserved'. The va.size field is labeled 'va.size'. The 0 bit is labeled 'address'.](87658d45f2d2f009cbb9cd1079519cb5_img.jpg)

Figure 2: Pointer layout on a 64-bit ARM. The 64-bit pointer is divided into 63 bits (PAC), 55 bits (PAC), va.size, and 0. The 63 bits are labeled 'tag / reserved' and 'upper/lower bit'. The 55 bits are labeled 'PAC' and 'reserved'. The va.size field is labeled 'va.size'. The 0 bit is labeled 'address'.

Figure 2: Pointer layout on 64-bit ARM. The PAC is stored in the reserved bits, and its size depends on the used virtual address range. If pointer tagging is disabled, then the PAC can also extend to the tag bits.

which the pointer is created and used. The modifier value is not necessarily confidential (see Section 4) but ideally such that it 1) precisely describes the context of use in which the pointer is valid, and 2) cannot be influenced by the attacker.

PA is used by instrumenting code with PAC creation and authentication instructions. PA instruction mnemonics are generally prefixed either with *pac* or *aut* for creation and authentication, respectively, followed by two characters that select one of the data or code keys. For instance, the *pacia* instruction in Figure 1 will generate an authenticated pointer (pac) based on the instruction (1) A-key (a). Table 5 in Appendix C provides a list of PA instructions referred to in this paper. An authenticated pointer cannot be used directly, as the PAC embedded in the pointer value intentionally interferes with address translation. The corresponding PA authentication instruction (in this case, *autia*) removes the PAC from the pointer if authentication is successful, i.e., if the current pointer value, key and modifier for *autia* yields a PAC that matches the PAC embedded in the pointer. If authentication fails, the pointer is invalidated such that a dereference or call using the pointer will cause a memory translation fault. Dedicated PA instructions are encoded in NOP space; older processors without PA support will ignore them.

**Return address signing.** Qualcomm's return address signing scheme [31] is the first to make use of ARMv8-A PA. It was first introduced in Linaro's GCC toolchain, but has been supported by mainline GCC since version 7.0<sup>2</sup>. It thwarts attacks that manipulate function return addresses through stack corruption (see Section 2.1.1) by ensuring that the return address in LR always contains a PAC when written to or retrieved from memory. Listing 1 shows an example.

The instrumentation `addspaciap` (1) at beginning of the function prologue, before the LR value is stored on the stack. `paciap` adds a PAC tag using the current Stack Pointer (SP) value as the modifier. Before function return, `autiasp` (2) authenticates the pointer and either removes the PAC or invalidates the pointer. An alternative is to use the combined `autiasp+ret` instruction, `retaa`, but it is not backwards-compatible with older processors.

<sup>2</sup>GCC return address signing and PA support is based on patches provided by ARM, <https://github.com/gcc-mirror/gcc/commit/06f29de13f4f8f7da8a8c616108f4e14a1d19b2c8>

```
function :  
    paciasp ; ① create PAC  
    stp FP, LR, [SP, #0] ; store LR  
    ; ...  
    ldp FP, LR, [SP, #0] ; load LR  
    autiasp ; ② authenticate  
    ret ; return
```

Listing 1: Return address signing using PA. At function entry, `paciasp` is used to create a PAC in LR (①). The value is then authenticated with `autiasp` before return (②).

The PAC cryptographically binds the return address to the current SP value. It is valid only when authenticated using the same SP value as on PAC creation. The goal is to limit the validity of the PAC to the function invocation that created it, thus preventing reuse of authenticated return addresses.

## 3 Attacks on Pointer Authentication

PA prevents an attacker from injecting or forging pointer values. This effectively prevents any attack that relies on corrupting pointers, resisting even attackers with *arbitrary access to program memory*.

The modifier value used in computing a PAC can depend on both static (e.g., a hard-coded value) and dynamic (e.g., the SP) information. We assume that the program code itself is not confidential and that the attacker can learn how dynamic modifiers are generated and may infer their values.

PA also relies on the security of the underlying cryptographic primitives. In particular, an attacker may attempt to brute-force either the PA keys themselves, or individual PAC values. Sophisticated adversaries may even attempt cryptanalysis attacks based on known PAC values, or side-channels attacks against the hardware circuitry for computing PACs. The security of the QARMA block cipher has already been analyzed [43, 23]. We leave the scrutiny of the cryptographic building blocks outside the scope of this paper. Nevertheless, the limited PAC size means that guessing attacks are a potential concern. We discuss the feasibility of brute-forcing PACs in Section 7.2.4. Assuming proper precautions for the lifetime of PA keys (see Section 2.2), we do not consider guessing attacks the primary attack vector against PA. However, the following concerns for the security of PA-based defenses remain: 1) an attacker controlling the creation of PAC values, or 2) an attacker *reusing* previously authenticated pointers.

**Malicious PAC generation.** Attackers can potentially control PAC values in three ways, by controlling:

1. *the unauthenticated pointer value before PAC creation:* get an arbitrary authenticated pointer for any context with the same modifier and PA key.
2. *control the PA modifier value:* get an authenticated pointer for a context with the same PA key, but with an attacker-chosen modifier.
3. *both:* get arbitrary authenticated pointers for a context with attacker-chosen modifier, and the same PA key.

To prevent the attacker from generating arbitrary authenticated pointers, the program must not contain PA creation instructions with attacker controlled inputs. Also, a control-flow attack could be mounted by chaining together instruction sequences to prepare the PA operand registers with attacker controlled input and then jump to a PA instruction at another part of the program. This suggests that PA-based defenses *must provide, or be combined with, CFI guarantees* that prevent the use of individual authentication instructions as attacker-controlled gadgets.

**Reuse attacks.** The attacker can read authenticated pointers (including PAC values), and later reuse them to either:

- *rollback* an authenticated pointer to a previous value, or
- *substitute* an authenticated pointer with another using the same PA modifier.

For instance, in GCC's return address signing scheme (Section 2.2), the return address is bound to the location of the stack frame by using the current SP value as the PA modifier. However, the SP value is not necessarily unique to a specific function invocation. Consequently, an attacker can reuse the authenticated return addresses value from one function when a different vulnerable function executes with a matching SP value. Given that typical programs offer no guarantees on the uniqueness of SP values between different function invocations, this approach exposes a large attack surface for pointer reuse attacks. Therefore, a concern for any PA-based defense is partitioning authenticated pointers into distinct classes based on different <PA key, modifier> pairs.

Attackers can reuse only those pointers they can observe (as opposed all possible values a function pointer can take). Even with full read access to memory (and hence the ability to observe any pointer value that has been generated so far), attackers are still limited to authenticated pointer values the program has already generated.

## 4 Adversary Model and Requirements

### 4.1 Pointer Integrity

Kuznetsov et al. [21] introduced the idea of *code pointer integrity*: ensuring precise memory safety for all code pointers in a program. Since control-flow attacks depend on the

manipulation of code pointers, guaranteeing code pointer integrity will render *all* control-flow attacks impossible [21].

The notion of *pointer integrity* is generalizable to both code and data pointers. In Section 9.1, we provide a more rigorous definition of pointer integrity. Intuitively, pointer integrity aims to prevent unintentional changes to pointers while they remain in program memory so that the value of a pointer at the time it is “used” (e.g., dereferenced or loaded from memory) is the same as when it was created or stored on memory. In particular, integrity-protected pointers reference the intended target objects. As explained in Section 2.1, all control-flow attacks, all known DOP attacks and many other data-oriented attacks rely on the manipulation of vulnerable pointers. Consequently, ensuring pointer integrity will prevent these attacks.

### 4.2 Attacker Capabilities

To reason about how effectively PA defends against state-of-the-art attacks we assume attacker capabilities consistent with prior work on run-time attacks (Section 2.1). Our adversary model assumes a powerful attacker with arbitrary memory read and write capabilities restricted only by DEP. The attacker can thus read any program memory and write to non-code segments. We further assume that the attacker has no control of higher privilege levels, i.e., an attacker targeting a user space process cannot access the kernel or higher privilege levels. Specifically, we assume that the attacker cannot infer the PA keys, as they are in registers not directly readable from user space (Section 2.2). We discuss protection of kernel code using PA in Section 10. The attacker’s ability to read arbitrary memory precludes the use of randomization-based defenses that cannot withstand information disclosure (e.g., address space layout randomization [36] or software shadow-stacks [1]). PA was specifically designed to remain effective even when the entire memory layout of the victim process is known.

### 4.3 Goal and Requirements

Our goal is to thwart control-flow and data-oriented attacks by preventing the attacker from forging pointers used by a vulnerable program. We identify the following requirements that our solution should satisfy:

**R1** *Pointer Integrity*: Detect/prevent the use of corrupted code and data pointers.

**R2** *PA-attack resistance*: Resist attempts to control PAC generation, and pointer reuse attacks.

**R3** *Compatibility*: Allow protection of existing programs without interfering with their normal operation.

**R4** *Performance*: Minimize run-time and memory overhead and gracefully scale in relation to the number of protected pointers and dereferences/calls.

## 5 Design

To meet our requirements (Section 4.3) we must solve a number of challenges which we elaborate below.

### 5.1 Instrument program with PA instructions

To meet requirement **R1**, the program executable must be instrumented with PA instructions to create and authenticate PACs when needed. For this, we designed and implemented *Pointer Authentication Run-Time Safety* (PARTS), a compiler enhancement that emits PA instructions to sign pointers in memory as required. Specifically, it protects:

- return addresses;
- local, global and static pointers; and
- pointers in C structures.

Figure 3 shows the overall architecture of the PARTS-enhanced compiler. PARTS analyzes the compiler’s intermediate representation (IR) to identify any pointers used by the program and then emits PA instructions at points in the program where pointers are (a) created or stored in memory, and (b) loaded from memory or used.

### 5.2 Create PACs in statically allocated data

Programs may contain pointers which are initialized by the compiler, e.g., defined global variables. However, PAC values for authenticated pointers cannot be calculated before program execution, as PA keys are set only at program launch. Consequently, initialized pointers in the program’s data segment pose a challenge, as their values are normally initialized by the linker and loaded into memory separately. PARTS solves this problem by generating a custom initializer function for pointers requiring PACs. At run-time, the PARTS runtime library, PARTSlib, processes the relocated variables and invokes the generated initializer function to ensure that any defined pointers are furnished with a PAC.

### 5.3 Pointer compartmentalization

As described in Section 3 the attacker may attempt to reuse previously signed pointers. To meet requirement **R2** PARTS therefore limits the scope of such reuse attacks by compartmentalizing pointers in three different ways, as shown in Table 1.

*Code / Data Pointer Compartmentalization*: Recall from Section 2.2, that PA provides separate key sets for data and code pointers making it possible to limit reuse attacks.

Table 1: For code and data pointers PARTS uses a static PA modifier based on the pointer’s *ElementType* as defined by LLVM. Return address signing uses a 48-bit *function-id* and the 16 most-significant bits of the SP value.

|   | key                    | Modifier type | Modifier construction |                                       |
|---|------------------------|---------------|-----------------------|---------------------------------------|
| ① | Data pointer signing   | Data A        | static                | type-id = SHA3(ElementType)           |
| ② | Code pointer signing   | Instr A       | static                | type-id = SHA3(ElementType)           |
| ③ | Return address signing | Instr B       | dynamic + static      | SP   function-id = compile-time nonce |

*Run-time type safety*: Pointer compartmentalization, while effective, is coarse-grained. To address this, PARTS adds run-time type safety for data and code pointers. Run-time type safety records the pointer’s type by encoding it in the PA modifier. Then, it checks that pointer dereferences or indirect calls take place using a pointer with a recorded type that matches the type expected at the use site. PARTS assigns pointers a unique id, *type-id*, based on the pointer’s LLVM *ElementType* which depends on the pointed-to data, structure, or function signature. Two pointers are *compatible* (have the same *type-id*) if their *ElementType* is the same. PARTS uses a deterministic scheme, detailed in Section 6.1 and shown in Table 1, to calculate *type-ids* during compilation. This ensures that separate compilation units generate equivalent *type-ids* for compatible objects, and different *type-ids* for non-compatible ones.

*Improved Return Address Signing*: While run-time type safety could also be applied for return addresses, it would result in an over-permissive policy for backward edges. As described in Section 3, binding the authenticated return address to the current stack pointer value alone is insufficient because the stack pointer may not be unique to a specific function invocation. Instead, PARTS uses a combination of the current stack pointer value, and a compile-time nonce (*function-id*) ensuring that the authenticated return address cannot be reused across invocations of *different functions*, while the stack pointer values effectively compartmentalizes return addresses to callers with different stack layouts.

### 5.4 On-load data pointer authentication

Pointers with PACs can be authenticated either as they are loaded from memory, or immediately before they are used. We refer to these as *on-load* and *on-use* authentication, respectively. Data pointers are often dereferenced frequently without intervening function calls, i.e., they will not be cleared after use. This allows the compiler to optimize memory accesses such that, for instance, temporary values might never be written to memory. PARTS accommodates this behavior by only using on-load authentication for data pointers. The combined PA instructions can be used for on-use authentication of code pointers, which are typically loaded to a register, used once, and cleared. On-load authentication always uses the standalone authentication instructions. An

attacker could attempt to exploit either the standalone authentication or the separate pointer dereference by diverting control flow to either. However, as mentioned in Section 3, PA solutions must be combined with CFI guarantees, which prevent this type of attacks.

### 5.5 Handling pointer conversions

A data pointer to an object of a specific type may be converted to a pointer to a different object type. When run-time type safety is applied to authenticated pointers, special care must be taken to not interfere with legitimate pointer conversions to meet requirement [R3]. For instance, if a struct pointer is cast to a pointer to its first field, it will change the *type-id* and hence the expected PAC.

If the source and destination object types are compatible, no special consideration is needed. If not, PARTS must convert the authenticated pointer to the correct *type-id*. Because data pointer PAC creation and authentication is done at store/load, PARTS handles conversions by: (a) if loading the pointer from memory, validating and stripping the PAC using the *type-id* of the original object, and (b) on store, creating a new PAC using the destination object *type-id*.

A pointer to a function of one type may be converted to a pointer to a function of another type. However, the behavior when calling a function pointer cast to a non-compatible type is undefined [18][6.3.2.3§8]. Hence, PARTS does not need to convert the pointer’s PAC to match the destination function’s *type-id*. If the converted pointer is converted back, the result is expected to be the same as the original pointer [18][6.3.2.3§8]. PARTS satisfies this as it does not modify the pointer’s PAC.

## 6 Implementation

The PARTS compiler is based on LLVM 6.0 but modifies and adds new passes to the optimizer and the AArch64 backend (Figure 3). The optimization passes (●) generate necessary metadata for PA modifiers, inserts wrappers for compatibility with legacy code, and prepares initializers for statically allocated pointers. The AArch64 Frame Lowering emits function prologues and epilogues and is modified to include instructions for authenticating the LR value (●). The

![Figure 3: PARTS architecture diagram. Source code flows into the Clang Frontend, which connects to the LLVM opt component (containing PARTS opt-passes). The opt component outputs LLVM IR. The LLVM opt component connects to the LLVM backend (containing AArch64 modifications and PARTS backend-passes). The backend component outputs Machine IR. The backend component connects to the executable, which is linked with PARTSlib. The diagram includes a legend: new component (unfilled square) and LLVM internal (filled square).](4086a572c080354982c11f1de4d6921d_img.jpg)

Figure 3: PARTS architecture diagram. Source code flows into the Clang Frontend, which connects to the LLVM opt component (containing PARTS opt-passes). The opt component outputs LLVM IR. The LLVM opt component connects to the LLVM backend (containing AArch64 modifications and PARTS backend-passes). The backend component outputs Machine IR. The backend component connects to the executable, which is linked with PARTSlib. The diagram includes a legend: new component (unfilled square) and LLVM internal (filled square).

Figure 3: PARTS architecture.

PARTS backend passes (3) retrieve the PA modifiers and instruments appropriate low-level instructions. The resulting binary is linked with PARTSlib (4), which at run-time creates PACs for the initialized pointers.

### 6.1 LLVM Compiler Integration

While the LLVM 6.0 AArch64 backend recognizes PA instructions, they are not used by any pre-existing security feature. Our modifications consist of added optimizer and backend passes, minor modifications to the AArch64 backend, and new PARTS-specific intrinsics. Where applicable, we use optimizer passes that operate on the high-level LLVM *intermediate representation* (IR). Nonetheless, much of the needed functionality is PA-specific and thus implemented in the backend that uses low-level LLVM *machine IR* (MIR), and a register- and instruction set specific to 64-bit ARM.

**Determining pointer type-id.** The compiler backend views the program from a low-level perspective, and the MIR has lost much of the semantics present in C or the high-level IR. Therefore, PARTS must determine type-ids during its optimizer passes where this information is still available (Figure 3, 1). The type-id for data consists of a truncated 64-bit SHA-3 hash of the pointer's LLVM *ElementType*. The *ElementType* represents the IR level data type and distinguishes between basic data types, but does not retain typedef or other information from the frontend (i.e., clang). Code pointers use the same scheme wherein the *ElementType* consists of the function signature at the same abstraction level. The type-ids are passed to the backend either via PARTS-specific compiler intrinsics, or by embedding them as metadata in the existing IR instructions. The

AArch64 instruction selection retrieves the information from the IR instructions and transfers it to the emitted MIR (Figure 3, 2). To facilitate the run-time bootstrap (Section 6.2) PARTS also includes a pass that prepares a custom initializer function that is called at run-time to generate PACs for defined global pointers (Figure 3, 1).

**Return addresses signing.** Return address signing is implemented in the AArch64 backend during frame lowering (Figure 3, 2). Frame lowering emits the function prologues and epilogues, and for non-leaf functions, emits instructions for storing and retrieving the LR value from the stack. PARTS authenticates the value of the LR only if it was retrieved from the stack. The PAC modifier is based on the 16 least-significant bits of the SP value and a 48-bit function-specific function-id. The function-id is guaranteed to be unique within the current compilation unit or, with link time optimization (LTO), the whole program. To avoid repetition across different compilation units, the function-id is generated using a pseudorandom, non-repetitive sequence.

**Code pointer signing.** PARTS uses the combined PA instructions for branches and converts branch instructions directly to their PA variants (Figure 3, 3). The PAC for any code pointer is created only once at the time of pointer creation, e.g., when the address of a function is taken. This is instrumented by adding a PAC-creation instruction immediately after the instruction that moves a code pointer to a register. Subsequent load and store operations do not authenticate the signed code pointers, instead they are authenticated only on use.

**Data pointer signing.** As discussed in Section 5.4, it is not feasible to perform on-use authentication for data pointers. Instead, we authenticate data pointers when they are loaded from memory and create PACs before storing them. In some cases, e.g., using globals, the IR will include explicit load and store operations that can be furnished with the type-id. Our modified Instruction Selection then forwards the type-id to the emitted MIR (Figure 3, 2). However, stack-based store and load operations, in particular, are often not present before the backend finalizes the stack-layout and register allocation. Thus, some load and store instructions must be instrumented solely in the backend.

While it would be possible to modify the AArch64 backend (e.g., register allocation), we have instead opted for a less invasive approach. The PARTS backend pass (Figure 3, 3) finds load and store instructions in the MIR, and uses the attached type-id for instrumentation. When the type-id is not present, e.g., because the load and store is a register spill, the type-id is fetched from surrounding code. For instance, when instrumenting the store due to register spilling

```
MACRO movFunctionId Mod
    movk Mod, #func_id16, ls1 #16
    movk Mod, #func_id32, ls1 #32
    movk Mod, #func_id48, ls1 #48
ENDM

function:
    mov Xd, SP ; ① get SP
    movFunctionId Xd ; ② get id
    pacib LR, Xd ; ③ PAC
    stp FP, LR, [SP, #0] ; store
    ; function body
    ldp FP, LR, [SP, #0] ; load LR
    mov Xd, SP ; ⑤ get SP
    movFunctionId Xd ; ④ get id
    autib LR, X
    ret
```

Listing 2: The PARTS return address signing binds the PAC to the SP (①,⑤) and unique function id (②,④). The PA modifier is in register Xd during PAC creation (③) and authentication (⑥). The 48-bit func-id is split into three 16-bit parts, each moved individually to Xd by left-shifting.

a pointer variable, the correct type-id can be fetched from the original load.

### 6.2 Run-time Bootstrap

Programs may contain pointers in statically allocated data, i.e., pointers stored in global variables or static local variables. These are initialized by the compiler or linker, and therefore cannot include PACs. The PARTSlib runtime library instead invokes the compiler generated custom PAC initializer function at process startup. Our Proof-of-Concept implementation invokes the PARTSlib bootstrap using compiler instrumentation that explicitly calls the functionality when entering main.

### 6.3 Instrumentation

PARTS uses only in-line instrumentation and does not require storage of separate run-time metadata. With the exception of the bootstrap process the original code structure is thus largely unchanged. As discussed in Section 2.2, no explicit error handling is added by PARTS; instead, an authentication failure will set specific high-order bits in the pointer, thus triggering a memory translation fault on subsequent dereference or call using the pointer that failed authentication. The high-order bits ensure that the fault is distinguishable as one caused by authentication failure. Our code listings use two macros for setting up PA modifiers for

```
MACRO movTypeId Mod
    mov Mod, #type_id00
    movk Mod, #type_id16, ls1 #16
    movk Mod, #type_id32, ls1 #32
    movk Mod, #type_id48, ls1 #48
ENDM

mov cPtr, #instr_addr ; load cPtr
movTypeId Xd ; ① get id
pacia cPtr, Xd ; ② PAC
; no intermediate cPtr instrumentation
movTypeId Xd ; ③ get id
blraa cPtr, Xd ; ④ branch
```

Listing 3: The PARTS forward-edge code pointer signing uses the code pointer's type-id as the PA modifier (①,③). The 64-bit type-id is split into four 16-bit parts. The PAC is created only once when initially creating the code pointer (②). Upon use, i.e., indirect call, the PAC is authenticated using the combined branch and authenticated instruction (④). PARTS does not instrument intermediate store/load operations.

return address signing and type-id based PACs, these are shown in Listing 2 and Listing 3.

**Return address signing.** The return address signing instrumentation is similar to GCC's implementation [31] but includes an added modifier (Listing 2). The function prologue is instrumented such that it prepares the PA modifier by moving SP (①) value into a free register. The SP value is combined with the function-id (②) to form the PA modifier, which is then used with the instruction B key (③). The function-id is generated at compile-time using LLVM's random number generator, and is guaranteed to be unique within the LLVM Module (i.e., the whole program, when using link time optimization). The function epilogues (i.e., any part that ends with a return or a tail-call) are similarly instrumented to generate the same PA modifier (④,⑤) and to verify the PAC in the restored LR (⑥).

**Code pointer signing.** PARTS instruments code pointers only on creation and use (Listing 3). Specifically, when a code pointer is initially created, PARTS will use the instruction A-key to create a PAC (②) based on the target type-id (①). The instrumentation will at no point remove the PAC from a code pointer. Instead, PARTS uses the combined authenticate and branch instructions — e.g., blraa—to perform the branch directly on an authenticated pointer (④), again using the same PA modifier (⑥).

```
ldr dPtr, [SP, #0] ; load dPtr
movTypeId Xd, #type_id ; ① get id
autda dPtr, Xd ; ② authenticate
; dPtr is directly usable
```

Listing 4: PARTS immediately authenticates data pointers loaded from writeable memory. This is done by first loading the type-id (①) and then verifying the PAC (②).

**Data pointer signing.** All data pointer stores and loads are instrumented such that a PAC is created immediately before store and authenticated immediately after load (Listing 4). When a data-pointer is used the instrumentation first sets up the correct PA modifier, i.e., the type-id (①). The pointer is then immediately authenticated using the modifier and data A-key (②); this also strips the PAC from the pointer. As long as the data pointer resides in a register it can thus be used without any performance overhead. PARTS creates PACs for pointers immediately before store in the same manner, save for the `pacda` instruction.

## 7 Evaluation

We develop our Proof-of-Concept implementation of PARTS on the ARMv8-A Base Platform Fixed Virtual Platform (FVP), based on Fast Models 11.4, which supports version 8.0 to 8.4 of the ARMv8-A architecture [4]. At the time of writing, the only PA-capable hardware is the Apple A12 and S4 SoCs featuring ARMv8.3-A CPUs [2]. However, these proprietary SoCs are, to the best of our knowledge, not available in development versions outside Apple. The FVP provides a software simulation of an ARMv8.3-A processor in AArch64 mode, and is, to the best of our knowledge, the only publicly available environment with ARMv8-A PA support.

### 7.1 ARMv8.3 Emulation and Software Stack

We use GNU/Linux with a 4.14 kernel, modified to support PA. We modified the bootloader and kernel to activate ARMv8-A PA, and allow key configuration during kernel scheduling at Exception Level 1 (EL1 in Figure 4). Our kernel modifications are based on Mark Rutland's 2018 PA patches<sup>3</sup>.

PA keys for each task are stored in a process-specific `mm_context_t` structure (in the process' memory descriptor in the kernel) which contains architecture-specific data related to the process address space. Threads within the same process have a common memory descriptor, and thus share the same PA keys. The scheduler will configure the PA key registers using the keys in the process' memory descriptor

![Diagram illustrating the trapping of PA configuration. The diagram shows three execution levels: EL3 - ARM trusted FW, EL2 - Hypervisor, and EL1 - Kernel. The EL1 - Kernel contains components: scheduler, key reg. bank (1/core), and mm_context_t (1/task). The EL0 - user space contains two instances of 'binary with PARTS'. The 'source PARTS compiler' interacts with the EL0 - user space. Arrows indicate the flow: 1. EL0 - user space interacts with EL2 - Hypervisor. 2. EL0 - user space interacts with EL1 - Kernel. 3. EL0 - user space interacts with the source PARTS compiler.](0d5fdb87a392819c7d2e3b6230912a0b_img.jpg)

Diagram illustrating the trapping of PA configuration. The diagram shows three execution levels: EL3 - ARM trusted FW, EL2 - Hypervisor, and EL1 - Kernel. The EL1 - Kernel contains components: scheduler, key reg. bank (1/core), and mm\_context\_t (1/task). The EL0 - user space contains two instances of 'binary with PARTS'. The 'source PARTS compiler' interacts with the EL0 - user space. Arrows indicate the flow: 1. EL0 - user space interacts with EL2 - Hypervisor. 2. EL0 - user space interacts with EL1 - Kernel. 3. EL0 - user space interacts with the source PARTS compiler.

Figure 4: The trapping of PA configuration must be released ①, in order to allow the kernel to manage the PA keys on process creation and context switches ②. Faults generated by failed authentications will be trapped by the kernel ③.

whenever a task is scheduled to run. When a new child process is forked, the parent's keys are duplicated to the child's memory descriptor. However, when a new executable file is exec'd in the context of an existing process, the kernel initializes a new set of PA keys using `get_random_bytes()`. In other words, each new process receives a new set of PA keys which remain unchanged thereafter.

### 7.2 Security Evaluation

#### 7.2.1 Return address signing

Return address signing in both GCC [31], and PARTS prevents an attacker from introducing forged return addresses to the program stack. Compared to GCC, PARTS augments the PA modifier used for return address signing by combining a function-specific identifier with the SP value ( $R2$ ). As a result, PARTS return address signing precludes the possibility of reuse of the return address between different functions, irrespective of SP value collisions. It remains susceptible to pointer reuse between distinct invocations of the same function from call sites with same SP value ( $R1$ ).

#### 7.2.2 Forward-edge code pointer signing

As with PARTS return address signing, forward-edge code pointer signing prevents an attacker from using forged code pointers injected into program memory ( $R1$ ). This prevents a large class of attacks (e.g., typical ROP/JOP gadgets) that rely on redirecting the control flow to code in the middle of functions, i.e., addresses that never were valid targets of benign control-flow transfers.

<sup>3</sup>https://lwn.net/Articles/752116/

PARTS restricts forward-edge code pointer reuse by enforcing *run-time type safety* for signed pointers (R2). Under this scheme, pointers used in a pointer reuse attack must share the same type-id (i.e., have a matching type on the LLVM IR level). This prevents large classes of function-reuse attacks. The solution is compatible with common programming patterns involving function pointers (R3), such as callbacks, but allows reuse between code pointers to functions with identical type signatures.

#### 7.2.3 Data pointer signing

PARTS data pointer signing protects all data pointers and prevents an attacker from loading a forged data pointer to program memory (R1). This prevents all non-control data attacks that rely on corrupting data pointers to unintended parts of memory. This class of attacks includes all currently known DOP attacks [16].

PARTS restricts data pointer reuse by enforcing run-time type safety also for data pointers (R2). Reuse attacks would be more useful to an attacker if they could substitute a vulnerable pointer with one referencing an object of different size or type. Therefore restricting pointer substitution based on the pointer's type restricts the attacker's capability to cause unintended data flows within the program. However, pointer conversions are a challenge for data pointer integrity. As discussed in Section 5.3, PARTS accommodates data pointers that are cast from type *A* to an incompatible type *B* by writing the converted pointer using the type-id of *B*. This may expand the effective set of reusable pointers under our threat model; the attacker can record pointers of type *A* and reuse them at PAC conversion site  $A \to B$ , thereby obtaining a pointer of type *B* to an object of type *A*. This converted pointer can then be used at de-reference sites that require pointers of type *B*. If the program also includes a conversion from *B* to *A* this makes both types interchangeable.

PARTS data pointer integrity does not guarantee spatial safety of pointer accesses to data objects, nor does it address the temporal safety (e.g., prevent use-after-free conditions). ARMv8-A PA does not provide facilities to directly address these challenges. We discuss orthogonal schemes that can be used in combination with PARTS to provide spatial and temporal safety guarantees in Section 8.

#### 7.2.4 PAC entropy

As explained in Section 3, the PAC size *b* is a concern for any PA-based scheme. On typical AArch64 Linux systems, *b* is between 16 and 24. To succeed with probability *p*, a PAC guessing attack requires  $\frac{\log(1-p)}{\log(1-2^{-b})}$  guesses on the assumption that a PAC comparison failure leads to program termination. On our simulator setup where *b* = 16, achieving a 50%-likelihood for a correct guess requires 45425 attempts.

Note that ROP/DOP attacks require an environment where a set of jumps (gadgets) can be set up, each requiring a separate PAC to be broken. Consequently, success probability of a complete attack will decrease exponentially with the number of jumps necessary.

Pre-forked or multithreaded programs will share the same PA key between the parent and all sibling threads/processes. This could allow an attacker to brute force a PAC by targeting a sibling, if PAC failure on a sibling does not result in the termination (and hence PA key reset) of all threads/processes sharing the same PAC key. In this scenario,  $2^{b-1}$  guesses on average are enough to guess a *b*-bit PAC (32768 guesses for *b* = 16). Multithreaded / pre-forking applications could be hardened against guessing attacks by requiring a full application restart if the number of unexpected terminations of child threads/processes exceeds a pre-defined threshold.

### 7.3 Performance Evaluation

The FVP processor, peripheral models, and micro-architectural fabric is simplified. Consequently, timing on the FVP model differs from actual hardware. The ARM Fast Models documentation states that “*all instructions execute in one processor master clock cycle*”. We confirm this behavior for PA instructions in the FVP by using microbenchmarks that allow PA instructions to be timed in isolation. As a result, we cannot use the FVP to estimate the expected runtime overhead of PARTS. Instead, we estimate the execution time of PA instructions and develop a PA-analogue that emulates the run-time cost of PA instructions (Section 7.3.1). We then run large-scale benchmarks on real (non-PA) hardware using our PA-analogue (Section 7.3.2).

#### 7.3.1 PA-analogue

From [5, Table 8] we can deduce that on a (1.2GHz) mobile core, the PAC is computable with an approximate overhead of 4 cycles, without accounting for the potential speed benefits of opportunistic pipelining or the inclusion of several parallel PAC computing engines per core. For simplicity, we assume equal cycle counts for all PA instructions. Based on this assumption we construct a *PA-analogue* (Listing 5) as a proxy to measure overhead of PA instrumentation on non-PA CPUs: it consists of four exclusive-or (*eor*) operations to account for the 4 cycles. The final *eor* operates on the modifier and SP to enforce a memory read/write dependency, thus preventing the CPU pipeline from arbitrarily delaying the operations. We have confirmed that our PA-analogue exhibits the expected overhead using our microbenchmarks.

```
eor Xptr, Xptr, #0x2 ; spend cycles
eor Xptr, Xptr, #0x3 ; to approximate
eor Xptr, Xptr, #0x5 ; PA instruction
eor Xptr, Xptr, Xmod ; overhead
```

Listing 5: PA-analogue simulating PA instructions

#### 7.3.2 nbench-byte benchmarks

For our performance evaluation we use the Linux nbench-byte 2.2.3 synthetic benchmark<sup>4</sup> designed to measure CPU and memory subsystem performance, providing a reasonable prediction of real-world system performance<sup>5</sup>. We follow work such as [6, 10, 22, 33, 37, 10] and use nbench rather than the SPEC CPU standardized applications benchmarks for our evaluation, as nbench allows us verify the functionality of PARTS instrumentation with manageable simulation times on the FVP. The current version of the SPEC CPU benchmark suite, SPEC CPU2017<sup>6</sup>, has replaced many tests in the previous, now retired SPEC CPU2006<sup>7</sup> with significantly larger and more complex workloads (up to ~10X higher dynamic instruction counts). As a result, the SPEC simulation times on the FVP proved to be unmanageable; for example, running individual SPEC benchmarks take hours to days to complete on the FVP. This is a challenge for both researchers and industry practitioners who rely on hardware simulation for evaluation [30]. We report our results for a subset of SPEC CPU2017 tests in Appendix B.

The nbench benchmarks include 10 different tests. We adopt the same methodology as Brasser et al. [6] and run each test a constant number of iterations for the following cases: a) uninstrumented baseline b) each PARTS scheme (return address signing, forward-edge code pointer integrity, and data pointer integrity) enabled individually, and c) all schemes enabled simultaneously. Compiler optimizations were disabled for all tests. The tests were performed on a 96boards Kirin 620 HiKey (LeMaker version) with a ARMv8-A Cortex A53 Octa-core CPU (1.2GHz) / 2GB LPDDR3 SDRAM (800MHz) / 8GB eMMC, running the Linux kernel v4.18.0 and BusyBox v1.29.2. Figure 5 shows the results, normalized to the baseline. A more detailed description can be found in Appendix A.

Return address signing incurs a negligible overhead of less than 0.5%. This is expected because the estimated performance overhead of 12 to 16 cycles is typically small compared to the full execution time of the instrumented function. The same holds for indirect calls (6-8 cycle overhead at the call site), although indirect calls are underrepresented in nbench-byte. However, our microbenchmarks for the code

pointer integrity instrumentation indicate that a 6 to 8 cycle overhead per indirect function call is reasonable under the assumed QARMA performance.

Data pointer integrity depends largely on the memory profile of the instrumented program. For instance, the floating point emulation test extensively handles data pointers, resulting in a 39.5% overhead. In contrast, the Fourier and neural network benchmarks contain no data pointers and thus incur no discernible overhead. The geometric mean of the overhead of the combined instrumentation for all tests is 19.5%.

### 7.4 Compatibility Evaluation

Based on our evaluation, PARTS is compatible with standard C code (R3). Because return address signing only affects the instrumented function, it can be safely applied without interfering with the operation of other parts of programs, or uninstrumented code.

PARTS forward-edge code pointer integrity and data pointer integrity can be safely applied to complete code bases. However, if PARTS is applied only to a partial code base, the instrumented code interfacing with non-instrumented (legacy) libraries requires special consideration. In particular pointers used by both instrumented and uninstrumented code cannot be passed directly between them. We discuss solutions for backwards compatibility with legacy libraries in Section 10.

We encountered no compatibility issues with PARTS during our performance evaluation with nbench (Section 7.3).

## 8 Related Work

Code-pointer integrity (CPI) [21] protects access to code pointers — and data pointers that may point to code pointers — by storing them in a disjoint area of memory; the SafeStack<sup>8</sup>. The SafeStack itself must be protected from unauthorized access. Randomizing the location of the SafeStack is efficient [20], but easily defeated by an attacker who can read arbitrary memory. Stronger protection of the SafeStack using hardware-enforced isolation or software-isolation incurs an average performance overhead of 8.4% or 13.8% in SPEC CPU2006 benchmarks.

**Protecting pointers using cryptography.** Prior cryptographic defenses against run-time attacks generally assume the attacker cannot read memory. PointGuard [12] instruments a program to apply a secret XOR mask to all pointer values. This prevents an attacker from reliably forging pointer values without knowledge of the mask. Data randomization [7] extends data masking to cover all data in memory. It uses static points-to analysis and distinct masks to partition memory accesses in separate classes. Neither

<sup>4</sup>http://www.math.utah.edu/~mayer/linux/bmark.html

<sup>5</sup>http://www.math.utah.edu/~mayer/linux/byte/bdoc.pdf

<sup>6</sup>https://www.spec.org/cpu2017/

<sup>7</sup>https://www.spec.org/cpu2006/

<sup>8</sup>https://clang.llvm.org/docs/SafeStack.html

![](36ac3e730a00d3f42d3400f5709f641a_img.jpg)

Figure 5(a) is a bar chart showing the normalized overhead (Y-axis, ranging from 0.9 to 1.5) for various nbench benchmarks (X-axis: Numeric sort, String sort, Bitfield, FP emulation, Fourier, Assignment, Idea, Huffman, Neural net, Lu decomposition) when instrumented with different signing methods. The legend indicates four signing methods: return address signing (light gray), forward-edge code pointer signing (medium gray), data pointer signing (dark gray), and all enabled (black). FP emulation shows the highest overhead (around 1.4) when all enabled signing is used.

(a) Results of instrumented nbench-byte tests features, normalized to a non-instrumented baseline.

![](f176174c2978785e86a8352bd45e322e_img.jpg)

Figure 5(b) is a bar chart showing the event count (Y-axis, ranging from 0 to 5.9E+08) for various nbench benchmarks (X-axis: Numeric sort, String sort, Bitfield, FP emulation, Fourier, Assignment, Idea, Huffman, Neural net, Lu decomposition) when instrumented with different signing methods. The legend indicates three signing methods: return address signing (light gray), forward-edge code pointer signing (medium gray), and data pointer signing (dark gray). FP emulation shows the highest event count (around 5.9E+08) when all enabled signing is used.

(b) Run-time count of executed locations instrumentable by PARTS. Because the program’s memory profile affects performance the benchmark results clearly correlate with observed memory use (e.g., FP emulation has a large data pointer integrity overhead because it uses many data pointers)

Figure 5: nbench benchmark results

PointGuard nor data randomization remain effective under our threat model.

Similarly to ARMv8-A PA, *Cryptographic CFI* (CCFI) [25] uses MACs to protect control-flow data, such as return addresses, function pointers, and vtable pointers. Like PARTS, CCFI uses a function’s type signature to separate function pointers to distinct protection domains, but does not protect function pointers embedded in C structures. Unlike PA, CCFI only benefits from hardware-accelerated AES for speeding up MAC, resulting in a high performance overhead (52% overhead on average in SPEC CPU2006 benchmarks). In contrast, PARTS also benefits from hardware-accelerated checks by using ARMv8-A PA instructions, protects both code and data pointers, including pointers embedded in C structures.

**Hardware-assisted mechanisms.** Various hardware-assisted defenses are described in research literature [15, 42, 41, 14, 38, 40, 28, 32]. The majority of such defenses have only been realized as soft microprocessor prototypes on FPGAs. Here we describe mechanisms available in commercial off-the-shelf processor architectures.

Only a few commercial processors, such as the SPARC M79, support tagged memory, which can be used to realize variety of security models (including pointer integrity). ARM recently announced support for memory tagging in the

ARMv8.5-A architecture<sup>10</sup>. It enforces that all accesses to memory must be made via a pointer with the correct tag. Pointer tags use the existing address tagging feature in the ARM ISA that partly overlaps with the bits used to store PA PACs, meaning that enabling both features simultaneously reduces the available PAC size by eight bits.

Hardware-assisted memory tagging is designed primarily as a statistical debug aid against use-after-free and other temporal memory errors. *Hardware-Assisted AddressSanitizer* (HWASAN) [34] is an AArch64-specific compiler-based tool that builds upon *AddressSanitizer* (ASAN) — a memory-error detector popular for vetting memory safety bugs during software testing. ASAN can detect both spatial and temporal memory errors. HWASAN can leverage hardware tagged memory, such as SPARC ADI and the upcoming ARMv8.5-A to reduce the performance overhead associated with managing tagged memory checks in software. ASAN / HWASAN are complementary to PARTS, as they provide spatial and temporal safety for data accesses via pointers.

*Intel Memory Protection Extensions* (MPX) is a hardware feature for detecting spatial memory errors that debuted in the Intel Skylake microarchitecture. MPX is similar to the software based SoftBound [27] and its hardware-based predecessor [15]. Although Intel MPX is a hardware-assisted approach specifically designed to provide spatial memory safety guarantees, it is not faster than software-based approaches [29]. It can cause up to 4x slowdown in the worst

<sup>10</sup>https://community.arm.com/processors/b/blog/posts/arm-a-profile-architecture-2018-developments-armv85a

<sup>9</sup>https://swisdev.oracle.com/\_files/What-Is-ADI.html

case with an average run-time overhead of 50%. It also suffers from other shortcomings, such as the lack of support for multithreading and several common C/C++ idioms. GCC has dropped support for MPX altogether<sup>11</sup>.

**Control-flow integrity.** Carlini et al. [8] define *fully-precise static CFI* as follows: “An indirect control-flow transfer along some edge is allowed only if there exists a non-malicious trace that follows that edge.” In other words, fully-precise static CFI enforces that execution follows a CFG that contains an edge if and only if that edge is exercised by intended program behavior. Fully-precise static CFI is thus the most restrictive *stateless* policy possible without breaking intended functionality. To date, there exist no implementation of fully-precise CFI; all practical implementations are limited by the precision of CFGs obtained through static control analysis.

Carlini et al. further show that all stateless CFI schemes, including fully-precise static CFI are vulnerable to *control-flow bending*; attacks where each control-flow transfer is within a valid CFG, but where the program execution trace conforms to no feasible benign execution trace. For instance, in a stateless policy such as fully-precise static CFI, the best possible policy for return instructions (i.e., backward edges in the CFG) is to allow return instructions within a function *F* to target any instruction that follows a call to *F*. In other words, fully-precise static CFI checks if a given control-flow transfer conforms to any of the known control-flow transfers from the current position in the CFG, and does not distinguish between different paths in the CFG that lead to a given control-flow transfer. For this reason CFI is typically augmented with a *shadow call stack* [1, 13] to enforce integrity of return addresses stored on the call stack. We compare PARTS to CFI solutions in Section 9.2.

## 9 Comparison with other integrity policies

### 9.1 Fully precise pointer integrity

As discussed in Section 4.1, Pointer Integrity can be loosely defined as a policy ensuring that the value of a pointer at the time of use (dereference or call) corresponds to the value of the pointer when it was created. In this section, we provide a more rigorous definition of Pointer Integrity.

We define *fully-precise pointer integrity* as follows: A pointer dereference is allowed if and only if the pointer is based on its target object. We adopt Kuznetsov et al.'s [21] definition of “*based on*” and say a pointer *P* is *based* on a target object *X* if, and only if, *P* is obtained at run-time by “(i) allocating *X* on the heap, (ii) explicitly taking the address of *X*, if *X* is allocated statically, such as a local or global variable, or is a control-flow target (including return locations,

<sup>11</sup>https://gcc.gnu.org/viewcvs/gcc?view=revision&revision=261304

whose addresses are implicitly taken and stored on the stack when calling a function), (iii) taking the address of a sub-object *y* of *X* (e.g., a field in the struct *X*), or (iv) computing a pointer expression (e.g., pointer arithmetic, array indexing, or simply copying a pointer) involving operands that are either themselves based on object *X* or are not pointers.”

Kuznetsov et al.'s CFI [21] (Section 8) provides fully-precise integrity guarantees for *code pointers* by ensuring that accesses to sensitive pointers are safe (sensitive pointers are code pointers and pointers that may later be used to access sensitive pointers). However, CFI requires dedicated, integrity-protected storage for sensitive pointers.

As discussed in Section 7.2, PARTS, and PA solutions in general, achieve an approximation of fully-precise pointer integrity. In particular, PARTS allows the substitution of a pointer *P* by another pointer *P'* based on object *X*, if *P* and *P'* share the PA modifier. In other words, when PA modifiers are unique to each protected pointer value, PA provides fully-precise pointer integrity. However, ensuring the uniqueness of PA modifiers is not possible in practice due to the following reasons: 1) program semantics may require a set of pointers to be substitutable with each other (e.g., pointers to callback functions) 2) the choice of allowed pointers may depend on run-time properties (e.g., which callback function was registered earlier). In these cases, a unique modifier must be determined at run-time. Fully-precise pointer integrity does not imply *memory safety*. In the case of PA, if the modifier is determined at run-time and stored in memory, the PA modifier itself may become a target for an attacker wishing to undermine the integrity policy. To avoid this, modifier values must be derived in a way which leaves the value outside the control of the attacker, e.g., stored in a dedicated hardware register, or read-only program memory.

### 9.2 Fully-precise static CFI

In contrast to stateless CFI, which allows control-flow transitions present in its CFG regardless of the origin of the code pointer value, PA-based solutions (including PARTS) can preclude forged pointer values from outside the process. The policy that prevents pointer reuse can suffer from limitations similar to those present stateless CFI.

PARTS return address signing provides strong guarantees even when subjected to pointer reuse. In contrast, a stateless CFI policy allows a function to return to any of its call sites. As such, static CFI cannot prevent injection of pointers that are within the expected CFG, i.e., control-flow bending attacks. PARTS additionally requires matching SP values, and that the reused return address originates from a prior function invocation of the same function within the same process for an attack to succeed.

PARTS forward-edge code pointer integrity provides similar guarantees (under reuse attacks) as LLVM's type-based protection (when subjected to any forged pointer). In both

cases, attacks are limited to using pointers of the correct dynamic type. PARTS in addition requires that the injected pointer originates from the victim process.

While shadow-stacks protected through randomization can be implemented with minimal performance overhead, our adversary model precludes this approach. Furthermore, software-isolated shadow stack solutions impose impractical performance overheads, and ARM processors do not currently provide direct hardware support for shadow stacks.

## 10 Conclusion and Future Work

We plan to extend PARTS protection architecture to other protection domains like the OS kernel, or hypervisor. The only significant change for PARTS architecture is to arrange for key configuration for both kernel and EL0 PARTS to be trapped (and managed) on a higher exception level (EL2,3). We are further looking at adding C++ support PARTS. While we do not expect any fundamental problems, some C++ specific features, such as inheritance, cannot be directly handled by our current instrumentation strategy.

Authenticated pointers with PACs cannot be used by legacy code (Section 2.2) while PARTS-instrumented code will trap if pointers without PACs are used. For legacy and PARTS code to interact, we can use wrappers that manipulate function arguments and return values by embedding/stripping PACs. For shared pointers or complex data structures, annotations can disable authentication of selected pointers, allowing programmers to manually adjust pointer conversion to and from legacy code.

Currently, the PARTS compiler assumes shared libraries to be uninstrumented. Instrumented shared libraries must deal with PACs for statically allocated pointers after linking, and thus require changes to the dynamic linker.

Pointer integrity does not imply full memory safety (Section 9.1). Although ARMv8-A PA does not support bounds checking for pointer accesses with authenticated pointers, it has a general-purpose instruction, `pacga`, for producing and validating PACs computed over the contents of two 64-bit registers. This can be used to build authenticated canaries to identify buffer overflow attacks, or to validate the integrity (freshness) of atomic data, such as integer or counter values. In principle, `pacga` instructions can even be chained to validate arbitrary-sized blocks of data.

Finally, effective ways of complementing PA with other emerging memory safety mechanisms like the forthcoming support for memory tagging in ARMv8.5-A is an important line of future work.

## Acknowledgments

This work was supported in part by the Academy of Finland under grant nr. 309994 (SELIoT), and the Intel Collabora-

tive Research Institute for Collaborative Autonomous & Re-silient Systems (ICRI-CARS).

The authors thank Kostya Serebryany and Rémi Denis-Courmont for interesting discussions and Zaheer Gauhar for implementation assistance.

## References

1. ABADI, M., ET AL. Control-flow integrity principles, implementations, and applications. *ACM Trans. Inf. Syst. Secur.* 13, 1 (Nov. 2009), 4:1-4:40.
2. APPLE INC. iOS Security — iOS 12. [https://www.apple.com/business/site/docs/iOS\\_Security\\_Guide.pdf](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf), 2018.
3. ARM LTD. ARMv8 architecture reference manual, for ARMv8-A architecture profile (ARM DDI 0487C.a). [https://static.docs.arm.com/ddi0487/ca/DDI0487C\\_a\\_armv8\\_arm.pdf](https://static.docs.arm.com/ddi0487/ca/DDI0487C_a_armv8_arm.pdf), 2017.
4. ARM LTD. Fast models, version 11.4, fixed virtual platforms (FVP) reference guide. [https://static.docs.arm.com/100966/1104/fast\\_models\\_fvp\\_rg\\_100966\\_1104\\_00\\_en.pdf](https://static.docs.arm.com/100966/1104/fast_models_fvp_rg_100966_1104_00_en.pdf), 2018.
5. AVANZI, R. The QARMA block cipher family. almost MDS matrices over rings with zero divisors, nearly symmetric even-mansour constructions with non-involutory central rounds, and search heuristics for low-latency s-boxes. *IACR Trans. Symmetric Cryptol.* 2017, 1 (2017), 4-44.
6. BRASSER, F., ET AL. DR.SGX: Hardening SGX enclaves against cache attacks with data location randomization. <https://arxiv.org/abs/1709.09917>, 2017.
7. CADAR, C., ET AL. Data randomization. Tech. Rep. MSR-TR-2008-120, Microsoft Research, September 2008.
8. CARLINI, N., ET AL. Control-flow bending: On the effectiveness of control-flow integrity. In *Proc. USENIX Security '15* (2015), pp. 161-176.
9. CHECKOWAY, S., ET AL. Return-oriented programming without returns. In *Proceedings of the 17th ACM Conference on Computer and Communications Security* (New York, NY, USA, 2010), CCS '10, ACM, pp. 559-572.
10. CHEN, S., ET AL. Detecting privileged side-channel attacks in shielded execution with Déjà Vu. In *Proc. ACM ASIA CCS '17* (2017), pp. 7-18.

[11] CHEN, S., XU, J., SEZER, E. C., GAURIAR, P., AND IYER, R. K. Non-control-data attacks are realistic threats. In *Proc. USENIX Security '05* (2005), pp. 177–191.

[12] COWAN, C., ET AL. PointGuard™: Protecting pointers from buffer overflow vulnerabilities. In *Proc. USENIX Security '03* (2003), pp. 91–104.

[13] DAVI, L., ET AL. MoCFI: A framework to mitigate control-flow attacks on smartphones. In *Proc. NDSS '12* (2012).

[14] DAVI, L., ET AL. HAFIX: Hardware-assisted flow integrity extension. In *Proc. ACM/EDAC/IEEE DAC '15* (2015), pp. 74:1–74:6.

[15] DEVIETTI, J., ET AL. Hardbound: Architectural support for spatial safety of the C programming language. In *Proc. '08* (2008), pp. 103–114.

[16] HU, H., ET AL. Data-oriented programming: On the expressiveness of non-control data attacks. In *Proc. IEEE S&P '16* (2016), pp. 969–986.

[17] INTEL. Control-flow enforcement technology preview. <https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf>, 2016.

[18] ISO/IEC. ISO/IEC 9899:201x committee draft — December 2, 2010. <http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1548.pdf>, 2010.

[19] KORNAU, T. *Return Oriented Programming for the ARM Architecture*. PhD thesis, Ruhr-Universität Bochum, 2009.

[20] KUZNETSOV, V., ET AL. Poster: Getting the point(er): On the feasibility of attacks on code-pointer integrity. *IEEE S&P '15*.

[21] KUZNETSOV, V., ET AL. Code-pointer integrity. In *Proc. USENIX OSDI '14* (2014), pp. 147–163.

[22] LEE, S., ET AL. Inferring fine-grained control flow inside SGX enclaves with branch shadowing. In *Proc. USENIX Security '17* (2017), pp. 557–574.

[23] LI, R., AND JIN, C. Meet-in-the-middle attacks on reduced-round QARMA-64/128. *The Computer Journal* 61, 8 (2018), 1158–1165.

[24] LILJESTRAND, H., ET AL. PAC it up: Towards pointer integrity using ARM pointer authentication. <arXiv:1811.09189> [cs.CR], 2019.

[25] MASHTIZADEH, A. J., ET AL. CCFI: Cryptographically enforced control flow integrity. In *Proc. ACM CCS '15* (2015), pp. 941–951.

[26] MICROSOFT. Enhanced Mitigation Experience Toolkit. <https://www.microsoft.com/emet>, 2016.

[27] NAGARAKATTE, S., ET AL. SoftBound: Highly compatible and complete spatial memory safety for C. In *Proc. ACM PLDI '09* (2009), pp. 245–258.

[28] NYMAN, T., ET AL. HardScope: Thwarting DOP with hardware-assisted run-time scope enforcement. <arXiv:1705.10295> [cs.CR], 2017.

[29] OLEKSENKO, O., ET AL. Intel MPX explained: An empirical study of Intel MPX and software-based bounds checking approaches. <https://arxiv.org/abs/1702.00719>, 2017.

[30] PANDA, R., ET AL. Wait of a decade: Did SPEC CPU 2017 broaden the performance horizon? In *Proc. IEEE HPCA '18* (2018), pp. 271–282.

[31] QUALCOMM TECHNOLOGIES, INC. Pointer authentication on ARMv8.3. <https://www.qualcomm.com/media/documents/files/whitepaper-pointer-authentication-on-armv8-3.pdf>, 2017.

[32] ROESSLER, N., AND DEHON, A. Protecting the stack with metadata policies and tagged hardware. In *Proc. IEEE S&P '18* (2018), pp. 1072–1089.

[33] SEO, J., ET AL. SGX-Shield: Enabling address space layout randomization for SGX programs. In *Proc. NDSS '17* (2017).

[34] SEREBRYANY, K., ET AL. Memory tagging and how it improves C/C++ memory safety. <arXiv:1802.09517> [cs.CR], 2018.

[35] SHACHAM, H. The geometry of innocent flesh on the bone: Return-into-libc without function calls (on the x86). In *Proc. ACM CCS '07* (2007), pp. 552–561.

[36] SHACHAM, H., ET AL. On the effectiveness of address-space randomization. In *Proc. ACM CCS '04* (2004), pp. 298–307.

[37] SHIH, M.-W., ET AL. T-SGX: Eradicating controlled-channel attacks against enclave programs. In *Proc. NDSS '17* (2017).

[38] SONG, C., ET AL. HDFI: Hardware-assisted data-flow isolation. In *Proc. IEEE S&P '16* (2016), pp. 1–17.

[39] SZKERES, L., ET AL. SoK: Eternal war in memory. In *Proc. IEEE S&P '13* (2013), vol. 12, pp. 48–62.

[40] TSAMPAS, S., ET AL. Towards automatic compartmentalization of c programs on capability machines. In *Workshop on Foundations of Computer Security 2017* (2017), pp. 1–14.

[41] WATSON, R. N. M., ET AL. CHERI: A hybrid capability-system architecture for scalable software compartmentalization. In *Proc. IEEE S&P ’15* (2015), pp. 20–37.

[42] WOODRUFF, J., ET AL. The CHERI capability model: Revisiting RISC in an age of risk. In *Proc. ’14* (2014), pp. 457–468.

[43] ZONG, R., AND DONG, X. Meet-in-the-middle attack on QARMA block cipher. *IACR Cryptology ePrint Archive* (2016).

## A nbench experimental setup

The nbench benchmarks employs dynamic workload adjustment to allow the tests to expand or contract depending on the capabilities of the system under test. To achieve this, nbench employs timestamping to ensure that a test run exceeds a pre-determined minimum execution time. If a test run finishes before the minimum execution time has been reached, the test dynamically adjusts its workload, and tries again. For example, the Numeric Sort test will construct an array filled with random numbers, measure the time taken to sort the array. If the time is less than the pre-determined minimum time, the test will build two arrays, and try again. If sorting two arrays takes less time than the pre-determined minimum, the process repeats with more arrays.

Since we want to determine the relative overhead in execution time caused by our instrumentation, we employ the methodology described by Brasser et al. [6] and modify nbench to instead run each test a constant number of iterations. The number of iterations was determined individually for each test based on the iteration counts determined by an unmodified nbench run on the FVP. We then instrument the nbench benchmarks using our PA-analogue (Section 7.3.1) and measure the relative execution time between non-instrumented and instrumented nbench tests on the HiKey development platform using the BusyBox time utility.

Each individual benchmark test was run 200 times using the pre-determined number of iterations. Figure 5a, in Section 7.3.2 shows instrumentation overhead for individual tests in relation to the uninstrumented test run. Table 3 shows the numeric overhead ratio for each individual test. Because the nbench benchmarks are designed to measure performance in a manner which is operating system agnostic, they are written in ANSI C and only execute in a single thread. We therefore only consider user time when measuring the overhead of the instrumentation, and exclude context switches and system calls.

The run-time overhead of PARTS is dependent on specific run-time events, such as the number of function invocations in the case of return address signing. Figure 5b in

Table 2: Overhead as ratio and standard deviation ( $\sigma$ ) for return address signing and (forward-edge) code pointer signing for 505.mcf\_r and 519.lbm\_r SPEC benchmarks.

| Benchmark | Uninstrumented ratio | $\sigma$ | ret. addr. sign. + code ptr. integrity |          |
|-----------|----------------------|----------|----------------------------------------|----------|
|           |                      |          | ratio                                  | $\sigma$ |
| 505.mcf_r | 1                    | 0.004    | 1.005                                  | 0.004    |
| 519.lbm_r | 1                    | 0.000    | 1.000                                  | 0.000    |

Section 7.3.2 shows the order of magnitude of instrumented run-time events in the nbench tests. We also report the user mode run-time for uninstrumented nbench tests, the number of iterations of each individual test, and number of instrumented run-time events in Table 4.

## B SPEC CPU2017 experimental setup

Due to unmanageable simulation times in the FVP simulator we have verified the correctness of PARTS instrumentation only on a subset of SPEC CPU2017 benchmarks. Specifically, we chose the 505.mcf\_r and 519.lbm\_r benchmarks from the SPECrate 2017 integer and floating point suites, because these were the smallest C benchmarks in terms of lines of code. The benchmarks were compiled using SPEC runcpu, with a AArch64-specific configuration specifying whole-program-llvm<sup>12</sup>, with our PARTS-enabled LLVM, as the compiler. We then extracted the bitcode — created by whole-program-llvm during compilation — and used it to instrument and compile the binaries we used for evaluation: one uninstrumented, one instrumented with PA instructions, and one instrumented with our PA-analogue. We enabled both return address and forward-edge code pointer signing for the instrumented binaries.

We run the PARTS instrumented binaries on the FVP simulator to confirm correct functionality. The simulation time for the tested benchmarks was between 12 and 48 hours. Performance benchmarks, for baseline and PA-enabled binaries, were run on the HiKey devices, using the same setup as our nbench evaluation. The results are shown in Table 2, and are based on five runs of each benchmark. In 505.mcf\_r we observed overheads consistent with our results from nbench. We observed no discernible overhead in 519.lbm\_r. We attributed this to the following properties of 519.lbm\_r: (a) it does not exhibit forward-edge code pointers, and (b) it has few non-leaf function calls in relation to the arithmetic computation performed part of the benchmark.

<sup>12</sup><https://github.com/travitch/whole-program-llvm>

Table 3: Overhead as ratio and standard deviation ( $\sigma$ ) for nbench tests reported separately for uninstrumented, return address signing, (forward-edge) code pointer signing, data pointer signing and all instrumentation enabled.

| Test                     | PARTS          |          |                 |          |                   |          |                   |          |             |          |
|--------------------------|----------------|----------|-----------------|----------|-------------------|----------|-------------------|----------|-------------|----------|
|                          | Uninstrumented |          | ret. addr. sign |          | code ptr. signing |          | data ptr. signing |          | all enabled |          |
|                          | ratio          | $\sigma$ | ratio           | $\sigma$ | ratio             | $\sigma$ | ratio             | $\sigma$ | ratio       | $\sigma$ |
| Numeric sort             | 1              | 0.002    | 1               | 0.003    | 1                 | 0.003    | 1.293             | 0.003    | 1.293       | 0.003    |
| String sort              | 1              | 0.002    | 1.01            | 0.002    | 1                 | 0.002    | 1.251             | 0.002    | 1.259       | 0.002    |
| Bitfield                 | 1              | 0.002    | 1               | 0.002    | 1                 | 0.002    | 1.15              | 0.002    | 1.15        | 0.001    |
| FP emulation             | 1              | 0.001    | 1               | 0.001    | 1                 | 0.001    | 1.395             | 0.001    | 1.396       | 0.001    |
| Fourier                  | 1              | 0.002    | 1.027           | 0.004    | 0.999             | 0.003    | 0.998             | 0.002    | 1.016       | 0.003    |
| Assignment               | 1              | 0.001    | 1               | 0.002    | 1                 | 0.002    | 1.145             | 0.002    | 1.145       | 0.002    |
| Idea                     | 1              | 0.001    | 1.004           | 0.002    | 1                 | 0.002    | 1.279             | 0.002    | 1.283       | 0.002    |
| Huffman                  | 1              | 0.001    | 0.999           | 0.001    | 0.999             | 0.001    | 1.294             | 0.001    | 1.295       | 0.002    |
| Neural net               | 1              | 0.001    | 1.002           | 0.002    | 1                 | 0.002    | 1.001             | 0.002    | 1.001       | 0.003    |
| Lu decomposition         | 1              | 0.001    | 1               | 0.002    | 1                 | 0.002    | 1.173             | 0.002    | 1.173       | 0.002    |
| <b>Geometric average</b> | 1              | -        | 1.004           | -        | 1.000             | -        | 1.191             | -        | 1.195       | -        |

Table 4: User mode run-time (utime) and standard deviation ( $\sigma$ ) in seconds for uninstrumented nbench tests, the pre-determined number of iterations for each individual test, and the number of run-time events that are affected by instrumentation. Non-leaf calls correspond to function invocations protected by return address signing. Leaf calls correspond to function invocations which do not store the value of LR in memory, and thus can be left uninstrumented. Instruction pointers created and indirect calls are instrumented by (forward-edge) code pointer signing, and data pointer loads / stores correspond to events where data pointer instrumentation is active.

| Test             | Baseline |          |            | Instrumented events |            |                     |                |                   |  |  |
|------------------|----------|----------|------------|---------------------|------------|---------------------|----------------|-------------------|--|--|
|                  | utime    | $\sigma$ | iterations | non-leaf calls      | leaf calls | instr. ptr. created | indirect calls | data ptr. ldr/str |  |  |
| Numeric sort     | 3.573    | 0.007    | 350        | 1802                | 7117598    | 10                  | 5              | 302212833         |  |  |
| String sort      | 2.971    | 0.005    | 125        | 3977237             | 1022510    | 10                  | 5              | 180105579         |  |  |
| Bitfield         | 2.687    | 0.004    | 101647890  | 5669                | 4308       | 10                  | 5              | 104670943         |  |  |
| FP emulation     | 5.862    | 0.004    | 35         | 616536              | 37906118   | 10                  | 5              | 589518589         |  |  |
| Fourier          | 2.693    | 0.005    | 25870      | 5240188             | 161        | 10                  | 5              | 27504             |  |  |
| Assignment       | 4.414    | 0.005    | 10         | 225602              | 113353     | 10                  | 5              | 190662093         |  |  |
| Idea             | 2.808    | 0.004    | 1500       | 1640184             | 54420196   | 10                  | 5              | 196844406         |  |  |
| Huffman          | 4.212    | 0.005    | 1000       | 17659               | 46983276   | 10                  | 5              | 343176061         |  |  |
| Neural net       | 5.477    | 0.007    | 10         | 359423              | 441412     | 10                  | 5              | 782               |  |  |
| Lu decomposition | 3.596    | 0.005    | 230        | 18970               | 441412     | 10                  | 5              | 186704928         |  |  |

## C ARMv8-A PA Instructions

Table 5: List of PA instructions referred to in the main paper [3]. *PA Key* indicates the PA key the instruction uses. *Addr.* indicates the source of the address to be signed / authenticated (*Xd* indicates that the address is specified using a general purpose register). *Mod.* indicates the modifier used by the instruction (*Xm* indicates that the modifier is specified by a general purpose register.) The *backwards-compatible* column indicates if the instruction encoding resides in the NOP space for pre-existing ARMv8-A processors.

| Instruction                                                   | Mnemonic | PA Key          |               |              | Addr. | Mod. | Backwards-compatible |
|---------------------------------------------------------------|----------|-----------------|---------------|--------------|-------|------|----------------------|
|                                                               |          | Instr.<br>A   B | Data<br>A   B | Gen-<br>eric |       |      |                      |
| <strong>BASIC POINTER AUTHENTICATION INSTRUCTIONS</strong>    |          |                 |               |              |       |      |                      |
| Add PAC to instr. addr.                                       | pciasp   | ✓               |               |              | LR    | SP   | ✓                    |
|                                                               | pcia     | ✓               |               |              | Xd    | Xm   | ✓                    |
|                                                               | pcibsp   |                 | ✓             |              | LR    | SP   | ✓                    |
|                                                               | pcib     |                 | ✓             |              | Xd    | Xm   | ✓                    |
| Add PAC to data addr.                                         | pcda     |                 | ✓             | ✓            | Xd    | Xm,  | ✓                    |
|                                                               | pcdb     |                 |               |              | Xd    | Xm   | ✓                    |
| Calculate generic MAC                                         | pcga     |                 |               |              | ✓     |      | ✓                    |
| Authenticate instr. addr.                                     | autiasp  | ✓               |               |              | LR    | SP   | ✓                    |
|                                                               | autia    | ✓               |               |              | Xd    | Xm   | ✓                    |
|                                                               | autibsp  |                 | ✓             |              | LR    | SP   | ✓                    |
|                                                               | autib    |                 | ✓             |              | Xd    | Xm   | ✓                    |
| Authenticate data addr.                                       | autda    |                 | ✓             | ✓            | Xd    | Xm,  | ✓                    |
|                                                               | autdb    |                 |               |              | Xd    | Xm   | ✓                    |
| <strong>COMBINED POINTER AUTHENTICATION INSTRUCTIONS</strong> |          |                 |               |              |       |      |                      |
| Authenticate instr. addr.<br>and return                       | retaa    | ✓               | ✓             |              | LR    | SP   | ×                    |
|                                                               | retab    |                 |               |              | LR    | SP   | ×                    |
| Authenticate instr. addr.<br>and branch                       | braa     | ✓               | ✓             |              | Xd    | Xm   | ×                    |
|                                                               | brab     |                 |               |              | Xd    | Xm   | ×                    |
| Authenticate instr. addr.<br>and branch with link             | blraa    | ✓               |               |              | Xd    | Xm   | ×                    |
|                                                               | blrab    |                 | ✓             |              | Xd    | Xm   | ×                    |
| Authenticate instr. addr.<br>and exception return             | eretaa   | ✓               |               |              | ELR   | SP   | ×                    |
|                                                               | eretab   |                 | ✓             |              | ELR   | SP   | ×                    |
| Authenticate data. addr.<br>and load register                 | ldraa    |                 |               | ✓            | Xd    | zero | ×                    |
|                                                               | ldrab    |                 |               | ✓            | Xd    | zero | ×                    |