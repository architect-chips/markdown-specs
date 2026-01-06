

arm

SVE Deep Dive

arm

# Arm C Language Extensions for SVE

Compiler Intrinsics for SVE

## Arm C Language Extensions

Intrinsics and other features for supporting Arm features in C and C++

- ACLE extends C/C++ with Arm-specific features
  - Predefined macros: `__ARM_ARCH_ISA_A64`, `__ARM_BIG_ENDIAN`, etc.
  - Intrinsic functions: `__clz(uint32_t x)`, `__cls(uint32_t x)`, etc.
  - Data types: SVE, NEON and FP16 data types
- **ACLE for SVE** enables VLA programming with ACLE
  - Nearly one intrinsic per SVE instruction
  - Data types to represent the size-less vectors used for SVE intrinsics
- Intended for users that...
  - Want to hand-tune SVE code
  - Want to adapt or hand-optimize applications and libraries
  - Need low-level access to Arm targets

## How to useACLE

### - Include the headers you need

- arm\_acle.h → for core ACLE
- arm\_fp16.h → to add scalar FP16 arithmetic
- arm\_neon.h → to add NEON intrinsics and data types
- arm\_sve.h → to add SVE intrinsics and data types

### - Each of those require certain features at the compilation target

- arm\_fp16.h → Your target platform needs to support FP16 (-march=armv8-a+fp16)
- arm\_neon.h → Your target platform needs to support NEON (-march=armv8-a+simd)
- arm\_sve.h → Your target platform needs to support SVE (-march=armv8-a+sve)

## SVEACLE

### SVE Arm C Language Extensions – aka *C intrinsics*

```
#include <arm_sve.h>
```

- VLA Data types:
  - `svfloat64_t`, `svfloat16_t`,  
    `svuint32_t`,...
- Predication:
  - Merging: `_m`
  - Zeroing: `_z`
  - Don't care: `_x`
  - Predicate type: `svbool_t`
- Use *C11 generics* for function overloading.
- Intrinsics are **not 1-1** with the ISA.

## Examples

```
svfloat32_t
svadd[_n_f32]_z (svbool_t pg,
                 svfloat32_t op1,
                 float32_t op2);
```

```
svfloat16_t
svsqrt_m(svfloat16_t inactive,
         svbool_t pg,
         svfloat16_t op)
```

### Vectorizing a scalar loop withACLE

```
a[i] = 2.0 * a[i];
```

#### Original Code

```
for (int i=0; i < N; ++i) {  
    a[i] = 2.0 * a[i];  
}
```

#### 128-bit NEON vectorization withACLE

```
int i;  
  
// vector loop  
for (i=0; (i<N-3) && (N&~3); i+=4) {  
    float32x4_t va = vld1q_f32(&a[i]);  
    va = vmulq_n_f32(va, 2.0);  
    vst1q_f32(&a[i], va)  
}  
  
// drain loop  
for (; i < N; ++i)  
    a[i] = 2.0 * a[i];
```

This is NEON,  
not SVE!

### Vectorizing a scalar loop withACLE

```
a[i] = 2.0 * a[i];
```

```
for (int i=0; i < N; ++i) {  
    a[i] = 2.0 * a[i];  
}
```

#### SVE vectorization

```
for (int i = 0; i < N; i += ????????) svcntw())  
{  
    svbool_t Pg = svwhilelt_b32(i, N);  
    svfloat32_t va = svld1(Pg, &a[i]);  
    va = svmul_x(Pg, va, 2.0);  
    svst1(Pg, &a[i], va);  
}
```

#### 128-bit NEON vectorization

```
int i;  
  
// vector loop  
for (i=0; (i<N-3) && (N&~3); i+=4) {  
    float32x4_t va = vld1q_f32(&a[i]);  
    va = vmulq_n_f32(va, 2.0);  
    vst1q_f32(&a[i], va)  
}  
  
// drain loop  
for (; i < N; ++i)  
    a[i] = 2.0 * a[i];
```

### Vectorizing a scalar loop withACLE

```
a[i] = 2.0 * a[i]
```

```
for (int i=0; i < N; ++i) {  
    a[i] = 2.0 * a[i];  
}
```

#### SVE vectorization

```
for (int i = 0; i < N; i += ????????) svcntw())  
{  
    svbool_t Pg = svwhilelt_b32(i, N);  
    svfloat32_t va = svld1(Pg, &a[i]);  
    va = svmul_x(Pg, va, 2.0);  
    svst1(Pg, &a[i], va);  
}
```

### SVE vectorization with fewer branches

```
svbool_t all = svptrue_b32();  
svbool_t Pg;  
for (int i=0;  
    svptest_first(all,  
        Pg=svwhilelt_b32(i, N));  
    i += svcntw())  
{  
    svfloat32_t va = svld1(Pg, &a[i]);  
    va = svmul_x(Pg, va, 2.0);  
    svst1(Pg, &a[i], va);  
}
```

## ACLE for SVE Cheat Sheet

### Vector types

- `sv<datatype><datasize>_t`
  - `svfloat32_t`
  - `svint8_t`
  - `svuint16_t`

### Predicate types

- `svbool_t`

### Functions

- `svbase[disambiguator][type0][type1]...[predication]`
- base is the lower-case name of an SVE instruction
- *disambiguator* distinguishes between different forms of a function
- *typeN* lists the types of vectors and predicates
- *predication* describes the inactive elements in the result of a predicated operation

```
svfloat64_t svld1_f64(svbool_t pg, const float64_t *base)svbool_t svwhilelt_b8(int64_t op1, int64_t op2)svuint32_t svmla_u32_z(svbool_t pg, svuint32_t op1, svuint32_t op2, svuint32_t op3)svuint32_t svmla_u32_m(svbool_t pg, svuint32_t op1, svuint32_t op2, svuint32_t op3)
```

## 02ACLE/01\_vecadd

See README.md for details

#### GCC 9.3

