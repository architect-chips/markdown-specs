

# Formal Verification of Macro-op Cache for Arm Cortex-A77, and its Successor CPU

Vaibhav Agrawal

Principal Engineer, Arm

March 4, 2020

![ARM logo](390120de4fe440c42fea8154fcaad334_img.jpg)

ARM logo

## Cortex A-77

- Announced in Q2, 2019
- From Wikipedia:
  - The **Arm Cortex-A77** is a microarchitecture implementing the ARMv8.2-A 64-bit instruction set designed by ARM Holdings' Austin design centre. The Cortex-A77 is a 4-wide decode out-of-order superscalar design **with a new 1.5K macro-OP (MOPs) cache**. The instruction fetch is 6-wide (up from 4-wide). The backend is 12 execution ports with a pipeline depth of 13 stages and the execution latencies of 10 stages.

## Agenda

- Instruction fetch unit overview
- Reducing design complexity
- End to end checker design, including macro-op cache and instr cache coherence
- Results and summary

### Instruction Fetch Unit Overview

![](7fb5215fd72210a2e4cce6df55550c89_img.jpg)

Diagram illustrating the Instruction Fetch Unit Overview, showing the interaction between the Fetch Unit (left) and the iDecode unit (right).

**Fetch Unit Components and Flow:**

- **Architectural registers** (Top boundary).
- **Predictors and next fetch address generation** receives input CT and interacts with the **Fetch Queue**.
- **Fetch Queue** interacts with **MMU** (via ITLB).
- **MMU** receives input IQ and interacts with **itlb**.
- **MMU** interacts with **Instruction Cache** and **Macro-op cache**.
- **Instruction Cache** interacts with **Macro-op cache**.
- **Macro-op cache** interacts with **Snoop**.
- **Snoop** interacts with **CMO, TMO, DAR**.
- **Macro-op cache** interacts with **ID** and **L2**.

**iDecode Unit Components and Flow:**

- **iDecode** unit contains two parallel **DECODE** blocks.
- The top **DECODE** block receives input ID and interacts with **Instruction Cache**.
- The bottom **DECODE** block receives input ID and interacts with **Macro-op cache**.
- The output of the iDecode unit feeds into the **Macro-op cache**.

### Verification Goal for Formal

- Very high flop and gate count => high control complexity
- Therefore, goal was to find bugs (full proofs a bonus)
- Complement simulation for functional verification
- Primary vehicle for ensuring no hangs (forward progress)

## MANAGING COMPLEXITY

### Managing Complexity

- Complexity reduction
  - Reducing the sequential depth and/or time required to reach interesting design states

| S. No. | Complexity management technique                           |
|--------|-----------------------------------------------------------|
| 1      | Table mutations (designer assisted, or tool assisted)     |
| 2      | RAMs: Replace number of tracked entries (sets for caches) |
| 3      | Initial Value abstractions                                |
| 4      | Reduce data width if implementation doesn't care          |
| 5      | Black boxing                                              |

### Table Mutations

![](a71911ad87414271aeb190e0eebcb989_img.jpg)

Diagram illustrating the architecture of a processor core, likely focusing on the instruction fetch and decode path, relevant to Table Mutations.

The diagram shows the following components and data paths:

- **Architectural registers** (Top section): Contains the Fetch Queue and Instruction Cache.
- **Fetch Queue** and **Instruction Cache** are connected to the **Macro-op cache** (highlighted in orange).
- The **Macro-op cache** is connected to the **Snoop** unit.
- The **Snoop** unit is connected to the **CMO, TMO, DAR** (Cache Management/Translation/Debugging) unit.
- The **Macro-op cache** is connected bidirectionally to the **L2** cache.
- The **Macro-op cache** is connected bidirectionally to the **ID** (Instruction Decoder) unit.
- The **Fetch Queue** is connected bidirectionally to the **Predictors and next fetch address generation** unit.
- The **Predictors and next fetch address generation** unit receives input from the **CT** (Control Transfer) unit.
- The **Predictors and next fetch address generation** unit is connected to the **BX** (Branch/Exception) unit.
- The **BX** unit receives input from the **IQ** (Instruction Queue) unit.
- The **BX** unit is connected to the **iTLB** (Instruction Translation Lookaside Buffer).
- The **iTLB** unit is connected bidirectionally to the **MMU** (Memory Management Unit).

