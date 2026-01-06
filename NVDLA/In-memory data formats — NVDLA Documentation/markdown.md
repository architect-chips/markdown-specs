

# In-memory data formats

## Overview

DLA engine supports various types of CNN layers like convolution layer, pooling, ReLU, LRN, etc. To improve the performance DLA engine also applies some options like Winograd, weight compression and multi-batch mode. To support these layers DLA engine uses specified input and output data formats.

There are two main types of input formats. They are weight data and activation data. The weight formats include below branches:

- weight for direct convolution
- weight for image input
- weight for Winograd convolution

Two options for weight formats:

- channel post-extension for image input mode
- sparse compression

The activation formats supported by DLA engine includes:

- feature data format
- pixel format (ROI input)

The output formats supported by DLA engine includes:

- feature data format

Besides, DLA engine will fetch below auxiliary formats from external memory

- bias data
- PRELU data
- batch-normalization data
- element-wise data

Channel extension refers to a set of mapping rule for both weight data and activation data to fit with accelerator. It includes:

- Channel extension for Winograd convolution
- Channel pre-extension for image input mode
- Channel post-extension for image input mode

The channel post-extension for image input mode is an option for performance. Other two are mandatory for their working mode. HW handles all channel extension on feature/pixel data, while SW shall do channel extension to weight data accordingly.

All data formats should be mapping in memory with rules.

## Precision Type

NVDLA engine pipeline support three types of data precision. They are int8, int16 and fp16. For int8, one element of data refers to an 8-bit signed integer. For int16, one element refers to a 16-bit signed integer. For fp16, one element refers to a 16-bit floating point data, which is also named as half-precision floating-point format.

All input feature data should belong to one of three precision types. And all image input data will be converted to one precision type before calculation. For example, DLA engine can take a T\_R10G10B10A2 image as input (for first layer) and convert the component to int8, int16 or fp16.

### Precision Conversion

NVDLA engine supports dynamical precision conversion. There are some rules:

- NVDLA convolution pipeline supports precision conversion for image input mode only.
- Direct convolution (DC) mode and Winograd convolution mode do not support precision conversion
- For image input mode (please see section 6.1.1.4), pipeline allows conversion from integer to all 3 types. Floating point images can only be converted to fp16.
- Batch-normalization and element-wise layer (implemented in SDP) support free conversion of int16 <-> fp16 and int8 <-> int16 for DC mode only.
- LRN layer (implemented in CDP) does not support any precision conversion
- Pooling layer (implemented in PDP) does not support any precision conversion.

Here is the summary:

Table 29 - Precision conversion for convolutional layer

| Configured input format | Configured output precision | Real precision in pipeline | Corresponding weight precision |
|-------------------------|-----------------------------|----------------------------|--------------------------------|
| image input<br>(uint8/  | int8                        | int8                       | int8                           |
|                         | int16                       | int16                      | int16                          |
| int16/uint16)           | fp16                        | fp16                       | fp16                           |
|                         |                             |                            |                                |
| image input<br>(fp16)   | int8                        | <b>Invalid case</b>        | <b>Invalid case</b>            |
|                         | int16                       | <b>Invalid case</b>        | <b>Invalid case</b>            |
| int8 feature data       | int8                        | int8                       | int8                           |
|                         | int16                       | <b>Invalid case</b>        | <b>Invalid case</b>            |
| int16 feature data      | int8                        | <b>Invalid case</b>        | <b>Invalid case</b>            |
|                         | int16                       | int16                      | int16                          |
|                         | fp16                        | <b>Invalid case</b>        | <b>Invalid case</b>            |

| Configured input format | Configured output precision | Real precision in pipeline | Corresponding weight precision |
|-------------------------|-----------------------------|----------------------------|--------------------------------|
| fp16 feature data       | int8                        | Invalid case               | Invalid case                   |
|                         | int16                       | Invalid case               | Invalid case                   |
|                         | fp16                        | fp16                       | fp16                           |

Table 30 - Precision conversion for SDP layer (offline mode)

| Configured input format | Configured output precision | Real precision in pipeline |
|-------------------------|-----------------------------|----------------------------|
| int8 feature data       | int8                        | int32                      |
|                         | int16                       | int32                      |
|                         | fp16                        | Invalid case               |
| int16 feature data      | int8                        | int32                      |
|                         | int16                       | int32                      |
|                         | fp16                        | int32                      |
| fp16 feature data       | int8                        | Invalid case               |
|                         | int16                       | fp32                       |
|                         | fp16                        | fp32                       |

Table 6-3 precision conversion for LRN layer

Table 31 - Precision conversion for LRN layer

| Configured input format | Configured output precision | Real precision in pipeline |
|-------------------------|-----------------------------|----------------------------|
| int8 feature data       | int8                        | int8                       |
|                         | int16                       | Invalid case               |
|                         | fp16                        | Invalid case               |
| int16 feature data      | int8                        | Invalid case               |
|                         | int16                       | int16                      |
|                         | fp16                        | Invalid case               |
| fp16 feature data       | int8                        | Invalid case               |
|                         | int16                       | Invalid case               |
|                         | fp16                        | fp16                       |

Table 32 - Precision conversion for pooling layer

| Configured input format | Configured output precision | Real precision in pipeline |
|-------------------------|-----------------------------|----------------------------|
| int8 feature data       | int8                        | int8                       |
|                         | int16                       | Invalid case               |
|                         | int16                       | Invalid case               |
| int16 feature data      | int8                        | Invalid case               |
|                         | int16                       | int16                      |
|                         | fp16                        | Invalid case               |

| Configured input format | Configured output precision | Real precision in pipeline |
|-------------------------|-----------------------------|----------------------------|
| fp16 feature data       | int8                        | Invalid case               |
|                         | int16                       | Invalid case               |
|                         | fp16                        | fp16                       |

For pixel formats, the conversion to int8/int16/float16 follows the equation below.

