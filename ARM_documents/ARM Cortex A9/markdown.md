

# ARM Cortex A9

Alyssa Colyette  
Xiao Ling Zhuang

## Outline

- Introduction
- ARMv7-A ISA
- Cortex-A9 Microarchitecture
  - Single and Multicore Processor
- Advanced Multicore Technologies
- Integrating System on Chips

## Introduction

- ARM Cortex-A9 is the 2nd generation of ARM MPCore technology series
- High performance
- Uses ARMv7-A ISA
- Used many embedded devices due to its ability to control different level of power consumption
  - essential for mobile devices

## ARMv7-A Architecture

- RISC-based
- Implement two instruction sets
  - 32-bit ARM instruction set
  - 16-bit Thumb-2 instruction set
  - switch ISA as branch or exception
- 37 registers, all 32-bit long
- Support shared and local memory
- Has configurable cache policy
- Backward compatibility

## Application Specific Optimization

- 2.50 DMIPS/MHz (Dhrystone)
- Clock rate: 800MHz ~ 2GHz
- NEON Media and Floating Point Processing Engine
- Cache coherence option for enhanced inter-process communication
- Thumb-2 Technology: 30% reduction in memory required to store instruction
- TrustZone Technology
- L2 Cache Controller

## Cortex-A9 Single Core Microarchitecture

![](c54b3ca7603d65d4589151bc3a49d054_img.jpg)

This diagram illustrates the Cortex-A9 Single Core Microarchitecture and its interfaces.

The core components of the **Cortex-A9 Single core Processor** include:

- **Instruction Fetch Stage:** Instruction prefetch stage, Dual-instruction Decode stage, and Branches.
- **Execution Stage:** Register Rename stage, Out of order multi-issue with speculation (Instruction queue and Dispatch stage), and OoO Write back stage.
- **Execution Units:** ALU/MUL, ALU, FPU/NEON, and Address unit.
- **Memory System:** Auto-prefetcher, Load-Store Unit (with Store Buffer and quad-slot with forwarding),  $\mu$ TLB, MMU, Data Cache, and Program Trace Unit.
- **Debug/Trace:** CoreSight / JTAG Debug, CoreSight Debug Access Port, Profiling Monitor Block, and CoreSight Trace.
- **Interrupts:** IRQ/FIQ, PL390 Interrupt Controller.

The processor connects to the **PL310 L2 Cache Controller**, which includes L2 Cache Control, Bus Interface Unit (BIU) with Master interface and Secondary master (with filtering), and ECC RAMs. The BIU connects to the AMBA 3 AXI 64bit bus.

Cortex-A9 Microarchitecture Structure and the Single Core Interfaces

### Microarchitecture: Instruction Fetch

![](73c3e4508cae529acf4e6c7fa70b361a_img.jpg)

Diagram illustrating the Instruction prefetch stage components:

- Instruction prefetch stage
- Fast-loop mode
- Instruction cache
- Branch Prediction
  - Global History Buffer
  - BR-Target Addr Cache
  - Return Stack

- Instruction cache size: 16, 32, or 64KB
- Fetching two instructions
- Branch prediction:
  - Global History Buffer: 1-16K entries, 2-bit
  - Branch-Target Address Cache: 512-4K entries, 2-way
  - Return stack of 8 x 32 bits
- Fast-loop mode: instruction loop smaller than 64 bytes complete without additional cache accesses

### Microarchitecture: Instruction Decode

![](892f25e3d71d8e315a2a51092a8a8da7_img.jpg)

Diagram illustrating the Dual-instruction Decode stage. The stage is shown as a large blue box labeled "Dual-instruction Decode stage". Below it, two smaller green boxes feed into the stage: "Instruction queue" on the left and "Prediction queue" on the right. Arrows indicate that instructions are input into the Dual-instruction Decode stage from both queues.

- Superscalar Decoder
  - capable of decoding two full instructions per cycle

### Microarchitecture: Rename