### Reduce Number of Tracked Sets in Caches

![](91be14371a97fb5ce9eeb29ae18d07c3_img.jpg)

Diagram illustrating a cache hierarchy and associated components, likely for a DVCON 2020 presentation.

The diagram shows the following components and their interconnections:

- **Architectural registers** (Top level)
- **Predictors and next fetch address generation** (Left side, receives CT input)
- **Fetch Queue** (Center, connected to Predictors and next fetch address generation)
- **BX** (Left side, receives IQ input, connected to Predictors and next fetch address generation)
- **iTLB** (Center, connected to MMU)
- **MMU** (Bottom, connected to iTLB)
- **Instruction Cache** (Top right, connected to ID)
- **Macro-op cache** (Bottom right, connected to ID)
- **Snoop** (Bottom right, connected to CMO, TMO, DAR)
- **ID** (Bottom, connected to Instruction Cache, Macro-op cache, and L2)
- **L2** (Bottom, connected to Macro-op cache and ID)
- **CMO, TMO, DAR** (Bottom, connected to Snoop)

### IVAs – Initial Value Abstractions

![Diagram illustrating Initial Value Abstractions (IVAs). The diagram shows a large light blue rectangular area containing two concentric sets of blue ellipses (representing regions or constraints). The left set is centered around a green dot. The right set is centered around a green dot, which is enclosed by an orange oval boundary. A red dot is located on the outermost blue ellipse of the left set. A cyan arrow points from this red dot towards the right set. A dashed line connects the red dot to the green dot in the right set. A black arrow points from the green dot in the right set towards a second red dot located on the innermost blue ellipse of the right set.](349ca0a6a9c2e2651a4deeeaf8be6da1_img.jpg)

Diagram illustrating Initial Value Abstractions (IVAs). The diagram shows a large light blue rectangular area containing two concentric sets of blue ellipses (representing regions or constraints). The left set is centered around a green dot. The right set is centered around a green dot, which is enclosed by an orange oval boundary. A red dot is located on the outermost blue ellipse of the left set. A cyan arrow points from this red dot towards the right set. A dashed line connects the red dot to the green dot in the right set. A black arrow points from the green dot in the right set towards a second red dot located on the innermost blue ellipse of the right set.

### Reduce Instructions & Mops Size & Number

![](10c82dcc5f2c237961329dd29d65859c_img.jpg)

Diagram illustrating a processor architecture focused on reducing instructions and Mops (Memory Operations) size and number.

The architecture includes:

- **Architectural registers** (Top level).
- **Predictors and next fetch address generation** (Left side, connected to CT input).
- **Fetch Queue** (Center).
- **Instruction Cache** (Top right, connected to ID input).
- **Mop cache** (Bottom right, connected to ID input).
- **MMU** (Bottom center, connected to iTLB).
- **iTLB** (Bottom center, connected to MMU and BX).
- **BX** (Bottom left, connected to IQ input and Predictors and next fetch address generation).
- **Snoop** (Bottom right, connected to CMO, TMO, DAR).
- **Memory Hierarchy** (Bottom): ID, L2, CMO, TMO, DAR.

Key connections shown:

- CT input connects to Predictors and next fetch address generation.
- IQ input connects to BX.
- Predictors and next fetch address generation connects to Fetch Queue.
- Fetch Queue connects to iTLB.
- iTLB connects to MMU.
- MMU connects to iTLB and ID.
- Instruction Cache connects to ID.
- Mop cache connects to ID.
- Instruction Cache connects to L2.
- Mop cache connects to L2.
- Snoop connects to CMO, TMO, DAR.

### Black-boxing Unneeded Design Components

![](f176174c2978785e86a8352bd45e322e_img.jpg)