$$d_{int8} = truncate2int8 ((d_{pixel} - offset) * SF)$$
$$d_{int16} = truncate2int16 ((d_{pixel} - offset) * SF)$$
$$d_{fp16} = int2fp ((d_{pixel} - offset) * SF)$$

Equation 1 pixel precision conversion

Here *SF* refers to scaling factor, *offset* refers to offset value. They are both given by programmable register fields.

For conversion between int16 and int8, the equations are:

$$d_{int8} = truncate2int8 ((d_{int16} - offset) * SF)$$
$$d_{int16} = truncate2int16 ((d_{int8} - offset) * SF)$$

Equation 3 precision conversion between int8 and int16

**The CDMA and SDP convert precision individually.** When working in on-flying mode, SDP takes precision of convolution pipeline output as input precision then do another precision conversion, but the input precision and output precision should have the same bit-depth.

### FP16 Supporting

This section describes NVDLA how to support float16 in data-path.

### - Infinity

NVDLA treats infinity value as different normalized value module by module:

| Sub-module           | INF converted values                         |
|----------------------|----------------------------------------------|
| Convolution pipeline | +/-65536 (DC/IMG)<br>+/-65504 (Winograd)     |
| SDP                  | +/-3.40282e+38                               |
| CDP                  | +/-4292870144                                |
| PDP                  | +/-4292870144 (For AVE)<br>INF (For Max/Min) |

There won't be any INF output from any NVDLA sub-module, if saturation happens, NVDLA will output the maximum representable (+/-65504 for FP16, 32767/-32768 for INT16, 127/-128 for INT8).

### - NaN

NVDLA won't generate NaN since no infinity value involves in any operation. But it supports NaN propagation. If input data have NaN, any result related to NaN operand will be NaN (mantissa propagation behavior is undefined).

NVDLA provides a register field to flush NaN to Zeros. If the register is set, all input NaNs are treated as zero value in float point data-path and output data cube doesn't have any NaN. Otherwise input NaNs propagate to output.

NVDLA also provide input/output NaN counting registers that summarize total NaN number in input/output data cube. The counting registers are updated when layer is done. When done interrupts arrives, FW can poll NaN counting registers to figure out whether input/output data cubes have any NaN value.

### - Denormalized value

NVDLA supports denormalized value for both input and output. The dealing of denormalized value is completely following the requirement of IEEE754 standard.

Actually, NVDLA internal float point data-path often provide fp17/fp32 value for better precision. These fp17 and fp32 format doesn't support denormalized value during calculation. Even though these formats have better precision than fp16 with denormalized value. Before writing back to memory, fp17/fp32 will convert to fp16 with denormalized value.

## - Rounding

NVDLA supports Rounding to Nearest (or RN) in calculation except overflow case. If the result is exceeding maximal normal value, it will be clipped to max normalized value.

## Feature Data Format

DLA engine maintains a private data format for all supported HW-layers. The data format is called feature data format. This format is only generated by DLA engine itself.

All elements of feature data for one layer are organized as a 3D data cube. Three dimensions are width (W), height (H) and channel size (C). The memory mapping rules are:

- Adding data into end of channel if the original data is not 32byte aligned in C direction.
- The attached data can be any value except NaN when it's fp16.
- Split the data cube into 1x1x32byte small atom cubes.
- Reordering atom cubes in by progressively scanning the data cube. Scanning order: W (line) -> H (height) -> C (channel).
- Map all atom cubes into memory by scanning sequence.
- All atom cubes in the same line are mapped compactly.
- Atom cube mapping at line boundary and/or surface boundary can be either adjacently or incompatibly. But they are always 32-byte aligned.
- In conclusion, mapping in memory follows pitch linear format. The order is C' (32byte) -> W -> H -> C (surfaces). Here C' changes fastest and C changes slowest.

Fig. 10 is a case of feature data that all small cubes are mapped compactly. This is called packed feature data. If the line or surface of small cubes is not mapped compactly, it is called unpacked. See Fig. 11.

### **Note**

Line stride and surface stride of feature data shall always align to 32bytes. Start address has same alignment as well. This is mandatory requirement.

![](0ad3f61f997eb05afb341fc46024bf2b_img.jpg)

Diagram illustrating Packed feature data mapping.

A 3D **DATA CUBE** (Feature data cube) is shown, with dimensions W (Width), H (Height), and C (Channels). The data is packed compactly, meaning the entire cube is mapped sequentially in memory.

The mapping proceeds from the DATA CUBE to **Memory Mapping**. The memory is shown as a 1D array of 32 bytes, with addresses ranging from 0 (low memory address) to 31 (high memory address). The data elements are packed sequentially, corresponding to the order of the DATA CUBE (e.g., 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31).

Fig. 10 - Packed feature data

![](ed2fa033a401564314cdc32fe9732935_img.jpg)

Diagram illustrating Unpacked feature data mapping, showing line stride and surface stride.

A 3D **DATA CUBE** is shown, with dimensions W (Width), H (Height), and C (Channels). The data is unpacked, meaning the mapping is non-compact. The diagram highlights the **line\_stride** (horizontal dimension) and **surface\_stride** (vertical dimension).

The mapping proceeds from the DATA CUBE to **Memory Mapping**. The memory is shown as a 1D array of 32 bytes, with addresses ranging from 0 (low memory address) to 31 (high memory address). The data elements are mapped non-compact, corresponding to the order of the DATA CUBE (e.g., 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31).

*Fig. 11 - Unpacked feature data*

If a 1x1xC feature data cube maps as surface-packed, NVDLA can treat it like (C/32) x1x 32 cube to save bandwidth.

Mapping of feature data cube is done by NVDLA core logic. Falcon does not involve in mapping procedures.

### Pixel Format

DLA engine supports pixel data for ROI. The pixel data comes from a part or a whole image. The pixel formats are listed in table Table 33.