![](d4e9f8f6bf5d7853ecae9c9633900af1_img.jpg)

Diagram illustrating the Register Rename stage in microarchitecture. The stage consists of three components:

- Virtual to physical register pool (Top component)
- Register Rename stage (Middle component)
- Branches (Bottom component)

Arrows indicate data flow: Input flows into the Register Rename stage, and output flows out. The Branches component is connected below the Register Rename stage.

- Register Renaming
  - resolving data dependencies
  - loop unrolling

### Microarchitecture:Issue

![](4e0ade2f41b66d5602160da5cc978274_img.jpg)

Diagram illustrating the Issue unit structure:

- Out of order multi-issue with speculation
- Instruction queue and Dispatch
- 3+1 Dispatch stage

- Issue can feed max. of 2 instructions per cycle
- Can dispatch up to 4 instructions per cycle
- Out of order selection of instructions from the issue queue

### Microarchitecture: Execute

- Concurrent execution
- variable length of executing stage (1-3 cycles)
  - ADD R0, R1, R2 (1 cycle)
  - ADD R0, R1, R2 LSL #2 (2 cycle)
  - ADD R0, R1, R2 LSL R3 (3 cycle)
- Neon media and/or floating point processing engine

![Diagram illustrating the execution stages of a microarchitecture. Four parallel execution units are shown: ALU/MUL, ALU, FPU/NEON, and Address. The FPU/NEON unit is highlighted, indicating its role in media and floating point processing.](6d9013c24741e861f3c8e0a763b6da22_img.jpg)

Diagram illustrating the execution stages of a microarchitecture. Four parallel execution units are shown: ALU/MUL, ALU, FPU/NEON, and Address. The FPU/NEON unit is highlighted, indicating its role in media and floating point processing.

### NEON Media Process Engine (MPE)

- 128-bit SIMD (single instruction multiple data)
- accelerate multimedia and signal processing algorithms
  - video, 2D/3D graphic, audio and speech processing
- has 32 registers (vectors of elements), 64-bits wide
- data type: signed/unsigned 8-bit, 32-bit, 64-bit, and single precision floating point

![](e3b8510f6a2194e250205ab7bc38076d_img.jpg)

Diagram illustrating the NEON SIMD processing architecture.

The diagram shows three parallel processing units (Lanes) operating on data vectors. Each Lane processes multiple Elements simultaneously.

- **Source Registers:** Located above the Lanes, these registers feed data into the processing units. The width of the Source Registers is indicated by  $D_m$ .
- **Operation:** The processing units perform the required operation on the data.
- **Destination Register:** Located below the Lanes, this register receives the processed data. The width of the Destination Register is indicated by  $D_d$ .

The overall structure demonstrates Single Instruction, Multiple Data (SIMD) processing.

### Floating Point Unit (FPU)

- High-performance single, and double precision floating point instructions
- Double the performance of previous ARM floating point units
- Capable significant enhancing solution with rich graphic, 3D, imaging and scientific computation

### Microarchitecture: Memory

![](0b8b087a7baa471015d3ffeaa43d9a6c_img.jpg)

Diagram illustrating the Microarchitecture Memory components:

- Auto-prefetcher
- Memory System
- Load-Store Unit
- Store Buffer (quad-slot with forwarding)
- $\mu$ TLB
- MMU
- Data Cache

- Data forwarding
- 2-level TLB structure
  - Micro and main TLB
- Data prefetcher
  - monitor cache line requests by processor
  - supports 4 cache line fill requests

#### Memory Hierarchy

- L1 cache
  - split, non-unified
    - 32KB data and 32KB instruction
  - 4-way associative
- L2 cache
  - shared, unified
  - 128KB to 8MB
  - 4 to 16-way associative

### Microarchitecture: Writeback

![Diagram of a microarchitecture component, specifically the Out of Order Writeback stage. It is a vertical blue rectangle with an orange border, showing four input/output arrows on the left side. The text inside reads: OoO Write back stage.](662933fe00899933b36b5a214ac6095c_img.jpg)

