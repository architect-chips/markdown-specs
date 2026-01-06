

arm Research

# Vector Processing with Arm SVE

Alex Rico

Staff Research Engineer

# 70%

of the world's population  
uses Arm technology

![Decorative plus sign marker](61972112770d9c8fb00883057954f885_img.jpg)

Decorative plus sign marker

## A continuous partnership model

Arm develops technology that is licensed to semiconductor companies.

Arm receives an upfront license fee and a royalty on every chip that contains its technology.

![](e863446d7d263c68be9402afd63668ac_img.jpg)

Diagram illustrating the continuous partnership model:

- **Arm** licenses **Technology** to **SemiCo Partner**.
- **SemiCo Partner** receives a **License Fee** from **Arm**.
- **SemiCo Partner** develops chips.
- **OEM Customer** receives chips from **SemiCo Partner**.
- **OEM Customer** sells consumer products.
- **Arm** receives **Per Chip Royalty** from **OEM Customer**.
- The entire process is overseen by **Business Development**.

## The architects of global possibilities

The global leader in the development of licensable technology

- R&D outsourcing for semiconductor companies

Focused on freedom and flexibility to innovate

- Technology reused across multiple applications

With a partnership based culture & business model

- Licensees take advantage of learnings from a uniquely collaborative ecosystem

**>1,400**

licenses, growing by  
>100 every year

**17.7bn**

Arm-based chips  
shipped in FY2016

**>460**  
licensees

Industry leaders and high-growth  
start-ups; chip companies and OEMs

### From inception to now

1990

Joint venture between  
Acorn Computers and Apple.

![Image showing an Acorn Archimedes computer and an Apple Newton PDA.](17a042ee648d9fdaddb609aead503980_img.jpg)

Image showing an Acorn Archimedes computer and an Apple Newton PDA.

![Image showing three mobile phones: a flip phone, a feature phone, and a smartphone.](8e065eabc40a3645a569db7e9cd0da32_img.jpg)

Image showing three mobile phones: a flip phone, a feature phone, and a smartphone.

Designed into first  
mobile phones and  
then smartphones.

1993  
onwards

Today

Now all electronic  
devices can use  
intelligent Arm  
technology.

![Image showing a variety of modern electronic devices including a car, laptop, smartwatch, TV, and various sensors.](04519be9bd73b202914a1bb3da732edd_img.jpg)

Image showing a variety of modern electronic devices including a car, laptop, smartwatch, TV, and various sensors.

The road ahead  
is exciting

![](c54b3ca7603d65d4589151bc3a49d054_img.jpg)

Timeline showing chip shipment milestones:

- 1991: 26 years
- 2017: 100 billion chips shipped
- 2021: 4 years! 100 billion chips shipped

### Distributing intelligence from edge to cloud

![Icon representing on-device learning, showing a location pin inside a smartphone.](9ebd85380ef496499e5f23ec0d9cd744_img.jpg)

Icon representing on-device learning, showing a location pin inside a smartphone.

On-device learning for enhanced user privacy

![Icon representing compute performance, showing a laptop.](c1c7af7ea36be0323047962df57d75b0_img.jpg)

Icon representing compute performance, showing a laptop.

Compute performance to deliver a hi-fidelity world

![Icon representing real-time inference, showing a circuit board or processor.](67b83c4adaaa4de02d367168308deb2a_img.jpg)

Icon representing real-time inference, showing a circuit board or processor.

Real-time inference for autonomous systems

![Icon representing security and privacy, showing a fingerprint.](f3e03accc76df483950e65a9fb19c20e_img.jpg)

Icon representing security and privacy, showing a fingerprint.

Security and privacy for your data

![Icon representing human-like interfaces, showing a monitor with a stylized eye or sunburst pattern.](48d61f7cf40bacce4d63f9e98ea225fb_img.jpg)

Icon representing human-like interfaces, showing a monitor with a stylized eye or sunburst pattern.

4k, HDR and 5G for more human-like interfaces

### Enabling ubiquitous mobile compute at the edge

- The world's primary compute device
- Expanding Arm mobile leadership
- Advanced graphics within mobile power budgets
- Blazing a path toward secure, always 5G connectivity

**No. 1**

shipped GPU in the world

**20+bn**

Arm-based cellular modems shipped to-date

**100x**

compute increase since 2009

**95%**

of the world's smartphones are based on Arm

## The architecture of choice for the internet of things

1 **trillion** connected devices are expected to ship between now and **2035**

## 10mn

Arm-based Raspberry Pi devices have shipped to-date

## 50%

of Arm chips shipped in FY16 (17+bn) into diverse embedded devices

## 90%

of wearables powered by Arm-based SoCs

## 70%

share of rich embedded devices occupied by Arm-based SoCs

## 55%

of consumer devices are powered by Arm IP

## Providing a platform for secure, connected & living vehicles

Innovating across a common  
Arm platform for automotive

### Arm in automotive today

- More than 25% of SoCs for ADAS applications based on Arm
- 85% of IVI systems are Arm-based

### Building a foundation for secure, autonomous driving

- SoCs designed with functional safety for self-driving vehicles
- Proven and trusted technology for end-to-end security

### Protecting billions of devices today

### arm Trust Zone Security System

![A person using a smartphone for contactless payment (NFC) at a point-of-sale terminal.](6d9013c24741e861f3c8e0a763b6da22_img.jpg)

A person using a smartphone for contactless payment (NFC) at a point-of-sale terminal.

PSA

![A person holding a smartphone, suggesting mobile security or enterprise security.](d29cfbf30a471dc06a78be27f86bd1cf_img.jpg)

A person holding a smartphone, suggesting mobile security or enterprise security.

Enterprise  
Security

![A hand holding a remote control, suggesting content protection or access control.](2de51a31da9b0ffd9d017f035d498997_img.jpg)

A hand holding a remote control, suggesting content protection or access control.

Content  
Protection

![A close-up of a human eye with digital targeting lines, symbolizing authentication.](8c49beafe7c55ea578abcaee4bdca0ba_img.jpg)

A close-up of a human eye with digital targeting lines, symbolizing authentication.

Authentication

## Scalable Vector Extension

### Arm Architecture

Armv7 Advanced SIMD (aka Arm NEON instructions)  
now 12 years old

- Integer, fixed-point and non-IEEE single-precision float
- 16 × 128-bit vector registers

AArch64 Advanced SIMD was an evolution

- Gained full IEEE double-precision float and 64-bit integer vector ops
- 32 × 128-bit vector registers

![](8791f79b259a7463279c1aeb14c31580_img.jpg)

Diagram illustrating the evolution of Arm architectures and associated features:

- ARMv5: VFPv2, Jazelle®
- ARMv6: Thumb®-2, TrustZone®, SIMD
- ARMv7-A/R: VFPv3/v4, NEON™ Adv SIMD
- ARMv8-A: A32+T32 ISAs (including: Scalar FP (SP and DP), Adv SIMD (SP Float)), A64 ISA (including: Scalar FP (SP and DP), Adv SIMD (SP+DP Float))

Key feature: ARMv7-A compatibility

### Scalable Vector Extension – SVE

Significantly extends vector processing capabilities of AArch64

Enables implementation choices of vector lengths – **128 to 2048 bits**

- *Vector Length Agnostic (VLA)* programming adjusts dynamically to the available VL
- No need to recompile, or to rewrite hand-coded SVE assembler or C intrinsics

Focus is HPC scientific workloads and machine learning, not media/image processing

Will enable advanced vectorizing compilers to extract more fine-grain parallelism from existing code and so reduce software deployment effort

#### Post-K Supercomputer goes Arm with SVE

#### A64FX Chip Overview

#### ■ Architecture Features

- Armv8.2-A (AArch64 only)
- SVE 512-bit wide SIMD
- 48 computing cores + 4 assistant cores\*  
  \*All the cores are identical
- HBM2 32GiB
- Tofu 6D Mesh/Torus 28Gbps x 2 lanes x 10 ports
- PCIe Gen3 16 lanes

![](fe753d01ad5fe6cf150018c958173c6d_img.jpg)

**<A64FX>**

Diagram illustrating the A64FX chip architecture:

- CMG specification: 13 cores, L2S 8MiB, Mem 8GiB, 256GB/s
- Tofu: 28Gbps, 2 lanes, 10 ports
- I/O: PCIe Gen3, 16 lanes
- Components include Tofu controller, PCIe controller, Network on Chip, and HBM2 memory blocks.

#### ■ 7nm FinFET

- 8,786M transistors
- 594 package signal pins

#### ■ Peak Performance (Efficiency)

- >2.7TFLOPS (>90%@DGEMM)
- Memory B/W 1024GB/s (>80%@Stream Triad)

|                  | A64FX (Post-K) | SPARC64 Xifx (PRIMEHPC FX100) |
|------------------|----------------|-------------------------------|
| ISA (Base)       | Armv8.2-A      | SPARC-V9                      |
| ISA (Extension)  | SVE            | HPC-ACE2                      |
| Process Node     | 7nm            | 20nm                          |
| Peak Performance | >2.7TFLOPS     | 1.1TFLOPS                     |
| SIMD             | 512-bit        | 256-bit                       |
| # of Cores       | 48+4           | 32+2                          |
| Memory           | HBM2           | HMC                           |
| Memory Peak B/W  | 1024GB/s       | 240GB/s x2 (in/out)           |

All Rights Reserved. Copyright © FUJITSU LIMITED 2018

![Image of a Fujitsu supercomputer rack, featuring a red panel with the Fujitsu logo and the text 'K computer'.](ded1520e45c0c3e4c46c58984602bf0e_img.jpg)

Image of a Fujitsu supercomputer rack, featuring a red panel with the Fujitsu logo and the text 'K computer'.

slides from Fujitsu

### Introducing the Scalable Vector Extension (SVE)

A vector extension to the ARMv8-A architecture with some major new features:

![Diagram illustrating Gather-load and scatter-store. Four memory locations are shown above a vector register, with arrows indicating data flow from the memory locations into the vector register lanes.](83926108dd52e3998fda7a99a91cdf3b_img.jpg)

Diagram illustrating Gather-load and scatter-store. Four memory locations are shown above a vector register, with arrows indicating data flow from the memory locations into the vector register lanes.

#### Gather-load and scatter-store

Loads a single register from several non-contiguous memory locations.

|             | 1 | 2 | 3 | 4 |
|-------------|---|---|---|---|
| +           | 5 | 5 | 5 | 5 |
| <i>pred</i> | 1 | 0 | 1 | 0 |
| =           | 6 | 2 | 8 | 4 |

#### Per-lane predication

Operations work on individual lanes under control of a predicate register.

```
for (i = 0; i < n; ++i)  
INDEX i n-2 n-1 n n+1  
CMPLT n 1 1 0 0
```

#### Predicate-driven loop control and management

Eliminate scalar loop heads and tails by processing partial vectors.

### Introducing the Scalable Vector Extension (SVE)

A vector extension to the ARMv8-A architecture with some major new features:

![](f4d72193f77f6646a2a1f4baaa927154_img.jpg)

Diagram illustrating vector partitioning and software-managed speculation. A vector register is shown partitioned into segments (blue, white, orange). The white segment is further divided into elements 1 and 2. Below, the operation  $pred$  (prediction) is shown, where elements 1 and 2 are used to generate the prediction values 1 and 1, respectively, while the remaining elements are 0.

#### Vector partitioning and software-managed speculation

First Faulting Load instructions allow memory accesses to cross into invalid pages.

$$\begin{array}{cccc} \boxed{1} + \boxed{2} + \boxed{3} + \boxed{4} = \\ \boxed{1} + \boxed{2} \quad \boxed{3} + \boxed{4} \\ = \quad = \\ \boxed{3} + \boxed{7} = \end{array}$$

#### Extended floating-point horizontal reductions

In-order and tree-based reductions trade-off performance and repeatability.

### What's the vector length?

There is **no** preferred vector length

- Vector Length (VL) is the CPU **implementor's choice**, from 128 to 2048 bits, in increments of 128
- Adopting a **Vector Length Agnostic (VLA)** code generation style makes code portable across all possible vector lengths
- **VLA** is made possible by the per-lane predication, predicate-driven loop control, vector partitioning and software-managed speculation features of SVE
- **No need to recompile**, or to rewrite hand-coded SVE assembler or C intrinsics

![](1a6a826cc13d4e964b7bda69508d78e6_img.jpg)

Diagram illustrating Vector Length (VL) options:

- 128b: 0, 64, 128
- 256b: 0, 128, 256
- 384b: 0, 128, 256, 384
- 512b: 0, 128, 256, 384, 512

VL

#### SVE – architectural state

- Scalable vector registers
  - Z0-Z31 extending NEON's V0-V31
    - DP & SP floating-point
    - 64, 32, 16 & 8-bit integer
- Scalable predicate registers
  - P0-P7 lane masks for ld/st/arith
  - P8-P15 for predicate manipulation
  - FFR *first fault register*
- Scalable vector control registers
  - ZCR\_ELx vector length (LEN=1..16)
  - Exception / privilege level EL1 to EL3

![](7bed2d7c96d86bf922295a1252da52a5_img.jpg)

Diagram illustrating the SVE architectural state, showing the organization of registers:

- **Scalable Vector Registers (Z0-Z31):** These registers are shown as blue blocks. The top register, Z31, is associated with V31. The register Z0 is associated with V0. The diagram indicates a length of  $LEN \times 128$  for the top section, and a length of 128 for the bottom section.
- **Scalable Predicate Registers (P0-P15, FFR):** These registers are shown as colored blocks. P0-P7 are associated with orange blocks, and P8-P15 are associated with green blocks. The FFR (First Fault Register) is also a green block. The diagram indicates a length of  $LEN \times 16$  for the top section.
- **Scalable Vector Control Registers (ZCR):** These registers are shown as yellow blocks labeled ZCR. They are associated with the exception/privilege levels EL1 and EL3, and the vector length (LEN).

### SVE Visual Examples

#### daxpy (scalar)

```
void daxpy(double *x, double *y, double a, int n)
{
    for (int i = 0; i < n; i++) {
        y[i] = a * x[i] + y[i];
    }
}
```

```
// x0 = &x[0]
// x1 = &y[0]
// x2 = &a
// x3 = &n
daxpy_:
    ldrsw      x3, [x3]
    mov        x4, #0
    ldr        d0, [x2]
    b          .latch
.loop:
    ldr        d1, [x0, x4, ls1 #3]
    ldr        d2, [x1, x4, ls1 #3]
    fmadd      d2, d1, d0, d2
    str        d2, [x1, x4, ls1 #3]
    add        x4, x4, #1
.latch:
    cmp        x4, x3
    b.lt       .loop
    ret
```

#### daxpy (SVE)

#### daxpy (scalar)

Loop fiberization: pulling multiple scalar iterations into a vector

```
daxpy_:
    ldrsw x3, [x3]
    mov x4, #0
    whilelt p0.d, x4, x3
    ld1rd z0.d, p0/z, [x2]
    .loop:
        ld1d z1.d, p0/z, [x0, x4, ls1 #3]
        ld1d z2.d, p0/z, [x1, x4, ls1 #3]
        fmla z2.d, p0/m, z1.d, z0.d
        st1d z2.d, p0, [x1, x4, ls1 #3]
        incd x4
    .latch:
        whilelt p0.d, x4, x3
        b.first .loop
        ret
```

```
daxpy_:
    ldrsw x3, [x3]
    mov x4, #0
    ldr d0, [x2]
    b .latch
    .loop:
        ldr d1, [x0, x4, ls1 #3]
        ldr d2, [x1, x4, ls1 #3]
        fmadd d2, d1, d0, d2
        str d2, [x1, x4, ls1 #3]
        add x4, x4, #1
    .latch:
        cmp x4, x3
        b.lt .loop
        ret
```

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilet p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilet p0.d, x4, x3  
    b.first .loop  
    ret
```

![](a289b64f80c6df506c0c55d553fc4496_img.jpg)

|        | 256 | ... | 128 | 64  |
|--------|-----|-----|-----|-----|
| x0     |     |     |     | &x  |
| x1     |     |     |     | &y  |
| x3     |     |     |     | 3   |
| x4     |     |     |     | 0   |
| p0     |     |     |     | T T |
| z0     |     |     |     |     |
| z1     |     |     |     |     |
| z2     |     |     |     |     |
| CYCLES | 2   |     |     |     |

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 0   |
| p0 |     |     |     | T T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilet p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilet p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
|     |     |
|     |     |

CYCLES 3

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 0   |
| p0 |     |     |     | T T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
|     |     |

CYCLES 4

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 0   |
| p0 |     |     |     | T T |

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
| 0.0 | 0.0 |

CYCLES 5

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 0   |
| p0 |     |     |     | T T |

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
| 2.0 | 0.0 |

CYCLES 6

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 0   |
| p0 |     |     |     | T T |

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
| 2.0 | 0.0 |

CYCLES 7

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 2   |
| p0 |     |     |     | T T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
    .loop:  
        ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
        ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
        fm1a z2.d, p0/m, z1.d, z0.d  
        st1d z2.d, p0, [x1,x4,ls1 #3]  
        incd x4  
    .latch:  
        whilelt p0.d, x4, x3  
        b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
| 2.0 | 0.0 |

CYCLES 8

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

| 256 | ... | 128 | 64  |
|-----|-----|-----|-----|
| x0  |     |     | &x  |
| x1  |     |     | &y  |
| x3  |     |     | 3   |
| x4  |     |     | 2   |
| p0  |     |     | F T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilet p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilet p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
| 2.0 | 0.0 |

CYCLES 9

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

| 256 | ... | 128 | 64  |
|-----|-----|-----|-----|
| x0  |     |     | &x  |
| x1  |     |     | &y  |
| x3  |     |     | 3   |
| x4  |     |     | 2   |
| p0  |     |     | F T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 1.0 | 0.0 |
| 2.0 | 0.0 |

CYCLES 10

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

| 256 | ... | 128 | 64  |
|-----|-----|-----|-----|
| x0  |     |     | &x  |
| x1  |     |     | &y  |
| x3  |     |     | 3   |
| x4  |     |     | 2   |
| p0  |     |     | F T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilet p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilet p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 2.0 | 0.0 |

CYCLES 11

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 2   |
| p0 |     |     |     | F T |

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 0.0 |

CYCLES 12

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 2 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
    .loop:  
        ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
        ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
        fmla z2.d, p0/m, z1.d, z0.d  
        st1d z2.d, p0, [x1,x4,ls1 #3]  
        incd x4  
    .latch:  
        whilelt p0.d, x4, x3  
        b.first .loop  
    ret
```

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 2   |
| p0 |     |     |     | F T |

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 4.0 |

CYCLES 13

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

| 256 | ... | 128 | 64  |
|-----|-----|-----|-----|
| x0  |     |     | &x  |
| x1  |     |     | &y  |
| x3  |     |     | 3   |
| x4  |     |     | 2   |
| p0  |     |     | F T |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 4.0 |

CYCLES 14

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 4   |
| p0 |     |     |     | F T |

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 4.0 |

CYCLES 15

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 4   |
| p0 |     |     |     | F F |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilet p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilet p0.d, x4, x3  
    b.first .loop  
    ret