When NVDLA takes image as input data, there are some limits of configuration.

- Channel size. The valid channel size highly depends on each format. Please see table Table 33.
- Input precision. The input precision highly depends on pixel each format. Please see table Table 33. DMA logic will turn unsigned integer value to signed integer value automatically.
- **Both start address and line stride of pitch linear shall aligned to 32 bytes. This is mandatory requirement.**
- It may have redundant data between 32-byte aligned address and first element. NVDLA use x offset to indicate how many redundant data are. The unit of offset is pixel.

Table 33 - Pixel formats and valid setting

| Format Name       | # of planar | Valid channel size setting | Valid input precision setting | Valid X offset range |
|-------------------|-------------|----------------------------|-------------------------------|----------------------|
| T_R8              | 1           | 1                          | int8                          | 0~31                 |
| T_R10             | 1           | 1                          | int16                         | 0~15                 |
| T_R12             | 1           | 1                          | int16                         | 0~15                 |
| T_R16             | 1           | 1                          | int16                         | 0~15                 |
| T_R16_I           | 1           | 1                          | int16                         | 0~15                 |
| T_R16_F           | 1           | 1                          | int16                         | 0~15                 |
| T_A16B16G16 R16   | 1           | 4                          | int16                         | 0~3                  |
| T_X16B16G16 R16   | 1           | 4                          | int16                         | 0~3                  |
| T_A16B16G16 R16_F | 1           | 4                          | fp16                          | 0~3                  |
| T_A16Y16U16 V16   | 1           | 4                          | int16                         | 0~3                  |
| T_V16U16Y16 A16   | 1           | 4                          | int16                         | 0~3                  |
| T_A16Y16U16 V16_F | 1           | 4                          | fp16                          | 0~3                  |

| Format Name            | # of planar | Valid channel size setting | Valid input precision setting | Valid X offset range |
|------------------------|-------------|----------------------------|-------------------------------|----------------------|
| T_A8B8G8R8             | 1           | 4                          | int8                          | 0~7                  |
| T_A8R8G8B8             | 1           | 4                          | int8                          | 0~7                  |
| T_B8G8R8A8             | 1           | 4                          | int8                          | 0~7                  |
| T_R8G8B8A8             | 1           | 4                          | int8                          | 0~7                  |
| T_X8B8G8R8             | 1           | 4                          | int8                          | 0~7                  |
| T_X8R8G8B8             | 1           | 4                          | int8                          | 0~7                  |
| T_B8G8R8X8             | 1           | 4                          | int8                          | 0~7                  |
| T_R8G8B8X8             | 1           | 4                          | int8                          | 0~7                  |
| T_A2B10G10R_10         | 1           | 4                          | int16                         | 0~7                  |
| T_A2R10G10B_10         | 1           | 4                          | int16                         | 0~7                  |
| T_B10G10R10_A2         | 1           | 4                          | int16                         | 0~7                  |
| T_R10G10B10_A2         | 1           | 4                          | int16                         | 0~7                  |
| T_A2Y10U10V_10         | 1           | 4                          | int16                         | 0~7                  |
| T_V10U10Y10_A2         | 1           | 4                          | int16                         | 0~7                  |
| T_A8Y8U8V8             | 1           | 4                          | int8                          | 0~7                  |
| T_V8U8Y8A8             | 1           | 4                          | int8                          | 0~7                  |
| T_Y8__U8V8<br>__N444   | 2           | 3                          | int8                          | 0~31                 |
| T_Y8__V8U8<br>__N444   | 2           | 3                          | int8                          | 0~31                 |
| T_Y10__U10<br>V10_N444 | 2           | 3                          | int16                         | 0~15                 |
| T_Y10__V10<br>U10_N444 | 2           | 3                          | int16                         | 0~15                 |
| T_Y12__U12<br>V12_N444 | 2           | 3                          | int16                         | 0~15                 |
| T_Y12__V12<br>U12_N444 | 2           | 3                          | int16                         | 0~15                 |
| T_Y16__U16<br>V16_N444 | 2           | 3                          | int16                         | 0~15                 |
| T_Y16__V16<br>U16_N444 | 2           | 3                          | int16                         | 0~15                 |

### Weight Format

Unlike pixel data or feature data, weight data are generated long before convolution operation. And DLA engine never changes them during operation. Software should map weight data with property rules to fit with the calculation sequence in DLA.

The original weight data has 4 dimensions: width, height, channel and number of kernels. They can construct as a group of 3D data cubes. One data cube is called a kernel. See Fig. 12.

DLA engine support 4 types of weight data. They are weight for direct convolution, weight for Winograd convolution, weight for image input and weight for deconvolution. There are two options for weight to improve DLA performance: sparse compression and channel post-extension.

DLA engine support 4 basic formats of weight data for different operation mode:

- weight for direct convolution
- weight for image input
- weight for deconvolution
- weight for Winograd convolution

There are some mandatory requirements for some formats:

- channel pre-extension for image input
- channel extension for Winograd
- Set split for deconvolution

And two options for weight formats:

- channel post-extension
- sparse compressing

Table 34 - Weight formats and options

| Weight types             | Sparse compression option | Post-extension option |
|--------------------------|---------------------------|-----------------------|
| Weight for DC            | Support                   | <b>NOT support</b>    |
| Weight for Winograd      | Support                   | <b>NOT support</b>    |
| Weight for image input   | Support                   | Support               |
| Weight for deconvolution | Support                   | <b>NOT support</b>    |

![Diagram illustrating the structure of original weight data. It shows three stacked rectangular blocks representing weight tensors. The dimensions are labeled: W (width), H (height), and K (kernel size). The vertical dimension is labeled C (channel size). The diagram shows the structure of the weight data.](ae21ece48844b14b230832cbb6fcf735_img.jpg)

(.../images/format\_original\_weight\_data.svg)

