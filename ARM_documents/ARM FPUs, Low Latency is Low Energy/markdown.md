

# ARM FPUs: Low Latency is Low Energy

David Lutz

## Every computer has a power budget

| device             | simple phone | smartphone | tablet | laptop | supercomputer |
|--------------------|--------------|------------|--------|--------|---------------|
| total power budget | 3W           | 5W         | 15W    | 35W    | 20 megawatts  |
| screen size        | 3"           | 4-5"       | 10"    | 13"    |               |

- Power limited by heat generated
- Performance increases over time, but power budget does not
- Active research area: how to get more performance within a power budget

## Low Latency is Low Energy

![](d9d706121d1c4ba9ad2c793746382361_img.jpg)

A bar chart illustrating the relationship between Power and Time, and the resulting Energy. The vertical axis is labeled "Power" and the horizontal axis is labeled "Time". A yellow rectangular area, labeled "Energy", represents the total energy consumption, which is the product of Power and Time. A green vertical bar, representing Power, is shown adjacent to the yellow area, indicating that Power is the rate of energy consumption.

- Energy = Power \* Time
- Datapaths consume little power on out-of-order cores
  - Current ARM FPU's consume about 7% of "big" core power running DAXPY
- Decreasing latency can decrease time
- Energy savings is not just datapath energy

### Typical 5-cycle FMA

- all 3 operands needed at the beginning of the operation
- sum of 4 products:  $s = a*x + b*y + c*z + d*w$

|            | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 |
|------------|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|----|----|----|----|----|
| fmul s,a,x | M | M | M | M | M |   |   |   |   |    |    |    |    |    |    |    |    |    |    |    |
| fma s,b,y  |   |   |   |   |   | F | F | F | F | F  |    |    |    |    |    |    |    |    |    |    |
| fma s,c,z  |   |   |   |   |   |   |   |   |   |    | F  | F  | F  | F  | F  |    |    |    |    |    |
| fma s,d,w  |   |   |   |   |   |   |   |   |   |    |    |    |    |    |    | F  | F  | F  | F  |    |

### ARM 6-cycle FMA with separate multiply and add

- 3-cycle multiply followed by 3-cycle add
- Note that a single FMA is slower
- sum of 4 products:  $s = a*x + b*y + c*z + d*w$

|            | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | 11 | 12 | 13 |
|------------|----|----|----|----|----|----|----|----|----|----|----|----|----|
| fmul s,a,x | M1 | M2 | M3 |    |    |    |    |    |    |    |    |    |    |
| fma s,b,y  |    | M1 | M2 | M3 | A1 | A2 | A3 |    |    |    |    |    |    |
| fma s,c,z  |    |    |    |    | M1 | M2 | M3 | A1 | A2 | A3 |    |    |    |
| fma s,d,w  |    |    |    |    |    |    |    | M1 | M2 | M3 | A1 | A2 | A3 |

### 3-cycle multiplier

- V1
  - normalization
  - Booth encoding
- V2
  - Booth mux
  - 18:2 reduction
  - compute shift, round, mask
- V3
  - add and round (2)
  - subnormal shift
  - select

![](55d2bfe1c3d04e86df8d7a104d802172_img.jpg)

Diagram illustrating the 3-cycle multiplier pipeline stages (V1, V2, V3) for computing the product  $\text{product}[63:0]$ .

**V1 (Normalization and Booth Encoding):**

- Inputs  $\text{opa}[63:0]$  and  $\text{opb}[63:0]$  are normalized.
- Normalization checks ( $\text{CLZ siga}$ ,  $\text{CLZ sigb}$ ) and left shifts (0-63 bit left shift) are applied to the normalized sigmas.
- The normalized sigmas are processed by a Booth 8 mux, along with  $\text{BM}[17:0]$ , to generate the computed exponent.
- Booth encoding is performed using a radix 8 Booth encoder on the normalized sigmas.

**V2 (18:2 Reduction and Shift/round/Mask Generation):**