Diagram illustrating the black-boxing of unneeded design components in a processor architecture.

The diagram shows the following components and data paths:

- **Architectural registers** (Top section).
- **Predictors and next fetch address generation** (Left, connected to BX and CT).
- **Fetch Queue** (Center, connected to Predictors and next fetch address generation, iTLB, and ID).
- **iTag** and **iData** (Center, connected to Macro-op cache and ID).
- **Macro-op cache** (Center, connected to iTag, iData, and ID).
- **iTLB** (Center, connected to Fetch Queue and MIMU).
- **Snoop** (Bottom, connected to ID, L2, and CMO, TMO, DAR).
- **MMU** (Bottom, connected to iTLB and ID).
- **CT** (Center, connected to Predictors and next fetch address generation and BX).
- **BX** (Bottom, connected to CT and ID).
- **ID** (Bottom, connected to Fetch Queue, Macro-op cache, Snoop, and ID).
- **L2** (Bottom, connected to Macro-op cache and Snoop).
- **CMO, TMO, DAR** (Bottom, connected to Snoop).
- **IQ** (Left, connected to BX and Predictors and next fetch address generation).
- **Decoding Unit** (Right, connected to ID, IQ, and ID).

## END TO END CHECKER DESIGN

### The Basics of Formal Checker Design

- Minimize the number of Flops (both TB and RTL)
- Avoid complex tracking structures
- Think pseudo-constants
  - assume: ##1 \$stable (signal)
- Think coloring (tagging) techniques
- Oracles based management of conflicting constraints for assertions

### Macro-op Cache Ordering Checker

- 2 Tracked VAs
- Constraint:  $VA1 \to VA2$
- Constraint: color mops at tr\_VA{1,2}
- Check on outputs:  $m[VA1] \to m[VA2]$

- Constrain both preloading and fills

![](fe753d01ad5fe6cf150018c958173c6d_img.jpg)

Diagram illustrating the Mop cache structure and constraints.

The cache is organized into 4 ways (0, 1, 2, 3) and 4 sets (0, 1, 2, 3). The structure is labeled "Mop cache".

Legend:

- ●  $m[VA1]$
- ●  $m[VA2]$
- ● All other VAs

The diagram shows entries in Set 0, Way 1, and Way 2. Entries in Set 0, Way 1, and Set 0, Way 2 are colored light blue, indicating  $m[VA1]$ . Entries in Set 0, Way 2 and Set 1, Way 2 are colored teal, indicating  $m[VA2]$ . A curved arrow indicates a transition or dependency between entries in Set 0, Way 2 and Set 1, Way 2.

### Macro-op Fusion with Nop Elimination: Ordering Check

- 3 Tracked VAs
- Constraint:
  - VA1 $\to$ VA2 $\to$ VA3
  - Coloring
  - Fuse  
     $m[\text{VA2}] \leftrightarrow m[\text{VA3}]$
  - $m[\text{VA2}]$  is eliminated-nop
- Check on outputs:  
   $m[\text{VA1}] \to m[\text{VA3}]$

- Constrain both preloading and fills

![](e95f47f7a4c01c8889d6d46919b4c73d_img.jpg)

Legend:

- $m[\text{VA1}] = 2'b01$
- $m[\text{VA2}] = 2'b10$
- $m[\text{VA3}] = 2'b11$
- All other VAs =  $2'b00$

Diagram showing a 4-set, 4-way Mop cache structure. The cache is divided into 4 sets (0, 1, 2, 3) and 4 ways (0, 1, 2, 3). The cache lines are colored according to the legend. A curved arrow indicates a specific sequence of cache line accesses or updates.

Mop cache

### Breakpoint Check

- 2 Tracked VAs
- Constraint:  $VA1 \to VA2$
- Constraint: color mops at  $VA\{1,2\}$
- Constraint: bkpt always on  $VA2$ ; never on  $VA1$
- Liveness Chk:  $d[VA1]$  must eventually be seen
- Safety Chk:  $d[VA2]$  not seen

- Constrain both preloading and fills

![](fdcfba1180dc160c7d539c5fb2a6c1e6_img.jpg)

