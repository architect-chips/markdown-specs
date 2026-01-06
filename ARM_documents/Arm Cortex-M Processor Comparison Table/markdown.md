

# Arm Cortex-M Processor Comparison Table

The Cortex-M processor family is optimized for cost and energy-efficient microcontrollers. These processors are found in a variety of applications, including IoT, industrial and everyday consumer devices.

The processor family is based on the M-Profile Architecture that provides low-latency and a highly deterministic operation, for deeply embedded systems.

| Feature                                   | Cortex-M0         | Cortex-M0+        | Cortex-M1         | Cortex-M23       | Cortex-M3         | Cortex-M4         | Cortex-M33       | Cortex-M35P      | Cortex-M52                   | Cortex-M55          | Cortex-M7       | Cortex-M85          |
|-------------------------------------------|-------------------|-------------------|-------------------|------------------|-------------------|-------------------|------------------|------------------|------------------------------|---------------------|-----------------|---------------------|
| Instruction Set Architecture              | Armv6-M           | Armv6-M           | Armv6-M           | Armv8-M Baseline | Armv7-M           | Armv7-M           | Armv8-M Mainline | Armv8-M Mainline | Armv8.1-M Mainline           | Armv8.1-M Mainline  | Armv7-M         | Armv8.1-M Mainline  |
| TrustZone for Armv8-M                     | No                | No                | No                | Yes (option)     | No                | No                | Yes (option)     | Yes (option)     | Yes (option)                 | Yes (option)        | No              | Yes                 |
| Helium (M-Profile Vector Extension)       | No                | No                | No                | No               | No                | No                | No               | No               | Single-beat (option)         | Dual-beat (option)  | No              | Dual-beat (option)  |
| PACBTI Extension                          | No                | No                | No                | No               | No                | No                | No               | No               | Yes (option)                 | No                  | No              | Yes (option)        |
| Floating-Point Unit (FPU)                 | No                | No                | No                | No               | No                | SP (option)       | SP (option)      | SP (option)      | HP, SP, DP (option)          | HP, SP, DP (option) | SP, DP (option) | HP, SP, DP (option) |
| Digital Signal Processing (DSP) Extension | No                | No                | No                | No               | No                | Yes               | Yes (option)     | Yes (option)     | Yes                          | Yes                 | Yes             | Yes                 |
| Hardware Divide                           | No                | No                | No                | Yes              | Yes               | Yes               | Yes              | Yes              | Yes                          | Yes                 | Yes             | Yes                 |
| Arm Custom Instructions                   | No                | No                | No                | No               | No                | No                | Yes (option)     | No               | Yes (option)                 | Yes (option)        | No              | Yes (option)        |
| Coprocessor Interface                     | No                | No                | No                | No               | No                | No                | Yes (option)     | Yes (option)     | Yes (option)                 | Yes (option)        | No              | Yes (option)        |
| DMIPS/MHz*                                | 0.96              | 0.99              | 0.88              | 1.03             | 1.24              | 1.26              | 1.54             | 1.50             | 1.60                         | 1.69                | 2.31            | 3.13                |
| CoreMark@MHz*                             | 2.33              | 2.46              | 1.83              | 2.64             | 3.45              | 3.54              | 4.10             | 4.10             | 4.30                         | 4.40                | 5.29            | 6.28                |
| Maximum # External Interrupts             | 32                | 32                | 32                | 240              | 240               | 240               | 480              | 480              | 480                          | 480                 | 240             | 480                 |
| Maximum MPU Regions                       | 0                 | 8                 | 0                 | 16               | 8                 | 8                 | 16               | 16               | 16                           | 16                  | 16              | 16                  |
| Main Bus                                  | AHB Lite (32-bit) | AHB Lite (32-bit) | AHB Lite (32-bit) | AHB (32-bit)     | AHB Lite (32-bit) | AHB Lite (32-bit) | AHB (32-bit)     | AHB (32-bit)     | AXI (32-bit) or AHB (32-bit) | AXI (64-bit)        | AXI (64-bit)    | AXI (64-bit)        |
| Instruction Cache                         | No                | No                | No                | No               | No                | No                | No               | 2-16kB           | 0-64kB                       | 0-64kB              | 0-64kB          | 0-64kB              |
| Data Cache                                | No                | No                | No                | No               | No                | No                | No               | No               | 0-64kB                       | 0-64kB              | 0-64kB          | 0-64kB              |
| Instruction TCM                           | No                | No                | 0-1MB             | No               | No                | No                | No               | No               | 0-16MB                       | 0-16MB              | 0-16MB          | 0-16MB              |
| Data TCM                                  | No                | No                | 0-1MB             | No               | No                | No                | No               | No               | 0-16MB                       | 0-16MB              | 0-16MB          | 0-16MB              |
| Dual Core Lock-Step (DCLS) Configuration  | No                | No                | No                | No               | No                | No                | No               | Yes              | Yes (option)                 | Yes (option)        | Yes (option)    | Yes (option)        |

| Common Criteria Certification | No | No | No | No | No | No | Yes | Yes | No | No | No | No |
|-------------------------------|----|----|----|----|----|----|-----|-----|----|----|----|----|
|-------------------------------|----|----|----|----|----|----|-----|-----|----|----|----|----|

\*See individual Cortex-M product pages for further information.

SP = Single-Precision

DP = Double-Precision

HP = Half-Precision

For more information, contact your Arm account manager today or explore the processors in more detail here: [developer.arm.com/ip-products/processors/cortex-m](https://developer.arm.com/ip-products/processors/cortex-m)