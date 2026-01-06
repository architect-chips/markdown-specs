

arm

# Arm and SVE

International Workshop on High-Performance Computing and Programming on Quantum Chemistry and Physics 2020 (HPCPQCP2020)

Dr. Olly Perks (olly.perks@arm.com)

15<sup>th</sup> January 2020

## Agenda

- Part 1: Getting to SVE (45 Mins)
  - A quick introduction of Arm in HPC / Scientific Computing
  - Existing Arm vector units / instructions: NEON
  - The SVE specification
- Part 2: Going Forward with SVE (45 mins)
  - Using SVE for real applications
  - Next generation vector instructions: Beyond SVE

arm

## Part 1: Getting to SVE

arm

Recap:  
Arm and Arm in HPC

### Arm Technology Already Connects the World

#### Arm is ubiquitous

21 billion chips sold by partners in 2017 alone

Mobile/Embedded/IoT/  
Automotive/Server/GPUs

#### Partnership is key

We design IP, not manufacture chips

Partners build products for their target markets

#### Choice is good

One size is not always the best fit for all

HPC is a great fit for co-design and collaboration

### Armv8-A Architecture Evolution

#### RISC architecture

- Only have 32 bits available for encoding all instructions
- Supports the development of efficient implementations

#### 64-bit capable since 2012

- Known as AArch64 (or AArch32 when run in a 32-bit mode)
- 128-bit vector unit (aka NEON Advanced SIMD)

![](0ad3f61f997eb05afb341fc46024bf2b_img.jpg)

Timeline of ARMv8-A Architecture Evolution:

- **October 2011: ARM v8.0**
  - AArch64 execution state
  - A64 instruction set
- **December 2014: ARM v8.1-A**
  - Atomic memory ops
  - Type2 hypervisor support
- **January 2016: ARM v8.2-A**
  - Half-precision float
  - RAS support
  - Statistical profiling
- **October 2016: ARM v8.3-A**
  - Pointer authentication
  - Nested virtualization
  - Complex float

### History of Arm in HPC: A Busy Decade

![Image of a Calxada HPC system component, likely a memory module or CPU die.](9ebd85380ef496499e5f23ec0d9cd744_img.jpg)

Image of a Calxada HPC system component, likely a memory module or CPU die.

#### 2011 Calxada

- 32-bit ARmv7-A – Cortex A9

![Image of a Mont-Blanc 1 HPC system server rack.](0872c27ab0a48c6e88ef4f09f773872f_img.jpg)

Image of a Mont-Blanc 1 HPC system server rack.

#### 2011-2015 Mont-Blanc 1

- 32-bit Armv7-A
- Cortex A15
- First Arm HPC system

![Image of an AMD Opteron A1100 CPU die.](f3e03accc76df483950e65a9fb19c20e_img.jpg)

Image of an AMD Opteron A1100 CPU die.

#### 2014 AMD Opteron A1100

- 64-bit Armv8-A
- Cortex A57
- 4-8 Cores

![Image of a Cavium ThunderX CPU die.](8a58f9778d09be5d0a0ae25e5393a583_img.jpg)

Image of a Cavium ThunderX CPU die.

#### 2015 Cavium ThunderX

- 64-bit Armv8-A
- 48 Cores

![Image of a Marvell ThunderX 2 CPU die.](b388303c53ef0594eb52ab80c2e23feb_img.jpg)

Image of a Marvell ThunderX 2 CPU die.

#### 2017 (Cavium) Marvell ThunderX 2

- 64-bit Armv8-A
- 32 Cores

### History of Arm in HPC: A Busy Decade

![Image of a Calxada memory module.](3121afa7ca030b22ee0345864ca6f38b_img.jpg)

|                                              | <img alt="Image of a Mont-Blanc 1 HPC system server rack."/>                         | <img alt="Image of an AMD Opteron A1100 CPU."/>                           | <img alt="Image of a Cavium ThunderX chip."/>          | <img alt="Image of a Marvell ThunderX 2 chip."/>                   | <img alt="Image of a Fujitsu A64FX chip."/>                                 |
|----------------------------------------------|--------------------------------------------------------------------------------------|---------------------------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------|
| 2011 Calxada<br>• 32-bit ARmv7-A – Cortex A9 | 2011-2015 Mont-Blanc 1<br>• 32-bit Armv7-A<br>• Cortex A15<br>• First Arm HPC system | 2014 AMD Opteron A1100<br>• 64-bit Armv8-A<br>• Cortex A57<br>• 4-8 Cores | 2015 Cavium ThunderX<br>• 64-bit Armv8-A<br>• 48 Cores | 2017 (Cavium) Marvell ThunderX 2<br>• 64-bit Armv8-A<br>• 32 Cores | 2019 Fujitsu A64FX<br>• First Arm chip with SVE vectorisation<br>• 48 Cores |

Image of a Calxada memory module.

### Why Arm?

Especially for Infrastructure / HPC / Scientific Computing / ML?

### Hardware

- Flexibility: Allow vendors to differentiate
  - Speed and cost of development
- Provide different licensing
  - Core - Reference design (A53/A72/N1)
  - Architecture - Design your own (TX2, A64FX)
- Other hardware components
  - NoCs, GPUs, memory controllers
  - “Building blocks” design
- Architecture validation for correctness

#### Software

- All based on the same instruction set
  - Commonality between hardware
  - Reuse of software
- Comprehensive software ecosystem
  - Operating systems, compilers, libraries, tools
  - Not just vendor - third party too
- Large community
  - Everything from Android to HPC

Each generation brings faster performance and new infrastructure specific features

![](4e0ade2f41b66d5602160da5cc978274_img.jpg)

| 16nm            | 7nm                   | 7nm+          | 5nm               |
|-----------------|-----------------------|---------------|-------------------|
| Cosmos Platform | Ares Platform<br>“N1” | Zeus Platform | Poseidon Platform |
| 2018            | Today                 | 2020          | 2021              |

30% Faster System Performance per Generation + New Features

#### Variation in the Processor Market

| Marvell (Cavium)   |                      | CAVIUM THUNDERX        | CAVIUM THUNDERX2                    | THUNDERX3 7nm      |  |
|--------------------|----------------------|------------------------|-------------------------------------|--------------------|--|
| Ampere (X-Gene)    | applied micro X-Gene | applied micro X-Gene 2 | AMPERE eMag                         | AMPERE Quicksilver |  |
| Fujitsu            |                      |                        |                                     | FUJITSU A64FX      |  |
| Huawei (HiSilicon) | Hi1612               | 1616                   | Kunpeng 920                         | Hi1630             |  |
| Amazon (Annapurna) |                      |                        | aws Graviton                        | aws Graviton2      |  |
| EPI / SiPearl      |                      |                        |                                     | SiPEARL RHEA       |  |
| Other              |                      | PHYTIUM                | QUALCOMM Qualcomm Centriq Processor |                    |  |

#### Arm Processor Top Trumps

##### Marvell: ThunderX2

![Marvell ThunderX2 logo](e3b8510f6a2194e250205ab7bc38076d_img.jpg)

Marvell ThunderX2 logo

| Core Count:         | 32           |
|---------------------|--------------|
| Clock Speed:        | 2.5 GHz      |
| Memory Bandwidth:   | ~130 GB/s    |
| Energy Consumption: | ~200 w       |
| Vector Units:       | 128-bit NEON |

##### Huawei: Kunpeng 920

![Huawei Kunpeng 920 logo](e159e9f78612406820a4d40e26e01413_img.jpg)