Diagram illustrating the structure of original weight data. It shows three stacked rectangular blocks representing weight tensors. The dimensions are labeled: W (width), H (height), and K (kernel size). The vertical dimension is labeled C (channel size). The diagram shows the structure of the weight data.

Fig. 12 - Original weight data

#### Basic Weight for Direct Convolution

Basic weight for direct convolution is the most basic and common weight format. Other weight formats are all extended from this format.

The mapping rules of uncompressed weight for direct convolution are:

- Distribute the kernels into groups. For int16 and fp16 weight, one group has 16 kernels. For int8, one group has 32 kernels. Last group can have fewer kernels.
- Divide each kernel to 1x1x64-element small cubes. For int16/fp16 the small cube is 128 bytes each; and for int8 the small cube is 64 bytes each. Do not append 0 if channel size is not divisible by 128/64.
- After division, all weights are stored in 1x1xC' small cubes, where C' is no more than 128 bytes.
- Scan the 1x1xC' small cubes in a group with C'->K->W->H->C sequence. Here C' changes fastest and C changes slowest. And map them compactly as scanning sequence.
- Map the weight groups compactly. Do not append any 0s between group boundaries.
- Append 0s at end of all mapped weight for 128-byte alignment.

Diagram below shows how a group of 3x3x192Byte kernel maps for direct convolution.

![Diagram illustrating weight mapping for direct convolution inside one group. It shows four 3D kernel cubes (K0, K1, K14, K15) with dimensions W=3, H=3, and C=192 bytes. The cubes are connected by a dotted line, indicating a sequence. Below the cubes, a memory layout is shown, mapping the weights sequentially from K0_00 to K15_17, with an arrow pointing down indicating the mapping sequence. The memory layout is labeled 'Low memory address' on the left and 'High memory address' on the right.](6b32b7b928d34eeccb15c29cdf9d2cb3_img.jpg)

Diagram illustrating weight mapping for direct convolution inside one group. It shows four 3D kernel cubes (K0, K1, K14, K15) with dimensions W=3, H=3, and C=192 bytes. The cubes are connected by a dotted line, indicating a sequence. Below the cubes, a memory layout is shown, mapping the weights sequentially from K0\_00 to K15\_17, with an arrow pointing down indicating the mapping sequence. The memory layout is labeled 'Low memory address' on the left and 'High memory address' on the right.

(../\_images/format\_dc\_weight\_mapping.svg)

Fig. 13 - Weight mapping for direct convolution inside one group

#### Basic Weight for image input

Weight mapping for image input is like weight for direct convolution. The main difference is that image weight needs an additional channel extension step ahead of mapping steps for direct convolution weight.

The channel pre-extension for image weight is a mandatory requirement, while channel post-extension is an option to improve performance.

#### Note

Channel pre-extension for image weight is different from channel extension for Winograd convolution.

The key idea of per-extension is to turn all weights in same line to a single channel. Fig. 14 is a case for an int16 image input whose channel size is 3.

![](10c82dcc5f2c237961329dd29d65859c_img.jpg)

Diagram illustrating channel extension for image weight. An initial  $5 \times 5 \times 3$  weight kernel for  $\text{int16}/\text{fp16}$  is shown, with dimensions  $C=3$  (channels),  $H=5$  (height), and  $W=5$  (width). The values are:

|   | 0  | 1  | 2  | 3  | 4  |
|---|----|----|----|----|----|
| 0 | 5  | 6  | 7  | 8  | 9  |
| 1 | 10 | 11 | 12 | 13 | 14 |
| 2 | 15 | 16 | 17 | 18 | 19 |
| 3 | 20 | 21 | 22 | 23 | 24 |

An arrow points to the extended kernel, which is  $3 \times 5 \times 15$  for  $\text{int16}/\text{fp16}$ . The dimensions are  $C=3$  (channels),  $H=5$  (height), and  $W=15$  (width). The values are:

|   | 0  | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | 11 | 12 | 13 | 14 |
|---|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| 0 | 5  | 6  | 7  | 8  | 9  | 5  | 6  | 7  | 8  | 9  | 5  | 6  | 7  | 8  | 9  |
| 1 | 10 | 11 | 12 | 13 | 14 | 10 | 11 | 12 | 13 | 14 | 10 | 11 | 12 | 13 | 14 |
| 2 | 15 | 16 | 17 | 18 | 19 | 15 | 16 | 17 | 18 | 19 | 15 | 16 | 17 | 18 | 19 |
| 3 | 20 | 21 | 22 | 23 | 24 | 20 | 21 | 22 | 23 | 24 | 20 | 21 | 22 | 23 | 24 |

Fig. 14 - Channel extension for image weight

Channel pre-extension is the first step for image weight. Then all extended kernels follow the same steps of weight for direct convolution. That is, SW still need to do group and channel distribution after channel extension.

#### Basic Weight for Winograd Convolution

The memory mapping of Winograd weight is very different from direct convolution. There are two phases to process the weights. Phase 1 is to do channel extension and conversion for each kernel. Phase 2 is to group the kernels and map small cubes in memory.

Steps of phase 1:

- Divide kernels to  $1 \times 1 \times 32$  Byte small cubes. If the channel size is not divisible by 32, append 0s.
- Do channel extension in if convolution stride is not 1. The new width and height of a kernel should be 3 after extension.
- Convert the kernel from  $3 \times 3 \times C$  cube to a  $4 \times 4 \times C$  cube. The equation is GWGT. Here W is each  $4 \times 4 \times 1$  of weight cube, G is a  $4 \times 4 \times 3$  matrix and GT is transpose matrix.
- During conversion, a scaling factor may involve. Please see the Winograd convolution documentation for reference.
- The width and height of a kernel should be 4 after conversion.

$$G = \begin{bmatrix} 1 & 0 & 0 \\ 0.5 & 0.5 & 0.5 \\ 0.5 & -0.5 & 0.5 \\ 0 & 0 & 1 \end{bmatrix}$$

