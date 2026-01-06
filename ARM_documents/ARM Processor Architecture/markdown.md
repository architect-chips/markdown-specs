

# ARM Processor Architecture

Jin-Fu Li

Department of Electrical Engineering

National Central University

Adopted from National Chiao-Tung University  
IP Core Design

- ARM Processor Core
- Memory Hierarchy
- Software Development
- Summary

## ARM Processor Core

### 3-Stage Pipeline ARM Organization

![](7fb5215fd72210a2e4cce6df55550c89_img.jpg)

Diagram illustrating the 3-Stage Pipeline ARM Organization. The pipeline stages are: Instruction Decode and Control, Data In Register, and Data Out Register.

The Instruction Decode and Control stage receives the instruction  $D[31:0]$  and generates control signals. It also provides the PC value to the Address Register and the PC value to the Register Bank.

The Address Register receives the PC value, the instruction  $A[31:0]$ , and the output of the Incrementer. It outputs the address to the Register Bank and the ALU Bus.

The Register Bank holds the PC value and provides data to the Multiply Register and the Barrel Shifter. It also receives data from the ALU Bus and outputs data to the Multiply Register and the Barrel Shifter.

The Multiply Register provides data to the Barrel Shifter.

The Barrel Shifter receives data from the Multiply Register and the Register Bank, and outputs data to the ALU.

The ALU receives data from the Register Bank, the Multiply Register, and the Barrel Shifter. It outputs data to the Register Bank and the Data Out Register.

The Data Out Register receives data from the ALU and outputs data to the Data In Register.

The Data In Register receives data from the Data Out Register and outputs data to the Register Bank.

- Register Bank
  - 2 read ports, 1 write ports, access any register
  - 1 additional read port, 1 additional write port for r15 (PC)
- Barrel Shifter
  - Shift or rotate the operand by any number of bits
- ALU
- Address register and incrementer
- Data Registers
  - Hold data passing to and from memory
- Instruction Decoder and Control

### 3-Stage Pipeline (1/2)

![](7a3561af571faf036baa93f5f4b1bdb9_img.jpg)

Diagram illustrating a 3-stage pipeline over time for three instructions (1, 2, 3). The stages are Fetch, Decode, and Execute. The horizontal axis represents time, and the vertical axis represents the instruction number.

Instruction 1 is shown completing the Fetch stage. Instruction 2 is shown completing the Decode stage. Instruction 3 is shown completing the Execute stage.

#### ☐ Fetch

- The instruction is fetched from memory and placed in the instruction pipeline

#### ☐ Decode

- The instruction is decoded and the datapath control signals prepared for the next cycle

#### ☐ Execute

- The register bank is read, an operand shifted, the ALU result generated and written back into destination register

### 3-Stage Pipeline (2/2)

- At any time slice, 3 different instructions may occupy each of these stages, so the hardware in each stage has to be capable of independent operations
- When the processor is executing data processing instructions, the **latency = 3** cycles and the **throughput = 1** instruction/cycle

#### Multi-cycle Instruction

![](c0843c6d138705289960d9f53a6e72a1_img.jpg)

Diagram illustrating the execution of a multi-cycle instruction across 5 cycles (1 to 5) over time. The instruction is labeled "instruction" and the horizontal axis is labeled "time".

The stages of the instruction execution are:

- Cycle 1: fetch ADD, decode, execute
- Cycle 2: fetch STR, decode, calc. addr., data xfer
- Cycle 3: fetch ADD, decode, execute
- Cycle 4: fetch ADD, decode, execute
- Cycle 5: fetch ADD, decode, execute

- Memory access (fetch, data transfer) in every cycle
- Datapath used in every cycle (execute, address calculation, data transfer)
- Decode logic generates the control signals for the data path use in next cycle (decode, address calculation)

#### Data Processing Instruction

![](a71911ad87414271aeb190e0eebcb989_img.jpg)

Diagram (a) illustrates register-register operations. The address register feeds the PC register. The PC register output is Rd registers ( $R_n$  and  $R_m$ ). The Rd registers output feeds the 'mult' unit. The 'mult' unit output feeds the 'as ins.' unit. The 'as ins.' unit output feeds the 'as instruction' unit. The 'as instruction' unit output feeds the 'data out' unit and the 'i. pipe' unit. The 'data in' unit feeds the 'i. pipe' unit. The 'i. pipe' unit output feeds the 'data out' unit. The 'PC' register output also feeds the 'increment' unit, which feeds the 'address register'.

(a) register - register operations

![](ecb25d766719ce041cf4cc390791a098_img.jpg)

Diagram (b) illustrates register-immediate operations. The address register feeds the PC register. The PC register output is Rd registers ( $R_n$  and  $R_m$ ). The Rd registers output feeds the 'mult' unit. The 'mult' unit output feeds the 'as ins.' unit. The 'as ins.' unit output feeds the 'as instruction' unit. The 'as instruction' unit output feeds the 'data out' unit and the 'i. pipe' unit. The 'data in' unit feeds the 'i. pipe' unit. The 'i. pipe' unit output feeds the 'data out' unit. The 'as instruction' unit output also feeds the immediate value register [7:0]. The 'PC' register output also feeds the 'increment' unit, which feeds the 'address register'.

(b) register - immediate operations

All operations take place in a single clock cycle

## **Data Transfer Instructions**

![](d4e9f8f6bf5d7853ecae9c9633900af1_img.jpg)![](0ba998c66ef6a980bac9c0c12e9452bf_img.jpg)

(a) 1st cycle - compute address

![](c37fe03d7cad74ad675a0eb16aa43821_img.jpg)

(b) 2nd cycle - store data & auto-index

- Computes a memory address similar to a data processing instruction
- Load instruction follow a similar pattern except that the data from memory only gets as far as the 'data in' register on the 2nd cycle and a 3rd cycle is needed to transfer the data from there to the destination register

#### Branch Instructions

![](7801d00a216dc4dc8a7d210dcb5fe3c5_img.jpg)

Diagram (a) illustrates the 1st cycle for computing the branch target. The address register feeds into the PC registers. The PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations.

(a) 1st cycle - compute branch target

![](6b32b7b928d34eeccb15c29cdf9d2cb3_img.jpg)

Diagram (b) illustrates the 2nd cycle for saving the return address. The address register feeds into the PC registers. The PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then used for data out, data in, and i. pipe operations. Additionally, the PC registers output the PC value, which is multiplied (mult) by the instruction field  $IsI \#2$  (labeled  $IsI \#2$ ), resulting in the calculation  $= A + B$ . The output of this calculation is the branch target address, which is 23 bits wide ( $[23:0]$ ). This address is then

##### Branch Pipeline Example

![](10c82dcc5f2c237961329dd29d65859c_img.jpg)

| Cycle   |           | 1     | 2      | 3       | 4       | 5      |         |         |       |
|---------|-----------|-------|--------|---------|---------|--------|---------|---------|-------|
| address | operation |       |        |         |         |        |         |         |       |
| 0x8000  | BL        | fetch | decode | execute | linkret | adjust |         |         |       |
| 0x8004  | X         |       | fetch  | decode  |         |        |         |         |       |
| 0x8008  | XX        |       |        | fetch   |         |        |         |         |       |
| 0x8FEC  | ADD       |       |        |         | fetch   | decode | execute |         |       |
| 0x8FF0  | SUB       |       |        |         |         | fetch  | decode  | execute |       |
| 0x8FF4  | MOV       |       |        |         |         |        | fetch   | decode  | fetch |