Huawei Kunpeng 920 logo

| Core Count:         | 64           |
|---------------------|--------------|
| Clock Speed:        | 2.6 GHz      |
| Memory Bandwidth:   | ~130 GB/s    |
| Energy Consumption: | ~180 w       |
| Vector Units:       | 128-bit NEON |

##### Fujitsu: A64FX

![Fujitsu A64FX logo](a8a65eb4968947846b288d693535f03a_img.jpg)

Fujitsu A64FX logo

| Core Count:         | 48          |
|---------------------|-------------|
| Clock Speed:        | 2 GHz       |
| Memory Bandwidth:   | ~1 TB/s     |
| Energy Consumption: | ~150 w      |
| Vector Units:       | 512-bit SVE |

#### HPC Deployments

- More Arm based CPUs are being adopted
  - Lots of large scale deployments
- Different OEMs
  - Cray, HPE, Atos-Bull, Fujitsu, Huawei, E4
- EU Deployments
  - Isambard: Cray 10k TX2 cores
  - GENCIE: Atos 18k TX2 cores
  - Catalyst 3 systems: HPE 4k TX2 core
  - Fugaku Prototype: Fujitsu 36.8K A64FX cores
  - **Future** Isambard 2: Cray A64FX
  - **Future** Deucalion: Cray A64FX

