

# ARM Neoverse N1

Aishik Ghosh, Anant Kandikuppa, Zane Fink

CS 433 Mini Project

## Outline

1. Introduction
2. Core Microarchitecture
3. Memory Hierarchy
4. Parallelism Support
5. Special Features for Infrastructure and Security

## Introduction

- ARM CPUs are RISC processors designed by Arm Holdings
- ARM Neoverse N1 is an infrastructure-focused chip that implements the Arm v8.2-A instruction set
- Hardware features make the Neoverse N1 especially suited to cloud and infrastructure applications

## Introduction: Infrastructure

- Workloads commonly found in cloud environments such as AWS, Microsoft Azure, etc.
- Codes characterized by:
  - Complex branching behavior
  - JIT compiled
  - Object management
  - Garbage collection
- Concretely: web servers, datacenter applications

## **Core Microarchitecture**

- Superscalar processor
- 11-stage out of order accordion pipeline
  - Can drop to 9-stages

![](7a3561af571faf036baa93f5f4b1bdb9_img.jpg)

**WikiChip - Neoverse N1 Microarchitecture**

![](8e065eabc40a3645a569db7e9cd0da32_img.jpg)

## **Core Microarchitecture**

- Core has
  - 4 way decode
  - 3 ALUs
  - 1 branch exec unit
  - 2 adv SIMD units
  - 2 load/store exec unit

![](55d2bfe1c3d04e86df8d7a104d802172_img.jpg)

**WikiChip - Neoverse N1 Microarchitecture**

![](bdc6095967437c168a3f2a4ff8ca38bd_img.jpg)

### SIMD

- Single instruction multiple data
- Adv SIMD performance
  - native quad-word, dual 128-bit units fed by separate issue queues
  - Latencies
    - Floating point add - 2 cycles
    - Floating point multiply - 3 cycles
    - Floating point multiply add - 4 cycles

![](c0843c6d138705289960d9f53a6e72a1_img.jpg)

Diagram illustrating SIMD (Single Instruction, Multiple Data) processing. Vector A and Vector B are input data streams, each consisting of four elements. These elements are processed simultaneously by four parallel units, each labeled Op1. The results are combined into Vector C, also consisting of four elements.

SIMD

### Core Backend

![](3121afa7ca030b22ee0345864ca6f38b_img.jpg)

Diagram illustrating the Core Backend of the WikiChip - Neoverse N1 Microarchitecture.

The pipeline stages are:

1. **4-Way Decode** (Decoder, Decoder, Decoder, Decoder)
2. **Rename / Allocate / Commit** (ReOrder Buffer (128-entry))
3. **Dispatch** (General-Purpose Register File, System Registers, Advanced SIMD & FP Register File)
4. **Issue (120-entry)** (Queue (16-entry), Port, Queue (16-entry), Port, Queue (16-entry), Port, Queue (16-entry), Port, Queue (16-entry), Port, Queue (16-entry), Port, Queue (16-entry), Port, Queue (12-entry), Port, Queue (12-entry), Port)
5. **Execution Engine** (Integer, EUs, ASIMD, LSU)

The Execution Engine components include:

- **Integer** (Branch, ALU, ALU, ALU, MAC, DIV)
- **EUs** (ALU, FADD, FMUL, FDIV, IMAC)
- **ASIMD** (ALU, FADD, FMUL, FDIV, IMAC)
- **LSU** (Load Buffer (68-entry), Store Buffer (72-entry))

Execution Engine Data Widths: 32B, 32B, 32B, 32B.