```
gcc --version
```

```
gcc (GCC) 9.3.0
```

```
gcc -fopt-info-all-vec -Ofast \  
-mcpu=native vec_add_acle.c
```

```
vec_add_acle.c:22:10: fatal error: arm_sve.h: No such file or  
directory
```

```
22 | #include <arm_sve.h>
```

```
| ^~~~~~~~~~~
```

```
compilation terminated.
```

#### GCC 11

```
gcc --version
```

```
gcc (GCC) 11.0.0 20201025 (experimental)
```

```
gcc -fopt-info-all-vec -Ofast \  
-mcpu=native vec_add.c
```

```
# No errors
```

### 02\_ACLE/01\_vecadd

See README.md for details

#### vec\_add\_acle\_arm.exe

```
whilelo p0.s, x8, x9
ld1w { z0.s }, p0/z, [x1, x8, Isl #2]
ld1w { z1.s }, p0/z, [x2, x8, Isl #2]
fadd z0.s, p0/m, z0.s, z1.s
st1w { z0.s }, p0, [x0, x8, Isl #2]
incw x8
cmp x8, #256, Isl #12
b.lo #-28 <vec_svadd_m+0x20>
ret
```

#### vec\_add\_arm.exe

```
whilelo p0.s, xzr, x9
b #24 <vec_add+0x60>
... (six nop instructions)
ld1w { z0.s }, p0/z, [x1, x8, Isl #2]
ld1w { z1.s }, p0/z, [x2, x8, Isl #2]
fadd z0.s, z1.s, z0.s
st1w { z0.s }, p0, [x0, x8, Isl #2]
incw x8
whilelo p0.s, x8, x9
b.mi #-24 <vec_add+0x60>
b #64 <vec_add+0xbc>
mov x8, xzr
b #28 <vec_add+0xa0>
```

arm

Working with  
SVE Instructions

### SAXPY

```
subroutine saxpy(x,y,a,n)
real*4 x(n),y(n),a
do i = 1,n
    y(i) = a*x(i) + y(i)
enddo
```

### Key Operations

- whilelt constructs a **predicate** (p0) to dynamically map vector operations to vector data
- incw increments a scalar register (x4) by the number of float elements that fit in a vector register
- No drain loop! Predication handles the remainder

#### Scalar [-march=armv8-a]

```
// x0 = &x[0], x1 = &y[0], x2 = &a, x3 = &n
saxpy_:
    ldrsw x3, [x3] // x3=*n
    mov x4, #0 // x4=i=0
    ldr s0, [x2] // d0=*a

b .latch

.loop:
    ldr s1, [x0,x4,1s1 2] // s1=x[i]
    ldr s2, [x1,x4,1s1 2] // s2=y[i]
    fmadd s2, s1, s0, s2 // s2+=x[i]*a
    str s2, [x1,x4,1s1 2] // y[i]=s2

add x4, x4, #1 // i+=1

.latch:
    cmp x4, x3 // i < n
    b.lt .loop // more to do?
    ret
```

#### SVE [-march=armv8-a+sve]

```
// x0 = &x[0], x1 = &y[0], x2 = &a, x3 = &n
saxpy_:
    ldrsw x3, [x3] // x3=*n
    mov x4, #0 // x4=i=0

whilelt p0.s, x4, x3 // p0=while(i++<n)
    ld1rw z0.s, p0/z, [x2] // p0:z0=bcast(*a)

.loop:
    ld1w z1.s, p0/z, [x0,x4,1s1 2] // p0:z1=x[i]
    ld1w z2.s, p0/z, [x1,x4,1s1 2] // p0:z2=y[i]
    fm1a z2.s, p0/m, z1.s, z0.s // p0?z2+=x[i]*a
    st1w z2.s, p0, [x1,x4,1s1 2] // p0?y[i]=z2

incw x4 // i+=(VL/32)

.latch:
    whilelt p0.s, x4, x3 // p0=while(i++<n)
    b.first .loop // more to do?
    ret
```

#### How do you count by vector width?

No need for multi-versioning: one increment for all vector sizes

```
ld1w z1.s, p0/z, [x0,x4,ls1 2] // p0:z1=x[i]
ld1w z2.s, p0/z, [x1,x4,ls1 2] // p0:z2=y[i]
fmla z2.s, p0/m, z1.s, z0.s // p0?z2+=x[i]*a
st1w z2.s, p0, [x1,x4,ls1 2] // p0?y[i]=z2
incw x4 // i+=(VL/32)
```

“Increment x4 by the number of 32-bit lanes (w) that fit in a VL.”

### VLA Increment and Count

```
incb x0, mul3, mul1 #2      x0 += 2 x (largest mul3 <= VL.b)
incd z0.d, pow2             each lane += largest pow2 <= VL.d
incp x0, p0.s               x0 += # active lanes
incp z0.h, p0               each vector lane += # active lanes of p

cntw x0                     x0 = VL.s
cntp x0, p0, p1.s.          x0 = # active lanes of (p0 && p1.s)
```

### Predicates: Active Lanes vs Inactive Lanes

Predicate registers track lane activity

- 16 predicate registers (P0-P15)
- 1 predicate bit per 8 vector bits (lowest predicate bit per lane is significant)
- On **load**, active elements update the destination
- On **store**, inactive lanes leave destination unchanged (p0/m) or set to 0's (p0/z)

![](cbc4516eb885829fe8c9dabc0946dcbe_img.jpg)

p0 . d

| 255 | 192 191 |     | 128 127 |     | 64 63 |     | 0 |
|-----|---------|-----|---------|-----|-------|-----|---|
|     |         | 64b |         | 64b |       | 64b |   |
|     |         | I   | I       |     | I     |     | I |
| 31  | 24 23   |     | 16 15   |     | 8 7   |     | 0 |
|     |         | 32b |         | 32b |       | 32b |   |
|     |         | 0   | 0       | 0   | I     | I   | I |