![Image of the Astra supercomputer, labeled 'THE WORLD'S FIRST PETASCALE ARM SUPERCOMPUTER'.](bb6d33498937738ff5dac8d91c9ebaad_img.jpg)

Image of the Astra supercomputer, labeled 'THE WORLD'S FIRST PETASCALE ARM SUPERCOMPUTER'.

>5k ThunderX2 CPUs

![Image of a row of server racks, labeled 'Atlas 900'.](c092f712a80ce3310c5e29d0fa0e454a_img.jpg)

Image of a row of server racks, labeled 'Atlas 900'.

2k Kunpeng 920 CPUs + 8k AI accelerators

![Image of the Fugaku supercomputer logo, featuring stylized Japanese characters.](b8205e5e617a8946ddc956c816156fec_img.jpg)

Image of the Fugaku supercomputer logo, featuring stylized Japanese characters.

150k+ Fujitsu A64FX CPUs

![ARM logo.](34fccc54a5930cbdf0f07e02c3745e35_img.jpg)

ARM logo.

#### The Cloud

Open access to server class Arm

VERNE GLOBAL

Verne Global: What is hpcDIRECT? In partnership with Arm and

VERNE GLOBAL

in partnership

arm

![Marvell logo](159f15d60777adb6b16c91d84b32c32f_img.jpg)

Marvell logo

HPC

Since 1987 - Covering the Fastest Computers in the World and the People Who Run Them

![Image of an AWS Graviton processor chip](d26f02d49d7295c5e4f60c6cbb1a9bce_img.jpg)

Image of an AWS Graviton processor chip

AWS Graviton Processor

![Speaker on stage presenting](fd83312f7686fc54a1c891340b925092_img.jpg)

Speaker on stage presenting

First Arm Cloud Instances

POWERED BY AWS GRAVITON2 PROCESSORS

M6g, R6g, C6g instances for EC2

New generation of Arm-based instances powered by AWS Graviton2 processors offer 40% better price/performance than current x86-based instances

M6g C6g R6g

![Diagram illustrating the M6g, R6g, and C6g instance types](6b4458bb11bedb60a9bd64fa0c651a66_img.jpg)

Diagram illustrating the M6g, R6g, and C6g instance types

c1.large.arm

With 96 physical Arm cores, this server is anything but a lightweight - and it comes with 128 GB of RAM for just \$0.50/hr. Nice!

packet

#### NAMD 3 Alpha, Tesla V100 Performance, ApoA1 92k Atoms

| Hardware platform |                 | ns/day | Speedup |
|-------------------|-----------------|--------|---------|
| Intel Xeon 8168   | + 1x Tesla V100 | 102.1, | 1.0x    |
| IBM Power9        | + 1x Tesla V100 | 99.7,  | 0.97x   |
| Cavium ThunderX2  | + 1x Tesla V100 | 98.2,  | 0.96x   |

![Molecular structure visualization of ApoA1 protein, showing the folded protein chain (yellow/green) surrounded by solvent molecules (red/blue) inside a gray, wavy boundary.](d25a962fde4b3171879749757440c3c5_img.jpg)

Molecular structure visualization of ApoA1 protein, showing the folded protein chain (yellow/green) surrounded by solvent molecules (red/blue) inside a gray, wavy boundary.

##### NAMD 3 Alpha Note:

This measured the new NAMD 3 Alpha in single-node mode, yielding greatest overall GPU acceleration for small to moderate sized atomic structure simulations.

ARM+NVIDIA  
Preliminary Results

#### Not Just Hardware

#### Applications

Open-source, owned, commercial ISV codes, ...

#### Containers, Interpreters, etc.

Singularity, PodMan, Docker, Python, ...

#### Performance Engineering

Arm Forge (DDT, MAP),  
Rogue Wave, HPC Toolkit,  
Scalasca, Vampir, TAU, ...

#### Middleware

Mellanox IB/OFED/HPC-X, OpenMPI, MPICH, MVAPICH2, OpenSHMEM, OpenUCX, HPE MPI

#### OEM/ODM's

Cray-HPE, ATOS-Bull,  
Fujitsu, Gigabyte, ...

#### Compilers

Arm, GNU, LLVM, Clang, Flang,  
Cray, PGI/NVIDIA, Fujitsu, ...

#### Libraries

ArmPL, FFTW, OpenBLAS,  
NumPy, SciPy, Trilinos, PETSc,  
Hypre, SuperLU, ScaLAPACK, ...

#### Filesystems

BeeGFS, Lustre, ZFS,  
HDFS, NetCDF, GFS, ...

#### Silicon Suppliers

Marvell, Fujitsu,  
Mellanox, NVIDIA, ...

#### OS

RHEL, SUSE, CentOS, Ubuntu, ...

#### Arm Server Ready Platform

Standard firmware and RAS

#### Schedulers

SURM, IBM LSF, Altair PBS Pro, ...

#### Cluster Management

Bright, HPE CMU, Xcat, Warewulf, ...

### A Rich and Growing Application Ecosystem

![](af06598cfb31b517e79b50d74f72a0ca_img.jpg)

| GROMACS   | LAMMPS           | CESM2    | MrBayes       | Bowtie   |
|-----------|------------------|----------|---------------|----------|
| NAMD      | AMBER            | Paraview | SIESTA        | UM       |
| WRF       | Quantum ESPRESSO | VASP     | MILC          | GEANT4   |
| OpenFOAM  | GAMESS           | VisIt    | DL-Poly       | NEMO     |
| BLAST     | NWCHEM           | Abitit   | BWA           | QMCPACK  |
| Chem/Phys | Weather          | CFD      | Visualization | Genomics |

![LS-DYNA logo](93afce28d7dec5b2202789b31b4ef8ab_img.jpg)

LS-DYNA logo

![ANSYS FLUENT and Altair logos](6cc4a2d5ea0462e4825d57bd689bd2b3_img.jpg)

ANSYS FLUENT and Altair logos

cādence

Community driven Applications recipes:

<https://gitlab.com/arm-hpc/packages/-/wikis/categories/allPackages>

#### Single node performance results

![](b6750d26d3dd287a4a4d49b3670a44bd_img.jpg)

Bar chart showing Single node performance results (normalized to Broadwell) for four CPU architectures across various benchmarks. The Y-axis represents Performance (normalized to Broadwell), ranging from 0 to 2.0. The X-axis lists the benchmarks: CP2K, GROMACS, NAMD, NEMO, OpenFOAM, OpenSBLI, Unified Model, VASP, and Geometric Mean.

Legend:

- Broadwell 22c (Blue)
- Skylake 20c (Red)
- Skylake 28c (Tan)
- ThunderX2 32c (Dark Gray)

Performance data (normalized to Broadwell):

| Benchmark      | Broadwell 22c | Skylake 20c | Skylake 28c | ThunderX2 32c |
|----------------|---------------|-------------|-------------|---------------|
| CP2K           | 1.00          | 1.29        | 1.37        | 1.15          |
| GROMACS        | 1.00          | 1.29        | 1.45        | 0.68          |
| NAMD           | 1.00          | 0.98        | 1.21        | 1.16          |
| NEMO           | 1.00          | 1.44        | 1.65        | 1.49          |
| OpenFOAM       | 1.00          | 1.57        | 1.66        | 1.87          |
| OpenSBLI       | 1.00          | 1.39        | 1.72        | 1.69          |
| Unified Model  | 1.00          | 1.06        | 1.19        | 0.92          |
| VASP           | 1.00          | 1.32        | 1.42        | 0.76          |
| Geometric Mean | 1.00          | 1.28        | 1.45        | 1.15          |

#### Arm Provided HPC Software

Just from Arm, other vendors provide their own

#### Compilers and Libraries

- Arm Compiler for Linux
  - LLVM based compiler optimized for Arm
  - C/C++ & Fortran
- GCC
  - Optimized for Arm
- Maths libraries
  - LAPACK, BLAS, FFT, SpMV, SpMM
  - Transcendentals
  - Micro-architecture optimized

#### Parallel Tools

- DDT: Debugger
  - C/C++, Fortran and Python
  - MPI, OpenMP, CUDA, OpenACC
- MAP: Performance Profiler
  - Scalable sampling-based profiler
- ArmIE: Instruction Emulator
  - Emulate unsupported instructions
  - SVE

#### Machine Learning and Artificial Intelligence

![](de2d3e89ee4dd60958b64426cd3a81ca_img.jpg)

Diagram illustrating the Machine Learning and Artificial Intelligence stack, organized into three layers:

- **Ecosystem** (AI/ML Applications, Algorithms and Frameworks):
  - TensorFlow™
  - TensorFlow Lite™
  - mxnet™
  - Caffe™
  - PyTorch™
  - Caffe2™
  - ONNX™
  - Android™ NNAPI
- **Software Products** (Software Libraries Optimized for Arm Hardware):
  - arm NN
  - arm COMPUTE LIBRARY
  - CMSIS-NN
- **Hardware Products** (Arm Hardware IP for AI/ML):
  - CPU:
    - arm CORTEX
    - arm DynamIQ
    - arm NEOVERSE
  - GPU:
    - arm MALI
  - NPU:
    - Machine Learning Processor (ML)
  - Partner IP:
    - DSPs, FPGAs, Accelerators

#### ML Frameworks on AArch64

##### On-CPU server-scale ML workloads

- Leading frameworks and dependencies built on AArch64
  - TensorFlow: <https://gitlab.com/arm-hpc/packages/-/wikis/packages/tensorflow>
  - PyTorch: <https://gitlab.com/arm-hpc/packages/-/wikis/packages/pytorch>
  - MXNET: <https://gitlab.com/arm-hpc/packages/-/wikis/packages/mxnet>
- OS Docker tools for TensorFlow part of [github.com/ARM-software/Tool-Solutions](https://github.com/ARM-software/Tool-Solutions)
  - <https://github.com/ARM-software/Tool-Solutions/tree/master/docker/tensorflow-aarch64>
    - Compiler: GCC 9.2
    - Maths libraries: Arm Optimized Routines and OpenBLAS 0.3.6
    - Python3 environment built from CPython 3.7 and containing:
      - NumPy 1.17.1
      - TensorFlow 1.15
      - TensorFlow Benchmarks
- Focus has been on TensorFlow, and the maths libraries
  - Inference applications
  - Many-core systems
  - Significant GEMM, and vector maths, work

#### TensorFlow and maths libraries on AArch64

![](ed75e80b1e08237f7e90b65357de84d5_img.jpg)

Diagram illustrating the software stack for TensorFlow and maths libraries on AArch64, showing dependencies and compatibility.

**Top Level (Data & Models):** Imagenet, coco, various icons (people, clothing, objects), mobilenet, ResNet50, and a robot icon.

**Framework:** TensorFlow

**Scheduling:** Eigen: pthread pools; GEMM workload distribution

**Maths lib:** Eigen, Eigen – tensor contraction, DNNL (MKL-DNN)

**Kernels:** libamath, GEBP, ArmPL, C++ ref, BLAS + Ref, AVX512 JIT

**Hardware:** AArch64

**Legend:**

- Green arrow: = works on AArch64
- Orange arrow: = option
- Red arrow: = not supported

23 © 2019 Arm Limited

##### Increasing ML performance over CPU generations

![](e9f324c9d7f5305a55cb156855e95b95_img.jpg)

Bar chart showing Int8 GEMM kernel performance (normalized to A72).

| CPU Generation | Performance (Normalized to A72) |
|----------------|---------------------------------|
| A53            | 0.44                            |
| A72            | 1.00                            |
| Helios         | 1.35                            |
| N1 (Ares)      | 5.74                            |
| Zeus           | 25.72                           |

##### A72

2x ML performance  
improvement over Cortex-A53

##### Helios

>3x ML performance  
improvement over Cortex-A53  
(First Multi-threaded CPU)

##### N1

>5x ML performance  
improvement over Cortex-A72  
(PPA leadership & ML  
enhancements)

#### Zeus

>25x ML performance  
improvement over Cortex-A72  
(Breakthrough ML performance)

arm

### NEON: General Purpose Vector Instructions

#### Arm NEON Vector Units

- SIMD Vector Extensions
  - Advanced Single Instruction Multiple Data
  - Fixed width at 128-bit
- As of Armv8-a
  - 31x 64-bit general-purpose registers
    - The 32-bit W register is lower half of 64-bit X register
  - 32x 128-bit floating-point registers
    - D is lower 64 bits of 128-bit Q registers
- Example:
  - fadd v0.4s, v0.4s, v1.4s
  - Addition of 4 x 32-bit floats
    - 128-bit NEON/32-bit Int = 4 Lanes

##### 64-bit register layout

![](a1545557e366b6302109d13360b199c3_img.jpg)

Diagram illustrating the 64-bit register layout, showing the bit positions from 63 down to 0. The register is divided into two main sections: the lower 32 bits (Wn) and the upper 32 bits (Xn).

#### SPSR: Saved Program State Register

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8      | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|---|--------|---|---|---|---|---|---|---|---|
| N  | Z  | C  | V  |    |    |    |    | SS |    |    |    | IL |    |    |    |    |    | D  | A  | I  | F  | M | M[3:0] |   |   |   |   |   |   |   |   |

![](0245dc88c1db93181871e732bc0655dd_img.jpg)

Diagram illustrating the 128-bit vector register layout (Q0, Q1, Q0) and the 4-lane addition operation. The vector register is divided into 4 lanes (127-96, 95-64, 63-32, 31-0). The 4-lane addition operation is shown below the register, where inputs from Q0 and Q1 are summed in parallel across the 4 lanes, resulting in the output Q0.

#### Arm NEON Vector Instructions

- Comprehensive set of vector operations
  - Loads, stores and maths operations
  - Scalar and floating point

```
FADD <Vd> . <T>, <Vn> . <T>, <Vm> . <T>
```

Instruction Destination Operand 1 Operand 2

- <Vd> - Destination register, <T> - Type e.g. 4S or 2D

```
FADD V0 . 4S, V0 . 4S, V1 . 4S
```

- Add 4 single precision floating point values from V0 to V1 and store in V0
  - $V0 += V1$

#### Programming NEON

```
.LBB0_4:
    ldp      q0, q1, [x10, #-16]
    subs     x11, x11, #8
    fadd     v0.4s, v0.4s, v0.4s
    fadd     v1.4s, v1.4s, v1.4s
    stp      q0, q1, [x10, #-16]
    add      x10, x10, #32
    b.ne     .LBB0_4

// %bb.5:
    cmp      x9, x8
    b.eq     .LBB0_8

.LBB0_6:
    add      x10, x1, x9, lsl #2
    sub      x8, x8, x9

.LBB0_7:
    ldr      s0, [x10]
    subs     x8, x8, #1
    fadd     s0, s0, s0
    str      s0, [x10], #4
    b.ne     .LBB0_7

.LBB0_8:
    mov      w0, wzr
    ret
```

```
for (int i=0; i < n; ++i) {
    a[i] = 2.0 * a[i];
}
```

- .LBB0\_4: Start with vector loop (and unroll)
  - Load 8 x 32-bit values (into 2 x 128-bit registers)
  - Subtract 8 from loop counter
  - 2x NEON add instructions (register to itself => 2.0\*a[i])
  - Store pair of 128-bit registers back
  - Update array offsets
  - Loop if >=8 iterations left
- .LBB0\_7: Remainder (fewer than 8 iterations left)
  - Load a single scalar
  - Add it to itself
  - Store
  - Loop if iterations left

#### Ease of Use for NEON

#### Where to start

#### NEON Intrinsics (ACLE)

- `#include arm_neon.h`
  - Header file of NEON intrinsics
- Map to assembly types and instruction names

```
float32x4_t va = vld1q_f32(&a[i]);
va = vmulq_n_f32(va, 2.0);
vst1q_f32(&a[i], va)
```

- Load 4x 32-bit floats into `va` from `a[i]`
- Multiply the floats in `va` by 2.0
- Store contents of `va` back into `a[i]`

#### Auto Vectorisation & Libraries

- Not everyone wants to hand code assembly
- Compilers will generate vector code
  - Generally at optimization levels  $> -O2$
  - Supported in GCC, LLVM, Cray, Arm compiler
  - Vectorisation reports will inform on success
- Vectorised libraries
  - Such as ArmPL maths library

#### Limitations of NEON

- NEON is firstly only 128-bit
  - Not much use to HPC / Scientific Computing
- Want bigger vectors
  - To expand to 256-bit of 512-bit we would need separate instructions
  - Arm like to offer flexibility to customers - Different vector lengths
    - However it is a RISC architecture (32-bit instruction encoding)
- Suffers from same drawbacks as other vector implementations (AVX)
  - Difficulty to autovectorise
  - Remainder loops

arm

### SVE: Today's new Vectorisation Paradigm

#### SVE: Scalable Vector Extension

- **SVE is Vector Length Agnostic (VLA)**
  - Vector Length (VL) is a hardware implementation choice from 128 up to 2048 bits.
  - New programming model allows software to scale dynamically to available vector length.
  - No need to define a new ISA, rewrite or recompile for new vector lengths.
- **SVE is not an extension of Advanced SIMD (aka Neon)**
  - A separate, optional extension with a new set of instruction encodings.
  - Initial focus is HPC and general-purpose server, not media/image processing.
- **SVE begins to tackle traditional barriers to auto-vectorization**
  - Software-managed speculative vectorization allows uncounted loops to be vectorized.
  - In-vector serialised inner loop permits outer loop vectorization in spite of dependencies.

#### How can you program when the vector length is unknown?

SVE provides features to enable VLA programming from the assembly level and up

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

|             | 1 | 2 |   |   |
|-------------|---|---|---|---|
| +           | 1 | 2 | 0 | 0 |
| <i>pred</i> | 1 | 1 | 0 | 0 |

#### Vector partitioning & software-managed speculation

First Faulting Load instructions allow memory accesses to cross into invalid pages.

#### SVE Registers

##### Scalable vector registers

- Z0-Z31 extending NEON's 128-bit v0-v31.
- Packed DP, SP & HP floating-point elements.
- Packed 64, 32, 16 & 8-bit integer elements.

##### Scalable predicate registers

- P0-P15 predicates for loop / arithmetic control.
- $1/8^{\text{th}}$  size of SVE registers (1 bit / byte).
- FFR first fault register for software speculation.

![](bac21fd48fcd7f025c723590e07d1823_img.jpg)

Diagram illustrating the Scalable Vector Extension (SVE) vector registers (Z0-Z31) and their associated predicate registers (P0-P15).

The vector registers are shown as four horizontal bars, labeled Z31, Z2, Z1, and Z0 (from top to bottom). The total length is indicated as  $\text{LEN} \times 128$ . The rightmost portion of each register is highlighted in green and labeled V31, V2, V1, and V0, respectively, corresponding to the NEON registers.

The predicate registers are shown as two columns of horizontal bars, labeled P7, P2, P1, P0 (left column, teal) and P15, P10, P9, P8 (right column, purple). The total length for the predicate registers is indicated as  $\text{LEN} \times 16$ .

![](6fe536731996880570f251da168376cf_img.jpg)

Continuation of the SVE register diagram, showing the predicate registers (P0-P15) and the First Fault Register (FFR).

The left column shows predicate registers P7, P2, P1, P0 (teal). The right column shows predicate registers P15, P10, P9, P8 (purple). The FFR (First Fault Register) is shown as a separate purple bar.

#### Predicates: Active Lanes vs Inactive Lanes

Predicate registers track lane activity

- 16 predicate registers (P0-P15)
- 1 predicate bit per 8 vector bits (lowest predicate bit per lane is significant)
- On **load**, active elements update the destination
- On **store**, inactive lanes leave destination unchanged (p0/m) or set to 0's (p0/z)

![](b9d879f357d5f15fac9ea8585b87d0a2_img.jpg)

p0.d

| 255 | 192 191 |  | 128 127 |  | 64 63 |  | 0 |  |
|-----|---------|--|---------|--|-------|--|---|--|
| 64b | I       |  | I       |  | I     |  | I |  |
| 31  | 24 23   |  | 16 15   |  | 8 7   |  | 0 |  |

p0.s

| 32b | 32b | 32b | 32b | 32b | 32b | 32b | 32b |
|-----|-----|-----|-----|-----|-----|-----|-----|
| 0   | 0   | 0   | I   | I   | I   | I   | I   |

#### SVE Predicate condition flags

##### SVE is a *predicate-centric* architecture

- Predicates are central, not an afterthought
- Support complex nested conditions and loops.
- Predicate generation also sets condition flags.
- Reduces vector loop management overhead.

##### Overloading the A64 NZCV condition flags

| Flag | SVE   | Condition                           |
|------|-------|-------------------------------------|
| N    | First | Set if first active element is true |
| Z    | None  | Set if no active element is true    |
| C    | !Last | Set if last active element is false |
| V    |       | Scalarized loop state, else zero    |

##### Reuses the A64 conditional instructions

- Conditional branches B.EQ → B.NONE
- Conditional select, set, increment, etc.

| Condition Test | A64 Name | SVE Alias | SVE Interpretation                                                  |
|----------------|----------|-----------|---------------------------------------------------------------------|
| Z=1            | EQ       | NONE      | No active elements are true                                         |
| Z=0            | NE       | ANY       | Any active element is true                                          |
| C=1            | CS       | NLAST     | Last active element is not true                                     |
| C=0            | CC       | LAST      | Last active element is true                                         |
| N=1            | MI       | FIRST     | First active element is true                                        |
| N=0            | PL       | NFRST     | First active element is not true                                    |
| C=1 & Z=0      | HI       | PMORE     | More partitions: some active elements are true but not the last one |
| C=0   Z=1      | LS       | PLAST     | Last partition: last active element is true or none are true        |
| N=V            | GE       | TCONT     | Continue scalar loop                                                |
| N!=V           | LT       | TSTOP     | Stop scalar loop                                                    |

### SVE supports vectorization in complex code

Right from the start, SVE was engineered to handle codes that usually won't vectorize

![Diagram illustrating Gather-load and scatter-store. Four separate memory locations (gray boxes) are shown, each connected by an arrow pointing down to a single contiguous memory segment (dark blue bar), indicating data is loaded from non-contiguous locations into a single register.](02f9c911b69504d90bd20e0bc61c4bbb_img.jpg)

Diagram illustrating Gather-load and scatter-store. Four separate memory locations (gray boxes) are shown, each connected by an arrow pointing down to a single contiguous memory segment (dark blue bar), indicating data is loaded from non-contiguous locations into a single register.

#### Gather-load and scatter-store

Loads a single register from several non-contiguous memory locations.

$$\begin{array}{cccccc} \boxed{1} & + & \boxed{2} & + & \boxed{3} & + & \boxed{4} & = \\ \boxed{1} & + & \boxed{2} & & \boxed{3} & + & \boxed{4} & \\ & = & & & = & & & \\ & \boxed{3} & + & & \boxed{7} & & & = \end{array}$$

#### Extended floating-point horizontal reductions

In-order and tree-based reductions trade-off performance and repeatability.

arm

Questions and  
Break

arm

Part 2: Going  
Forward with SVE

#### Quick Recap

- SVE enables Vector Length Agnostic (VLA) programming
- VLA enables portability, scalability, and optimization
- Predicates control which operations affect which vector lanes
  - Predicates are not bitmasks
  - You can think of them as dynamically resizing the vector registers
- The actual vector length is set by the CPU architect
  - Any multiple of 128 bits up to 2048 bits
  - May be dynamically reduced by the OS or hypervisor
- SVE was designed for HPC and can vectorize complex structures
- Many open source and commercial tools currently support SVE

![](16c69c0dacd3c57ae91acd114e5f5bd2_img.jpg)

```
for (i = 0; i < n; ++i)  
INDEX i n-2 n-1 n n+1  
CMPLT n 1 1 0 0
```

![](673e9e5873f9a4b71bbe7bac2cf6b758_img.jpg)

Diagram illustrating predicate logic:

Vector lanes are shown with indices 1, 2, and 0, 0 (n+1). A predicate (pred) is applied, resulting in a vector of 1s and 0s.

![](15cfb04d6d02b0e125966b0edb907b68_img.jpg)

Diagram showing four arrows pointing down onto a horizontal bar, representing vector lanes.

![](c188a16c19591cada6a7e3e3d690c21b_img.jpg)

Cartoon image of three cows with horns, labeled "GNU! GNU! GNU!".

arm

#### VLA Programming

Vector Length Agnostic

#### Vector Length Agnostic Programming

A paradigm shift for developers

#### Advantages

- Not thinking about vector length
  - Rather just vectorization
- No peel/remainder loops
  - All handled by predication
- Key is loop structures
  - Predicates are powerful

#### Considerations

- Should not be writing fixed width
  - Applies to data structures and instructions
  - More portable for different hardware
- Can the compiler identify loop structure?
  - Generate predicated instructions
- However: VLA \*may\* be slower
  - Cost of generating predicates
  - Near empty loops

##### How do you count by vector width?

No need for multi-versioning: one increment to rule all vector sizes

```
ld1w z1.s, p0/z, [x0,x4,ls1 2] // p0:z1=x[i]
ld1w z2.s, p0/z, [x1,x4,ls1 2] // p0:z2=y[i]
fmla z2.s, p0/m, z1.s, z0.s // p0?z2+=x[i]*a
st1w z2.s, p0, [x1,x4,ls1 2] // p0?y[i]=z2

incw x4 // i+=(VL/32)
```

“Increment x4 by the number of 32-bit lanes (w) that fit in a VL.”

#### Initialization when vector length is unknown

- Vectors cannot be initialized from compile-time constant, so...
  - INDEX Zd.S, #1, #4 : Zd = [ 1, 5, 9, 13, 17, 21, 25, 29 ]
- Predicates cannot be initialized from memory, so...
  - PTRUE Pd.S, MUL3 : Pd = [ T, T, T, T, T, T, F, F ]
- Vector loop increment and trip count are unknown at compile-time, so...
  - INCD Xi : increment scalar Xi by # of 64b dwords in vector
  - WHILELT Pd.D, Xi, Xe : next iteration predicate Pd = [ while i++ < e ]
- Vectors stores to stack must be dynamically allocated and indexed, so...
  - ADDVL SP, SP, #-4 : decrement stack pointer by (4\*VL)
  - STR Zi, [SP, #3, MUL VL] : store vector Z1 to address (SP+3\*VL)

#### Vectorizing A Scalar Loop WithACLE

```
a[i] = 2.0 * a[i];
```

##### Original Code

```
for (int i=0; i < N; ++i) {  
    a[i] = 2.0 * a[i];  
}
```

##### 128-bit NEON vectorization

```
int i;  
  
// vector loop  
for (i=0; (i<N-3) && (N&~3); i+=4) {  
    float32x4_t va = vld1q_f32(&a[i]);  
    va = vmulq_n_f32(va, 2.0);  
    vst1q_f32(&a[i], va)  
}  
  
// drain loop  
for (; i < N; ++i)  
    a[i] = 2.0 * a[i];
```

This is NEON,  
not SVE!

#### Vectorizing A Scalar Loop WithACLE

```
a[i] = 2.0 * a[i];
```

```
for (int i=0; i < N; ++i) {  
    a[i] = 2.0 * a[i];  
}
```

##### 128-bit NEON vectorization

```
int i;  
  
// vector loop  
for (i=0; (i<N-3) && (N&~3); i+=4) {  
    float32x4_t va = vld1q_f32(&a[i]);  
    va = vmulq_n_f32(va, 2.0);  
    vst1q_f32(&a[i], va)  
}  
  
// drain loop  
for (; i < N; ++i)  
    a[i] = 2.0 * a[i];
```

#### SVE vectorization

```
for (int i = 0; i < N; i += svcntw() )  
{  
    svbool_t Pg = svwhilelt_b32(i, N);  
    svfloat32_t va = svld1(Pg, &a[i]);  
    va = svmul_x(Pg, va, 2.0);  
    svst1(Pg, &a[i], va);  
}
```

#### Vectorizing A Scalar Loop WithACLE

```
a[i] = 2.0 * a[i];
```

```
for (int i=0; i < N; ++i) {  
    a[i] = 2.0 * a[i];  
}
```

#### SVE vectorization

```
for (int i = 0; i < N; i += svcntw() )  
{  
    svbool_t Pg = svwhilelt_b32(i, N);  
    svfloat32_t va = svld1(Pg, &a[i]);  
    va = svmul_x(Pg, va, 2.0);  
    svst1(Pg, &a[i], va);  
}
```

##### Assembly ``` armclang -march=armv8.2-a+sve -O3 -S sve2.c ```

```
cmp w0, #1  
b.lt .LBB0_3  
  
mov w8, wzr  
.LBB0_2:  
whilelt p0.s, w8, w0  
sxtw x9, w8  
ld1w { z0.s }, p0/z, [x1, x9, lsl #2]  
incw x8  
cmp w8, w0  
fmul z0.s, p0/m, z0.s, #2.0  
st1w { z0.s }, p0, [x1, x9, lsl #2]  
b.lt .LBB0_2  
.LBB0_3:  
ret
```

#### SVE Gives You More

- SVE is really powerful (mainly due to predicates)
  - Compilers can exploit this power
  - Autovectorisation getting much better
- Power is also being able to vectorise new things
  - Previously hard to vectorise
  - Mapping IF statements to predicates
- Shown in the following real-world example
  - Users code had a 'mask' in the inner loop
  - Previously prevented vectorisation

#### More Complex Example

#### Code

```
void foo(char* mask,  
        double * result, int n)  
{  
    for (int x = 0; x < n; x++)  
        if(mask[x] == 0)  
            result[x] += 2.0;  
}
```

```
armclang -S -march=armv8.2-a+sve -O3 sve.c
```

#### Assembly

```
.LBB0_7:  
    mov x9, xzr  
    whileo p0.d, xzr, x8  
    mov z0.d, #0  
    fmov z1.d, #2.000000000  
  
.LBB0_8:  
    ld1b { z2.d }, p0/z, [x0, x9]  
    cmpeq p0.d, p0/z, z2.d, z0.d  
    ld1d { z2.d }, p0/z, [x1, x9, lsl #3]  
    fadd z2.d, z2.d, z1.d  
    st1d { z2.d }, p0, [x1, x9, lsl #3]  
    incd x9  
    whileo p0.d, x9, x8  
    b.mi .LBB0_8  
  
.LBB0_9:  
    ret
```

#### Annotations

Generate initial loop predicate

Generate initial register values

Load mask with loop predicate

Generate predicate mask[i]==0

Load result with mask predicate

Addition with mask predicate

Store with mask predicate

Loop counter increment

Generate new loop predicate

Loop

arm

#### Toolchain Support

Getting Help

### How to Make Use of SVE

#### Using the tools that are available

- Many ways to use SVE in your application
  - Different levels of effort, reward and portability
- SVE libraries
  - Such as SVE ArmPL for SVE maths operations, just link the correct version
- Auto-vectorisation
  - Compiler spots vectorisation and exploits it, compiler reports to inform
    - `-march=armv8-a+sve`
- Pragmas
  - Help and guide auto-vectorisation (e.g. OMP SIMD, IVDEP)
- Intrinsics
  - ACLE for SVE - friendly interface into SVE instructions
- Assembly
  - Hand code your SVE instructions

#### Arm Compiler for Linux user-space

Commercial C/C++/Fortran compiler with best-in-class performance

![Icon representing data storage or servers, used for the first feature.](ea6ece883b48a4d2836837ec994657f0_img.jpg)

Icon representing data storage or servers, used for the first feature.

Compilers tuned for Scientific Computing and HPC

##### Tuned for Scientific Computing, HPC and Enterprise workloads

- Processor-specific optimizations for various server-class Arm-based platforms
- Optimal shared-memory parallelism using latest Arm-optimized OpenMP runtime

![Icon representing a speedometer or performance gauge, used for the second feature.](b1795618eec028c987e87649aeb360bb_img.jpg)

Icon representing a speedometer or performance gauge, used for the second feature.

Latest features and performance optimizations

##### Linux user-space compiler with latest features

- C++ 14 and Fortran 2003 language support with OpenMP 4.5
- Support for Armv8-A and SVE architecture extension
- Based on LLVM and Flang, leading open-source compiler projects

![Icon representing a handshake, used for the third feature.](b7c2a0945280e5c6ec235c51b1c84038_img.jpg)

Icon representing a handshake, used for the third feature.

Commercially supported by Arm

#### Commercially supported by Arm

- Available for a wide range of Arm-based platforms running leading Linux distributions – RedHat, SUSE and Ubuntu

#### Arm Compiler – Auto-vectorization

##### LLVM9

- Arm pulls all relevant cost models and optimizations into the downstream codebase.
- Auto-vectorization via LLVM **vectorizers**:
  - Use cost models to drive decisions about what code blocks can and/or should be vectorized.
  - Since October 2018, two different vectorizers used from LLVM: [Loop Vectorizer](#) and [SLP Vectorizer](#).
- Loop Vectorizer support for SVE and NEON:
  - Loops with unknown trip count
  - Runtime checks of pointers
  - Reductions
  - Inductions
  - “If” conversion
  - Pointer induction variables
  - Reverse iterators
  - Scatter / gather
  - Vectorization of mixed types
  - Global structures alias analysis

#### New: ACFL Vectorisation Reports

‘-fsave-optimization-record’ & ‘arm-opt-report file.opt.yaml’

```
$ armclang -O3 or.c -c -o or.o -fsave-optimization-record -march=armv8-a+sve
$ arm-opt-report or.opt.yaml
```

< or.c

```
1 | void bar();
2 | void foo() { bar(); }
3 |
4 | void Test(int *res, int *c, int *d, int *p, int n) {
5 |     int i;
6 |
7 | #pragma clang loop vectorize(assume_safety)
8 |     for (i = 0; i < 1600; i++) {
9 |         res[i] = (p[i] == 0) ? res[i] : res[i] + d[i];
10 |     }
11 |
12 |     for (i = 0; i < 16; i++) {
13 |         res[i] = (p[i] == 0) ? res[i] : res[i] + d[i];
14 |     }
15 |
16 |     foo();
17 |
18 |     foo(); bar(); foo();
19 | }
```

Vectorized

4x 32-bit lanes

1-way  
interleaving

Fully  
unrolled

All 3 instances of  
foo() were  
inlined

#### Arm Performance Libraries

Optimized BLAS, LAPACK and FFT

![Now With SVE logo](4c8721520bc36623aa6c19562146bab9_img.jpg)

Now With SVE logo

![Icon of two hands shaking](c391b0a0928f19ae05b796299c4abfaa_img.jpg)

Icon of two hands shaking

Commercially supported  
by Arm

![Icon of a speedometer](088933666d010cbfb12581f0e8c3d045_img.jpg)

Icon of a speedometer

Best in class performance

![Icon of a checklist](70f89886abc3f0c7d46be7412bb4bbf8_img.jpg)

Icon of a checklist

Validated with  
NAG test suite

##### Commercial 64-bit Armv8-A math libraries

- Commonly used low-level math routines - BLAS, LAPACK and FFT
- Provides FFTW compatible interface for FFT routines
- Sparse linear algebra and batched BLAS support
- libamath gives high-performing math.h functions implementations

##### Best-in-class serial and parallel performance

- Generic Armv8-A optimizations by Arm
- Tuning for specific platforms like Marvell ThunderX2 in collaboration with silicon vendors

#### Validated and supported by Arm

- Available for a wide range of server-class Arm-based platforms
- Validated with NAG's test suite, a de-facto standard

#### SVE Compiler Support

![GCC logo featuring a bull head.](227a123b49ae9a5715dc7885e638d3e0_img.jpg)

GCC logo featuring a bull head.

![Stylized black bird or dragon logo.](36bb407df7b71163bd6f82d7bb2b47fa_img.jpg)

Stylized black bird or dragon logo.

![FUJITSU logo.](9e3dccfc3a1dfa5759408d1269137ed0_img.jpg)

FUJITSU logo.

![CRAY logo.](3a72302c41d1a35116b0c294df7aac60_img.jpg)

CRAY logo.

| Compiler             | Assembly / Disassembly | Inline Assembly | ACLE                  | Auto-vectorization    | Math Libraries |
|----------------------|------------------------|-----------------|-----------------------|-----------------------|----------------|
| Arm Compiler for HPC | SVE + SVE2             | SVE + SVE2      | SVE + SVE2            | SVE + SVE2            | SVE            |
| LLVM/Clang           | SVE + SVE2             | SVE + SVE2      | SVE + SVE2 in LLVM 10 | SVE + SVE2 in LLVM 11 |                |
| GNU                  | SVE + SVE2             | SVE + SVE2      | SVE + SVE2 in GNU 10  | SVE now SVE2 in GNU10 |                |

arm

Realising SVE

#### The First SVE CPU - Available ~Now

##### Fujitsu A64FX

- Custom Arm design by Fujitsu
- 512-bit SVE
- 4 Core Memory Groups
  - 12 cores + 1 OS core
  - 8 GB High Bandwidth Memory (HBM)
- 1 socket / node, 2 nodes / blade
  - Direct water cooling

![Close-up view of the Fujitsu A64FX CPU blade showing the large copper heat spreader and water cooling channels.](3489a3f420d1f2d8b7d626d3a6851388_img.jpg)

Close-up view of the Fujitsu A64FX CPU blade showing the large copper heat spreader and water cooling channels.

![Diagram of the Fujitsu A64FX CPU die showing the core layout, memory groups, and interfaces. The die features multiple core clusters, L2 caches, and connections to the HBM2 interface, TofuD interface, and PCIe interface.](e999b14cdba9a4824937bb35d8489a03_img.jpg)

Diagram of the Fujitsu A64FX CPU die showing the core layout, memory groups, and interfaces. The die features multiple core clusters, L2 caches, and connections to the HBM2 interface, TofuD interface, and PCIe interface.

##### A64FX Now in Top500 - #159

| System                                                                       | Year | Vendor | Cores  | Rmax<br>(GFlop/s) | Rpeak<br>(GFlop/s) |
|------------------------------------------------------------------------------|------|--------|--------|-------------------|--------------------|
| A64FX prototype - Fujitsu A64FX, Fujitsu A64FX 48C 2GHz, Tofu interconnect D | 2019 |        | 36,864 | 1,999,500         | 2,359,296          |

##### Green500 - #1

| Rank | TOP500 | System                                                                                                           | Cores  | Rmax      | Power | Power                        |
|------|--------|------------------------------------------------------------------------------------------------------------------|--------|-----------|-------|------------------------------|
|      | Rank   |                                                                                                                  |        | (TFlop/s) | (kW)  | Efficiency<br>(GFlops/watts) |
| 1    | 159    | A64FX prototype - Fujitsu A64FX, Fujitsu A64FX 48C 2GHz, Tofu interconnect D, Fujitsu Fujitsu Numazu Plant Japan | 36,864 | 1,999.5   | 118   | 16.876                       |

![Image of a Fujitsu A64FX supercomputer system, featuring a black and red server rack with the Fujitsu logo and an infinity symbol.](04201bc1cef022cb47c075c55fb6c98c_img.jpg)

Image of a Fujitsu A64FX supercomputer system, featuring a black and red server rack with the Fujitsu logo and an infinity symbol.

arm

Post SVE:

The Vector Instructions of  
the Next Generation

#### FMMLA: High Performance Matrix Multiplication

- Added to Armv8.6
  - NEON and SVE instructions
  - FMMLA instructions for FP (SVE)
- FMMLA  $\langle Z_d \rangle$ .S,  $\langle Z_n \rangle$ .S,  $\langle Z_m \rangle$ .S  
  FMMLA  $\langle Z_d \rangle.D,  $\langle Z_n \rangle.D,  $\langle Z_m \rangle.D$$$
- 2x2 matrix multiplication
  - Works on multiple of 'vector granules'
  - $2 \times 2 \times \text{FP32} = 128\text{-bit granules}$
  - Assumes vector length is multiple
- May require layout transformations
  - Outer loop to minimise cost
- Accelerated libraries

| <table border="1"><tbody><tr><td>0</td><td>1</td></tr><tr><td>2</td><td>3</td></tr></tbody></table> | 0 | 1 | 2                               | 3                               | $+$ | $=$ | $\times$ | <table border="1"><tbody><tr><td>0</td><td>1</td></tr><tr><td>2</td><td>3</td></tr></tbody></table> | 0 | 1 | 2 | 3 |
|-----------------------------------------------------------------------------------------------------|---|---|---------------------------------|---------------------------------|-----|-----|----------|-----------------------------------------------------------------------------------------------------|---|---|---|---|
| 0                                                                                                   | 1 |   |                                 |                                 |     |     |          |                                                                                                     |   |   |   |   |
| 2                                                                                                   | 3 |   |                                 |                                 |     |     |          |                                                                                                     |   |   |   |   |
| 0                                                                                                   | 1 |   |                                 |                                 |     |     |          |                                                                                                     |   |   |   |   |
| 2                                                                                                   | 3 |   |                                 |                                 |     |     |          |                                                                                                     |   |   |   |   |
| Dest (D)                                                                                            |   |   | Left (L)                        | Right (R)                       |     |     |          |                                                                                                     |   |   |   |   |
| $2 \times 2 \times \text{FP32}$                                                                     |   |   | $2 \times 2 \times \text{FP32}$ | $2 \times 2 \times \text{FP32}$ |     |     |          |                                                                                                     |   |   |   |   |

$$D[0] += (L[0] * R[0]) + (L[1] * R[1])$$

$$D[1] += (L[0] * R[2]) + (L[1] * R[3])$$

$$D[2] += (L[2] * R[0]) + (L[3] * R[1])$$

$$D[3] += (L[2] * R[2]) + (L[3] * R[3])$$

![](1da66f5fec34c001912c84a9abf145d7_img.jpg)

$4 \times \text{FP32} = 128 \text{ bits}$

Diagram illustrating the 2x2 matrix multiplication process, showing the input vectors  $Z_L$  and  $Z_R$  being multiplied to produce the output vector  $Z_D$ . The calculation involves four parallel 2x2 blocks, each resulting in a 128-bit granule ( $4 \times \text{FP32} = 128 \text{ bits}$ ).

The diagram shows the input elements being multiplied (e.g.,  $0.0 \times 1.1$ ,  $0.2 \times 1.3$ ,  $2.0 \times 3.1$ ,  $2.2 \times 3.3$ ) and summed to produce the final 128-bit result.

#### New Data Type Support: BFloat16

- New addition to Armv8-A
  - Adds support for BF16
- Instructions for NEON and SVE
  - Including:
    - **BFDOT**: Dot Product  $(1\times 2)\times(2\times 1)$
    - **BFMMLA**: Mat Multiply  $(2\times 4)\times(4\times 2)$
- Significant performance gains
  - ML training and inference workloads
- Supported in Arm libraries
  - Arm NN and Arm Compute Libraries

![](5000e9028ee2990f6242b2c0a952010d_img.jpg)

Diagram illustrating the bit layout for three floating-point formats:

| Format                     | Bits (15-0)         | Sign | Exponent | Fraction | Breakdown                          |
|----------------------------|---------------------|------|----------|----------|------------------------------------|
| IEEE FP16 half-precision   | 15 14 10 9 0        | S    | exponent | fraction | 1b sign, 5b exponent, 10b fraction |
| BF16 bfloat16              | 15 14 7 6 0         | S    | exponent | fraction | 1b sign, 8b exponent, 7b fraction  |
| IEEE FP32 single-precision | 31 30 23 22 16 15 0 | S    | exponent | fraction | 1b sign, 8b exponent, 23b fraction |

#### Scalable Vector Extensions V2 (SVE2)

#### SVE for non HPC markets

![Icon representing SVE foundation: a central cube connected to four smaller cubes.](34af3678e28d5fc4f9116198a4ec28b8_img.jpg)

Icon representing SVE foundation: a central cube connected to four smaller cubes.

Built on SVE

- Built on the SVE foundation.
  - Scalable vectors with hardware choice from 128 to 2048 bits.
  - Vector-length agnostic programming for “write once, run anywhere”.
  - Tackles some obstacles to compiler auto-vectorisation.
- Scaling single-thread performance to exploit long vectors.
  - SVE2 adds NEON™-style fixed-point DSP/multimedia plus other new features.
  - Performance parity and beyond with classic NEON DSP/media SIMD.
  - Tackles further obstacles to compiler auto-vectorization.
- Enables vectorization of a wider range of applications than SVE.
  - Multiple use cases in Client, Edge, Server and HPC.
    - DSP, Codecs/filters, Computer vision, Photography, Game physics, AR/VR,
    - Networking, Baseband, Database, Cryptography, Genomics, Web serving.
  - Improves competitiveness of Arm-based CPU vs proprietary solutions.
  - Reduces s/w development time and effort.

![Icon representing improved scalability: a large cube connected to a smaller cube.](92dce1b40f244557eaed7c73a97bafba_img.jpg)

Icon representing improved scalability: a large cube connected to a smaller cube.

Improved scalability

![Icon representing vectorization of more workloads: four smaller cubes arranged in a 2x2 grid.](a6e078ee88b9c9a47ca03cf0779db47f_img.jpg)

Icon representing vectorization of more workloads: four smaller cubes arranged in a 2x2 grid.

Vectorization of  
more workloads

#### SVE2 Instructions Add:

#### What's new

- Thorough support for fixed-point DSP arithmetic
  - (traditional Neon DSP/Media processing, complex numbers arithmetic for LTE)
- Multi-precision arithmetic
  - (bignum, crypto)
- Non-temporal gather/scatter
  - (HPC, sort)
- Enhanced permute and bitwise permute instructions
  - (CV, FIR, FFT, LTE, ML, genomics, cryptanalysis)
- Histogram acceleration support
  - (CV, HPC, sort)
- String processing acceleration support
  - (parsers)
- (optional) Cryptography support instructions for AES, SM4, SHA standards
  - (encryption)

##### Example: Widening and Narrowing

#### NEON vs SVE2

#### NEON

UADDL Vd.2D, Vn.2S, Vm.2S

![](6a7053cf740d86c2b7cca3cf67a9564b_img.jpg)

Diagram illustrating UADDL Vd.2D, Vn.2S, Vm.2S. The input vectors Vn.2S and Vm.2S are split into high (d, c) and low (b, a) halves. The low halves (b and a) are added, resulting in the low half of the output vector (b+n, a+m).

UADDL2 Vd.2D, Vn.4S, Vm.4S

![](5f7d01d7025c1fb35ed8adf53f9fd8e5_img.jpg)

Diagram illustrating UADDL2 Vd.2D, Vn.4S, Vm.4S. The input vectors Vn.4S and Vm.4S are split into odd (d, c) and even (b, a) halves. The odd halves (d and c) are added, resulting in the odd half of the output vector (d+p, c+o). The even halves (b and a) are added, resulting in the even half of the output vector (b+n, a+m).

- NEON uses high/low half of vector
- Expensive for large vector lengths
  - >> 128-bit

#### SVE2

UADDLB Zd.D, Zn.S, Zm.S

![](edfcf246c5c2d9d6638f872c37bed2b1_img.jpg)

Diagram illustrating UADDLB Zd.D, Zn.S, Zm.S. The input vectors Zn.S and Zm.S are split into odd (d, c) and even (b, a) halves. The odd halves (d and c) are added, resulting in the odd half of the output vector (c+o). The even halves (b and a) are added, resulting in the even half of the output vector (a+m).

UADDLT Zd.D, Zn.S, Zm.S

![](aafe4112778931ebe3b882d9afc307a2_img.jpg)

Diagram illustrating UADDLT Zd.D, Zn.S, Zm.S. The input vectors Zn.S and Zm.S are split into odd (d, c) and even (b, a) halves. The odd halves (d and c) are added, resulting in the odd half of the output vector (d+p). The even halves (b and a) are added, resulting in the even half of the output vector (b+n).

- SVE2 uses odd/even half of vector
- Bottom and top
- Happens 'in-lane'

### Transactional Memory Extension (TME)

Scalable Thread-Level Parallelism (TLP) for multi-threaded applications

![Icon representing Hardware Transactional Memory, showing a stack of layers.](91adc884c2a1e14b3258c20f3bd85c3c_img.jpg)

Icon representing Hardware Transactional Memory, showing a stack of layers.

Hardware Transactional Memory

![Icon representing Improved scalability, showing two stacked cubes.](74f85242c070a96bf758f513b1db6572_img.jpg)

Icon representing Improved scalability, showing two stacked cubes.

Improved scalability

![Icon representing Simpler software design, showing a computer monitor displaying binary code.](bb33b19af6e384bda6f0975f108ada47_img.jpg)

Icon representing Simpler software design, showing a computer monitor displaying binary code.

Simpler software design

- Hardware Transactional Memory (HTM) for the Arm architecture.
  - Improved competitiveness with other architectures that support HTM. • Strong isolation between threads.
  - Failure atomicity.
- Scaling multi-thread performance to exploit many-core designs.
  - Database.
  - Network dataplane.
  - Dynamic web serving.
- Simplifies software design for massively multi-threaded code.
  - Supports Transactional Lock Elision (TLE) for existing locking code.
  - Low-level concurrent access to shared data is easier to write and debug.

arm

Conclusion

### Vector Instruction Sets on Arm

- Arm is new to HPC but has a compelling justification and heritage
- Arm has a constantly evolving set of vector instructions
  - From NEON to SVE and beyond
- Designed to give flexibility to hardware designers
  - Maximise ability to differentiate
  - Still present a consistent end-user experience
- Designed for real use-cases for improved performance
  - Started with HPC workloads
  - Moving to AI / ML server

arm

\*The Arm trademarks featured in this presentation are registered trademarks or trademarks of Arm Limited (or its subsidiaries) in the US and/or elsewhere. All rights reserved. All other marks featured may be trademarks of their respective owners.

[www.arm.com/company/policies/trademarks](http://www.arm.com/company/policies/trademarks)