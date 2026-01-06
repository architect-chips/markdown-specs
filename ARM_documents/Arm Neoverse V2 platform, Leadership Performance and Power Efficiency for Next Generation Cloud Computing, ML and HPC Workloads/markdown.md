

![Arm logo](2dfa6ac3edfe874f68aa0cbccaa42322_img.jpg)

Arm logo

# Arm Neoverse V2 platform: Leadership Performance and Power Efficiency for Next-Generation Cloud Computing, ML and HPC Workloads

Hot Chips 2023

Magnus Bruce, Lead CPU Architect and Fellow, Arm

August 28<sup>th</sup>, 2023

## Arm Technology is Defining the Future of Computing

A semiconductor design and software platform company

## 250+ Billion

Arm-based chips shipped since inception

## 30.6 Billion

Arm-based chips reported shipped in FYE 2023

## 650+

Active licensees, growing by 50+ every year.

The global leader in the development of licensable compute technology

R&D excellence for semiconductor companies and large OEMs.

Arm's energy-efficient processor designs and software platforms enable advanced computing

Our technologies securely power products from the sensor to the smartphone and the supercomputer.

Arm delivers the foundational building blocks for trust in the digital world

Arm provides enhanced system-level security technologies such as Arm TrustZone and Arm Confidential Compute Architecture (CCA).

## Arm Neoverse Roadmap and Product Positioning

### Neoverse V-series

**Maximum  
Performance and  
Optimal TCO**  
Cloud, HPC, AI/ML

V1  
Platform

V2  
Platform

V-Series Next  
Platform

### Neoverse N-series

**Efficient Performance**  
Cloud, Networking,  
DPU, 5G

N1 Platform

CSS N2

N2  
Platform

N-Series Next  
Platform

### Neoverse E-series

**Throughput Efficiency**  
Networking, 5G

E1  
Platform

E2  
Platform

E-Series Next  
Platform

## Arm Neoverse V2 Design Principles

### Performance Leadership in Cloud, HPC and AI/ML

- Run-ahead branch prediction pipeline
  - Decouples branch from fetch
  - Tolerates a relatively small L1 instruction cache
  - Large BTBs to avoid redirection later in pipeline
  - Predicts direct branches during fetch
- Store-to-load forwarding at L1 hit latency
- Advanced prefetchers with timeliness and accuracy monitoring
- Physical register files, read after issue
- Dynamic feedback mechanisms to adapt to system conditions
- High bandwidth, low-latency L1 and private L2 caches
- Push 'width' and 'depth' higher
  - Maintain short pipelines for quick branch mispredict recovery

Continue to deliver the highest single-thread performance in the lowest power and area footprint

### High-Level Microarchitecture

- Every aspect of the microarchitecture optimized for performance & TCO

![](7a3561af571faf036baa93f5f4b1bdb9_img.jpg)

Arm Neoverse V2

Core components and features:

- Branch Predictor
- Instruction Fetch
- Mop\$ Fetch
- Decode Queue
- Decode
- Rename / Dispatch
- Issue Queues
- Load-Store Pipelines
- HW Prefetch
- Integer Pipelines
- Advanced SIMD Pipelines
- L2
- AMBA CHI

Key specifications:

- 320+ OoO window
- 8-wide dispatch
- 8-wide retire
- 6-wide/8-wide front-end
- 2 LS + 1 LD / cycle
- 64kB DCache
- 6-ALU + 2-branch
- Advanced data prefetchers
- ECC/Parity for all Core and L2 RAMs
- Instruction prefetcher
- Advanced branch predictors
- High-bandwidth fetch, 64kB ICache
- Power-optimized decode
- Quad 128-bit, low-latency datapath
- 10-cycle load-to-use, 128B/cycle private L2 cache – 1 or 2MB
- AMBA CHI.E system interface
- 32B DAT channels

Ultra-High Performance Armv9 CPU

#### Branch Predict/Fetch/ICache

##### uArch features shared with Neoverse V1