[WikiChip - Neoverse N1 Microarchitecture](#)

![Red stylized I logo](efca2dce0095c9dc2a68e9af6b2bfd40_img.jpg)

Red stylized I logo

### Branch Prediction

- 6k-entry main branch target buffer
- 3-cycle access latency to retrieve branch target addresses (without I-cache)
- Once a prediction is made, the predicted address is stored into a 12-entry fetch queue which tracks future fetch transactions.
- Decoupled Branch Prediction

## Memory Hierarchy Introduction

- Deep Cache Hierarchy L1, L2, optional shared L3, and an optional system-level cache.
- Strict inclusivity between L1 data cache and L2 cache, non-inclusivity between L1 instruction cache and L2 cache

[Arm Neoverse N1 Cloud-to-Edge Infrastructure SoCs](#)

![](f519a5be118c846f631c992412353fb9_img.jpg)

Diagram illustrating the memory hierarchy of the Arm Neoverse N1 CPU.

The CPU structure includes:

- I-Cache: 64KB, 4-way
- D-Cache: 64KB, 4-way
- Private L2: 512KB/1MB, 8-way

The I-Cache and D-Cache communicate with the Private L2 cache at a rate of 64B/cycle. The Private L2 cache connects to the CAL (Cluster Aggregation Layer) via the CHI (Cluster Hub Interface).

The CAL connects to two System Cache Slices, which are connected to each other and the CAL.

Legend: CAL = Cluster Aggregation Layer

### Memory Hierarchy Overview

- **Instruction Cache (Private):**
  - 64 KB
  - 4-way set-associative
  - 16B of instructions per cycle
  - 4-cycle LD-use latency.
- **L1 Data Cache (Private):**
  - 64 KB
  - 4-way set-associative
  - 32B per cycle
  - 4-cycle LD-use latency

### Memory Hierarchy Overview

- L2 Data Cache (Private):
  - Configurable, 256KB-1MB in size
  - 8-way set associative
  - 64B per cycle between L1/L2 caches
  - 9-11-cycle LD-use latency

### Memory Hierarchy Overview

- **(Optional) L3 Cluster Data Cache:**
  - Multiple cores can be configured in a cluster
  - Up to 2MB, 28-33 cycle LD-use latency
  - Modified Exclusive Shared Invalid (MESI) coherence protocol
  - Coherency managed through snoop filter
- **(Optional) System level Cache:**
  - Up to 128MB
  - Coherency managed through snoop filter
  - 22ns LD-use Latency

### Memory Hierarchy Overview

- Instruction TLB
  - 48-entry, fully associative
  - Support for 4KB, 16KB, 64KB, 2MB, and 32MB page sizes
- Data TLB
  - 48-entry, fully associative
  - Support for 4 KB, 16KB, 64KB, 2MB, and 512MB page sizes
- Unified (instruction/data) L2 TLB
  - 1280-entry 5-way set associative

### Memory Hierarchy Key Features

- Cache miss predictor: Bypasses cache hierarchy to avoid cache access times.
- Cache prefetcher that can detect complicated access patterns.
- Fetch-aware cache replacement policies
- Supports maximum physical memory of 256 TB
- 68 in-flight loads, 72 in-flight stores

### Parallelism Support

- 4-128 single threaded cores per chip
- Private L1 & L2 caches
- Optional shared L3 cache
- Multiple clusters supported by CoreLink CMN-600 mesh interconnect
- Allows specialized cores and accelerators to work together

![Red stylized I logo](83926108dd52e3998fda7a99a91cdf3b_img.jpg)

Red stylized I logo

### Corelink CMN-600 Mesh Interconnect

- Provides high-frequency, non-blocking access to shared memory resources
- Supports upto 32 coherent clusters of CPUs / Accelerators
- Provides upto 128MB of shared system cache (SC)
- Optimized for low memory latency; ~1TB/s bandwidth

![](f4d72193f77f6646a2a1f4baaa927154_img.jpg)

Diagram illustrating the CoreLink CMN-600 Mesh Interconnect architecture.

The CoreLink CMN-600 connects four main components: ARMv8-A CPUs, Accelerators, IO Subsystems, and Memory Controllers. The CMN-600 is connected to two System Caches (SC) below it. The ARMv8-A CPUs, Accelerators, and IO Subsystems are connected to the CMN-600 via bidirectional links. The Memory Controllers are connected to the System Caches via bidirectional links. The System Caches are connected to each other and to the Memory Controllers via bidirectional links, forming a mesh structure.

[CMN-600 Overview](#)

#### Corelink CMN-600 Mesh Interconnect - SC

- Integrated Snoop Filters
  - Reduces number of snoop requests
  - Lowers power consumption
- Cache Stashing
  - Allows external agents to directly place data into L3/L2 core caches
- Direct Memory Transfer
  - Allows memory controllers to directly send data to the requestor

## Infrastructure Specific Features

- Enhanced Virtualization Support
  - VMID extended to 16 bits
  - Hardware update of access/dirty bits in page tables
- Improved Side Channel Protection
- Supports Armv8-A architecture extensions
  - CRC32 instruction to accelerate checksum computation
  - FP16 and int8 dot product support for ML inference
- Commercial deployment - AWS Graviton 2 processor

# Thank You!

Questions?

## References

[1] R. Christy, S. Riches, S. Kottekkat, P. Gopinath, K. Sawant, A. Kona, and R. Harrison. 2020. 8.3 A 3GHz ARM Neoverse N1 CPU in 7nm FinFET for Infrastructure Applications. In *2020 IEEE International Solid- State Circuits Conference - (ISSCC)*, 148–150.  
DOI:https://doi.org/10.1109/ISSCC19947.2020.9062889

[2] A. Pellegrini and C. Abernathy. 2019. Arm Neoverse N1 Cloud-to-Edge Infrastructure SoCs. In *2019 IEEE Hot Chips 31 Symposium (HCS)*, 1–21.  
DOI:https://doi.org/10.1109/HOTCHIPS.2019.8875640

[3] A. Pellegrini, N. Stephens, M. Bruce, Y. Ishii, J. Pusdesris, A. Raja, C. Abernathy, J. Koppanalil, T. Ringe, A. Tummala, J. Jalal, M. Werkheiser, and A. Kona. 2020. The Arm Neoverse N1 Platform: Building Blocks for the Next-Gen Cloud-to-Edge Infrastructure SoC. *IEEE Micro* 40, 2 (March 2020), 53–62.  
DOI:https://doi.org/10.1109/MM.2020.2972222

[4] Neoverse N1 - Microarchitectures - ARM - WikiChip. Retrieved December 2, 2020 from  
[https://en.wikichip.org/wiki/arm\\_holdings/microarchitectures/neoverse\\_n1](https://en.wikichip.org/wiki/arm_holdings/microarchitectures/neoverse_n1)

[5] Single Data Multiple Instruction. Retrieved December 6, 2020 from  
<https://www.sciencedirect.com/topics/computer-science/single-instruction-multiple-data>

[6] Corelink CMN-600 - ARM - Retrieved December 6, 2020 from  
<https://developer.arm.com/ip-products/system-ip/corelink-interconnect/corelink-coherent-mesh-network-family/corelink-cmn-600>

## Appendix

### Concrete Example Application

- Nginx: an open-source high-performance webserver, proxy, and load balancer
- Goal: Reduce latency of a single request, maximize number of concurrent requests that can be serviced
- Quickly servicing a request requires:
  - Low memory latency and high bandwidth to process the request and transfer the response
  - Fast context switches between user and kernel space
  - Fast instruction fetching on the CPU front end

![](9b5411fa2d169b66f6185fbf67b49766_img.jpg)

Diagram illustrating the request flow and context switching:

request → NIC → IRQ → TCP/IP → Nginx → OS files → Nginx → TCP/IP → NIC → response

Context switching diagram:

Network interface → User → Kernel

### Memory Hierarchy Performance

![](df0685d2d1176d617ed1e642de4e5425_img.jpg)

| Workload stressor     | Neooverse N1 Features                               | N1 improvement over Cortex-A72               |
|-----------------------|-----------------------------------------------------|----------------------------------------------|
| Object management     | Memory allocations                                  | <b>2.4x faster</b>                           |
|                       | Object/array initializations                        | <b>5x faster</b>                             |
|                       | Copy chars                                          | <b>1.6x faster</b>                           |
|                       | Smart HW handling of SW barriers (DMBs)             | <b>Memory barriers elided if unnecessary</b> |
| Instruction footprint | i-cache miss rate and branch mispredicts            | <b>Reduced by 1.4x</b>                       |
|                       | L2 accesses                                         | <b>Reduced by 2.25x</b>                      |
|                       | Fully HW coherent lcache                            | <b>Accelerates VM bring up by up to 20x</b>  |
| Garbage collection    | Locking throughput w/ V8.2 Arch Atomic Instructions | <b>Improved by 2x</b>                        |

Java Based Benchmark (throughput)

Speedup vs 1 Cortex-A72

1 2 4

Cortex-A72 Neooverse N1

### Cache Stashing

### Offload acceleration

![](5500ab73cf84ccc0055eecf28889b4db_img.jpg)

Diagram illustrating Offload acceleration:

1. Configure registers for task
2. Fetches data from Core memory
3. Carries out acceleration
4. Writes result into Core memory

The system components are the DynamIQ cluster (PP, ACP) and the Accelerator.

Example application:  
Offload crypto acceleration

### I/O processing

![](d8d893dd559845f86c5dd46147ef98b6_img.jpg)

Diagram illustrating I/O processing:

1. Writes data into Core memory
2. Carries out computation
3. Processing completed
4. Reads result from Core memory or sends data for onward processing

The system components are the DynamIQ cluster (PP, ACP) and the I/O agent.

Example application:  
Packet processing in network systems

### Direct Memory Transfer

![](a848a8de7c2614546db51319bd55328f_img.jpg)

Diagram illustrating the Snoopable Read Direct Memory Transfer (DMT) structure.

The diagram shows three entities: RN-F (Requester), ICN (Intermediate Controller), and SN (SNOOPER).

The flow is as follows:

1. RN-F sends REQ to ICN.
2. ICN sends Snoopable Read to RN-F.
3. ICN sends ReadNoSnp to SN.
4. SN sends REQ to ICN.
5. SN sends RDAT (Data) to ICN.
6. ICN sends CompData (Compressed Data) to RN-F.
7. RN-F sends SRSP (Snoop Response) to ICN.
8. ICN sends CompAck (Compressed Acknowledgement) to RN-F.

Figure 2-1 Snoopable Read DMT structure