```

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 4.0 |

CYCLES 16

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 4   |
| p0 |     |     |     | F F |

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 4.0 |

CYCLES 17

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

#### daxpy (SVE – 128b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

|    | 256 | ... | 128 | 64  |
|----|-----|-----|-----|-----|
| x0 |     |     |     | &x  |
| x1 |     |     |     | &y  |
| x3 |     |     |     | 3   |
| x4 |     |     |     | 4   |
| p0 |     |     |     | F F |

| 2.0 | 2.0 |
|-----|-----|
| 0.0 | 2.0 |
| 0.0 | 4.0 |

CYCLES 18

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

#### daxpy (SVE – 256b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

![](cfc852835f2d91bea8dc074568937e22_img.jpg)

|        | 256 | ... | 128 | 64      |
|--------|-----|-----|-----|---------|
| x0     |     |     |     | &x      |
| x1     |     |     |     | &y      |
| x3     |     |     |     | 3       |
| x4     |     |     |     | 0       |
| p0     |     |     |     | F T T T |
| z0     |     |     |     |         |
| z1     |     |     |     |         |
| z2     |     |     |     |         |
| CYCLES | 2   |     |     |         |

#### daxpy (SVE – 256b)

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fm1a z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

![](516d9f1866cc2e359a35fb1d8c046454_img.jpg)

|        | 256 | ... | 128 | 64              |
|--------|-----|-----|-----|-----------------|
| x0     |     |     |     | &x              |
| x1     |     |     |     | &y              |
| x3     |     |     |     | 3               |
| x4     |     |     |     | 0               |
| p0     |     |     |     | F T T T         |
| z0     |     |     |     | 0.0 2.0 2.0 2.0 |
| z1     |     |     |     |                 |
| z2     |     |     |     |                 |
| CYCLES | 3   |     |     |                 |

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

![](0892c0cb3b8502a44c4fe4e786be912a_img.jpg)

|    | 256 | ... | 128 | 64              |
|----|-----|-----|-----|-----------------|
| x0 |     |     |     | &x              |
| x1 |     |     |     | &y              |
| x3 |     |     |     | 3               |
| x4 |     |     |     | 0               |
| p0 |     |     |     | F T T T         |
| z0 |     |     |     | 0.0 2.0 2.0 2.0 |
| z1 |     |     |     | 0.0 2.0 1.0 0.0 |
| z2 |     |     |     |                 |

CYCLES 4

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

![](a85105fd544c64ef624aa45c72378647_img.jpg)

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 0       |
| p0 |     |     |     | F T T T |

|  | 0.0 | 2.0 | 2.0 | 2.0 |
|--|-----|-----|-----|-----|
|  | 0.0 | 2.0 | 1.0 | 0.0 |
|  | 0.0 | 0.0 | 0.0 | 0.0 |

CYCLES 5

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 0 | 0 | 0 |

![](c69f84a5cf3ebb8f0fc511e642d4c02a_img.jpg)

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 0       |
| p0 |     |     |     | F T T T |

|    | 0.0 | 2.0 | 2.0 | 2.0 |
|----|-----|-----|-----|-----|
| z0 | 0.0 | 2.0 | 1.0 | 0.0 |
| z1 | 0.0 | 4.0 | 2.0 | 0.0 |
| z2 | 0.0 | 4.0 | 2.0 | 0.0 |

CYCLES 6

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
    .loop:  
        ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
        ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
        fmla z2.d, p0/m, z1.d, z0.d  
        st1d z2.d, p0, [x1,x4,ls1 #3]  
        incd x4  
    .latch:  
        whilelt p0.d, x4, x3  
        b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 0       |
| p0 |     |     |     | F T T T |

|    | 0.0 | 2.0 | 2.0 | 2.0 |
|----|-----|-----|-----|-----|
| z0 | 0.0 | 2.0 | 1.0 | 0.0 |
| z1 | 0.0 | 2.0 | 1.0 | 0.0 |
| z2 | 0.0 | 4.0 | 2.0 | 0.0 |

CYCLES 7

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

![](068b3a3247570c4b78342a943f15de9e_img.jpg)

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 4       |
| p0 |     |     |     | F T T T |

|    | 0.0 | 2.0 | 2.0 | 2.0 |
|----|-----|-----|-----|-----|
| z0 | 0.0 | 2.0 | 1.0 | 0.0 |
| z1 | 0.0 | 2.0 | 1.0 | 0.0 |
| z2 | 0.0 | 4.0 | 2.0 | 0.0 |

CYCLES 8

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
    .loop:  
        ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
        ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
        fm1a z2.d, p0/m, z1.d, z0.d  
        st1d z2.d, p0, [x1,x4,ls1 #3]  
        incd x4  
    .latch:  
        whilelt p0.d, x4, x3  
        b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 4       |
| p0 |     |     |     | F F F F |

|    | 0.0 | 2.0 | 2.0 | 2.0 |
|----|-----|-----|-----|-----|
| z0 | 0.0 | 2.0 | 1.0 | 0.0 |
| z1 | 0.0 | 2.0 | 1.0 | 0.0 |
| z2 | 0.0 | 4.0 | 2.0 | 0.0 |

CYCLES 9

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ldlrd z0.d, p0/z, [x2]  
    .loop:  
        ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
        ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
        fm1a z2.d, p0/m, z1.d, z0.d  
        st1d z2.d, p0, [x1,x4,ls1 #3]  
        incd x4  
    .latch:  
        whilelt p0.d, x4, x3  
        b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

![](70ececdbb871824c3e57cace6262c4d6_img.jpg)

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 4       |
| p0 |     |     |     | F F F F |

|    | 0.0 | 2.0 | 2.0 | 2.0 |
|----|-----|-----|-----|-----|
| z0 | 0.0 | 2.0 | 1.0 | 0.0 |
| z1 | 0.0 | 2.0 | 1.0 | 0.0 |
| z2 | 0.0 | 4.0 | 2.0 | 0.0 |

CYCLES 10

#### daxpy (SVE – 256b)

```
daxpy_:  
    ldrsw x3, [x3]  
    mov x4, #0  
    whilelt p0.d, x4, x3  
    ld1rd z0.d, p0/z, [x2]  
