

![Arm logo](2dfa6ac3edfe874f68aa0cbccaa42322_img.jpg)

Arm logo

SC17 Arm SVE Workshop

# Introducing the Armv8-A Scalable Vector Extension

Neil Burgess

Denver, CO

16 November 2017

## Why is it called Scalable Vector Extension?

SVE is not a simple extension of AArch64 Advanced SIMD (“NEON”)

- A separate, optional architectural extension with a new set of instruction encodings.
- Initial focus is HPC and general-purpose server software, not media/image processing.

SVE does not mandate a single, fixed vector length

- Vector Length (VL) is hardware implementation choice of 128 to 2048 bits.
- Vector Length Agnostic (VLA) programming paradigm adapts to the available vector length.

SVE begins to address traditional barriers to auto-vectorization

- Compilers often cannot vectorize due to intra-vector control and data dependencies.
- Software-managed speculative vectorization allows more loops to be vectorized by a compiler.

## Introducing the Scalable Vector Extension (SVE)

A vector extension to the Armv8-A architecture with some major new features

### Gather-load and scatter-store

- Loads a single register from several non-contiguous memory locations.
- Enables vectorization of complex data structures with non-linear access patterns.

![Diagram illustrating gather-load and scatter-store operations. Four arrows point from memory locations to a single vector register, showing non-contiguous access.](48f188337e3ba41df38fab9ac0afb1bd_img.jpg)

Diagram illustrating gather-load and scatter-store operations. Four arrows point from memory locations to a single vector register, showing non-contiguous access.

### Per-lane predication

- Operations work on individual lanes under control of a predicate register.
- Enables vectorization of complex, nested control code containing side effects.

|      | 1 | 2 | 3 | 4 |
|------|---|---|---|---|
| +    | 5 | 5 | 5 | 5 |
| pred | 1 | 0 | 1 | 0 |
| =    | 6 | 2 | 8 | 4 |

### Predicate-driven loop control and management

- Eliminate loop heads and tails and other overhead by processing partial vectors.
- Reduces vectorization overhead relative to scalar code.

```
for (i = 0; i < n; ++i)  
INDEX i n-2 n-1 n n+1  
CMPLT n 1 1 0 0
```

### Vector partitioning and software-managed speculation

- First-faulting vector load instructions allow memory accesses to cross into invalid pages.

![](9bce5f32731f4bc988d83174aa34a60e_img.jpg)

|      | 1 | 2 |   |   |
|------|---|---|---|---|
| +    | 1 | 2 | 0 | 0 |
| pred | 1 | 1 | 0 | 0 |

### New SVE architectural state

## Scalable vector registers

- Z0-Z31 extending NEON's V0-V31.
- Packed DP, SP & HP floating-point elements.
- Packed 64, 32, 16 & 8-bit integer elements.

![](f961cbef0f8217e216b553bed270315b_img.jpg)

Diagram illustrating the Scalable Vector Extension (SVE) vector registers Z0-Z31. The registers are shown as horizontal bars. The total width is labeled  $\text{LEN} \times 128$ . The rightmost portion of each register is labeled 128, corresponding to the V registers (V0, V1, V2, V31). The registers are Z31, Z2, Z1, and Z0, corresponding to V31, V2, V1, and V0 respectively.

### Scalable predicate registers

- P0-P7 governing predicates for load/store/arithmetic.
- P8-P15 additional predicates for loop management.
- FFR first fault register for speculation.

![](954ff3c220707f98bcb2c4b197bd7d9f_img.jpg)

Diagram illustrating the Scalable Predicate Registers (P0-P15). The registers are shown as horizontal bars. The total width is labeled  $\text{LEN} \times 16$ . The registers are P7, P2, P1, P0 (teal bars) and P15, P10, P9, P8 (purple bars). The FFR (First Fault Register) is also shown as a purple bar.

### Scalable vector control registers

- ZCR\_ELx vector length ( $\text{LEN}=1..16$ ).
- For exception/privilege levels EL1 to EL3.

![](846242b2850d88b17a6d47cd9dd0ccbf_img.jpg)

Diagram illustrating the Scalable Vector Control Registers (ZCR). The ZCR register is shown as a stack of four registers, labeled ZCR. The width of each register is labeled  $\text{LEN}$ . The registers are associated with exception/privilege levels EL1, EL2, and EL3, indicated by arrows pointing to the corresponding  $\text{LEN}$  labels.

### Predication

16 predicate registers defined (P0-P15)

- 1 bit per lane  $\therefore$  1 predicate bit per 8 vector bits (lowest predicate bit per lane is significant)