- Decoupled predict/fetch pipelines
  - Predict runs ahead to avoid bubbles and cover cache misses
- 64kB, 4-way set-associative L1 instruction cache
- Two predicted branches per cycle
- Two-level Branch Target Buffer
- Predictor acts as ICache prefetcher
- 8 table TAGE direction predictor with staged output

##### uArch features **new with Neoverse V2**

| Branch Target Buffer | 10x larger nanoBTB<br>Split main BTB into two levels with 50% more entries |
|----------------------|----------------------------------------------------------------------------|
| TAGE                 | 2x larger tables with 2-way associativity<br>Longer history                |
| Indirect branches    | Dedicated predictor                                                        |
| Fetch bandwidth      | Doubled instruction TLB and cache BW                                       |
| Fetch Queue          | Doubled from 16 to 32 entries                                              |
| Fill Buffer          | Increased size from 12 to 16 entries                                       |
| uOp cache            | Reduced size for efficiency                                                |

![](0ad3f61f997eb05afb341fc46024bf2b_img.jpg)

Diagram illustrating the Fetch and Branch Predict components of the Neoverse V2 architecture.

**Fetch Path:** The Fetch Queue feeds into ITLB and uOp\$ Tag. ITLB outputs I\$ Tag and I\$ Data. uOp\$ Tag and I\$ Tag feed into uOp\$ Data. uOp\$ Data and I\$ Data feed into the Align unit. The Align unit outputs 8 uOps and 6 insts. The Fetch Queue also feeds into the Main BTB, Main GHB, and LO BTB.

**Branch Predict Path:** The Main BTB, Main GHB, and LO BTB feed into the Main BP. Main BP outputs to FB (Fetch Buffer). ITLB also feeds into FB.

+2.9% SPEC CPU® 2017 Integer<sup>1</sup>

#### Decode/Rename/Dispatch

##### uArch features shared with Neoverse V1

- Partially decoded instructions from I\$ feed parallel decoders
- Fully decoded uOps bypass decode with higher width
- Decode handles simple instruction fusion
- Rename manages physical register files with both architected and speculative state using mapping tables and free list

##### uArch features **new with Neoverse V2**

| Decode bandwidth   | Increased decoder lanes from 5 to 6<br>Increased Decode Queue from 16 to 24 entries |
|--------------------|-------------------------------------------------------------------------------------|
| Rename checkpoints | Increased from 5 to 6 total checkpoints<br>Increased from 3 to 5 vector checkpoints |
| Rename rebuild     | Improved rebuild flows for more efficient recovery after pipeline flush             |

![](4279c8be6ec4ed56f4b3349be98bb426_img.jpg)

Diagram illustrating the Decode/Rename/Dispatch pipeline structure.

Inputs:

- 8 uOps enter the **uOp Queue**.
- 6 insts enter the **Decode Queue**.

Processing flow:

- The **uOp Queue** outputs 8 uOps to the **Rename** stage.
- The **Decode Queue** feeds into the **Decode** stage.
- The **Decode** stage outputs 8 uOps to the **Rename** stage.
- The **Rename** stage outputs 8 uOps to the final output.

+2.8% SPEC CPU® 2017 Integer<sup>1</sup>

#### Issue/Execute

uArch features shared with Neoverse V1

- Multiple independent Issue Queues, some with dual pickers
- Late read of physical register file – no data in IQs
- Result caches with lazy writeback

uArch features **new with Neoverse V2**

| ALU bandwidth        | Added two more single-cycle ALUs                                                    |
|----------------------|-------------------------------------------------------------------------------------|
| Larger Issue Queues  | SX/MX: Increased from 20 to 22 entries<br>VX: Increased from 20 to 28 entries       |
| Predicate operations | Doubled predicate bandwidth                                                         |
| Zero latency MOV     | Subset of register-register and immediate move operations execute with zero latency |
| Instruction fusion   | More fusion cases, including CMP + CSEL/CSET                                        |

8 uOps