Legend:

- d[VA1]
- d[VA2]
- All other VAs

Diagram: Example cache structure showing 4 sets (0, 1, 2, 3) and 4 ways (0, 1, 2, 3). The cache is mostly empty (red background). Set 0, Way 1 contains d[VA1] (light blue). Set 1, Way 1 contains d[VA2] (dark blue). Set 1, Way 2 contains d[VA2] (dark blue). A curved arrow indicates a transition or movement within the cache.

Example cache

### Coherence Checking Between Instr Cache and Macro-op cache

- 1 Tracked VA: VA1
- Constraint: color mops & instrs at VA1
- Constraint: d[VA1] in macro-op cache only if also in instr cache
- Check: If d[VA1] absent from instr cache, then it must also be absent from macro-op cache
- Constrain both preloading and fills

![](1a6a826cc13d4e964b7bda69508d78e6_img.jpg)

Diagram illustrating an example cache structure (4 sets, 4 ways) and the placement of tracked and other VAs.

The cache structure is labeled "Example cache" and shows 4 sets (0, 1, 2, 3) and 4 ways (0, 1, 2, 3).

Legend:

- d[VA1] (Tracked VA, represented by a light blue circle)
- All other VAs (Other VAs, represented by a light pink circle)

Cache entries are color-coded:

- Set 0: All entries are red.
- Set 1: Entry in Way 1 is light blue (d[VA1]). Other entries are red.
- Set 2: Entry in Way 2 is light blue (d[VA1]). Other entries are red.
- Set 3: All entries are red.

## RESULTS AND SUMMARY

### Macro-op / Instr Cache Switching Bug

- For Power: macro-op cache hit => instr cache lookup suppressed
- Instr cache awakens if an address misses in macro-op cache
- Bug in icac wakeup functionality after <N> consecutive back to back macro-op cache hits

### Mopc Fusion with Nop Elimination

Fused instructions: (A, A+4)

![Diagram showing a sequence of instructions in memory. Two consecutive instructions, labeled A and A+4, are highlighted in red and grouped together, labeled 'Fused mops'.](20ab59bc10b900f6cf8a34549848bbf4_img.jpg)

Diagram showing a sequence of instructions in memory. Two consecutive instructions, labeled A and A+4, are highlighted in red and grouped together, labeled 'Fused mops'.

Predicted taken or breakpoint

- If
  - Instruction{A} predicted as taken branch, OR
  - Instruction{A+4} has a breakpoint
- Then
  - Instr{A+4} cannot be delivered from macro-op cache

### Forward Progress Bugs by Formal

- 10+ bugs in database for forward progress; all were found by formal before other testbenches found them
- 2 were corner cases
- 2 bugs found by bug hunting

### Bugs Found by Coherence Checker

- 7 bugs were found by formal checker
- Checker ready before sim environment could be brought up
- 2 of the bugs were “corner case” (included line victimizations, followed by fills, with parity errors, and snoops from L2)

### Formal Bug dissection (all bugs)

#### By RTL quality

![](45329c7d9aa2bd1290af5b2027f08d7e_img.jpg)

Pie chart showing the distribution of bugs by RTL quality (time since bring up):

- more than 6 months: 78%
- 3 to 6 months: 10%
- last 3 months: 12%

#### Both RTL bring up and late in project

- 78% of bugs found during RTL bring up
- 12% found in the last 3 months

### Formal Bugs by Property Type (all bugs)

![](5500ab73cf84ccc0055eecf28889b4db_img.jpg)

Pie chart showing the distribution of Formal Bugs by Property Type (all bugs).

| Property Type | Percentage |
|---------------|------------|
| End to end    | 42%        |
| Embedded      | 38%        |
| Interface     | 20%        |

## Summary

- Definite impact on ensuring forward progress for high performance A class CPU core
- Exposed a high risk, leading to hardware change: deadlock avoidance mode was added
- Complexity management is crucial
- IVAs necessary, and highly effective
- Bugs found both for bring up, and later in the development cycle before LAC