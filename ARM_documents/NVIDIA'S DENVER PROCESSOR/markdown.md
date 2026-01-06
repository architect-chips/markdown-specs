

![NVIDIA logo](2dfa6ac3edfe874f68aa0cbccaa42322_img.jpg)

NVIDIA logo

# HOT CHIPS 2014NVIDIA'S DENVER PROCESSOR

Darrell Boggs, CPU Architecture

Co-authors: Gary Brown, Bill Rozas,  
Nathan Tuck, K S Venkatraman

![A large, green circuit board (chip) resting on a keyboard, overlaid with abstract graphics of neurons and a wireframe car.](5fb340ad68b0c71df0b56698b137e35b_img.jpg)

A large, green circuit board (chip) resting on a keyboard, overlaid with abstract graphics of neurons and a wireframe car.

## TEGRA K1

with Dual Denver CPUs

The First 64-bit  
Android Kepler-Class  
Chip

![NVIDIA logo](317e0525ef1b2458976c246876f4a948_img.jpg)

NVIDIA logo

### One Chip – Two Versions

TEGRA K1  
192-core  
Kepler-Class Chip

![Image of the Tegra K1 chip, showing the core array and CPU dies.](7e2f2d03a5dda38b038fd4884629a2b4_img.jpg)

Image of the Tegra K1 chip, showing the core array and CPU dies.

Pin  
Compatible

![Image of the Tegra K1 chip, showing the core array and CPU dies, representing the second version.](48f188337e3ba41df38fab9ac0afb1bd_img.jpg)

Image of the Tegra K1 chip, showing the core array and CPU dies, representing the second version.

Quad A15 CPUs

32-bit

3-way Superscalar

Up to 2.3GHz

32K+32K L1\$

Dual Denver CPUs

64-bit

7-way Superscalar

Up to 2.5GHz

128K+64K L1\$

## DENVER VALUE PROPOSITION

![Icon representing performance and efficiency, showing a speedometer and a leaf.](dc1e692e5b7efd8e5a2a790c458646d9_img.jpg)

Icon representing performance and efficiency, showing a speedometer and a leaf.

Highest performance and very energy-efficient ARMv8 processor

- Greater dynamic sharing with GPU
- Extended battery life
- Low latency power-state transition
- Best web browsing experience

![Icon representing PC-class performance, showing a desktop computer setup.](b615ff07e8a0f467f0a6f4783c4463eb_img.jpg)

Icon representing PC-class performance, showing a desktop computer setup.

Designed to bring PC-class performance to the ARM ecosystem

- Content creation
- Gaming
- Enterprise applications

## DENVER CPU

### Highest Perf ARMv8 CPU

- 7-wide superscalar
- Aggressive HW prefetcher

### Dynamic Code Optimization

- Optimize once, use many times
- OOO execution without the power

![](6bbc398f520a7bcc5491cab18d3e4cac_img.jpg)

Diagram illustrating the Denver Core architecture.

The core includes the BPU (Branch Prediction Unit) and IFU (Instruction Fetch Unit), which is connected to the L1 Inst Cache (128 K - 4 Way). The IFU feeds into the ARM HW Decoder. The ARM HW Decoder is connected to the Scheduler and also interacts with the HW Prefetch unit. The HW Prefetch unit feeds into the L1 Data Cache (64 K - 4 Way). The Scheduler is connected to the L1 Data Cache and also feeds into the execution units.

The execution units are arranged horizontally and include: JSR (Jump/Return), IEU0, IEU1, FP0, FP1, LS0, and LS1.

## TEGRA K1 SUPERSCALAR ARCHITECTURE

### Cortex-A15 Tegra K1-32

![](55d2bfe1c3d04e86df8d7a104d802172_img.jpg)

Diagram illustrating the Tegra K1-32 superscalar architecture. The pipeline consists of 8 execution units: Branch, Integer, Integer, Mul, FP NEON, FP NEON, Load, and Store. The execution units are fed by a Scheduler, which is controlled by a Decoder (3 wide).

- Branch: 1
- Integer: 2
- Multiply: 1
- Floating Point/Neon: 2 x 64-bit
- LD/ST: 1 LD and 1 ST

Peak IPC 3

### Denver Tegra K1-64

![](e1dda754c2c88a8ad0b968aea4fc0786_img.jpg)

Diagram illustrating the Tegra K1-64 superscalar architecture. The pipeline consists of 8 execution units: Branch, Mul Integer, Integer, FP NEON, FP NEON, Load Store Integer, and Load Store Integer. The execution units are fed by a Scheduler, which is controlled by a Decoder (predecode) (8 wide).

- Branch: 1
- Integer: 2 (+ Mul) + 2
- Floating Point/Neon: 2 x 128-bit
- LD/ST: 2 LD and/or ST