Diagram of a microarchitecture component, specifically the Out of Order Writeback stage. It is a vertical blue rectangle with an orange border, showing four input/output arrows on the left side. The text inside reads: OoO Write back stage.

- Out of order write back of instructions

## Cortex-A9 MultiCore Processor

![](af06598cfb31b517e79b50d74f72a0ca_img.jpg)

Diagram illustrating the Cortex-A9 MultiCore Processor Configuration.

The architecture is built around four identical Cortex-A9 CPU cores, each featuring an FPU/NEON unit, a PTM I/F, an Instruction Cache, and a Data Cache.

These cores connect to a shared subsystem below, which includes:

- Generalized Interrupt Control and Distribution
- Snoop Control Unit (SCU), which contains Cache-2-Cache Transfers, Snoop Filtering, and Timers.
- Accelerator Coherence Port
- Advanced Bus Interface Unit, which includes a Primary AMBA 3 64bit Interface and an Optional 2<sup>nd</sup> I/F with Address Filtering.

The Advanced Bus Interface Unit connects to the L2 Cache Controller (PL310).

The entire configuration is supported by the ARM CoreSight™ Multicore Debug and Trace Architecture.

Cortex-A9 Multicore Processor Configuration

## Cortex-A9 MultiCore Processor

- support between 1-4 CPU in an integrated cache coherent manner
- cache size, FPU (float point unit), PTM (program flow trace macrocell), MPE (media processing engine) interfaces can be configured
- support either single or dual 64-bit AMBA 3 AXI interface

### Cortex-A9 MPCore Technology: Snoop Control Unit (SCU)

- central intelligence
- responsible for managing:
  - interconnect
  - arbitration
  - communication
  - cache-2-cache
  - system memory transfer
  - cache data coherence

### Cortex-A9 MPCore Technology: Accelerator Coherence Port

- 64-bit slave port
- supports all standard read and write transactions
- follow L1 write through and L2 write back policy

![](96a7eac66ef72bb016c280278506ac63_img.jpg)

Diagram illustrating the Cortex-A9 MPCore Technology Accelerator Coherence Port architecture.

The Cortex-A9 MPCore (1-4 CPUs) contains CPU, CPU, CPU, and MPCore Technology / SCU components. The MPCore Technology / SCU connects to the Local Coherence Bus (no snooping on bus) via AMBA 3 AXI.

The Local Coherence Bus connects to DMA and Crypto accelerators.

**Example: Write**  
Writes clean and invalidates L1 lines if necessary. Optionally allocating into the shared L2 cache.

**Example: Read**  
May hit and resolve in CPU's L1 cache. Else may hit in shared L2 cache. Else read from main memory.

The bus connects to L2 Cache, which is shared with per-master lockdown to limit high-throughput master flooding. L2 Cache connects to Main Memory / SoC.

### Cortex-A9 MPCore Technology: Generic Interrupt Controller

- supports up to 224 independent interrupts
- can interpret private (TrustZone) I/O interrupts and regular interrupts (OS layer)
- distributed across CPU and hardware prioritized

### Cortex-A9 MPCore Technology: Advanced Bus Interface Unit

- enhance the interface between processor and system
- capable of exceeding 12GB/s into the system interconnect
- offer different CPU to bus frequency ratios
- support advance power management

### Advanced L2 Cache Controller

- Used to help utilized the performance and throughput of the processor
  - disabled by default
- Serves as a monitor for memory accesses to the L2 cache between CPUs
- supporting up to 8MB, with between 4 and 16-way associative L2 cache

## Apple A5

![Image of the Apple A5 CPU chip.](7cdd3a0b8107619a3a05ea9ed16eff02_img.jpg)

Image of the Apple A5 CPU chip.

- iPhone 4s, iPad2, iPad mini
- consists of a dual-core ARM Cortex-A9 MPCore CPU
- Max. CPU clock rate
  - 0.8GHz for iPhone 4s
  - 1GHz for iPad2, mini