Active elements update destination

- inactive lanes leave destination unchanged or set to 0's
- power-saving opportunities

$\approx$ 6% SVE instructions act on and return predicates  $\to$  “Predicate ALU”

| 255 | 192 191 |   | 128 127 |   | 64 63 |   | 0   |
|-----|---------|---|---------|---|-------|---|-----|
|     | 64b     |   | 64b     |   | 64b   |   | 64b |
|     | I       |   | I       |   | I     |   | I   |
| 31  | 24 23   |   | 16 15   |   | 8 7   |   | 0   |
|     | 32b     |   | 32b     |   | 32b   |   | 32b |
|     | 0       | 0 | 0       | I | I     | I | I   |

### SVE instruction breakdown

1400 opcodes (cf 5000 AArch32 A32/T32; 4000 AArch64 A64; 1200 NEON)

- # opcodes includes element size but excludes immediates, regID's
  - SVE: A64 opcode[28:25] = 4'b0010
  - 130 basic operation “types”
  - 50% already in NEON
  - 30% “sort of” already in NEON

![](46f43cb4ffd47565e7c0ca306d461435_img.jpg)

Pie chart illustrating the breakdown of SVE instructions:

- Float (12%)
- Load/Store (29%)
- Integer (59%)

### SVE integer MUL/MAC operations

| Instruction | src's & dst                                                                  | Notes                                                                                                                                      |
|-------------|------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| MUL         | Zds1, Zs2 / Pg -> Zds1,<br>Zds1, immS2 -> Zds1                               | 8-b signed immediate                                                                                                                       |
| MLA, MLS    | Zs1, Zs2, Zds3 / Pg -> Zds3                                                  | overwrite addend                                                                                                                           |
| MAD, MSB    | Zds1, Zs2, Zs3 / Pg -> Zds1                                                  | overwrite multiplicand                                                                                                                     |
| [SU]MULH    | Zds1, Zs2 / Pg -> Zds1                                                       | 16-b & 32-b only <u>SQDMULH</u> in NEON                                                                                                    |
| INDEX       | immS1, immS2 -> Zd<br>immS1, Rs2 -> Zd<br>Rs1, immS2 -> Zd<br>Rs1, Rs2 -> Zd | Zd = s1 + (n × s2): n = 0 ... #elems - 1)<br>Useful for constructing vector addresses<br>5-b unsigned immediates; 32-b or 64-b GPSR values |

MAC: 48 opcodes, 4 “basic” types; none new

≈28 genuinely new types: LSU, PERM, vector and scalar ALU's, FPU

### Differences between SVE and NEON

### Load/Store

- Vectors used for addressing (gather/scatter)
- Predicated
- First-faulting behaviour
- Non-temporal
- Retain NEON “structured” load/stores

#### Speculative first-fault loads using FFR

Speculative gather from addresses in Z3

- **SETFFR**: initialises FFR to all TRUE
- A[2] is a **Bad** (e.g. unmapped) address

**Initial state**

P1

| T    | T   | T    | T    |
|------|-----|------|------|
| A[3] | Bad | A[1] | A[0] |
| T    | T   | T    | T    |

Z3

FFR

### SVE predicate condition flags

Overloads the ARM NZCV condition flags (reuse Aarch64 branch instructions)

More flag-setting instructions in SVE than NEON

- Vector compares set SVE flags

Logic for N and C identical to carry out from adder

| Flag | SVE   | Condition                                        |
|------|-------|--------------------------------------------------|
| N    | First | Set if first active predicate element is true    |
| Z    | None  | Set if no active predicate elements are true     |
| C    | !Last | Cleared if last active predicate element is true |
| V    | n/a   | Set to zero by most SVE instructions             |

#### Scalar strlen()

```
// --------------------------------
// int strlen(const char *s) {
//     const char *e = s;
//     while (*e) e++;
//     return e - s;
// }
// --------------------------------
// x0 = s
```

// Unoptimized A64 scalar strlen  
strlen:

```
mov x1, x0 // e=s
.loop:
    ldrb x2, [x1], #1 // x2=*e++
    cbnz x2, .loop // while(*e)
.done:
    sub x0, x1, x0 // e-s
    sub x0, x0, #1 // return e-s-1
    ret
```

#### SVE strlen()

```
// --------------------------------
// int strlen(const char *s) {
//     const char *e = s;
//     while (*e) e++;
//     return e - s;
// }
// --------------------------------
// x0 = s
```