Peak IPC 7+

## Pipeline Microarchitecture - Mispredict Penalty

![](73c3e4508cae529acf4e6c7fa70b361a_img.jpg)

Diagram illustrating the pipeline microarchitecture and the 13 Cycle Penalty for a misprediction on the Denver architecture.

The pipeline stages shown are: JCC, Bypass, CMP, ES6, EW7, IP1, IC2, IW3, IN4, IN5, SB1, SB2, EB0, EB1, EA2, ED3, EL4, EE5, ES6, EW7.

A misprediction occurs when the CMP stage (ES6) predicts incorrectly. This triggers a Misprediction Signal, which bypasses the ITLB stage (IP1) and the subsequent stages (IC2, IW3, IN4, IN5, SB1, SB2, EB0, EB1, EA2, ED3) and forces execution to continue from the ALU stage (EE5) onwards, leading to a 13 cycle penalty.

![](c0843c6d138705289960d9f53a6e72a1_img.jpg)

Bar chart titled "Branch misprediction rates".

The Y-axis represents "Branch mispredicts per thousand instructions", ranging from 0 to 10.

The X-axis shows three benchmarks: SPECfp2000, Google-Octane, and SPECint2000.

Legend:

- Tegra K1-32 (Red bars)
- Tegra K1-64 (Green bars)

Approximate data points:

| Benchmark     | Tegra K1-32 | Tegra K1-64 |
|---------------|-------------|-------------|
| SPECfp2000    | ~1.0        | ~0.8        |
| Google-Octane | ~4.5        | ~3.0        |
| SPECint2000   | ~9.0        | ~6.5        |

Lower is better.

- Tegra K1-32
  - 15 cycle mispredict
- Tegra K1-64
  - 13 cycle mispredict

Higher ILP and efficiency

### CORE CLUSTER RETENTION STATE

- New power management state: CC4
- Allows cache and architectural state retention
- Allows voltage to be reduced below  $V_{min}$  to a retention voltage
- Fast entry and exit latencies enable wider range of use

![](a71911ad87414271aeb190e0eebcb989_img.jpg)

Graph showing Average Power (mW) versus Idle duration (ms) for three power management states: Rail-gating, Clock-gating, and Cluster retention.

The Y-axis (Avg Power (mW)) ranges from 0 to 200. The X-axis (Idle duration (ms)) ranges from 0 to 400.

Legend:

- Rail-gating (Blue line): Power drops rapidly to near zero mW after approximately 100 ms.
- Clock-gating (Red line): Power drops rapidly to approximately 95 mW after approximately 100 ms, remaining stable.
- Cluster retention (Green line): Power drops rapidly to near zero mW after approximately 100 ms, remaining stable.

### DENVER IDLE POWER IMPROVES WITH RETENTION

Power penalty if entered for short durations

![](91be14371a97fb5ce9eeb29ae18d07c3_img.jpg)

Avg. Power (mW)

Leakage

Overhead from energy required to flush L2

Efficiency crossover

Idle duration (ms)

Rail-gating Clock-gating Cluster retention

## DYNAMIC CODE OPTIMIZATIONOPTIMIZE ONCE, USE MANY TIMES

![](4e0ade2f41b66d5602160da5cc978274_img.jpg)

Instructions

Hardware Decoder

Execution Units

Denver Hardware

Optimizer

Optimization  $\mu$ -interrupt

### DYNAMIC CODE OPTIMIZATIONOPTIMIZE ONCE, USE MANY TIMES

![](32cbf74724dd69f0603b24cf051810a9_img.jpg)

Instructions

Hardware Decoder

Execution Units

Denver Hardware

Dynamic Profile Information

Optimizer

- Unrolls Loops
- Renames registers
- Reorders Loads and Stores
- Improves control flow
- Removes unused computation
- Hoists redundant computation
- Sinks uncommonly executed computation
- Improves scheduling

Optimized µcode

Optimization Cache

### DYNAMIC CODE OPTIMIZATIONOPTIMIZE ONCE, USE MANY TIMES

![](398674b42e3466add6d47f420c136494_img.jpg)

Instructions

Optimization Lookup

Hardware Decoder

Execution Units

Denver Hardware

Optimized code execution from optimization cache

Optimized µcode

Optimization Cache

### DYNAMIC CODE OPTIMIZATIONOPTIMIZE ONCE, USE MANY TIMES

![](2236272d3b3db6e6363337f5a8db72f6_img.jpg)

Instructions

Optimization Lookup

Hardware Decoder

Execution Units

Denver Hardware

Dynamic Profile Information

Optimizer

Optimized  $\mu$ code