Matrix for weight transfer for Winograd

Steps of phase 2:

- Distribute the converted kernels into groups. For  $\text{int16}$  and  $\text{fp16}$  weight, one group has 16 kernels. For  $\text{int8}$ , one group has 32 kernels.
- Divide converted kernels to  $4 \times 4 \times 4$  elements small cubes. For  $\text{int16}/\text{fp16}$  small cube is 128 bytes each. For  $\text{int8}$  small cube is 64 bytes each. The channel size should always divisible by 4.

- Scan the 4x4x4 elements small cubes in a group with K->C sequence. Take int16 for example, the scan order is small cube 0 of K0, small cube 0 of K1, small cube 0 of K2, ..., small cube 0 of K15, small cube 1 of K0, small cube 1 of K1, ..., small cube 1 of K15, ..., small cube N of K15.
- Maps the 4x4x4 elements small cubes closely with scanning order
- Maps the weight groups one by one closely

The phase 2 is similar to weight for direct convolution except the small cube size is 4x4x4 elements.

Figure below shows how to do channel extension to one kernel and map the data.

![Diagram illustrating channel extension and conversion for Winograd. The process starts with a 5x5x488byte weight kernel (C=64 bytes, W=5, H=5). A 4x4x4 convolution window is shown with a vertical stride of 2 and a horizontal stride of 2. This kernel is extended to a 3x3x256byte weight kernel (C=256 bytes, W=3, H=3). Finally, the kernel is converted to a 4x4x256byte weight kernel (C=256 bytes, W=4, H=4). The diagram also shows memory address mapping for the extended kernel, indicating low memory addresses (K0_00, K1_00, ..., K15_00) and high memory addresses (K14_08, K15_08, ..., K15_31).](602ada2a012ff3cc38d91de2eec5b450_img.jpg)

Diagram illustrating channel extension and conversion for Winograd. The process starts with a 5x5x488byte weight kernel (C=64 bytes, W=5, H=5). A 4x4x4 convolution window is shown with a vertical stride of 2 and a horizontal stride of 2. This kernel is extended to a 3x3x256byte weight kernel (C=256 bytes, W=3, H=3). Finally, the kernel is converted to a 4x4x256byte weight kernel (C=256 bytes, W=4, H=4). The diagram also shows memory address mapping for the extended kernel, indicating low memory addresses (K0\_00, K1\_00, ..., K15\_00) and high memory addresses (K14\_08, K15\_08, ..., K15\_31).

Fig. 15 - Channel extension and conversion for Winograd

#### Weight Channel Post-extension for image input

Weight channel post-extension is an option to enhance MAC efficiency when channel size is less than 32. It is available for image input mode only.

Key idea of channel post-extension is to combine two neighbor lines to saving the efficiency. It allows two-line ( $C \le 32$ ) or four-line ( $C \le 16$ ) combination. 1, 2 and 4 parameters are available.

If this option is enabled, NVDLA manage to post-extend input feature (or image) data in CSC sub units. And SW needs to adjust weight mapping order.

The channel post-extension is done after pre-extension. Figure below shows one case which parameter is 2.

![](b05a8a3551db31147979064952179990_img.jpg)

Diagram illustrating weight channel post-extension, parameter = 2.

The diagram shows a sequence of 3D weight tensors (K0, K1, K14, K15) with dimensions  $H=3$  and  $W=3$ . The channel dimension is  $C=28$ . The tensors are connected by an arrow indicating the flow of data.

Below the tensors, a linear memory layout is shown, ranging from Low memory address to High memory address. The memory addresses are grouped by kernel (K0, K1, K14, K15) and channel (00, 03, 01, 02, 05, 08).

Weight channel post-extension parameter = 2

Fig. 16 - Weight channel post-extension, parameter = 2

Flow of pre-extension, post-extension, mapping and compression option for image weight:

- Do pre-extension
- Do post-extension
- Remap weight data
- Do weight compression.

Some tips for post-extension:

- Channel post-extension cannot be used in Winograd convolution
- Channel post-extension only support 2-line and 4-line.
- If weight height is not divisible by 2 (2-lines) or 4 (4-lines), do NOT append 0s. This is unlike channel extension for Winograd.

#### Sparse Compression option

To reduce the bandwidth and power consumption on memory interface, NVDLA engine support weight sparse compression option. All four weight formats can support sparse compression. This option requires additional steps after basic mapping and post-extension option.

Sparse algorithm uses one-bit tag to indicate a weight element is zero or not. Bit tags of one kernel group compose a weight mask bit group, or WMB. WMBs reside in a dedicate memory surface. Since 0 values are marked by bit tags (assign 0 to corresponding bit), they can be removed from original weight memory surface. A third memory surface recodes remaining byte number of each kernel group (WGS).

The steps of weight compression are:

- Always use 1 bit to indicate 1 element of weight. For int16 and fp16, 1 bit represents 2 bytes of weight data; for int8, 1 bit represents 1 byte of weight data.
- Compress weight group by group. Assembly of bits for one weight group is called WMB. The bits in WMB are stored as little-endian.
- Align WMB surface to 128-byte by adding 0 bits in the end

- Remove all 0 weights in original surface and pack them compactly.
- Align compressed weight surface to 128-byte by adding 0s in the end.
- Calculate the byte number of each compressed group. The remaining byte number of each group is called weight group size or WGS. One WGS is of 32-bit wise.
- Store WGS, WMB and compressed weight into three separated memory surfaces.

The diagram below shows the memory mapping of compressed weight format.

![](411fa16c3211377525ba37c57784fee0_img.jpg)

Diagram illustrating the memory mapping of compressed weight format.

The process starts with the **Uncompressed Weights** (uncompressed weight surface), which is then compressed into the **Compressed Weight** (compressed weight surface).