p0 . s

| 255 | 192 191 |     | 128 127 |     | 64 63 |     | 0 |
|-----|---------|-----|---------|-----|-------|-----|---|
|     |         | 64b |         | 64b |       | 64b |   |
|     |         | I   | I       |     | I     |     | I |
| 31  | 24 23   |     | 16 15   |     | 8 7   |     | 0 |
|     |         | 32b |         | 32b |       | 32b |   |
|     |         | 0   | 0       | 0   | I     | I   | I |

### Predicate Condition Flags

#### SVE is a *predicate-centric* architecture

- Predicates support complex nested conditions and loops.
- Predicate generation also sets condition flags.
- Reduces vector loop management overhead.

#### Overloading the A64 NZCV condition flags

| Condition Test | A64 Name | SVE Alias | SVE Interpretation                                                  |
|----------------|----------|-----------|---------------------------------------------------------------------|
| Z=1            | EQ       | NONE      | No active elements are true                                         |
| Z=0            | NE       | ANY       | Any active element is true                                          |
| C=1            | CS       | NLAST     | Last active element is not true                                     |
| C=0            | CC       | LAST      | Last active element is true                                         |
| N=1            | MI       | FIRST     | First active element is true                                        |
| N=0            | PL       | NFRST     | First active element is not true                                    |
| C=1 & Z=0      | HI       | PMORE     | More partitions: some active elements are true but not the last one |
| C=0   Z=1      | LS       | PLAST     | Last partition: last active element is true or none are true        |
| N=V            | GE       | TCONT     | Continue scalar loop                                                |
| N!=V           | LT       | TSTOP     | Stop scalar loop                                                    |

#### Initialization when vector length is unknown

- Vectors cannot be initialized from compile-time constant, so...
  - INDEX Zd.S, #1, #4 : Zd = [ 1, 5, 9, 13, 17, 21, 25, 29 ]
- Predicates cannot be initialized from memory, so...
  - PTRUE Pd.S, MUL3 : Pd = [ (T, T, T), (T, T, T), F, F ]
- Vector loop increment and trip count are unknown at compile-time, so...
  - INCD Xi : increment scalar Xi by # of 64b dwords in vector
  - WHILELT Pd.D, Xi, Xe : next iteration predicate Pd = [ while i++ < e ]