Optimized  $\mu$ code

Optimized  $\mu$ code

Optimized  $\mu$ code

Chaining

Optimization Cache

## DENVER PERFORMANCE

![](0b8b087a7baa471015d3ffeaa43d9a6c_img.jpg)

Bar chart showing the performance relative to Tegra K1 32 for various benchmarks and processors.

Y-axis: Performance Relative to Tegra K1 32 (0% to 300%).

X-axis: DMIPS, SPECInt 2K, SPECFP 2K, AnTuTu 4, Geekbench 3 Single-Core, Google Octane v2.0, 16MB Memcpy (GB/s), 16MB Memset (GB/s), 16MB Memread (GB/s).

Legend:

- Baytrail (Celeron N2910)
- Krait-400 (8974-AA)
- iPhone 5s (A7 Cyclone)
- Haswell (Celeron 2955U)
- Tegra K1 64

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

![](eaae122ace5c0d761133c6ce971a6ffd_img.jpg)

Full benchmark run

Dynamic Code Optimizer

Ticks

% Exec Types

Profile of execution

HW Decoder execution

Optimized ucode execution

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](b3df5964338063224492c01f09e4fed6_img.jpg)

This figure displays two stacked bar charts illustrating execution profiles during a full benchmark run (CRAFTY EXECUTION).

**Top Chart: % Exec Types**

This stacked bar chart shows the percentage of execution time spent on different types of instructions over the duration of the benchmark run. The Y-axis represents Ticks (0 to 100). The majority of execution time is spent on a single type of instruction (represented by the large green bars), while smaller percentages are spent on other types (represented by smaller bars in yellow, purple, and blue).

**Bottom Chart: Profile of new ARM instructions**

This bar chart shows the frequency or count of new ARM instructions encountered during the benchmark run. The Y-axis represents ARM instructions (0 to 2,000). The profile shows a significant spike in the count of new ARM instructions near the beginning of the run, followed by a period of low frequency, and then a smaller spike later in the run.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](f4d72193f77f6646a2a1f4baaa927154_img.jpg)

This figure displays performance metrics for a full benchmark run (DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION).

The top chart, titled "% Exec Types", is a stacked bar chart showing the percentage of execution time spent on different types of instructions over the duration of the run. The Y-axis ranges from 0 to 100% (Ticks). The majority of execution time is spent on the green bars, representing the dominant instruction types.

The middle chart, titled "New ARM Code", is a histogram showing the count of new ARM instructions encountered during the run. The Y-axis ranges from 0 to 2,000. The distribution is highly skewed, with a large initial spike followed by very few instructions later in the run.

The bottom chart, titled "Profile of Instructions Per Cycle (IPC)", is a histogram showing the ratio of instructions executed per cycle (IPC) over the duration of the run. The Y-axis ranges from 0.0 to 3.0 (ratio). The IPC values are generally stable, fluctuating between 1.0 and 1.5.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](b6750d26d3dd287a4a4d49b3670a44bd_img.jpg)

This figure displays three stacked bar charts illustrating execution characteristics over the duration of a full benchmark run (labeled "Full benchmark run" above the charts).

- **% Exec Types:** The top chart shows the percentage of execution time spent on different types of instructions. The Y-axis ranges from 0 to 100%. The execution is dominated by a single type (green bars), which accounts for approximately 95% of the execution time. A smaller portion (yellow and brown bars) is also present, particularly at the beginning of the run.
- **New ARM Code:** The middle chart shows the number of new ARM instructions executed. The Y-axis ranges from 0 to 2,000. This metric is very low, indicating minimal new code generation during the benchmark run.
- **IPC (ratio):** The bottom chart shows the Instruction Per Cycle (IPC) ratio. The Y-axis ranges from 0.0 to 3.0. The IPC ratio is generally stable, fluctuating between 1.0 and 1.5, indicating efficient execution.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](7bed2d7c96d86bf922295a1252da52a5_img.jpg)

This figure displays three stacked bar charts illustrating execution characteristics over the duration of a full benchmark run (indicated by the blue arrow labeled "Full benchmark run"). The Y-axis for all charts is labeled "Ticks".

- **% Exec Types:** A stacked bar chart showing the percentage distribution of execution types. The Y-axis ranges from 0 to 100. The chart is dominated by a large green segment, representing the majority of execution time. A significant portion of the execution time is highlighted by a large red shaded area, indicating a specific phase or bottleneck.
- **New ARM Code:** A bar chart showing the count of new ARM instructions executed. The Y-axis ranges from 0 to 2,000. This chart shows a few large spikes, primarily at the beginning and end of the run, with the majority of instructions being small or zero.
- **IPC (ratio):** A bar chart showing the Instruction Per Cycle (IPC) ratio. The Y-axis ranges from 0.0 to 3.0. The IPC ratio is generally low (around 1.0 to 1.5) but shows a significant spike, highlighted by the red shaded area, reaching approximately 2.5.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](96a7eac66ef72bb016c280278506ac63_img.jpg)