- L1 cache: 32 KB instruction + 32 KB data
- L2 cache: 1 MB

![Image of an iPhone 4s.](c613ca237231251d524291a877d91f7a_img.jpg)

Image of an iPhone 4s.

![Image of two iPads, one displaying the home screen and the other displaying a web browser.](ca81500b365ed30190cb2d9c38fc1f84_img.jpg)

Image of two iPads, one displaying the home screen and the other displaying a web browser.

### OMAP4

- Motorola Razr, kindle Fire, PandaBoard
- version 4430, 4460, and 4470
  - 4470 has increased power efficiency up to 50-90%
- CPU frequency 1 to 1.5 GHz
- MIT Project: Ubuntu mini-cluster of 48 PandaBoards operating at 200W

![Image showing three Kindle Fire tablets.](56a7fc5964ed9463fa47ca8a60568dec_img.jpg)

Image showing three Kindle Fire tablets.

![Image showing a circuit board, likely a PandaBoard.](a8807f349e4e4d1d425fe4148f81741d_img.jpg)

Image showing a circuit board, likely a PandaBoard.

![Image showing a Motorola Razr smartphone and a stylus.](d4c143a69ccd7e28fe8d01dbc9dfbcfa_img.jpg)

Image showing a Motorola Razr smartphone and a stylus.

## PlayStation Vita SoC

- 4 Cortex-A9 processors
- Graphics: Quad-core PowerVR SGX543MP4+
- 2 GHz CPU clock rate
- Power: 2200 mAh, 3-5 hours
- 2.2 million units sold

![A black PlayStation Vita handheld console displaying the home screen with various game icons.](0ccbf2e1f1d9d0aae8865d824a1fc322_img.jpg)

A black PlayStation Vita handheld console displaying the home screen with various game icons.

### Exynos 4

- Samsung Galaxy S III, Galaxy Note
- Quad-core ARM Cortex A-9
- CPU: 1.4-1.6 GHz
- over 10 million note sold
- over 50 million of S III sold

![Two Samsung Galaxy Note smartphones displayed side-by-side. The left phone shows a calendar application, and the right phone shows a handwritten note application with a stylus.](39cfe42bf47ba1f871d52952bfbdfab1_img.jpg)

Two Samsung Galaxy Note smartphones displayed side-by-side. The left phone shows a calendar application, and the right phone shows a handwritten note application with a stylus.

![A single Samsung Galaxy S III smartphone displayed, showing the time 12:45 and a dandelion background image.](8f931bb1d65d0ee4ccafab751ee61282_img.jpg)

A single Samsung Galaxy S III smartphone displayed, showing the time 12:45 and a dandelion background image.

## References

- <http://www.arm.com/products/processors/cortex-a/cortex-a9.php>
- <http://www.arm.com/files/pdf/ARM Cortex A-9 Processors.pdf>
- <http://www.arm.com/products/processors/technologies/neon.php>
- <http://www.arm.com/products/processors/technologies/vector-floating-point.php>
- [http://en.wikipedia.org/wiki/ARM\\_Cortex-A9\\_MPCore](http://en.wikipedia.org/wiki/ARM_Cortex-A9_MPCore)
- [http://en.wikipedia.org/wiki/Apple\\_A5](http://en.wikipedia.org/wiki/Apple_A5)
- <http://en.wikipedia.org/wiki/Exynos>
- [http://en.wikipedia.org/wiki/Texas\\_Instruments\\_OMAP#OMAP\\_4](http://en.wikipedia.org/wiki/Texas_Instruments_OMAP#OMAP_4)
- [http://en.wikipedia.org/wiki/PlayStation\\_Vita](http://en.wikipedia.org/wiki/PlayStation_Vita)
- [http://www.phoronix.com/scan.php?page=article&item=mit\\_cluster\\_build&num=1](http://www.phoronix.com/scan.php?page=article&item=mit_cluster_build&num=1)