![](27b22513fc27a0ff5f230b062ad3112f_img.jpg)

Diagram illustrating the 8 uOps execution flow in the Neoverse V2 architecture. The flow shows instructions moving from Issue Queues (IQ) through the RF (Physical Register File) and Result Cache (Res\$ Rd) to the Forward (Fwd) unit, and finally to the execution units (ALU, BR, or VX ALUs).

The 8 uOps are:

1. SX0/BX0 IQ → RF Res\$ Rd → Fwd → ALU
2. SX1/BX1 IQ → RF Res\$ Rd → Fwd → ALU
3. SX2/MX0 IQ → RF Res\$ Rd → Fwd → ALU (SHIFT + ALU)  
   MUL/IMAC/DIV/CRC/SPR
4. SX3/MX1 IQ → RF Res\$ Rd → Fwd → ALU (SHIFT + ALU)  
   MUL/IMAC
5. SX4 IQ → RF Res\$ Rd → Fwd → ALU
6. SX5 IQ → RF Res\$ Rd → Fwd → ALU
7. VX0/1 IQ → IQ Read → RF Res\$ Rd → Fwd → VX ALUs
8. VX2/3 IQ → IQ Read → RF Res\$ Rd → Fwd → VX ALUs

+3.3% SPEC CPU® 2017 Integer<sup>1</sup>

#### LoadStore/DCache

##### uArch features shared with Neoverse V1

- Two load/store pipes + one load pipe accesses
- 4 x 8B result busses (integer)
- 3 x 16B result busses (FP, SVE, Neon)
- ST to LD forwarding at L1 hit latency
- RST and MB to reduce tag and data
- Fully-associative L1 DTLB with multiple page sizes
- 64kB 4-way set associative Dcache
- Read-After-Read and Read-After-Write hazard detection

##### uArch features new with Neoverse V2

| TLB                | Increased from 40 to 48 entries                 |
|--------------------|-------------------------------------------------|
| Replacement policy | Changed from PLRU to dynamic RRIP               |
| Larger Queues      | Store Buffer<br>ReadAfterRead<br>ReadAfterWrite |
| Efficiency         | VA hash based store to load forwarding          |
| Reduced flushes    | RAR hazards tracked through L2 cache lifetime   |

![](925f55ce69802b9d3b00546382663ee2_img.jpg)

Diagram illustrating the Load Store unit architecture, showing the flow from LS0 IQ, LS1 IQ, and LD IQ through DTLB, D\$ Tag, D\$ Data, and FB, leading to RST, MB, and RAR/RAW components. The diagram is labeled "Load Store".

+3.0% SPEC CPU® 2017 Integer<sup>1</sup>

#### Hardware Prefetching

##### uArch features shared with Neoverse V1

- Multiple prefetching engines training on L1 and L2 accesses
  - Spatial Memory Streaming
  - Best Offset
  - Stride
  - Correlated Miss Cache
  - Page
- Prefetch into L1 and L2
- Virtual address to allow page crossing and TLB prefetching
- Adaptive distance based on accuracy and timeliness

##### uArch features new with Neoverse V2

| Training           | Refined filtering of transactions used for training                                                                        |
|--------------------|----------------------------------------------------------------------------------------------------------------------------|
| Accuracy           | Apply Program Counter to L2 GSMS training                                                                                  |
| New PF engines     | Global SMS – larger offsets than SMS<br>Sampling Indirect Prefetch – pointer dereference<br>TableWalk – Page Table Entries |
| Differentiated QoS | Lower QoS value for prefetches than demand for reduced loaded latency                                                      |

![](8ee3b76dd49f31624d287885bc2c81ee_img.jpg)

Hardware Prefetching

Diagram illustrating the hardware prefetching architecture, showing L1\$ and L2\$ components feeding into various prefetch engines (Stride, Page, SMS, SIP, CMC, BO, GSMS, TBW) which output to L1PRQ and L2PRQ.

+5.3% SPEC CPU® 2017 Integer<sup>1</sup>