- Breaking the pipeline
- Note that the core is executing in the ARM state

### 5-Stage Pipeline ARM Organization

$$\square T_{\text{prog}} = N_{\text{inst}} \cdot \text{CPI} / f_{\text{clk}}$$

- $T_{\text{prog}}$ : the time that execute a given program
- $N_{\text{inst}}$ : the number of ARM instructions executed in the program => compiler dependent
- CPI: average number of clock cycles per instructions => hazard causes pipeline stalls
- $f_{\text{clk}}$ : frequency

$\square$  Separate instruction and data memories => **5** stage pipeline

$\square$  Used in ARM9TDMI

### 5-Stage Pipeline Organization (1/2)

![](b05a8a3551db31147979064952179990_img.jpg)

Diagram illustrating a 5-stage pipeline organization. The stages are Fetch, Instruction Decode, Execute, Buffer/Data, and Write-Back.

**Fetch Stage:** The PC register feeds into the I-cache. The I-cache output goes to I decode. The PC register is updated by the output of the I decode stage (PC + 4). The I decode stage outputs the instruction fields (immediate fields, reg shift) and the instruction decode signal.

**Instruction Decode Stage:** The instruction fields are used by the register read stage. The register read stage outputs the register operands (r15, r15) and the instruction decode signal.

**Execute Stage:** The register operands are used by the ALU. The ALU output goes to the byte repl. stage. The byte repl. stage output goes to the D-cache. The D-cache output goes to the rot/sgn ex stage. The rot/sgn ex stage output goes to the register write stage. The D-cache also outputs the load/store address.

**Buffer/Data Stage:** The load/store address is used by the m ux stage. The m ux stage output goes to the LDM/STM stage. The LDM/STM stage output goes to the register write stage. The register write stage output goes to the write-back stage.

**Write-Back Stage:** The register write stage output goes to the write-back stage. The write-back stage output goes to the PC register.

**Control Signals:** The PC register is updated by the output of the write-back stage (PC + 4). The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage output is used by the m ux stage. The m ux stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The register write stage output is also used by the D-cache. The D-cache output is used by the rot/sgn ex stage. The rot/sgn ex stage output is used by the register write stage. The register write stage output is used by the write-back stage. The write-back stage output is used by the PC register. The PC register output is used by the I-cache and the LDM/STM stage. The LDM/STM stage

## **5-Stage Pipeline Organization (2/2)**

![](78f163db583eb0c6d013e6f8ffe6d7d8_img.jpg)![](c2b98986bdf45e15707f6b2bd7ade2bd_img.jpg)

## Buffer/Data

Data memory is accessed if required. Otherwise the ALU result is simply buffered for one cycle

## Write back

The result generated by the instruction are written back to the register file, including any data loaded from memory

## Pipeline Hazards

- There are situations, called ***hazards***, that prevent the next instruction in the instruction stream from being executing during its designated clock cycle. Hazards reduce the performance from the ideal speedup gained by pipelining.
- There are three classes of hazards:
  - **Structural Hazards**: They arise from resource conflicts when the hardware cannot support all possible combinations of instructions in simultaneous overlapped execution.
  - **Data Hazards**: They arise when an instruction depends on the result of a previous instruction in a way that is exposed by the overlapping of instructions in the pipeline.
  - **Control Hazards**: They arise from the pipelining of branches and other instructions that change the PC

### Structural Hazards

- When a machine is pipelined, the overlapped execution of instructions requires pipelining of functional units and duplication of resources to allow all possible combinations of instructions in the pipeline.
- If some combination of instructions cannot be accommodated because of a *resource conflict*, the machine is said to have a **structural hazard**.

#### Example

☐ A machine has shared a **single-memory** pipeline for data and instructions. As a result, when an instruction contains a data-memory reference (load), it will conflict with the instruction reference for a later instruction (instr 3):

| Clock cycle number |    |    |    |            |     |     |     |    |
|--------------------|----|----|----|------------|-----|-----|-----|----|
| instr              | 1  | 2  | 3  | 4          | 5   | 6   | 7   | 8  |
| load               | IF | ID | EX | <b>MEM</b> | WB  |     |     |    |
| Instr 1            |    | IF | ID | EX         | MEM | WB  |     |    |
| Instr 2            |    |    | IF | ID         | EX  | MEM | WB  |    |
| Instr 3            |    |    |    | <b>IF</b>  | ID  | EX  | MEM | WB |

##### Solution (1/2)

☐ To resolve this, we **stall** the pipeline for one clock cycle when a data-memory access occurs. The effect of the stall is actually to occupy the resources for that instruction slot. The following table shows how the stalls are actually implemented.

|         | Clock cycle number |    |    |              |           |     |    |     |    |
|---------|--------------------|----|----|--------------|-----------|-----|----|-----|----|
| instr   | 1                  | 2  | 3  | 4            | 5         | 6   | 7  | 8   | 9  |
| load    | IF                 | ID | EX | <b>MEM</b>   | WB        |     |    |     |    |
| Instr 1 |                    | IF | ID | EX           | MEM       | WB  |    |     |    |
| Instr 2 |                    |    | IF | ID           | EX        | MEM | WB |     |    |
| Instr 3 |                    |    |    | <b>stall</b> | <b>IF</b> | ID  | EX | MEM | WB |

##### Solution (2/2)

- Another solution is to use separate instruction and data memories.
- ARM is use **Harvard** architecture, so we do not have this hazard

### Data Hazards

☐ **Data hazards** occur when the pipeline changes the order of read/write accesses to operands so that the order differs from the order seen by sequentially executing instructions on the unpipelined machine.

|     |            | Clock cycle number |    |                   |                   |                  |                   |     |     |    |  |
|-----|------------|--------------------|----|-------------------|-------------------|------------------|-------------------|-----|-----|----|--|
|     |            | 1                  | 2  | 3                 | 4                 | 5                | 6                 | 7   | 8   | 9  |  |
| ADD | R1,R2,R3   | IF                 | ID | EX                | MEM               | WB               |                   |     |     |    |  |
| SUB | R4,R5,R1   |                    | IF | ID <sub>sub</sub> | EX                | MEM              | WB                |     |     |    |  |
| AND | R6,R1,R7   |                    |    | IF                | ID <sub>and</sub> | EX               | MEM               | WB  |     |    |  |
| OR  | R8,R1,R9   |                    |    |                   | IF                | ID <sub>or</sub> | EX                | MEM | WB  |    |  |
| XOR | R10,R1,R11 |                    |    |                   |                   | IF               | ID <sub>xor</sub> | EX  | MEM | WB |  |

## Forwarding

☐ The problem with data hazards, introduced by this sequence of instructions can be solved with a simple hardware technique called **forwarding**.

|     |          | Clock cycle number |    |                   |                   |     |     |    |
|-----|----------|--------------------|----|-------------------|-------------------|-----|-----|----|
|     |          | 1                  | 2  | 3                 | 4                 | 5   | 6   | 7  |
| ADD | R1,R2,R3 | IF                 | ID | EX                | MEM               | WB  |     |    |
| SUB | R4,R5,R1 |                    | IF | ID <sub>sub</sub> | EX                | MEM | WB  |    |
| AND | R6,R1,R7 |                    |    | IF                | ID <sub>and</sub> | EX  | MEM | WB |

### Forwarding Architecture

![](9a19da4f7fccb96a934411c0bb5a386d_img.jpg)