The compressed weight surface is divided into three separate memory surfaces:

- **WGS surface:** Contains weight group sizes (WGS 0, WGS 1, ..., WGS n).
- **WMB surface:** Contains weight memory blocks (WMB 0, WMB 1, ..., WMB n).
- **Compressed Weight:** Contains the actual compressed weight data.

Fig. 17 - Memory mapping of compressed weight

### Bias Data Format

Bias data is another optional input data for convolution layers. When this option is enabled, DLA engine will add the bias data to result of convolution before writing back to memory.

There are three types of bias data,

- Per layer bias data
- Per channel bias data
- Per element bias data

They both store in memory for DLA engine to fetch.

If the output feature data cube is  $W \times H \times C$ , check below table for the corresponding bias cube size:

| Per Layer   | 1x1x1 (Register)      |
|-------------|-----------------------|
| Per Channel | $1 \times 1 \times C$ |
| Per Element | $W \times H \times C$ |

For INT pipeline, bias data can be either INT8 or INT16, and FP16 type of bias data is in16-bit fp16 format. They are generated along with CNN network.

The memory mapping of bias data is described as below:

### **Per Channel:**

- Two bytes per element with INT16/FP16 or 1 byte per element with INT8

![](1145fc59efdc7dacc8d3c715d7ff3248_img.jpg)

Diagram illustrating the memory mapping of Per Channel Bias Data (Case 1).

The left side shows a 3D representation of the data structure, labeled C/32Byte, with 8 channels (0 to 7) and 8 elements per channel (0 to 7).

An arrow points to the right side, which shows the linear memory mapping:

- The memory is 32 bytes total.
- Addresses 0 through 7 are labeled "low memory address".
- Addresses 28 through 31 are labeled "high memory address".

The mapping is labeled **Memory Mapping**.

Fig. 18 - Memory Mapping of Per Channel Bias Data (Case 1)

- 2 bytes per element with INT8:

![](b3df5964338063224492c01f09e4fed6_img.jpg)

Diagram illustrating memory mapping for Per Channel Bias Data (Case 2).

On the left, a 3D block labeled C/64Byte is shown, containing 8 elements (0 through 7).

An arrow points to the right, indicating the mapping to memory.

On the right, the memory is shown as a 2D array structure. The top section is labeled "64 bytes" and contains addresses 0 through 7 (low memory address). The bottom section contains addresses 28 through 31 (high memory address). The addresses 8 through 27 are indicated by a dotted line, representing the intermediate memory space.

### Memory Mapping

Fig. 19 - Memory Mapping of Per Channel Bias Data (Case 2)

- 2 bytes per element with INT8:

### **Per Element:**

- Two bytes per element with INT16/FP16 or 1 byte per element with INT8

![](f4d72193f77f6646a2a1f4baaa927154_img.jpg)

Diagram illustrating the memory mapping of Per Element Bias Data (Case 1).

The left side shows a **DATA CUBE** with dimensions W (Width), H (Height), and C (Channels). The cube is indexed from 0 to 31. A group of 32 bytes is highlighted, corresponding to the first 32 elements (0 to 31).

An arrow points from the DATA CUBE to the **Memory Mapping** on the right.

The Memory Mapping shows the 32 bytes stored sequentially in memory, labeled "low memory address" at the top and "high memory address" at the bottom. The elements are stored in the order: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31.

Fig. 20 - Memory Mapping of Per Element Bias Data (Case 1)

- 2 bytes per element with INT8:

![](a706c91f074ac2840c161a3d4a7c0f91_img.jpg)

Diagram illustrating the memory mapping of Per Element Bias Data when 2 bytes per element with INT8 is used.

The left side shows a **DATA CUBE** with dimensions W (Width), H (Height), and C (Channels). The cube is indexed from 0 to 31. A group of 64 bytes is highlighted, corresponding to the first 64 elements (0 to 63).

An arrow points from the DATA CUBE to the **Memory Mapping** on the right.

The Memory Mapping shows the 64 bytes stored sequentially in memory, labeled "low memory address" at the top and "high memory address" at the bottom. The elements are stored in the order: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31.

Fig. 21 - Memory Mapping of Per Element Bias Data (Case 2)

### PRELU Data Format

Each PReLU data just have one component and it will be fed into multiplier of SDP.

PReLU always operated per-channel thus there is only one type of PReLU data:

- Per channel PReLU data

Per channel PReLU data is stored in memory in a continuous  $1 \times 1 \times C$  space. Be noted that C is in unit of channel.

- For INT8/16, each channel can occupy 1 or 2 bytes depending on B/N/E RDMA\_DATA\_SIZE
- In FP16 types, each channel need 2 bytes data

The memory mapping of PReLU data is described as below:

- Two bytes per element with INT16/FP16 or 1 byte per element with INT8

![](ef075538e1af84d8c6631c84087faeab_img.jpg)

Diagram illustrating the memory mapping of Per Channel PReLU Data (Case 1).

The left side shows a 3D block representing the data space, labeled  $C/32\text{Byte}$ . The block is divided into 8 channels (0 to 7). Each channel contains 8 elements (0 to 7), totaling 64 elements.

An arrow points from the data block to the right side, which shows the linear memory mapping.

The right side shows the memory layout, labeled "Memory Mapping". The memory is accessed sequentially from low memory address to high memory address.

The first 32 bytes (0 to 31) are shown, corresponding to 16 elements (0 to 15) mapped across 8 channels (2 bytes per element). The elements are listed as 0, 1, 2, 3, 4, 5, 6, 7, followed by 28, 29, 30, 31.

Fig. 22 - Memory Mapping of Per Channel PReLU Data (Case 1)

- 2 bytes per element with INT8:

![](7bed2d7c96d86bf922295a1252da52a5_img.jpg)

Diagram illustrating the memory mapping of Per Channel PReLU Data (Case 2).