- The Booth encoded results are processed by 18-to-2 compressors (3:2 compressors).
- The compressed results are used to generate the shift, round, and mask values.
- The compressed results are also used to determine the overflow status ( $\text{ovfi}$ ).

**V3 (Addition and Rounding):**

- The compressed results are used to calculate the sum ( $\text{sum}[105:0]$ ) and the sum of the last bits ( $\text{sum}[105:0]$ ).
- The sum is processed by 3:2 compressors to generate the rounded sum.
- The rounded sum is combined with the last bit and flags to determine the final rounded sum and the sign/overflow status.
- The final result is combined with special cases to produce  $\text{sum}[105:0]$  and  $\text{special}$ , which is then used to calculate the product  $\text{product}[63:0]$ .

### 3-cycle adder

- V1
  - compare/swap
  - 4xLZA
  - compute exponent
  - compute lshift, rshift
- V2
  - Left and right shift
  - select
  - 3:2 for rounding
- V3
  - add and round
  - select

![](c0843c6d138705289960d9f53a6e72a1_img.jpg)

Diagram illustrating the 3-cycle adder pipeline structure, divided into V1, V2, and V3 stages.

**V1 Stage:**

- Inputs:  $opa\_sources[63:0]$  and  $opb\_sources[116:0]$ .
- Components:  $opa\_mux$ ,  $opb\_mux$ ,  $comparison$ ,  $LZAs/exp\_compares$ ,  $4:1$  multiplexer,  $op\_ops$ .
- Outputs:  $larger, shift1$  and  $op\_ops$ .

**V2 Stage:**

- Inputs:  $lshift[6:0]$ ,  $op1[106:0]$ ,  $ops[106:0]$ ,  $exp\_diff$ .
- Components:  $left\_shift$  (two instances),  $right\_shift$ ,  $3:1$  multiplexer (two instances),  $round1$ ,  $round0$ ,  $Is, rs, subnormal$ .
- Outputs:  $3:1$  multiplexer outputs,  $3:2$  FA inputs.

**V3 Stage:**

- Inputs:  $c1[107:0]$ ,  $s1[107:0]$ ,  $c0[107:0]$ ,  $s0[107:0]$ .
- Components:  $add1$ ,  $add0$ ,  $specials$ ,  $overflow, overflow2$ ,  $special$ ,  $4:1$  multiplexer,  $sum[63:0]$ .
- Outputs:  $sum[63:0]$ .

## Faster FPU = higher performance and lower energy

- Suppose lower latency FPU is 15% faster than higher latency FPU
- Takes  $1/1.15 = .87$  of the time to complete SpecFP

|            | time | FP power | non-FP power | energy = time * power             |
|------------|------|----------|--------------|-----------------------------------|
| Slower FPU | 1    | 7        | 93           | $1.0 \times (7+93) = 100$         |
| Faster FPU | 0.87 | p        | 93           | $.87 \times (p+93) = .87p + 80.9$ |

- New scheme lower energy if  $100 > .87p + 80.9$ 
  - if  $p < 22$
  - if  $p < 3$  times slower FPU power

### Faster FPU can lead to lower area

- Fewer (flip)flops vs. more logic
- Where is the area going?

![A diagram showing a large green area, likely representing the overall chip area. In the top left corner, there is a small, colorful inset showing four labeled blocks: ufmulj, ufmulj, ufmulj, and ufmulj. These labels likely represent specific functional units or logic blocks within the chip.](91be14371a97fb5ce9eeb29ae18d07c3_img.jpg)

A diagram showing a large green area, likely representing the overall chip area. In the top left corner, there is a small, colorful inset showing four labeled blocks: ufmulj, ufmulj, ufmulj, and ufmulj. These labels likely represent specific functional units or logic blocks within the chip.

## Strategy for out-of-order cores

- Do the execution as quickly as possible to save energy
- Be suspicious of slower execution, e.g.
  - double pumped multipliers
  - slower dividers
- Execution units are where you want to spend power

## Conclusions

- Low execution latency has an outsized effect on performance
- Low latency can improve area
- Low latency is low energy