#### Level 2 Cache

##### uArch features shared with Neoverse V1

- Private unified Level 2 cache, 8-way SA, 4 independent banks
- 64B read or write per 2 cycles per bank = 128B/cycle total
- 96-entry Transaction Queue
- Inclusive with L1 caches for efficient data and instruction coherency
- Inline SECDED ECC in Tag, Data, and TQ RAMs
- AMBA CHI interface with 256b DAT channels

##### uArch features **new with Neoverse V2**

| Capacity                    | 2MB/8-way with latency of 1MB (10-cycle Id-to-use)                                                                                     |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Replacement policy          | 6-state RRIIP (up from 4)                                                                                                              |
| Dead-block prediction       | Separate tracking of used-once and used-multiple data                                                                                  |
| Replacement                 | L2 copybacks transfer replacement hints to SLC                                                                                         |
| CHI revision E interconnect | Improved store-hit-shared flow (MakeReadUnique)<br>Combined Write/Cache Maintenance transactions<br>Write*Zero transactions for memset |

![](eb903413d070b64f45cd763804ba443f_img.jpg)

Diagram illustrating the Level 2 Cache architecture.

The Level 2 Cache consists of multiple banks (L2 Bank). Each bank contains an Arbiter (Arb), a Tag RAM, and a Data RAM. A Transaction Queue (TQ) is connected to the Data RAM and the AMBA CHI interface.

Requests enter the cache structure, and Responses (64B) exit. A Prefetch unit is shown connected to the Data RAM.

The AMBA CHI interface connects to the TQ and exchanges 32B data with the external system.

+0.5% SPEC CPU® 2017 Integer<sup>1</sup>  
8.2% reduction in SLC misses

### Neooverse V2 Performance Uplift over Neooverse V1

![](398674b42e3466add6d47f420c136494_img.jpg)

Arm Neooverse V2

Core components and their unit uplift over Neooverse V1:

| Component               | Unit uplift over Neooverse V1 |
|-------------------------|-------------------------------|
| Branch Predictor        | 2.9%                          |
| Instruction Fetch       | 2.0%                          |
| Mop\$ Fetch             | 0.8%                          |
| Decode Queue            | 0.9%                          |
| Decode                  | 0.7%                          |
| Rename / Dispatch       | 0.7%                          |
| Issue Queues            | 3.3%                          |
| Load-Store Pipelines    | 3.0%                          |
| Integer Pipelines       | 5.3%                          |
| Advanced SIMD Pipelines | 0.5%                          |
| HW Prefetch             | 5.3%                          |
| L2                      | 0.5%                          |
| AMBA CHI                | 0.5%                          |

Unit uplift over Neooverse V1

13% increase in SPEC CPU® 2017 Integer performance<sup>1</sup>,  
while seeing a 10.5% reduction in SLC misses

## Arm Neoverse V2 Performance, Power, Area (PPA)

![Microscopic view of the Neoverse V1 chip layout, showing various colored blocks representing different components.](2236272d3b3db6e6363337f5a8db72f6_img.jpg)

Microscopic view of the Neoverse V1 chip layout, showing various colored blocks representing different components.

Neoverse V1 with 1 MB L2

Typical 7nm implementation

2.52 mm<sup>2</sup> with 1 MB L2

1.2 W\*

\*SIR at 2.8 GHz, 0.75 V, H280, 16LM

![Microscopic view of the Neoverse V2 chip layout, showing various colored blocks representing different components.](c222a9006d6d60a8d81e6ffbfc0e74ad_img.jpg)

Microscopic view of the Neoverse V2 chip layout, showing various colored blocks representing different components.

Neoverse V2 with 2 MB L2

Typical 5nm implementation

2.50 mm<sup>2</sup> with 2 MB L2

1.4 W\*

\*SIR at 2.8 GHz, 0.75 V, H280, 17LM

### Arm Neoverse V2 Platform IP

![](0b8b087a7baa471015d3ffeaa43d9a6c_img.jpg)