// Unoptimized SVE strlen  
strlen:

```
mov x1, x0 // e=s
ptrue p0.b // p0=true
.loop:
    setffr // ffr=true
    ldiffb z0.b, p0/z, [x1] // p0:z0=ldff(e)
    rdffr p1.b, p0/z // p0:p1=ffr
    cmpeq p2.b, p1/z, z0.b, #0 // p1:p2=(*e==0)
    brkbs p2.b, p1/z, p2.b // p1:p2=until(*e==0)
    incp x1, p2.b // e+=popcnt(p2)
    b.last .loop // last active=>!break
    sub x0, x1, x0 // return e-s
    ret
```

### More on Predication

### Other instructions that update predicates

- Vector compares return predicates
- WHILE instructions operate on two GPRs & return predicates
- Most predicate-generating instructions also write the NZCV condition flags
- Load/Store read predicates

## Hardware impact: predication mostly doesn't affect execution

- can be implemented away from datapaths to share logic (muxes, operand staging)
- but sometimes it does e.g. vector reduction

## HPC benchmarks SVE vs. NEON

![](2236272d3b3db6e6363337f5a8db72f6_img.jpg)

Bar chart showing the "Increase in vectorisation" (left Y-axis, 0% to 80%) and line chart showing "Speedup" (right Y-axis, 1.0 to 9.0) for various HPC benchmarks comparing SVE 128b + Vector% (grey bars) against SVE 128b Speedup (blue line), SVE 256b Speedup (red line), and SVE 512b Speedup (green line).

The benchmarks tested are: hpgrng\_finite-volume, NPB-3p0\_FT, NPB-3p0\_MG, asc\_seqoia\_irsrk, himenobmt, torch\_denseLinearAlgebra, and asc\_coral\_hacmk.

Approximate data extracted from the chart:

| Benchmark                | SVE 128b + Vector% | SVE 128b Speedup | SVE 256b Speedup | SVE 512b Speedup |
|--------------------------|--------------------|------------------|------------------|------------------|
| hpgrng_finite-volume     | 45%                | 5%               | 10%              | 10%              |
| NPB-3p0_FT               | 50%                | 5%               | 10%              | 15%              |
| NPB-3p0_MG               | 55%                | 10%              | 15%              | 20%              |
| asc_seqoia_irsrk         | 75%                | 10%              | 20%              | 30%              |
| himenobmt                | 70%                | 15%              | 25%              | 45%              |
| torch_denseLinearAlgebra | 55%                | 20%              | 35%              | 60%              |
| asc_coral_hacmk          | 65%                | 25%              | 45%              | 75%              |

### SVE impact on CPU with NEON

![](0b8b087a7baa471015d3ffeaa43d9a6c_img.jpg)

Diagram illustrating the SVE impact on CPU with NEON, showing the interaction between scalar and vector components.

The diagram features several registers and processing units:

- **Scalar RegFile (GPR)** and **Vector RegFile (VRF)** are connected to **LSU** and **IALU**.
- **IALU** is connected to **Flags**.
- **LSU** is connected to **Flags** and **Vector RegFile (VRF)**.
- **Vector RegFile (VRF)** is connected to **Scalar RegFile (GPR)**, **LSU**, **Predicate RegFile (PRF)**, and the **NEON execution units**.
- **Predicate RegFile (PRF)** is connected to **P-ALU** and **Flags**.
- **P-ALU** is connected to **Flags**.

The **NEON execution units** (VALU, VSHF, VMAC, PERM, IDIV, FMUL, FADD, FCVT, FDIV) are shown below the main register file structure, indicating they are the primary processing units for SVE operations.

### SVE impact on area of vector execution units

| Unit | Area Increase | New SVE functionality           |
|------|---------------|---------------------------------|
| VSHF | 145%          | ASRD, “wide” shfamt             |
| VMAC | 163%          | 64-b elements, INDEX            |
| VALU | 215%          | “wide CMP”, NZCV logic, new ADR |
| PERM | 418%          | 12 new “basic” operations       |

### NEON 128-b vs SVE 256-b

- Double-size vectors → 100% area increase
- extra functionality & muxing; timing pressure

### PERM block

- 256-b crossbar >5x area of 128-b
- Major increase in # op types executed

FPU area increase ≈100% (2x # units)

Overall execution area increase ≈ 2.2x

Overall CPU area increase ≈ 15%

- Decoder area increase of ≈4%
- Power increase broadly similar to area

Thank You!

Danke!

Merci!

谢谢!

ありがとう!

Gracias!

Kiitos!

arm