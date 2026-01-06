

# Arm Cortex-R Processor Comparison Table

The Cortex-R series of processors deliver fast and deterministic processing and high performance, while meeting challenging real-time constraints in a range of situations. They combine these features in a performance, power and area optimized package, making them the trusted choice in reliable systems demanding high error-resistance.

| Feature                                  | Cortex-R4                          | Cortex-R5                          | Cortex-R7 <sup>1</sup>                   | Cortex-R8                                | Cortex-R52                          | Cortex-R52+                         | Cortex-R82                           |
|------------------------------------------|------------------------------------|------------------------------------|------------------------------------------|------------------------------------------|-------------------------------------|-------------------------------------|--------------------------------------|
| Architecture                             | Armv7-R                            | Armv7-R                            | Armv7-R                                  | Armv7-R                                  | Armv8-R<br>AArch32                  | Armv8-R<br>AArch32                  | Armv8-R<br>AArch64                   |
| Instruction Set                          | Arm(32),<br>Thumb(T32)             | Arm(32),<br>Thumb(T32)             | Arm(32),<br>Thumb(T32)                   | Arm(32),<br>Thumb(T32)                   | Arm(32),<br>Thumb(T32)              | Arm(32),<br>Thumb(T32)              | A64                                  |
| Pipeline Depth                           | 8 stage<br>in-order,<br>dual issue | 8 stage<br>in-order,<br>dual issue | 11 stage<br>out-of-order,<br>superscalar | 11 stage<br>out-of-order,<br>superscalar | 8 stage<br>in-order,<br>superscalar | 8 stage<br>in-order,<br>superscalar | 8 stage<br>in-order,<br>triple issue |
| Address Bits                             | 32                                 | 32                                 | 32                                       | 32                                       | 32                                  | 32                                  | 40                                   |
| Addressable Memory                       | 4GB                                | 4GB                                | 4GB                                      | 4GB                                      | 4GB                                 | 4GB                                 | 1TB                                  |
| ECC on Memories                          | Yes                                | Yes                                | Yes                                      | Yes                                      | Yes                                 | Yes                                 | Yes                                  |
| MPU or MMU                               | MPU                                | MPU                                | MPU                                      | MPU                                      | MPU                                 | MPU                                 | Both                                 |
| Maximum MPU Regions                      | 12                                 | 16                                 | 16                                       | 24                                       | 24+24                               | 24+24                               | 32+32                                |
| Symmetric Multi-Processing (SMP) Support | 1 core,<br>No coherency            | 2 core,<br>IO coherency            | Up to MP2                                | Up to MP4                                | Up to UP4,<br>No coherence          | Up to UP4,<br>No coherence          | Up to MP8                            |
| Floating Point Unit (FPU)                | Optional                           | Optional                           | Optional                                 | Optional                                 | Optional                            | Optional                            | Optional                             |
| SIMD (Neon)                              | No                                 | No                                 | No                                       | No                                       | Optional                            | Optional                            | Optional                             |
| DMIPS/MHz <sup>2</sup>                   | 1.67                               | 1.67                               | 2.5                                      | 2.5                                      | 2.09                                | 2.09                                | 3.71                                 |
| CoreMark@/MHz <sup>2</sup>               | 3.47                               | 3.47                               | 4.35                                     | 4.62                                     | 4.3                                 | 4.3                                 | 6.28                                 |
| Maximum # External Interrupts            | Up to 480                          | Up to 480                          | Up to 480                                | Up to 480                                | Up to 960                           | Up to 960                           | External,<br>GICStream<br>v3.1       |

| Feature                    | Cortex-R4  | Cortex-R5  | Cortex-R7† | Cortex-R8 | Cortex-R52 | Cortex-R52+ | Cortex-R82     |
|----------------------------|------------|------------|------------|-----------|------------|-------------|----------------|
| Bus Protocol               | AXI3       | AXI3       | AXI3       | AXI3      | AXI4       | AXI4        | AXI5 and CHI-E |
| Instruction TCM            | 0-8MB      | 0-8MB      | 0-128KB    | 0-1MB     | 0-1MB      | 0-1MB       | 0,16KB-1MB     |
| Data TCM                   | 0-8MB      | 0-8MB      | 0-128KB    | 0-1MB     | 0-1MB      | 0-1MB       | 0,16KB-1MB     |
| Instruction Cache          | 0,4KB-64KB | 0,4KB-64KB | 0,4KB-64KB | 0KB-64KB  | 0KB-32KB   | 0KB-32KB    | 16KB-128KB     |
| Data Cache                 | 4KB-64KB   | 4KB-64KB   | 4KB-64KB   | 0KB-64KB  | 0KB-32KB   | 0KB-32KB    | 16KB-64KB      |
| L2 Cache                   | N/A        | N/A        | N/A        | N/A       | N/A        | N/A         | 0,128KB-4MB    |
| Dual Core Lock-Step (DCLS) | No         | Yes        | No         | No        | Yes        | Yes         | No             |
| Safety Package             | No         | Yes        | No         | No        | Yes        | Yes         | No             |
| Software Test Library      | No         | Yes        | No         | No        | Yes        | Yes         | No             |

† Arm products undergo continual development and improvement. The Cortex-R7 processor is no longer available to license and is included here for comparison purposes only.

Cortex-R series processors support compatibility, enabling software reuse and migration as functionality and/or additional processing power is required.

\*See individual Cortex-R product pages for further information.

For more information, contact your Arm account manager today or explore the processors in more detail here:  
[developer.arm.com/ip-products/processors/cortex-r](http://developer.arm.com/ip-products/processors/cortex-r)