Diagram illustrating the Forwarding Architecture of a processor pipeline. The pipeline stages shown are Fetch, Instruction Decode, Register Read, ALU, and Register Write.

**Fetch Stage:** Fetches instructions from the I-cache. The PC register is updated by adding 4 to the previous PC value. The PC register also receives input from the Register Write stage (PC + 8).

**Instruction Decode Stage:** Decodes the fetched instruction, extracting immediate fields and the destination register  $r_{15}$ .

**Register Read Stage:** Reads data from the register file. The ALU output is fed back to the register file input via the **forwarding paths** (highlighted in red).

**ALU Stage:** Performs arithmetic and logical operations. The ALU input includes immediate fields, register shift results, and results from the forwarding paths. The ALU output is used for register write and also feeds back to the register file input via the forwarding paths.

**Register Write Stage:** Writes data back to the register file. The write-back path is labeled "write-back".

**Memory Access:** The D-cache handles load/store operations. The load/store address is generated by combining the base address (B, BL, MOV, pc, SUBS) with an offset (LDM/STM, +4, post-index, pre-index, shift, reg shift). The D-cache output is used for register write and also feeds back to the register file input via the forwarding paths.

**PC Update:** The PC register is updated by adding 4 to the previous PC value. The PC register also receives input from the Register Write stage (PC + 8).

☐ Forwarding works as follows:

- The ALU result from the EX/MEM register is always **fed back** to the ALU input latches.
- If the forwarding hardware detects that the previous ALU operation has written the register corresponding to the current ALU source for the current ALU operation, **control logic** selects the forwarded result as the ALU input rather than the value read from the register file.

**forwarding paths**

#### Forward Data

|     |          | Clock cycle number |    |                   |                    |                   |     |    |
|-----|----------|--------------------|----|-------------------|--------------------|-------------------|-----|----|
|     |          | 1                  | 2  | 3                 | 4                  | 5                 | 6   | 7  |
| ADD | R1,R2,R3 | IF                 | ID | EX <sub>add</sub> | MEM <sub>add</sub> | WB                |     |    |
| SUB | R4,R5,R1 |                    | IF | ID                | EX <sub>sub</sub>  | MEM               | WB  |    |
| AND | R6,R1,R7 |                    |    | IF                | ID                 | EX <sub>and</sub> | MEM | WB |

- The first forwarding is for value of **R1** from **EX<sub>add</sub>** to **EX<sub>sub</sub>**. The second forwarding is also for value of **R1** from **MEM<sub>add</sub>** to **EX<sub>and</sub>**. This code now can be executed without stalls.
- Forwarding can be generalized to include passing the result directly to the functional unit that requires it: a result is forwarded from the output of one unit to the input of another, rather than just from the result of a unit to the input of the same unit.

#### Without Forward

|     |          | Clock cycle number |    |       |       |                   |                   |     |     |    |
|-----|----------|--------------------|----|-------|-------|-------------------|-------------------|-----|-----|----|
|     |          | 1                  | 2  | 3     | 4     | 5                 | 6                 | 7   | 8   | 9  |
| ADD | R1,R2,R3 | IF                 | ID | EX    | MEM   | WB                |                   |     |     |    |
| SUB | R4,R5,R1 |                    | IF | stall | stall | ID <sub>sub</sub> | EX                | MEM | WB  |    |
| AND | R6,R1,R7 |                    |    | stall | stall | IF                | ID <sub>and</sub> | EX  | MEM | WB |

#### Data forwarding

- Data dependency arises when an instruction needs to use the result of one of its predecessors before the result has returned to the register file => pipeline hazards
- Forwarding paths allow results to be passed between stages as soon as they are available
- 5-stage pipeline requires each of the three source operands to be forwarded from any of the intermediate result registers
- Still one load stall

```
LDR rN, [...]
```

```
ADD r2, r1, rN ; use rN immediately
```

- One stall
- Compiler rescheduling

#### Stalls are required

|     |          | 1  | 2  | 3  | 4                 | 5                 | 6   | 7   | 8  |
|-----|----------|----|----|----|-------------------|-------------------|-----|-----|----|
| LDR | R1,@(R2) | IF | ID | EX | MEM               | WB                |     |     |    |
| SUB | R4,R1,R5 |    | IF | ID | EX <sub>sub</sub> | MEM               | WB  |     |    |
| AND | R6,R1,R7 |    |    | IF | ID                | EX <sub>and</sub> | MEM | WB  |    |
| OR  | R8,R1,R9 |    |    |    | IF                | ID                | EXE | MEM | WB |

☐ The load instruction has a delay or latency that cannot be eliminated by forwarding alone.

#### The Pipeline with one Stall

|     |          | 1  | 2  | 3  | 4     | 5                 | 6   | 7   | 8   | 9  |
|-----|----------|----|----|----|-------|-------------------|-----|-----|-----|----|
| LDR | R1,@(R2) | IF | ID | EX | MEM   | WB                |     |     |     |    |
| SUB | R4,R1,R5 |    | IF | ID | stall | EX <sub>sub</sub> | MEM | WB  |     |    |
| AND | R6,R1,R7 |    |    | IF | stall | ID                | EX  | MEM | WB  |    |
| OR  | R8,R1,R9 |    |    |    | stall | IF                | ID  | EX  | MEM | WB |

☐ The only necessary forwarding is done for R1 from **MEM** to **EX<sub>sub</sub>**.

### LDR Interlock

![](abc0eb594f9d2c0daa0e60df05f2a666_img.jpg)

| Cycle                                                                   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|-------------------------------------------------------------------------|---|---|---|---|---|---|---|---|---|
| Operation                                                               |   |   |   |   |   |   |   |   |   |
| ADD R1, R1, R2                                                          | F | D | E | W |   |   |   |   |   |
| SUB R3, R4, R1                                                          |   | F | D | E | W |   |   |   |   |
| LDR R4, [R7]                                                            |   |   | F | D | E | M | W |   |   |
| ORR R8, R3, R4                                                          |   |   |   | F | D | I | E | W |   |
| AND R6, R3, R1                                                          |   |   |   |   | F | I | D | E | W |
| EOR R3, R1, R2                                                          |   |   |   |   |   | F | D | E | W |
| F - Fetch D - Decode E - Execute I - Interlock M - Memory W - Writeback |   |   |   |   |   |   |   |   |   |

- In this example, it takes 7 clock cycles to execute 6 instructions, CPI of 1.2
- The LDR instruction immediately followed by a data operation using the same register cause an interlock

### Optimal Pipelining

![](20727e57890be6da5692a02d13c0a8ec_img.jpg)

| Cycle                                                                      | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|----------------------------------------------------------------------------|---|---|---|---|---|---|---|---|---|
| Operation                                                                  |   |   |   |   |   |   |   |   |   |
| ADD R1, R1, R2                                                             | F | D | E | W |   |   |   |   |   |
| SUB R3, R4, R1                                                             |   | F | D | E | W |   |   |   |   |
| LDR R4, [R7]                                                               |   |   | F | D | E | M | W |   |   |
| AND R6, R3, R1                                                             |   |   |   | F | D | E | W |   |   |
| ORR R8, R3, R4                                                             |   |   |   |   | F | D | E | W |   |
| EOR R3, R1, R2                                                             |   |   |   |   |   | F | D | E | W |
| F - Fetch D - Decode E - Execute I - Interlock M - Memory<br>W - Writeback |   |   |   |   |   |   |   |   |   |