The input data is represented as a 3D tensor labeled  $C/64\text{Byte}$ , with dimensions 0, 1, 2, 3, 4, 5, 6, 7 (C) and 0, 1, 2, 3, 4, 5, 6, 7 (7).

An arrow points to the memory layout, which is a 1D array of 64 bytes, indexed from low memory address (0) to high memory address (31).

The memory mapping is shown as:

| Index | Value |
|-------|-------|
| 0     | 0     |
| 1     | 1     |
| 2     | 2     |
| 3     | 3     |
| 4     | 4     |
| 5     | 5     |
| 6     | 6     |
| 7     | 7     |
| ...   | ...   |
| 28    | 28    |
| 29    | 29    |
| 30    | 30    |
| 31    | 31    |

**Memory Mapping**

Fig. 23 - Memory Mapping of Per Channel PReLU Data (Case 2)

### Batch Normalization Data Format

Batch Normalization data is another optional input data for batch normalization layers.

Each normalization data consists of two parts, one is to add onto the feature data and the other is to multiple with the result after addition.

There are two types of batch normalization data

- Per channel batch normalization data
- Per layer batch normalization data

Per channel batch normalization data is stored in memory in a continuous  $1\times 1\times C$  space. Be noted that C is in unit of channel.

- In INT8/16 types, each of the two parts of normalization data can be either 1 byte or 2 bytes, so each channel need  $2\times 1$  or  $2\times 2$  bytes data
- In FP16 types, each of the two parts of normalization data is 2 byte, so each channel need 4 bytes data

The pair data of each element are always packed together in memory. The memory mapping of data is described as below:

- Two bytes per element with INT16/FP16 or 1 byte per element with INT8

![](96a7eac66ef72bb016c280278506ac63_img.jpg)

Diagram illustrating the memory mapping of Batch Normalization Data (Case 1).

On the left, a 3D block labeled  $C/64\text{Byte}$  is shown, representing 8 elements (0 to 7) stored in 8 bytes (0 to 7). This block is mapped via an arrow to the right side, which shows the memory layout.

The right side shows the memory mapping:

- 64 bytes (low memory address): Elements 0 through 7 are stored in 8 bytes (0 through 7).
- High memory address: Elements 28 through 31 are stored in 4 bytes (28 through 31).

### Memory Mapping

Fig. 24 - Memory Mapping of Batch Normalization Data (Case 1)

- 2 bytes per element with INT8:

![](ca80b99f7e1d6e6b854f22190f2e14d8_img.jpg)

Diagram illustrating the memory mapping of Batch Normalization Data (Case 2).

On the left, a 3D block labeled  $C/128\text{Byte}$  is shown, representing 8 elements (0 to 7) stored in 16 bytes (0 to 7). This block is mapped via an arrow to the right side, which shows the memory layout.

The right side shows the memory mapping:

- 128 bytes (low memory address): Elements 0 through 7 are stored in 16 bytes (0 through 7).
- High memory address: Elements 28 through 31 are stored in 4 bytes (28 through 31).

### Memory Mapping

Fig. 25 - Memory Mapping of Batch Normalization Data (Case 2)

Per layer batch normalization data is stored in register.

Be noted that INT8 and INT16 here means the processing precision, so when the layer is running from INT16 to INT8 or INT8 to INT16 precision conversion, batch normalization data need set to processing precision which is always INT8.

### Element-Wise Data Format

Element-Wise data is another optional input data for Element-Wise layers.

Each Element-Wise data consists of just one part and either for ALU or multiplier.

There are one type of element-wise data

- Per element Element-Wise data

Per element Element-Wise data is stored in memory with size of  $W \times H \times C$ .

- In INT8/16 types, each of the two parts of element-wise data can be either 1 byte or 2 bytes, so each element need 1/2 bytes data
- In FP16 types, each of the two parts of element-wise data is 2 bytes, so each element need 2 bytes data

From algorithm perspective, element-wise employs ALU or MUL only but never both, however, DLA hardware support employ both operations for per-element operation, in this case, each element size should be x2 of description above;

The memory mapping of data is described as below:

- Two bytes per element with INT16/FP16 or 1 byte per element with INT8

![](9a19da4f7fccb96a934411c0bb5a386d_img.jpg)

Diagram illustrating the memory mapping of Element Wise Data (Case 1).

The left side shows a 3D **DATA CUBE** with dimensions W (Width), H (Height), and C (Channels). The cube contains 32 elements, indexed from 0 to 31. The indexing is row-major, starting at (0, 0, 0) and proceeding through the C dimension, then H, then W.

An arrow indicates the mapping direction from the DATA CUBE to the **Memory Mapping** on the right.

The **Memory Mapping** shows a 1D array of 32 bytes, indexed from 0 to 31. The mapping is sequential, corresponding to the element order in the DATA CUBE:

| DATA CUBE Index | Memory Mapping Index |
|-----------------|----------------------|
| 0               | 0                    |
| 1               | 1                    |
| 2               | 2                    |
| 3               | 3                    |
| 4               | 4                    |
| 5               | 5                    |
| 6               | 6                    |
| 7               | 7                    |
| 8               | 8                    |
| 9               | 9                    |
| 10              | 10                   |
| 11              | 11                   |
| 12              | 12                   |
| 13              | 13                   |
| 14              | 14                   |
| 15              | 15                   |
| 16              | 16                   |
| 17              | 17                   |
| 18              | 18                   |
| 19              | 19                   |
| 20              | 20                   |
| 21              | 21                   |
| 22              | 22                   |
| 23              | 23                   |
| 24              | 24                   |
| 25              | 25                   |
| 26              | 26                   |
| 27              | 27                   |
| 28              | 28                   |
| 29              | 29                   |
| 30              | 30                   |
| 31              | 31                   |

The memory addresses range from low memory address (0) to high memory address (31).

### DATA CUBE