Diagram illustrating the Arm Neoverse V2 Platform IP architecture.

The core components are:

- **Processor Block**: Contains two V2 CPUs, each with L1\$ and L2\$ caches, connected to a Direct Connect DSU.
- **I/O Macro**: Contains NI-700 and MMU-700, connected to PCIe G5 and CXL.
- **System Control & Management**: Includes System Control Processor (SCP), Manageability Control Processor (MCP), Debug, NIC-450, and GIC-700.
- **CMN-700 Interconnect**: Provides Chip-to-Chip Expansion. Features include:
  - Up to 256-cores per die
  - Up to 512MB of system level cache (SLC)
  - Up to 4TB/s cross-sectional bandwidth
- **Memory Expansion**: Includes System Level Cache (SLC) and four DDR5 memory modules.
- **General I/O**: Includes NIC-450 and Peripheral Block.

Key connections shown:

- Processor Block connects to I/O Macro and CMN-700 Interconnect.
- I/O Macro connects to PCIe G5, CXL, System Control & Management, and CMN-700 Interconnect.
- System Control & Management connects to CMN-700 Interconnect and General I/O.
- CMN-700 Interconnect connects to Memory Expansion and General I/O.

### Next: Performance Analysis of Neoverse V2 compared to Neoverse V1

- Neoverse V1 and Neoverse V2 performance comparisons are derived from equivalent systems in an emulation environment
- 32 CPU cores @ 3 GHz
- Neoverse V1 with 1MB L2, Neoverse V2 with 2MB L2
- CMN-700 interconnect @ 2GHz with 32MB System Level Cache
- Four DDR-5600 memory controllers, 40-bit memory interfaces – 89.6 GB/s max BW
- SPEC CPU®2017 scores are estimated using reduced benchmarks
- GCC 10 with standard compile options – no special optimizations

### General Performance: SPEC CPU® 2017 Integer

![](b05fbb6a015ea153c1e25245772b1a1b_img.jpg)

Bar chart titled "SPEC CPU® 2017 Integer" comparing performance (Y-axis, 0 to 16) between Neoverse V1 (dark gray) and Neoverse V2 (orange) across various benchmarks (X-axis).

Legend: Neoverse V1 (dark gray), Neoverse V2 (orange).

On SPEC CPU® 2017 Integer, Neoverse V2 shows a 13% improvement over Neoverse V1<sup>1</sup>

![](cbc4516eb885829fe8c9dabc0946dcbe_img.jpg)

Bar chart titled "SPECrate® 2017 Integer" comparing performance (Y-axis, 0 to 250) between Neoverse V1 (dark gray) and Neoverse V2 (orange) across various benchmarks (X-axis).

Legend: Neoverse V1 (dark gray), Neoverse V2 (orange).

On SPECrate® 2017 Integer, Neoverse V2 shows a 17.3% improvement over Neoverse V1<sup>1</sup>

1. Performance is estimated for SPEC CPU® 2017

#### Caching Tier Performance: MemCacheD

![](af06598cfb31b517e79b50d74f72a0ca_img.jpg)

Three bar charts comparing Neoverse V1 (gray) and Neoverse V2 (orange) performance (M Queries/s) across 1 to 16 Threads, under different update percentages: 0% Update, 5% Update, and 25% Update.

Legend: Neoverse V1 (Gray), Neoverse V2 (Orange).

On Memcached, Neoverse V2 shows a 13-15% improvement over Neoverse V1

Performance scaling becomes system limited as the update percentage increases

#### Web and Proxy Server Performance: NGINX

![](8ccbc9fa77bf60ba0ca0b79dec8681b8_img.jpg)

Four bar charts comparing Neoverse V1 (dark gray) and Neoverse V2 (orange) performance across different thread counts (1, 2, 4, 8, 16) for Web Server, Web Server Secure, Reverse Proxy, and Reverse Proxy Secure workloads. The Y-axis represents K Requests/s.