.loop:  
    ld1d z1.d, p0/z, [x0,x4,ls1 #3]  
    ld1d z2.d, p0/z, [x1,x4,ls1 #3]  
    fmla z2.d, p0/m, z1.d, z0.d  
    st1d z2.d, p0, [x1,x4,ls1 #3]  
    incd x4  
.latch:  
    whilelt p0.d, x4, x3  
    b.first .loop  
    ret
```

| Arrays | 3 | 2 | 1 | 0 |
|--------|---|---|---|---|
| x[]    | 3 | 2 | 1 | 0 |
| y[]    | 0 | 4 | 2 | 0 |

|    | 256 | ... | 128 | 64      |
|----|-----|-----|-----|---------|
| x0 |     |     |     | &x      |
| x1 |     |     |     | &y      |
| x3 |     |     |     | 3       |
| x4 |     |     |     | 4       |
| p0 |     |     |     | F F F F |

|    | 0.0 | 2.0 | 2.0 | 2.0 |
|----|-----|-----|-----|-----|
| z0 | 0.0 | 2.0 | 1.0 | 0.0 |
| z1 | 0.0 | 2.0 | 1.0 | 0.0 |
| z2 | 0.0 | 4.0 | 2.0 | 0.0 |

CYCLES 11

### Fault-tolerant Speculative Vectorization

Some loops have dynamic exit conditions that prevent vectorization

- E.g., the loop breaks on a particular value of the traversed array

| 'h' | 'o' | 'o' | 'k' | "" | 'e' | 'm' | 0 | 0 |
|-----|-----|-----|-----|----|-----|-----|---|---|
| ✓   | ✓   | ✓   | ✓   | ✓  | ✓   | ✓   | ✓ | X |

The access to unallocated space does not trap if it is not the first element

- Faulting elements are stored in the first-fault register (FFR)
- Subsequent instructions are predicated using the FFR information to operate only on successful element accesses

#### strlen (scalar)

```
int strlen(const char *s) {  
    const char *e = s;  
    while (*e) e++;  
    return e - s;  
}
```

```
// x0 = s  
strlen:  
    mov x1, x0 // e=s  
.loop:  
    ldrb x2, [x1], #1 // x2=*e++  
    cbnz x2, .loop // while(*e)  
.done:  
    sub x0, x1, x0 // e-s  
    sub x0, x0, #1 // return e-s-1  
    ret
```

#### strlen (SVE)

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

Simplified and suboptimal implementation

#### strlen (scalar)

```
// x0 = s
strlen:
    mov      x1, x0      // e=s
.loop:
    ldrb     x2, [x1], #1 // x2=*e++
    cbnz     x2, .loop   // while(*e)
.done:
    sub      x0, x1, x0  // e-s
    sub      x0, x0, #1  // return e-s-1
    ret
```

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'r' | 'e' | 'h' | 't' |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](6752cee124f693bc4cebc66180f4f91f_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|---|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| x1 | 0 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

FFR

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

CYCLES 0

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3  | 2   | 1   | 0    |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|----|-----|-----|------|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | '' | 'e' | 'h' | '\0' |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last .loop
    sub      x0, x1, x0
    ret
```

![](201de44da5d99899a8cf58eac2fa7bc9_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |
|----|---|
| x1 | 0 |

FFR

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|

CYCLES 1

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0    |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|------|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'r' | 'e' | 'h' | '\0' |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](1bc1bf231ada31f57cd9f0d8791b784b_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |
|----|---|
| x1 | 0 |

FFR

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|

CYCLES 2

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3  | 2   | 1   | 0   |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|----|-----|-----|-----|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | '' | 'e' | 'h' | 't' |
|        | X  | X  |    |     |     |     |     |     |     |     |     |     |    |     |     |     |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](b4b7023ccc81c5f4ebfd3ccb58361529_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |
|----|---|
| x1 | 0 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

CYCLES

3

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0 |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|---|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'e' | 'h' | 't' |   |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](e91633da5160c8af51a4ace6d3347f53_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |
|----|---|
| x1 | 0 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|

CYCLES

4

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0 |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|---|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'e' | 'h' | 't' |   |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](3881b390d52f27a35faedfc170916c86_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |
|----|---|
| x1 | 0 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | T | F | F | F | F | F | F | F | F | F | F | F | F | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|

CYCLES

5

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0 |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|---|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'e' | 'h' | 't' |   |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](730b6615db6d402580db1024a7f4e163_img.jpg)

128 ... 64 ... 32 16

| x0 | 0 |
|----|---|
| x1 | 0 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|

CYCLES

6

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3  | 2   | 1   | 0   |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|----|-----|-----|-----|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | '' | 'e' | 'h' | 't' |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](98ea5e21d919b389f3ce8b17ef4e65f6_img.jpg)

128 ... 64 ... 32 16

| x0 | 0  |
|----|----|
| x1 | 13 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

CYCLES

7

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3  | 2   | 1   | 0   |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|----|-----|-----|-----|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | '' | 'e' | 'h' | 't' |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](9c888dd6588358989047de6ced8b2bdb_img.jpg)

128 ... 64 ... 32 16

| x0 | 0  |
|----|----|
| x1 | 13 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

CYCLES 8

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0 |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|---|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'e' | 'h' | 't' |   |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](e0113695dbf148bf5ec34354e544414b_img.jpg)

128 ... 64 ... 32 16

| x0 | 13 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|----|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| x1 | 13 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|

CYCLES

9

#### strlen (SVE)

| Arrays | 15 | 14 | 13 | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0 |
|--------|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|---|
| s[]    | 0  | 0  | 0  | 's' | 'n' | 'r' | 'o' | 'h' | 'g' | 'n' | 'o' | 'r' | 'e' | 'h' | 't' |   |

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

![](7b96fce298a23fd76a01ff6c176c1059_img.jpg)

128 ... 64 ... 32 16

| x0 | 13 |
|----|----|
| x1 | 13 |

FFR

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p0

| T | T | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p1

| F | F | T | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

p2

| F | F | F | T | T | T | T | T | T | T | T | T | T | T | T | T |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

z0

| 0 | 0 | 0 | s | n | r | o | h | g | n | o | l | e | h | t |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|--|

CYCLES 10

### Gather-Load & Scatter-Store

#### Gather/Scatter Operations are Good and Evil

- Enable vectorization of codes with non-adjacent accesses on adjacent lanes
- Examples:
  - Outer loop vectorization
  - Strided accesses (larger than +1)
  - Random accesses
- Performance implementation dependent
  - Worst case one separate access per element
- LD1D  $\langle Zt \rangle \cdot D$ , Ps/Z [ $\langle Xn \rangle$ ,  $\langle Zm \rangle \cdot D$ ]

![](a7d6560ff54237234261b647f30ec25c_img.jpg)

Diagram illustrating a Gather/Scatter operation.

The input vectors are  $Zm$  and  $Xn$ .  $Zm$  contains elements  $@a$ ,  $@b$ ,  $@c$ ,  $@d$ .  $Xn$  contains the offset value.

The offset is added to the index values in  $Zt$  (2, 3, 1, 4) to determine the memory addresses for the scatter operation.

The scatter operation writes the values 1, 2, 3, 4 to memory at the addresses  $@a$ ,  $@c$ ,  $@b$ , and  $@d$  respectively.

Memory contains the values 1, 2, 3, 4 at the specified addresses.

Memory

arm Research

### Array of Structures vs. Structure of Arrays

```
typedef struct {  
    uint64_t num_projects;  
    float caffeine;  
    bool vim_nemacs;  
} Programmer_t;
```

![](bc53843127b23a7d84a6184c283d3361_img.jpg)