- In this example, it takes 6 clock cycles to execute 6 instructions, CPI of 1
- The LDR instruction does not cause the pipeline to interlock

#### LDM Interlock (1/2)

![](7119b28e39fa3784606bf8b8f44e4f9d_img.jpg)

| Cycle                                  |               | 1          | 2 | 3           | 4 | 5             | 6  | 7          | 8 | 9             | 10 |
|----------------------------------------|---------------|------------|---|-------------|---|---------------|----|------------|---|---------------|----|
| Operation                              |               |            |   |             |   |               |    |            |   |               |    |
| LDM/LA                                 | R13!, {R0-R3} | F          | D | E           | M | MW            | MW | MW         | W |               |    |
| SUB                                    | R9, R7, R2    |            | F | D           | I | I             | I  | E          |   | W             |    |
| STR                                    | R4, [R9]      |            |   | F           | I | I             | I  | D          | E | M             | W  |
| ORR                                    | R8, R4, R3    |            |   |             |   |               | F  | D          | E |               | W  |
| AND                                    | R6, R3, R1    |            |   |             |   |               |    | F          | D | E             | W  |
| F - Fetch                              |               | D - Decode |   | E - Execute |   | I - Interlock |    | M - Memory |   | W - Writeback |    |
| ME - Simultaneous Memory and Writeback |               |            |   |             |   |               |    |            |   |               |    |

- In this example, it takes 8 clock cycles to execute 5 instructions, CPI of 1.6
- During the LDM there are parallel memory and writeback cycles

#### LDM Interlock (2/2)

![](ec36a1ba48e13289c395fab4a7730bdb_img.jpg)

| Cycle     |              | 1 | 2 | 3 | 4 | 5  | 6  | 7  | 8 | 9 | 10 |
|-----------|--------------|---|---|---|---|----|----|----|---|---|----|
| Operation |              |   |   |   |   |    |    |    |   |   |    |
| LDM LA    | R13, [R0-R3] | F | D | E | M | MW | MW | MW | W |   |    |
| SUB       | R9, R7, R3   |   | F | D | I | I  | I  | I  | E |   |    |
| STR       | R4, [R9]     |   |   | F | I | I  | I  | I  | D | E | M  |
| ORR       | R8, R4, R3   |   |   |   |   |    |    | F  | D | E | W  |
| AND       | R6, R3, R1   |   |   |   |   |    |    |    | F | D | E  |

F - Fetch D - Decode E - Execute I - Interlock M - Memory  
ME - Simultaneous Memory and Writeback W - Writeback

- In this example, it takes 9 clock cycles to execute 5 instructions, CPI of 1.8
- The SUB incurs a further cycle of interlock due to it using the highest specified register in the LDM instruction

## ARM7TDMI Processor Core

- Current low-end ARM core for applications like digital mobile phones
- TDMI
  - **T**: Thumb, 16-bit compressed instruction set
  - **D**: on-chip Debug support, enabling the processor to halt in response to a debug request
  - **M**: enhanced Multiplier, yield a full 64-bit result, high performance
  - **I**: EmbeddedICE hardware
- Von Neumann architecture
- 3-stage pipeline, CPI ~ 1.9

### ARM7TDMI Block Diagram

![](a844248c1fa0a79f187fc9aa111182f7_img.jpg)

Diagram illustrating the ARM7TDMI block diagram, showing the interaction between the Embedded ICE, processor core, bus splitter, and JTAG TAP controller.

**Embedded ICE Inputs:** extern0, extern1,  $\overline{\text{opc}}$ ,  $\overline{\text{r/w}}$ ,  $\overline{\text{mreq}}$ ,  $\overline{\text{trans}}$ , mas[1:0], A[31:0].

**Processor Core Inputs/Outputs:** scan chain 0, scan chain 1, scan chain 2, other signals.

**Bus Splitter Inputs/Outputs:** Din[31:0], Dout[31:0].

**JTAG TAP Controller Inputs:** TCK, TMS, TRST, TDI, TDO.

### ARM7TDMI Core Diagram

![](fae82236e4211f753df5789eb276d3a4_img.jpg)

Diagram illustrating the ARM7TDMI Core structure, showing the interconnection of various functional units.

**Address Generation Path:**

- Address Register receives ALE and ABE signals.
- Address Incrementer receives Address Register output and C signal.
- Address Register output also feeds the Register Bank.

**Register Bank:**

- 31 x 32-bit registers (8 status registers).
- Outputs connect to the 32 x 8 Multiplier and the 32-bit ALU.

**ALU and Data Path:**

- 32-bit ALU receives inputs from the Register Bank and the Barrel Shifter.
- 32 x 8 Multiplier receives inputs from the Register Bank and the Barrel Shifter.
- Barrel Shifter receives inputs from the 32 x 8 Multiplier and the 32-bit ALU.
- 32-bit ALU output connects to the Write Data Register.
- Write Data Register outputs connect to the Instruction Pipeline & Read Data Register & Thumb Instruction Decoder.

**Instruction Pipeline & Read Data Register & Thumb Instruction Decoder:**

- Inputs include the Write Data Register output, the Instruction Decoder & Control Logic output, and the Scan Control output.
- Outputs include the Instruction Decoder & Control Logic output, the Scan Control output, and the D[31:0] output.

**Instruction Decoder & Control Logic:**

- Inputs include the Scan Control output and the Instruction Pipeline & Read Data Register & Thumb Instruction Decoder output.
- Outputs include DBGRQI, BREAKPTI, DBGACK, ECLK, nEXEC, ISYNC, BL[3:0], APE, MCLK, nWAIT, nRW, MAS[1:0], nIRQ, nFIQ, nRESET, ABORT, nTRANS, nMREQ, nOPC, SEQ, LOCK, nCPI, CPA, CPB, nM[4:0], TBE, TBIT, and HIGHZ.

**Write Data Register:**

- Inputs include the 32-bit ALU output, the Instruction Pipeline & Read Data Register & Thumb Instruction Decoder output, and the D[31:0] output.
- Outputs include nENOUT, nENIN, and DBE.

### ARM7TDMI Interface Signals (1/4)

![](03498c9b76f980b32f2dfbb7c2e539d2_img.jpg)

Diagram illustrating the ARM7TDMI core interface signals, categorized into groups:

- **clock control**: mclk, wait, eclk
- **configuration**: bigend
- **interrupts**: irq,  $\bar{irq}$ , isync
- **initialization**: reset, enin,  $\bar{enin}$ , enout,  $\bar{enout}$ , able, ale, ape, dbe, tbe
- **bus control**: busen, highz, busdis, ecapclk, dbgirq, breakpoint, dbgback, exec, extern1, extern0, dbggen, rangeout0, rangeout1, dbgraqi, commrx, commtx
- **debug**: opc, cpi, cpa, cpb
- **coprocessor interface**: Vdd, Vss
- **power**: Vdd, Vss

The core is connected to the following external interfaces:

- **memory interface**: A[31:0], D[31:0], Dout[31:0], Din[31:0], b[3:0],  $\bar{b}$ [3:0],  $\bar{r}$ [w], mas[1:0], mreq, seq, lock
- **MMU interface**: trans, mode[4:0], abort
- **state**: Tbit
- **TAP information**: tapsm[3:0], ir[3:0], tdoen, tck1, tck2, screg[3:0]
- **boundary scan extension**: drivebs, ecapclkbs, icapclkbs, highz, pclkbs, rstclkbs, sdnibs, sdoutbs, shclk2bs, shclk2bs
- **JTAG controls**: TRST, TCK, TMS, TDI, TDO