- Vectors stores to stack must be dynamically allocated and indexed, so...
  - ADDVL SP, SP, #-4 : decrement stack pointer by (4\*VL)
  - STR Zi, [SP, #3, MUL VL] : store vector Z1 to address (SP+3\*VL)

arm

Horizontal  
Reductions

### SVE includes a rich set of horizontal operations

The operation happens across the lanes of a vector

- Addition, maximum, minimum, bitwise AND, OR, XOR ...

![](9260ae281f6b6470331f4a0f82dbc2b1_img.jpg)

SADDV  $\langle Dd \rangle$ ,  $\langle Pg \rangle$ ,  $\langle Zn.T \rangle$

Zn

| -46 | -12 | 93 | 4 |
|-----|-----|----|---|
|-----|-----|----|---|

Diagram illustrating the horizontal addition operation (SADDV). The input vector Zn is split into two pairs of lanes: (-46, -12) and (93, 4). Each pair is summed horizontally (e.g., -46 + -12 = -58, 93 + 4 = 97). The results of these two horizontal additions are then summed together to produce the final result Dd, which is 39.

Dd 39

### C code without intrinsics

Compile with -march=armv8-a+sve or -mcpu=native if your CPU has SVE

```
double ddot (double *a, double *b, int n){    double sum = 0.0;    for ( int i = 0; i < n; i++ ) {        sum += a[i] * b[i];    }    return sum;}
```

- Accumulates in a scalar
- No horizontal reductions

```
cmp w2, #1b.lt #52 <ddot+0x38>mov w9, w2mov x8, xzrwhile0 p0.d, xzr, x9fmov d0, xzrld1d { z1.d }, p0/z, [x0, x8, lsl #3]ld1d { z2.d }, p0/z, [x1, x8, lsl #3]incd x8fmul z1.d, z1.d, z2.dfadda d0, p0, d0, z1.dwhile0 p0.d, x8, x9b.mi #-24 <ddot+0x18>retfmov d0, xzrret
```

### C code with SVE intrinsics

Vector accumulator; horizontal reduction

```
#include <arm_sve.h>

double ddot (double *a, double *b, int n) {
    svfloat64_t svs = svdup_f64(0.0);
    svbool_t pg;
    svfloat64_t sva, svb, svs;
    for (int i = 0; i < n; i += svcntd()) {
        pg = svwhilelt_b64(i, n);
        sva = svld1_f64(pg, &a[i]);
        svb = svld1_f64(pg, &b[i]);
        svs = svmla_f64_m(pg, svs, sva, svb);
    }
    return svaddv_f64(svptrue_b64(), svs);
}
```

```
cmp w2, #1
b.lt #60 <ddot+0x40>
mov w8, wzr
cntd x9
mov z0.d, #0
whilelt p0.d, w8, w2
sxtw x10, w8
ld1d { z1.d }, p0/z, [x0, x10, ls1 #3]
ld1d { z2.d }, p0/z, [x1, x10, ls1 #3]
add w8, w8, w9
cmp w8, w2
fmla z0.d, p0/m, z1.d, z2.d
b.lt #-28 <ddot+0x14>
ptrue p0.d
faddv d0, p0, z0.d
ret
mov z0.d, #0
ptrue p0.d
faddv d0, p0, z0.d
ret
```

## 02\_ACLE/02\_hreduce

- Most vector instructions operate on a lane-by-lane basis
- SVE includes a rich set of horizontal operations where the operation happens across the lanes of a vector
- Examples of such operations are addition, maximum, minimum, bitwise AND, OR, XOR

![](9b5411fa2d169b66f6185fbf67b49766_img.jpg)

`suint32_t svmaxv(svbool_t pg, svuin32_t op)` op

Diagram illustrating the horizontal maximum operation (hreduce) across four lanes of a vector:

| 46 | 12 | 93 | 4 |
|----|----|----|---|
| 46 | 12 | 93 | 4 |

The lanes are processed pairwise:

- 46 and 12 are compared (max operation), resulting in 46.
- 93 and 4 are compared (max operation), resulting in 93.

The results (46 and 93) are then compared (max operation), resulting in 93.

### 02\_ACLE/02\_hreduce

See README.md for details

Reduce to scalar on every iteration

```
uint32_t max_scalar(uint32_t array[SIZE])
{
    uint32_t max = 0;
    uint32_t vl = svcntw();
    svbool_t p32_all = svptrue_b32();

    for (int i=0; i<SIZE; i+=vl) {
        // load array elements from memory
        svuint32_t vec = svld1(p32_all, &array[i]);
        // get max within vector
        uint32_t vecmax = svmaxv(p32_all, vec);
        if (vecmax > max) {
            max = vecmax;
        }
    }

    return max;
}
```

Reduce to vector; final reduction to scalar

```
uint64_t max(uint64_t array[SIZE])
{
    // initialize max vector with zeros
    svuint64_t max = svdup_u64(0);

    // get number of 64-bit elements in vector
    uint64_t vl = svcntd();

    // all true mask - assuming no partial vector mask needed for simplicity
    svbool_t p64_all = svptrue_b64();

    for (int i=0; i<SIZE; i+=vl) {
        // load array elements from memory
        svuint64_t vec = svld1(p64_all, &array[i]);
        // get max between loaded vector to max
        max = svmax_m(p64_all, max, vec);
    }

    // return max across values within the vector
    return svmaxv(p64_all, max);
}
```

arm

Low-precision  
Dot Product  
with Widening

### 02ACLE/03\_dotprod

- Dot product for low-precision value with widening

```
svint32_t sdot(svint8_t src1, svint8_t src2)
```

```
svint64_t sdot(svint16_t src1, svint16_t src2)
```

![](004a497465710d16d63f436bb330fb42_img.jpg)

Diagram illustrating the dot product operation with widening. The diagram shows three parallel data paths, each consisting of 8 elements (4 orange, 4 green, 4 blue).

src1 (Orange) and src2 (Green) are multiplied element-wise (represented by a circle with a dot inside). The results are summed (represented by a circle with a plus sign inside) to produce the final result, dst (Blue).

### 02\_ACLE/03\_dotprod

#### dotprod\_acle\_arm.exe

```
0000000000400720 dot_product:
400720: e8 03 1f aa      mov      x8, xzr
400724: 00 c0 b8 25       mov      z0.s, #0
400728: e0 e3 18 25       ptrue    p0.b
40072c: 05 00 00 14       b         #20 <dot_product+0x20>
400730: 1f 20 03 d5       nop
400734: 1f 20 03 d5       nop
400738: 1f 20 03 d5       nop
40073c: 1f 20 03 d5       nop
400740: 01 40 08 a4       ldbl     { z1.b }, p0/z, [x0, x8]
400744: 22 40 08 a4       ldbl     { z2.b }, p0/z, [x1, x8]
400748: 28 50 28 04       addv1    x8, x8, #1
40074c: 1f 01 10 71       cmp      w8, #1024
400750: 20 04 82 44       udot     z0.s, z1.b, z2.b
400754: 63 ff ff 54       b.lo     #-20 <dot_product+0x20>
400758: e0 e3 98 25       ptrue    p0.s
40075c: 00 20 81 04       uaddv    d0, p0, z0.s
400760: 00 00 26 1e       fmov     w0, s0
400764: c0 03 5f d6       ret
400768: 06 00 00 14       b         #24 <main>
40076c: 1f 20 03 d5       nop
400770: 1f 20 03 d5       nop
400774: 1f 20 03 d5       nop
400778: 1f 20 03 d5       nop
40077c: 1f 20 00 d5       nop
```

#### dotprod\_arm.exe

```
00000000004006c0 dot_product:
4006c0: 09 80 80 52       mov      w9, #1024
4006c4: e8 03 1f aa       mov      x8, xzr
4006c8: e0 1f 29 25       whileo   p0.b, xzr, x9
4006cc: 00 c0 b8 25       mov      z0.s, #0
4006d0: 04 00 00 14       b         #16 <dot_product+0x20>
4006d4: 1f 20 03 d5       nop
4006d8: 1f 20 03 d5       nop
4006dc: 1f 20 03 d5       nop
4006e0: 01 40 08 a4       ldbl     { z1.b }, p0/z, [x0, x8]
4006e4: 22 40 08 a4       ldbl     { z2.b }, p0/z, [x1, x8]
4006e8: 28 50 28 04       addv1    x8, x8, #1
4006ec: 00 1d 29 25       whileo   p0.b, x8, x9
4006f0: 40 04 81 44       udot     z0.s, z2.b, z1.b
4006f4: 64 ff ff 54       b.mi     #-20 <dot_product+0x20>
4006f8: e0 e3 98 25       ptrue    p0.s
4006fc: 00 20 81 04       uaddv    d0, p0, z0.s
400700: 00 00 66 9e       fmov     x0, d0
400704: c0 03 5f d6       ret
400708: 06 00 00 14       b         #24 <main>
40070c: 1f 20 03 d5       nop
400710: 1f 20 03 d5       nop
400714: 1f 20 03 d5       nop
400718: 1f 20 03 d5       nop
40071c: 1f 20 03 d5       nop
```

arm

### Vector Partition with the First-faulting Register (FFR)

#### Vector Partitioning: when a vector spans a protected region

With VLA, we don't always know what data we may touch

![](20727e57890be6da5692a02d13c0a8ec_img.jpg)

Diagram illustrating vector partitioning across a page boundary. A vector register is shown spanning a boundary. The first element (1) is mandatory, and the second element (2) is speculative. The result of the operation (pred) shows the first two elements as 1, and the last two elements as 0, indicating successful loading of the first two elements and failure for the speculative elements.

- **Software-managed speculative vectorisation**
  - Create sub-vectors (partitions) in response to data and dynamic faults
- **First-fault load allows access to safely cross a page boundary**
  - First element is mandatory but others are a “speculative prefetch”
  - Dedicated FFR predicate register indicates successfully loaded elements
- **Allows uncounted loops with break conditions**
  - Load data using first-fault load
  - Create a *before-fault* partition from FFR
  - Test for break condition
  - Create a *before-break* partition from condition predicate
  - Process data within partition
  - Exit loop if break condition was found.

### Vectorizing strlen

A vector load could result in a segfault if the vector spans protected memory.

#### Source Code

```
int strlen(const char *s) {  
    const char *e = s;  
    while (*e) e++;  
    return e - s;  
}
```

#### Scalar [-march=armv8-a]

```
// x0 = s  
strlen:  
    mov x1, x0 // e=s  
.loop:  
    ldrb x2, [x1], #1 // x2=*e++  
    cbnz x2, .loop // while(*e)  
.done:  
    sub x0, x1, x0 // e-s  
    sub x0, x0, #1 // return e-s-1  
    ret
```

#### Fault-tolerant Speculative Vectorization

- Some loops have dynamic exit conditions that prevent vectorization
  - E.g. the loop breaks on a particular value of the traversed array

| 'S' | 'C' | '2' | '0' | '2' | '0' | '0' |   |   |
|-----|-----|-----|-----|-----|-----|-----|---|---|
| ✓   | ✓   | ✓   | ✓   | ✓   | ✓   | ✓   | X | X |

- The access to unallocated space **does not trap** if it is not the first element
  - Faulting elements are stored in the first-fault register (FFR)
  - Subsequent instructions are predicated using the FFR information to operate only on successful element accesses

### Vectorizing strlen

Partitioning off protected memory

```
int strlen(const char *s) {  
    const char *e = s;  
    while (*e) e++;  
    return e - s;  
}
```

#### SVE [-march=armv8-a+sve]

```
strlen:  
    mov x1, x0 // e=s  
    ptrue p0.b // p0=true  
loop:  
    setffr // ffr=true  
    ldff1b z0.b, p0/z, [x1] // p0:z0=ldff(e)  
    rdffr p1.b, p0/z // p0:p1=ffr  
    cmpeq p2.b, p1/z, z0.b, #0 // p1:p2=(*e==0)  
    brkbs p2.b, p1/z, p2.b // p1:p2=until(*e==0)  
    incp x1, p2.b // e+=popcnt(p2)  
    b.last .loop // last active=>|break  
    sub x0, x1, x0 // return e-s  
    ret
```

#### Scalar [-march=armv8-a]

```
// x0 = s  
strlen:  
    mov x1, x0  
loop:  
    ldrb x2, [x1], #1  
    cbnz x2, .loop  
done:  
    sub x0, x1, x0  
    sub x0, x0, #1  
    ret
```

#### Optimized strlen (SVE)

```
strlen:
    mov      x1, x0
    ptrue    p0.b
.loop:
    setffr
    ldfflb   z0.b, p0/z, [x1]
    rdffr    p1.b, p0/z
    cmpeq    p2.b, p1/z, z0.b, #0
    brkbs    p2.b, p1/z, p2.b
    incp     x1, p2.b
    b.last   .loop
    sub      x0, x1, x0
    ret
```

#### Suboptimal implementation

```
setffr      /* initialize FFR */
ptrue p2.b   /* all ones; loop invariant */
mov x1, 0    /* initialize length */
```

```
0: /* Read a vector's worth of bytes, stopping on first fault. */
    ldfflb   z0.b, p2/z, [x0, x1]
    rdffrs   p0.b, p2/z
    b.nlast  2f
```

```
/* First fault did not fail: the whole vector is valid. Avoid
depending on the contents of FFR beyond the branch. */
    incb     x1, all      /* speculate increment */
    cmpeq    p1.b, p2/z, z0.b, 0  /* loop if no zeros */
    b.none   0b
    decb     x1, all      /* undo speculate */
```

```
1: /* Zero found. Select the bytes before the first and count them. */
    brkb     p0.b, p2/z, p1.b
    incp     x1, p0.b
    mov      x0, x1
    ret
```

```
/* First fault failed: only some of the vector is valid. Perform the
comparison only on the valid bytes. */
2: cmpeq    p1.b, p0/z, z0.b, 0
    b.any    1b
```

```
/* No zero found. Re-init FFR, increment, and loop. */
    setffr
    incp     x1, p0.b
    b 0b
```

### 03\_SVE/D3.1\_sve\_strcmp

See 03\_SVE/SVE-SVE2-programming-examples-REL-01.pdf

```
ptrue p5.b
setffr
mov x5, #0
.L_loop:
ldff1b z0.b, p5/z, [str1, x5]
ldff1b z1.b, p5/z, [str2, x5]
rdffrs p7.b, p5/z
b.nlast .L_fault
incb x5
cmpeq p0.b, p5/z, z0.b, #0
cmpne p1.b, p5/z, z0.b, z1.b
.L_test:
orrs p4.b, p5/z, p0.b, p1.b
b.none .L_loop
.L_fault:
incp x5, p7.b
setffr
cmpeq p0.b, p7/z, z0.b, #0
cmpne p1.b, p7/z, z0.b, z1.b
```

```
Initialize predicate
Initialize FFR to all true
Initialize loop counter to 0
- BEGIN LOOP BODY -
Load str1 with first-fault
Load str2 with first-fault
Read FFR and place active elements in predicate p7
If first active element is not true handle string remainder
Increment loop counter by number of byte lanes in SVE register
Compare full vector of str1 chars to 0 (look for end of string)
Compare full vector of str1 to str2
- BEGIN LOOP CONDITION -
Bitwise OR of predicates to check for differences and str end
Predicate condition: no active elements are true (keep looping)
- BEGIN reminder strcmp -
Increment loop counter by number of true predicate elements
Reset FFR
Compare partial vector of str1 chars to 0
Compare partial vector of str1 to str2
```

arm

Complex  
Arithmetic

### 02ACLE/04\_dotprod\_complex

Complex arithmetic with FMLA or FCMLA

Complex multiply:

$$(a+ib).(c+id) = (ac-bd)+i(ad+bc)$$

![](3fe839e8110987c60318d18e542f4a10_img.jpg)

rot=0

src1 src2 src3

| b | a | d | c | f | e |
|---|---|---|---|---|---|
|---|---|---|---|---|---|

Diagram illustrating the calculation for rotation 0:

Intermediate results:

- $x$  (product of b and d)
- $x$  (product of c and e)
- $f+a.d$  (result of  $f + a \cdot d$ )
- $e+a.c$  (result of  $e + a \cdot c$ )

FCMLA in SVE works for 4 rotations:

- 0, 90, 180 and 270

Complex multiply-add needs a pair of instructions

`svcmla_z(pg, src3, src1, src2, 0);`

`svcmla_z(pg, src3, src1, src2, 90);`

![](9c1941fcc429d4fd6e7ad245285c5c33_img.jpg)

rot=90

src1 src2 src3

| b | a | d | c | f | e |
|---|---|---|---|---|---|
|---|---|---|---|---|---|

Diagram illustrating the calculation for rotation 90:

Intermediate results:

- $x$  (product of b and d)
- $x-1$  (product of c and e)
- $f+b.c$  (result of  $f + b \cdot c$ )
- $e-b.d$  (result of  $e - b \cdot d$ )

### 02\_ACLE/04\_dotprod\_complex

See README.md for details

### ACLE code using FMLA

```
for (int i=0; i<SIZE; i+=v1) {  
    svfloat32x2_t va = svld2(p32_all, (float32_t*)&a[i]);  
    svfloat32x2_t vb = svld2(p32_all, (float32_t*)&b[i]);  
    svfloat32x2_t vc = svld2(p32_all, (float32_t*)&c[i]);  
  
    vc.v0 = svm1a_m(p32_all, vc.v0, va.v0, vb.v0); //c.re += a.re * b.re  
    vc.v1 = svm1a_m(p32_all, vc.v1, va.v1, vb.v1); //c.im += a.im * b.re  
    vc.v0 = svm1s_m(p32_all, vc.v0, va.v1, vb.v1); //c.re -= a.im * b.im  
    vc.v1 = svm1a_m(p32_all, vc.v1, va.v0, vb.v0); //c.im += a.re * b.im  
  
    svst2(p32_all, (float32_t*)&c[i], vc);  
}
```

#### ACLE code using FCMLA

```
for (int i=0; i<SIZE; i+=v1/2) {  
    svfloat32_t va = svld1(p32_all, (float32_t*)&a[i]);  
    svfloat32_t vb = svld1(p32_all, (float32_t*)&b[i]);  
    svfloat32_t vc = svld1(p32_all, (float32_t*)&c[i]);  
  
    vc = svcm1a_m(p32_all, vc, va, vb, 0); //c += a * b  
    vc = svcm1a_m(p32_all, vc, va, vb, 90);  
  
    svst1(p32_all, (float32_t*)&c[i], vc);  
}
```

arm

Data Movement

### Gather/Scatter Operations

- Enable vectorization of codes with non-adjacent accesses on adjacent lanes
- Examples:
  - Outer loop vectorization
  - Strided accesses (larger than +1)
  - Random accesses
- Performance implementation dependent
  - Worst case one separate access per element
- LD1D <Zt>.D, Ps/Z [ $\langle X_n \rangle$ ,  $\langle Z_m \rangle$ .D]

![](16c69c0dacd3c57ae91acd114e5f5bd2_img.jpg)

Diagram illustrating a Gather/Scatter operation.

The diagram shows four registers: Zm, Xn, Zt, and Memory.

Zm contains pointers: @a, @b, @c, @d.

Xn contains the offset.

Zt contains the resulting values: 2, 3, 1, 4.

The offset in Xn is added to the pointers in Zm to calculate the final memory addresses (indicated by the '+' symbol).

The resulting addresses are used to access the Memory block, which contains the values 1, 2, 3, 4. The values 2, 3, 1, 4 are loaded from the memory block into Zt.

Memory is labeled at the bottom.

ARM logo is visible in the bottom right corner.

### Array of Structures vs. Structure of Arrays

```
typedef struct {  
    uint64_t num_projects;  
    float caffeine;  
    bool vim_nemacs;  
} Programmer_t;
```

![](a52d0eb8feb4ddf21fec03f9f175e9d1_img.jpg)

Programmer\_t programmers[N];

Diagram illustrating the memory layout of an Array of Structures (AoS). The array is indexed 0, 1, 2, ... Each element contains the fields: num\_projects (blue), caffeine (orange), and vim\_nemacs (green). The diagram shows load instructions (LD1D, LD1W, LD1B) accessing individual fields within a single element.

```
typedef struct {  
    uint64_t num_projects[N];  
    float caffeine[N];  
    bool vim_nemacs[N];  
} Programmer_t;
```

![](7cb2bb7f9f6fd8be2dc5679e7053ae04_img.jpg)

Programmer\_t programmers;

Diagram illustrating the memory layout of a Structure of Arrays (SoA). The fields are stored contiguously: num\_projects (blue), caffeine (orange), and vim\_nemacs (green). The diagram shows that accessing a field requires loading the entire array (e.g., LD1D for num\_projects, LD1W for caffeine, LD1B for vim\_nemacs).

### 02ACLE/05\_gather

- Use SVE vector tuples to access structure
- Performance depends on u-arch and memory system

```
typedef struct {  
    uint32_t x;  
    uint32_t y;  
} Particle_t;
```

Structure loads:

LD2W {<Zt>.H, <Zt+1>.H}, P0/Z, [X0]

Particle\_t particles[N];

![](54bab05b404ce895e109a02e758a548a_img.jpg)

Diagram illustrating the memory layout of the structure array `particles[N]`. The array is indexed by 0, 1, 2, etc. Each element is a `Particle_t` structure, which consists of two 32-bit fields, `x` (blue) and `y` (orange). The diagram shows the memory access pattern for the first three elements (0, 1, 2), where the blue and orange fields alternate.

memory

Zt

Zt+1

register file

![](59fdf9faef450c0a4236031fb44d9faa_img.jpg)

Diagram illustrating the register file contents for the SVE vector tuple access. The register file contains two rows of registers. The top row is labeled Zt, and the bottom row is labeled Zt+1. Each register is divided into two fields, corresponding to the structure fields `x` (blue) and `y` (orange). The diagram shows the contents of the first four registers in the Zt row (blue fields) and the first four registers in the Zt+1 row (orange fields).

### 02ACLE/05\_gather

See README.md for details

#### Original code

```
typedef struct {  
    int32_t x;  
    int32_t y;  
} Particle_t;  
  
void move(Particle_t p[SIZE], int32_t x, int32_t y)  
{  
    for (int i=0; i<SIZE; i++) {  
        p[i].x += x;  
        p[i].y += y;  
    }  
}
```

#### Use Vector Tuples

```
void move(Particle_t p[SIZE], int32_t x, int32_t y)  
{  
    uint32_t v1 = svcntw();  
  
    svbool_t p32_all = svptrue_b32();  
  
    for (int i=0; i<SIZE; i+=v1) {  
        svint32x2_t vp = svld2(p32_all, (int32_t*)&p[i]);  
  
        vp.v0 = svadd_m(p32_all, vp.v0, x);  
        vp.v1 = svadd_m(p32_all, vp.v1, y);  
  
        svst2(p32_all, (int32_t*)&p[i], vp);  
    }  
}
```

arm

### SVE Load Replicate and GEMM

Neat theory; YMMV

### GEMM

![](3a5bbd20003027ede9cd24b5c622404a_img.jpg)

$$c_{ij} += \sum_{k=0}^{K-1} a_{ik} b_{kj}$$

Diagram illustrating the GEMM operation, showing matrices A, B, and C. Matrix A (blue) has dimensions M x K. Matrix B (orange) has dimensions K x N. Matrix C (yellow) has dimensions M x N. The diagram highlights the current element  $c_{ij}$  being calculated by summing the products of the corresponding elements from the current row  $i$  of A and the current column  $j$  of B.

#### GEMM – step 1 – vectorize along the columns

![](f2c40bfbb63eaf7fd84888bdbf1a0a51_img.jpg)

The figure illustrates the GEMM (General Matrix Multiplication) operation, focusing on the first step: vectorizing along the columns. The matrices involved are A (blue), B (orange), and C (yellow).

The matrix C is updated using the formula:

$$c_{ij} += \sum_{k=0}^{K-1} a_{ik} b_{kj}$$

The dimensions shown are:

- Matrix A: Height M, Width K.
- Matrix B: Height K, Width N.
- Matrix C: Height M, Width N.

The diagram shows the current state of matrix C (yellow) and the contribution of the current column of A (blue) and the current column of B (orange) to the update. The indices i, j, and k are indicated.

#### GEMM – step 2 – unroll along rows

![](734487b0336ba703328f4484af34e77d_img.jpg)

The figure illustrates the GEMM (General Matrix Multiplication) step 2, unrolling along rows, showing the matrices A, B, and C, and the resulting element  $c_{ij}$ .

The matrix multiplication formula is:

$$c_{ij} += \sum_{k=0}^{K-1} a_{ik} b_{kj}$$

The matrices are shown with dimensions:

- Matrix A (blue): Dimensions  $M \times K$ . The current row  $i$  is highlighted.
- Matrix B (orange): Dimensions  $K \times N$ . The current column  $j$  is highlighted, with the range  $[j:j+L]$  indicated.
- Matrix C (yellow): Dimensions  $M \times N$ . The resulting element  $c_{ij}$  is highlighted.

### DGEMM kernel (NEON, 128-bit, 24 accumulators + 4 + 3)

![](1ddf3a99e7935a2f5f85e7f7e038e2fa_img.jpg)

Diagram illustrating the DGEMM kernel structure:

Matrix C (Rows 0-7, vector cols 0-2) is shown on the left. Matrix A (Rows 0-7, vector cols 0-2) is shown on the right, with specific elements  $A_{01}$ ,  $A_{23}$ ,  $A_{45}$ , and  $A_{67}$  highlighted. The operation is  $C_{ij} = A_{ij} + B_{ij}$ .

Matrix B (Rows 0-2, vector cols 0-2) is shown on the far right, with elements  $B_0$ ,  $B_1$ , and  $B_2$  highlighted. The iteration variable  $k$  is indicated by an arrow pointing down.

Each k iteration:

- 4 vector loads from A
- 3 vector loads from B
- 24 indexed FMLA in C

```
fm1a C20.2d, B0.2d, A23.d[0] fm1a C30.2d, B0.2d, A23.d[1]
fm1a C21.2d, B1.2d, A23.d[0] fm1a C31.2d, B1.2d, A23.d[1]
fm1a C22.2d, B2.2d, A23.d[0] fm1a C32.2d, B2.2d, A23.d[1]
```

### SVE load Replicate Quadword instructions: LD1RQ [BHWD]

![](4203d38ddc712f22bd4d88ca28c7a2af_img.jpg)

double \*A;

Mem.

128 bit 128 bit

LD1D { Z0.D }, P0/Z, [X0]

A[0] A[1] A[2] A[3] ...

Z0

LD1RQD { Z1.D }, P0/Z, [X0]

A[0] A[1] A[0] A[1] ...

Z1

### DGEMM kernel (SVE, **LEN** x **128-bit**, 24 accumulators + 4 + 3)

![](5148ae85e7c243139ae6b37e24f01940_img.jpg)

Diagram illustrating the DGEMM kernel operation:

Matrix  $C_{ij}$  (ROWS (i), vector cols (j)) is updated by adding the product of matrices  $A$  and  $B$ .

Matrix  $A$  is shown with elements  $A_{01}$ ,  $A_{23}$ ,  $A_{45}$ ,  $A_{67}$ . Matrix  $B$  is shown with elements  $B_0$ ,  $B_1$ ,  $B_2$ .

Each k iteration:

- 4 vector **load replicate** from **A**
- 3 vector loads from **B**
- 24 indexed FMLA in **C**

fmla  $C_{20}$ .d,  $B_0$ .d,  $A_{23}$ .d[0]

fmla  $C_{21}$ .d,  $B_1$ .d,  $A_{23}$ .d[0]

fmla  $C_{22}$ .d,  $B_2$ .d,  $A_{23}$ .d[0]

fmla  $C_{30}$ .d,  $B_0$ .d,  $A_{23}$ .d[1]

fmla  $C_{31}$ .d,  $B_1$ .d,  $A_{23}$ .d[1]

fmla  $C_{32}$ .d,  $B_2$ .d,  $A_{23}$ .d[1]

### DGEMM: SVE vs NEON

|      | Each k iteration                                                                             | Bytes in one k iteration                                  | Total C area computed              | SVE/NEON A and B data reads for same C area                          |
|------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------|------------------------------------|----------------------------------------------------------------------|
| SVE  | <ul><li>4 vector <b>load</b> <b>replicate</b> from A</li><li>3 vector loads from B</li></ul> | $4 \times 128b$<br>+<br>$3 \times \text{LEN} \times 128b$ | $24 \times 128b \times \text{LEN}$ | $\frac{\text{SVE}}{\text{NEON}} = \frac{4 + 3 \times \text{LEN}}{7}$ |
| NEON | <ul><li>4 vector loads from A</li><li>3 vector loads from B</li></ul>                        | $7 \times 128b$                                           | $24 \times 128b$                   |                                                                      |

#### DGEMM: SVE more memory efficient than LEN times NEON

![](49281e6ec325a21f4b1574ad0851fea3_img.jpg)

Bar chart illustrating the memory efficiency ratio of SVE (Scalable Vector Extension) to NEON (Advanced SIMD) for DGEMM (Double-Generic Matrix Multiply) across different SVE Vector Bit widths.

The Y-axis represents the ratio  $\frac{\text{SVE}}{\text{NEON}}$ , ranging from 0 to 1.2. The X-axis represents the SVE Vector Bits, ranging from 128 to 2048.

| SVE Vector Bits | Ratio ( $\frac{\text{SVE}}{\text{NEON}}$ ) |
|-----------------|--------------------------------------------|
| 128             | 1.0                                        |
| 256             | 0.7                                        |
| 384             | 0.6                                        |
| 512             | 0.58                                       |
| 640             | 0.55                                       |
| 768             | 0.52                                       |
| 896             | 0.50                                       |
| 1024            | 0.48                                       |
| 2048            | 0.45                                       |

The chart demonstrates that as the SVE vector width increases, the memory efficiency ratio decreases, indicating that SVE becomes less memory efficient than NEON relative to the vector width, although it remains more efficient than NEON for smaller vector widths.

arm

Micro-examples

## 03\_SVE: Micro-examples for individual SVE instructions

Based on <https://developer.arm.com/documentation/dai0548/latest>

![Screenshot of a file directory listing for SVE micro-examples. The directory contains folders for sections B1, B3, B4, B5, C1, C2, C3, D1, D2, D3, and a README.md file, along with a PDF file titled 'SVE-SVE2-programming-examples-REL-01.pdf'.](1f61b8ff3409af7114e85a9bef257305_img.jpg)

Screenshot of a file directory listing for SVE micro-examples. The directory contains folders for sections B1, B3, B4, B5, C1, C2, C3, D1, D2, D3, and a README.md file, along with a PDF file titled 'SVE-SVE2-programming-examples-REL-01.pdf'.

### Using the Micro-examples

- PDF document describes each example
- Directory name indicates section in the PDF
- Includes both SVE and SVE2 examples
- May need ArmIE to run some examples, e.g. SVE2 examples require ArmIE to run on A64FX

## 03\_SVE: Micro-examples for individual SVE instructions

Based on<https://developer.arm.com/documentation/dai0548/latest>

![](fe6af03ab7804980cff28a06241be192_img.jpg)![](c391b0a0928f19ae05b796299c4abfaa_img.jpg)![](7c166dd7ef469f2cddf2fc4025f9188b_img.jpg)

# SVE Resources

<http://developer.arm.com/hpc>

## • **Porting and Optimizing Guides**

- For SVE: <https://developer.arm.com/docs/101726/0110>
- For Arm in general: <https://developer.arm.com/docs/101725/0110>

## • **The SVE Specification and Arm Instruction Reference**

- Arm Architecture Reference Manual Supplement, SVE for ARMv8-A
- <https://developer.arm.com/docs/ddi0596/i/a64-sve-instructions-alphabetic-order>

## • **ACLE References and Examples**

- ACLE for SVE: <https://developer.arm.com/docs/100987/latest>
- Worked examples: [A Sneak Peek Into SVE and VLA Programming](#)
- Optimized machine learning: [Arm SVE and Applications to Machine Learning](#)

arm

Thank You

Danke

Merci

谢谢

ありがとう

Gracias

Kiitos

감사합니다

धन्यवाद

شكرًا

תודה