Legend: Neoverse V1 (dark gray), Neoverse V2 (orange).

Performance improvement percentages (1. Average performance improvement across thread count):

- Web Server: 20% increase<sup>1</sup>
- Web Server Secure: 25% increase<sup>1</sup>
- Reverse Proxy: 23% increase<sup>1</sup>
- Reverse Proxy Secure: 32% increase<sup>1</sup>

On NGINX, Neoverse V2 shows a 20-32% performance improvement over Neoverse V1

Performance scaling improves with higher thread count

1. Average performance improvement across thread count

#### Database Performance: Percona MySQL Server

![](3ae74a33759ae31781f484406db4feed_img.jpg)

Bar chart showing Transactions/s versus Threads (1, 2, 4, 8, 16) comparing Neoverse V1 (dark gray) and Neoverse V2 (orange).

Annotations:

- 80% reduction in branch mis-predicts
- 70% reduction in unused prefetches

Legend:

- Neoverse V1
- Neoverse V2

On Percona MySQL, Neoverse V2 shows a 35-104% performance improvement over Neoverse V1

Significant gains from improvements in branch prediction, fetch, and hardware prefetching

### ML Performance: XGBoost

![](de2d3e89ee4dd60958b64426cd3a81ca_img.jpg)

Bar chart comparing ML performance (XGBoost) between Neoverse V1 (dark gray) and Neoverse V2 (orange) across five datasets: higgs\_noqt, higgs\_qt, yahoo\_notq, yahoo\_qt, and Average.

Y-axis represents performance percentage (0% to 250%).

Legend: Neoverse V1 (dark gray), Neoverse V2 (orange).

| Dataset    | Neoverse V1 (%) | Neoverse V2 (%) |
|------------|-----------------|-----------------|
| higgs_noqt | ~100            | ~210            |
| higgs_qt   | ~100            | ~160            |
| yahoo_notq | ~100            | ~190            |
| yahoo_qt   | ~100            | ~170            |
| Average    | ~100            | ~180            |

On XGBoost, Neoverse V2 shows a 67-114% performance improvement over Neoverse V1

Branch prediction and fetch improvements enable large performance gains

#### NVIDIA Grace CPU Delivers 2X Throughput at the Same Power

Powered by Neoverse V2 Core and High-Speed NVIDIA-Designed Scalable Coherency Fabric with LPDDR5X Memory

![](2a77eb32ef4c4d8a5c1758a53a908336_img.jpg)

**Server Performance**

Bar chart comparing performance (Y-axis, 0.0X to 1.5X) across six workloads (X-axis): Weather WRF, MD CP2K, Climate NEMO, CFD OpenFOAM, Graph Analytics GapBS BFS.

Legend: Intel SPR (Dark Gray), AMD Genoa (Light Gray), NVIDIA Grace (Green).

| Workload                  | Intel SPR | AMD Genoa | NVIDIA Grace |
|---------------------------|-----------|-----------|--------------|
| Weather WRF               | 0.6X      | 1.0X      | 1.0X         |
| MD CP2K                   | 0.6X      | 1.0X      | 1.0X         |
| Climate NEMO              | 0.6X      | 1.0X      | 1.0X         |
| CFD OpenFOAM              | 0.7X      | 1.0X      | 1.1X         |
| Graph Analytics GapBS BFS | 1.0X      | 1.0X      | 1.4X         |

![](ebce355620876e10f907f8b71926c112_img.jpg)

**5 MW Data Center Throughput**

Bar chart comparing throughput (Y-axis, 0.0X to 3.0X) across six workloads (X-axis): Weather WRF, MD CP2K, Climate NEMO, CFD OpenFOAM, Graph Analytics GapBS BFS.

Legend: Intel SPR (Dark Gray), AMD Genoa (Light Gray), NVIDIA Grace (Green).