### ARM7TDMI Interface Signals (2/4)

#### ☐ Clock control

- All state change within the processor are controlled by *mclk*, the memory clock
- Internal clock = *mclk* AND *\wait*
- *eclk* clock output reflects the clock used by the core

#### ☐ Memory interface

- 32-bit address *A*[31:0], bidirectional data bus *D*[31:0], separate data out *Dout*[31:0], data in *Din*[31:0]
- *\mreq* indicates that the memory address will be sequential to that used in the previous cycle

| <i>mreq</i> | <i>seq</i> | Cycle | Use                                             |
|-------------|------------|-------|-------------------------------------------------|
| 0           | 0          | N     | Non-sequential memory access                    |
| 0           | 1          | S     | Sequential memory access                        |
| 1           | 0          | I     | Internal cycle – bus and memory inactive        |
| 1           | 1          | C     | Coprocessor register transfer – memory inactive |

### ARM7TDMI Interface Signals (3/4)

- Lock indicates that the processor should keep the bus to ensure the atomicity of the read and write phase of a SWAP instruction
- \r/w, read or write
- mas[1:0], encode memory access size – byte, half – word or word
- bl[3:0], externally controlled enables on latches on each of the 4 bytes on the data input bus

#### ☐ MMU interface

- \trans (translation control), 0: user mode, 1: privileged mode
- \mode[4:0], bottom 5 bits of the CPSR (inverted)
- Abort, disallow access

#### ☐ State

- T bit, whether the processor is currently executing ARM or Thumb instructions

#### ☐ Configuration

- Bigend, big-endian or little-endian

### ARM7TDMI Interface Signals (4/4)

#### ☐ Interrupt

- \fiq, fast interrupt request, higher priority
- \irq, normal interrupt request
- \isync, allow the interrupt synchronizer to be passed

#### ☐ Initialization

- \reset, starts the processor from a known state, executing from address 00000000<sub>16</sub>

### ☐ ARM7TDMI characteristics

| Process      | 0.35 $\mu$ m | Transistors | 74,209              | MIPS   | 60    |
|--------------|--------------|-------------|---------------------|--------|-------|
| Metal layers | 3            | Core area   | 2.1 mm <sup>2</sup> | Power  | 87 mW |
| Vdd          | 3.3 V        | Clock       | 0 to 66 MHz         | MIPS/W | 690   |

### Memory Access

- The ARM7 is a **Von Neumann**, load/store architecture, i.e.,
  - Only 32 bit data bus for both inst. And data.
  - Only the load/store inst. (and SWP) access memory.
- Memory is addressed as a 32 bit address space
- Data type can be 8 bit **bytes**, 16 bit **half-words** or 32 bit **words**, and may be seen as a **byte line** folded into 4-byte words
- Words must be aligned to 4 byte boundaries, and half-words to 2 byte boundaries.
- Always ensure that memory controller supports all three access sizes

![](673e9e5873f9a4b71bbe7bac2cf6b758_img.jpg)

Diagram illustrating memory access structure.

The diagram shows a vertical memory structure labeled **Byte Line** (addresses 0x13 to 0x1A). Addresses 0x13, 0x14, 0x15, 0x16, 0x17, 0x18, 0x19, 0x1A are shown. Addresses 0x13 through 0x16 are shaded, indicating a 4-byte line.

Below the Byte Line, a grid structure is shown labeled **Memory as words** (addresses 0x00 to 0x10). The grid is organized into 4 rows and 4 columns, representing 4-byte words. Addresses 0x00, 0x04, 0x08, 0x0C, 0x10 are shown on the right side of the grid.

Arrows point from the Byte Line addresses 0x12 and 0x11 down to the Memory as words grid, indicating how byte addresses map to word addresses.

### ARM Memory Interface

- Sequential (S cycle)
  - $(nMREQ, SEQ) = (0, 1)$
  - The ARM core requests a transfer to or from an address which is either the same, or one word or one-half-word greater than the preceding address.
- Non-sequential (N cycle)
  - $(nMREQ, SEQ) = (0, 0)$
  - The ARM core requests a transfer to or from an address which is unrelated to the address used in the preceding address.
- Internal (I cycle)
  - $(nMREQ, SEQ) = (1, 0)$
  - The ARM core does not require a transfer, as it performing an internal function, and no useful prefetching can be performed at the same time
- Coprocessor register transfer (C cycle)
  - $(nMREQ, SEQ) = (1, 1)$
  - The ARM core wished to use the data bus to communicate with a coprocessor, but does no require any action by the memory system.

### Cached ARM7TDMI Macrocells

![](1316cc5a3c69067473f110271212db3b_img.jpg)

Diagram illustrating the Cached ARM7TDMI Macrocell architecture.

The core components are:

- ARM7TDMI (containing EmbeddedICE & JTAG)
- CP15
- MMU
- Inst. & data cache
- Write Buffer
- AMBA Interface

Key signals and data paths:

- JTAG and non-AMBA signals connect to ARM7TDMI and CP15.
- ARM7TDMI connects to MMU.
- MMU handles Virtual Address (to Inst. & data cache) and Physical Address (to AMBA Interface).
- Inst. & data cache connects to MMU and Write Buffer.
- Write Buffer connects to AMBA Interface.
- AMBA Interface outputs AMBA Address and AMBA Data.

#### ☐ ARM710T

- 8K unified write through cache
- Full memory management unit supporting virtual memory
- Write buffer

#### ☐ ARM720T

- As ARM 710T but with WinCE support

#### ☐ ARM 740T

- 8K unified write through cache
- Memory protection unit
- Write buffer

#### ☐ Higher performance than ARM7

- By increasing the clock rate
- By reducing the CPI
  - Higher memory bandwidth, 64-bit wide memory
  - Separate memories for instruction and data accesses

#### ☐ ARM 8 ARM9TDMI ARM10TDMI

### ☐ Core Organization

- The prefetch unit is responsible for fetching instructions from memory and buffering them (exploiting the double bandwidth memory)
- It is also responsible for branch prediction and use static prediction based on the branch prediction (backward: predicted 'taken'; forward: predicted 'not taken')

![](237dbb78d0cad58f4dfc140988f3cd16_img.jpg)

Diagram illustrating the ARM8 Core Organization:

- A **prefetch unit** receives **addresses** from the **memory (double-bandwidth)** and sends **PC instructions** to the **integer unit**.
- The **integer unit** sends **CPinst. CPdata** to the **coprocessor(s)**.
- The **memory (double-bandwidth)** exchanges **read data** with the **integer unit** and **write data** with the **coprocessor(s)**.

### Pipeline Organization

☐ 5-stage, prefetch unit occupies the 1st stage, integer unit occupies the remainder

(1) Instruction prefetch → **Prefetch Unit**

(2) Instruction decode and register read

(3) Execute (shift and ALU)

(4) Data memory access

(5) Write back results

(2), (3), (4), and (5) are grouped by a brace and labeled **Integer Unit**.

#### Integer Unit Organization

![](94796d524bd7e0f31f89a379bae95996_img.jpg)

Diagram illustrating the organization of an Integer Unit, structured as a 5-stage pipeline:

- **Decode Stage:** Inputs are instructions (from coprocessor instructions) and PC+8. The stage includes the **inst. decode** block and **register read** block.
- **Execute Stage:** Inputs are coprocessor data and the output of the register read stage. The stage includes the **multiplier** block and the **ALU/shifter** block.
- **Write Stage:** Inputs are the output of the ALU/shifter block and the output of the multiplier block. The stage includes a **write pipeline** block, a **memory** block, and a **rot/sqn ex** block.
- **Forwarding Paths:** The diagram shows paths for forwarding data between stages.
- **Register Write Stage:** The final stage, which receives the output of the write pipeline and rot/sqn ex blocks.

#### ARM8 Macrocell

![](68ec8ddd77b91c6e59d90ca84ad64f11_img.jpg)

Diagram illustrating the ARM8 Macrocell architecture, showing the interaction between the CPU components and the memory system.

- The central component is the **ARM8 integer unit**, which includes the **prefetch unit** and **PC instructions** (PCinst, CPdata).
- The **prefetch unit** interacts with the **8 Kbyte cache (double-bandwidth)** via **virtual address** and **read data** paths.
- The **ARM8 integer unit** interacts with the **8 Kbyte cache** via **write data** and **CPinst** paths.
- The **ARM8 integer unit** connects to **CP15** (Coproprocessor).
- **CP15** connects to the **MMU** (Memory Management Unit) via **update TLB** and **CPdata** paths.
- The **MMU** connects to the **8 Kbyte cache** via **physical address** and **address buffer** paths.
- The **MMU** connects to the **address buffer** via **address** path.
- The **8 Kbyte cache** connects to the **write buffer** via **copy-back tag** and **copy-back data** paths.
- The **write buffer** connects to the **8 Kbyte cache** via **data in** and **data out** paths.
- A **JTAG** block is shown connected to the **write buffer**.

#### ☐ ARM810

- 8Kbyte unified instruction and data cache
- Copy-back
- Double-bandwidth
- MMU
- Coproprocessor
- Write buffer

### Harvard architecture

- Increases available memory bandwidth
  - Instruction memory interface
  - Data memory interface
- Simultaneous accesses to instruction and data memory can be achieved

### 5-stage pipeline

### Changes implemented to

- Improve CPI to  $\sim 1.5$
- Improve maximum clock frequency

### ARM9TDMI Organization

![](7fdd9eacc17f06e094850c6755b47418_img.jpg)

Diagram illustrating the ARM9TDMI Organization, showing the data path flow:

- **Fetch:** The instruction fetch unit calculates the next PC ( $\text{next pc} = \text{pc} + 4$ ) and fetches the instruction from the I-cache. The instruction is then passed to the I decode unit.
- **Instruction Decode:** The I decode unit outputs the instruction fields (immediate fields) and the register number ( $r15$ ) to the register read unit.
- **Register Read:** The register read unit reads the register value. This value is used for immediate fields and is also passed to the shift unit. The register number ( $r15$ ) is used to calculate the PC for branch instructions ( $\text{pc} + 8$ ).
- **Shift:** The shift unit receives the register value and the immediate fields, and outputs the result to the ALU.
- **ALU:** The ALU receives the shifted register value and the result of the immediate fields. It also receives forwarding paths from the D-cache. The ALU output is used for the load/store address calculation and for the byte replacement unit (byte repl.).
- **Load/Store Address:** The ALU output is used to calculate the load/store address, which is passed to the D-cache.
- **Byte Replacement:** The byte repl. unit receives the ALU output and the data from the D-cache, and outputs the final data to the register write unit.
- **D-cache:** The D-cache receives the load/store address and the data from the byte repl. unit. It also receives forwarding paths from the ALU. The D-cache outputs the data to the byte repl. unit and the register write unit.
- **Register Write:** The register write unit receives the data from the D-cache and the byte repl. unit. It also receives the register number ( $r15$ ) from the I decode unit. The register write unit outputs the updated register value to the register read unit.
- **Branch/Link Instructions:** The B, BL, MOV, and SUBS instructions modify the PC. The PC is updated by the register write unit and the register read unit. The LDR instruction also modifies the PC.

### ARM9TDMI Pipeline Operations (1/2)

![](9857175bc98d86591d24a161fe615f12_img.jpg)

ARM7TDMI: Fetch Decode Execute

| instruction fetch | Thumb decompress | ARM decode | reg read | shift/ALU | reg write |
|-------------------|------------------|------------|----------|-----------|-----------|
|                   |                  |            |          |           |           |

ARM9TDMI: Fetch Decode Execute Memory Write

| instruction fetch | r_read decode | shift/ALU | data memory access | reg write |
|-------------------|---------------|-----------|--------------------|-----------|
|                   |               |           |                    |           |

Not sufficient slack time to translate Thumb instructions into ARM instructions and then decode, instead the hardware decode both ARM and Thumb instructions directly

### ARM9TDMI Pipeline Operations (2/2)

#### ☐ Coprocessor support

- Coprocessors: floating-point, digital signal processing, special-purpose hardware accelerator

#### ☐ On-chip debugger

- Additional features compared to ARM7TDMI
  - Hardware single stepping
  - Breakpoint can be set on exceptions

#### ☐ ARM9TDMI characteristics

| Process      | 0.25 $\mu$ m | Transistors | 110,000           | MIPS   | 220    |
|--------------|--------------|-------------|-------------------|--------|--------|
| Metal layers | 3            | Core area   | 2.1 $\text{mm}^2$ | Power  | 150 mW |
| Vdd          | 2.5 V        | Clock       | 0 to 200 MHz      | MIPS/W | 1500   |

### ARM9TDMI Macrocells (1/2)

![](7e2465b81aed11b2e58575a811424b75_img.jpg)

Diagram illustrating the ARM9TDMI Macrocells architecture.

The core components are:

- Instruction Cache
- Instruction MMU
- CP15
- ARM9TDMI (containing EmbeddedICE & JTAG)
- External Coprocessor Interface
- Data Cache
- Data MMU
- Physical Address Tag
- Write Buffer
- AMBA Interface

Data paths include:

- virtual IA (Instruction Address) from Instruction Cache and Instruction MMU to CP15 and ARM9TDMI.
- virtual DA (Data Address) from ARM9TDMI to Data Cache and Data MMU.
- physical DA (Data Address) from Data MMU to Physical Address Tag and Write Buffer.
- physical IA (Instruction Address) from Instruction MMU to ARM9TDMI.
- AMBA address and AMBA data paths connecting to the AMBA Interface.
- copy-back DA (Data Address) from Write Buffer to Physical Address Tag.

#### ☐ ARM920T

- 2 × 16K caches
- Full memory management unit supporting virtual addressing and memory protection
- Write buffer

### ARM9TDMI Macrocells (2/2)

#### ☐ ARM 940T

- 2 × 4K caches
- Memory protection Unit
- Write buffer

![](6dda36bad0978e272ca0420b0902b73a_img.jpg)

Diagram illustrating the ARM9TDMI Macrocell architecture (2/2).

The core components are:

- ARM9TDMI (containing Embedded ICE & JTAG)
- Protection Unit
- AMBA interface
- Write buffer
- Instruction cache
- Data cache
- External coprocessor interface

Data flow:

- Instruction cache provides instructions to the ARM9TDMI.
- ARM9TDMI provides I address to the AMBA interface.
- ARM9TDMI provides data address and data to the data cache.
- ARM9TDMI provides data address and data to the write buffer.
- Write buffer provides AMBA address and AMBA data to the AMBA interface.
- AMBA interface provides AMBA address and AMBA data to the ARM9TDMI.
- ARM9TDMI provides instructions to the external coprocessor interface.
- External coprocessor interface provides instructions to the ARM9TDMI.
- ARM9TDMI provides data address and data to the Protection Unit.
- Protection Unit provides data address and data to the ARM9TDMI.