This figure displays three stacked bar charts illustrating execution characteristics over the duration of a full benchmark run (indicated by the blue arrow labeled "Full benchmark run").

- **% Exec Types:** The top chart shows the percentage of execution time spent on different types of instructions. The Y-axis ranges from 0 to 100%. The execution is dominated by a single type (green bars), which accounts for approximately 95% of the execution time. A vertical pink shaded area highlights a specific segment of the run.
- **New ARM Code:** The middle chart shows the number of new ARM instructions generated or executed. The Y-axis ranges from 0 to 2,000. This metric is generally low, with a small peak around the time of the pink shaded area.
- **IPC (ratio):** The bottom chart shows the Instruction Per Cycle (IPC) ratio. The Y-axis ranges from 0.0 to 3.0. The IPC is generally stable, fluctuating between 1.0 and 1.5. A vertical pink shaded area highlights a segment where the IPC drops significantly, indicating a performance bottleneck or inefficiency.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](2a77eb32ef4c4d8a5c1758a53a908336_img.jpg)

This figure displays execution metrics over the duration of a full benchmark run (indicated by the blue arrow and the red shaded area).

The metrics shown are:

- **% Exec Types** (Y-axis scale 0 to 100): A stacked bar chart showing the percentage of execution time spent on different types of instructions. The chart shows a transition from a mix of instruction types (green, yellow, purple) to a dominant type (brown/tan) during the red shaded period.
- **New ARM Code** (Y-axis scale 0 to 2,000): A bar chart showing the number of new ARM instructions generated or used. This metric is low throughout the run.
- **IPC** (Y-axis scale 0.0 to 3.0 (ratio)): A bar chart showing the Instruction Per Cycle (IPC) ratio. The IPC is generally low (around 1.0 to 1.5) and remains relatively stable during the red shaded period.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

Full benchmark run

![](9a19da4f7fccb96a934411c0bb5a386d_img.jpg)

This figure displays three stacked bar charts illustrating execution characteristics over the duration of a full benchmark run (indicated by the blue arrow labeled "Full benchmark run").

- **% Exec Types:** The top chart shows the percentage of execution time spent on different types of instructions. The Y-axis ranges from 0 to 100%. The execution is dominated by a single type (green bars), which accounts for approximately 95% of the execution time. Other types (yellow, brown, and dark red) contribute the remaining 5%.
- **New ARM Code:** The middle chart shows the number of new ARM instructions executed. The Y-axis ranges from 0 to 2,000. This metric is very low, with only a few instructions executed, indicating minimal code generation or modification.
- **IPC (ratio):** The bottom chart shows the Instruction Per Cycle (IPC) ratio. The Y-axis ranges from 0.0 to 3.0. The IPC ratio is generally stable, fluctuating between 1.0 and 1.5, suggesting efficient execution.

### DCO: AN EXAMPLE SPECINT - CRAFTY EXECUTION

3% of benchmark run

![](9b5411fa2d169b66f6185fbf67b49766_img.jpg)

This figure displays three stacked bar charts illustrating execution characteristics during a 3% segment of a benchmark run (likely SPECINT - CRAFTY EXECUTION).

- **% Exec Types (Top Chart):** A stacked bar chart showing the percentage of execution time spent on different types of instructions. The Y-axis ranges from 0 to 100%. The execution is dominated by green instructions (approximately 60-70%), followed by yellow (approximately 20-30%), and smaller contributions from purple and red instructions.
- **New ARM Code (Middle Chart):** A bar chart showing the count of new ARM instructions executed. The Y-axis ranges from 0 to 120. The count starts high (around 100) and decreases rapidly, stabilizing near zero after the initial segment.
- **IPC (Bottom Chart):** A bar chart showing the Instruction Per Cycle (IPC) ratio. The Y-axis ranges from 0.0 to 3.0. The IPC ratio is generally stable, fluctuating between 1.0 and 1.5.

## CONCLUSION

- Dynamic Code Optimization is the architecture of the future
  - Breaks the out-of-order window physical limitation
  - Opens synergy between HW and SW that current architectures lack
  - Improves efficiency by optimizing once and using many times
- Delivering PC-class performance to mobile form factors
  - Enables PC-class gaming experience
  - Enables true enterprise applications
  - Enables content creation

## ACKNOWLEDGMENT

- We would like to thank the CPU team in NVIDIA for all the creativity, hard work, and dedication to bring this vision to a reality.