Programmer\_t programmers[N];

Diagram illustrating the memory layout for an Array of Structures (AoS). The array is indexed 0, 1, 2, ... Each element contains fields of different sizes (uint64\_t, float, bool) stored contiguously. The diagram shows memory segments (blue, orange, green) and load instructions (LD1D, LD1W, LD1B) accessing these fields.

```
typedef struct {  
    uint64_t num_projects[N];  
    float caffeine[N];  
    bool vim_nemacs[N];  
} Programmer_t;
```

![](0775f419af4e481eea2fb9706fe0b035_img.jpg)

Programmer\_t programmers;

Diagram illustrating the memory layout for a Structure of Arrays (SoA). The fields are stored contiguously within each structure, but the structures themselves are separated. The diagram shows memory segments (blue, orange, green) grouped by field type, with the structures separated by gaps.

### Contiguous Multi-Register Structure Loads/Stores

```
typedef struct {  
    uint16_t num_students;  
    uint16_t num_projects;  
};
```

Researcher\_t researchers[N];

![](53d8bef47c63e0897de4cd058bad2cbd_img.jpg)

Diagram illustrating contiguous multi-register structure loads/stores. The structure `Researcher_t` is stored in memory (represented by alternating blue and orange blocks) in a contiguous manner. The memory layout is indexed by 0, 1, and 2. The load/store instruction is shown as:

`LD2H {<Zt>.H, <Zt+1>.H}, P0/Z, [...]`

memory

register file

![](524cc6038f81916add4e259efa7e780b_img.jpg)

Diagram showing the register file structure. The register file contains two registers, `Zt` (top row, blue blocks) and `Zt+1` (bottom row, orange blocks). The register file is divided into four fields, corresponding to the four fields of the structure being loaded/stored.

### Non-temporal Loads & Stores

## SVE Non-Temporal Vector Instructions