### ARM9E-S Family Overview

- ARM9E-S is based on an ARM9TDMI with the following extensions:
  - Single cycle  $32 \times 6$  multiplier implementation
  - EmbeddedICE logic RT
  - Improved ARM/Thumb interworking
  - New  $32 \times 16$  and  $16 \times 16$  multiply instructions
  - New count leading zero instruction
  - New saturated math instructions

Architecture v5TE

- ARM946E-S
  - ARM9E-S core
  - Instruction and data caches, selectable sizes
  - Instruction and data RAMs, selectable sizes
  - Protection unit
  - AHB bus interface

### ARM10TDMI (1/2)

- Current high-end ARM processor core
- Performance on the same IC process

ARM10TDMI  $\leftarrow_{\times 2}$  ARM9TDMI  $\leftarrow_{\times 2}$  ARM7TDMI

- 300MHz, 0.25 $\mu$ m CMOS
- Increase clock rate

### ARM10TDMI

![](810e9c03f216ccb41879979badc63a3f_img.jpg)

| branch prediction |        |                | addr. calc.        | data memory access      | data write |
|-------------------|--------|----------------|--------------------|-------------------------|------------|
| instruction fetch | decode | r. read decode | shift/ALU multiply | multiplier partials add | reg write  |
| Fetch             | Issue  | Decode         | Execute            | Memory                  | Write      |

#### ☐ Reduce CPI

- Branch prediction
- Non-blocking load and store execution
- 64-bit data memory → transfer 2 registers in each cycle

### ARM1020T Overview

- Architecture v5T
  - ARM1020E will be v5TE
- CPI ~ 1.3
- 6-stage pipeline
- Static branch prediction
- 32KB instruction and 32KB data caches
  - 'hit under miss' support
- 64 bits per cycle LDM/STM operations
- EmbeddedICE Logic RT-II
- Support for new VFPv1 architecture
- ARM10200 test chip
  - ARM1020T
  - VFP10
  - SDRAM memory interface
  - PLL

### Memory Hierarchy

### Memory Size and Speed

![](03afcee7dbcfc0af9eae2f7bf5eb6712_img.jpg)

Memory Hierarchy Diagram:

Memory types (top to bottom): registers, On-chip cache memory, 2nd-level off chip cache, Main memory, Hard disk.

Memory characteristics (left to right):

- Small capacity
- Fast Access time
- Expensive Cost
- Large capacity
- Slow Access time
- Cheap Cost

### Caches (1/2)

- A cache memory is a small, very fast memory that retains copies of recently used memory values.
- It usually implemented on the same chip as the processor.
- Caches work because programs normally display the property of **locality**, which means that at any particular time they tend to execute the same instruction many times on the same areas of data.
- An access to an item which is in the cache is called a **hit**, and an access to an item which is not in the cache is a **miss**.

### Caches (2/2)

- A processor can have one of the following two organizations:
  - A unified cache
    - This is a single cache for both instructions and data
  - Separate instruction and data caches
    - This organization is sometimes called a **modified Harvard** architectures

### Unified instruction and data cache

![](9fe11419dec507724d0362eb31c7b217_img.jpg)

Diagram illustrating a Unified Instruction and Data Cache architecture.

The **processor** contains **registers** and communicates with the **cache** and **memory**.

The **cache** contains **copies of instructions** and **copies of data**.

The **memory** contains **instructions** and **data**.

Addressing and data flow:

- The processor sends an **address** to the cache.
- The cache sends **instructions and data** back to the processor.
- The cache sends an **address** to the memory.
- The memory sends **instructions and data** back to the cache.

Address ranges shown on the right side:

- FF..FF<sub>16</sub> (Top address range)
- 00..00<sub>16</sub> (Bottom address range)

### Separate data and instruction caches

![](5000e9028ee2990f6242b2c0a952010d_img.jpg)

Diagram illustrating a separate data and instruction cache architecture.

The system consists of a **processor**, two **caches** (one for instructions, one for data), and **memory**.

**Instruction Cache:**

- Contains **copies of instructions**.
- Connects to **memory** (address range  $FF..FF_{16}$ ) for instructions.
- Provides **instructions** to the **processor**.

**Data Cache:**

- Contains **copies of data**.
- Connects to **memory** (address range  $00..00_{16}$ ) for data.
- Provides **data** to the **processor**.

**Processor:**

- Contains **registers**.
- Provides **address** to both the **Instruction Cache** and the **Data Cache**.
- Provides **instructions** to the **Instruction Cache**.
- Provides **data** to the **Data Cache**.

**Memory:**

- Contains **instructions** (upper section, address range  $FF..FF_{16}$ ) and **data** (lower section, address range  $00..00_{16}$ ).
- Connects bidirectionally with both the **Instruction Cache** and the **Data Cache**.

#### The direct-mapped cache

![](c3a537b0b6eced7fb3f46a5d4c19b62e_img.jpg)

Diagram illustrating the structure of a direct-mapped cache. The address input is split into tag and index fields. The tag field is fed into a decoder, which outputs to a tag RAM. The index field is used to select a specific line within the data RAM. The tag RAM output is compared against the tag field. If the comparison is successful (hit), the data RAM output is selected by a multiplexer (mux) to produce the final data output.

- The index address bits are used to access the cache entry
- The top address bit are then compared with the stored tag
- If they are equal, the item is in the cache
- The lowest address bit can be used to access the desired item within the line.

###### Example

![](e91d950121dbb814d5c91603c7cd146e_img.jpg)

Diagram illustrating a set-associative cache organization.

The address is decomposed into three fields: tag (19 bits), index (9 bits), and line (4 bits).

The index field selects one of the 512 lines within the data RAM. The tag field is used to compare with the tag stored in the tag RAM to determine a cache hit.

The data RAM is organized into 512 lines, each containing 16 bytes of data.

The output of the comparison unit is 'hit' or 'miss'. If a hit occurs, the data is read from the selected line of the data RAM via a multiplexer (mux) to produce the final 'data' output.

- The 8Kbytes of data in 16-byte lines. There would therefore be 512 lines
- A 32-bit address:
  - 4 bits to address bytes within the line
  - 9 bits to select the line
  - 19-bit tag

#### The set-associative cache

![](839caaa69e77dd042dd8910e8d294d01_img.jpg)

Diagram illustrating a 2-way set-associative cache organization. The address input is split into tag and index fields. The index field is used by a decoder to select one of two sets of tag RAM and data RAM. Each set consists of a tag RAM and a data RAM. The tag RAM outputs are compared against the incoming tag. The comparison results are ANDed to determine a hit. The hit signal controls a multiplexer (MUX) that selects data from the corresponding data RAMs.

- A 2-way set-associative cache
- This form of cache is effectively two direct-mapped caches operating in parallel.

###### Example

![](a7d6560ff54237234261b647f30ec25c_img.jpg)

Diagram illustrating a 2-way set-associative cache organization.

The address is divided into three fields: tag (20 bits), index (8 bits), and line (4 bits).

The cache consists of two sets, each containing 256 lines (indicated by the bracket labeled "256 lines").