Fig. 26 - Memory Mapping of Element Wise Data (Case 1)

- 2 bytes per element with INT8:

![](f630450865788387c4821c6d5760c850_img.jpg)

Diagram illustrating the memory mapping of Element Wise Data (Case 2) when 2 bytes per element with INT8.

The left side shows a 3D **DATA CUBE** with dimensions W (Width), H (Height), and C (Channels). The cube contains 64 elements, indexed from 0 to 63. The indexing is row-major, starting at (0, 0, 0) and proceeding through the C dimension, then H, then W.

An arrow indicates the mapping direction from the DATA CUBE to the **Memory Mapping** on the right.

The **Memory Mapping** shows a 1D array of 64 bytes, indexed from 0 to 63. The mapping is sequential, corresponding to the element order in the DATA CUBE:

| DATA CUBE Index | Memory Mapping Index |
|-----------------|----------------------|
| 0               | 0                    |
| 1               | 1                    |
| 2               | 2                    |
| 3               | 3                    |
| 4               | 4                    |
| 5               | 5                    |
| 6               | 6                    |
| 7               | 7                    |
| 8               | 8                    |
| 9               | 9                    |
| 10              | 10                   |
| 11              | 11                   |
| 12              | 12                   |
| 13              | 13                   |
| 14              | 14                   |
| 15              | 15                   |
| 16              | 16                   |
| 17              | 17                   |
| 18              | 18                   |
| 19              | 19                   |
| 20              | 20                   |
| 21              | 21                   |
| 22              | 22                   |
| 23              | 23                   |
| 24              | 24                   |
| 25              | 25                   |
| 26              | 26                   |
| 27              | 27                   |
| 28              | 28                   |
| 29              | 29                   |
| 30              | 30                   |
| 31              | 31                   |
| 32              | 32                   |
| 33              | 33                   |
| 34              | 34                   |
| 35              | 35                   |
| 36              | 36                   |
| 37              | 37                   |
| 38              | 38                   |
| 39              | 39                   |
| 40              | 40                   |
| 41              | 41                   |
| 42              | 42                   |
| 43              | 43                   |
| 44              | 44                   |
| 45              | 45                   |
| 46              | 46                   |
| 47              | 47                   |
| 48              | 48                   |
| 49              | 49                   |
| 50              | 50                   |
| 51              | 51                   |
| 52              | 52                   |
| 53              | 53                   |
| 54              | 54                   |
| 55              | 55                   |
| 56              | 56                   |
| 57              | 57                   |
| 58              | 58                   |
| 59              | 59                   |
| 60              | 60                   |
| 61              | 61                   |
| 62              | 62                   |
| 63              | 63                   |

The memory addresses range from low memory address (0) to high memory address (63).

#### DATA CUBE

### Memory Mapping

Fig. 27 - Memory Mapping of Element Wise Data (Case 2)

Be noted that INT8 and INT16 here means the processing precision, so when the layer is running from INT16 to INT8 or INT8 to INT16 precision conversion, Element-Wise data need set to processing precision which is always INT8.

Normally, one atom contains 1x1x32Bytes data, but it's no longer true for:

- Bias data format;
- PRELU data format;
- Batch normalization data format;
- Element-wise data format

The bytes-per-atom for those formats should be computed by:

BytesPerAtom=ElementPerAtom \* ComponentsPerElement \* BytesPerComponent

Where ElementPerAtom is decided by PROC\_PRECISION of SDP data pipeline:

| PROC_PRECISION | ElementPerAtom |
|----------------|----------------|
| INT8           | 32             |
| INT16/FP16     | 16             |

ComponentsPerElement is decided by use case (or DATA\_USE register):

| Use case                                | ComponentsPerElement |
|-----------------------------------------|----------------------|
| Bias                                    | 1                    |
| PRELU                                   | 1                    |
| BatchNormalization                      | 2                    |
| Element-wise (Only ALU or MUL enabled)  | 1                    |
| Element-wise (Both ALU/MUL are enabled) | 2                    |

BytesPerComponent is decided by precision (or DATA\_SIZE register)

| DATA_SIZE | BytesPerComponent |
|-----------|-------------------|
| ONE_BYTE  | 1                 |
| TWO_BYTE  | 2                 |

### Alignment of Start Address and Stride

Here is the conclusion of requirements of alignment:

Table 35 - Requirements of alignment

| Data format | Alignment of start address | Alignment of line stride | Alignment of surface stride | Alignment of planar/ cube stride | Alignment of data size |
|-------------|----------------------------|--------------------------|-----------------------------|----------------------------------|------------------------|
|-------------|----------------------------|--------------------------|-----------------------------|----------------------------------|------------------------|

| Data format                     | Alignment of start address | Alignment of line stride | Alignment of surface stride | Alignment of planar/ cube stride | Alignment of data size |
|---------------------------------|----------------------------|--------------------------|-----------------------------|----------------------------------|------------------------|
| Feature data cube               | 32 bytes                   | 32 bytes                 | 32 bytes                    | 32 bytes                         | NA                     |
| uncompressed/ compressed weight | 256 bytes                  | NA                       | NA                          | NA                               | 128 bytes              |
| WMB                             | 256 bytes                  | NA                       | NA                          | NA                               | 128 bytes              |
| WGS                             | 256 bytes                  | NA                       | NA                          | NA                               | 128 bytes              |
| Pitch linear pixel              | 32 bytes                   | 32 bytes                 | NA                          | NA                               | NA                     |
| Bias                            | 32 bytes                   | 32 bytes                 | 32 bytes                    | NA                               | NA                     |
| PRReLU                          | 32 bytes                   | N/A                      | N/A                         | NA                               | NA                     |
| Batch Normalization             | 32 bytes                   | NA                       | NA                          | NA                               | NA                     |
| Element-wise                    | 32 bytes                   | 32 bytes                 | NA                          | NA                               | 32 bytes               |