| Workload                  | Intel SPR | AMD Genoa | NVIDIA Grace |
|---------------------------|-----------|-----------|--------------|
| Weather WRF               | 0.6X      | 1.0X      | 1.7X         |
| MD CP2K                   | 0.6X      | 1.0X      | 1.8X         |
| Climate NEMO              | 0.7X      | 1.0X      | 1.9X         |
| CFD OpenFOAM              | 0.7X      | 1.0X      | 1.9X         |
| Graph Analytics GapBS BFS | 1.1X      | 1.0X      | 2.5X         |

Data provided by NVIDIA

## Arm Neoverse V2 Platform Summary

### Designed for cloud performance leadership

- Double-digit gains over Neoverse V1 on cloud infrastructure workloads
  - 13% uplift on SPEC CPU® 2017 Integer<sup>1</sup>
  - 15% to 100% uplift across a range of server workloads (caching, web, database)

### Designed for HPC and AI/ML performance leadership

- Up to 2x the performance of Neoverse V1 on HPC and ML workloads
  - Up to 114% uplift on XGBoost (83% average)
  - Meets or exceeds leading x86-CPU's on performance with up to 2x the performance efficiency

- Available today in NVIDIA Grace CPU Superchip
- Additional partner silicon expected

![Image of the NVIDIA Grace CPU Superchip, showing two large dies mounted on a substrate.](6f78ea3343d75a12a76a4c51af28da87_img.jpg)

Image of the NVIDIA Grace CPU Superchip, showing two large dies mounted on a substrate.

![NVIDIA logo.](5756508641ee599941f6d1e85de7e84b_img.jpg)

NVIDIA logo.

### Performance and benchmark disclaimer

- This benchmark presentation made by Arm Ltd and its subsidiaries (Arm) contains forward-looking statements and information. The information contained herein is therefore provided by Arm on an "as-is" basis without warranty or liability of any kind. While Arm has made every attempt to ensure that the information contained in the benchmark presentation is accurate and reliable at the time of its publication, it cannot accept responsibility for any errors, omissions or inaccuracies or for the results obtained from the use of such information and should be used for guidance purposes only and is not intended to replace discussions with a duly appointed representative of Arm. Any results or comparisons shown are for general information purposes only and any particular data or analysis should not be interpreted as demonstrating a cause and effect relationship. Comparable performance on any performance indicator does not guarantee comparable performance on any other performance indicator.
- Any forward-looking statements involve known and unknown risks, uncertainties and other factors which may cause Arm's stated results and performance to be materially different from any future results or performance expressed or implied by the forward-looking statements.
- Arm does not undertake any obligation to revise or update any forward-looking statements to reflect any event or circumstance that may arise after the date of this benchmark presentation and Arm reserves the right to revise our product offerings at any time for any reason without notice.
- Any third-party statements included in the presentation are not made by Arm, but instead by such third parties themselves and Arm does not have any responsibility in connection therewith.

## End Notes

Slide Title: Branch Predict/Fetch/ICache

Slide Title: Decode/Rename/Dispatch

Slide Title: Issue/Execute

Slide Title: LoadStore/DCache

Slide Title: Hardware Prefetching

Slide Title: Level 2 Cache

Slide Title: Neoverse V2 Performance Uplift over Neoverse V1

Slide Title: General Performance: SPEC CPU® 2017 Integer

Slide Title: Arm Neoverse V2 Platform Summary

- SPEC CPU®2017 scores are estimated using reduced benchmarks
  - Neoverse V1 and Neoverse V2 performance comparisons are derived from equivalent systems in an emulation environment, 32 CPU cores @ 3 GHz, Neoverse V1 with 1MB L2, Neoverse V2 with 2MB L2, CMN-700 interconnect @ 2GHz with 32MB system level cache, four DDR-5600 memory controllers, 40-bit memory interfaces – 89.6 GB/s max BW
  - GCC 10 with standard compile options – no special optimizations

arm

Thank You

Danke

Gracias

Grazie

謝謝

ありがとう

Asante

Merci

감사합니다

धन्यवाद

Kiitos

شكرًا

ধন্যবাদ

תודה