- LDNT1D { <Zt1>.D }, <Pg1o>/Z, [<Xn|SP>, <Xm>, LSL #3]
- STNT1D { <Zt1>.D }, <Pg1o>, [<Xn|SP>{, #<simm4>, MUL VL}]

From the Arm ARM (Architecture Reference Manual):

*Non-temporal contiguous load and stores include a **hint to the memory system** that this is a "streaming" access, and the memory locations **are not expected to be accessed again soon** so do not need to be retained in local caches.*

#### Being non-temporal is not enough

### Vector Addition

```
for (i=0; i<N; i++) {  
    a[i] = b[i] + c[i];  
}
```

No benefit if all accesses are temporal

Target to leave space for *temporal* accesses

Idnt1d

![](7c9ab05e6be565a03146efb1d02dcfec_img.jpg)

Diagram illustrating non-temporal access patterns for vectors c and b. Both vectors are shown as sequences of boxes with dashed lines indicating non-temporal access (e.g.,  $c[0], c[1], \dots, c[N-1]$ ).

Idnt1d

![](e74c2048ae64bac0236715f23679476d_img.jpg)

Diagram illustrating non-temporal access patterns for vectors b and a. Both vectors are shown as sequences of boxes with dashed lines indicating non-temporal access (e.g.,  $b[0], b[1], \dots, b[N-1]$ ).

stnt1d

![](8c2b7159561b35cd2f9ef2d0b3a087da_img.jpg)

Diagram illustrating non-temporal access patterns for vector a. The vector is shown as a sequence of boxes with dashed lines indicating non-temporal access (e.g.,  $a[0], a[1], \dots, a[N-1]$ ).

#### Mixed temporal and non-temporal

![](f7f399cd0cd821c0542d77db740e4470_img.jpg)

Diagram illustrating a mixed temporal and non-temporal access pattern. A vertical blue line represents the access path. Three red horizontal bars represent data elements accessed sequentially (temporal locality). The top red bar is accessed by an upward arrow, and the bottom red bar is accessed by a downward arrow, indicating non-temporal access (e.g., a stride access). A green horizontal bar is positioned below the bottom red bar, representing a subsequent access.

#### Mixed temporal and non-temporal

![](5e147601f25f1c4eb5d89d810e906c69_img.jpg)

Diagram illustrating memory access patterns (mixed temporal and non-temporal). A vertical blue arrow indicates a non-temporal access path (e.g., a gather operation) traversing three horizontal red memory blocks (representing data segments) and ending at a green block (representing the destination or a different access pattern). The red blocks show varying degrees of temporal locality, with the middle block being the longest.

![](3040912f5c829555787992af40034f60_img.jpg)

Diagram showing L1 cache structure (green and red blocks).

With non-temporal gather  
And LRU allocation

![](cd5470ebc42e0b621378f0fa519c8e83_img.jpg)

Diagram showing L2 cache structure (a large white block with a red bottom section).

![](d892e79d540ae6841e9b70c59a3931e2_img.jpg)

Diagram showing L3 cache structure (a large white block with a red bottom section).

### Sparse Matrix Vector

```
for(m=row_start[j]; m<row_start[j+1]; m++)
y[j] += A[m] * x[col[m]];
```

![](a4cabfec798f5330bf8cc750d4d518ee_img.jpg)

Diagram illustrating the sparse matrix vector multiplication. The matrix A is shown with non-zero elements highlighted in red. The column index 'col' points to the column of the non-zero element being multiplied by the vector x. The resulting vector y is shown on the right, with the corresponding element being updated.

```
whilelt p1.d, xzr, x4
ld1sw z1.d, p1/z, [x2] // z1 = &col[]
ld1d z2.d, p1/z, [x1, z1.d, ls1 #3] // z2 = &x[&col[]]
ld1d z3.d, p1/z, [x0] // z3 = &A[]
fmla z0.d, p1/m, z2.d, z3.d

add x2, x2, x7 // add half vector reg length (in bytes)
addvl x0, x0, 1 // add vector register length (in bytes)
subs x4, x4, x8 // Remaining length
bgt .L4

faddv d0, p0, z0.d // result for y[j]
```

### Vector ArchitectureDesign Trade-offs

### Cache Coherent Vector Microarchitecture

![](4303ddaf5ad09021ea1c0e0e57c7b82e_img.jpg)

Diagram illustrating the Cache Coherent Vector Microarchitecture. Multiple Cores are shown, each containing L1, L2 caches, SVE (Scalar Vector Extension), and LS (Load/Store) units. These cores are connected via a Network on Chip (NoC) to System-level Caches (SLC) and Memory Controllers (MC).

Cores with one or more SVE and Load/Store (LS) unit(s)

Private L1 and L2 caches (considered part of the core)

System-level cache (SLC) shared among cores

Memory controllers (MC)

Network on chip (NoC) interconnects cores, SLCs and MCs

Disclaimer: Logical representation, not representative of a physical implementation

## SVE Execution Pipeline

![](e931edfeb30764a64be2a430ccb6f928_img.jpg)

Diagram illustrating the SVE Execution Pipeline architecture. Multiple processing units (SLC, MC) are connected via a NoC (Network-on-Chip) to a Core. The Core contains L2, L1, and internal execution units (SVE and LS). The SVE unit is highlighted in red.

### Vector length

- Vectorized code will execute less instructions
- Vector register file size

### Number of execution units and width

- Determines computation throughput

### Vector instruction latencies, cracking, etc...

#### Example:

- Core implements SVE-256 – registers are 256-bit wide
  - There are two execution units of 256 bits (dual issue)
  - Peak throughput per core is 512b/cycle
- A smaller core could implement SVE-256 but one 128b exec unit
  - Each instruction would use two issue cycles
  - Peak throughput per core would be 128b/cycle

### Load-Store Execution Pipeline

![](7f4cf6128a3f5c1bae150ec6cbe13d7b_img.jpg)

Diagram illustrating the Load-Store Execution Pipeline architecture. Multiple SLC (Store/Load Coordinators) and MC (Memory Controller) units are connected via a NoC (Network-on-Chip) to multiple Core units. Each Core unit contains L2 cache, L1 cache (highlighted in red), SVE (Scalar Vector Extension), and LS (Load/Store) execution units.

Number of Load-Store execution units

L1 maximum access width

L1 concurrent accesses

- Number of ports
- Number of banks/arrays

L1 cache size

Prefetching aggressiveness

### L2 Cache

![](cad9f65638b7c839304d8939cb11e6d2_img.jpg)

Diagram illustrating the L2 Cache structure and connectivity. Multiple SLCs (Shared Last Level Cache) and MCs (Memory Controllers) are connected to a NoC (Network-on-Chip). The NoC connects to multiple Core units. One Core unit is shown in detail, containing L1, L2 (highlighted in red), SVE (Scalar Vector Extension), and LS (Load Store).

L2 size to filter NoC accesses

Prefetching aggressiveness

### Network on Chip

![](2281492deb1b39494451c7c123dc449c_img.jpg)

Diagram illustrating a Network on Chip (NoC) architecture. The NoC connects several components:

- System Level Controllers (SLC) and Memory Controllers (MC).
- Two Core components, one of which is detailed further.

The detailed Core component includes:

- L2 cache
- L1 cache
- SVE (Scalable Vector Extension)
- LS (Load Store)

Bandwidth

Connectivity – topology, number of links

Routing to reduce congestion

### System Level Cache

![](a972ca1187ea7285bc4009055bcedd34_img.jpg)

Diagram illustrating the System Level Cache (SLC) architecture. Multiple SLCs (highlighted in red) and Memory Controllers (MCs) are connected via a NoC (Network-on-Chip). The NoC connects to multiple Cores. One Core is shown with its internal cache hierarchy: L2, L1, SVE (System Vector Extension), and LS (Load Store).

SLC size, prefetching, replacement to filter main memory accesses

### Memory

![](8df4b47ea3ab99d6b9dfb79edad57eb1_img.jpg)

Diagram illustrating memory hierarchy and interconnect structure.

Components shown include:

- SLC (Single Level Cache) blocks connected to a NoC (Network-on-Chip).
- MC (Memory Controller) blocks highlighted in red, connected to the NoC.
- Core blocks connected to the NoC.
- Core blocks contain L2, L1, SVE (Scalar Vector Extension), and LS (Load Store).

#### Memory bandwidth

- Channels, banks, width,...

HBM vs DRAM vs NVM...

## Basic Concept

![](82c65e3cbb8271c4ececc92f643526a3_img.jpg)

Diagram illustrating the basic concept of a multi-core system architecture. The diagram shows two main components: a generic Core (left) and a Core with SVE/LS (right). Above the cores is a NoC (Network-on-Chip) connecting various components.

- The NoC connects to SLC (System Level Cache) units and MC (Memory Controller) units.
- The NoC connects to the L2 cache of the Core with SVE/LS.
- The Core with SVE/LS contains L1, L2, SVE (Scalable Vector Extension), and LS (Load Store).

← Memory hierarchy and NoC to feed data to SVE units

← SVE unit configuration for target throughput

## SVE Programming and Tools

### SVE Programming

Assembly  
Full ISA Specification:  
[The Scalable Vector Extension for Armv8-A](#)  
Lots of worked examples in [A sneak peek into SVE and VLA programming](#)

Intrinsics  
[Arm C Language Extensions for SVE](#)  
[Arm Scalable Vector Extensions and application to Machine Learning](#)

Compiler  
Autovectorization – GCC, Arm Compiler for HPC, Cray, Fujitsu  
Help the compiler: OpenMP `#pragma omp parallel for simd`

### SVE Tools

#### Arm Compiler

arm COMPILER

#### Arm Instruction Emulator

![](b9cce3eab268463a9ec78f900b8d1798_img.jpg)

Diagram illustrating the Arm Instruction Emulator workflow:

- Input: Arm v8-A Binary
- Input: Arm v8-A Binary with new features
- Process: Arm Instruction Emulator
- Output: Arm v8-A
- Environment: Linux

#### Research Enablement Kit

![](3f544ab3315559cb5049a9bc4c37bb44_img.jpg)

Illustration of the Research Enablement Kit, showing three stacked components: GEM5, a gear icon, and an ARM chip.

#### arm COMPILER

Commercial C/C++/Fortran compiler with best-in-class performance

![Icon representing a database or server stack.](c0d2c142f0249c1a69993f851b3cd7fe_img.jpg)

Icon representing a database or server stack.

Compilers tuned for Scientific Computing and HPC

#### Tuned for Scientific Computing, HPC and Enterprise workloads

- Processor-specific optimizations for various server-class Arm-based platforms
- Optimal shared-memory parallelism using latest Arm-optimized OpenMP runtime

![Icon representing a speedometer or performance gauge.](09fbde256592c7090e32570c57e2463b_img.jpg)

Icon representing a speedometer or performance gauge.

Latest features and performance optimizations

#### Linux user-space compiler with latest features

- C++ 14 and Fortran 2003 language support with OpenMP 4.5\*
- Support for Armv8-A and SVE architecture extension
- Based on LLVM and Flang, leading open-source compiler projects

![Icon representing a handshake, symbolizing commercial support.](2d5d40d251a8f59bfb5dec1e608544fe_img.jpg)

Icon representing a handshake, symbolizing commercial support.

Commercially supported by Arm

#### Commercially supported by Arm

- Available for a wide range of Arm-based platforms running leading Linux distributions – RedHat, SUSE and Ubuntu

#### Arm Compiler – Building on LLVM, Clang and Flang projects

![](4619c14be962e4c3ba6613aad97f7a86_img.jpg)

Diagram illustrating the Arm C/C++/Fortran Compiler architecture, which is built on LLVM, Clang, and Flang projects.

The compiler consists of the following components and flow:

- **Input Files:** C/C++ Files (.c/.cpp) and Fortran Files (.f/.f90).
- **Frontends:**
  - C/C++ Frontend (Clang based)
  - Fortran Frontend (PGI Flang based)

  These are Language specific frontends.
- **Optimizer:** LLVM based, Language agnostic optimization. It includes:
  - IR Optimizations
  - Auto-vectorization
  - Enhanced optimization for Armv8-A and SVE
- **Code Generators:**
  - Armv8-A code-gen (LLVM based)
  - SVE code-gen (LLVM based)

  These are Architecture specific backends.

**Flow:** C/C++ Files and Fortran Files are processed by their respective frontends, which output LLVM IR. This IR is input to the Optimizer. The Optimizer outputs LLVM IR, which is input to both the Armv8-A code-gen and SVE code-gen. The code-gens output the final binaries: Armv8-A binary and SVE binary.

#### SVE Compiler Support

| Feature                                      | Upstream GCC                                | Upstream LLVM               | Arm Compiler 6 (For bare metal) | Arm HPC Compiler (for Linux user-space) |
|----------------------------------------------|---------------------------------------------|-----------------------------|---------------------------------|-----------------------------------------|
| SVE asm and disasm                           | Yes                                         | Yes                         | Yes                             | Yes                                     |
| SVE code generation                          | Yes                                         | No<br>Planned for 2018-19   | Yes                             | Yes                                     |
| SVE Arm C Language Extensions ("intrinsics") | No<br>Planned for GCC9 (2019)               | No<br>Planned for 2018-19   | Yes                             | Yes                                     |
| Auto-vectorization                           | Basic<br>More improvements planned for GCC9 | None<br>Planned for 2019-20 | Advanced                        | Advanced                                |

#### Arm Instruction Emulator

Develop your user-space applications for future hardware today

![Icon of an alarm clock, symbolizing time to market.](1262b6a2a7586dd7fdc732c999d9afef_img.jpg)

Icon of an alarm clock, symbolizing time to market.

Develop software for  
tomorrow's hardware today

#### Start porting and tuning for future architectures early

- Reduce time to market, Save development and debug time with Arm support

![Icon of a speedometer, symbolizing speed.](a695afb4e99e8c0412e8ae831077dfb1_img.jpg)

Icon of a speedometer, symbolizing speed.

Runs at close to  
native speed

#### Run 64-bit user-space Linux code that uses new hardware features on current Arm hardware

- SVE support available now. Support for 8.x planned.
- Tested with Arm Architecture Verification Suite (AVS)

![Icon of two hands shaking, symbolizing commercial support.](f85901c04910147b1057081deab67741_img.jpg)

Icon of two hands shaking, symbolizing commercial support.

Commercially Supported  
by ARM

#### Near native speed with commercial support

- Emulates only unsupported instructions
- Integrated with other commercial Arm tools including compiler and profiler
- Maintained and supported by Arm for a wide range of Arm-based SoCs

#### Arm Instruction Emulator

Develop your user-space applications for future hardware today

Run Linux user-space code that uses new hardware features (SVE) on current Arm hardware

Simple “black box” command line tool

```
$ armclang hello.c --march=armv8+sve
$ ./a.out
Illegal instruction
$ armie -msve-vector-bits=256 ./a.out
Hello
```

![](a02c9887f2bdb2fc97a46aea5c241d96_img.jpg)

Diagram illustrating the Arm Instruction Emulator workflow:

- Input: Arm v8-A Binary
- Input: Arm v8-A Binary with new features
- Process: Arm Instruction Emulator
- Output: Linux (User Space)
- Output: Arm v8-A (Hardware)

The emulator converts unsupported instructions to native Armv8-A instructions.

#### Instrumenting Aarch64 and SVE

![](52c2f593b127e110ac6fb67e135f1ad3_img.jpg)

Diagram illustrating the instrumentation of Aarch64 and SVE.

The central component is the **SVE Emulation API (in development)**, which is enclosed by a dashed green box.

Inputs to the API include:

- **Armv8-A + SVE Binary** (represented by blue and orange fragments).
- **DynamoRIO** (blue box).
- **ArmIE (client)** (orange box).

Outputs from the API include:

- **SVE Memtrace Client** (blue box). This client outputs a list of instructions (e.g., 0x10000 LD, 0x20000 ST, 0x30000 SVE LD, 0x40000 SVE LD, 0x50000 SVE ST, ...).
- **SVE Inscout Client** (blue box). This client outputs a summary: "XX instructions executed, of which YY were SVE instructions".

Below the API, there are four **SVE custom clients** (represented by blue and orange fragments), which interact bidirectionally with the API.

#### Arm Research Enablement Kit – System Modeling Using gem5

<https://developer.arm.com/research/research-enablement/system-modeling>

- HPI: First Armv8-A based CPU timing model released by Arm
- Documentation about the HPI core model (based on MinorCPU)
- Documentation about running benchmarks (PARSEC)
- Useful scripts (`clone.sh`, `read_results.sh`)
  - Using the current mainline gem5 source code
  - SVE patches will be upstreamed after completing beta testing

![Diagram showing three stacked layers representing system modeling components: gem5, a gear icon, and an ARM chip.](c13f6935817282291ff1db48a1488a68_img.jpg)

Diagram showing three stacked layers representing system modeling components: gem5, a gear icon, and an ARM chip.

## More on SVE

<http://developer.arm.com/hpc>

- Full SVE specification: [Arm Architecture Reference Manual Supplement, SVE for ARMv8-A](#)
- Intrinsics: [Arm C Language Extensions for SVE](#) and
- Lots of worked examples in [A sneak peek into SVE and VLA programming](#)
- Optimized machine learning in [Arm SVE and application to Machine Learning](#)

## Internships & Full-time Opportunities

[arm.com/careers](http://arm.com/careers)

Twitter: @alexrico46

LinkedIn: alexrico

The Arm trademarks featured in this presentation are registered trademarks or trademarks of Arm Limited (or its subsidiaries) in the US and/or elsewhere. All rights reserved. All other marks featured may be trademarks of their respective owners.

arm Research

[www.arm.com/company/policies/trademarks](http://www.arm.com/company/policies/trademarks)

Thank You!

Danke!

Merci!

谢谢!

ありがとうございます!

Gracias!

Kiitos!

arm Research