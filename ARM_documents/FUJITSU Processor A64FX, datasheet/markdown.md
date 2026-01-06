

![Fujitsu logo](935eed7aa61f7777f62cfc032e11bee9_img.jpg)

Fujitsu logo

# FUJITSU Processor A64FXInnovative Arm-based HPC processor

## Designed for the new generation of massive parallel computing

![Image of the A64FX processor chip](5fb340ad68b0c71df0b56698b137e35b_img.jpg)

Image of the A64FX processor chip

The processor integrates 52 processor cores including assistant cores; a memory controller supporting HBM2; a Tofu interconnect D controller; and a root complex supporting PCI-Express Gen3. The A64FX adopts several characteristic architectures for HPC.

The A64FX processor (called A64FX, below) is a superscalar processor of the out-of-order execution type. The A64FX is designed for high-performance computing (HPC) and complies with the Armv8-A architecture profile and the Scalable Vector Extension for Armv8-A.

The A64FX becomes the heart of supercomputers that can perform quick simulations and analyze large data sets. Supercomputers with this processor perform at a high level, are highly reliable and offer a strong performance vs. power ratio.

![Diagram of the A64FX processor showing Core Memory Group (13 Cores, L2S 8MB, Mem 8GiB, 256GiB/s), Tofu D (28 Gbps, 2 lanes, 10 ports), I/O (PCIe Gen3, 16 lanes), and Network on Chip.](88096eec96db1b919e141720a47f97c6_img.jpg)

Diagram of the A64FX processor showing Core Memory Group (13 Cores, L2S 8MB, Mem 8GiB, 256GiB/s), Tofu D (28 Gbps, 2 lanes, 10 ports), I/O (PCIe Gen3, 16 lanes), and Network on Chip.

## A64FX Main Features

| <b>Predicted Operations</b>          | Enable selectively operate, load, and store only specific SIMD elements.                                                                                                                                                                                       |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <b>Four-operand FMA</b>              | In the operation of $A \times B + C \Rightarrow D$ , the register of A, B, C, and D can be freely selected. Although Armv8-A SIMD has only $A \times B + C \Rightarrow D$ operations, the A64FX realizes Four-operand FMA by packing with MOVPRFX instruction. |
| <b>Gather/Scatter</b>                | Reads discontinuous data in memory and converts to SIMD (vectorization). Writes SIMD (Vector) data to non-contiguous area in memory.                                                                                                                           |
| <b>Math. Acceleration</b>            | Speeds up when finding trigonometric and exponential functions.                                                                                                                                                                                                |
| <b>Compress</b>                      | Aggregates data that is sparse on registers.                                                                                                                                                                                                                   |
| <b>First Fault Load</b>              | Suppresses and records traps other than the first element in memory access instructions.                                                                                                                                                                       |
| <b>Hardware Barrier</b>              | Supports synchronization between software processes or threads through hardware for simplification of programs and higher-speed synchronization processing.                                                                                                    |
| <b>Sector Cache</b>                  | Provides software with a method of controlling the use of the L1 and L2 cache by partitioning each cache.                                                                                                                                                      |
| <b>FP16/ INT16/ INT8 Dot Product</b> | Introduced for AI applications.                                                                                                                                                                                                                                |

## Fujitsu Processor A64FX Specifications

| CPU Specifications                    |                                                                        |                                         |
|---------------------------------------|------------------------------------------------------------------------|-----------------------------------------|
| ISA                                   | Armv8.2-A + SVE                                                        |                                         |
| Number of Processor Cores             | 48 compute cores, and 2 or 4 assistant cores *                         |                                         |
| Threads                               | 48                                                                     |                                         |
| Base Frequency                        | 1.8GHz, 2.0GHz, 2.2GHz                                                 |                                         |
| Turbo Frequency                       | None (same as base frequency)                                          |                                         |
| SIMD Width                            | 512bit                                                                 |                                         |
| L1I Cache Size                        | 3MiB (64KiB /core)                                                     |                                         |
| L1D Cache Size                        | 3MiB (64KiB /core)                                                     |                                         |
| L2 Cache Size                         | 32MiB (8MiB x 4)                                                       |                                         |
| Cache-Line Size                       | 256 bytes                                                              |                                         |
| Memory Controller                     | 4                                                                      |                                         |
| SVE-Implemented Vector Length         | 128 / 256 / 512bits                                                    |                                         |
| Peak Flops; D / S / H<br>[FLOPS]      | 1.8GHz                                                                 | 2.7648T / 5.5296T / 11.0592T            |
|                                       | 2.0GHz                                                                 | 3.072T / 6.144T / 12.288T               |
|                                       | 2.2GHz                                                                 | 3.3792T / 6.7584T / 13.5168T            |
| Peak Int Ops; 8 / 4 / 2 / 1B<br>[OPS] | 1.8GHz                                                                 | 2.7648T / 5.5296T / 11.0592T / 22.1184T |
|                                       | 2.0GHz                                                                 | 3.072T / 6.144T / 12.288T / 24.576T     |
|                                       | 2.2GHz                                                                 | 3.3792T / 6.7584T / 13.5168T / 27.0336T |
| Network                               | Tofu interconnect D [68GB/s x2 (in/out)] *                             |                                         |
| IO / Socket                           | PCIe Gen3 16 lanes [15.75GB/s(in/out)]<br>(Need chipsets for USB/SATA) |                                         |
| Process Technology                    | 7 nm CMOS FinFET                                                       |                                         |
| Number of Transistors                 | 8,786M pcs                                                             |                                         |
| Package Signal Pins                   | 594 BGA pins                                                           |                                         |

\* Only when the frequency is 2.2 GHz

| Memory Specifications             |                           |            |
|-----------------------------------|---------------------------|------------|
| Memory Bandwidth                  | 1,024 GB/s                |            |
| Memory Capacity                   | 32 GiB                    |            |
| Number of HBM2 Stacks Per Package | 4                         |            |
| HBM2                              | Data Signal Transfer Rate | 2.0 Gbps   |
|                                   | Data Width                | 1,024 bits |
|                                   | Memory Bandwidth          | 256 GB/s   |
|                                   | Memory Capacity           | 8 GiB      |

![Fujitsu logo](b0d31e6842af4e5cee75a79f4eac72ff_img.jpg)

Fujitsu logo

Website: www.fujitsu.com

© Copyright 2021 Fujitsu and the Fujitsu logo are trademarks or registered trademarks of Fujitsu Limited in Japan and other countries. Other company, product and service names may be trademarks or registered trademarks of their respective owners. Technical data subject to modification and delivery subject to availability. Any liability that the data and illustrations are complete, actual or correct is excluded. Designations may be trademarks and/or copyrights of the respective manufacturer, the use of which by third parties for their own purposes may infringe the rights of such owner.