Each set contains a tag RAM and a data RAM. The tag RAM output is fed into a compare unit. The output of the compare unit is used to determine a hit/miss signal, which controls a multiplexer (MUX) that selects data from the data RAM.

The data output of the MUX is the final data output.

- The 8Kbytes of data in 16-byte lines. There would therefore be 256 lines in each half of the cache
- A 32-bit address:
  - 4 bits to address bytes within the line
  - 8 bits to select the line
  - 20-bit tag

#### Fully associative cache

![](bc53843127b23a7d84a6184c283d3361_img.jpg)

Diagram illustrating a Fully Associative Cache structure.

An address input is split into a tag and a data RAM index. The tag is fed into a tag CAM (Content Addressed Memory). The CAM output is compared against the data RAM index to determine a hit or miss. If a hit occurs, the data is retrieved from the data RAM and output via a multiplexer (mux) to the data output.

- A **CAM** (Content Addressed Memory) cell is a RAM cell with an inbuilt comparator, so a CAM based tag store can perform a parallel search to locate an address in any location
- The address bits are compared with the stored tag
- If they are equal, the item is in the cache
- The lowest address bit can be used to access the desired item within the line.

###### Example

![](750677d35a0db0f1a6d44ede4e11d347_img.jpg)

Diagram illustrating a set-associative cache organization.

The address input is split into a 28-bit tag and a 4-bit index (line number).

The 4-bit index selects one of 256 lines within the data RAM I.

The data RAM I output is fed into a multiplexer (mux), which outputs the final data.

The tag is input to a tag CAM (Content Addressable Memory).

The tag CAM output indicates a 'hit' or 'miss'.

- The 8Kbytes of data in 16-byte lines. There would therefore be 512 lines
- A 32-bit address:
  - 4 bits to address bytes within the line
  - 28-bit tag

## Write Strategies

### ☐ Write-through

- All write operations are passed to main memory

### ☐ Write-through with buffered write

- All write operations are still passed to main memory and the cache updated as appropriate, but instead of slowing the processor down to main memory speed the write address and data are stored in a **write buffer** which can accept the write information at high speed.

### ☐ Copy-back (write-back)

- No kept coherent with main memory

## Software Development

### ARM Tools

![](14294c70b5a0effb6bdaf09c46bbdc9f_img.jpg)

Diagram illustrating the ARM development toolchain and environment:

- C source and C libraries feed into the C compiler.
- C compiler and asm source feed into the assembler.
- C compiler and assembler output .aof (ARM object format).
- linker takes .aof and object libraries as input.
- linker outputs .aif (ARM image format) and debug.
- system model feeds into the ARMulator.
- ARMulator and ARMsd feed into the development board.

aof: ARM object format

aif: ARM image format

- ARM software development – ADS
- ARM system development – ICE and trace
- ARM-based SoC development – modeling, tools, design flow

### ARM Development Suite (ADS), ARM Software Development Toolkit (SDT) (1/3)

![SOC Consortium logo](81c2fa4df3adbe409a3d45790bc574cf_img.jpg)

SOC Consortium logo

Develop and debug C/C++ or assembly language program

*armcc* ARM C compiler

*armcpp* ARM C++ compiler

*tcc* Thumb C compiler

*tcpp* Thumb C++ compiler

*armasm* ARM and Thumb assembler

*armlink* ARM linker

*armsd* ARM and Thumb symbolic debugger

### ARM Development Suite (ADS), ARM Software Development Toolkit (SDT) (2/3)

![SOC Consortium logo](a5d51e317448b2a944e3dc28dcc6c4b7_img.jpg)

SOC Consortium logo

- *.aof* ARM object format file
- *.aif* ARM image format file
- The *.aif* file can be built to include the debug tables
  - ARM symbolic debugger, ARMsd
- ARMsd can load, run and debug programs either on hardware such as the ARM development board or using the software emulation of the ARM
- AXD (ARM eXtended Debugger)

- ARM debugger for Windows and Unix with graphics user interface
- Debug C, C++, and assembly language source

#### CodeWarrior IDE

- Project management tool for windows

### ARM Development Suite (ADS), ARM Software Development Toolkit (SDT) (3/3)

![SOC Consortium logo](1a89bc3889e652dc3b181a04e16636f1_img.jpg)

SOC Consortium logo

#### ☐ Utilities

*armprof* ARM profiler

*Flash downloader* download binary images to Flash memory on a development board

### ☐ Supporting software

– *ARMulator* ARM core simulator

- Provide instruction accurate simulation of ARM processors and enable ARM and Thumb executable programs to be run on non-native hardware
- Integrated with the ARM debugger

– *Angle* ARM debug monitor

- Run on target development hardware and enable you to develop and debug applications on ARM-based hardware

### ARM C Compiler

- Compiler is compliant with the ANSI standard for C
- Supported by the appropriate library of functions
- Use ARM Procedure Call Standard, APCS for all external functions
  - For procedure entry and exit
- May produce assembly source output
  - Can be inspected, hand optimized and then assembled sequentially
- Can also produce Thumb codes

### Linker

- Take one or more object files and combine them
- Resolve symbolic references between the object files and extract the object modules from libraries
- Normally the linker includes debug tables in the output file

### ARM Symbolic Debugger

- A front-end interface to debug program running either under emulator (on the ARMulator) or remotely on a ARM development board (via a serial line or through JTAG test interface)
- ARMsd allows an executable program to be loaded into the ARMulator or a development board and run. It allows the setting of
  - Breakpoints, addresses in the code
  - Watchpoints, memory address if accessed as data address
    - Cause exception to halt so that the processor state can be examined

### ARM Emulator (1/2)

- ARMulator is a suite of programs that models the behavior of various ARM processor cores in software on a host system
- It operates at various levels of accuracy
  - Instruction accuracy
  - Cycle accuracy
  - Timing accuracy
    - Instruction count or number of cycles can be measured for a program
    - Performance analysis
- Timing accuracy model is used for cache, memory management unit analysis, and so on

### ARM Emulator (2/2)

- ARMulator supports a C library to allow complete C programs to run on the simulated system
- To run software on ARMulator, through ARM symbolic debugger or ARM GUI debuggers, AXD
- It includes
  - Processor core models which can emulate any ARM core
  - A memory interface which allows the characteristics of the target memory system to be modeled
  - A coprocessor interface that supports custom coprocessor models
  - An OS interface that allows individual system calls to be handled

### ARM Development Board

- A circuit board including an ARM core (e.g. ARM7TDMI), memory component, I/O and electrically programmable devices
- It can support both hardware and software development before the final application-specific hardware is available

## Summary (1/2)

### ☐ ARM7TDMI

- Von Neumann architecture
- 3-stage pipeline
- CPI ~ 1.9

### ☐ ARM9TDMI, ARM9E-S

- Harvard architecture
- 5-stage pipeline
- CPI ~ 1.5

### ☐ ARM10TDMI

- Harvard architecture
- 6-stage pipeline
- CPI ~ 1.3

## Summary (2/2)

### ☐ Cache

- Direct-mapped cache
- Set-associative cache
- Fully associative cache

### ☐ Software Development

- CodeWarrior
- AXD

## References

[1] [http://twins.ee.nctu.edu.tw/courses/ip\\_core\\_02/index.html](http://twins.ee.nctu.edu.tw/courses/ip_core_02/index.html)

[2] **ARM System-on-Chip Architecture** by S.Furber, Addison  
Wesley Longman: ISBN 0-201-67519-6.

[3] [www.arm.com](http://www.arm.com)