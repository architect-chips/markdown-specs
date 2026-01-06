

![ARM logo](2dfa6ac3edfe874f68aa0cbccaa42322_img.jpg)

ARM logo

# Arm Neon IntrinsicsReference forACLE Q3 2020

Non-Confidential

Copyright © 2014 - 2020 Arm Limited (or its affiliates).  
All rights reserved.

Issue G

IHI 0073G

## Arm Neon Intrinsics

## Reference

Copyright © 2014 - 2020 Arm Limited (or its affiliates). All rights reserved.

## Release information

## Document history

| Issue | Date              | Confidentiality  | Change               |
|-------|-------------------|------------------|----------------------|
| A     | 09 May 2014       | Non-Confidential | First release        |
| B     | 24 March 2016     | Non-Confidential | Updated for ARMv8.1  |
| C     | 30 March 2019     | Non-Confidential | VersionACLE Q1 2019. |
| D     | 30 June 2019      | Non-Confidential | VersionACLE Q2 2019. |
| E     | 30 September 2019 | Non-Confidential | VersionACLE Q3 2019  |
| F     | 30 May 2020       | Non-Confidential | VersionACLE Q2 2020  |
| G     | 30 October 2020   | Non-Confidential | VersionACLE Q3 2020  |

## Non-Confidential Proprietary Notice

This document is protected by copyright and other related rights and the practice or implementation of the information contained in this document may be protected by one or more patents or pending patent applications. No part of this document may be reproduced in any form by any means without the express prior written permission of Arm. No license, express or implied, by estoppel or otherwise to any intellectual property rights is granted by this document unless specifically stated.

Your access to the information in this document is conditional upon your acceptance that you will not use or permit others to use the information for the purposes of determining whether implementations infringe any third party patents.

THIS DOCUMENT IS PROVIDED "AS IS". ARM PROVIDES NO REPRESENTATIONS AND NO WARRANTIES, EXPRESS, IMPLIED OR STATUTORY, INCLUDING, WITHOUT LIMITATION, THE IMPLIED WARRANTIES OF MERCHANTABILITY, SATISFACTORY QUALITY, NON-INFRINGEMENT OR FITNESS FOR A PARTICULAR PURPOSE WITH RESPECT TO THE DOCUMENT. For the avoidance of doubt, Arm makes no representation with respect to, and has undertaken no analysis to identify or understand the scope and content of, patents, copyrights, trade secrets, or other rights.

This document may include technical inaccuracies or typographical errors.

TO THE EXTENT NOT PROHIBITED BY LAW, IN NO EVENT WILL ARM BE LIABLE FOR ANY DAMAGES, INCLUDING WITHOUT LIMITATION ANY DIRECT, INDIRECT, SPECIAL, INCIDENTAL, PUNITIVE, OR CONSEQUENTIAL DAMAGES, HOWEVER CAUSED AND

REGARDLESS OF THE THEORY OF LIABILITY, ARISING OUT OF ANY USE OF THIS DOCUMENT, EVEN IF ARM HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

This document consists solely of commercial items. You shall be responsible for ensuring that any use, duplication or disclosure of this document complies fully with any relevant export laws and regulations to assure that this document or any portion thereof is not exported, directly or indirectly, in violation of such export laws. Use of the word "partner" in reference to Arm's customers is not intended to create or refer to any partnership relationship with any other company. Arm may make changes to this document at any time and without notice.

If any of the provisions contained in these terms conflict with any of the provisions of any click through or signed written agreement covering this document with Arm, then the click through or signed written agreement prevails over and supersedes the conflicting provisions of these terms. This document may be translated into other languages for convenience, and you agree that if there is any conflict between the English version of this document and any translation, the terms of the English version of the Agreement shall prevail.

The Arm corporate logo and words marked with ® or ™ are registered trademarks or trademarks of Arm Limited (or its subsidiaries) in the US and/or elsewhere. All rights reserved. Other brands and names mentioned in this document may be the trademarks of their respective owners. Please follow Arm's trademark usage guidelines at <http://www.arm.com/company/policies/trademarks>.

Copyright © 2014 - 2020 Arm Limited (or its affiliates). All rights reserved.

Arm Limited. Company 02557590 registered in England.

110 Fulbourn Road, Cambridge, England CB1 9NJ.

LES-PRE-20349

## Confidentiality Status

This document is Non-Confidential. The right to use, copy and disclose this document may be subject to license restrictions in accordance with the terms of the agreement entered into by Arm and the party that Arm delivered this document to.

Unrestricted Access is an Arm internal classification.

### Product Status

The information in this document is final, that is for a developed product.

### Web Address

<http://www.arm.com>

## About this document

This document is complementary to the main Arm C Language Extensions (ACLE) specification, which can be found on [developer.arm.com](#).

## List of Intrinsics

| Intrinsic                                             | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|-------------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| int8x8_t vaddl_s8(int8x8_t a, int8x8_t b)             | a -> Vn.8B<br>b -> Vm.8B   | ADD Vd.8B,Vn.8B,Vm.8B      | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vaddq_s8(int8x16_t a, int8x16_t b)          | a -> Vn.16B<br>b -> Vm.16B | ADD Vd.16B,Vn.16B,Vm.16B   | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vaddq_s16(int16x4_t a, int16x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | ADD Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vaddq_s16(int16x8_t a, int16x8_t b)         | a -> Vn.8H<br>b -> Vm.8H   | ADD Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vaddq_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | ADD Vd.2S,Vn.2S,Vm.2S      | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vaddq_s32(int32x4_t a, int32x4_t b)         | a -> Vn.4S<br>b -> Vm.4S   | ADD Vd.4S,Vn.4S,Vm.4S      | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vaddq_s64(int64x1_t a, int64x1_t b)         | a -> Dn<br>b -> Dm         | ADD Dd,Dn,Dm               | Dd -> result     | v7/A32/A64              |
| int64x2_t vaddq_s64(int64x2_t a, int64x2_t b)         | a -> Vn.2D<br>b -> Vm.2D   | ADD Vd.2D,Vn.2D,Vm.2D      | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vaddq_u8(uint8x8_t a, uint8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | ADD Vd.8B,Vn.8B,Vm.8B      | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vaddq_u8(uint8x16_t a, uint8x16_t b)       | a -> Vn.16B<br>b -> Vm.16B | ADD Vd.16B,Vn.16B,Vm.16B   | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vaddq_u16(uint16x4_t a, uint16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | ADD Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vaddq_u16(uint16x8_t a, uint16x8_t b)      | a -> Vn.8H<br>b -> Vm.8H   | ADD Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vaddq_u32(uint32x2_t a, uint32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | ADD Vd.2S,Vn.2S,Vm.2S      | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vaddq_u32(uint32x4_t a, uint32x4_t b)      | a -> Vn.4S<br>b -> Vm.4S   | ADD Vd.4S,Vn.4S,Vm.4S      | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vaddq_u64(uint64x1_t a, uint64x1_t b)      | a -> Dn<br>b -> Dm         | ADD Dd,Dn,Dm               | Dd -> result     | v7/A32/A64              |
| uint64x2_t vaddq_u64(uint64x2_t a, uint64x2_t b)      | a -> Vn.2D<br>b -> Vm.2D   | ADD Vd.2D,Vn.2D,Vm.2D      | Vd.2D -> result  | v7/A32/A64              |
| float32x2_t vaddf_f32(float32x2_t a, float32x2_t b)   | a -> Vn.2S<br>b -> Vm.2S   | FADD Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t vaddf_f32(float32x4_t a, float32x4_t b)   | a -> Vn.4S<br>b -> Vm.4S   | FADD Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| float64x1_t vaddf_f64(float64x1_t a, float64x1_t b)   | a -> Dn<br>b -> Dm         | FADD Dd,Dn,Dm              | Dd -> result     | A64                     |
| float64x2_t vaddf_f64(float64x2_t a, float64x2_t b)   | a -> Vn.2D<br>b -> Vm.2D   | FADD Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | A64                     |
| int64_t vaddl_s64(int64_t a, int64_t b)               | a -> Dn<br>b -> Dm         | ADD Dd,Dn,Dm               | Dd -> result     | A64                     |
| uint64_t vaddl_u64(uint64_t a, uint64_t b)            | a -> Dn<br>b -> Dm         | ADD Dd,Dn,Dm               | Dd -> result     | A64                     |
| int16x8_t vaddl_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | SADDL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vaddl_s32(int32x4_t a, int32x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | SADDL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vaddl_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | SADDL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vaddl_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UADDL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vaddl_u16(uint16x4_t a, uint16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | UADDL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vaddl_u32(uint32x2_t a, uint32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | UADDL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vaddl_high_s8(int8x16_t a, int8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | SADDL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| int32x4_t vaddl_high_s16(int16x8_t a, int16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | SADDL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| int64x2_t vaddl_high_s32(int32x4_t a, int32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | SADDL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| uint16x8_t vaddl_high_u8(uint8x16_t a, uint8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | UADDL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| uint32x4_t vaddl_high_u16(uint16x8_t a, uint16x8_t b) | a -> Vn.8H<br>b -> Vm.8H   | UADDL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| uint64x2_t vaddl_high_u32(uint32x4_t a, uint32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | UADDL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |

| Intrinsic                                             | Argument Preparation       | Instruction                 | Result           | Supported Architectures |
|-------------------------------------------------------|----------------------------|-----------------------------|------------------|-------------------------|
| int16x8_t vaddw_s8(int16x8_t a, int8x8_t b)           | a -> Vn.8H<br>b -> Vm.8B   | SADDDW Vd.8H,Vn.8H,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vaddw_s16(int32x4_t a, int16x4_t b)         | a -> Vn.4S<br>b -> Vm.4H   | SADDDW Vd.4S,Vn.4S,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vaddw_s32(int64x2_t a, int32x2_t b)         | a -> Vn.2D<br>b -> Vm.2S   | SADDDW Vd.2D,Vn.2D,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vaddw_u8(uint16x8_t a, uint8x8_t b)        | a -> Vn.8H<br>b -> Vm.8B   | UADDDW Vd.8H,Vn.8H,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vaddw_u16(uint32x4_t a, uint16x4_t b)      | a -> Vn.4S<br>b -> Vm.4H   | UADDDW Vd.4S,Vn.4S,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vaddw_u32(uint64x2_t a, uint32x2_t b)      | a -> Vn.2D<br>b -> Vm.2S   | UADDDW Vd.2D,Vn.2D,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vaddw_high_s8(int16x8_t a, int8x16_t b)     | a -> Vn.8H<br>b -> Vm.16B  | SADDDW2 Vd.8H,Vn.8H,Vm.16B  | Vd.8H -> result  | A64                     |
| int32x4_t vaddw_high_s16(int32x4_t a, int16x8_t b)    | a -> Vn.4S<br>b -> Vm.8H   | SADDDW2 Vd.4S,Vn.4S,Vm.8H   | Vd.4S -> result  | A64                     |
| int64x2_t vaddw_high_s32(int64x2_t a, int32x4_t b)    | a -> Vn.2D<br>b -> Vm.4S   | SADDDW2 Vd.2D,Vn.2D,Vm.4S   | Vd.2D -> result  | A64                     |
| uint16x8_t vaddw_high_u8(uint16x8_t a, uint8x16_t b)  | a -> Vn.8H<br>b -> Vm.16B  | UADDDW2 Vd.8H,Vn.8H,Vm.16B  | Vd.8H -> result  | A64                     |
| uint32x4_t vaddw_high_u16(uint32x4_t a, uint16x8_t b) | a -> Vn.4S<br>b -> Vm.8H   | UADDDW2 Vd.4S,Vn.4S,Vm.8H   | Vd.4S -> result  | A64                     |
| uint64x2_t vaddw_high_u32(uint64x2_t a, uint32x4_t b) | a -> Vn.2D<br>b -> Vm.4S   | UADDDW2 Vd.2D,Vn.2D,Vm.4S   | Vd.2D -> result  | A64                     |
| int8x8_t vhadd_s8(int8x8_t a, int8x8_t b)             | a -> Vn.8B<br>b -> Vm.8B   | SHADD Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vhaddq_s8(int8x16_t a, int8x16_t b)         | a -> Vn.16B<br>b -> Vm.16B | SHADD Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vhadd_s16(int16x4_t a, int16x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | SHADD Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vhaddq_s16(int16x8_t a, int16x8_t b)        | a -> Vn.8H<br>b -> Vm.8H   | SHADD Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vhadd_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | SHADD Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vhaddq_s32(int32x4_t a, int32x4_t b)        | a -> Vn.4S<br>b -> Vm.4S   | SHADD Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vhadd_u8(uint8x8_t a, uint8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | UHADD Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vhaddq_u8(uint8x16_t a, uint8x16_t b)      | a -> Vn.16B<br>b -> Vm.16B | UHADD Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vhadd_u16(uint16x4_t a, uint16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | UHADD Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vhaddq_u16(uint16x8_t a, uint16x8_t b)     | a -> Vn.8H<br>b -> Vm.8H   | UHADD Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vhadd_u32(uint32x2_t a, uint32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | UHADD Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vhaddq_u32(uint32x4_t a, uint32x4_t b)     | a -> Vn.4S<br>b -> Vm.4S   | UHADD Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| int8x8_t vrhadd_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | SRHADD Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vrhaddq_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | SRHADD Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vrhadd_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | SRHADD Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vrhaddq_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | SRHADD Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vrhadd_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | SRHADD Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vrhaddq_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | SRHADD Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vrhaddq_u8(uint8x8_t a, uint8x8_t b)        | a -> Vn.8B<br>b -> Vm.8B   | URHADD Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vrhaddq_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | URHADD Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vrhaddq_u16(uint16x4_t a, uint16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | URHADD Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vrhaddq_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | URHADD Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vrhaddq_u32(uint32x2_t a, uint32x2_t b)    | a -> Vn.2S<br>b -> Vm.2S   | URHADD Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vrhaddq_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | URHADD Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|---------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| int8x8_t vqadd_s8(int8x8_t a, int8x8_t b)         | a -> Vn,8B<br>b -> Vm,8B   | SQADD Vd,8B,Vn,8B,Vm,8B    | Vd,8B -> result  | v7/A32/A64              |
| int8x16_t vqaddq_s8(int8x16_t a, int8x16_t b)     | a -> Vn,16B<br>b -> Vm,16B | SQADD Vd,16B,Vn,16B,Vm,16B | Vd,16B -> result | v7/A32/A64              |
| int16x4_t vqadd_s16(int16x4_t a, int16x4_t b)     | a -> Vn,4H<br>b -> Vm,4H   | SQADD Vd,4H,Vn,4H,Vm,4H    | Vd,4H -> result  | v7/A32/A64              |
| int16x8_t vqaddq_s16(int16x8_t a, int16x8_t b)    | a -> Vn,8H<br>b -> Vm,8H   | SQADD Vd,8H,Vn,8H,Vm,8H    | Vd,8H -> result  | v7/A32/A64              |
| int32x2_t vqadd_s32(int32x2_t a, int32x2_t b)     | a -> Vn,2S<br>b -> Vm,2S   | SQADD Vd,2S,Vn,2S,Vm,2S    | Vd,2S -> result  | v7/A32/A64              |
| int32x4_t vqaddq_s32(int32x4_t a, int32x4_t b)    | a -> Vn,4S<br>b -> Vm,4S   | SQADD Vd,4S,Vn,4S,Vm,4S    | Vd,4S -> result  | v7/A32/A64              |
| int64x1_t vqadd_s64(int64x1_t a, int64x1_t b)     | a -> Dn<br>b -> Dm         | SQADD Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| int64x2_t vqaddq_s64(int64x2_t a, int64x2_t b)    | a -> Vn,2D<br>b -> Vm,2D   | SQADD Vd,2D,Vn,2D,Vm,2D    | Vd,2D -> result  | v7/A32/A64              |
| uint8x8_t vqadd_u8(uint8x8_t a, uint8x8_t b)      | a -> Vn,8B<br>b -> Vm,8B   | UQADD Vd,8B,Vn,8B,Vm,8B    | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vqaddq_u8(uint8x16_t a, uint8x16_t b)  | a -> Vn,16B<br>b -> Vm,16B | UQADD Vd,16B,Vn,16B,Vm,16B | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vqadd_u16(uint16x4_t a, uint16x4_t b)  | a -> Vn,4H<br>b -> Vm,4H   | UQADD Vd,4H,Vn,4H,Vm,4H    | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vqaddq_u16(uint16x8_t a, uint16x8_t b) | a -> Vn,8H<br>b -> Vm,8H   | UQADD Vd,8H,Vn,8H,Vm,8H    | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vqaddq_u32(uint32x2_t a, uint32x2_t b) | a -> Vn,2S<br>b -> Vm,2S   | UQADD Vd,2S,Vn,2S,Vm,2S    | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vqaddq_u32(uint32x4_t a, uint32x4_t b) | a -> Vn,4S<br>b -> Vm,4S   | UQADD Vd,4S,Vn,4S,Vm,4S    | Vd,4S -> result  | v7/A32/A64              |
| uint64x1_t vqadd_u64(uint64x1_t a, uint64x1_t b)  | a -> Dn<br>b -> Dm         | UQADD Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| uint64x2_t vqaddq_u64(uint64x2_t a, uint64x2_t b) | a -> Vn,2D<br>b -> Vm,2D   | UQADD Vd,2D,Vn,2D,Vm,2D    | Vd,2D -> result  | v7/A32/A64              |
| int8_t vqaddb_s8(int8_t a, int8_t b)              | a -> Bn<br>b -> Bm         | SQADD Bd,Bn,Bm             | Bd -> result     | A64                     |
| int16_t vqaddh_s16(int16_t a, int16_t b)          | a -> Hn<br>b -> Hm         | SQADD Hd,Hn,Hm             | Hd -> result     | A64                     |
| int32_t vqaddq_s32(int32_t a, int32_t b)          | a -> Sn<br>b -> Sm         | SQADD Sd,Sn,Sm             | Sd -> result     | A64                     |
| int64_t vqaddq_s64(int64_t a, int64_t b)          | a -> Dn<br>b -> Dm         | SQADD Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint8_t vqaddb_u8(uint8_t a, uint8_t b)           | a -> Bn<br>b -> Bm         | UQADD Bd,Bn,Bm             | Bd -> result     | A64                     |
| uint16_t vqaddh_u16(uint16_t a, uint16_t b)       | a -> Hn<br>b -> Hm         | UQADD Hd,Hn,Hm             | Hd -> result     | A64                     |
| uint32_t vqaddq_u32(uint32_t a, uint32_t b)       | a -> Sn<br>b -> Sm         | UQADD Sd,Sn,Sm             | Sd -> result     | A64                     |
| uint64_t vqaddq_u64(uint64_t a, uint64_t b)       | a -> Dn<br>b -> Dm         | UQADD Dd,Dn,Dm             | Dd -> result     | A64                     |
| int8x8_t vqadd_s8(int8x8_t a, int8x8_t b)         | a -> Vd,8B<br>b -> Vn,8B   | SUQADD Vd,8B,Vn,8B         | Vd,8B -> result  | A64                     |
| int8x16_t vqaddq_s8(int8x16_t a, int8x16_t b)     | a -> Vd,16B<br>b -> Vn,16B | SUQADD Vd,16B,Vn,16B       | Vd,16B -> result | A64                     |
| int16x4_t vqaddq_s16(int16x4_t a, int16x4_t b)    | a -> Vd,4H<br>b -> Vn,4H   | SUQADD Vd,4H,Vn,4H         | Vd,4H -> result  | A64                     |
| int16x8_t vqaddq_s16(int16x8_t a, int16x8_t b)    | a -> Vd,8H<br>b -> Vn,8H   | SUQADD Vd,8H,Vn,8H         | Vd,8H -> result  | A64                     |
| int32x2_t vqaddq_s32(int32x2_t a, int32x2_t b)    | a -> Vd,2S<br>b -> Vn,2S   | SUQADD Vd,2S,Vn,2S         | Vd,2S -> result  | A64                     |
| int32x4_t vqaddq_s32(int32x4_t a, int32x4_t b)    | a -> Vd,4S<br>b -> Vn,4S   | SUQADD Vd,4S,Vn,4S         | Vd,4S -> result  | A64                     |
| int64x1_t vqaddq_s64(int64x1_t a, int64x1_t b)    | a -> Dd<br>b -> Dn         | SUQADD Dd,Dn               | Dd -> result     | A64                     |
| int64x2_t vqaddq_s64(int64x2_t a, int64x2_t b)    | a -> Vd,2D<br>b -> Vn,2D   | SUQADD Vd,2D,Vn,2D         | Vd,2D -> result  | A64                     |
| int8_t vqaddqb_s8(int8_t a, uint8_t b)            | a -> Bd<br>b -> Bn         | SUQADD Bd,Bn               | Bd -> result     | A64                     |
| int16_t vqaddqh_s16(int16_t a, uint16_t b)        | a -> Hd<br>b -> Hn         | SUQADD Hd,Hn               | Hd -> result     | A64                     |
| int32_t vqaddqhs_s32(int32_t a, uint32_t b)       | a -> Sd<br>b -> Sn         | SUQADD Sd,Sn               | Sd -> result     | A64                     |
| int64_t vqaddqd_s64(int64_t a, uint64_t b)        | a -> Dd<br>b -> Dn         | SUQADD Dd,Dn               | Dd -> result     | A64                     |

| Intrinsic                                                             | Argument Preparation             | Instruction                | Result           | Supported Architectures |
|-----------------------------------------------------------------------|----------------------------------|----------------------------|------------------|-------------------------|
| uint8x8_t vsqadd_u8(uint8x8_t a, int8x8_t b)                          | a->Vd,8B<br>b->Vn,8B             | USQADD Vd,8B,Vn,8B         | Vd,8B -> result  | A64                     |
| uint8x16_t vsqaddq_u8(uint8x16_t a, int8x16_t b)                      | a->Vd,16B<br>b->Vn,16B           | USQADD Vd,16B,Vn,16B       | Vd,16B -> result | A64                     |
| uint16x4_t vsqadd_u16(uint16x4_t a, int16x4_t b)                      | a->Vd,4H<br>b->Vn,4H             | USQADD Vd,4H,Vn,4H         | Vd,4H -> result  | A64                     |
| uint16x8_t vsqaddq_u16(uint16x8_t a, int16x8_t b)                     | a->Vd,8H<br>b->Vn,8H             | USQADD Vd,8H,Vn,8H         | Vd,8H -> result  | A64                     |
| uint32x2_t vsqaddq_u32(uint32x2_t a, int32x2_t b)                     | a->Vd,2S<br>b->Vn,2S             | USQADD Vd,2S,Vn,2S         | Vd,2S -> result  | A64                     |
| uint32x4_t vsqaddq_u32(uint32x4_t a, int32x4_t b)                     | a->Vd,4S<br>b->Vn,4S             | USQADD Vd,4S,Vn,4S         | Vd,4S -> result  | A64                     |
| uint64x1_t vsqaddq_u64(uint64x1_t a, int64x1_t b)                     | a->Dd<br>b->Dn                   | USQADD Dd,Dn               | Dd -> result     | A64                     |
| uint64x2_t vsqaddq_u64(uint64x2_t a, int64x2_t b)                     | a->Vd,2D<br>b->Vn,2D             | USQADD Vd,2D,Vn,2D         | Vd,2D -> result  | A64                     |
| uint8_t tvsqaddb_u8(uint8_t a, int8_t b)                              | a->Bd<br>b->Bn                   | USQADD Bd,Bn               | Bd -> result     | A64                     |
| uint16_t tvsqaddh_u16(uint16_t a, int16_t b)                          | a->Hd<br>b->Hn                   | USQADD Hd,Hn               | Hd -> result     | A64                     |
| uint32_t tvsqaddq_u32(uint32_t a, int32_t b)                          | a->Sd<br>b->Sn                   | USQADD Sd,Sn               | Sd -> result     | A64                     |
| uint64_t tvsqaddq_u64(uint64_t a, int64_t b)                          | a->Dd<br>b->Dn                   | USQADD Dd,Dn               | Dd -> result     | A64                     |
| int8x8_t tvaddhn_s16(int16x8_t a, int16x8_t b)                        | a->Vn,8H<br>b->Vm,8H             | ADDHN Vd,8B,Vn,8H,Vm,8H    | Vd,8B -> result  | V7/A32/A64              |
| int16x4_t tvaddhn_s32(int32x4_t a, int32x4_t b)                       | a->Vn,4S<br>b->Vm,4S             | ADDHN Vd,4H,Vn,4S,Vm,4S    | Vd,4H -> result  | V7/A32/A64              |
| int32x2_t tvaddhn_s64(int64x2_t a, int64x2_t b)                       | a->Vn,2D<br>b->Vm,2D             | ADDHN Vd,2S,Vn,2D,Vm,2D    | Vd,2S -> result  | V7/A32/A64              |
| uint8x8_t tvaddhn_u16(uint16x8_t a, int16x8_t b)                      | a->Vn,8H<br>b->Vm,8H             | ADDHN Vd,8B,Vn,8H,Vm,8H    | Vd,8B -> result  | V7/A32/A64              |
| uint16x4_t tvaddhn_u32(uint32x4_t a, int32x4_t b)                     | a->Vn,4S<br>b->Vm,4S             | ADDHN Vd,4H,Vn,4S,Vm,4S    | Vd,4H -> result  | V7/A32/A64              |
| uint32x2_t tvaddhn_u64(uint64x2_t a, int64x2_t b)                     | a->Vn,2D<br>b->Vm,2D             | ADDHN Vd,2S,Vn,2D,Vm,2D    | Vd,2S -> result  | V7/A32/A64              |
| int8x16_t tvaddhn_high_s16(int8x8_t r, int16x8_t a, int16x8_t b)      | r->Vd,8B<br>a->Vn,8H<br>b->Vm,8H | ADDHN2 Vd,16B,Vn,8H,Vm,8H  | Vd,16B -> result | A64                     |
| int16x8_t tvaddhn_high_s32(int16x4_t r, int32x4_t a, int32x4_t b)     | r->Vd,4H<br>a->Vn,4S<br>b->Vm,4S | ADDHN2 Vd,8H,Vn,4S,Vm,4S   | Vd,8H -> result  | A64                     |
| int32x4_t tvaddhn_high_s64(int32x2_t r, int64x2_t a, int64x2_t b)     | r->Vd,2S<br>a->Vn,2D<br>b->Vm,2D | ADDHN2 Vd,4S,Vn,2D,Vm,2D   | Vd,4S -> result  | A64                     |
| uint8x16_t tvaddhn_high_u16(uint8x8_t r, uint16x8_t a, uint16x8_t b)  | r->Vd,8B<br>a->Vn,8H<br>b->Vm,8H | ADDHN2 Vd,16B,Vn,8H,Vm,8H  | Vd,16B -> result | A64                     |
| uint16x8_t tvaddhn_high_u32(uint16x4_t r, uint32x4_t a, uint32x4_t b) | r->Vd,4H<br>a->Vn,4S<br>b->Vm,4S | ADDHN2 Vd,8H,Vn,4S,Vm,4S   | Vd,8H -> result  | A64                     |
| uint32x4_t tvaddhn_high_u64(uint32x2_t r, uint64x2_t a, uint64x2_t b) | r->Vd,2S<br>a->Vn,2D<br>b->Vm,2D | ADDHN2 Vd,4S,Vn,2D,Vm,2D   | Vd,4S -> result  | A64                     |
| int8x8_t tvaddhn_s16(int16x8_t a, int16x8_t b)                        | a->Vn,8H<br>b->Vm,8H             | RADDHN Vd,8B,Vn,8H,Vm,8H   | Vd,8B -> result  | V7/A32/A64              |
| int16x4_t tvaddhn_s32(int32x4_t a, int32x4_t b)                       | a->Vn,4S<br>b->Vm,4S             | RADDHN Vd,4H,Vn,4S,Vm,4S   | Vd,4H -> result  | V7/A32/A64              |
| int32x2_t tvaddhn_s64(int64x2_t a, int64x2_t b)                       | a->Vn,2D<br>b->Vm,2D             | RADDHN Vd,2S,Vn,2D,Vm,2D   | Vd,2S -> result  | V7/A32/A64              |
| uint8x8_t tvaddhn_u16(uint16x8_t a, uint16x8_t b)                     | a->Vn,8H<br>b->Vm,8H             | RADDHN Vd,8B,Vn,8H,Vm,8H   | Vd,8B -> result  | V7/A32/A64              |
| uint16x4_t tvaddhn_u32(uint32x4_t a, uint32x4_t b)                    | a->Vn,4S<br>b->Vm,4S             | RADDHN Vd,4H,Vn,4S,Vm,4S   | Vd,4H -> result  | V7/A32/A64              |
| uint32x2_t tvaddhn_u64(uint64x2_t a, uint64x2_t b)                    | a->Vn,2D<br>b->Vm,2D             | RADDHN Vd,2S,Vn,2D,Vm,2D   | Vd,2S -> result  | V7/A32/A64              |
| int8x16_t tvaddhn_high_s16(int8x8_t r, int16x8_t a, int16x8_t b)      | r->Vd,8B<br>a->Vn,8H<br>b->Vm,8H | RADDHN2 Vd,16B,Vn,8H,Vm,8H | Vd,16B -> result | A64                     |
| int16x8_t tvaddhn_high_s32(int16x4_t r, int32x4_t a, int32x4_t b)     | r->Vd,4H<br>a->Vn,4S<br>b->Vm,4S | RADDHN2 Vd,8H,Vn,4S,Vm,4S  | Vd,8H -> result  | A64                     |

| Intrinsic                                                                 | Argument Preparation                       | Instruction                   | Result           | Supported Architectures |
|---------------------------------------------------------------------------|--------------------------------------------|-------------------------------|------------------|-------------------------|
| int32x4_t vraddhn_high_s64(int32x2_t r, int64x2_t a, int64x2_t b)         | r -> Vd.2S<br>a -> Vn.2D<br>b -> Vm.2D     | RADDHN2 Vd.4S,Vn.2D,Vm.2D     | Vd.4S -> result  | A64                     |
| uint8x16_t vraddhn_high_u16(uint8x8_t r, uint16x8_t a, uint16x8_t b)      | r -> Vd.8B<br>a -> Vn.8H<br>b -> Vm.8H     | RADDHN2 Vd.16B,Vn.8H,Vm.8H    | Vd.16B -> result | A64                     |
| uint16x8_t vraddhn_high_u32(uint16x4_t r, uint32x4_t a, uint32x4_t b)     | r -> Vd.4H<br>a -> Vn.4S<br>b -> Vm.4S     | RADDHN2 Vd.8H,Vn.4S,Vm.4S     | Vd.8H -> result  | A64                     |
| uint32x4_t vraddhn_high_u64(uint32x2_t r, uint64x2_t a, uint64x2_t b)     | r -> Vd.2S<br>a -> Vn.2D<br>b -> Vm.2D     | RADDHN2 Vd.4S,Vn.2D,Vm.2D     | Vd.4S -> result  | A64                     |
| int8x8_t vmul_s8(int8x8_t a, int8x8_t b)                                  | a -> Vn.8B<br>b -> Vm.8B                   | MUL Vd.8B,Vn.8B,Vm.8B         | Vd.8B -> result  | V7/A32/A64              |
| int8x16_t vmul_s8(int8x16_t a, int8x16_t b)                               | a -> Vn.16B<br>b -> Vm.16B                 | MUL Vd.16B,Vn.16B,Vm.16B      | Vd.16B -> result | V7/A32/A64              |
| int16x4_t vmul_s16(int16x4_t a, int16x4_t b)                              | a -> Vn.4H<br>b -> Vm.4H                   | MUL Vd.4H,Vn.4H,Vm.4H         | Vd.4H -> result  | V7/A32/A64              |
| int16x8_t vmul_s16(int16x8_t a, int16x8_t b)                              | a -> Vn.8H<br>b -> Vm.8H                   | MUL Vd.8H,Vn.8H,Vm.8H         | Vd.8H -> result  | V7/A32/A64              |
| int32x2_t vmul_s32(int32x2_t a, int32x2_t b)                              | a -> Vn.2S<br>b -> Vm.2S                   | MUL Vd.2S,Vn.2S,Vm.2S         | Vd.2S -> result  | V7/A32/A64              |
| int32x4_t vmul_s32(int32x4_t a, int32x4_t b)                              | a -> Vn.4S<br>b -> Vm.4S                   | MUL Vd.4S,Vn.4S,Vm.4S         | Vd.4S -> result  | V7/A32/A64              |
| uint8x8_t vmul_u8(uint8x8_t a, uint8x8_t b)                               | a -> Vn.8B<br>b -> Vm.8B                   | MUL Vd.8B,Vn.8B,Vm.8B         | Vd.8B -> result  | V7/A32/A64              |
| uint8x16_t vmul_u8(uint8x16_t a, uint8x16_t b)                            | a -> Vn.16B<br>b -> Vm.16B                 | MUL Vd.16B,Vn.16B,Vm.16B      | Vd.16B -> result | V7/A32/A64              |
| uint16x4_t vmul_u16(uint16x4_t a, uint16x4_t b)                           | a -> Vn.4H<br>b -> Vm.4H                   | MUL Vd.4H,Vn.4H,Vm.4H         | Vd.4H -> result  | V7/A32/A64              |
| uint16x8_t vmul_u16(uint16x8_t a, uint16x8_t b)                           | a -> Vn.8H<br>b -> Vm.8H                   | MUL Vd.8H,Vn.8H,Vm.8H         | Vd.8H -> result  | V7/A32/A64              |
| uint32x2_t vmul_u32(uint32x2_t a, uint32x2_t b)                           | a -> Vn.2S<br>b -> Vm.2S                   | MUL Vd.2S,Vn.2S,Vm.2S         | Vd.2S -> result  | V7/A32/A64              |
| uint32x4_t vmul_u32(uint32x4_t a, uint32x4_t b)                           | a -> Vn.4S<br>b -> Vm.4S                   | MUL Vd.4S,Vn.4S,Vm.4S         | Vd.4S -> result  | V7/A32/A64              |
| float32x2_t vmul_f32(float32x2_t a, float32x2_t b)                        | a -> Vn.2S<br>b -> Vm.2S                   | FMUL Vd.2S,Vn.2S,Vm.2S        | Vd.2S -> result  | V7/A32/A64              |
| float32x4_t vmul_f32(float32x4_t a, float32x4_t b)                        | a -> Vn.4S<br>b -> Vm.4S                   | FMUL Vd.4S,Vn.4S,Vm.4S        | Vd.4S -> result  | V7/A32/A64              |
| poly8x8_t vmul_p8(poly8x8_t a, poly8x8_t b)                               | a -> Vn.8B<br>b -> Vm.8B                   | PMUL Vd.8B,Vn.8B,Vm.8B        | Vd.8B -> result  | V7/A32/A64              |
| poly8x16_t vmul_p8(poly8x16_t a, poly8x16_t b)                            | a -> Vn.16B<br>b -> Vm.16B                 | PMUL Vd.16B,Vn.16B,Vm.16B     | Vd.16B -> result | V7/A32/A64              |
| float64x1_t vmul_f64(float64x1_t a, float64x1_t b)                        | a -> Dn<br>b -> Dm                         | FMUL Dd,Dn,Dm                 | Dd -> result     | A64                     |
| float64x2_t vmul_f64(float64x2_t a, float64x2_t b)                        | a -> Vn.2D<br>b -> Vm.2D                   | FMUL Vd.2D,Vn.2D,Vm.2D        | Vd.2D -> result  | A64                     |
| float32x2_t vmulx_f32(float32x2_t a, float32x2_t b)                       | a -> Vn.2S<br>b -> Vm.2S                   | FMULX Vd.2S,Vn.2S,Vm.2S       | Vd.2S -> result  | A64                     |
| float32x4_t vmulx_f32(float32x4_t a, float32x4_t b)                       | a -> Vn.4S<br>b -> Vm.4S                   | FMULX Vd.4S,Vn.4S,Vm.4S       | Vd.4S -> result  | A64                     |
| float64x1_t vmulx_f64(float64x1_t a, float64x1_t b)                       | a -> Dn<br>b -> Dm                         | FMULX Dd,Dn,Dm                | Dd -> result     | A64                     |
| float64x2_t vmulx_f64(float64x2_t a, float64x2_t b)                       | a -> Vn.2D<br>b -> Vm.2D                   | FMULX Vd.2D,Vn.2D,Vm.2D       | Vd.2D -> result  | A64                     |
| float32_t vmulxs_f32(float32_t a, float32_t b)                            | a -> Sn<br>b -> Sm                         | FMULX Sd,Sn,Sm                | Sd -> result     | A64                     |
| float64_t vmulxd_f64(float64_t a, float64_t b)                            | a -> Dn<br>b -> Dm                         | FMULX Dd,Dn,Dm                | Dd -> result     | A64                     |
| float32x2_t vmulx_lane_f32(float32x2_t a, float32x2_t v, const int lane)  | a -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | FMULX Vd.2S,Vn.2S,Vm.\$[lane] | Vd.2S -> result  | A64                     |
| float32x4_t vmulxq_lane_f32(float32x4_t a, float32x2_t v, const int lane) | a -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | FMULX Vd.4S,Vn.4S,Vm.\$[lane] | Vd.4S -> result  | A64                     |
| float64x1_t vmulx_lane_f64(float64x1_t a, float64x1_t v, const int lane)  | a -> Dn<br>v -> Vm.1D<br>lane == 0         | FMULX Dd,Dn,Vm.D[lane]        | Dd -> result     | A64                     |

| Intrinsic                                                                  | Argument Preparation                | Instruction                  | Result         | Supported Architectures |
|----------------------------------------------------------------------------|-------------------------------------|------------------------------|----------------|-------------------------|
| float64x2_t vmulq_lane_f64(float64x2_t a, float64x1_t v, const int lane)   | a->Vn.2D<br>v->Vm.1D<br>lane==0     | FMULX Vd.2D,Vn.2D,Vm.D[lane] | Vd.2D->result  | A64                     |
| float32_t vmulxs_lane_f32(float32_t a, float32x2_t v, const int lane)      | a->Sn<br>v->Vm.2S<br>0<=lane<=1     | FMULX Sd,Sn,Vm.S[lane]       | Sd->result     | A64                     |
| float64_t vmulxd_lane_f64(float64_t a, float64x1_t v, const int lane)      | a->Dn<br>v->Vm.1D<br>lane==0        | FMULX Dd,Dn,Vm.D[lane]       | Dd->result     | A64                     |
| float32x2_t vmulx_laneq_f32(float32x2_t a, float32x4_t v, const int lane)  | a->Vn.2S<br>v->Vm.4S<br>0<=lane<=3  | FMULX Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S->result  | A64                     |
| float32x4_t vmulxq_laneq_f32(float32x4_t a, float32x4_t v, const int lane) | a->Vn.4S<br>v->Vm.4S<br>0<=lane<=3  | FMULX Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S->result  | A64                     |
| float64x1_t vmulx_laneq_f64(float64x1_t a, float64x2_t v, const int lane)  | a->Dn<br>v->Vm.2D<br>0<=lane<=1     | FMULX Dd,Dn,Vm.D[lane]       | Dd->result     | A64                     |
| float64x2_t vmulxq_laneq_f64(float64x2_t a, float64x2_t v, const int lane) | a->Vn.2D<br>v->Vm.2D<br>0<=lane<=1  | FMULX Vd.2D,Vn.2D,Vm.D[lane] | Vd.2D->result  | A64                     |
| float32_t vmulxs_laneq_f32(float32_t a, float32x4_t v, const int lane)     | a->Sn<br>v->Vm.4S<br>0<=lane<=3     | FMULX Sd,Sn,Vm.S[lane]       | Sd->result     | A64                     |
| float64_t vmulxd_laneq_f64(float64_t a, float64x2_t v, const int lane)     | a->Dn<br>v->Vm.2D<br>0<=lane<=1     | FMULX Dd,Dn,Vm.D[lane]       | Dd->result     | A64                     |
| float32x2_t vdiv_f32(float32x2_t a, float32x2_t b)                         | a->Vn.2S<br>b->Vm.2S                | FDIV Vd.2S,Vn.2S,Vm.2S       | Vd.2S->result  | A64                     |
| float32x4_t vdivq_f32(float32x4_t a, float32x4_t b)                        | a->Vn.4S<br>b->Vm.4S                | FDIV Vd.4S,Vn.4S,Vm.4S       | Vd.4S->result  | A64                     |
| float64x1_t vdiv_f64(float64x1_t a, float64x1_t b)                         | a->Dn<br>b->Dm                      | FDIV Dd,Dn,Dm                | Dd->result     | A64                     |
| float64x2_t vdivq_f64(float64x2_t a, float64x2_t b)                        | a->Vn.2D<br>b->Vm.2D                | FDIV Vd.2D,Vn.2D,Vm.2D       | Vd.2D->result  | A64                     |
| int8x8_t vmla_s8(int8x8_t a, int8x8_t b, int8x8_t c)                       | a->Vd.8B<br>b->Vn.8B<br>c->Vm.8B    | MLA Vd.8B,Vn.8B,Vm.8B        | Vd.8B->result  | v7/A32/A64              |
| int8x16_t vmlaq_s8(int8x16_t a, int8x16_t b, int8x16_t c)                  | a->Vd.16B<br>b->Vn.16B<br>c->Vm.16B | MLA Vd.16B,Vn.16B,Vm.16B     | Vd.16B->result | v7/A32/A64              |
| int16x4_t vmla_s16(int16x4_t a, int16x4_t b, int16x4_t c)                  | a->Vd.4H<br>b->Vn.4H<br>c->Vm.4H    | MLA Vd.4H,Vn.4H,Vm.4H        | Vd.4H->result  | v7/A32/A64              |
| int16x8_t vmlaq_s16(int16x8_t a, int16x8_t b, int16x8_t c)                 | a->Vd.8H<br>b->Vn.8H<br>c->Vm.8H    | MLA Vd.8H,Vn.8H,Vm.8H        | Vd.8H->result  | v7/A32/A64              |
| int32x2_t vmla_s32(int32x2_t a, int32x2_t b, int32x2_t c)                  | a->Vd.2S<br>b->Vn.2S<br>c->Vm.2S    | MLA Vd.2S,Vn.2S,Vm.2S        | Vd.2S->result  | v7/A32/A64              |
| int32x4_t vmlaq_s32(int32x4_t a, int32x4_t b, int32x4_t c)                 | a->Vd.4S<br>b->Vn.4S<br>c->Vm.4S    | MLA Vd.4S,Vn.4S,Vm.4S        | Vd.4S->result  | v7/A32/A64              |
| uint8x8_t vmla_u8(uint8x8_t a, uint8x8_t b, uint8x8_t c)                   | a->Vd.8B<br>b->Vn.8B<br>c->Vm.8B    | MLA Vd.8B,Vn.8B,Vm.8B        | Vd.8B->result  | v7/A32/A64              |
| uint8x16_t vmlaq_u8(uint8x16_t a, uint8x16_t b, uint8x16_t c)              | a->Vd.16B<br>b->Vn.16B<br>c->Vm.16B | MLA Vd.16B,Vn.16B,Vm.16B     | Vd.16B->result | v7/A32/A64              |
| uint16x4_t vmla_u16(uint16x4_t a, uint16x4_t b, uint16x4_t c)              | a->Vd.4H<br>b->Vn.4H<br>c->Vm.4H    | MLA Vd.4H,Vn.4H,Vm.4H        | Vd.4H->result  | v7/A32/A64              |
| uint16x8_t vmlaq_u16(uint16x8_t a, uint16x8_t b, uint16x8_t c)             | a->Vd.8H<br>b->Vn.8H<br>c->Vm.8H    | MLA Vd.8H,Vn.8H,Vm.8H        | Vd.8H->result  | v7/A32/A64              |

| Intrinsic                                                           | Argument Preparation                      | Instruction                                     | Result           | Supported Architectures |
|---------------------------------------------------------------------|-------------------------------------------|-------------------------------------------------|------------------|-------------------------|
| uint32x2_t vmla_u32(uint32x2_t a, uint32x2_t b, uint32x2_t c)       | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S    | MLA Vd.2S,Vn.2S,Vm.2S                           | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vmlaq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)      | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S    | MLA Vd.4S,Vn.4S,Vm.4S                           | Vd.4S -> result  | v7/A32/A64              |
| float32x2_t vmla_f32(float32x2_t a, float32x2_t b, float32x2_t c)   | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] + [b[i] * c[i]] for i = 0 to 1 | N/A -> result    | v7/A32/A64              |
| float32x4_t vmlaq_f32(float32x4_t a, float32x4_t b, float32x4_t c)  | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] + [b[i] * c[i]] for i = 0 to 3 | N/A -> result    | v7/A32/A64              |
| float64x1_t vmla_f64(float64x1_t a, float64x1_t b, float64x1_t c)   | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] + [b[i] * c[i]] for i = 0      | N/A -> result    | A64                     |
| float64x2_t vmlaq_f64(float64x2_t a, float64x2_t b, float64x2_t c)  | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] + [b[i] * c[i]] for i = 0 to 1 | N/A -> result    | A64                     |
| int16x8_t vmlal_s8(int16x8_t a, int8x8_t b, int8x8_t c)             | a -> Vd.8H<br>b -> Vn.8B<br>c -> Vm.8B    | SMLAL Vd.8H,Vn.8B,Vm.8B                         | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vmlal_s16(int32x4_t a, int16x4_t b, int16x4_t c)          | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H    | SMLAL Vd.4S,Vn.4H,Vm.4H                         | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vmlal_s32(int64x2_t a, int32x2_t b, int32x2_t c)          | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S    | SMLAL Vd.2D,Vn.2S,Vm.2S                         | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vmlal_u8(uint16x8_t a, uint8x8_t b, uint8x8_t c)         | a -> Vd.8H<br>b -> Vn.8B<br>c -> Vm.8B    | UMLAL Vd.8H,Vn.8B,Vm.8B                         | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vmlal_u16(uint32x4_t a, uint16x4_t b, uint16x4_t c)      | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H    | UMLAL Vd.4S,Vn.4H,Vm.4H                         | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vmlal_u32(uint64x2_t a, uint32x2_t b, uint32x2_t c)      | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S    | UMLAL Vd.2D,Vn.2S,Vm.2S                         | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vmlal_high_s8(int16x8_t a, int8x16_t b, int8x16_t c)      | a -> Vd.8H<br>b -> Vn.16B<br>c -> Vm.16B  | SMLAL2 Vd.8H,Vn.16B,Vm.16B                      | Vd.8H -> result  | A64                     |
| int32x4_t vmlal_high_s16(int32x4_t a, int16x8_t b, int16x8_t c)     | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H    | SMLAL2 Vd.4S,Vn.8H,Vm.8H                        | Vd.4S -> result  | A64                     |
| int64x2_t vmlal_high_s32(int64x2_t a, int32x4_t b, int32x4_t c)     | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S    | SMLAL2 Vd.2D,Vn.4S,Vm.4S                        | Vd.2D -> result  | A64                     |
| uint16x8_t vmlal_high_u8(uint16x8_t a, uint8x16_t b, uint8x16_t c)  | a -> Vd.8H<br>b -> Vn.16B<br>c -> Vm.16B  | UMLAL2 Vd.8H,Vn.16B,Vm.16B                      | Vd.8H -> result  | A64                     |
| uint32x4_t vmlal_high_u16(uint32x4_t a, uint16x8_t b, uint16x8_t c) | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H    | UMLAL2 Vd.4S,Vn.8H,Vm.8H                        | Vd.4S -> result  | A64                     |
| uint64x2_t vmlal_high_u32(uint64x2_t a, uint32x4_t b, uint32x4_t c) | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S    | UMLAL2 Vd.2D,Vn.4S,Vm.4S                        | Vd.2D -> result  | A64                     |
| int8x8_t vmls_s8(int8x8_t a, int8x8_t b, int8x8_t c)                | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | MLS Vd.8B,Vn.8B,Vm.8B                           | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vmlsq_s8(int8x16_t a, int8x16_t b, int8x16_t c)           | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | MLS Vd.16B,Vn.16B,Vm.16B                        | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vmls_s16(int16x4_t a, int16x4_t b, int16x4_t c)           | a -> Vd.4H<br>b -> Vn.4H<br>c -> Vm.4H    | MLS Vd.4H,Vn.4H,Vm.4H                           | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vmlsq_s16(int16x8_t a, int16x8_t b, int16x8_t c)          | a -> Vd.8H<br>b -> Vn.8H<br>c -> Vm.8H    | MLS Vd.8H,Vn.8H,Vm.8H                           | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vmls_s32(int32x2_t a, int32x2_t b, int32x2_t c)           | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S    | MLS Vd.2S,Vn.2S,Vm.2S                           | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vmlsq_s32(int32x4_t a, int32x4_t b, int32x4_t c)          | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S    | MLS Vd.4S,Vn.4S,Vm.4S                           | Vd.4S -> result  | v7/A32/A64              |

| Intrinsic                                                           | Argument Preparation                      | Instruction                                     | Result           | Supported Architectures |
|---------------------------------------------------------------------|-------------------------------------------|-------------------------------------------------|------------------|-------------------------|
| uint8x8_t vmuls_u8(uint8x8_t a, uint8x8_t b, uint8x8_t c)           | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | MLS Vd.8B,Vn.8B,Vm.8B                           | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vmulsq_u8(uint8x16_t a, uint8x16_t b, uint8x16_t c)      | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | MLS Vd.16B,Vn.16B,Vm.16B                        | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vmuls_u16(uint16x4_t a, uint16x4_t b, uint16x4_t c)      | a -> Vd.4H<br>b -> Vn.4H<br>c -> Vm.4H    | MLS Vd.4H,Vn.4H,Vm.4H                           | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vmulsq_u16(uint16x8_t a, uint16x8_t b, uint16x8_t c)     | a -> Vd.8H<br>b -> Vn.8H<br>c -> Vm.8H    | MLS Vd.8H,Vn.8H,Vm.8H                           | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vmuls_u32(uint32x2_t a, uint32x2_t b, uint32x2_t c)      | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S    | MLS Vd.2S,Vn.2S,Vm.2S                           | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vmulsq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)     | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S    | MLS Vd.4S,Vn.4S,Vm.4S                           | Vd.4S -> result  | v7/A32/A64              |
| float32x2_t vmuls_f32(float32x2_t a, float32x2_t b, float32x2_t c)  | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] - [b[i] * c[i]] for i = 0 to 1 | N/A -> result    | v7/A32/A64              |
| float32x4_t vmulsq_f32(float32x4_t a, float32x4_t b, float32x4_t c) | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] - [b[i] * c[i]] for i = 0 to 3 | N/A -> result    | v7/A32/A64              |
| float64x1_t vmuls_f64(float64x1_t a, float64x1_t b, float64x1_t c)  | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] - [b[i] * c[i]] for i = 0      | N/A -> result    | A64                     |
| float64x2_t vmulsq_f64(float64x2_t a, float64x2_t b, float64x2_t c) | a -> N/A<br>b -> N/A<br>c -> N/A          | RESULT[i] = a[i] - [b[i] * c[i]] for i = 0 to 1 | N/A -> result    | A64                     |
| int16x8_t vmvsl_s8(int16x8_t a, int8x8_t b, int8x8_t c)             | a -> Vd.8H<br>b -> Vn.8B<br>c -> Vm.8B    | SMLSL Vd.8H,Vn.8B,Vm.8B                         | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vmvsl_s16(int32x4_t a, int16x4_t b, int16x4_t c)          | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H    | SMLSL Vd.4S,Vn.4H,Vm.4H                         | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vmvsl_s32(int64x2_t a, int32x2_t b, int32x2_t c)          | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S    | SMLSL Vd.2D,Vn.2S,Vm.2S                         | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vmvsl_u8(uint16x8_t a, uint8x8_t b, uint8x8_t c)         | a -> Vd.8H<br>b -> Vn.8B<br>c -> Vm.8B    | UMLSL Vd.8H,Vn.8B,Vm.8B                         | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vmvsl_u16(uint32x4_t a, uint16x4_t b, uint16x4_t c)      | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H    | UMLSL Vd.4S,Vn.4H,Vm.4H                         | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vmvsl_u32(uint64x2_t a, uint32x2_t b, uint32x2_t c)      | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S    | UMLSL Vd.2D,Vn.2S,Vm.2S                         | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vmvsl_high_s8(int16x8_t a, int8x16_t b, int8x16_t c)      | a -> Vd.8H<br>b -> Vn.16B<br>c -> Vm.16B  | SMLSL2 Vd.8H,Vn.16B,Vm.16B                      | Vd.8H -> result  | A64                     |
| int32x4_t vmvsl_high_s16(int32x4_t a, int16x8_t b, int16x8_t c)     | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H    | SMLSL2 Vd.4S,Vn.8H,Vm.8H                        | Vd.4S -> result  | A64                     |
| int64x2_t vmvsl_high_s32(int64x2_t a, int32x4_t b, int32x4_t c)     | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S    | SMLSL2 Vd.2D,Vn.4S,Vm.4S                        | Vd.2D -> result  | A64                     |
| uint16x8_t vmvsl_high_u8(uint16x8_t a, uint8x16_t b, uint8x16_t c)  | a -> Vd.8H<br>b -> Vn.16B<br>c -> Vm.16B  | UMLSL2 Vd.8H,Vn.16B,Vm.16B                      | Vd.8H -> result  | A64                     |
| uint32x4_t vmvsl_high_u16(uint32x4_t a, uint16x8_t b, uint16x8_t c) | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H    | UMLSL2 Vd.4S,Vn.8H,Vm.8H                        | Vd.4S -> result  | A64                     |
| uint64x2_t vmvsl_high_u32(uint64x2_t a, uint32x4_t b, uint32x4_t c) | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S    | UMLSL2 Vd.2D,Vn.4S,Vm.4S                        | Vd.2D -> result  | A64                     |
| float32x2_t vfma_f32(float32x2_t a, float32x2_t b, float32x2_t c)   | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S    | FMLA Vd.2S,Vn.2S,Vm.2S                          | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t vfmaq_f32(float32x4_t a, float32x4_t b, float32x4_t c)  | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S    | FMLA Vd.4S,Vn.4S,Vm.4S                          | Vd.4S -> result  | v7/A32/A64              |

| Intrinsic                                                                               | Argument Preparation                               | Instruction                  | Result         | Supported Architectures |
|-----------------------------------------------------------------------------------------|----------------------------------------------------|------------------------------|----------------|-------------------------|
| float64x1_t vfmq_f64(float64x1_t a, float64x1_t b, float64x1_t c)                       | a->Da<br>b->Dn<br>c->Dm                            | FMAADD Dd,Dn,Dm,Da           | Dd-> result    | A64                     |
| float64x2_t vfmq_f64(float64x2_t a, float64x2_t b, float64x2_t c)                       | a->Vd.2D<br>b->Vn.2D<br>c->Vm.2D                   | FMLA Vd.2D,Vn.2D,Vm.2D       | Vd.2D-> result | A64                     |
| float32x2_t vfmq_lane_f32(float32x2_t a, float32x2_t b, float32x2_t v, const int lane)  | a->Vd.2S<br>b->Vn.2S<br>v->Vm.2S<br>0 <= lane <= 1 | FMLA Vd.2S,Vn.2S,Vm.\$[lane] | Vd.2S-> result | A64                     |
| float32x4_t vfmq_lane_f32(float32x4_t a, float32x4_t b, float32x4_t v, const int lane)  | a->Vd.4S<br>b->Vn.4S<br>v->Vm.2S<br>0 <= lane <= 1 | FMLA Vd.4S,Vn.4S,Vm.\$[lane] | Vd.4S-> result | A64                     |
| float64x1_t vfmq_lane_f64(float64x1_t a, float64x1_t b, float64x1_t v, const int lane)  | a->Dd<br>b->Dn<br>v->Vm.1D<br>lane == 0            | FMLA Dd,Dn,Vm.D[lane]        | Dd-> result    | A64                     |
| float64x2_t vfmq_lane_f64(float64x2_t a, float64x2_t b, float64x2_t v, const int lane)  | a->Vd.2D<br>b->Vn.2D<br>v->Vm.1D<br>lane == 0      | FMLA Vd.2D,Vn.2D,Vm.D[lane]  | Vd.2D-> result | A64                     |
| float32_t vfmq_lane_f32(float32_t a, float32_t b, float32x2_t v, const int lane)        | a->Sd<br>b->Sn<br>v->Vm.2S<br>0 <= lane <= 1       | FMLA Sd,Sn,Vm.\$[lane]       | Sd-> result    | A64                     |
| float64_t vfmad_lane_f64(float64_t a, float64_t b, float64x1_t v, const int lane)       | a->Dd<br>b->Dn<br>v->Vm.1D<br>lane == 0            | FMLA Dd,Dn,Vm.D[lane]        | Dd-> result    | A64                     |
| float32x2_t vfmq_laneq_f32(float32x2_t a, float32x2_t b, float32x4_t v, const int lane) | a->Vd.2S<br>b->Vn.2S<br>v->Vm.4S<br>0 <= lane <= 3 | FMLA Vd.2S,Vn.2S,Vm.\$[lane] | Vd.2S-> result | A64                     |
| float32x4_t vfmq_laneq_f32(float32x4_t a, float32x4_t b, float32x4_t v, const int lane) | a->Vd.4S<br>b->Vn.4S<br>v->Vm.4S<br>0 <= lane <= 3 | FMLA Vd.4S,Vn.4S,Vm.\$[lane] | Vd.4S-> result | A64                     |
| float64x1_t vfmq_laneq_f64(float64x1_t a, float64x1_t b, float64x2_t v, const int lane) | a->Dd<br>b->Dn<br>v->Vm.2D<br>0 <= lane <= 1       | FMLA Dd,Dn,Vm.D[lane]        | Dd-> result    | A64                     |
| float64x2_t vfmq_laneq_f64(float64x2_t a, float64x2_t b, float64x2_t v, const int lane) | a->Vd.2D<br>b->Vn.2D<br>v->Vm.2D<br>0 <= lane <= 1 | FMLA Vd.2D,Vn.2D,Vm.D[lane]  | Vd.2D-> result | A64                     |
| float32_t vfmq_laneq_f32(float32_t a, float32_t b, float32x4_t v, const int lane)       | a->Sd<br>b->Sn<br>v->Vm.4S<br>0 <= lane <= 3       | FMLA Sd,Sn,Vm.\$[lane]       | Sd-> result    | A64                     |
| float64_t vfmad_laneq_f64(float64_t a, float64_t b, float64x2_t v, const int lane)      | a->Dd<br>b->Dn<br>v->Vm.2D<br>0 <= lane <= 1       | FMLA Dd,Dn,Vm.D[lane]        | Dd-> result    | A64                     |
| float32x2_t vfmq_f32(float32x2_t a, float32x2_t b, float32x2_t c)                       | a->Vd.2S<br>b->Vn.2S<br>c->Vm.2S                   | FMLA Vd.2S,Vn.2S,Vm.2S       | Vd.2S-> result | v7/A32/A64              |
| float32x4_t vfmq_f32(float32x4_t a, float32x4_t b, float32x4_t c)                       | a->Vd.4S<br>b->Vn.4S<br>c->Vm.4S                   | FMLA Vd.4S,Vn.4S,Vm.4S       | Vd.4S-> result | v7/A32/A64              |
| float64x1_t vfmq_f64(float64x1_t a, float64x1_t b, float64x1_t c)                       | a->Da<br>b->Dn<br>c->Dm                            | FMSUB Dd,Dn,Dm,Da            | Dd-> result    | A64                     |

| Intrinsic                                                                               | Argument Preparation                                     | Instruction                 | Result          | Supported Architectures |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------|-----------------------------|-----------------|-------------------------|
| float64x2_t vfmsq_f64(float64x2_t a, float64x2_t b, float64x2_t c)                      | a -> Vd.2D<br>b -> Vn.2D<br>c -> Vm.2D                   | FMLS Vd.2D,Vn.2D,Vm.2D      | Vd.2D -> result | A64                     |
| float32x2_t vfms_lane_f32(float32x2_t a, float32x2_t b, float32x2_t v, const int lane)  | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | FMLS Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | A64                     |
| float32x4_t vfmsq_lane_f32(float32x4_t a, float32x4_t b, float32x2_t v, const int lane) | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | FMLS Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | A64                     |
| float64x1_t vfms_lane_f64(float64x1_t a, float64x1_t b, float64x1_t v, const int lane)  | a -> Dd<br>b -> Dn<br>v -> Vm.1D<br>lane == 0            | FMLS Dd,Dn,Vm.D[lane]       | Dd -> result    | A64                     |
| float64x2_t vfmsq_lane_f64(float64x2_t a, float64x2_t b, float64x1_t v, const int lane) | a -> Vd.2D<br>b -> Vn.2D<br>v -> Vm.1D<br>lane == 0      | FMLS Vd.2D,Vn.2D,Vm.D[lane] | Vd.2D -> result | A64                     |
| float32_t vfmsq_lane_f32(float32_t a, float32_t b, float32x2_t v, const int lane)       | a -> Sd<br>b -> Sn<br>v -> Vm.2S<br>0 <= lane <= 1       | FMLS Sd,Sn,Vm.S[lane]       | Sd -> result    | A64                     |
| float64_t vfmsq_lane_f64(float64_t a, float64_t b, float64x1_t v, const int lane)       | a -> Dd<br>b -> Dn<br>v -> Vm.1D<br>lane == 0            | FMLS Dd,Dn,Vm.D[lane]       | Dd -> result    | A64                     |
| float32x2_t vfms_lane_f32(float32x2_t a, float32x2_t b, float32x4_t v, const int lane)  | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | FMLS Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | A64                     |
| float32x4_t vfmsq_lane_f32(float32x4_t a, float32x4_t b, float32x4_t v, const int lane) | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | FMLS Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | A64                     |
| float64x1_t vfms_lane_f64(float64x1_t a, float64x1_t b, float64x2_t v, const int lane)  | a -> Dd<br>b -> Dn<br>v -> Vm.2D<br>0 <= lane <= 1       | FMLS Dd,Dn,Vm.D[lane]       | Dd -> result    | A64                     |
| float64x2_t vfmsq_lane_f64(float64x2_t a, float64x2_t b, float64x2_t v, const int lane) | a -> Vd.2D<br>b -> Vn.2D<br>v -> Vm.2D<br>0 <= lane <= 1 | FMLS Vd.2D,Vn.2D,Vm.D[lane] | Vd.2D -> result | A64                     |
| float32_t vfmsq_lane_f32(float32_t a, float32_t b, float32x4_t v, const int lane)       | a -> Sd<br>b -> Sn<br>v -> Vm.4S<br>0 <= lane <= 3       | FMLS Sd,Sn,Vm.S[lane]       | Sd -> result    | A64                     |
| float64_t vfmsq_lane_f64(float64_t a, float64_t b, float64x2_t v, const int lane)       | a -> Dd<br>b -> Dn<br>v -> Vm.2D<br>0 <= lane <= 1       | FMLS Dd,Dn,Vm.D[lane]       | Dd -> result    | A64                     |
| int16x4_t vqdmulh_s16(int16x4_t a, int16x4_t b)                                         | a -> Vn.4H<br>b -> Vm.4H                                 | SQDMULH Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vqdmulhq_s16(int16x8_t a, int16x8_t b)                                        | a -> Vn.8H<br>b -> Vm.8H                                 | SQDMULH Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vqdmulh_s32(int32x2_t a, int32x2_t b)                                         | a -> Vn.2S<br>b -> Vm.2S                                 | SQDMULH Vd.2S,Vn.2S,Vm.2S   | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vqdmulhq_s32(int32x4_t a, int32x4_t b)                                        | a -> Vn.4S<br>b -> Vm.4S                                 | SQDMULH Vd.4S,Vn.4S,Vm.4S   | Vd.4S -> result | v7/A32/A64              |
| int16_t vqdmulhq_s16(int16_t a, int16_t b)                                              | a -> Hn<br>b -> Hm                                       | SQDMULH Hd,Hn,Hm            | Hd -> result    | A64                     |
| int32_t vqdmulhs_s32(int32_t a, int32_t b)                                              | a -> Sn<br>b -> Sm                                       | SQDMULH Sd,Sn,Sm            | Sd -> result    | A64                     |
| int16x4_t vqrdmulh_s16(int16x4_t a, int16x4_t b)                                        | a -> Vn.4H<br>b -> Vm.4H                                 | SQRDMULH Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | v7/A32/A64              |

| Intrinsic                                                          | Argument Preparation                   | Instruction                 | Result          | Supported Architectures |
|--------------------------------------------------------------------|----------------------------------------|-----------------------------|-----------------|-------------------------|
| int16x8_t vqrdmulhq_s16(int16x8_t a, int16x8_t b)                  | a -> Vn.8H<br>b -> Vm.8H               | SQRDMULH Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vqrdmulh_s32(int32x2_t a, int32x2_t b)                   | a -> Vn.2S<br>b -> Vm.2S               | SQRDMULH Vd.2S,Vn.2S,Vm.2S  | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vqrdmulhq_s32(int32x4_t a, int32x4_t b)                  | a -> Vn.4S<br>b -> Vm.4S               | SQRDMULH Vd.4S,Vn.4S,Vm.4S  | Vd.4S -> result | v7/A32/A64              |
| int16_t vqrdmulh_s16(int16_t a, int16_t b)                         | a -> Hn<br>b -> Hm                     | SQRDMULH Hd,Hn,Hm           | Hd -> result    | A64                     |
| int32_t vqrdmulh_s32(int32_t a, int32_t b)                         | a -> Sn<br>b -> Sm                     | SQRDMULH Sd,Sn,Sm           | Sd -> result    | A64                     |
| int32x4_t vqdmllal_s16(int32x4_t a, int16x4_t b, int16x4_t c)      | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H | SQDMLLAL Vd.4S,Vn.4H,Vm.4H  | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmllal_s32(int64x2_t a, int32x2_t b, int32x2_t c)      | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S | SQDMLLAL Vd.2D,Vn.2S,Vm.2S  | Vd.2D -> result | v7/A32/A64              |
| int32_t vqdmllah_s16(int32_t a, int16_t b, int16_t c)              | a -> Sd<br>b -> Hn<br>c -> Hm          | SQDMLLAL Sd,Hn,Hm           | Sd -> result    | A64                     |
| int64_t vqdmllas_s32(int64_t a, int32_t b, int32_t c)              | a -> Dd<br>b -> Sn<br>c -> Sm          | SQDMLLAL Dd,Sn,Sm           | Dd -> result    | A64                     |
| int32x4_t vqdmllal_high_s16(int32x4_t a, int16x8_t b, int16x8_t c) | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H | SQDMLLAL2 Vd.4S,Vn.8H,Vm.8H | Vd.4S -> result | A64                     |
| int64x2_t vqdmllal_high_s32(int64x2_t a, int32x4_t b, int32x4_t c) | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S | SQDMLLAL2 Vd.2D,Vn.4S,Vm.4S | Vd.2D -> result | A64                     |
| int32x4_t vqdmlls_s16(int32x4_t a, int16x4_t b, int16x4_t c)       | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H | SQDMLLS Vd.4S,Vn.4H,Vm.4H   | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmlls_s32(int64x2_t a, int32x2_t b, int32x2_t c)       | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S | SQDMLLS Vd.2D,Vn.2S,Vm.2S   | Vd.2D -> result | v7/A32/A64              |
| int32_t vqdmllsh_s16(int32_t a, int16_t b, int16_t c)              | a -> Sd<br>b -> Hn<br>c -> Hm          | SQDMLLS Sd,Hn,Hm            | Sd -> result    | A64                     |
| int64_t vqdmllsh_s32(int64_t a, int32_t b, int32_t c)              | a -> Dd<br>b -> Sn<br>c -> Sm          | SQDMLLS Dd,Sn,Sm            | Dd -> result    | A64                     |
| int32x4_t vqdmlls_high_s16(int32x4_t a, int16x8_t b, int16x8_t c)  | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H | SQDMLLS2 Vd.4S,Vn.8H,Vm.8H  | Vd.4S -> result | A64                     |
| int64x2_t vqdmlls_high_s32(int64x2_t a, int32x4_t b, int32x4_t c)  | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S | SQDMLLS2 Vd.2D,Vn.4S,Vm.4S  | Vd.2D -> result | A64                     |
| int16x8_t vmull_s8(int8x8_t a, int8x8_t b)                         | a -> Vn.8B<br>b -> Vm.8B               | SMULL Vd.8H,Vn.8B,Vm.8B     | Vd.8H -> result | v7/A32/A64              |
| int32x4_t vmull_s16(int16x4_t a, int16x4_t b)                      | a -> Vn.4H<br>b -> Vm.4H               | SMULL Vd.4S,Vn.4H,Vm.4H     | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vmull_s32(int32x2_t a, int32x2_t b)                      | a -> Vn.2S<br>b -> Vm.2S               | SMULL Vd.2D,Vn.2S,Vm.2S     | Vd.2D -> result | v7/A32/A64              |
| uint16x8_t vmull_u8(uint8x8_t a, uint8x8_t b)                      | a -> Vn.8B<br>b -> Vm.8B               | UMULL Vd.8H,Vn.8B,Vm.8B     | Vd.8H -> result | v7/A32/A64              |
| uint32x4_t vmull_u16(uint16x4_t a, uint16x4_t b)                   | a -> Vn.4H<br>b -> Vm.4H               | UMULL Vd.4S,Vn.4H,Vm.4H     | Vd.4S -> result | v7/A32/A64              |
| uint64x2_t vmull_u32(uint32x2_t a, uint32x2_t b)                   | a -> Vn.2S<br>b -> Vm.2S               | UMULL Vd.2D,Vn.2S,Vm.2S     | Vd.2D -> result | v7/A32/A64              |
| poly16x8_t vmull_p8(poly8x8_t a, poly8x8_t b)                      | a -> Vn.8B<br>b -> Vm.8B               | PMULL Vd.8H,Vn.8B,Vm.8B     | Vd.8H -> result | v7/A32/A64              |
| int16x8_t vmull_high_s8(int8x16_t a, int8x16_t b)                  | a -> Vn.16B<br>b -> Vm.16B             | SMULL2 Vd.8H,Vn.16B,Vm.16B  | Vd.8H -> result | A64                     |
| int32x4_t vmull_high_s16(int16x8_t a, int16x8_t b)                 | a -> Vn.8H<br>b -> Vm.8H               | SMULL2 Vd.4S,Vn.8H,Vm.8H    | Vd.4S -> result | A64                     |
| int64x2_t vmull_high_s32(int32x4_t a, int32x4_t b)                 | a -> Vn.4S<br>b -> Vm.4S               | SMULL2 Vd.2D,Vn.4S,Vm.4S    | Vd.2D -> result | A64                     |
| uint16x8_t vmull_high_u8(uint8x16_t a, uint8x16_t b)               | a -> Vn.16B<br>b -> Vm.16B             | UMULL2 Vd.8H,Vn.16B,Vm.16B  | Vd.8H -> result | A64                     |
| uint32x4_t vmull_high_u16(uint16x8_t a, uint16x8_t b)              | a -> Vn.8H<br>b -> Vm.8H               | UMULL2 Vd.4S,Vn.8H,Vm.8H    | Vd.4S -> result | A64                     |
| uint64x2_t vmull_high_u32(uint32x4_t a, uint32x4_t b)              | a -> Vn.4S<br>b -> Vm.4S               | UMULL2 Vd.2D,Vn.4S,Vm.4S    | Vd.2D -> result | A64                     |

| Intrinsic                                            | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|------------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| poly16x8_t vmull_high_p8(poly8x16_t a, poly8x16_t b) | a -> Vn.16B<br>b -> Vm.16B | PMULL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| int32x4_t vqdmull_s16(int16x4_t a, int16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | SQDMULL Vd.4S,Vn.4H,Vm.4H  | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vqdmull_s32(int32x2_t a, int32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | SQDMULL Vd.2D,Vn.2S,Vm.2S  | Vd.2D -> result  | v7/A32/A64              |
| int32_t vqdmulls_s16(int16_t a, int16_t b)           | a -> Hn<br>b -> Hm         | SQDMULL Sd,Hn,Hm           | Sd -> result     | A64                     |
| int64_t vqdmulls_s32(int32_t a, int32_t b)           | a -> Sn<br>b -> Sm         | SQDMULL Dd,Sn,Sm           | Dd -> result     | A64                     |
| int32x4_t vqdmull_high_s16(int16x8_t a, int16x8_t b) | a -> Vn.8H<br>b -> Vm.8H   | SQDMULL2 Vd.4S,Vn.8H,Vm.8H | Vd.4S -> result  | A64                     |
| int64x2_t vqdmull_high_s32(int32x4_t a, int32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | SQDMULL2 Vd.2D,Vn.4S,Vm.4S | Vd.2D -> result  | A64                     |
| int8x8_t vsub_s8(int8x8_t a, int8x8_t b)             | a -> Vn.8B<br>b -> Vm.8B   | SUB Vd.8B,Vn.8B,Vm.8B      | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vsubq_s8(int8x16_t a, int8x16_t b)         | a -> Vn.16B<br>b -> Vm.16B | SUB Vd.16B,Vn.16B,Vm.16B   | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vsub_s16(int16x4_t a, int16x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | SUB Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vsubq_s16(int16x8_t a, int16x8_t b)        | a -> Vn.8H<br>b -> Vm.8H   | SUB Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vsub_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | SUB Vd.2S,Vn.2S,Vm.2S      | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vsubq_s32(int32x4_t a, int32x4_t b)        | a -> Vn.4S<br>b -> Vm.4S   | SUB Vd.4S,Vn.4S,Vm.4S      | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vsubq_s64(int64x1_t a, int64x1_t b)        | a -> Dn<br>b -> Dm         | SUB Dd,Dn,Dm               | Dd -> result     | v7/A32/A64              |
| int64x2_t vsubq_s64(int64x2_t a, int64x2_t b)        | a -> Vn.2D<br>b -> Vm.2D   | SUB Vd.2D,Vn.2D,Vm.2D      | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vsub_u8(uint8x8_t a, uint8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | SUB Vd.8B,Vn.8B,Vm.8B      | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vsubq_u8(uint8x16_t a, uint8x16_t b)      | a -> Vn.16B<br>b -> Vm.16B | SUB Vd.16B,Vn.16B,Vm.16B   | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vsubq_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | SUB Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vsubq_u16(uint16x8_t a, uint16x8_t b)     | a -> Vn.8H<br>b -> Vm.8H   | SUB Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vsubq_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | SUB Vd.2S,Vn.2S,Vm.2S      | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vsubq_u32(uint32x4_t a, uint32x4_t b)     | a -> Vn.4S<br>b -> Vm.4S   | SUB Vd.4S,Vn.4S,Vm.4S      | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vsubq_u64(uint64x1_t a, uint64x1_t b)     | a -> Dn<br>b -> Dm         | SUB Dd,Dn,Dm               | Dd -> result     | v7/A32/A64              |
| uint64x2_t vsubq_u64(uint64x2_t a, uint64x2_t b)     | a -> Vn.2D<br>b -> Vm.2D   | SUB Vd.2D,Vn.2D,Vm.2D      | Vd.2D -> result  | v7/A32/A64              |
| float32x2_t vsub_f32(float32x2_t a, float32x2_t b)   | a -> Vn.2S<br>b -> Vm.2S   | FSUB Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t vsubq_f32(float32x4_t a, float32x4_t b)  | a -> Vn.4S<br>b -> Vm.4S   | FSUB Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| float64x1_t vsubq_f64(float64x1_t a, float64x1_t b)  | a -> Dn<br>b -> Dm         | FSUB Dd,Dn,Dm              | Dd -> result     | A64                     |
| float64x2_t vsubq_f64(float64x2_t a, float64x2_t b)  | a -> Vn.2D<br>b -> Vm.2D   | FSUB Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | A64                     |
| int64_t vsubd_s64(int64_t a, int64_t b)              | a -> Dn<br>b -> Dm         | SUB Dd,Dn,Dm               | Dd -> result     | A64                     |
| uint64_t vsubd_u64(uint64_t a, uint64_t b)           | a -> Dn<br>b -> Dm         | SUB Dd,Dn,Dm               | Dd -> result     | A64                     |
| int16x8_t vsubl_s8(int8x8_t a, int8x8_t b)           | a -> Vn.8B<br>b -> Vm.8B   | SSUBL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vsubl_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | SSUBL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vsubl_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | SSUBL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vsubl_u8(uint8x8_t a, uint8x8_t b)        | a -> Vn.8B<br>b -> Vm.8B   | USUBL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vsubl_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | USUBL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vsubl_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | USUBL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vsubl_high_s8(int8x16_t a, int8x16_t b)    | a -> Vn.16B<br>b -> Vm.16B | SSUBL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |

| Intrinsic                                             | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|-------------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| int32x4_t vsubl_high_s16(int16x8_t a, int16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | SSUBL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| int64x2_t vsubl_high_s32(int32x4_t a, int32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | SSUBL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| uint16x8_t vsubl_high_u8(uint8x16_t a, uint8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | USUBL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| uint32x4_t vsubl_high_u16(uint16x8_t a, uint16x8_t b) | a -> Vn.8H<br>b -> Vm.8H   | USUBL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| uint64x2_t vsubl_high_u32(uint32x4_t a, uint32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | USUBL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| int16x8_t vsubw_s8(int16x8_t a, int8x8_t b)           | a -> Vn.8H<br>b -> Vm.8B   | SSUBW Vd.8H,Vn.8H,Vm.8B    | Vd.8H -> result  | V7/A32/A64              |
| int32x4_t vsubw_s16(int32x4_t a, int16x4_t b)         | a -> Vn.4S<br>b -> Vm.4H   | SSUBW Vd.4S,Vn.4S,Vm.4H    | Vd.4S -> result  | V7/A32/A64              |
| int64x2_t vsubw_s32(int64x2_t a, int32x2_t b)         | a -> Vn.2D<br>b -> Vm.2S   | SSUBW Vd.2D,Vn.2D,Vm.2S    | Vd.2D -> result  | V7/A32/A64              |
| uint16x8_t vsubw_u8(uint16x8_t a, uint8x8_t b)        | a -> Vn.8H<br>b -> Vm.8B   | USUBW Vd.8H,Vn.8H,Vm.8B    | Vd.8H -> result  | V7/A32/A64              |
| uint32x4_t vsubw_u16(uint32x4_t a, uint16x4_t b)      | a -> Vn.4S<br>b -> Vm.4H   | USUBW Vd.4S,Vn.4S,Vm.4H    | Vd.4S -> result  | V7/A32/A64              |
| uint64x2_t vsubw_u32(uint64x2_t a, uint32x2_t b)      | a -> Vn.2D<br>b -> Vm.2S   | USUBW Vd.2D,Vn.2D,Vm.2S    | Vd.2D -> result  | V7/A32/A64              |
| int16x8_t vsubw_high_s8(int16x8_t a, int8x16_t b)     | a -> Vn.8H<br>b -> Vm.16B  | SSUBW2 Vd.8H,Vn.8H,Vm.16B  | Vd.8H -> result  | A64                     |
| int32x4_t vsubw_high_s16(int32x4_t a, int16x8_t b)    | a -> Vn.4S<br>b -> Vm.8H   | SSUBW2 Vd.4S,Vn.4S,Vm.8H   | Vd.4S -> result  | A64                     |
| int64x2_t vsubw_high_s32(int64x2_t a, int32x4_t b)    | a -> Vn.2D<br>b -> Vm.4S   | SSUBW2 Vd.2D,Vn.2D,Vm.4S   | Vd.2D -> result  | A64                     |
| uint16x8_t vsubw_high_u8(uint16x8_t a, uint8x16_t b)  | a -> Vn.8H<br>b -> Vm.16B  | USUBW2 Vd.8H,Vn.8H,Vm.16B  | Vd.8H -> result  | A64                     |
| uint32x4_t vsubw_high_u16(uint32x4_t a, uint16x8_t b) | a -> Vn.4S<br>b -> Vm.8H   | USUBW2 Vd.4S,Vn.4S,Vm.8H   | Vd.4S -> result  | A64                     |
| uint64x2_t vsubw_high_u32(uint64x2_t a, uint32x4_t b) | a -> Vn.2D<br>b -> Vm.4S   | USUBW2 Vd.2D,Vn.2D,Vm.4S   | Vd.2D -> result  | A64                     |
| int8x8_t vsubq_s8(int8x8_t a, int8x8_t b)             | a -> Vn.8B<br>b -> Vm.8B   | SHSUB Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | V7/A32/A64              |
| int8x16_t vsubq_s8(int8x16_t a, int8x16_t b)          | a -> Vn.16B<br>b -> Vm.16B | SHSUB Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | V7/A32/A64              |
| int16x4_t vsubq_s16(int16x4_t a, int16x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | SHSUB Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | V7/A32/A64              |
| int16x8_t vsubq_s16(int16x8_t a, int16x8_t b)         | a -> Vn.8H<br>b -> Vm.8H   | SHSUB Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | V7/A32/A64              |
| int32x2_t vsubq_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | SHSUB Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | V7/A32/A64              |
| int32x4_t vsubq_s32(int32x4_t a, int32x4_t b)         | a -> Vn.4S<br>b -> Vm.4S   | SHSUB Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | V7/A32/A64              |
| uint8x8_t vsubq_u8(uint8x8_t a, uint8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | UHSUB Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | V7/A32/A64              |
| uint8x16_t vsubq_u8(uint8x16_t a, uint8x16_t b)       | a -> Vn.16B<br>b -> Vm.16B | UHSUB Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | V7/A32/A64              |
| uint16x4_t vsubq_u16(uint16x4_t a, uint16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | UHSUB Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | V7/A32/A64              |
| uint16x8_t vsubq_u16(uint16x8_t a, uint16x8_t b)      | a -> Vn.8H<br>b -> Vm.8H   | UHSUB Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | V7/A32/A64              |
| uint32x2_t vsubq_u32(uint32x2_t a, uint32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | UHSUB Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | V7/A32/A64              |
| uint32x4_t vsubq_u32(uint32x4_t a, uint32x4_t b)      | a -> Vn.4S<br>b -> Vm.4S   | UHSUB Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | V7/A32/A64              |
| int8x8_t vqsqb_s8(int8x8_t a, int8x8_t b)             | a -> Vn.8B<br>b -> Vm.8B   | SQSUB Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | V7/A32/A64              |
| int8x16_t vqsqb_s8(int8x16_t a, int8x16_t b)          | a -> Vn.16B<br>b -> Vm.16B | SQSUB Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | V7/A32/A64              |
| int16x4_t vqsqb_s16(int16x4_t a, int16x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | SQSUB Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | V7/A32/A64              |
| int16x8_t vqsqb_s16(int16x8_t a, int16x8_t b)         | a -> Vn.8H<br>b -> Vm.8H   | SQSUB Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | V7/A32/A64              |
| int32x2_t vqsqb_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | SQSUB Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | V7/A32/A64              |
| int32x4_t vqsqb_s32(int32x4_t a, int32x4_t b)         | a -> Vn.4S<br>b -> Vm.4S   | SQSUB Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | V7/A32/A64              |
| int64x1_t vqsqb_s64(int64x1_t a, int64x1_t b)         | a -> Dn<br>b -> Dm         | SQSUB Dd,Dn,Dm             | Dd -> result     | V7/A32/A64              |

| Intrinsic                                                           | Argument Preparation                   | Instruction                | Result           | Supported Architectures |
|---------------------------------------------------------------------|----------------------------------------|----------------------------|------------------|-------------------------|
| uint64x2_1 vqsqub_64(uint64x2_1 a, int64x2_1 b)                     | a -> Vn.ZD<br>b -> Vm.ZD               | SQSUB Vd.ZD,Vn.ZD,Vm.ZD    | Vd.ZD -> result  | v7/A32/A64              |
| uint8x8_1 vqsqub_8(uint8x8_1 a, uint8x8_1 b)                        | a -> Vn.BB<br>b -> Vm.BB               | UQSUB Vd.BB,Vn.BB,Vm.BB    | Vd.BB -> result  | v7/A32/A64              |
| uint8x16_1 vqsqub_8(uint8x16_1 a, uint8x16_1 b)                     | a -> Vn.16B<br>b -> Vm.16B             | UQSUB Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_1 vqsqub_16(uint16x4_1 a, uint16x4_1 b)                    | a -> Vn.4H<br>b -> Vm.4H               | UQSUB Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_1 vqsqub_16(uint16x8_1 a, uint16x8_1 b)                    | a -> Vn.8H<br>b -> Vm.8H               | UQSUB Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_1 vqsqub_32(uint32x2_1 a, uint32x2_1 b)                    | a -> Vn.2S<br>b -> Vm.2S               | UQSUB Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_1 vqsqub_32(uint32x4_1 a, uint32x4_1 b)                    | a -> Vn.4S<br>b -> Vm.4S               | UQSUB Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_1 vqsqub_64(uint64x1_1 a, uint64x1_1 b)                    | a -> Vn.ZD<br>b -> Vm.ZD               | UQSUB Vd.ZD,Vn.ZD,Vm.ZD    | Vd.ZD -> result  | v7/A32/A64              |
| uint64x2_1 vqsqub_64(uint64x2_1 a, uint64x2_1 b)                    | a -> Vn.ZD<br>b -> Vm.ZD               | UQSUB Vd.ZD,Vn.ZD,Vm.ZD    | Vd.ZD -> result  | v7/A32/A64              |
| int8_1 vqsqsb_8(int8_1 a, int8_1 b)                                 | a -> Bn<br>b -> Bm                     | SQSUB Bd.Bn,Bm             | Bd -> result     | A64                     |
| int16_1 vqsqsb_16(int16_1 a, int16_1 b)                             | a -> Hn<br>b -> Hm                     | SQSUB Hd.Hn,Hm             | Hd -> result     | A64                     |
| int32_1 vqsqsb_32(int32_1 a, int32_1 b)                             | a -> Sn<br>b -> Sm                     | SQSUB Sd.Sn,Sm             | Sd -> result     | A64                     |
| int64_1 vqsqsb_64(int64_1 a, int64_1 b)                             | a -> Dn<br>b -> Dm                     | SQSUB Dd.Dn,Dm             | Dd -> result     | A64                     |
| uint8_1 vqsqub_8(uint8_1 a, uint8_1 b)                              | a -> Bn<br>b -> Bm                     | UQSUB Bd.Bn,Bm             | Bd -> result     | A64                     |
| uint16_1 vqsqub_16(uint16_1 a, uint16_1 b)                          | a -> Hn<br>b -> Hm                     | UQSUB Hd.Hn,Hm             | Hd -> result     | A64                     |
| uint32_1 vqsqub_32(uint32_1 a, uint32_1 b)                          | a -> Sn<br>b -> Sm                     | UQSUB Sd.Sn,Sm             | Sd -> result     | A64                     |
| uint64_1 vqsqub_64(uint64_1 a, uint64_1 b)                          | a -> Dn<br>b -> Dm                     | UQSUB Dd.Dn,Dm             | Dd -> result     | A64                     |
| int8x8_1 vsubhn_8(int8x8_1 a, int16x8_1 b)                          | a -> Vn.BH<br>b -> Vm.BH               | SUBHN Vd.BB,Vn.BH,Vm.BH    | Vd.BB -> result  | v7/A32/A64              |
| int16x4_1 vsubhn_32(int32x4_1 a, int32x4_1 b)                       | a -> Vn.4S<br>b -> Vm.4S               | SUBHN Vd.4H,Vn.4S,Vm.4S    | Vd.4H -> result  | v7/A32/A64              |
| int32x2_1 vsubhn_64(int64x2_1 a, int64x2_1 b)                       | a -> Vn.ZD<br>b -> Vm.ZD               | SUBHN Vd.2S,Vn.ZD,Vm.ZD    | Vd.2S -> result  | v7/A32/A64              |
| uint8x8_1 vsubhn_8(uint8x8_1 a, uint16x8_1 b)                       | a -> Vn.8H<br>b -> Vm.8H               | SUBHN Vd.BB,Vn.8H,Vm.8H    | Vd.BB -> result  | v7/A32/A64              |
| uint16x4_1 vsubhn_32(uint32x4_1 a, uint32x4_1 b)                    | a -> Vn.4S<br>b -> Vm.4S               | SUBHN Vd.4H,Vn.4S,Vm.4S    | Vd.4H -> result  | v7/A32/A64              |
| uint32x2_1 vsubhn_64(uint64x2_1 a, uint64x2_1 b)                    | a -> Vn.ZD<br>b -> Vm.ZD               | SUBHN Vd.2S,Vn.ZD,Vm.ZD    | Vd.2S -> result  | v7/A32/A64              |
| int8x8_1 vsubhn_high_8(int8x8_1 r, int16x8_1 a, int16x8_1 b)        | r -> Vd.BB<br>a -> Vn.BH<br>b -> Vm.BH | SUBHNZ Vd.16B,Vn.BH,Vm.BH  | Vd.16B -> result | A64                     |
| int16x4_1 vsubhn_high_32(int32x4_1 r, int32x4_1 a, int32x4_1 b)     | r -> Vd.4H<br>a -> Vn.4S<br>b -> Vm.4S | SUBHNZ Vd.4H,Vn.4S,Vm.4S   | Vd.4H -> result  | A64                     |
| int32x2_1 vsubhn_high_64(int64x2_1 r, int64x2_1 a, int64x2_1 b)     | r -> Vd.2S<br>a -> Vn.ZD<br>b -> Vm.ZD | SUBHNZ Vd.2S,Vn.ZD,Vm.ZD   | Vd.2S -> result  | A64                     |
| uint8x8_1 vsubhn_high_8(uint8x8_1 r, uint16x8_1 a, uint16x8_1 b)    | r -> Vd.BB<br>a -> Vn.BH<br>b -> Vm.BH | SUBHNZ Vd.16B,Vn.BH,Vm.BH  | Vd.16B -> result | A64                     |
| uint16x4_1 vsubhn_high_32(uint32x4_1 r, uint32x4_1 a, uint32x4_1 b) | r -> Vd.4H<br>a -> Vn.4S<br>b -> Vm.4S | SUBHNZ Vd.4H,Vn.4S,Vm.4S   | Vd.4H -> result  | A64                     |
| uint32x2_1 vsubhn_high_64(uint64x2_1 r, uint64x2_1 a, uint64x2_1 b) | r -> Vd.2S<br>a -> Vn.ZD<br>b -> Vm.ZD | SUBHNZ Vd.2S,Vn.ZD,Vm.ZD   | Vd.2S -> result  | A64                     |
| int8x8_1 vsubhn_8(uint8x8_1 a, uint16x8_1 b)                        | a -> Vn.BH<br>b -> Vm.BH               | RSUBHN Vd.BB,Vn.BH,Vm.BH   | Vd.BB -> result  | v7/A32/A64              |
| int16x4_1 vsubhn_32(int32x4_1 a, int32x4_1 b)                       | a -> Vn.4S<br>b -> Vm.4S               | RSUBHN Vd.4H,Vn.4S,Vm.4S   | Vd.4H -> result  | v7/A32/A64              |
| int32x2_1 vsubhn_64(int64x2_1 a, int64x2_1 b)                       | a -> Vn.ZD<br>b -> Vm.ZD               | RSUBHN Vd.2S,Vn.ZD,Vm.ZD   | Vd.2S -> result  | v7/A32/A64              |
| uint8x8_1 vsubhn_8(uint8x8_1 a, uint16x8_1 b)                       | a -> Vn.8H<br>b -> Vm.8H               | RSUBHN Vd.BB,Vn.8H,Vm.8H   | Vd.BB -> result  | v7/A32/A64              |

| Intrinsic                                                            | Argument Preparation                   | Instruction                | Result           | Supported Architectures |
|----------------------------------------------------------------------|----------------------------------------|----------------------------|------------------|-------------------------|
| uint16x4_t vsubhn_u32(uint32x4_t a, uint32x4_t b)                    | a -> Vn,4S<br>b -> Vm,4S               | RSUBHN Vd,4H,Vn,4S,Vm,4S   | Vd,4H -> result  | v7/A32/A64              |
| uint32x2_t vsubhn_u64(uint64x2_t a, uint64x2_t b)                    | a -> Vn,2D<br>b -> Vm,2D               | RSUBHN Vd,2S,Vn,2D,Vm,2D   | Vd,2S -> result  | v7/A32/A64              |
| int8x16_t vsubhn_high_s32(int8x8_t r, int16x8_t a, int16x8_t b)      | r -> Vd,8H<br>a -> Vn,8H<br>b -> Vm,8H | RSUBHNZ Vd,16B,Vn,8H,Vm,8H | Vd,16B -> result | A64                     |
| int16x8_t vsubhn_high_s32(int16x4_t r, int32x4_t a, int32x4_t b)     | r -> Vd,4H<br>a -> Vn,4S<br>b -> Vm,4S | RSUBHNZ Vd,8H,Vn,4S,Vm,4S  | Vd,8H -> result  | A64                     |
| int32x4_t vsubhn_high_s64(int32x2_t r, int64x2_t a, int64x2_t b)     | r -> Vd,2S<br>a -> Vn,2D<br>b -> Vm,2D | RSUBHNZ Vd,4S,Vn,2D,Vm,2D  | Vd,4S -> result  | A64                     |
| uint8x16_t vsubhn_high_u16(uint8x8_t r, uint16x8_t a, uint16x8_t b)  | r -> Vd,8H<br>a -> Vn,8H<br>b -> Vm,8H | RSUBHNZ Vd,16B,Vn,8H,Vm,8H | Vd,16B -> result | A64                     |
| uint16x8_t vsubhn_high_u32(uint16x4_t r, uint32x4_t a, uint32x4_t b) | r -> Vd,4H<br>a -> Vn,4S<br>b -> Vm,4S | RSUBHNZ Vd,8H,Vn,4S,Vm,4S  | Vd,8H -> result  | A64                     |
| uint32x2_t vsubhn_high_u64(uint32x2_t r, uint64x2_t a, uint64x2_t b) | r -> Vd,2S<br>a -> Vn,2D<br>b -> Vm,2D | RSUBHNZ Vd,4S,Vn,2D,Vm,2D  | Vd,4S -> result  | A64                     |
| uint8x8_t vceqq_s8(int8x8_t a, int8x8_t b)                           | a -> Vn,8B<br>b -> Vm,8B               | CMEQ Vd,8B,Vn,8B,Vm,8B     | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vceqq_s16(int16x8_t a, int8x16_t b)                       | a -> Vn,16B<br>b -> Vm,16B             | CMEQ Vd,16B,Vn,16B,Vm,16B  | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vceqq_s16(int16x4_t a, int16x4_t b)                       | a -> Vn,4H<br>b -> Vm,4H               | CMEQ Vd,4H,Vn,4H,Vm,4H     | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vceqq_s16(int16x8_t a, int16x8_t b)                       | a -> Vn,8H<br>b -> Vm,8H               | CMEQ Vd,8H,Vn,8H,Vm,8H     | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vceqq_s32(int32x2_t a, int32x2_t b)                       | a -> Vn,2S<br>b -> Vm,2S               | CMEQ Vd,2S,Vn,2S,Vm,2S     | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vceqq_s32(int32x4_t a, int32x4_t b)                       | a -> Vn,4S<br>b -> Vm,4S               | CMEQ Vd,4S,Vn,4S,Vm,4S     | Vd,4S -> result  | v7/A32/A64              |
| uint8x8_t vceqq_u8(uint8x8_t a, uint8x8_t b)                         | a -> Vn,8B<br>b -> Vm,8B               | CMEQ Vd,8B,Vn,8B,Vm,8B     | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vceqq_u8(uint8x16_t a, uint8x16_t b)                      | a -> Vn,16B<br>b -> Vm,16B             | CMEQ Vd,16B,Vn,16B,Vm,16B  | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vceqq_u16(uint16x4_t a, uint16x4_t b)                     | a -> Vn,4H<br>b -> Vm,4H               | CMEQ Vd,4H,Vn,4H,Vm,4H     | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vceqq_u16(uint16x8_t a, uint16x8_t b)                     | a -> Vn,8H<br>b -> Vm,8H               | CMEQ Vd,8H,Vn,8H,Vm,8H     | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vceqq_u32(uint32x2_t a, uint32x2_t b)                     | a -> Vn,2S<br>b -> Vm,2S               | CMEQ Vd,2S,Vn,2S,Vm,2S     | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vceqq_u32(uint32x4_t a, uint32x4_t b)                     | a -> Vn,4S<br>b -> Vm,4S               | CMEQ Vd,4S,Vn,4S,Vm,4S     | Vd,4S -> result  | v7/A32/A64              |
| uint32x2_t vceqq_f32(float32x2_t a, float32x2_t b)                   | a -> Vn,2S<br>b -> Vm,2S               | FCEQ Vd,2S,Vn,2S,Vm,2S     | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vceqq_f32(float32x4_t a, float32x4_t b)                   | a -> Vn,4S<br>b -> Vm,4S               | FCEQ Vd,4S,Vn,4S,Vm,4S     | Vd,4S -> result  | v7/A32/A64              |
| uint8x8_t vceqq_p8(poly8x8_t a, poly8x8_t b)                         | a -> Vn,8B<br>b -> Vm,8B               | CMEQ Vd,8B,Vn,8B,Vm,8B     | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vceqq_p8(poly8x16_t a, poly8x16_t b)                      | a -> Vn,16B<br>b -> Vm,16B             | CMEQ Vd,16B,Vn,16B,Vm,16B  | Vd,16B -> result | v7/A32/A64              |
| uint64x1_t vceqq_s64(int64x1_t a, int64x1_t b)                       | a -> Dn<br>b -> Dm                     | CMEQ Dd,Dn,Dm              | Dd -> result     | A64                     |
| uint64x2_t vceqq_s64(int64x2_t a, int64x2_t b)                       | a -> Vn,2D<br>b -> Vm,2D               | CMEQ Vd,2D,Vn,2D,Vm,2D     | Vd,2D -> result  | A64                     |
| uint64x4_t vceqq_s64(int64x4_t a, int64x4_t b)                       | a -> Dn<br>b -> Dm                     | CMEQ Dd,Dn,Dm              | Dd -> result     | A64                     |
| uint64x2_t vceqq_p64(poly64x2_t a, poly64x2_t b)                     | a -> Dn<br>b -> Dm                     | CMEQ Dd,Dn,Dm              | Dd -> result     | A32/A64                 |
| uint64x2_t vceqq_p64(poly64x2_t a, poly64x2_t b)                     | a -> Vn,2D<br>b -> Vm,2D               | CMEQ Vd,2D,Vn,2D,Vm,2D     | Vd,2D -> result  | A32/A64                 |
| uint64x4_t vceqq_f64(float64x4_t a, float64x4_t b)                   | a -> Dn<br>b -> Dm                     | FCEQ Dd,Dn,Dm              | Dd -> result     | A64                     |
| uint64x2_t vceqq_f64(float64x2_t a, float64x2_t b)                   | a -> Vn,2D<br>b -> Vm,2D               | FCEQ Vd,2D,Vn,2D,Vm,2D     | Vd,2D -> result  | A64                     |
| uint64_t vceqq_s64(int64_t a, int64_t b)                             | a -> Dm<br>b -> Dm                     | CMEQ Dd,Dn,Dm              | Dd -> result     | A64                     |

| Intrinsic                                          | Argument Preparation   | Instruction               | Result         | Supported Architectures |
|----------------------------------------------------|------------------------|---------------------------|----------------|-------------------------|
| uint64_t vceqd_u64(uint64_t a, uint64_t b)         | a->Dn<br>b->Dm         | CMEQ Dd,Dn,Dm             | Dd->result     | A64                     |
| uint32_t vceqs_f32(float32_t a, float32_t b)       | a->Sn<br>b->Sm         | FCMEQ Sd,Sn,Sm            | Sd->result     | A64                     |
| uint64_t vceqd_f64(float64_t a, float64_t b)       | a->Dn<br>b->Dm         | FCMEQ Dd,Dn,Dm            | Dd->result     | A64                     |
| uint8x8_t vceqz_s8(int8x8_t a)                     | a->Vn,8B               | CMEQ Vd,8B,Vn,8B,#0       | Vd,8B->result  | A64                     |
| uint8x16_t vceqz_s8(int8x16_t a)                   | a->Vn,16B              | CMEQ Vd,16B,Vn,16B,#0     | Vd,16B->result | A64                     |
| uint16x4_t vceqz_s16(int16x4_t a)                  | a->Vn,4H               | CMEQ Vd,4H,Vn,4H,#0       | Vd,4H->result  | A64                     |
| uint16x8_t vceqz_s16(int16x8_t a)                  | a->Vn,8H               | CMEQ Vd,8H,Vn,8H,#0       | Vd,8H->result  | A64                     |
| uint32x2_t vceqz_s32(int32x2_t a)                  | a->Vn,2S               | CMEQ Vd,2S,Vn,2S,#0       | Vd,2S->result  | A64                     |
| uint32x4_t vceqz_s32(int32x4_t a)                  | a->Vn,4S               | CMEQ Vd,4S,Vn,4S,#0       | Vd,4S->result  | A64                     |
| uint8x8_t vceqz_u8(uint8x8_t a)                    | a->Vn,8B               | CMEQ Vd,8B,Vn,8B,#0       | Vd,8B->result  | A64                     |
| uint8x16_t vceqz_u8(uint8x16_t a)                  | a->Vn,16B              | CMEQ Vd,16B,Vn,16B,#0     | Vd,16B->result | A64                     |
| uint16x4_t vceqz_u16(uint16x4_t a)                 | a->Vn,4H               | CMEQ Vd,4H,Vn,4H,#0       | Vd,4H->result  | A64                     |
| uint16x8_t vceqz_u16(uint16x8_t a)                 | a->Vn,8H               | CMEQ Vd,8H,Vn,8H,#0       | Vd,8H->result  | A64                     |
| uint32x2_t vceqz_u32(uint32x2_t a)                 | a->Vn,2S               | CMEQ Vd,2S,Vn,2S,#0       | Vd,2S->result  | A64                     |
| uint32x4_t vceqz_u32(uint32x4_t a)                 | a->Vn,4S               | CMEQ Vd,4S,Vn,4S,#0       | Vd,4S->result  | A64                     |
| uint32x2_t vceqz_f32(float32x2_t a)                | a->Vn,2S               | FCMEQ Vd,2S,Vn,2S,#0      | Vd,2S->result  | A64                     |
| uint32x4_t vceqz_f32(float32x4_t a)                | a->Vn,4S               | FCMEQ Vd,4S,Vn,4S,#0      | Vd,4S->result  | A64                     |
| uint8x8_t vceqz_p8(poly8x8_t a)                    | a->Vn,8B               | CMEQ Vd,8B,Vn,8B,#0       | Vd,8B->result  | A64                     |
| uint8x16_t vceqz_p8(poly8x16_t a)                  | a->Vn,16B              | CMEQ Vd,16B,Vn,16B,#0     | Vd,16B->result | A64                     |
| uint64x1_t vceqz_s64(int64x1_t a)                  | a->Dn                  | CMEQ Dd,Dn,#0             | Dd->result     | A64                     |
| uint64x2_t vceqz_s64(int64x2_t a)                  | a->Vn,2D               | CMEQ Vd,2D,Vn,2D,#0       | Vd,2D->result  | A64                     |
| uint64x1_t vceqz_u64(uint64x1_t a)                 | a->Dn                  | CMEQ Dd,Dn,#0             | Dd->result     | A64                     |
| uint64x2_t vceqz_u64(uint64x2_t a)                 | a->Vn,2D               | CMEQ Vd,2D,Vn,2D,#0       | Vd,2D->result  | A64                     |
| uint64x1_t vceqz_p64(poly64x1_t a)                 | a->Dn                  | CMEQ Dd,Dn,#0             | Dd->result     | A32/A64                 |
| uint64x2_t vceqz_p64(poly64x2_t a)                 | a->Vn,2D               | CMEQ Vd,2D,Vn,2D,#0       | Vd,2D->result  | A32/A64                 |
| uint64x1_t vceqz_f64(float64x1_t a)                | a->Dn                  | FCMEQ Dd,Dn,#0            | Dd->result     | A64                     |
| uint64x2_t vceqz_f64(float64x2_t a)                | a->Vn,2D               | FCMEQ Vd,2D,Vn,2D,#0      | Vd,2D->result  | A64                     |
| uint64_t vceqzd_s64(int64_t a)                     | a->Dn                  | CMEQ Dd,Dn,#0             | Dd->result     | A64                     |
| uint64_t vceqzd_u64(uint64_t a)                    | a->Dn                  | CMEQ Dd,Dn,#0             | Dd->result     | A64                     |
| uint32_t vceqzs_f32(float32_t a)                   | a->Sn                  | FCMEQ Sd,Sn,#0            | Sd->result     | A64                     |
| uint64_t vceqzd_f64(float64_t a)                   | a->Dn                  | FCMEQ Dd,Dn,#0            | Dd->result     | A64                     |
| uint8x8_t vceq_s8(int8x8_t a, int8x8_t b)          | a->Vn,8B<br>b->Vm,8B   | CMGE Vd,8B,Vm,8B,Vn,8B    | Vd,8B->result  | v7/A32/A64              |
| uint8x16_t vceqz_s8(int8x16_t a, int8x16_t b)      | a->Vn,16B<br>b->Vm,16B | CMGE Vd,16B,Vm,16B,Vn,16B | Vd,16B->result | v7/A32/A64              |
| uint16x4_t vceqz_s16(int16x4_t a, int16x4_t b)     | a->Vn,4H<br>b->Vm,4H   | CMGE Vd,4H,Vm,4H,Vn,4H    | Vd,4H->result  | v7/A32/A64              |
| uint16x8_t vceqz_s16(int16x8_t a, int16x8_t b)     | a->Vn,8H<br>b->Vm,8H   | CMGE Vd,8H,Vm,8H,Vn,8H    | Vd,8H->result  | v7/A32/A64              |
| uint32x2_t vceqz_s32(int32x2_t a, int32x2_t b)     | a->Vn,2S<br>b->Vm,2S   | CMGE Vd,2S,Vm,2S,Vn,2S    | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vceqz_s32(int32x4_t a, int32x4_t b)     | a->Vn,4S<br>b->Vm,4S   | CMGE Vd,4S,Vm,4S,Vn,4S    | Vd,4S->result  | v7/A32/A64              |
| uint8x8_t vceqz_u8(uint8x8_t a, uint8x8_t b)       | a->Vn,8B<br>b->Vm,8B   | CMHS Vd,8B,Vm,8B,Vn,8B    | Vd,8B->result  | v7/A32/A64              |
| uint8x16_t vceqz_u8(uint8x16_t a, uint8x16_t b)    | a->Vn,16B<br>b->Vm,16B | CMHS Vd,16B,Vm,16B,Vn,16B | Vd,16B->result | v7/A32/A64              |
| uint16x4_t vceqz_u16(uint16x4_t a, uint16x4_t b)   | a->Vn,4H<br>b->Vm,4H   | CMHS Vd,4H,Vm,4H,Vn,4H    | Vd,4H->result  | v7/A32/A64              |
| uint16x8_t vceqz_u16(uint16x8_t a, uint16x8_t b)   | a->Vn,8H<br>b->Vm,8H   | CMHS Vd,8H,Vm,8H,Vn,8H    | Vd,8H->result  | v7/A32/A64              |
| uint32x2_t vceqz_u32(uint32x2_t a, uint32x2_t b)   | a->Vn,2S<br>b->Vm,2S   | CMHS Vd,2S,Vm,2S,Vn,2S    | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vceqz_u32(uint32x4_t a, uint32x4_t b)   | a->Vn,4S<br>b->Vm,4S   | CMHS Vd,4S,Vm,4S,Vn,4S    | Vd,4S->result  | v7/A32/A64              |
| uint32x2_t vceqz_f32(float32x2_t a, float32x2_t b) | a->Vn,2S<br>b->Vm,2S   | FCMGE Vd,2S,Vm,2S,Vn,2S   | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vceqz_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vm,4S   | FCMGE Vd,4S,Vm,4S,Vn,4S   | Vd,4S->result  | v7/A32/A64              |
| uint64x1_t vceqz_s64(int64x1_t a, int64x1_t b)     | a->Dn<br>b->Dm         | CMGE Dd,Dn,Dm             | Dd->result     | A64                     |
| uint64x2_t vceqz_s64(int64x2_t a, int64x2_t b)     | a->Vn,2D<br>b->Vm,2D   | CMGE Vd,2D,Vm,2D,Vn,2D    | Vd,2D->result  | A64                     |
| uint64x1_t vceqz_u64(uint64x1_t a, uint64x1_t b)   | a->Dn<br>b->Dm         | CMHS Dd,Dn,Dm             | Dd->result     | A64                     |

| Intrinsic                                          | Argument Preparation       | Instruction               | Result           | Supported Architectures |
|----------------------------------------------------|----------------------------|---------------------------|------------------|-------------------------|
| uint64x2_t vceqz_u64(uint64x2_t a, uint64x2_t b)   | a -> Vn,2D<br>b -> Vm,2D   | CMHS Vd,2D,Vm,2D,Vn,2D    | Vd,2D -> result  | A64                     |
| uint64x1_t vceqz_f64(float64x1_t a, float64x1_t b) | a -> Dm<br>b -> Dm         | FCMGE Vd,Dm,Dm            | Dd -> result     | A64                     |
| uint64x2_t vceqz_f64(float64x2_t a, float64x2_t b) | a -> Vn,2D<br>b -> Vm,2D   | FCMGE Vd,2D,Vm,2D,Vn,2D   | Vd,2D -> result  | A64                     |
| uint64_t vceqz_s64(int64_t a, int64_t b)           | a -> Dm<br>b -> Dm         | CMGE Vd,Dm,Dm             | Dd -> result     | A64                     |
| uint64_t vceqz_u64(uint64_t a, uint64_t b)         | a -> Dm<br>b -> Dm         | CMHS Vd,Dm,Dm             | Dd -> result     | A64                     |
| uint32_t vceqz_f32(float32_t a, float32_t b)       | a -> Sn<br>b -> Sm         | FCMGE Sd,Sn,Sm            | Sd -> result     | A64                     |
| uint64_t vceqz_f64(float64_t a, float64_t b)       | a -> Dm<br>b -> Dm         | FCMGE Vd,Dm,Dm            | Dd -> result     | A64                     |
| uint8x8_t vceqz_s8(int8x8_t a)                     | a -> Vn,BB<br>b -> Vn,16B  | CMGE Vd,BB,Vn,BB,#0       | Vd,BB -> result  | A64                     |
| uint8x16_t vceqz_s8(int8x16_t a)                   | a -> Vn,4B                 | CMGE Vd,16B,Vn,16B,#0     | Vd,16B -> result | A64                     |
| uint16x8_t vceqz_s16(int16x8_t a)                  | a -> Vn,4H                 | CMGE Vd,4H,Vn,4H,#0       | Vd,4H -> result  | A64                     |
| uint16x8_t vceqz_s16(int16x8_t a)                  | a -> Vn,8H                 | CMGE Vd,8H,Vn,8H,#0       | Vd,8H -> result  | A64                     |
| uint32x2_t vceqz_s32(int32x2_t a)                  | a -> Vn,2S                 | CMGE Vd,2S,Vn,2S,#0       | Vd,2S -> result  | A64                     |
| uint32x4_t vceqz_s32(int32x4_t a)                  | a -> Vn,4S                 | CMGE Vd,4S,Vn,4S,#0       | Vd,4S -> result  | A64                     |
| uint64x1_t vceqz_s64(int64x1_t a)                  | a -> Dm                    | CMGE Vd,Dm,#0             | Dd -> result     | A64                     |
| uint64x2_t vceqz_s64(int64x2_t a)                  | a -> Vn,2D                 | CMGE Vd,2D,Vn,2D,#0       | Vd,2D -> result  | A64                     |
| uint32x2_t vceqz_f32(float32x2_t a)                | a -> Vn,2S                 | FCMGE Vd,2S,Vn,2S,#0      | Vd,2S -> result  | A64                     |
| uint32x4_t vceqz_f32(float32x4_t a)                | a -> Vn,4S                 | FCMGE Vd,4S,Vn,4S,#0      | Vd,4S -> result  | A64                     |
| uint64x1_t vceqz_f64(float64x1_t a)                | a -> Dm                    | FCMGE Vd,Dm,#0            | Dd -> result     | A64                     |
| uint64x2_t vceqz_f64(float64x2_t a)                | a -> Vn,2D                 | FCMGE Vd,2D,Vn,2D,#0      | Vd,2D -> result  | A64                     |
| uint32_t vceqz_f32(float32_t a)                    | a -> Sn                    | FCMGE Sd,Sn,#0            | Sd -> result     | A64                     |
| uint64_t vceqz_f64(float64_t a)                    | a -> Dm                    | FCMGE Vd,Dm,#0            | Dd -> result     | A64                     |
| uint8x8_t vcleq_s8(int8x8_t a, int8x8_t b)         | a -> Vn,BB<br>b -> Vn,16B  | CMGE Vd,BB,Vm,BB,Vn,BB    | Vd,BB -> result  | v7.1A3/AA64             |
| uint8x8_t vcleq_s8(int8x8_t a, int8x8_t b)         | a -> Vn,16B<br>b -> Vn,16B | CMGE Vd,16B,Vm,16B,Vn,16B | Vd,16B -> result | v7.1A3/AA64             |
| uint16x8_t vcleq_s16(int16x8_t a, int16x8_t b)     | a -> Vn,4H<br>b -> Vn,4H   | CMGE Vd,4H,Vm,4H,Vn,4H    | Vd,4H -> result  | v7.1A3/AA64             |
| uint16x8_t vcleq_s16(int16x8_t a, int16x8_t b)     | a -> Vn,8H<br>b -> Vn,8H   | CMGE Vd,8H,Vm,8H,Vn,8H    | Vd,8H -> result  | v7.1A3/AA64             |
| uint32x2_t vcleq_s32(int32x2_t a, int32x2_t b)     | a -> Vn,2S<br>b -> Vn,2S   | CMGE Vd,2S,Vm,2S,Vn,2S    | Vd,2S -> result  | v7.1A3/AA64             |
| uint32x4_t vcleq_s32(int32x4_t a, int32x4_t b)     | a -> Vn,4S<br>b -> Vn,4S   | CMGE Vd,4S,Vm,4S,Vn,4S    | Vd,4S -> result  | v7.1A3/AA64             |
| uint8x8_t vcleq_s8(int8x8_t a, int8x8_t b)         | a -> Vn,BB<br>b -> Vn,BB   | CMHS Vd,BB,Vm,BB,Vn,BB    | Vd,BB -> result  | v7.1A3/AA64             |
| uint8x16_t vcleq_s8(int8x16_t a, int8x16_t b)      | a -> Vn,16B<br>b -> Vn,16B | CMHS Vd,16B,Vm,16B,Vn,16B | Vd,16B -> result | v7.1A3/AA64             |
| uint16x8_t vcleq_s16(int16x8_t a, int16x8_t b)     | a -> Vn,4H<br>b -> Vn,4H   | CMHS Vd,4H,Vm,4H,Vn,4H    | Vd,4H -> result  | v7.1A3/AA64             |
| uint16x8_t vcleq_s16(int16x8_t a, int16x8_t b)     | a -> Vn,8H<br>b -> Vn,8H   | CMHS Vd,8H,Vm,8H,Vn,8H    | Vd,8H -> result  | v7.1A3/AA64             |
| uint32x2_t vcleq_s32(int32x2_t a, int32x2_t b)     | a -> Vn,2S<br>b -> Vn,2S   | CMHS Vd,2S,Vm,2S,Vn,2S    | Vd,2S -> result  | v7.1A3/AA64             |
| uint32x4_t vcleq_s32(int32x4_t a, int32x4_t b)     | a -> Vn,4S<br>b -> Vn,4S   | CMHS Vd,4S,Vm,4S,Vn,4S    | Vd,4S -> result  | v7.1A3/AA64             |
| uint32x2_t vcleq_f32(float32x2_t a, float32x2_t b) | a -> Vn,2S<br>b -> Vn,2S   | FCMGE Vd,2S,Vm,2S,Vn,2S   | Vd,2S -> result  | v7.1A3/AA64             |
| uint32x4_t vcleq_f32(float32x4_t a, float32x4_t b) | a -> Vn,4S<br>b -> Vn,4S   | FCMGE Vd,4S,Vm,4S,Vn,4S   | Vd,4S -> result  | v7.1A3/AA64             |
| uint64x1_t vcleq_s64(int64x1_t a, int64x1_t b)     | a -> Dm<br>b -> Dm         | CMGE Vd,Dm,Dm             | Dd -> result     | A64                     |
| uint64x2_t vcleq_s64(int64x2_t a, int64x2_t b)     | a -> Vn,2D<br>b -> Vn,2D   | CMGE Vd,2D,Vm,2D,Vn,2D    | Vd,2D -> result  | A64                     |
| uint64x1_t vcleq_u64(uint64x1_t a, uint64x1_t b)   | a -> Dm<br>b -> Dm         | CMHS Vd,Dm,Dm             | Dd -> result     | A64                     |
| uint64x2_t vcleq_u64(uint64x2_t a, uint64x2_t b)   | a -> Vn,2D<br>b -> Vn,2D   | CMHS Vd,2D,Vm,2D,Vn,2D    | Vd,2D -> result  | A64                     |
| uint64x1_t vcleq_f64(float64x1_t a, float64x1_t b) | a -> Dm<br>b -> Dm         | FCMGE Vd,Dm,Dm            | Dd -> result     | A64                     |
| uint64x2_t vcleq_f64(float64x2_t a, float64x2_t b) | a -> Vn,2D<br>b -> Vn,2D   | FCMGE Vd,2D,Vm,2D,Vn,2D   | Vd,2D -> result  | A64                     |
| uint64x1_t vcleq_s64(int64x1_t a, int64x1_t b)     | a -> Dm<br>b -> Dm         | CMGE Vd,Dm,Dm             | Dd -> result     | A64                     |

| Intrinsic                                          | Argument Preparation   | Instruction               | Result         | Supported Architectures |
|----------------------------------------------------|------------------------|---------------------------|----------------|-------------------------|
| uint64_t vcleld_u64(uint64_t a, uint64_t b)        | a->Dn<br>b->Dm         | CMHS Dd,Dm,Dn             | Dd->result     | A64                     |
| uint32_t vcles_f32(float32_t a, float32_t b)       | a->Sn<br>b->Sm         | FCMGE Sd,Sm,Sn            | Sd->result     | A64                     |
| uint64_t vcleld_f64(float64_t a, float64_t b)      | a->Dn<br>b->Dm         | FCMGE Dd,Dm,Dn            | Dd->result     | A64                     |
| uint8x8_t vclez_s8(int8x8_t a)                     | a->Vn,8B               | CMLE Vd,8B,Vn,8B,#0       | Vd,8B->result  | A64                     |
| uint8x16_t vclezq_s8(int8x16_t a)                  | a->Vn,16B              | CMLE Vd,16B,Vn,16B,#0     | Vd,16B->result | A64                     |
| uint16x4_t vclez_s16(int16x4_t a)                  | a->Vn,4H               | CMLE Vd,4H,Vn,4H,#0       | Vd,4H->result  | A64                     |
| uint16x8_t vclezq_s16(int16x8_t a)                 | a->Vn,8H               | CMLE Vd,8H,Vn,8H,#0       | Vd,8H->result  | A64                     |
| uint32x2_t vclez_s32(int32x2_t a)                  | a->Vn,2S               | CMLE Vd,2S,Vn,2S,#0       | Vd,2S->result  | A64                     |
| uint32x4_t vclezq_s32(int32x4_t a)                 | a->Vn,4S               | CMLE Vd,4S,Vn,4S,#0       | Vd,4S->result  | A64                     |
| uint64x1_t vclez_s64(int64x1_t a)                  | a->Dn                  | CMLE Dd,Dn,#0             | Dd->result     | A64                     |
| uint64x2_t vclezq_s64(int64x2_t a)                 | a->Vn,2D               | CMLE Vd,2D,Vn,2D,#0       | Vd,2D->result  | A64                     |
| uint32x2_t vclez_f32(float32x2_t a)                | a->Vn,2S               | CMLE Vd,2S,Vn,2S,#0       | Vd,2S->result  | A64                     |
| uint32x4_t vclezq_f32(float32x4_t a)               | a->Vn,4S               | FCMLE Vd,4S,Vn,4S,#0      | Vd,4S->result  | A64                     |
| uint64x1_t vclez_f64(float64x1_t a)                | a->Dn                  | FCMLE Dd,Dn,#0            | Dd->result     | A64                     |
| uint64x2_t vclezq_f64(float64x2_t a)               | a->Vn,2D               | FCMLE Vd,2D,Vn,2D,#0      | Vd,2D->result  | A64                     |
| uint64_t vclezd_s64(int64_t a)                     | a->Dn                  | CMLE Dd,Dn,#0             | Dd->result     | A64                     |
| uint32_t vclezs_f32(float32_t a)                   | a->Sn                  | FCMLE Sd,Sn,#0            | Sd->result     | A64                     |
| uint64_t vclezd_f64(float64_t a)                   | a->Dn                  | FCMLE Dd,Dn,#0            | Dd->result     | A64                     |
| uint8x8_t vcgt_s8(int8x8_t a, int8x8_t b)          | a->Vn,8B<br>b->Vn,8B   | FCMGTE Dd,Dn,8B           | Vd,8B->result  | v7/A32/A64              |
| uint8x16_t vcgtq_s8(int8x16_t a, int8x16_t b)      | a->Vn,16B<br>b->Vn,16B | CMGT Vd,16B,Vn,16B,Vm,16B | Vd,16B->result | v7/A32/A64              |
| uint16x4_t vcgt_s16(int16x4_t a, int16x4_t b)      | a->Vn,4H<br>b->Vn,4H   | CMGT Vd,4H,Vn,4H,Vm,4H    | Vd,4H->result  | v7/A32/A64              |
| uint16x8_t vcgtq_s16(int16x8_t a, int16x8_t b)     | a->Vn,8H<br>b->Vn,8H   | CMGT Vd,8H,Vn,8H,Vm,8H    | Vd,8H->result  | v7/A32/A64              |
| uint32x2_t vcgt_s32(int32x2_t a, int32x2_t b)      | a->Vn,2S<br>b->Vn,2S   | CMGT Vd,2S,Vn,2S,Vm,2S    | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vcgtq_s32(int32x4_t a, int32x4_t b)     | a->Vn,4S<br>b->Vn,4S   | CMGT Vd,4S,Vn,4S,Vm,4S    | Vd,4S->result  | v7/A32/A64              |
| uint8x8_t vcgt_u8(uint8x8_t a, uint8x8_t b)        | a->Vn,8B<br>b->Vn,8B   | CMHI Vd,8B,Vn,8B,Vm,8B    | Vd,8B->result  | v7/A32/A64              |
| uint8x16_t vcgtq_u8(uint8x16_t a, uint8x16_t b)    | a->Vn,16B<br>b->Vn,16B | CMHI Vd,16B,Vn,16B,Vm,16B | Vd,16B->result | v7/A32/A64              |
| uint16x4_t vcgt_u16(uint16x4_t a, uint16x4_t b)    | a->Vn,4H<br>b->Vn,4H   | CMHI Vd,4H,Vn,4H,Vm,4H    | Vd,4H->result  | v7/A32/A64              |
| uint16x8_t vcgtq_u16(uint16x8_t a, uint16x8_t b)   | a->Vn,8H<br>b->Vn,8H   | CMHI Vd,8H,Vn,8H,Vm,8H    | Vd,8H->result  | v7/A32/A64              |
| uint32x2_t vcgt_u32(uint32x2_t a, uint32x2_t b)    | a->Vn,2S<br>b->Vn,2S   | CMHI Vd,2S,Vn,2S,Vm,2S    | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vcgtq_u32(uint32x4_t a, uint32x4_t b)   | a->Vn,4S<br>b->Vn,4S   | CMHI Vd,4S,Vn,4S,Vm,4S    | Vd,4S->result  | v7/A32/A64              |
| uint32x2_t vcgt_f32(float32x2_t a, float32x2_t b)  | a->Vn,2S<br>b->Vn,2S   | FCMGT Vd,2S,Vn,2S,Vm,2S   | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vcgtq_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vn,4S   | FCMGT Vd,4S,Vn,4S,Vm,4S   | Vd,4S->result  | v7/A32/A64              |
| uint64x1_t vcgt_s64(int64x1_t a, int64x1_t b)      | a->Dn<br>b->Dm         | CMGT Dd,Dn,Dm             | Dd->result     | A64                     |
| uint64x2_t vcgtq_s64(int64x2_t a, int64x2_t b)     | a->Vn,2D<br>b->Vn,2D   | CMGT Vd,2D,Vn,2D,Vm,2D    | Vd,2D->result  | A64                     |
| uint64x1_t vcgt_u64(uint64x1_t a, uint64x1_t b)    | a->Dn<br>b->Dm         | CMHI Dd,Dn,Dm             | Dd->result     | A64                     |
| uint64x2_t vcgtq_u64(uint64x2_t a, uint64x2_t b)   | a->Vn,2D<br>b->Vn,2D   | CMHI Vd,2D,Vn,2D,Vm,2D    | Vd,2D->result  | A64                     |
| uint64x1_t vcgt_f64(float64x1_t a, float64x1_t b)  | a->Dn<br>b->Dm         | FCMGT Dd,Dn,Dm            | Dd->result     | A64                     |
| uint64x2_t vcgtq_f64(float64x2_t a, float64x2_t b) | a->Vn,2D<br>b->Vn,2D   | FCMGT Vd,2D,Vn,2D,Vm,2D   | Vd,2D->result  | A64                     |
| uint64_t vcgtld_s64(int64_t a, int64_t b)          | a->Dn<br>b->Dm         | CMGT Dd,Dn,Dm             | Dd->result     | A64                     |
| uint64_t vcgtld_u64(uint64_t a, uint64_t b)        | a->Dn<br>b->Dm         | CMHI Dd,Dn,Dm             | Dd->result     | A64                     |
| uint32_t vcgts_f32(float32_t a, float32_t b)       | a->Sn<br>b->Sm         | FCMGTE Sd,Sn,Sm           | Sd->result     | A64                     |
| uint64_t vcgtld_f64(float64_t a, float64_t b)      | a->Dn<br>b->Dm         | FCMGT Dd,Dn,Dm            | Dd->result     | A64                     |
| uint8x8_t vcgtz_s8(int8x8_t a)                     | a->Vn,8B               | CMGT Vd,8B,Vn,8B,#0       | Vd,8B->result  | A64                     |

| Intrinsic                                        | Argument Preparation       | Instruction                      | Result           | Supported Architectures |
|--------------------------------------------------|----------------------------|----------------------------------|------------------|-------------------------|
| uint8x16_vqgtzq_s8(int8x16_t a)                  | a -> Vn.16B                | CMGT Vd.16B.Vn.16B.#0            | Vd.16B -> result | A64                     |
| uint16x8_vqgtzq_s16(int16x8_t a)                 | a -> Vn.4H                 | CMGT Vd.8H.Vn.4H.#0              | Vd.4H -> result  | A64                     |
| uint16x8_vqgtzq_s16(int16x8_t a)                 | a -> Vn.8H                 | CMGT Vd.8H.Vn.8H.#0              | Vd.8H -> result  | A64                     |
| uint32x2_vqgtzq_s32(int32x2_t a)                 | a -> Vn.2S                 | CMGT Vd.2S.Vn.2S.#0              | Vd.2S -> result  | A64                     |
| uint32x2_vqgtzq_s32(int32x2_t a)                 | a -> Vn.4S                 | CMGT Vd.4S.Vn.4S.#0              | Vd.4S -> result  | A64                     |
| uint64x1_vqgtzq_s64(int64x1_t a)                 | a -> Vn.8B                 | CMGT Vd.8B.Vn.8B.#0              | Vd.8B -> result  | A64                     |
| uint64x2_vqgtzq_s64(int64x2_t a)                 | a -> Vn.2D                 | CMGT Vd.2D.Vn.2D.#0              | Vd.2D -> result  | A64                     |
| uint32x2_vqgtzq_s32(float32x2_t a)               | a -> Vn.2S                 | FCMGT Vd.2S.Vn.2S.#0             | Vd.2S -> result  | A64                     |
| uint32x2_vqgtzq_s32(float32x2_t a)               | a -> Vn.4S                 | FCMGT Vd.4S.Vn.4S.#0             | Vd.4S -> result  | A64                     |
| uint64x1_vqgtzq_s64(float64x1_t a)               | a -> Vn.8B                 | FCMGT Vd.8B.Vn.8B.#0             | Vd.8B -> result  | A64                     |
| uint64x2_vqgtzq_s64(float64x2_t a)               | a -> Vn.2D                 | FCMGT Vd.2D.Vn.2D.#0             | Vd.2D -> result  | A64                     |
| uint64x1_vqgtzq_s64(int64x1_t a)                 | a -> Vn.8B                 | FCMGT Dd.Dn.#0                   | Dd -> result     | A64                     |
| uint64x2_vqgtzq_s64(int64x2_t a)                 | a -> Vn.2D                 | FCMGT Dd.Dn.#0                   | Dd -> result     | A64                     |
| uint64x1_vqgtzq_s64(float64x1_t a)               | a -> Vn.8B                 | FCMGT Dd.Dn.#0                   | Dd -> result     | A64                     |
| uint64x2_vqgtq_s64(int64x2_t a)                  | a -> Vn.2D                 | FCMGT Dd.Dn.#0                   | Dd -> result     | A64                     |
| uint8x16_vqthq_s8(int8x16_t a, int8x16_t b)      | a -> Vn.16B<br>b -> Vn.16B | CMGT Vd.16B.Vm.16B.Vn.16B result | Vd.16B -> result | V7/A32/A64              |
| uint16x8_vqthq_s16(int16x8_t a, int16x8_t b)     | a -> Vn.4H<br>b -> Vn.4H   | CMGT Vd.4H.Vm.4H.Vn.4H           | Vd.4H -> result  | V7/A32/A64              |
| uint16x8_vqthq_s16(int16x8_t a, int16x8_t b)     | a -> Vn.8H<br>b -> Vn.8H   | CMGT Vd.8H.Vm.8H.Vn.8H           | Vd.8H -> result  | V7/A32/A64              |
| uint32x2_vqthq_s32(int32x2_t a, int32x2_t b)     | a -> Vn.2S<br>b -> Vn.2S   | CMGT Vd.2S.Vm.2S.Vn.2S           | Vd.2S -> result  | V7/A32/A64              |
| uint32x2_vqthq_s32(int32x2_t a, int32x2_t b)     | a -> Vn.4S<br>b -> Vn.4S   | CMGT Vd.4S.Vm.4S.Vn.4S           | Vd.4S -> result  | V7/A32/A64              |
| uint64x1_vqthq_s64(int64x1_t a, int64x1_t b)     | a -> Vn.8B<br>b -> Vn.8B   | CMHI Vd.8B.Vm.8B.Vn.8B           | Vd.8B -> result  | V7/A32/A64              |
| uint8x16_vqthq_s8(uint8x16_t a, uint8x16_t b)    | a -> Vn.16B<br>b -> Vn.16B | CMHI Vd.16B.Vm.16B.Vn.16B        | Vd.16B -> result | V7/A32/A64              |
| uint16x8_vqthq_s16(uint16x8_t a, uint16x8_t b)   | a -> Vn.4H<br>b -> Vn.4H   | CMHI Vd.4H.Vm.4H.Vn.4H           | Vd.4H -> result  | V7/A32/A64              |
| uint16x8_vqthq_s16(uint16x8_t a, uint16x8_t b)   | a -> Vn.8H<br>b -> Vn.8H   | CMHI Vd.8H.Vm.8H.Vn.8H           | Vd.8H -> result  | V7/A32/A64              |
| uint32x2_vqthq_s32(uint32x2_t a, uint32x2_t b)   | a -> Vn.2S<br>b -> Vn.2S   | CMHI Vd.2S.Vm.2S.Vn.2S           | Vd.2S -> result  | V7/A32/A64              |
| uint32x2_vqthq_s32(uint32x2_t a, uint32x2_t b)   | a -> Vn.4S<br>b -> Vn.4S   | CMHI Vd.4S.Vm.4S.Vn.4S           | Vd.4S -> result  | V7/A32/A64              |
| uint32x2_vqthq_s32(float32x2_t a, float32x2_t b) | a -> Vn.2S<br>b -> Vn.2S   | FCMGT Vd.2S.Vm.2S.Vn.2S          | Vd.2S -> result  | V7/A32/A64              |
| uint32x2_vqthq_s32(float32x2_t a, float32x2_t b) | a -> Vn.4S<br>b -> Vn.4S   | FCMGT Vd.4S.Vm.4S.Vn.4S          | Vd.4S -> result  | V7/A32/A64              |
| uint64x1_vqthq_s64(int64x1_t a, int64x1_t b)     | a -> Vn.8B<br>b -> Vn.8B   | CMGT Dd.Dm.Dn                    | Dd -> result     | A64                     |
| uint64x1_vqthq_s64(int64x2_t a, int64x2_t b)     | a -> Vn.2D<br>b -> Vn.2D   | CMGT Vd.2D.Vm.2D.Vn.2D           | Vd.2D -> result  | A64                     |
| uint64x1_vqthq_s64(float64x1_t a, float64x1_t b) | a -> Vn.8B<br>b -> Vn.8B   | CMHI Dd.Dm.Dn                    | Dd -> result     | A64                     |
| uint64x2_vqthq_s64(int64x2_t a, int64x2_t b)     | a -> Vn.2D<br>b -> Vn.2D   | CMHI Vd.2D.Vm.2D.Vn.2D           | Vd.2D -> result  | A64                     |
| uint64x1_vqthq_s64(float64x1_t a, float64x1_t b) | a -> Vn.8B<br>b -> Vn.8B   | FCMGT Dd.Dm.Dn                   | Dd -> result     | A64                     |
| uint64x2_vqthq_s64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vn.2D   | FCMGT Vd.2D.Vm.2D.Vn.2D          | Vd.2D -> result  | A64                     |
| uint64x1_vqthq_s64(int64x1_t a, int64x1_t b)     | a -> Vn.8B<br>b -> Vn.8B   | CMGT Dd.Dm.Dn                    | Dd -> result     | A64                     |
| uint64x1_vqthq_s64(int64x2_t a, int64x2_t b)     | a -> Vn.2D<br>b -> Vn.2D   | CMGT Vd.2D.Vm.2D.Vn.2D           | Vd.2D -> result  | A64                     |
| uint32x2_vqthq_s32(float32x2_t a, float32x2_t b) | a -> Vn.2S<br>b -> Vn.2S   | FCMGT Sd.Sm.Sn                   | Sd -> result     | A64                     |
| uint64x1_vqthq_s64(float64x1_t a, float64x1_t b) | a -> Vn.8B<br>b -> Vn.8B   | FCMGT Dd.Dm.Dn                   | Dd -> result     | A64                     |
| uint64x2_vqthq_s64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vn.2D   | FCMGT Vd.2D.Vm.2D.Vn.2D          | Vd.2D -> result  | A64                     |
| uint8x16_vqthq_s8(uint8x16_t a)                  | a -> Vn.16B                | CMGT Vd.16B.Vn.16B.#0            | Vd.16B -> result | A64                     |
| uint16x8_vqthq_s16(uint16x8_t a)                 | a -> Vn.4H                 | CMGT Vd.4H.Vn.4H.#0              | Vd.4H -> result  | A64                     |
| uint16x8_vqthq_s16(uint16x8_t a)                 | a -> Vn.8H                 | CMGT Vd.8H.Vn.8H.#0              | Vd.8H -> result  | A64                     |
| uint32x2_vqthq_s32(uint32x2_t a)                 | a -> Vn.2S                 | CMGT Vd.2S.Vn.2S.#0              | Vd.2S -> result  | A64                     |
| uint32x2_vqthq_s32(uint32x2_t a)                 | a -> Vn.4S                 | CMGT Vd.4S.Vn.4S.#0              | Vd.4S -> result  | A64                     |
| uint64x1_vqthq_s64(int64x1_t a)                  | a -> Vn.8B                 | CMGT Dd.Dn.#0                    | Dd -> result     | A64                     |
| uint64x2_vqthq_s64(int64x2_t a)                  | a -> Vn.2D                 | CMGT Vd.2D.Vn.2D.#0              | Vd.2D -> result  | A64                     |

| Intrinsic                                           | Argument Preparation   | Instruction                | Result          | Supported Architectures |
|-----------------------------------------------------|------------------------|----------------------------|-----------------|-------------------------|
| uint32x2_t vcltz_f32(float32x2_t a)                 | a->Vn,2S               | FCMLT Vd,2S,Vn,2S,#0       | Vd,2S-> result  | A64                     |
| uint32x4_t vcltzq_f32(float32x4_t a)                | a->Vn,4S               | FCMLT Vd,4S,Vn,4S,#0       | Vd,4S-> result  | A64                     |
| uint64x1_t vcltz_f64(float64x1_t a)                 | a->Dn                  | FCMLT Dd,Dn,#0             | Dd-> result     | A64                     |
| uint64x2_t vcltzq_f64(float64x2_t a)                | a->Vn,2D               | FCMLT Vd,2D,Vn,2D,#0       | Vd,2D-> result  | A64                     |
| uint64_t vcltzd_s64(int64_t a)                      | a->Dn                  | CMULT Dd,Dn,#0             | Dd-> result     | A64                     |
| uint32_t vcltzs_f32(float32_t a)                    | a->Sn                  | FCMLT Sd,Sn,#0             | Sd-> result     | A64                     |
| uint64_t vcltzd_f64(float64_t a)                    | a->Dn                  | FCMLT Dd,Dn,#0             | Dd-> result     | A64                     |
| uint32x2_t vcage_f32(float32x2_t a, float32x2_t b)  | a->Vn,2S<br>b->Vn,2S   | FACGE Vd,2S,Vn,2S,Vm,2S    | Vd,2S-> result  | v7/A32/A64              |
| uint32x4_t vcageq_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vn,4S   | FACGE Vd,4S,Vn,4S,Vm,4S    | Vd,4S-> result  | v7/A32/A64              |
| uint64x1_t vcage_f64(float64x1_t a, float64x1_t b)  | a->Dn<br>b->Dm         | FACGE Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint64x2_t vcageq_f64(float64x2_t a, float64x2_t b) | a->Vn,2D<br>b->Vn,2D   | FACGE Vd,2D,Vn,2D,Vm,2D    | Vd,2D-> result  | A64                     |
| uint32_t vcages_f32(float32_t a, float32_t b)       | a->Sn<br>b->Sm         | FACGE Sd,Sn,Sm             | Sd-> result     | A64                     |
| uint64_t vcages_f64(float64_t a, float64_t b)       | a->Dn<br>b->Dm         | FACGE Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint32x2_t vcale_f32(float32x2_t a, float32x2_t b)  | a->Vn,2S<br>b->Vn,2S   | FACGE Vd,2S,Vn,2S,Vm,2S    | Vd,2S-> result  | v7/A32/A64              |
| uint32x4_t vcaleq_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vn,4S   | FACGE Vd,4S,Vn,4S,Vm,4S    | Vd,4S-> result  | v7/A32/A64              |
| uint64x1_t vcale_f64(float64x1_t a, float64x1_t b)  | a->Dn<br>b->Dm         | FACGE Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint64x2_t vcaleq_f64(float64x2_t a, float64x2_t b) | a->Vn,2D<br>b->Vn,2D   | FACGE Vd,2D,Vn,2D,Vm,2D    | Vd,2D-> result  | A64                     |
| uint32_t vcales_f32(float32_t a, float32_t b)       | a->Sn<br>b->Sm         | FACGE Sd,Sn,Sm             | Sd-> result     | A64                     |
| uint64_t vcaled_f64(float64_t a, float64_t b)       | a->Dn<br>b->Dm         | FACGE Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint32x2_t vcagt_f32(float32x2_t a, float32x2_t b)  | a->Vn,2S<br>b->Vn,2S   | FACGT Vd,2S,Vn,2S,Vm,2S    | Vd,2S-> result  | v7/A32/A64              |
| uint32x4_t vcagtg_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vn,4S   | FACGT Vd,4S,Vn,4S,Vm,4S    | Vd,4S-> result  | v7/A32/A64              |
| uint64x1_t vcagt_f64(float64x1_t a, float64x1_t b)  | a->Dn<br>b->Dm         | FACGT Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint64x2_t vcagtg_f64(float64x2_t a, float64x2_t b) | a->Vn,2D<br>b->Vn,2D   | FACGT Vd,2D,Vn,2D,Vm,2D    | Vd,2D-> result  | A64                     |
| uint32_t vcagts_f32(float32_t a, float32_t b)       | a->Sn<br>b->Sm         | FACGT Sd,Sn,Sm             | Sd-> result     | A64                     |
| uint64_t vcagtd_f64(float64_t a, float64_t b)       | a->Dn<br>b->Dm         | FACGT Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint32x2_t vcallt_f32(float32x2_t a, float32x2_t b) | a->Vn,2S<br>b->Vn,2S   | FACGT Vd,2S,Vn,2S,Vm,2S    | Vd,2S-> result  | v7/A32/A64              |
| uint32x4_t vcallq_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vn,4S   | FACGT Vd,4S,Vn,4S,Vm,4S    | Vd,4S-> result  | v7/A32/A64              |
| uint64x1_t vcallt_f64(float64x1_t a, float64x1_t b) | a->Dn<br>b->Dm         | FACGT Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint64x2_t vcallq_f64(float64x2_t a, float64x2_t b) | a->Vn,2D<br>b->Vn,2D   | FACGT Vd,2D,Vn,2D,Vm,2D    | Vd,2D-> result  | A64                     |
| uint32_t vcallts_f32(float32_t a, float32_t b)      | a->Sn<br>b->Sm         | FACGT Sd,Sn,Sm             | Sd-> result     | A64                     |
| uint64_t vcalltd_f64(float64_t a, float64_t b)      | a->Dn<br>b->Dm         | FACGT Dd,Dn,Dm             | Dd-> result     | A64                     |
| uint8x8_t vstl_s8(int8x8_t a, int8x8_t b)           | a->Vn,8B<br>b->Vn,8B   | CMTST Vd,8B,Vn,8B,Vm,8B    | Vd,8B-> result  | v7/A32/A64              |
| uint8x16_t vstsq_s8(int8x16_t a, int8x16_t b)       | a->Vn,16B<br>b->Vn,16B | CMTST Vd,16B,Vn,16B,Vm,16B | Vd,16B-> result | v7/A32/A64              |
| uint16x4_t vstst_s16(int16x4_t a, int16x4_t b)      | a->Vn,4H<br>b->Vn,4H   | CMTST Vd,4H,Vn,4H,Vm,4H    | Vd,4H-> result  | v7/A32/A64              |
| uint16x8_t vstsq_s16(int16x8_t a, int16x8_t b)      | a->Vn,8H<br>b->Vn,8H   | CMTST Vd,8H,Vn,8H,Vm,8H    | Vd,8H-> result  | v7/A32/A64              |
| uint32x2_t vstst_s32(int32x2_t a, int32x2_t b)      | a->Vn,2S<br>b->Vn,2S   | CMTST Vd,2S,Vn,2S,Vm,2S    | Vd,2S-> result  | v7/A32/A64              |
| uint32x4_t vstsq_s32(int32x4_t a, int32x4_t b)      | a->Vn,4S<br>b->Vn,4S   | CMTST Vd,4S,Vn,4S,Vm,4S    | Vd,4S-> result  | v7/A32/A64              |
| uint8x8_t vstl_u8(uint8x8_t a, uint8x8_t b)         | a->Vn,8B<br>b->Vn,8B   | CMTST Vd,8B,Vn,8B,Vm,8B    | Vd,8B-> result  | v7/A32/A64              |
| uint8x16_t vstsq_u8(uint8x16_t a, uint8x16_t b)     | a->Vn,16B<br>b->Vn,16B | CMTST Vd,16B,Vn,16B,Vm,16B | Vd,16B-> result | v7/A32/A64              |
| uint16x4_t vstst_u16(uint16x4_t a, uint16x4_t b)    | a->Vn,4H<br>b->Vn,4H   | CMTST Vd,4H,Vn,4H,Vm,4H    | Vd,4H-> result  | v7/A32/A64              |

| Intrinsic                                           | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|-----------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| uint16x8_t vtsq_u16(uint16x8_t a, uint16x8_t b)     | a -> Vn.8H<br>b -> Vm.8H   | CMTST Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vtsq_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | CMTST Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vtsq_u32(uint32x4_t a, uint32x4_t b)     | a -> Vn.4S<br>b -> Vm.4S   | CMTST Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vstl_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | CMTST Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vstq_p8(poly8x16_t a, poly8x16_t b)      | a -> Vn.16B<br>b -> Vm.16B | CMTST Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t vstl_s64(int64x1_t a, int64x1_t b)       | a -> Dn<br>b -> Dm         | CMTST Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint64x2_t vstq_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | CMTST Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint64x1_t vstl_u64(uint64x1_t a, uint64x1_t b)     | a -> Dn<br>b -> Dm         | CMTST Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint64x2_t vstq_u64(uint64x2_t a, uint64x2_t b)     | a -> Vn.2D<br>b -> Vm.2D   | CMTST Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint64x1_t vstl_p64(poly64x1_t a, poly64x1_t b)     | a -> Dn<br>b -> Dm         | CMTST Dd,Dn,Dm             | Dd -> result     | A32/A64                 |
| uint64x2_t vstq_p64(poly64x2_t a, poly64x2_t b)     | a -> Vn.2D<br>b -> Vm.2D   | CMTST Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A32/A64                 |
| uint64_t vstd_s64(int64_t a, int64_t b)             | a -> Dn<br>b -> Dm         | CMTST Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint64_t vstd_u64(uint64_t a, uint64_t b)           | a -> Dn<br>b -> Dm         | CMTST Dd,Dn,Dm             | Dd -> result     | A64                     |
| int8x8_t vabd_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | SABD Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vabdq_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | SABD Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vabd_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | SABD Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vabdq_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | SABD Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vabd_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | SABD Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vabdq_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | SABD Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vabd_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UABD Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vabdq_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UABD Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vabd_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UABD Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vabdq_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UABD Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vabd_s32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | UABD Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vabdq_s32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | UABD Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| float32x2_t vabd_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | FABD Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t vabdq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FABD Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| float64x1_t vabd_f64(float64x1_t a, float64x1_t b)  | a -> Dn<br>b -> Dm         | FABD Dd,Dn,Dm              | Dd -> result     | A64                     |
| float64x2_t vabdq_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FABD Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | A64                     |
| float32_t vabds_f32(float32_t a, float32_t b)       | a -> Sn<br>b -> Sm         | FABD Sd,Sn,Sm              | Sd -> result     | A64                     |
| float64_t vabdd_f64(float64_t a, float64_t b)       | a -> Dn<br>b -> Dm         | FABD Dd,Dn,Dm              | Dd -> result     | A64                     |
| int16x8_t vabdl_s8(int8x8_t a, int8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | SABDL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vabdl_s16(int16x4_t a, int16x4_t b)       | a -> Vn.4H<br>b -> Vm.4H   | SABDL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vabdl_s32(int32x2_t a, int32x2_t b)       | a -> Vn.2S<br>b -> Vm.2S   | SABDL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vabdl_u8(uint8x8_t a, uint8x8_t b)       | a -> Vn.8B<br>b -> Vm.8B   | UABDL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vabdl_u16(uint16x4_t a, uint16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | UABDL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |

| Intrinsic                                                      | Argument Preparation                      | Instruction                | Result           | Supported Architectures |
|----------------------------------------------------------------|-------------------------------------------|----------------------------|------------------|-------------------------|
| uint64x2_t vabdl_u32(uint32x2_t a, uint32x2_t b)               | a -> Vn.2S<br>b -> Vm.2S                  | UABDL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vabdl_high_s8(int8x16_t a, int8x16_t b)              | a -> Vn.16B<br>b -> Vm.16B                | SABDL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| int32x4_t vabdl_high_s16(int16x8_t a, int16x8_t b)             | a -> Vn.8H<br>b -> Vm.8H                  | SABDL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| int64x2_t vabdl_high_s32(int32x4_t a, int32x4_t b)             | a -> Vn.4S<br>b -> Vm.4S                  | SABDL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| uint16x8_t vabdl_high_u8(uint8x16_t a, uint8x16_t b)           | a -> Vn.16B<br>b -> Vm.16B                | UABDL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| uint32x4_t vabdl_high_u16(uint16x8_t a, uint16x8_t b)          | a -> Vn.8H<br>b -> Vm.8H                  | UABDL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| uint64x2_t vabdl_high_u32(uint32x4_t a, uint32x4_t b)          | a -> Vn.4S<br>b -> Vm.4S                  | UABDL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| int8x8_t vaba_s8(int8x8_t a, int8x8_t b, int8x8_t c)           | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | SABA Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vabaq_s8(int8x16_t a, int8x16_t b, int8x16_t c)      | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | SABA Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vaba_s16(int16x4_t a, int16x4_t b, int16x4_t c)      | a -> Vd.4H<br>b -> Vn.4H<br>c -> Vm.4H    | SABA Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vabaq_s16(int16x8_t a, int16x8_t b, int16x8_t c)     | a -> Vd.8H<br>b -> Vn.8H<br>c -> Vm.8H    | SABA Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vaba_s32(int32x2_t a, int32x2_t b, int32x2_t c)      | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S    | SABA Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vabaq_s32(int32x4_t a, int32x4_t b, int32x4_t c)     | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S    | SABA Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vaba_u8(uint8x8_t a, uint8x8_t b, uint8x8_t c)       | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | UABA Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vabaq_u8(uint8x16_t a, uint8x16_t b, uint8x16_t c)  | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | UABA Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vaba_u16(uint16x4_t a, uint16x4_t b, uint16x4_t c)  | a -> Vd.4H<br>b -> Vn.4H<br>c -> Vm.4H    | UABA Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vabaq_u16(uint16x8_t a, uint16x8_t b, uint16x8_t c) | a -> Vd.8H<br>b -> Vn.8H<br>c -> Vm.8H    | UABA Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vaba_u32(uint32x2_t a, uint32x2_t b, uint32x2_t c)  | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S    | UABA Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vabaq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c) | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S    | UABA Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| int16x8_t vabal_s8(int16x8_t a, int8x8_t b, int8x8_t c)        | a -> Vd.8H<br>b -> Vn.8B<br>c -> Vm.8B    | SABAL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vabal_s16(int32x4_t a, int16x4_t b, int16x4_t c)     | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H    | SABAL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vabal_s32(int64x2_t a, int32x2_t b, int32x2_t c)     | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S    | SABAL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| uint16x8_t vabal_u8(uint16x8_t a, uint8x8_t b, uint8x8_t c)    | a -> Vd.8H<br>b -> Vn.8B<br>c -> Vm.8B    | UABAL Vd.8H,Vn.8B,Vm.8B    | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vabal_u16(uint32x4_t a, uint16x4_t b, uint16x4_t c) | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.4H    | UABAL Vd.4S,Vn.4H,Vm.4H    | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vabal_u32(uint64x2_t a, uint32x2_t b, uint32x2_t c) | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.2S    | UABAL Vd.2D,Vn.2S,Vm.2S    | Vd.2D -> result  | v7/A32/A64              |
| int16x8_t vabal_high_s8(int16x8_t a, int8x16_t b, int8x16_t c) | a -> Vd.8H<br>b -> Vn.16B<br>c -> Vm.16B  | SABAL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |

| Intrinsic                                                           | Argument Preparation                     | Instruction                | Result           | Supported Architectures |
|---------------------------------------------------------------------|------------------------------------------|----------------------------|------------------|-------------------------|
| int32x4_t vabal_high_s16(int32x4_t a, int16x8_t b, int16x8_t c)     | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H   | SABAL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| int64x2_t vabal_high_s32(int64x2_t a, int32x4_t b, int32x4_t c)     | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S   | SABAL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| uint16x8_t vabal_high_u8(uint16x8_t a, uint8x16_t b, uint8x16_t c)  | a -> Vd.8H<br>b -> Vn.16B<br>c -> Vm.16B | UABAL2 Vd.8H,Vn.16B,Vm.16B | Vd.8H -> result  | A64                     |
| uint32x4_t vabal_high_u16(uint32x4_t a, uint16x8_t b, uint16x8_t c) | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.8H   | UABAL2 Vd.4S,Vn.8H,Vm.8H   | Vd.4S -> result  | A64                     |
| uint64x2_t vabal_high_u32(uint64x2_t a, uint32x4_t b, uint32x4_t c) | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.4S   | UABAL2 Vd.2D,Vn.4S,Vm.4S   | Vd.2D -> result  | A64                     |
| int8x8_t vmax_s8(int8x8_t a, int8x8_t b)                            | a -> Vn.8B<br>b -> Vm.8B                 | SMAX Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | V7/A32/A64              |
| int8x16_t vmaxq_s8(int8x16_t a, int8x16_t b)                        | a -> Vn.16B<br>b -> Vm.16B               | SMAX Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | V7/A32/A64              |
| int16x4_t vmax_s16(int16x4_t a, int16x4_t b)                        | a -> Vn.4H<br>b -> Vm.4H                 | SMAX Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | V7/A32/A64              |
| int16x8_t vmaxq_s16(int16x8_t a, int16x8_t b)                       | a -> Vn.8H<br>b -> Vm.8H                 | SMAX Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | V7/A32/A64              |
| int32x2_t vmax_s32(int32x2_t a, int32x2_t b)                        | a -> Vn.2S<br>b -> Vm.2S                 | SMAX Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | V7/A32/A64              |
| int32x4_t vmaxq_s32(int32x4_t a, int32x4_t b)                       | a -> Vn.4S<br>b -> Vm.4S                 | SMAX Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | V7/A32/A64              |
| uint8x8_t vmax_u8(uint8x8_t a, uint8x8_t b)                         | a -> Vn.8B<br>b -> Vm.8B                 | UMAX Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | V7/A32/A64              |
| uint8x16_t vmaxq_u8(uint8x16_t a, uint8x16_t b)                     | a -> Vn.16B<br>b -> Vm.16B               | UMAX Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | V7/A32/A64              |
| uint16x4_t vmax_u16(uint16x4_t a, uint16x4_t b)                     | a -> Vn.4H<br>b -> Vm.4H                 | UMAX Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | V7/A32/A64              |
| uint16x8_t vmaxq_u16(uint16x8_t a, uint16x8_t b)                    | a -> Vn.8H<br>b -> Vm.8H                 | UMAX Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | V7/A32/A64              |
| uint32x2_t vmax_u32(uint32x2_t a, uint32x2_t b)                     | a -> Vn.2S<br>b -> Vm.2S                 | UMAX Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | V7/A32/A64              |
| uint32x4_t vmaxq_u32(uint32x4_t a, uint32x4_t b)                    | a -> Vn.4S<br>b -> Vm.4S                 | UMAX Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | V7/A32/A64              |
| float32x2_t vmax_f32(float32x2_t a, float32x2_t b)                  | a -> Vn.2S<br>b -> Vm.2S                 | FMAX Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | V7/A32/A64              |
| float32x4_t vmaxq_f32(float32x4_t a, float32x4_t b)                 | a -> Vn.4S<br>b -> Vm.4S                 | FMAX Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | V7/A32/A64              |
| float64x1_t vmax_f64(float64x1_t a, float64x1_t b)                  | a -> Dn<br>b -> Dm                       | FMAX Dd,Dn,Dm              | Dd -> result     | A64                     |
| float64x2_t vmaxq_f64(float64x2_t a, float64x2_t b)                 | a -> Vn.2D<br>b -> Vm.2D                 | FMAX Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | A64                     |
| int8x8_t vmin_s8(int8x8_t a, int8x8_t b)                            | a -> Vn.8B<br>b -> Vm.8B                 | SMIN Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | V7/A32/A64              |
| int8x16_t vminq_s8(int8x16_t a, int8x16_t b)                        | a -> Vn.16B<br>b -> Vm.16B               | SMIN Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | V7/A32/A64              |
| int16x4_t vmin_s16(int16x4_t a, int16x4_t b)                        | a -> Vn.4H<br>b -> Vm.4H                 | SMIN Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | V7/A32/A64              |
| int16x8_t vminq_s16(int16x8_t a, int16x8_t b)                       | a -> Vn.8H<br>b -> Vm.8H                 | SMIN Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | V7/A32/A64              |
| int32x2_t vmin_s32(int32x2_t a, int32x2_t b)                        | a -> Vn.2S<br>b -> Vm.2S                 | SMIN Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | V7/A32/A64              |
| int32x4_t vminq_s32(int32x4_t a, int32x4_t b)                       | a -> Vn.4S<br>b -> Vm.4S                 | SMIN Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | V7/A32/A64              |
| uint8x8_t vmin_u8(uint8x8_t a, uint8x8_t b)                         | a -> Vn.8B<br>b -> Vm.8B                 | UMIN Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | V7/A32/A64              |
| uint8x16_t vminq_u8(uint8x16_t a, uint8x16_t b)                     | a -> Vn.16B<br>b -> Vm.16B               | UMIN Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | V7/A32/A64              |
| uint16x4_t vmin_u16(uint16x4_t a, uint16x4_t b)                     | a -> Vn.4H<br>b -> Vm.4H                 | UMIN Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | V7/A32/A64              |
| uint16x8_t vminq_u16(uint16x8_t a, uint16x8_t b)                    | a -> Vn.8H<br>b -> Vm.8H                 | UMIN Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | V7/A32/A64              |
| uint32x2_t vmin_u32(uint32x2_t a, uint32x2_t b)                     | a -> Vn.2S<br>b -> Vm.2S                 | UMIN Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | V7/A32/A64              |
| uint32x4_t vminq_u32(uint32x4_t a, uint32x4_t b)                    | a -> Vn.4S<br>b -> Vm.4S                 | UMIN Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | V7/A32/A64              |
| float32x2_t vmin_f32(float32x2_t a, float32x2_t b)                  | a -> Vn.2S<br>b -> Vm.2S                 | FMIN Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | V7/A32/A64              |

| Intrinsic                                           | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|-----------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| float32x4_t vminq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FMIN Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| float64x1_t vmin_f64(float64x1_t a, float64x1_t b)  | a -> Dn<br>b -> Dm         | FMIN Dd,Dn,Dm              | Dd -> result     | A64                     |
| float64x2_t vminq_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FMIN Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | A64                     |
| float32x2_t vmaxm_f32(float32x2_t a, float32x2_t b) | a -> Vn.2S<br>b -> Vm.2S   | FMAXNM Vd.2S,Vn.2S,Vm.2S   | Vd.2S -> result  | A32/A64                 |
| float32x4_t vmaxm_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FMAXNM Vd.4S,Vn.4S,Vm.4S   | Vd.4S -> result  | A32/A64                 |
| float64x1_t vmaxm_f64(float64x1_t a, float64x1_t b) | a -> Dn<br>b -> Dm         | FMAXNM Dd,Dn,Dm            | Dd -> result     | A64                     |
| float64x2_t vmaxm_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FMAXNM Vd.2D,Vn.2D,Vm.2D   | Vd.2D -> result  | A64                     |
| float32x2_t vminm_f32(float32x2_t a, float32x2_t b) | a -> Vn.2S<br>b -> Vm.2S   | FMINNM Vd.2S,Vn.2S,Vm.2S   | Vd.2S -> result  | A32/A64                 |
| float32x4_t vminm_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FMINNM Vd.4S,Vn.4S,Vm.4S   | Vd.4S -> result  | A32/A64                 |
| float64x1_t vminm_f64(float64x1_t a, float64x1_t b) | a -> Dn<br>b -> Dm         | FMINNM Dd,Dn,Dm            | Dd -> result     | A64                     |
| float64x2_t vminm_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FMINNM Vd.2D,Vn.2D,Vm.2D   | Vd.2D -> result  | A64                     |
| int8x8_t vshl_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | SSHL Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vshlq_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | SSHL Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vshl_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | SSHL Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vshlq_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | SSHL Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vshl_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | SSHL Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vshlq_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | SSHL Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vshl_s64(int64x1_t a, int64x1_t b)        | a -> Dn<br>b -> Dm         | SSHL Dd,Dn,Dm              | Dd -> result     | v7/A32/A64              |
| int64x2_t vshlq_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | SSHL Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vshl_u8(uint8x8_t a, int8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | USHL Vd.8B,Vn.8B,Vm.8B     | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vshlq_u8(uint8x16_t a, int8x16_t b)      | a -> Vn.16B<br>b -> Vm.16B | USHL Vd.16B,Vn.16B,Vm.16B  | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vshl_u16(uint16x4_t a, int16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | USHL Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vshlq_u16(uint16x8_t a, int16x8_t b)     | a -> Vn.8H<br>b -> Vm.8H   | USHL Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vshl_u32(uint32x2_t a, int32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | USHL Vd.2S,Vn.2S,Vm.2S     | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vshlq_u32(uint32x4_t a, int32x4_t b)     | a -> Vn.4S<br>b -> Vm.4S   | USHL Vd.4S,Vn.4S,Vm.4S     | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vshl_u64(uint64x1_t a, int64x1_t b)      | a -> Dn<br>b -> Dm         | USHL Dd,Dn,Dm              | Dd -> result     | v7/A32/A64              |
| uint64x2_t vshlq_u64(uint64x2_t a, int64x2_t b)     | a -> Vn.2D<br>b -> Vm.2D   | USHL Vd.2D,Vn.2D,Vm.2D     | Vd.2D -> result  | v7/A32/A64              |
| int64_t vshld_s64(int64_t a, int64_t b)             | a -> Dn<br>b -> Dm         | SSHL Dd,Dn,Dm              | Dd -> result     | A64                     |
| uint64_t vshld_u64(uint64_t a, int64_t b)           | a -> Dn<br>b -> Dm         | USHL Dd,Dn,Dm              | Dd -> result     | A64                     |
| int8x8_t vqshl_s8(int8x8_t a, int8x8_t b)           | a -> Vn.8B<br>b -> Vm.8B   | SQSHL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vqshlq_s8(int8x16_t a, int8x16_t b)       | a -> Vn.16B<br>b -> Vm.16B | SQSHL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vqshl_s16(int16x4_t a, int16x4_t b)       | a -> Vn.4H<br>b -> Vm.4H   | SQSHL Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vqshlq_s16(int16x8_t a, int16x8_t b)      | a -> Vn.8H<br>b -> Vm.8H   | SQSHL Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vqshl_s32(int32x2_t a, int32x2_t b)       | a -> Vn.2S<br>b -> Vm.2S   | SQSHL Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vqshlq_s32(int32x4_t a, int32x4_t b)      | a -> Vn.4S<br>b -> Vm.4S   | SQSHL Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vqshlq_s64(int64x1_t a, int64x1_t b)      | a -> Dn<br>b -> Dm         | SQSHL Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |

| Intrinsic                                        | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|--------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| int64x2_t vqshlq_s64(int64x2_t a, int64x2_t b)   | a -> Vn.2D<br>b -> Vm.2D   | SQSHL Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vqshl_u8(uint8x8_t a, int8x8_t b)      | a -> Vn.8B<br>b -> Vm.8B   | UQSHL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vqshlq_u8(uint8x16_t a, int8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | UQSHL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vqshl_u16(uint16x4_t a, int16x4_t b)  | a -> Vn.4H<br>b -> Vm.4H   | UQSHL Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vqshlq_u16(uint16x8_t a, int16x8_t b) | a -> Vn.8H<br>b -> Vm.8H   | UQSHL Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vqshl_u32(uint32x2_t a, int32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | UQSHL Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vqshlq_u32(uint32x4_t a, int32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | UQSHL Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vqshlq_u64(uint64x1_t a, int64x1_t b) | a -> Dn<br>b -> Dm         | UQSHL Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| uint64x2_t vqshlq_u64(uint64x2_t a, int64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | UQSHL Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | v7/A32/A64              |
| int8_t vqshlb_s8(int8_t a, int8_t b)             | a -> Bn<br>b -> Bm         | SQSHL Bd,Bn,Bm             | Bd -> result     | A64                     |
| int16_t vqshl_s16(int16_t a, int16_t b)          | a -> Hn<br>b -> Hm         | SQSHL Hd,Hn,Hm             | Hd -> result     | A64                     |
| int32_t vqshls_s32(int32_t a, int32_t b)         | a -> Sn<br>b -> Sm         | SQSHL Sd,Sn,Sm             | Sd -> result     | A64                     |
| int64_t vqshld_s64(int64_t a, int64_t b)         | a -> Dn<br>b -> Dm         | SQSHL Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint8_t vqshlb_u8(uint8_t a, int8_t b)           | a -> Bn<br>b -> Bm         | UQSHL Bd,Bn,Bm             | Bd -> result     | A64                     |
| uint16_t vqshlq_u16(uint16_t a, int16_t b)       | a -> Hn<br>b -> Hm         | UQSHL Hd,Hn,Hm             | Hd -> result     | A64                     |
| uint32_t vqshls_u32(uint32_t a, int32_t b)       | a -> Sn<br>b -> Sm         | UQSHL Sd,Sn,Sm             | Sd -> result     | A64                     |
| uint64_t vqshld_u64(uint64_t a, int64_t b)       | a -> Dn<br>b -> Dm         | UQSHL Dd,Dn,Dm             | Dd -> result     | A64                     |
| int8x8_t vrshl_s8(int8x8_t a, int8x8_t b)        | a -> Vn.8B<br>b -> Vm.8B   | SRSHL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vrshlq_s8(int8x16_t a, int8x16_t b)    | a -> Vn.16B<br>b -> Vm.16B | SRSHL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vrshl_s16(int16x4_t a, int16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | SRSHL Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vrshlq_s16(int16x8_t a, int16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | SRSHL Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vrshl_s32(int32x2_t a, int32x2_t b)    | a -> Vn.2S<br>b -> Vm.2S   | SRSHL Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vrshlq_s32(int32x4_t a, int32x4_t b)   | a -> Vn.4S<br>b -> Vm.4S   | SRSHL Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vrshlq_s64(int64x1_t a, int64x1_t b)   | a -> Dn<br>b -> Dm         | SRSHL Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| int64x2_t vrshlq_s64(int64x2_t a, int64x2_t b)   | a -> Vn.2D<br>b -> Vm.2D   | SRSHL Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vrshl_u8(uint8x8_t a, int8x8_t b)      | a -> Vn.8B<br>b -> Vm.8B   | URSHL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vrshlq_u8(uint8x16_t a, int8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | URSHL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vrshlq_u16(uint16x4_t a, int16x4_t b) | a -> Vn.4H<br>b -> Vm.4H   | URSHL Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vrshlq_u16(uint16x8_t a, int16x8_t b) | a -> Vn.8H<br>b -> Vm.8H   | URSHL Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vrshlq_u32(uint32x2_t a, int32x2_t b) | a -> Vn.2S<br>b -> Vm.2S   | URSHL Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vrshlq_u32(uint32x4_t a, int32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | URSHL Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vrshlq_u64(uint64x1_t a, int64x1_t b) | a -> Dn<br>b -> Dm         | URSHL Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| uint64x2_t vrshlq_u64(uint64x2_t a, int64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | URSHL Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | v7/A32/A64              |
| int64_t vrshld_s64(int64_t a, int64_t b)         | a -> Dn<br>b -> Dm         | SRSHL Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint64_t vrshld_u64(uint64_t a, int64_t b)       | a -> Dn<br>b -> Dm         | URSHL Dd,Dn,Dm             | Dd -> result     | A64                     |
| int8x8_t vqrshl_s8(int8x8_t a, int8x8_t b)       | a -> Vn.8B<br>b -> Vm.8B   | SQRSHL Vd.8B,Vn.8B,Vm.8B   | Vd.8B -> result  | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation       | Instruction                 | Result           | Supported Architectures |
|---------------------------------------------------|----------------------------|-----------------------------|------------------|-------------------------|
| int8x16_t vqrshl_s8(int8x16_t a, int8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | SQRSHL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vqrshl_s16(int16x4_t a, int16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | SQRSHL Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vqrshlq_s16(int16x8_t a, int16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | SQRSHL Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vqrshl_s32(int32x2_t a, int32x2_t b)    | a -> Vn.2S<br>b -> Vm.2S   | SQRSHL Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vqrshlq_s32(int32x4_t a, int32x4_t b)   | a -> Vn.4S<br>b -> Vm.4S   | SQRSHL Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vqrshl_s64(int64x1_t a, int64x1_t b)    | a -> Dn<br>b -> Dm         | SQRSHL Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| int64x2_t vqrshlq_s64(int64x2_t a, int64x2_t b)   | a -> Vn.2D<br>b -> Vm.2D   | SQRSHL Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vqrshl_u8(uint8x8_t a, int8x8_t b)      | a -> Vn.8B<br>b -> Vm.8B   | UQRSHL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vqrshlq_u8(uint8x16_t a, int8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | UQRSHL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vqrshl_u16(uint16x4_t a, int16x4_t b)  | a -> Vn.4H<br>b -> Vm.4H   | UQRSHL Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vqrshlq_u16(uint16x8_t a, int16x8_t b) | a -> Vn.8H<br>b -> Vm.8H   | UQRSHL Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vqrshl_u32(uint32x2_t a, int32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | UQRSHL Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vqrshlq_u32(uint32x4_t a, int32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | UQRSHL Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vqrshl_u64(uint64x1_t a, int64x1_t b)  | a -> Dn<br>b -> Dm         | UQRSHL Dd,Dn,Dm             | Dd -> result     | v7/A32/A64              |
| uint64x2_t vqrshlq_u64(uint64x2_t a, int64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | UQRSHL Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | v7/A32/A64              |
| int8_t vqrshlb_s8(int8_t a, int8_t b)             | a -> Bn<br>b -> Bm         | SQRSHL Bd,Bn,Bm             | Bd -> result     | A64                     |
| int16_t vqrshlb_s16(int16_t a, int16_t b)         | a -> Hn<br>b -> Hm         | SQRSHL Hd,Hn,Hm             | Hd -> result     | A64                     |
| int32_t vqrshlb_s32(int32_t a, int32_t b)         | a -> Sn<br>b -> Sm         | SQRSHL Sd,Sn,Sm             | Sd -> result     | A64                     |
| int64_t vqrshld_s64(int64_t a, int64_t b)         | a -> Dn<br>b -> Dm         | SQRSHL Dd,Dn,Dm             | Dd -> result     | A64                     |
| uint8_t vqrshlb_u8(uint8_t a, int8_t b)           | a -> Bn<br>b -> Bm         | UQRSHL Bd,Bn,Bm             | Bd -> result     | A64                     |
| uint16_t vqrshlb_u16(uint16_t a, int16_t b)       | a -> Hn<br>b -> Hm         | UQRSHL Hd,Hn,Hm             | Hd -> result     | A64                     |
| uint32_t vqrshlb_u32(uint32_t a, int32_t b)       | a -> Sn<br>b -> Sm         | UQRSHL Sd,Sn,Sm             | Sd -> result     | A64                     |
| uint64_t vqrshld_u64(uint64_t a, int64_t b)       | a -> Dn<br>b -> Dm         | UQRSHL Dd,Dn,Dm             | Dd -> result     | A64                     |
| int8x8_t vshrn_s8(int8x8_t a, const int n)        | a -> Vn.8B<br>1 <= n <= 8  | SSHR Vd.8B,Vn.8B,#n         | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vshrq_n_s8(int8x16_t a, const int n)    | a -> Vn.16B<br>1 <= n <= 8 | SSHR Vd.16B,Vn.16B,#n       | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vshrn_s16(int16x4_t a, const int n)     | a -> Vn.4H<br>1 <= n <= 16 | SSHR Vd.4H,Vn.4H,#n         | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vshrq_n_s16(int16x8_t a, const int n)   | a -> Vn.8H<br>1 <= n <= 16 | SSHR Vd.8H,Vn.8H,#n         | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vshrn_s32(int32x2_t a, const int n)     | a -> Vn.2S<br>1 <= n <= 32 | SSHR Vd.2S,Vn.2S,#n         | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vshrq_n_s32(int32x4_t a, const int n)   | a -> Vn.4S<br>1 <= n <= 32 | SSHR Vd.4S,Vn.4S,#n         | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vshrn_s64(int64x1_t a, const int n)     | a -> Dn<br>1 <= n <= 64    | SSHR Dd,Dn,#n               | Dd -> result     | v7/A32/A64              |
| int64x2_t vshrq_n_s64(int64x2_t a, const int n)   | a -> Vn.2D<br>1 <= n <= 64 | SSHR Vd.2D,Vn.2D,#n         | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vshrn_u8(uint8x8_t a, const int n)      | a -> Vn.8B<br>1 <= n <= 8  | USHR Vd.8B,Vn.8B,#n         | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vshrq_n_u8(uint8x16_t a, const int n)  | a -> Vn.16B<br>1 <= n <= 8 | USHR Vd.16B,Vn.16B,#n       | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vshrn_u16(uint16x4_t a, const int n)   | a -> Vn.4H<br>1 <= n <= 16 | USHR Vd.4H,Vn.4H,#n         | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vshrq_n_u16(uint16x8_t a, const int n) | a -> Vn.8H<br>1 <= n <= 16 | USHR Vd.8H,Vn.8H,#n         | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vshrn_u32(uint32x2_t a, const int n)   | a -> Vn.2S<br>1 <= n <= 32 | USHR Vd.2S,Vn.2S,#n         | Vd.2S -> result  | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation     | Instruction            | Result           | Supported Architectures |
|---------------------------------------------------|--------------------------|------------------------|------------------|-------------------------|
| uint32x4_t vshrq_n_u32(uint32x4_t a, const int n) | a->Vn,4S<br>1 <= n <= 32 | USHR Vd,4S,Vn,4S,#n    | Vd,4S -> result  | v7/A32/A64              |
| uint64x1_t vshrq_n_u64(uint64x1_t a, const int n) | a->Dn<br>1 <= n <= 64    | USHR Dd,Dn,#n          | Dd -> result     | v7/A32/A64              |
| uint64x2_t vshrq_n_u64(uint64x2_t a, const int n) | a->Vn,2D<br>1 <= n <= 64 | USHR Vd,2D,Vn,2D,#n    | Vd,2D -> result  | v7/A32/A64              |
| int64_t vshrd_n_s64(int64_t a, const int n)       | a->Dn<br>1 <= n <= 64    | SSHR Dd,Dn,#n          | Dd -> result     | A64                     |
| uint64_t vshrd_n_u64(uint64_t a, const int n)     | a->Dn<br>1 <= n <= 64    | USHR Dd,Dn,#n          | Dd -> result     | A64                     |
| int8x8_t vshl_n_s8(int8x8_t a, const int n)       | a->Vn,8B<br>0 <= n <= 7  | SHL Vd,8B,Vn,8B,#n     | Vd,8B -> result  | v7/A32/A64              |
| int8x16_t vshlq_n_s8(int8x16_t a, const int n)    | a->Vn,16B<br>0 <= n <= 7 | SHL Vd,16B,Vn,16B,#n   | Vd,16B -> result | v7/A32/A64              |
| int16x4_t vshlq_n_s16(int16x4_t a, const int n)   | a->Vn,4H<br>0 <= n <= 15 | SHL Vd,4H,Vn,4H,#n     | Vd,4H -> result  | v7/A32/A64              |
| int16x8_t vshlq_n_s16(int16x8_t a, const int n)   | a->Vn,8H<br>0 <= n <= 15 | SHL Vd,8H,Vn,8H,#n     | Vd,8H -> result  | v7/A32/A64              |
| int32x2_t vshlq_n_s32(int32x2_t a, const int n)   | a->Vn,2S<br>0 <= n <= 31 | SHL Vd,2S,Vn,2S,#n     | Vd,2S -> result  | v7/A32/A64              |
| int32x4_t vshlq_n_s32(int32x4_t a, const int n)   | a->Vn,4S<br>0 <= n <= 31 | SHL Vd,4S,Vn,4S,#n     | Vd,4S -> result  | v7/A32/A64              |
| int64x1_t vshlq_n_s64(int64x1_t a, const int n)   | a->Dn<br>0 <= n <= 63    | SHL Dd,Dn,#n           | Dd -> result     | v7/A32/A64              |
| int64x2_t vshlq_n_s64(int64x2_t a, const int n)   | a->Vn,2D<br>0 <= n <= 63 | SHL Vd,2D,Vn,2D,#n     | Vd,2D -> result  | v7/A32/A64              |
| uint8x8_t vshlq_n_u8(uint8x8_t a, const int n)    | a->Vn,8B<br>0 <= n <= 7  | SHL Vd,8B,Vn,8B,#n     | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vshlq_n_u8(uint8x16_t a, const int n)  | a->Vn,16B<br>0 <= n <= 7 | SHL Vd,16B,Vn,16B,#n   | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vshlq_n_u16(uint16x4_t a, const int n) | a->Vn,4H<br>0 <= n <= 15 | SHL Vd,4H,Vn,4H,#n     | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vshlq_n_u16(uint16x8_t a, const int n) | a->Vn,8H<br>0 <= n <= 15 | SHL Vd,8H,Vn,8H,#n     | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vshlq_n_u32(uint32x2_t a, const int n) | a->Vn,2S<br>0 <= n <= 31 | SHL Vd,2S,Vn,2S,#n     | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vshlq_n_u32(uint32x4_t a, const int n) | a->Vn,4S<br>0 <= n <= 31 | SHL Vd,4S,Vn,4S,#n     | Vd,4S -> result  | v7/A32/A64              |
| uint64x1_t vshlq_n_u64(uint64x1_t a, const int n) | a->Dn<br>0 <= n <= 63    | SHL Dd,Dn,#n           | Dd -> result     | v7/A32/A64              |
| uint64x2_t vshlq_n_u64(uint64x2_t a, const int n) | a->Vn,2D<br>0 <= n <= 63 | SHL Vd,2D,Vn,2D,#n     | Vd,2D -> result  | v7/A32/A64              |
| int64_t vshld_n_s64(int64_t a, const int n)       | a->Dn<br>0 <= n <= 63    | SHL Dd,Dn,#n           | Dd -> result     | A64                     |
| uint64_t vshld_n_u64(uint64_t a, const int n)     | a->Dn<br>0 <= n <= 63    | SHL Dd,Dn,#n           | Dd -> result     | A64                     |
| int8x8_t vshrq_n_s8(int8x8_t a, const int n)      | a->Vn,8B<br>1 <= n <= 8  | SRSHR Vd,8B,Vn,8B,#n   | Vd,8B -> result  | v7/A32/A64              |
| int8x16_t vshrq_n_s8(int8x16_t a, const int n)    | a->Vn,16B<br>1 <= n <= 8 | SRSHR Vd,16B,Vn,16B,#n | Vd,16B -> result | v7/A32/A64              |
| int16x4_t vshrq_n_s16(int16x4_t a, const int n)   | a->Vn,4H<br>1 <= n <= 16 | SRSHR Vd,4H,Vn,4H,#n   | Vd,4H -> result  | v7/A32/A64              |
| int16x8_t vshrq_n_s16(int16x8_t a, const int n)   | a->Vn,8H<br>1 <= n <= 16 | SRSHR Vd,8H,Vn,8H,#n   | Vd,8H -> result  | v7/A32/A64              |
| int32x2_t vshrq_n_s32(int32x2_t a, const int n)   | a->Vn,2S<br>1 <= n <= 32 | SRSHR Vd,2S,Vn,2S,#n   | Vd,2S -> result  | v7/A32/A64              |
| int32x4_t vshrq_n_s32(int32x4_t a, const int n)   | a->Vn,4S<br>1 <= n <= 32 | SRSHR Vd,4S,Vn,4S,#n   | Vd,4S -> result  | v7/A32/A64              |
| int64x1_t vshrq_n_s64(int64x1_t a, const int n)   | a->Dn<br>1 <= n <= 64    | SRSHR Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| int64x2_t vshrq_n_s64(int64x2_t a, const int n)   | a->Vn,2D<br>1 <= n <= 64 | SRSHR Vd,2D,Vn,2D,#n   | Vd,2D -> result  | v7/A32/A64              |
| uint8x8_t vshrq_n_u8(uint8x8_t a, const int n)    | a->Vn,8B<br>1 <= n <= 8  | URSHR Vd,8B,Vn,8B,#n   | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vshrq_n_u8(uint8x16_t a, const int n)  | a->Vn,16B<br>1 <= n <= 8 | URSHR Vd,16B,Vn,16B,#n | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vshrq_n_u16(uint16x4_t a, const int n) | a->Vn,4H<br>1 <= n <= 16 | URSHR Vd,4H,Vn,4H,#n   | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vshrq_n_u16(uint16x8_t a, const int n) | a->Vn,8H<br>1 <= n <= 16 | URSHR Vd,8H,Vn,8H,#n   | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vshrq_n_u32(uint32x2_t a, const int n) | a->Vn,2S<br>1 <= n <= 32 | URSHR Vd,2S,Vn,2S,#n   | Vd,2S -> result  | v7/A32/A64              |

| Intrinsic                                                       | Argument Preparation                  | Instruction           | Result           | Supported Architectures |
|-----------------------------------------------------------------|---------------------------------------|-----------------------|------------------|-------------------------|
| uint32x4_t vshrq_n_u32(uint32x4_t a, const int n)               | a->Vn,4S<br>1 <= n <= 32              | URSHR Vd,4S,Vn,4S,#n  | Vd,4S -> result  | v7/A32/A64              |
| uint64x1_t vshrn_n_u64(uint64x1_t a, const int n)               | a->Dn<br>1 <= n <= 64                 | URSHR Dd,Dn,#n        | Dd -> result     | v7/A32/A64              |
| uint64x2_t vshrq_n_u64(uint64x2_t a, const int n)               | a->Vn,2D<br>1 <= n <= 64              | URSHR Vd,2D,Vn,2D,#n  | Vd,2D -> result  | v7/A32/A64              |
| int64_t vshrd_n_s64(int64_t a, const int n)                     | a->Dn<br>1 <= n <= 64                 | SRSHR Dd,Dn,#n        | Dd -> result     | A64                     |
| uint64_t vshrd_n_u64(uint64_t a, const int n)                   | a->Dn<br>1 <= n <= 64                 | URSHR Dd,Dn,#n        | Dd -> result     | A64                     |
| int8x8_t vsra_n_s8(int8x8_t a, int8x8_t b, const int n)         | a->Vd,8B<br>b->Vn,8B<br>1 <= n <= 8   | SSRA Vd,8B,Vn,8B,#n   | Vd,8B -> result  | v7/A32/A64              |
| int8x16_t vsraq_n_s8(int8x16_t a, int8x16_t b, const int n)     | a->Vd,16B<br>b->Vn,16B<br>1 <= n <= 8 | SSRA Vd,16B,Vn,16B,#n | Vd,16B -> result | v7/A32/A64              |
| int16x4_t vsra_n_s16(int16x4_t a, int16x4_t b, const int n)     | a->Vd,4H<br>b->Vn,4H<br>1 <= n <= 16  | SSRA Vd,4H,Vn,4H,#n   | Vd,4H -> result  | v7/A32/A64              |
| int16x8_t vsraq_n_s16(int16x8_t a, int16x8_t b, const int n)    | a->Vd,8H<br>b->Vn,8H<br>1 <= n <= 16  | SSRA Vd,8H,Vn,8H,#n   | Vd,8H -> result  | v7/A32/A64              |
| int32x2_t vsra_n_s32(int32x2_t a, int32x2_t b, const int n)     | a->Vd,2S<br>b->Vn,2S<br>1 <= n <= 32  | SSRA Vd,2S,Vn,2S,#n   | Vd,2S -> result  | v7/A32/A64              |
| int32x4_t vsraq_n_s32(int32x4_t a, int32x4_t b, const int n)    | a->Vd,4S<br>b->Vn,4S<br>1 <= n <= 32  | SSRA Vd,4S,Vn,4S,#n   | Vd,4S -> result  | v7/A32/A64              |
| int64x1_t vsra_n_s64(int64x1_t a, int64x1_t b, const int n)     | a->Dd<br>b->Dn<br>1 <= n <= 64        | SSRA Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| int64x2_t vsraq_n_s64(int64x2_t a, int64x2_t b, const int n)    | a->Vd,2D<br>b->Vn,2D<br>1 <= n <= 64  | SSRA Vd,2D,Vn,2D,#n   | Vd,2D -> result  | v7/A32/A64              |
| uint8x8_t vsra_n_u8(uint8x8_t a, uint8x8_t b, const int n)      | a->Vd,8B<br>b->Vn,8B<br>1 <= n <= 8   | USRA Vd,8B,Vn,8B,#n   | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vsraq_n_u8(uint8x16_t a, uint8x16_t b, const int n)  | a->Vd,16B<br>b->Vn,16B<br>1 <= n <= 8 | USRA Vd,16B,Vn,16B,#n | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vsra_n_u16(uint16x4_t a, uint16x4_t b, const int n)  | a->Vd,4H<br>b->Vn,4H<br>1 <= n <= 16  | USRA Vd,4H,Vn,4H,#n   | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vsraq_n_u16(uint16x8_t a, uint16x8_t b, const int n) | a->Vd,8H<br>b->Vn,8H<br>1 <= n <= 16  | USRA Vd,8H,Vn,8H,#n   | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vsra_n_u32(uint32x2_t a, uint32x2_t b, const int n)  | a->Vd,2S<br>b->Vn,2S<br>1 <= n <= 32  | USRA Vd,2S,Vn,2S,#n   | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vsraq_n_u32(uint32x4_t a, uint32x4_t b, const int n) | a->Vd,4S<br>b->Vn,4S<br>1 <= n <= 32  | USRA Vd,4S,Vn,4S,#n   | Vd,4S -> result  | v7/A32/A64              |
| uint64x1_t vsra_n_u64(uint64x1_t a, uint64x1_t b, const int n)  | a->Dd<br>b->Dn<br>1 <= n <= 64        | USRA Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| uint64x2_t vsraq_n_u64(uint64x2_t a, uint64x2_t b, const int n) | a->Vd,2D<br>b->Vn,2D<br>1 <= n <= 64  | USRA Vd,2D,Vn,2D,#n   | Vd,2D -> result  | v7/A32/A64              |
| int64_t vsrad_n_s64(int64_t a, int64_t b, const int n)          | a->Dd<br>b->Dn<br>1 <= n <= 64        | SSRA Dd,Dn,#n         | Dd -> result     | A64                     |
| uint64_t vsrad_n_u64(uint64_t a, uint64_t b, const int n)       | a->Dd<br>b->Dn<br>1 <= n <= 64        | USRA Dd,Dn,#n         | Dd -> result     | A64                     |
| int8x8_t vsra_n_s8(int8x8_t a, int8x8_t b, const int n)         | a->Vd,8B<br>b->Vn,8B<br>1 <= n <= 8   | SRSA Vd,8B,Vn,8B,#n   | Vd,8B -> result  | v7/A32/A64              |
| int8x16_t vsraq_n_s8(int8x16_t a, int8x16_t b, const int n)     | a->Vd,16B<br>b->Vn,16B<br>1 <= n <= 8 | SRSA Vd,16B,Vn,16B,#n | Vd,16B -> result | v7/A32/A64              |
| int16x4_t vsra_n_s16(int16x4_t a, int16x4_t b, const int n)     | a->Vd,4H<br>b->Vn,4H<br>1 <= n <= 16  | SRSA Vd,4H,Vn,4H,#n   | Vd,4H -> result  | v7/A32/A64              |

| Intrinsic                                                        | Argument Preparation                      | Instruction            | Result           | Supported Architectures |
|------------------------------------------------------------------|-------------------------------------------|------------------------|------------------|-------------------------|
| int16x8_t vrsraq_n_s16(int16x8_t a, int16x8_t b, const int n)    | a -> Vd.8H<br>b -> Vn.8H<br>1 <= n <= 16  | SRSA Vd.8H.Vn.8H.#n    | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vrsra_n_s32(int32x2_t a, int32x2_t b, const int n)     | a -> Vd.2S<br>b -> Vn.2S<br>1 <= n <= 32  | SRSA Vd.2S.Vn.2S.#n    | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vrsraq_n_s32(int32x4_t a, int32x4_t b, const int n)    | a -> Vd.4S<br>b -> Vn.4S<br>1 <= n <= 32  | SRSA Vd.4S.Vn.4S.#n    | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vrsra_n_s64(int64x1_t a, int64x1_t b, const int n)     | a -> Dd<br>b -> Dn<br>1 <= n <= 64        | SRSA Dd.Dn.#n          | Dd -> result     | v7/A32/A64              |
| int64x2_t vrsraq_n_s64(int64x2_t a, int64x2_t b, const int n)    | a -> Vd.2D<br>b -> Vn.2D<br>1 <= n <= 64  | SRSA Vd.2D.Vn.2D.#n    | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vrsra_n_u8(uint8x8_t a, uint8x8_t b, const int n)      | a -> Vd.8B<br>b -> Vn.8B<br>1 <= n <= 8   | URSA Vd.8B.Vn.8B.#n    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vrsraq_n_u8(uint8x16_t a, uint8x16_t b, const int n)  | a -> Vd.16B<br>b -> Vn.16B<br>1 <= n <= 8 | URSA Vd.16B.Vn.16B.#n  | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vrsra_n_u16(uint16x4_t a, uint16x4_t b, const int n)  | a -> Vd.4H<br>b -> Vn.4H<br>1 <= n <= 16  | URSA Vd.4H.Vn.4H.#n    | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vrsraq_n_u16(uint16x8_t a, uint16x8_t b, const int n) | a -> Vd.8H<br>b -> Vn.8H<br>1 <= n <= 16  | URSA Vd.8H.Vn.8H.#n    | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vrsra_n_u32(uint32x2_t a, uint32x2_t b, const int n)  | a -> Vd.2S<br>b -> Vn.2S<br>1 <= n <= 32  | URSA Vd.2S.Vn.2S.#n    | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vrsraq_n_u32(uint32x4_t a, uint32x4_t b, const int n) | a -> Vd.4S<br>b -> Vn.4S<br>1 <= n <= 32  | URSA Vd.4S.Vn.4S.#n    | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vrsra_n_u64(uint64x1_t a, uint64x1_t b, const int n)  | a -> Dd<br>b -> Dn<br>1 <= n <= 64        | URSA Dd.Dn.#n          | Dd -> result     | v7/A32/A64              |
| uint64x2_t vrsraq_n_u64(uint64x2_t a, uint64x2_t b, const int n) | a -> Vd.2D<br>b -> Vn.2D<br>1 <= n <= 64  | URSA Vd.2D.Vn.2D.#n    | Vd.2D -> result  | v7/A32/A64              |
| int64_t vrsrad_n_s64(int64_t a, int64_t b, const int n)          | a -> Dd<br>b -> Dn<br>1 <= n <= 64        | SRSA Dd.Dn.#n          | Dd -> result     | A64                     |
| uint64_t vrsrad_n_u64(uint64_t a, uint64_t b, const int n)       | a -> Dd<br>b -> Dn<br>1 <= n <= 64        | URSA Dd.Dn.#n          | Dd -> result     | A64                     |
| int8x8_t vqshl_n_s8(int8x8_t a, const int n)                     | a -> Vn.8B<br>0 <= n <= 7                 | SQSHL Vd.8B.Vn.8B.#n   | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vqshlq_n_s8(int8x16_t a, const int n)                  | a -> Vn.16B<br>0 <= n <= 7                | SQSHL Vd.16B.Vn.16B.#n | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vqshl_n_s16(int16x4_t a, const int n)                  | a -> Vn.4H<br>0 <= n <= 15                | SQSHL Vd.4H.Vn.4H.#n   | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vqshlq_n_s16(int16x8_t a, const int n)                 | a -> Vn.8H<br>0 <= n <= 15                | SQSHL Vd.8H.Vn.8H.#n   | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vqshlq_n_s32(int32x2_t a, const int n)                 | a -> Vn.2S<br>0 <= n <= 31                | SQSHL Vd.2S.Vn.2S.#n   | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vqshlq_n_s32(int32x4_t a, const int n)                 | a -> Vn.4S<br>0 <= n <= 31                | SQSHL Vd.4S.Vn.4S.#n   | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vqshlq_n_s64(int64x1_t a, const int n)                 | a -> Dn<br>0 <= n <= 63                   | SQSHL Dd.Dn.#n         | Dd -> result     | v7/A32/A64              |
| int64x2_t vqshlq_n_s64(int64x2_t a, const int n)                 | a -> Vn.2D<br>0 <= n <= 63                | SQSHL Vd.2D.Vn.2D.#n   | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vqshl_n_u8(uint8x8_t a, const int n)                   | a -> Vn.8B<br>0 <= n <= 7                 | UQSHL Vd.8B.Vn.8B.#n   | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vqshlq_n_u8(uint8x16_t a, const int n)                | a -> Vn.16B<br>0 <= n <= 7                | UQSHL Vd.16B.Vn.16B.#n | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vqshlq_n_u16(uint16x4_t a, const int n)               | a -> Vn.4H<br>0 <= n <= 15                | UQSHL Vd.4H.Vn.4H.#n   | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vqshlq_n_u16(uint16x8_t a, const int n)               | a -> Vn.8H<br>0 <= n <= 15                | UQSHL Vd.8H.Vn.8H.#n   | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vqshlq_n_u32(uint32x2_t a, const int n)               | a -> Vn.2S<br>0 <= n <= 31                | UQSHL Vd.2S.Vn.2S.#n   | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vqshlq_n_u32(uint32x4_t a, const int n)               | a -> Vn.4S<br>0 <= n <= 31                | UQSHL Vd.4S.Vn.4S.#n   | Vd.4S -> result  | v7/A32/A64              |

| Intrinsic                                                            | Argument Preparation                 | Instruction             | Result           | Supported Architectures |
|----------------------------------------------------------------------|--------------------------------------|-------------------------|------------------|-------------------------|
| uint64x1_t vqshl_n_u64(uint64x1_t a, const int n)                    | a->Dn<br>0 <= n <= 63                | UQSHL Dd,Dn,#n          | Dd -> result     | v7/A32/A64              |
| uint64x2_t vqshlq_n_u64(uint64x2_t a, const int n)                   | a->Vn,2D<br>0 <= n <= 63             | UQSHL Vd,2D,Vn,2D,#n    | Vd,2D -> result  | v7/A32/A64              |
| int8_t vqshlb_n_s8(int8_t a, const int n)                            | a->Bn<br>0 <= n <= 7                 | SQSHL Bd,Bn,#n          | Bd -> result     | A64                     |
| int16_t vqshlq_n_s16(int16_t a, const int n)                         | a->Hn<br>0 <= n <= 15                | SQSHL Hd,Hn,#n          | Hd -> result     | A64                     |
| int32_t vqshlq_n_s32(int32_t a, const int n)                         | a->Sn<br>0 <= n <= 31                | SQSHL Sd,Sn,#n          | Sd -> result     | A64                     |
| int64_t vqshld_n_s64(int64_t a, const int n)                         | a->Dn<br>0 <= n <= 63                | SQSHL Dd,Dn,#n          | Dd -> result     | A64                     |
| uint8_t vqshlb_n_u8(uint8_t a, const int n)                          | a->Bn<br>0 <= n <= 7                 | UQSHL Bd,Bn,#n          | Bd -> result     | A64                     |
| uint16_t vqshlq_n_u16(uint16_t a, const int n)                       | a->Hn<br>0 <= n <= 15                | UQSHL Hd,Hn,#n          | Hd -> result     | A64                     |
| uint32_t vqshlq_n_u32(uint32_t a, const int n)                       | a->Sn<br>0 <= n <= 31                | UQSHL Sd,Sn,#n          | Sd -> result     | A64                     |
| uint64_t vqshld_n_u64(uint64_t a, const int n)                       | a->Dn<br>0 <= n <= 63                | UQSHL Dd,Dn,#n          | Dd -> result     | A64                     |
| uint8x8_t vqshlu_n_s8(int8x8_t a, const int n)                       | a->Vn,8B<br>0 <= n <= 7              | SQSHLU Vd,8B,Vn,8B,#n   | Vd,8B -> result  | v7/A32/A64              |
| uint8x16_t vqshluq_n_s8(int8x16_t a, const int n)                    | a->Vn,16B<br>0 <= n <= 7             | SQSHLU Vd,16B,Vn,16B,#n | Vd,16B -> result | v7/A32/A64              |
| uint16x4_t vqshluq_n_s16(int16x4_t a, const int n)                   | a->Vn,4H<br>0 <= n <= 15             | SQSHLU Vd,4H,Vn,4H,#n   | Vd,4H -> result  | v7/A32/A64              |
| uint16x8_t vqshluq_n_s16(int16x8_t a, const int n)                   | a->Vn,8H<br>0 <= n <= 15             | SQSHLU Vd,8H,Vn,8H,#n   | Vd,8H -> result  | v7/A32/A64              |
| uint32x2_t vqshluq_n_s32(int32x2_t a, const int n)                   | a->Vn,2S<br>0 <= n <= 31             | SQSHLU Vd,2S,Vn,2S,#n   | Vd,2S -> result  | v7/A32/A64              |
| uint32x4_t vqshluq_n_s32(int32x4_t a, const int n)                   | a->Vn,4S<br>0 <= n <= 31             | SQSHLU Vd,4S,Vn,4S,#n   | Vd,4S -> result  | v7/A32/A64              |
| uint64x1_t vqshluq_n_s64(int64x1_t a, const int n)                   | a->Dn<br>0 <= n <= 63                | SQSHLU Vd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| uint64x2_t vqshluq_n_s64(int64x2_t a, const int n)                   | a->Vn,2D<br>0 <= n <= 63             | SQSHLU Vd,2D,Vn,2D,#n   | Vd,2D -> result  | v7/A32/A64              |
| uint8_t vqshlub_n_s8(int8_t a, const int n)                          | a->Bn<br>0 <= n <= 7                 | SQSHLU Bd,Bn,#n         | Bd -> result     | A64                     |
| uint16_t vqshlubq_n_s16(uint16_t a, const int n)                     | a->Hn<br>0 <= n <= 15                | SQSHLU Hd,Hn,#n         | Hd -> result     | A64                     |
| uint32_t vqshlubq_n_s32(int32_t a, const int n)                      | a->Sn<br>0 <= n <= 31                | SQSHLU Sd,Sn,#n         | Sd -> result     | A64                     |
| uint64_t vqshlubq_n_s64(int64_t a, const int n)                      | a->Dn<br>0 <= n <= 63                | SQSHLU Dd,Dn,#n         | Dd -> result     | A64                     |
| int8x8_t vshrn_n_s16(int8x8_t a, const int n)                        | a->Vn,8H<br>1 <= n <= 8              | SHRN Vd,8B,Vn,8H,#n     | Vd,8B -> result  | v7/A32/A64              |
| int16x4_t vshrnq_n_s32(int16x4_t a, const int n)                     | a->Vn,4S<br>1 <= n <= 16             | SHRN Vd,4H,Vn,4S,#n     | Vd,4H -> result  | v7/A32/A64              |
| int32x2_t vshrnq_n_s64(int32x2_t a, const int n)                     | a->Vn,2D<br>1 <= n <= 32             | SHRN Vd,2S,Vn,2D,#n     | Vd,2S -> result  | v7/A32/A64              |
| uint8x8_t vshrnq_n_u16(uint16x8_t a, const int n)                    | a->Vn,8H<br>1 <= n <= 8              | SHRN Vd,8B,Vn,8H,#n     | Vd,8B -> result  | v7/A32/A64              |
| uint16x4_t vshrnq_n_u32(uint32x4_t a, const int n)                   | a->Vn,4S<br>1 <= n <= 16             | SHRN Vd,4H,Vn,4S,#n     | Vd,4H -> result  | v7/A32/A64              |
| uint32x2_t vshrnq_n_u64(uint64x2_t a, const int n)                   | a->Vn,2D<br>1 <= n <= 32             | SHRN Vd,2S,Vn,2D,#n     | Vd,2S -> result  | v7/A32/A64              |
| int8x16_t vshrn_high_n_s16(int8x8_t r, int16x8_t a, const int n)     | r->Vd,8B<br>a->Vn,8H<br>1 <= n <= 8  | SHRN2 Vd,16B,Vn,8H,#n   | Vd,16B -> result | A64                     |
| int16x8_t vshrn_high_n_s32(int16x4_t r, int32x4_t a, const int n)    | r->Vd,4H<br>a->Vn,4S<br>1 <= n <= 16 | SHRN2 Vd,8H,Vn,4S,#n    | Vd,8H -> result  | A64                     |
| int32x4_t vshrn_high_n_s64(int32x2_t r, int64x2_t a, const int n)    | r->Vd,2S<br>a->Vn,2D<br>1 <= n <= 32 | SHRN2 Vd,4S,Vn,2D,#n    | Vd,4S -> result  | A64                     |
| uint8x16_t vshrn_high_n_u16(uint8x8_t r, uint16x8_t a, const int n)  | r->Vd,8B<br>a->Vn,8H<br>1 <= n <= 8  | SHRN2 Vd,16B,Vn,8H,#n   | Vd,16B -> result | A64                     |
| uint16x8_t vshrn_high_n_u32(uint16x4_t r, uint32x4_t a, const int n) | r->Vd,4H<br>a->Vn,4S<br>1 <= n <= 16 | SHRN2 Vd,8H,Vn,4S,#n    | Vd,8H -> result  | A64                     |

| Intrinsic                                                              | Argument Preparation                     | Instruction              | Result           | Supported Architectures |
|------------------------------------------------------------------------|------------------------------------------|--------------------------|------------------|-------------------------|
| uint32x4_t vshrn_high_n_u64(uint32x2_t r, uint64x2_t a, const int n)   | r -> Vd,2S<br>a -> Vn,2D<br>1 <= n <= 32 | SHRN2 Vd,4S,Vn,2D,#n     | Vd,4S -> result  | A64                     |
| uint8x8_t vqshrun_n_s16(int16x8_t a, const int n)                      | a -> Vn,8H<br>1 <= n <= 8                | SQSHRUN Vd,8B,Vn,8H,#n   | Vd,8B -> result  | V7/A32/A64              |
| uint16x4_t vqshrun_n_s32(int32x4_t a, const int n)                     | a -> Vn,4S<br>1 <= n <= 16               | SQSHRUN Vd,4H,Vn,4S,#n   | Vd,4H -> result  | V7/A32/A64              |
| uint32x2_t vqshrun_n_s64(int64x2_t a, const int n)                     | a -> Vn,2D<br>1 <= n <= 32               | SQSHRUN Vd,2S,Vn,2D,#n   | Vd,2S -> result  | V7/A32/A64              |
| uint8_t vqshrunh_n_s16(int16_t a, const int n)                         | a -> Hn<br>1 <= n <= 8                   | SQSHRUN Bd,Hn,#n         | Bd -> result     | A64                     |
| uint16_t vqshrun_n_s32(int32_t a, const int n)                         | a -> Sn<br>1 <= n <= 16                  | SQSHRUN Hd,Sn,#n         | Hd -> result     | A64                     |
| uint32_t vqshrun_n_s64(int64_t a, const int n)                         | a -> Dn<br>1 <= n <= 32                  | SQSHRUN Sd,Dn,#n         | Sd -> result     | A64                     |
| uint8x16_t vqshrun_high_n_s16(uint8x8_t r, int16x8_t a, const int n)   | r -> Vd,8B<br>a -> Vn,8H<br>1 <= n <= 8  | SQSHRUN2 Vd,16B,Vn,8H,#n | Vd,16B -> result | A64                     |
| uint16x4_t vqshrun_high_n_s32(uint16x4_t r, int32x2_t a, const int n)  | r -> Vd,4H<br>a -> Vn,4S<br>1 <= n <= 16 | SQSHRUN2 Vd,8H,Vn,4S,#n  | Vd,8H -> result  | A64                     |
| uint32x2_t vqshrun_high_n_s64(uint64x2_t r, int64x2_t a, const int n)  | r -> Vd,2S<br>a -> Vn,2D<br>1 <= n <= 32 | SQSHRUN2 Vd,4S,Vn,2D,#n  | Vd,4S -> result  | A64                     |
| uint8x8_t vqshrun_n_s16(int16x8_t a, const int n)                      | a -> Vn,8H<br>1 <= n <= 8                | QRSHRUN Vd,8B,Vn,8H,#n   | Vd,8B -> result  | V7/A32/A64              |
| uint16x4_t vqshrun_n_s32(int32x4_t a, const int n)                     | a -> Vn,4S<br>1 <= n <= 16               | QRSHRUN Vd,4H,Vn,4S,#n   | Vd,4H -> result  | V7/A32/A64              |
| uint32x2_t vqshrun_n_s64(int64x2_t a, const int n)                     | a -> Vn,2D<br>1 <= n <= 32               | QRSHRUN Vd,2S,Vn,2D,#n   | Vd,2S -> result  | V7/A32/A64              |
| uint8_t vqrshrunh_n_s16(int16_t a, const int n)                        | a -> Hn<br>1 <= n <= 8                   | QRSHRUN Bd,Hn,#n         | Bd -> result     | A64                     |
| uint16_t vqrshrun_n_s32(int32_t a, const int n)                        | a -> Sn<br>1 <= n <= 16                  | QRSHRUN Hd,Sn,#n         | Hd -> result     | A64                     |
| uint32_t vqrshrun_n_s64(int64_t a, const int n)                        | a -> Dn<br>1 <= n <= 32                  | QRSHRUN Sd,Dn,#n         | Sd -> result     | A64                     |
| uint8x16_t vqrshrun_high_n_s16(uint8x8_t r, int16x8_t a, const int n)  | r -> Vd,8B<br>a -> Vn,8H<br>1 <= n <= 8  | QRSHRUN2 Vd,16B,Vn,8H,#n | Vd,16B -> result | A64                     |
| uint16x4_t vqrshrun_high_n_s32(uint16x4_t r, int32x2_t a, const int n) | r -> Vd,4H<br>a -> Vn,4S<br>1 <= n <= 16 | QRSHRUN2 Vd,8H,Vn,4S,#n  | Vd,8H -> result  | A64                     |
| uint32x2_t vqrshrun_high_n_s64(uint64x2_t r, int64x2_t a, const int n) | r -> Vd,2S<br>a -> Vn,2D<br>1 <= n <= 32 | QRSHRUN2 Vd,4S,Vn,2D,#n  | Vd,4S -> result  | A64                     |
| int8x8_t vqshrn_n_s16(int16x8_t a, const int n)                        | a -> Vn,8H<br>1 <= n <= 8                | SQSHRN Vd,8B,Vn,8H,#n    | Vd,8B -> result  | V7/A32/A64              |
| int16x4_t vqshrn_n_s32(int32x4_t a, const int n)                       | a -> Vn,4S<br>1 <= n <= 16               | SQSHRN Vd,4H,Vn,4S,#n    | Vd,4H -> result  | V7/A32/A64              |
| int32x2_t vqshrn_n_s64(int64x2_t a, const int n)                       | a -> Vn,2D<br>1 <= n <= 32               | SQSHRN Vd,2S,Vn,2D,#n    | Vd,2S -> result  | V7/A32/A64              |
| uint8x8_t vqshrn_n_u16(uint16x8_t a, const int n)                      | a -> Vn,8H<br>1 <= n <= 8                | UQSHRN Vd,8B,Vn,8H,#n    | Vd,8B -> result  | V7/A32/A64              |
| uint16x4_t vqshrn_n_u32(uint32x4_t a, const int n)                     | a -> Vn,4S<br>1 <= n <= 16               | UQSHRN Vd,4H,Vn,4S,#n    | Vd,4H -> result  | V7/A32/A64              |
| uint32x2_t vqshrn_n_u64(uint64x2_t a, const int n)                     | a -> Vn,2D<br>1 <= n <= 32               | UQSHRN Vd,2S,Vn,2D,#n    | Vd,2S -> result  | V7/A32/A64              |
| int8_t vqshrnh_n_s16(int16_t a, const int n)                           | a -> Hn<br>1 <= n <= 8                   | SQSHRN Bd,Hn,#n          | Bd -> result     | A64                     |
| int16_t vqshrn_n_s32(int32_t a, const int n)                           | a -> Sn<br>1 <= n <= 16                  | SQSHRN Hd,Sn,#n          | Hd -> result     | A64                     |
| int32_t vqshrnd_n_s64(int64_t a, const int n)                          | a -> Dn<br>1 <= n <= 32                  | SQSHRN Sd,Dn,#n          | Sd -> result     | A64                     |
| uint8_t vqshrnh_n_u16(uint16_t a, const int n)                         | a -> Hn<br>1 <= n <= 8                   | UQSHRN Bd,Hn,#n          | Bd -> result     | A64                     |
| uint16_t vqshrn_n_u32(uint32_t a, const int n)                         | a -> Sn<br>1 <= n <= 16                  | UQSHRN Hd,Sn,#n          | Hd -> result     | A64                     |
| uint32_t vqshrnd_n_u64(uint64_t a, const int n)                        | a -> Dn<br>1 <= n <= 32                  | UQSHRN Sd,Dn,#n          | Sd -> result     | A64                     |
| int8x16_t vqshrn_high_n_s16(int8x8_t r, int16x8_t a, const int n)      | r -> Vd,8B<br>a -> Vn,8H<br>1 <= n <= 8  | SQSHRN2 Vd,16B,Vn,8H,#n  | Vd,16B -> result | A64                     |

| Intrinsic                                                             | Argument Preparation                     | Instruction              | Result           | Supported Architectures |
|-----------------------------------------------------------------------|------------------------------------------|--------------------------|------------------|-------------------------|
| int16x8_t vqshrn_high_n_s32(int16x4_t r, int32x4_t a, const int n)    | r -> Vd.4H<br>a -> Vn.4S<br>1 <= n <= 16 | SQSHRN2 Vd.8H.Vn.4S.#n   | Vd.8H -> result  | A64                     |
| int32x4_t vqshrn_high_n_s64(int32x2_t r, int64x2_t a, const int n)    | r -> Vd.2S<br>a -> Vn.2D<br>1 <= n <= 32 | SQSHRN2 Vd.4S.Vn.2D.#n   | Vd.4S -> result  | A64                     |
| uint8x16_t vqshrn_high_n_u16(uint8x8_t r, uint16x8_t a, const int n)  | r -> Vd.8B<br>a -> Vn.8H<br>1 <= n <= 8  | UQSHRN2 Vd.16B.Vn.8H.#n  | Vd.16B -> result | A64                     |
| uint16x8_t vqshrn_high_n_u32(uint16x4_t r, uint32x4_t a, const int n) | r -> Vd.4H<br>a -> Vn.4S<br>1 <= n <= 16 | UQSHRN2 Vd.8H.Vn.4S.#n   | Vd.8H -> result  | A64                     |
| uint32x4_t vqshrn_high_n_u64(uint32x2_t r, uint64x2_t a, const int n) | r -> Vd.2S<br>a -> Vn.2D<br>1 <= n <= 32 | UQSHRN2 Vd.4S.Vn.2D.#n   | Vd.4S -> result  | A64                     |
| int8x8_t vrshrn_n_s16(int16x8_t a, const int n)                       | a -> Vn.8H<br>1 <= n <= 8                | RSHRN Vd.8B.Vn.8H.#n     | Vd.8B -> result  | V7/A32/A64              |
| int16x4_t vrshrn_n_s32(int32x4_t a, const int n)                      | a -> Vn.4S<br>1 <= n <= 16               | RSHRN Vd.4H.Vn.4S.#n     | Vd.4H -> result  | V7/A32/A64              |
| int32x2_t vrshrn_n_s64(int64x2_t a, const int n)                      | a -> Vn.2D<br>1 <= n <= 32               | RSHRN Vd.2S.Vn.2D.#n     | Vd.2S -> result  | V7/A32/A64              |
| uint8x8_t vrshrn_n_u16(uint16x8_t a, const int n)                     | a -> Vn.8H<br>1 <= n <= 8                | RSHRN Vd.8B.Vn.8H.#n     | Vd.8B -> result  | V7/A32/A64              |
| uint16x4_t vrshrn_n_u32(uint32x4_t a, const int n)                    | a -> Vn.4S<br>1 <= n <= 16               | RSHRN Vd.4H.Vn.4S.#n     | Vd.4H -> result  | V7/A32/A64              |
| uint32x2_t vrshrn_n_u64(uint64x2_t a, const int n)                    | a -> Vn.2D<br>1 <= n <= 32               | RSHRN Vd.2S.Vn.2D.#n     | Vd.2S -> result  | V7/A32/A64              |
| int8x16_t vrshrn_high_n_s16(int8x8_t r, int16x8_t a, const int n)     | r -> Vd.8B<br>a -> Vn.8H<br>1 <= n <= 8  | RSHRN2 Vd.16B.Vn.8H.#n   | Vd.16B -> result | A64                     |
| int16x8_t vrshrn_high_n_s32(int16x4_t r, int32x4_t a, const int n)    | r -> Vd.4H<br>a -> Vn.4S<br>1 <= n <= 16 | RSHRN2 Vd.8H.Vn.4S.#n    | Vd.8H -> result  | A64                     |
| int32x4_t vrshrn_high_n_s64(int32x2_t r, int64x2_t a, const int n)    | r -> Vd.2S<br>a -> Vn.2D<br>1 <= n <= 32 | RSHRN2 Vd.4S.Vn.2D.#n    | Vd.4S -> result  | A64                     |
| uint8x16_t vrshrn_high_n_u16(uint8x8_t r, uint16x8_t a, const int n)  | r -> Vd.8B<br>a -> Vn.8H<br>1 <= n <= 8  | RSHRN2 Vd.16B.Vn.8H.#n   | Vd.16B -> result | A64                     |
| uint16x8_t vrshrn_high_n_u32(uint16x4_t r, uint32x4_t a, const int n) | r -> Vd.4H<br>a -> Vn.4S<br>1 <= n <= 16 | RSHRN2 Vd.8H.Vn.4S.#n    | Vd.8H -> result  | A64                     |
| uint32x4_t vrshrn_high_n_u64(uint32x2_t r, uint64x2_t a, const int n) | r -> Vd.2D<br>a -> Vn.2D<br>1 <= n <= 32 | RSHRN2 Vd.4S.Vn.2D.#n    | Vd.4S -> result  | A64                     |
| int8x8_t vqrshrn_n_s16(int16x8_t a, const int n)                      | a -> Vn.8H<br>1 <= n <= 8                | SQRSHRN Vd.8B.Vn.8H.#n   | Vd.8B -> result  | V7/A32/A64              |
| int16x4_t vqrshrn_n_s32(int32x4_t a, const int n)                     | a -> Vn.4S<br>1 <= n <= 16               | SQRSHRN Vd.4H.Vn.4S.#n   | Vd.4H -> result  | V7/A32/A64              |
| int32x2_t vqrshrn_n_s64(int64x2_t a, const int n)                     | a -> Vn.2D<br>1 <= n <= 32               | SQRSHRN Vd.2S.Vn.2D.#n   | Vd.2S -> result  | V7/A32/A64              |
| uint8x8_t vqrshrn_n_u16(uint16x8_t a, const int n)                    | a -> Vn.8H<br>1 <= n <= 8                | UQRSHRN Vd.8B.Vn.8H.#n   | Vd.8B -> result  | V7/A32/A64              |
| uint16x4_t vqrshrn_n_u32(uint32x4_t a, const int n)                   | a -> Vn.4S<br>1 <= n <= 16               | UQRSHRN Vd.4H.Vn.4S.#n   | Vd.4H -> result  | V7/A32/A64              |
| uint32x2_t vqrshrn_n_u64(uint64x2_t a, const int n)                   | a -> Vn.2D<br>1 <= n <= 32               | UQRSHRN Vd.2S.Vn.2D.#n   | Vd.2S -> result  | V7/A32/A64              |
| int8_t vqrshrn_h_n_s16(int16_t a, const int n)                        | a -> Hn<br>1 <= n <= 8                   | SQRSHRN Bd.Hn.#n         | Bd -> result     | A64                     |
| int16_t vqrshrn_n_s32(int32_t a, const int n)                         | a -> Sn<br>1 <= n <= 16                  | SQRSHRN Hd.Sn.#n         | Hd -> result     | A64                     |
| int32_t vqrshrn_n_s64(int64_t a, const int n)                         | a -> Dn<br>1 <= n <= 32                  | SQRSHRN Sd.Dn.#n         | Sd -> result     | A64                     |
| uint8_t vqrshrn_n_u16(uint16_t a, const int n)                        | a -> Hn<br>1 <= n <= 8                   | UQRSHRN Bd.Hn.#n         | Bd -> result     | A64                     |
| uint16_t vqrshrn_n_u32(uint32_t a, const int n)                       | a -> Sn<br>1 <= n <= 16                  | UQRSHRN Hd.Sn.#n         | Hd -> result     | A64                     |
| uint32_t vqrshrn_n_u64(uint64_t a, const int n)                       | a -> Dn<br>1 <= n <= 32                  | UQRSHRN Sd.Dn.#n         | Sd -> result     | A64                     |
| int8x16_t vqrshrn_high_n_s16(int8x8_t r, int16x8_t a, const int n)    | r -> Vd.8B<br>a -> Vn.8H<br>1 <= n <= 8  | SQRSHRN2 Vd.16B.Vn.8H.#n | Vd.16B -> result | A64                     |

| Intrinsic                                                              | Argument Preparation                      | Instruction              | Result           | Supported Architectures |
|------------------------------------------------------------------------|-------------------------------------------|--------------------------|------------------|-------------------------|
| int16x8_t vqrshrn_high_n_s32(int16x4_t r, int32x4_t a, const int n)    | r -> Vd.4H<br>a -> Vn.4S<br>1 <= n <= 16  | SQRSHRN2 Vd.8H.Vn.4S,#n  | Vd.8H -> result  | A64                     |
| int32x4_t vqrshrn_high_n_s64(int32x2_t r, int64x2_t a, const int n)    | r -> Vd.2S<br>a -> Vn.2D<br>1 <= n <= 32  | SQRSHRN2 Vd.4S.Vn.2D,#n  | Vd.4S -> result  | A64                     |
| uint8x16_t vqrshrn_high_n_u16(uint8x8_t r, uint16x8_t a, const int n)  | r -> Vd.8B<br>a -> Vn.8H<br>1 <= n <= 8   | UQRSHRN2 Vd.16B.Vn.8H,#n | Vd.16B -> result | A64                     |
| uint16x8_t vqrshrn_high_n_u32(uint16x4_t r, uint32x4_t a, const int n) | r -> Vd.4H<br>a -> Vn.4S<br>1 <= n <= 16  | UQRSHRN2 Vd.8H.Vn.4S,#n  | Vd.8H -> result  | A64                     |
| uint32x4_t vqrshrn_high_n_u64(uint32x2_t r, uint64x2_t a, const int n) | r -> Vd.2S<br>a -> Vn.2D<br>1 <= n <= 32  | UQRSHRN2 Vd.4S.Vn.2D,#n  | Vd.4S -> result  | A64                     |
| int16x8_t vshll_n_s8(int8x8_t a, const int n)                          | a -> Vn.8B<br>0 <= n <= 7                 | SSHLL Vd.8H.Vn.8B,#n     | Vd.8H -> result  | V7/A32/A64              |
| int32x4_t vshll_n_s16(int16x4_t a, const int n)                        | a -> Vn.4H<br>0 <= n <= 15                | SSHLL Vd.4S.Vn.4H,#n     | Vd.4S -> result  | V7/A32/A64              |
| int64x2_t vshll_n_s32(int32x2_t a, const int n)                        | a -> Vn.2S<br>0 <= n <= 31                | SSHLL Vd.2D.Vn.2S,#n     | Vd.2D -> result  | V7/A32/A64              |
| uint16x8_t vshll_n_u8(uint8x8_t a, const int n)                        | a -> Vn.8B<br>0 <= n <= 7                 | USHLL Vd.8H.Vn.8B,#n     | Vd.8H -> result  | V7/A32/A64              |
| uint32x4_t vshll_n_u16(uint16x4_t a, const int n)                      | a -> Vn.4H<br>0 <= n <= 15                | USHLL Vd.4S.Vn.4H,#n     | Vd.4S -> result  | V7/A32/A64              |
| uint64x2_t vshll_n_u32(uint32x2_t a, const int n)                      | a -> Vn.2S<br>0 <= n <= 31                | USHLL Vd.2D.Vn.2S,#n     | Vd.2D -> result  | V7/A32/A64              |
| int16x8_t vshll_high_n_s8(int8x16_t a, const int n)                    | a -> Vn.16B<br>0 <= n <= 7                | SSHLL2 Vd.8H.Vn.16B,#n   | Vd.8H -> result  | A64                     |
| int32x4_t vshll_high_n_s16(int16x8_t a, const int n)                   | a -> Vn.8H<br>0 <= n <= 15                | SSHLL2 Vd.4S.Vn.8H,#n    | Vd.4S -> result  | A64                     |
| int64x2_t vshll_high_n_s32(int32x4_t a, const int n)                   | a -> Vn.4S<br>0 <= n <= 31                | SSHLL2 Vd.2D.Vn.4S,#n    | Vd.2D -> result  | A64                     |
| uint16x8_t vshll_high_n_u8(uint8x16_t a, const int n)                  | a -> Vn.16B<br>0 <= n <= 7                | USHLL2 Vd.8H.Vn.16B,#n   | Vd.8H -> result  | A64                     |
| uint32x4_t vshll_high_n_u16(uint16x8_t a, const int n)                 | a -> Vn.8H<br>0 <= n <= 15                | USHLL2 Vd.4S.Vn.8H,#n    | Vd.4S -> result  | A64                     |
| uint64x2_t vshll_high_n_u32(uint32x4_t a, const int n)                 | a -> Vn.4S<br>0 <= n <= 31                | USHLL2 Vd.2D.Vn.4S,#n    | Vd.2D -> result  | A64                     |
| int16x8_t vshll_n_s8(int8x8_t a, const int n)                          | a -> Vn.8B<br>n == 8                      | SHLL Vd.8H.Vn.8B,#n      | Vd.8H -> result  | V7/A32/A64              |
| int32x4_t vshll_n_s16(int16x4_t a, const int n)                        | a -> Vn.4H<br>n == 16                     | SHLL Vd.4S.Vn.4H,#n      | Vd.4S -> result  | V7/A32/A64              |
| int64x2_t vshll_n_s32(int32x2_t a, const int n)                        | a -> Vn.2S<br>n == 32                     | SHLL Vd.2D.Vn.2S,#n      | Vd.2D -> result  | V7/A32/A64              |
| uint16x8_t vshll_n_u8(uint8x8_t a, const int n)                        | a -> Vn.8B<br>n == 8                      | SHLL Vd.8H.Vn.8B,#n      | Vd.8H -> result  | V7/A32/A64              |
| uint32x4_t vshll_n_u16(uint16x4_t a, const int n)                      | a -> Vn.4H<br>n == 16                     | SHLL Vd.4S.Vn.4H,#n      | Vd.4S -> result  | V7/A32/A64              |
| uint64x2_t vshll_n_u32(uint32x2_t a, const int n)                      | a -> Vn.2S<br>n == 32                     | SHLL Vd.2D.Vn.2S,#n      | Vd.2D -> result  | V7/A32/A64              |
| int16x8_t vshll_high_n_s8(int8x16_t a, const int n)                    | a -> Vn.16B<br>n == 8                     | SHLL2 Vd.8H.Vn.16B,#n    | Vd.8H -> result  | A64                     |
| int32x4_t vshll_high_n_s16(int16x8_t a, const int n)                   | a -> Vn.8H<br>n == 16                     | SHLL2 Vd.4S.Vn.8H,#n     | Vd.4S -> result  | A64                     |
| int64x2_t vshll_high_n_s32(int32x4_t a, const int n)                   | a -> Vn.4S<br>n == 32                     | SHLL2 Vd.2D.Vn.4S,#n     | Vd.2D -> result  | A64                     |
| uint16x8_t vshll_high_n_u8(uint8x16_t a, const int n)                  | a -> Vn.16B<br>n == 8                     | SHLL2 Vd.8H.Vn.16B,#n    | Vd.8H -> result  | A64                     |
| uint32x4_t vshll_high_n_u16(uint16x8_t a, const int n)                 | a -> Vn.8H<br>n == 16                     | SHLL2 Vd.4S.Vn.8H,#n     | Vd.4S -> result  | A64                     |
| uint64x2_t vshll_high_n_u32(uint32x4_t a, const int n)                 | a -> Vn.4S<br>n == 32                     | SHLL2 Vd.2D.Vn.4S,#n     | Vd.2D -> result  | A64                     |
| int8x8_t vsri_n_s8(int8x8_t a, int8x8_t b, const int n)                | a -> Vd.8B<br>b -> Vn.8B<br>1 <= n <= 8   | SRI Vd.8B.Vn.8B,#n       | Vd.8B -> result  | V7/A32/A64              |
| int8x16_t vsriq_n_s8(int8x16_t a, int8x16_t b, const int n)            | a -> Vd.16B<br>b -> Vn.16B<br>1 <= n <= 8 | SRI Vd.16B.Vn.16B,#n     | Vd.16B -> result | V7/A32/A64              |
| int16x4_t vsri_n_s16(int16x4_t a, int16x4_t b, const int n)            | a -> Vd.4H<br>b -> Vn.4H<br>1 <= n <= 16  | SRI Vd.4H.Vn.4H,#n       | Vd.4H -> result  | V7/A32/A64              |

| Intrinsic                                                       | Argument Preparation              | Instruction          | Result           | Supported Architectures |
|-----------------------------------------------------------------|-----------------------------------|----------------------|------------------|-------------------------|
| int16x8_t vsriq_n_s16(int16x8_t a, int16x8_t b, const int n)    | a->Vd.8H<br>b->Vn.8H<br>1<=n<=16  | SRI Vd.8H,Vn.8H,#n   | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vsri_n_s32(int32x2_t a, int32x2_t b, const int n)     | a->Vd.2S<br>b->Vn.2S<br>1<=n<=32  | SRI Vd.2S,Vn.2S,#n   | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vsriq_n_s32(int32x4_t a, int32x4_t b, const int n)    | a->Vd.4S<br>b->Vn.4S<br>1<=n<=32  | SRI Vd.4S,Vn.4S,#n   | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vsri_n_s64(int64x1_t a, int64x1_t b, const int n)     | a->Dd<br>b->Dn<br>1<=n<=64        | SRI Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| int64x2_t vsriq_n_s64(int64x2_t a, int64x2_t b, const int n)    | a->Vd.2D<br>b->Vn.2D<br>1<=n<=64  | SRI Vd.2D,Vn.2D,#n   | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vsri_n_u8(uint8x8_t a, uint8x8_t b, const int n)      | a->Vd.8B<br>b->Vn.8B<br>1<=n<=8   | SRI Vd.8B,Vn.8B,#n   | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vsriq_n_u8(uint8x16_t a, uint8x16_t b, const int n)  | a->Vd.16B<br>b->Vn.16B<br>1<=n<=8 | SRI Vd.16B,Vn.16B,#n | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vsri_n_u16(uint16x4_t a, uint16x4_t b, const int n)  | a->Vd.4H<br>b->Vn.4H<br>1<=n<=16  | SRI Vd.4H,Vn.4H,#n   | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vsriq_n_u16(uint16x8_t a, uint16x8_t b, const int n) | a->Vd.8H<br>b->Vn.8H<br>1<=n<=16  | SRI Vd.8H,Vn.8H,#n   | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vsri_n_u32(uint32x2_t a, uint32x2_t b, const int n)  | a->Vd.2S<br>b->Vn.2S<br>1<=n<=32  | SRI Vd.2S,Vn.2S,#n   | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vsriq_n_u32(uint32x4_t a, uint32x4_t b, const int n) | a->Vd.4S<br>b->Vn.4S<br>1<=n<=32  | SRI Vd.4S,Vn.4S,#n   | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vsri_n_u64(uint64x1_t a, uint64x1_t b, const int n)  | a->Dd<br>b->Dn<br>1<=n<=64        | SRI Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| uint64x2_t vsriq_n_u64(uint64x2_t a, uint64x2_t b, const int n) | a->Vd.2D<br>b->Vn.2D<br>1<=n<=64  | SRI Vd.2D,Vn.2D,#n   | Vd.2D -> result  | v7/A32/A64              |
| poly64x1_t vsri_n_p64(poly64x1_t a, poly64x1_t b, const int n)  | a->Dd<br>b->Dn<br>1<=n<=64        | SRI Dd,Dn,#n         | Dd -> result     | A32/A64                 |
| poly64x2_t vsriq_n_p64(poly64x2_t a, poly64x2_t b, const int n) | a->Vd.2D<br>b->Vn.2D<br>1<=n<=64  | SRI Vd.2D,Vn.2D,#n   | Vd.2D -> result  | A32/A64                 |
| poly8x8_t vsri_n_p8(poly8x8_t a, poly8x8_t b, const int n)      | a->Vd.8B<br>b->Vn.8B<br>1<=n<=8   | SRI Vd.8B,Vn.8B,#n   | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vsriq_n_p8(poly8x16_t a, poly8x16_t b, const int n)  | a->Vd.16B<br>b->Vn.16B<br>1<=n<=8 | SRI Vd.16B,Vn.16B,#n | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vsri_n_p16(poly16x4_t a, poly16x4_t b, const int n)  | a->Vd.4H<br>b->Vn.4H<br>1<=n<=16  | SRI Vd.4H,Vn.4H,#n   | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vsriq_n_p16(poly16x8_t a, poly16x8_t b, const int n) | a->Vd.8H<br>b->Vn.8H<br>1<=n<=16  | SRI Vd.8H,Vn.8H,#n   | Vd.8H -> result  | v7/A32/A64              |
| int64_t vsrid_n_s64(int64_t a, int64_t b, const int n)          | a->Dd<br>b->Dn<br>1<=n<=64        | SRI Dd,Dn,#n         | Dd -> result     | A64                     |
| uint64_t vsrid_n_u64(uint64_t a, uint64_t b, const int n)       | a->Dd<br>b->Dn<br>1<=n<=64        | SRI Dd,Dn,#n         | Dd -> result     | A64                     |
| int8x8_t vsl1_n_s8(int8x8_t a, int8x8_t b, const int n)         | a->Vd.8B<br>b->Vn.8B<br>0<=n<=7   | SLI Vd.8B,Vn.8B,#n   | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vslq1_n_s8(int8x16_t a, int8x16_t b, const int n)     | a->Vd.16B<br>b->Vn.16B<br>0<=n<=7 | SLI Vd.16B,Vn.16B,#n | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vsl1_n_s16(int16x4_t a, int16x4_t b, const int n)     | a->Vd.4H<br>b->Vn.4H<br>0<=n<=15  | SLI Vd.4H,Vn.4H,#n   | Vd.4H -> result  | v7/A32/A64              |

| Intrinsic                                                       | Argument Preparation                      | Instruction          | Result           | Supported Architectures |
|-----------------------------------------------------------------|-------------------------------------------|----------------------|------------------|-------------------------|
| int16x8_t vslqi_n_s16(int16x8_t a, int16x8_t b, const int n)    | a -> Vd.8H<br>b -> Vn.8H<br>0 <= n <= 15  | SLI Vd.8H,Vn.8H,#n   | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vslj_n_s32(int32x2_t a, int32x2_t b, const int n)     | a -> Vd.2S<br>b -> Vn.2S<br>0 <= n <= 31  | SLI Vd.2S,Vn.2S,#n   | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vslqj_n_s32(int32x4_t a, int32x4_t b, const int n)    | a -> Vd.4S<br>b -> Vn.4S<br>0 <= n <= 31  | SLI Vd.4S,Vn.4S,#n   | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vslj_n_s64(int64x1_t a, int64x1_t b, const int n)     | a -> Dd<br>b -> Dn<br>0 <= n <= 63        | SLI Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| int64x2_t vslqj_n_s64(int64x2_t a, int64x2_t b, const int n)    | a -> Vd.2D<br>b -> Vn.2D<br>0 <= n <= 63  | SLI Vd.2D,Vn.2D,#n   | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vslj_n_u8(uint8x8_t a, uint8x8_t b, const int n)      | a -> Vd.8B<br>b -> Vn.8B<br>0 <= n <= 7   | SLI Vd.8B,Vn.8B,#n   | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vslqj_n_u8(uint8x16_t a, uint8x16_t b, const int n)  | a -> Vd.16B<br>b -> Vn.16B<br>0 <= n <= 7 | SLI Vd.16B,Vn.16B,#n | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vslj_n_u16(uint16x4_t a, uint16x4_t b, const int n)  | a -> Vd.4H<br>b -> Vn.4H<br>0 <= n <= 15  | SLI Vd.4H,Vn.4H,#n   | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vslqj_n_u16(uint16x8_t a, uint16x8_t b, const int n) | a -> Vd.8H<br>b -> Vn.8H<br>0 <= n <= 15  | SLI Vd.8H,Vn.8H,#n   | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vslj_n_u32(uint32x2_t a, uint32x2_t b, const int n)  | a -> Vd.2S<br>b -> Vn.2S<br>0 <= n <= 31  | SLI Vd.2S,Vn.2S,#n   | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vslqj_n_u32(uint32x4_t a, uint32x4_t b, const int n) | a -> Vd.4S<br>b -> Vn.4S<br>0 <= n <= 31  | SLI Vd.4S,Vn.4S,#n   | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vslj_n_u64(uint64x1_t a, uint64x1_t b, const int n)  | a -> Dd<br>b -> Dn<br>0 <= n <= 63        | SLI Dd,Dn,#n         | Dd -> result     | v7/A32/A64              |
| uint64x2_t vslqj_n_u64(uint64x2_t a, uint64x2_t b, const int n) | a -> Vd.2D<br>b -> Vn.2D<br>0 <= n <= 63  | SLI Vd.2D,Vn.2D,#n   | Vd.2D -> result  | v7/A32/A64              |
| poly64x1_t vslj_n_p64(poly64x1_t a, poly64x1_t b, const int n)  | a -> Dd<br>b -> Dn<br>0 <= n <= 63        | SLI Dd,Dn,#n         | Dd -> result     | A32/A64                 |
| poly64x2_t vslqj_n_p64(poly64x2_t a, poly64x2_t b, const int n) | a -> Vd.2D<br>b -> Vn.2D<br>0 <= n <= 63  | SLI Vd.2D,Vn.2D,#n   | Vd.2D -> result  | A32/A64                 |
| poly8x8_t vslj_n_p8(poly8x8_t a, poly8x8_t b, const int n)      | a -> Vd.8B<br>b -> Vn.8B<br>0 <= n <= 7   | SLI Vd.8B,Vn.8B,#n   | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vslqj_n_p8(poly8x16_t a, poly8x16_t b, const int n)  | a -> Vd.16B<br>b -> Vn.16B<br>0 <= n <= 7 | SLI Vd.16B,Vn.16B,#n | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vslj_n_p16(poly16x4_t a, poly16x4_t b, const int n)  | a -> Vd.4H<br>b -> Vn.4H<br>0 <= n <= 15  | SLI Vd.4H,Vn.4H,#n   | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vslqj_n_p16(poly16x8_t a, poly16x8_t b, const int n) | a -> Vd.8H<br>b -> Vn.8H<br>0 <= n <= 15  | SLI Vd.8H,Vn.8H,#n   | Vd.8H -> result  | v7/A32/A64              |
| int64_t vslid_n_s64(int64_t a, int64_t b, const int n)          | a -> Dd<br>b -> Dn<br>0 <= n <= 63        | SLI Dd,Dn,#n         | Dd -> result     | A64                     |
| uint64_t vslid_n_u64(uint64_t a, uint64_t b, const int n)       | a -> Dd<br>b -> Dn<br>0 <= n <= 63        | SLI Dd,Dn,#n         | Dd -> result     | A64                     |
| int32x2_t fcvtf_s32(f32(float32x2_t a))                         | a -> Vn.2S                                | FCVTZS Vd.2S,Vn.2S   | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t fcvtfq_s32(f32(float32x4_t a))                        | a -> Vn.4S                                | FCVTZS Vd.4S,Vn.4S   | Vd.4S -> result  | v7/A32/A64              |
| uint32x2_t fcvtf_u32(f32(float32x2_t a))                        | a -> Vn.2S                                | FCVTZU Vd.2S,Vn.2S   | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t fcvtfq_u32(f32(float32x4_t a))                       | a -> Vn.4S                                | FCVTZU Vd.4S,Vn.4S   | Vd.4S -> result  | v7/A32/A64              |
| int32x2_t fcvtn_s32(f32(float32x2_t a))                         | a -> Vn.2S                                | FCVTNS Vd.2S,Vn.2S   | Vd.2S -> result  | A32/A64                 |
| int32x4_t fcvtnq_s32(f32(float32x4_t a))                        | a -> Vn.4S                                | FCVTNS Vd.4S,Vn.4S   | Vd.4S -> result  | A32/A64                 |
| uint32x2_t fcvtn_u32(f32(float32x2_t a))                        | a -> Vn.2S                                | FCVTNU Vd.2S,Vn.2S   | Vd.2S -> result  | A32/A64                 |
| uint32x4_t fcvtnq_u32(f32(float32x4_t a))                       | a -> Vn.4S                                | FCVTNU Vd.4S,Vn.4S   | Vd.4S -> result  | A32/A64                 |
| int32x2_t fcvtnq_s32(f32(float32x2_t a))                        | a -> Vn.2S                                | FCVTMS Vd.2S,Vn.2S   | Vd.2S -> result  | A32/A64                 |
| int32x4_t fcvtnmq_s32(f32(float32x4_t a))                       | a -> Vn.4S                                | FCVTMS Vd.4S,Vn.4S   | Vd.4S -> result  | A32/A64                 |

| Intrinsic                                               | Argument Preparation     | Instruction           | Result        | Supported Architectures |
|---------------------------------------------------------|--------------------------|-----------------------|---------------|-------------------------|
| uint32x2_t vcvtm_u32_f32(float32x2_t a)                 | a->Vn,2S                 | FCVTMU Vd,2S,Vn,2S    | Vd,2S->result | A32/A64                 |
| uint32x4_t vcvtmq_u32_f32(float32x4_t a)                | a->Vn,4S                 | FCVTMU Vd,4S,Vn,4S    | Vd,4S->result | A32/A64                 |
| int32x2_t vcvtp_s32_f32(float32x2_t a)                  | a->Vn,2S                 | FCVTPS Vd,2S,Vn,2S    | Vd,2S->result | A32/A64                 |
| int32x4_t vcvtpq_s32_f32(float32x4_t a)                 | a->Vn,4S                 | FCVTPS Vd,4S,Vn,4S    | Vd,4S->result | A32/A64                 |
| uint32x2_t vcvtp_u32_f32(float32x2_t a)                 | a->Vn,2S                 | FCVTPU Vd,2S,Vn,2S    | Vd,2S->result | A32/A64                 |
| uint32x4_t vcvtpq_u32_f32(float32x4_t a)                | a->Vn,4S                 | FCVTPU Vd,4S,Vn,4S    | Vd,4S->result | A32/A64                 |
| int32x2_t vcvta_s32_f32(float32x2_t a)                  | a->Vn,2S                 | FCVTAS Vd,2S,Vn,2S    | Vd,2S->result | A32/A64                 |
| int32x4_t vcvtaq_s32_f32(float32x4_t a)                 | a->Vn,4S                 | FCVTAS Vd,4S,Vn,4S    | Vd,4S->result | A32/A64                 |
| uint32x2_t vcvta_u32_f32(float32x2_t a)                 | a->Vn,2S                 | FCVTAU Vd,2S,Vn,2S    | Vd,2S->result | A32/A64                 |
| uint32x4_t vcvtaq_u32_f32(float32x4_t a)                | a->Vn,4S                 | FCVTAU Vd,4S,Vn,4S    | Vd,4S->result | A32/A64                 |
| int32_t vcvts_s32_f32(float32_t a)                      | a->Sn                    | FCVTZS Sd,Sn          | Sd->result    | A64                     |
| uint32_t vcvts_u32_f32(float32_t a)                     | a->Sn                    | FCVTZU Sd,Sn          | Sd->result    | A64                     |
| int32_t vcvtns_s32_f32(float32_t a)                     | a->Sn                    | FCVTNS Sd,Sn          | Sd->result    | A64                     |
| uint32_t vcvtns_u32_f32(float32_t a)                    | a->Sn                    | FCVTNU Sd,Sn          | Sd->result    | A64                     |
| int32_t vcvtns_s32_f32(float32_t a)                     | a->Sn                    | FCVTMS Sd,Sn          | Sd->result    | A64                     |
| uint32_t vcvtns_u32_f32(float32_t a)                    | a->Sn                    | FCVTMU Sd,Sn          | Sd->result    | A64                     |
| int32_t vcvtp_s32_f32(float32_t a)                      | a->Sn                    | FCVTPS Sd,Sn          | Sd->result    | A64                     |
| uint32_t vcvtp_u32_f32(float32_t a)                     | a->Sn                    | FCVTPU Sd,Sn          | Sd->result    | A64                     |
| int32_t vcvtns_s32_f32(float32_t a)                     | a->Sn                    | FCVTZS Sd,Sn          | Sd->result    | A64                     |
| uint32_t vcvtns_u32_f32(float32_t a)                    | a->Sn                    | FCVTZU Sd,Sn          | Sd->result    | A64                     |
| int64x1_t vcvta_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTAU Dd,Dn          | Dd->result    | A64                     |
| int64x2_t vcvtaq_s64_f64(float64x2_t a)                 | a->Vn,2D                 | FCVTZS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| uint64x1_t vcvta_u64_f64(float64x1_t a)                 | a->Dn                    | FCVTZU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtaq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTZU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtn_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTNS Dd,Dn          | Dd->result    | A64                     |
| int64x2_t vcvtnq_s64_f64(float64x2_t a)                 | a->Vn,2D                 | FCVTNS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| uint64x1_t vcvtn_u64_f64(float64x1_t a)                 | a->Dn                    | FCVTNU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtnq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTNU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtp_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTPS Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtpq_s64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTPS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtp_u64_f64(float64x1_t a)                  | a->Dn                    | FCVTPU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtpq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTPU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvta_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTAS Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtaq_s64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTAS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvta_u64_f64(float64x1_t a)                  | a->Dn                    | FCVTAU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtaq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTAU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtd_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTZS Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtdq_s64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTZS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtd_u64_f64(float64x1_t a)                  | a->Dn                    | FCVTZU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtdq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTZU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtn_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTNS Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtnq_s64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTNS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtn_u64_f64(float64x1_t a)                  | a->Dn                    | FCVTNU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtnq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTNU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtp_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTPS Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtpq_s64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTPS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvtp_u64_f64(float64x1_t a)                  | a->Dn                    | FCVTPU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtpq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTPU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvta_s64_f64(float64x1_t a)                  | a->Dn                    | FCVTAS Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtaq_s64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTAS Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int64x1_t vcvta_u64_f64(float64x1_t a)                  | a->Dn                    | FCVTAU Dd,Dn          | Dd->result    | A64                     |
| uint64x2_t vcvtaq_u64_f64(float64x2_t a)                | a->Vn,2D                 | FCVTAU Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| int32x2_t vcvta_n_s32_f32(float32x2_t a, const int n)   | a->Vn,2S<br>1 <= n <= 32 | FCVTZS Vd,2S,Vn,2S,#n | Vd,2S->result | v7/A32/A64              |
| int32x4_t vcvtaq_n_s32_f32(float32x4_t a, const int n)  | a->Vn,4S<br>1 <= n <= 32 | FCVTZS Vd,4S,Vn,4S,#n | Vd,4S->result | v7/A32/A64              |
| uint32x2_t vcvta_n_u32_f32(float32x2_t a, const int n)  | a->Vn,2S<br>1 <= n <= 32 | FCVTZU Vd,2S,Vn,2S,#n | Vd,2S->result | v7/A32/A64              |
| uint32x4_t vcvtaq_n_u32_f32(float32x4_t a, const int n) | a->Vn,4S<br>1 <= n <= 32 | FCVTZU Vd,4S,Vn,4S,#n | Vd,4S->result | v7/A32/A64              |
| int32_t vcvtns_n_s32_f32(float32_t a, const int n)      | a->Sn<br>1 <= n <= 32    | FCVTZS Sd,Sn,#n       | Sd->result    | A64                     |
| uint32_t vcvtns_n_u32_f32(float32_t a, const int n)     | a->Sn<br>1 <= n <= 32    | FCVTZU Sd,Sn,#n       | Sd->result    | A64                     |
| int64x1_t vcvta_n_s64_f64(float64x1_t a, const int n)   | a->Dn<br>1 <= n <= 64    | FCVTZS Dd,Dn,#n       | Dd->result    | A64                     |
| int64x2_t vcvtaq_n_s64_f64(float64x2_t a, const int n)  | a->Vn,2D<br>1 <= n <= 64 | FCVTZS Vd,2D,Vn,2D,#n | Vd,2D->result | A64                     |
| uint64x1_t vcvta_n_u64_f64(float64x1_t a, const int n)  | a->Dn<br>1 <= n <= 64    | FCVTZU Dd,Dn,#n       | Dd->result    | A64                     |
| uint64x2_t vcvtaq_n_u64_f64(float64x2_t a, const int n) | a->Vn,2D<br>1 <= n <= 64 | FCVTZU Vd,2D,Vn,2D,#n | Vd,2D->result | A64                     |

| Intrinsic                                               | Argument Preparation | Instruction          | Result        | Supported Architectures |
|---------------------------------------------------------|----------------------|----------------------|---------------|-------------------------|
| int64_t vcvtd_n_s64_f64(float64_t a, const int n)       | a->Dn<br>1<n<=64     | FCVIZS Dd,Dn,#n      | Dd->result    | A64                     |
| uint64_t vcvtd_n_u64_f64(float64_t a, const int n)      | a->Dn<br>1<n<=64     | FCVIZU Dd,Dn,#n      | Dd->result    | A64                     |
| float32x2_t vcvtf_f32_s32(int32x2_t a)                  | a->Vn,2S             | SCVTF Vd,2S,Vn,2S    | Vd,2S->result | V7/A32/A64              |
| float32x2_t vcvtf_f32_s32(int32x2_t a)                  | a->Vn,4S             | SCVTF Vd,4S,Vn,4S    | Vd,4S->result | V7/A32/A64              |
| float32x2_t vcvtf_f32_s32(int32x2_t a)                  | a->Vn,2S             | SCVTF Vd,2S,Vn,2S    | Vd,2S->result | V7/A32/A64              |
| float32x2_t vcvtf_f32_u32(uint32x2_t a)                 | a->Vn,4S             | UCVTF Vd,4S,Vn,4S    | Vd,4S->result | V7/A32/A64              |
| float32_t vcvts_f32_s32(int32_t a)                      | a->Sn                | SCVTF Sd,Sn          | Sd->result    | A64                     |
| float64x1_t vcvtf_f64_s32(uint32x1_t a)                 | a->Sn                | UCVTF Sd,Sn          | Sd->result    | A64                     |
| float64x2_t vcvtf_f64_s32(uint32x2_t a)                 | a->Vn,2D             | SCVTF Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| float64x1_t vcvtf_f64_u32(uint32x1_t a)                 | a->Dn                | UCVTF Dd,Dn          | Dd->result    | A64                     |
| float64x2_t vcvtf_f64_u32(uint32x2_t a)                 | a->Vn,2D             | UCVTF Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| float64x2_t vcvtf_f64_u64(uint64x2_t a)                 | a->Vn,2D             | UCVTF Vd,2D,Vn,2D    | Vd,2D->result | A64                     |
| float64x1_t vcvtf_f64_u64(uint64x1_t a)                 | a->Dn                | UCVTF Dd,Dn          | Dd->result    | A64                     |
| float64x2_t vcvtf_f64_u64(uint64x2_t a, const int n)    | a->Vn,2S<br>1<n<=32  | SCVTF Vd,2S,Vn,2S,#n | Vd,2S->result | V7/A32/A64              |
| float32x2_t vcvtf_n_f32_s32(int32x2_t a, const int n)   | a->Vn,4S<br>1<n<=32  | SCVTF Vd,4S,Vn,4S,#n | Vd,4S->result | V7/A32/A64              |
| float32x2_t vcvtf_n_f32_u32(uint32x2_t a, const int n)  | a->Vn,2S<br>1<n<=32  | UCVTF Vd,2S,Vn,2S,#n | Vd,2S->result | V7/A32/A64              |
| float32x2_t vcvtf_n_f32_u32(uint32x2_t a, const int n)  | a->Vn,4S<br>1<n<=32  | UCVTF Vd,4S,Vn,4S,#n | Vd,4S->result | V7/A32/A64              |
| float32_t vcvts_n_f32_s32(int32_t a, const int n)       | a->Sn<br>1<n<=32     | SCVTF Sd,Sn,#n       | Sd->result    | A64                     |
| float32x2_t vcvts_n_f32_u32(uint32x2_t a, const int n)  | a->Sn<br>1<n<=32     | UCVTF Sd,Sn,#n       | Sd->result    | A64                     |
| float64x1_t vcvtf_n_f64_s64(int64x1_t a, const int n)   | a->Dn<br>1<n<=64     | SCVTF Dd,Dn,#n       | Dd->result    | A64                     |
| float64x2_t vcvtf_n_f64_s64(int64x2_t a, const int n)   | a->Vn,2D<br>1<n<=64  | SCVTF Vd,2D,Vn,2D,#n | Vd,2D->result | A64                     |
| float64x1_t vcvtf_n_f64_u64(uint64x1_t a, const int n)  | a->Dn<br>1<n<=64     | UCVTF Dd,Dn,#n       | Dd->result    | A64                     |
| float64x2_t vcvtf_n_f64_u64(uint64x2_t a, const int n)  | a->Vn,2D<br>1<n<=64  | UCVTF Vd,2D,Vn,2D,#n | Vd,2D->result | A64                     |
| float64x1_t vcvtd_n_f64_s64(int64x1_t a, const int n)   | a->Dn<br>1<n<=64     | SCVTF Dd,Dn,#n       | Dd->result    | A64                     |
| float64x2_t vcvtd_n_f64_u64(uint64x2_t a, const int n)  | a->Vn,2D<br>1<n<=64  | UCVTF Vd,2D,Vn,2D,#n | Vd,2D->result | A64                     |
| float64x1_t vcvtd_n_f64_u64(uint64x1_t a, const int n)  | a->Dn<br>1<n<=64     | UCVTF Dd,Dn,#n       | Dd->result    | A64                     |
| float64x2_t vcvtd_f64_f32(float32x2_t a)                | a->Vn,4S             | FCVTN Vd,4H,Vn,4S    | Vd,4H->result | V7/A32/A64              |
| float16x8_t vcvtf_f16_f32(float32x1_t r, float32x1_t a) | r->Vd,4H<br>a->Vn,4S | FCVTN2 Vd,8H,Vn,4S   | Vd,8H->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | V7/A32/A64              |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->Vn,2D             | FCVTN Vd,2S,Vn,2D    | Vd,2S->result | A64                     |
| float32x4_t vcvtf_f32_f64(float64x2_t r, float64x2_t a) | r->Vd,2S<br>a->Vn,2D | FCVTN2 Vd,4S,Vn,2D   | Vd,4S->result | A64                     |
| float32x2_t vcvtf_f32_f64(float64x2_t a)                | a->                  |                      |               |                         |

| Intrinsic                                            | Argument Preparation | Instruction            | Result         | Supported Architectures |
|------------------------------------------------------|----------------------|------------------------|----------------|-------------------------|
| float32x4_t vrdmaq_f32(float32x4_t a)                | a->Vn,4S             | FRINTA Vd,4S,Vn,4S     | Vd,4S->result  | A32/A64                 |
| float64x1_t vrdma_f64(float64x1_t a)                 | a->Dn                | FRINTA Dd,Dn           | Dd->result     | A64                     |
| float64x2_t vrdmaq_f64(float64x2_t a)                | a->Vn,2D             | FRINTA Vd,2D,Vn,2D     | Vd,2D->result  | A64                     |
| float32x2_t vrdmi_f32(float32x2_t a)                 | a->Vn,2S             | FRINTI Vd,2S,Vn,2S     | Vd,2S->result  | A32/A64                 |
| float32x4_t vrdmiq_f32(float32x4_t a)                | a->Vn,4S             | FRINTI Vd,4S,Vn,4S     | Vd,4S->result  | A32/A64                 |
| float64x1_t vrdmi_f64(float64x1_t a)                 | a->Dn                | FRINTI Dd,Dn           | Dd->result     | A64                     |
| float64x2_t vrdmiq_f64(float64x2_t a)                | a->Vn,2D             | FRINTI Vd,2D,Vn,2D     | Vd,2D->result  | A64                     |
| float32x2_t vrdmx_f32(float32x2_t a)                 | a->Vn,2S             | FRINTX Vd,2S,Vn,2S     | Vd,2S->result  | A32/A64                 |
| float32x4_t vrdmxq_f32(float32x4_t a)                | a->Vn,4S             | FRINTX Vd,4S,Vn,4S     | Vd,4S->result  | A32/A64                 |
| float64x1_t vrdmx_f64(float64x1_t a)                 | a->Dn                | FRINTX Dd,Dn           | Dd->result     | A64                     |
| float64x2_t vrdmxq_f64(float64x2_t a)                | a->Vn,2D             | FRINTX Vd,2D,Vn,2D     | Vd,2D->result  | A64                     |
| int8x8_t vmovn_s16(int16x8_t a)                      | a->Vn,8H             | XTN Vd,8H,Vn,8H        | Vd,8H->result  | v7/A32/A64              |
| int16x4_t vmovn_s32(int32x4_t a)                     | a->Vn,4S             | XTN Vd,4H,Vn,4S        | Vd,4H->result  | v7/A32/A64              |
| uint32x2_t vmovn_u64(int64x2_t a)                    | a->Vn,2D             | XTN Vd,2S,Vn,2D        | Vd,2S->result  | v7/A32/A64              |
| uint8x8_t vmovn_u16(uint16x8_t a)                    | a->Vn,8H             | XTN Vd,8H,Vn,8H        | Vd,8H->result  | v7/A32/A64              |
| uint16x4_t vmovn_u32(uint32x4_t a)                   | a->Vn,4S             | XTN Vd,4H,Vn,4S        | Vd,4H->result  | v7/A32/A64              |
| uint32x2_t vmovn_u64(uint64x2_t a)                   | a->Vn,2D             | XTN Vd,2S,Vn,2D        | Vd,2S->result  | v7/A32/A64              |
| int8x16_t vmovn_high_s16(int8x8_t, int16x8_t a)      | r->Vd,8B<br>a->Vn,8H | XTN2 Vd,16B,Vn,8H      | Vd,16B->result | v7/A32/A64              |
| int16x8_t vmovn_high_s32(int16x4_t, int32x4_t a)     | r->Vd,4H<br>a->Vn,4S | XTN2 Vd,8H,Vn,4S       | Vd,8H->result  | v7/A32/A64              |
| int32x4_t vmovn_high_s64(int32x2_t, int64x2_t a)     | r->Vd,2S<br>a->Vn,2D | XTN2 Vd,4S,Vn,2D       | Vd,4S->result  | v7/A32/A64              |
| uint8x16_t vmovn_high_u16(uint8x8_t, uint16x8_t a)   | r->Vd,8B<br>a->Vn,8H | XTN2 Vd,16B,Vn,8H      | Vd,16B->result | v7/A32/A64              |
| uint16x8_t vmovn_high_u32(uint16x4_t, uint32x4_t a)  | r->Vd,4H<br>a->Vn,4S | XTN2 Vd,8H,Vn,4S       | Vd,8H->result  | v7/A32/A64              |
| uint32x4_t vmovn_high_u64(uint32x2_t, uint64x2_t a)  | r->Vd,2S<br>a->Vn,2D | XTN2 Vd,4S,Vn,2D       | Vd,4S->result  | v7/A32/A64              |
| int16x8_t vmovl_s8(int8x8_t a)                       | a->Vn,8B             | SSHLL Vd,8H,Vn,8B,#0   | Vd,8H->result  | v7/A32/A64              |
| int32x4_t vmovl_s16(int16x4_t a)                     | a->Vn,4H             | SSHLL Vd,4S,Vn,4H,#0   | Vd,4S->result  | v7/A32/A64              |
| int64x2_t vmovl_s32(int32x2_t a)                     | a->Vn,2S             | SSHLL Vd,2D,Vn,2S,#0   | Vd,2D->result  | v7/A32/A64              |
| uint16x8_t vmovl_u8(uint8x8_t a)                     | a->Vn,8B             | USHLL Vd,8H,Vn,8B,#0   | Vd,8H->result  | v7/A32/A64              |
| uint32x4_t vmovl_u16(uint16x4_t a)                   | a->Vn,4H             | USHLL Vd,4S,Vn,4H,#0   | Vd,4S->result  | v7/A32/A64              |
| uint64x2_t vmovl_u32(uint32x2_t a)                   | a->Vn,2S             | USHLL Vd,2D,Vn,2S,#0   | Vd,2D->result  | v7/A32/A64              |
| int16x8_t vmovl_high_s8(int8x8_t a)                  | a->Vn,16B            | SSHLL2 Vd,8H,Vn,16B,#0 | Vd,8H->result  | A64                     |
| int32x4_t vmovl_high_s16(int16x4_t a)                | a->Vn,8H             | SSHLL2 Vd,4S,Vn,8H,#0  | Vd,4S->result  | A64                     |
| int64x2_t vmovl_high_s32(int32x4_t a)                | a->Vn,4S             | SSHLL2 Vd,2D,Vn,4S,#0  | Vd,2D->result  | A64                     |
| uint16x8_t vmovl_high_u8(uint8x16_t a)               | a->Vn,16B            | USHLL2 Vd,8H,Vn,16B,#0 | Vd,8H->result  | A64                     |
| uint32x4_t vmovl_high_u16(uint16x8_t a)              | a->Vn,8H             | USHLL2 Vd,4S,Vn,8H,#0  | Vd,4S->result  | A64                     |
| uint64x2_t vmovl_high_u32(uint32x4_t a)              | a->Vn,4S             | USHLL2 Vd,2D,Vn,4S,#0  | Vd,2D->result  | A64                     |
| int8x8_t vqmovn_s16(int16x8_t a)                     | a->Vn,8H             | SQXTN Vd,8B,Vn,8H      | Vd,8B->result  | v7/A32/A64              |
| int16x4_t vqmovn_s32(int32x4_t a)                    | a->Vn,4S             | SQXTN Vd,4H,Vn,4S      | Vd,4H->result  | v7/A32/A64              |
| int32x2_t vqmovn_s64(int64x2_t a)                    | a->Vn,2D             | SQXTN Vd,2S,Vn,2D      | Vd,2S->result  | v7/A32/A64              |
| uint8x8_t vqmovn_u16(uint16x8_t a)                   | a->Vn,8H             | UQXTN Vd,8B,Vn,8H      | Vd,8B->result  | v7/A32/A64              |
| uint16x4_t vqmovn_u32(uint32x4_t a)                  | a->Vn,4S             | UQXTN Vd,4H,Vn,4S      | Vd,4H->result  | v7/A32/A64              |
| uint32x2_t vqmovn_u64(uint64x2_t a)                  | a->Vn,2D             | UQXTN Vd,2S,Vn,2D      | Vd,2S->result  | v7/A32/A64              |
| int8_t vqmovnh_s16(int16_t a)                        | a->Hn                | SQXTN Bd,Hn            | Bd->result     | A64                     |
| int16_t vqmovns_s32(int32_t a)                       | a->Sn                | SQXTN Hd,Sn            | Hd->result     | A64                     |
| int32_t vqmovnd_s64(int64_t a)                       | a->Dn                | SQXTN Sd,Dn            | Sd->result     | A64                     |
| uint8_t vqmovnh_u16(uint16_t a)                      | a->Hn                | UQXTN Bd,Hn            | Bd->result     | A64                     |
| uint16_t vqmovns_u32(uint32_t a)                     | a->Sn                | UQXTN Hd,Sn            | Hd->result     | A64                     |
| uint32_t vqmovnd_u64(uint64_t a)                     | a->Dn                | UQXTN Sd,Dn            | Sd->result     | A64                     |
| int8x16_t vqmovn_high_s16(int8x8_t, int16x8_t a)     | r->Vd,8B<br>a->Vn,8H | SQXTN2 Vd,16B,Vn,8H    | Vd,16B->result | A64                     |
| int16x8_t vqmovn_high_s32(int16x4_t, int32x4_t a)    | r->Vd,4H<br>a->Vn,4S | SQXTN2 Vd,8H,Vn,4S     | Vd,8H->result  | A64                     |
| int32x4_t vqmovn_high_s64(int32x2_t, int64x2_t a)    | r->Vd,2S<br>a->Vn,2D | SQXTN2 Vd,4S,Vn,2D     | Vd,4S->result  | A64                     |
| uint8x16_t vqmovn_high_u16(uint8x8_t, uint16x8_t a)  | r->Vd,8B<br>a->Vn,8H | UQXTN2 Vd,16B,Vn,8H    | Vd,16B->result | A64                     |
| uint16x8_t vqmovn_high_u32(uint16x4_t, uint32x4_t a) | r->Vd,4H<br>a->Vn,4S | UQXTN2 Vd,8H,Vn,4S     | Vd,8H->result  | A64                     |
| uint32x4_t vqmovn_high_u64(uint32x2_t, uint64x2_t a) | r->Vd,2S<br>a->Vn,2D | UQXTN2 Vd,4S,Vn,2D     | Vd,4S->result  | A64                     |
| uint8x8_t vqmovun_s16(int16x8_t a)                   | a->Vn,8H             | SQXTUN Vd,8B,Vn,8H     | Vd,8B->result  | v7/A32/A64              |
| uint16x4_t vqmovun_s32(int32x4_t a)                  | a->Vn,4S             | SQXTUN Vd,4H,Vn,4S     | Vd,4H->result  | v7/A32/A64              |
| uint32x2_t vqmovun_s64(int64x2_t a)                  | a->Vn,2D             | SQXTUN Vd,2S,Vn,2D     | Vd,2S->result  | v7/A32/A64              |
| uint8_t vqmovunh_s16(int16_t a)                      | a->Hn                | SQXTUN Bd,Hn           | Bd->result     | A64                     |
| uint16_t vqmovunns_s32(int32_t a)                    | a->Sn                | SQXTUN Hd,Sn           | Hd->result     | A64                     |
| uint32_t vqmovunnd_s64(int64_t a)                    | a->Dn                | SQXTUN Sd,Dn           | Sd->result     | A64                     |

| Intrinsic                                                                               | Argument Preparation                                     | Instruction                                           | Result           | Supported Architectures |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|------------------|-------------------------|
| uint8x16_t vqmovun_high_s16(uint8x8_t r, int16x8_t a)                                   | r -> Vd.8H<br>a -> Vn.8H                                 | SQXTUN2 Vd.16B,Vn.8H                                  | Vd.16B -> result | A64                     |
| uint16x8_t vqmovun_high_s32(uint16x4_t r, int32x4_t a)                                  | r -> Vd.4H<br>a -> Vn.4S                                 | SQXTUN2 Vd.8H,Vn.4S                                   | Vd.8H -> result  | A64                     |
| uint32x4_t vqmovun_high_s64(uint32x2_t r, int64x2_t a)                                  | r -> Vd.2S<br>a -> Vn.2D                                 | SQXTUN2 Vd.4S,Vn.2D                                   | Vd.4S -> result  | A64                     |
| int16x4_t vmla_lane_s16(int16x4_t a, int16x4_t b, int16x4_t v, const int lane)          | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLA Vd.4H,Vn.4H,Vm.H[lane]                            | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vmlaq_lane_s16(int16x8_t a, int16x8_t b, int16x4_t v, const int lane)         | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLA Vd.8H,Vn.8H,Vm.H[lane]                            | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vmla_lane_s32(int32x2_t a, int32x2_t b, int32x2_t v, const int lane)          | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLA Vd.2S,Vn.2S,Vm.\$[lane]                           | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vmlaq_lane_s32(int32x4_t a, int32x4_t b, int32x2_t v, const int lane)         | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLA Vd.4S,Vn.4S,Vm.\$[lane]                           | Vd.4S -> result  | v7/A32/A64              |
| uint16x4_t vmla_lane_u16(uint16x4_t a, uint16x4_t b, uint16x4_t v, const int lane)      | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLA Vd.4H,Vn.4H,Vm.H[lane]                            | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vmlaq_lane_u16(uint16x8_t a, uint16x8_t b, uint16x4_t v, const int lane)     | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLA Vd.8H,Vn.8H,Vm.H[lane]                            | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vmla_lane_u32(uint32x2_t a, uint32x2_t b, uint32x2_t v, const int lane)      | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLA Vd.2S,Vn.2S,Vm.\$[lane]                           | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vmlaq_lane_u32(uint32x4_t a, uint32x4_t b, uint32x2_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLA Vd.4S,Vn.4S,Vm.\$[lane]                           | Vd.4S -> result  | v7/A32/A64              |
| float32x2_t vmla_lane_f32(float32x2_t a, float32x2_t b, float32x2_t v, const int lane)  | 0 <= lane <= 1                                           | RESULT[i] = a[i] + (b[i] * v[lane])<br>for i = 0 to 1 | N/A -> result    | v7/A32/A64              |
| float32x4_t vmiaq_lane_f32(float32x4_t a, float32x4_t b, float32x2_t v, const int lane) | 0 <= lane <= 1                                           | RESULT[i] = a[i] + (b[i] * v[lane])<br>for i = 0 to 3 | N/A -> result    | v7/A32/A64              |
| int16x4_t vmia_laneq_s16(int16x4_t a, int16x4_t b, int16x8_t v, const int lane)         | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLA Vd.4H,Vn.4H,Vm.H[lane]                            | Vd.4H -> result  | A64                     |
| int16x8_t vmiaq_laneq_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane)        | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLA Vd.8H,Vn.8H,Vm.H[lane]                            | Vd.8H -> result  | A64                     |
| int32x2_t vmia_laneq_s32(int32x2_t a, int32x2_t b, int32x4_t v, const int lane)         | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLA Vd.2S,Vn.2S,Vm.\$[lane]                           | Vd.2S -> result  | A64                     |
| int32x4_t vmiaq_laneq_s32(int32x4_t a, int32x4_t b, int32x4_t v, const int lane)        | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLA Vd.4S,Vn.4S,Vm.\$[lane]                           | Vd.4S -> result  | A64                     |

| Intrinsic                                                                                | Argument Preparation                                     | Instruction                                           | Result          | Supported Architectures |
|------------------------------------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|-----------------|-------------------------|
| uint16x4_t vmla_lane_u16(uint16x4_t a, uint16x4_t b, uint16x8_t v, const int lane)       | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLA Vd.4H,Vn.4H,Vm.H[lane]                            | Vd.4H -> result | A64                     |
| uint16x8_t vmlaq_lane_u16(uint16x8_t a, uint16x8_t b, uint16x8_t v, const int lane)      | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLA Vd.8H,Vn.8H,Vm.H[lane]                            | Vd.8H -> result | A64                     |
| uint32x2_t vmla_lane_u32(uint32x2_t a, uint32x2_t b, uint32x4_t v, const int lane)       | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLA Vd.2S,Vn.2S,Vm.S[lane]                            | Vd.2S -> result | A64                     |
| uint32x4_t vmlaq_lane_u32(uint32x4_t a, uint32x4_t b, uint32x4_t v, const int lane)      | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLA Vd.4S,Vn.4S,Vm.S[lane]                            | Vd.4S -> result | A64                     |
| float32x2_t vmla_lane_f32(float32x2_t a, float32x2_t b, float32x4_t v, const int lane)   | 0 <= lane <= 3                                           | RESULT[i] = a[i] + (b[i] * v[lane])<br>for i = 0 to 1 | N/A -> result   | A64                     |
| float32x4_t vmlaq_lane_f32(float32x4_t a, float32x4_t b, float32x4_t v, const int lane)  | 0 <= lane <= 3                                           | RESULT[i] = a[i] + (b[i] * v[lane])<br>for i = 0 to 3 | N/A -> result   | A64                     |
| int32x4_t vmlal_lane_s16(int32x4_t a, int16x4_t b, int16x4_t v, const int lane)          | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SMLAL Vd.4S,Vn.4H,Vm.H[lane]                          | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vmlal_lane_s32(int64x2_t a, int32x2_t b, int32x2_t v, const int lane)          | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SMLAL Vd.2D,Vn.2S,Vm.S[lane]                          | Vd.2D -> result | v7/A32/A64              |
| uint32x4_t vmlal_lane_u16(uint32x4_t a, uint16x4_t b, uint16x4_t v, const int lane)      | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | UMLAL Vd.4S,Vn.4H,Vm.H[lane]                          | Vd.4S -> result | v7/A32/A64              |
| uint64x2_t vmlal_lane_u32(uint64x2_t a, uint32x2_t b, uint32x2_t v, const int lane)      | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | UMLAL Vd.2D,Vn.2S,Vm.S[lane]                          | Vd.2D -> result | v7/A32/A64              |
| int32x4_t vmlal_high_lane_s16(int32x4_t a, int16x8_t b, int16x4_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SMLAL2 Vd.4S,Vn.8H,Vm.H[lane]                         | Vd.4S -> result | A64                     |
| int64x2_t vmlal_high_lane_s32(int64x2_t a, int32x4_t b, int32x2_t v, const int lane)     | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SMLAL2 Vd.2D,Vn.4S,Vm.S[lane]                         | Vd.2D -> result | A64                     |
| uint32x4_t vmlal_high_lane_u16(uint32x4_t a, uint16x8_t b, uint16x4_t v, const int lane) | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | UMLAL2 Vd.4S,Vn.8H,Vm.H[lane]                         | Vd.4S -> result | A64                     |
| uint64x2_t vmlal_high_lane_u32(uint64x2_t a, uint32x4_t b, uint32x2_t v, const int lane) | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | UMLAL2 Vd.2D,Vn.4S,Vm.S[lane]                         | Vd.2D -> result | A64                     |
| int32x4_t vmlal_laneq_s16(int32x4_t a, int16x4_t b, int16x8_t v, const int lane)         | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SMLAL Vd.4S,Vn.4H,Vm.H[lane]                          | Vd.4S -> result | A64                     |
| int64x2_t vmlal_laneq_s32(int64x2_t a, int32x2_t b, int32x4_t v, const int lane)         | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SMLAL Vd.2D,Vn.2S,Vm.S[lane]                          | Vd.2D -> result | A64                     |

| Intrinsic                                                                                 | Argument Preparation                                     | Instruction                     | Result          | Supported Architectures |
|-------------------------------------------------------------------------------------------|----------------------------------------------------------|---------------------------------|-----------------|-------------------------|
| uint32x4_t vmlal_laneq_u16(uint32x4_t a, uint16x4_t b, uint16x8_t v, const int lane)      | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | UMLAL Vd.4S,Vn.4H,Vm.H[lane]    | Vd.4S -> result | A64                     |
| uint64x2_t vmlal_laneq_u32(uint64x2_t a, uint32x2_t b, uint32x4_t v, const int lane)      | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | UMLAL Vd.2D,Vn.2S,Vm.S[lane]    | Vd.2D -> result | A64                     |
| int32x4_t vmlal_high_laneq_s16(int32x4_t a, int16x8_t b, int16x8_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SMLAL2 Vd.4S,Vn.8H,Vm.H[lane]   | Vd.4S -> result | A64                     |
| int64x2_t vmlal_high_laneq_s32(int64x2_t a, int32x4_t b, int32x4_t v, const int lane)     | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SMLAL2 Vd.2D,Vn.4S,Vm.S[lane]   | Vd.2D -> result | A64                     |
| uint32x4_t vmlal_high_laneq_u16(uint32x4_t a, uint16x8_t b, uint16x8_t v, const int lane) | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | UMLAL2 Vd.4S,Vn.8H,Vm.H[lane]   | Vd.4S -> result | A64                     |
| uint64x2_t vmlal_high_laneq_u32(uint64x2_t a, uint32x4_t b, uint32x4_t v, const int lane) | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | UMLAL2 Vd.2D,Vn.4S,Vm.S[lane]   | Vd.2D -> result | A64                     |
| int32x4_t vqdmal_lane_s16(int32x4_t a, int16x4_t b, int16x4_t v, const int lane)          | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMLAL Vd.4S,Vn.4H,Vm.H[lane]  | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmal_lane_s32(int64x2_t a, int32x2_t b, int32x2_t v, const int lane)          | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMLAL Vd.2D,Vn.2S,Vm.S[lane]  | Vd.2D -> result | v7/A32/A64              |
| int32_t vqdmalh_lane_s16(int32_t a, int16_t b, int16x4_t v, const int lane)               | a -> Sd<br>b -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3       | SQDMLAL Sd,Hn,Vm.H[lane]        | Sd -> result    | A64                     |
| int64_t vqdmalh_lane_s32(int64_t a, int32_t b, int32x2_t v, const int lane)               | a -> Dd<br>b -> Sn<br>v -> Vm.2S<br>0 <= lane <= 1       | SQDMLAL Dd,Sn,Vm.S[lane]        | Dd -> result    | A64                     |
| int32x4_t vqdmal_high_lane_s16(int32x4_t a, int16x8_t b, int16x4_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMLAL2 Vd.4S,Vn.8H,Vm.H[lane] | Vd.4S -> result | A64                     |
| int64x2_t vqdmal_high_lane_s32(int64x2_t a, int32x4_t b, int32x2_t v, const int lane)     | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMLAL2 Vd.2D,Vn.4S,Vm.S[lane] | Vd.2D -> result | A64                     |
| int32x4_t vqdmal_laneq_s16(int32x4_t a, int16x4_t b, int16x8_t v, const int lane)         | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMLAL Vd.4S,Vn.4H,Vm.H[lane]  | Vd.4S -> result | A64                     |
| int64x2_t vqdmal_laneq_s32(int64x2_t a, int32x2_t b, int32x4_t v, const int lane)         | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMLAL Vd.2D,Vn.2S,Vm.S[lane]  | Vd.2D -> result | A64                     |

| Intrinsic                                                                                | Argument Preparation                                     | Instruction                                        | Result          | Supported Architectures |
|------------------------------------------------------------------------------------------|----------------------------------------------------------|----------------------------------------------------|-----------------|-------------------------|
| int32_t vqdmllah_lane_s16(int32_t a, int16_t b, int16x8_t v, const int lane)             | a -> Sd<br>b -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7       | SQDMLAL Sd,Hn,Vm.H[lane]                           | Sd -> result    | A64                     |
| int64_t vqdmllas_lane_s32(int64_t a, int32_t b, int32x4_t v, const int lane)             | a -> Dd<br>b -> Sn<br>v -> Vm.4S<br>0 <= lane <= 3       | SQDMLAL Dd,Sn,Vm.S[lane]                           | Dd -> result    | A64                     |
| int32x4_t vqdmllah_high_lane_s16(int32x4_t a, int16x8_t b, int16x8_t v, const int lane)  | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMLAL2 Vd.4S,Vn.8H,Vm.H[lane]                    | Vd.4S -> result | A64                     |
| int64x2_t vqdmllah_high_lane_s32(int64x2_t a, int32x4_t b, int32x4_t v, const int lane)  | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMLAL2 Vd.2D,Vn.4S,Vm.S[lane]                    | Vd.2D -> result | A64                     |
| int16x4_t vmlls_lane_s16(int16x4_t a, int16x4_t b, int16x4_t v, const int lane)          | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLS Vd.4H,Vn.4H,Vm.H[lane]                         | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vmllsq_lane_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane)         | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLS Vd.8H,Vn.8H,Vm.H[lane]                         | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vmlls_lane_s32(int32x2_t a, int32x2_t b, int32x2_t v, const int lane)          | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLS Vd.2S,Vn.2S,Vm.S[lane]                         | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vmllsq_lane_s32(int32x4_t a, int32x4_t b, int32x4_t v, const int lane)         | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLS Vd.4S,Vn.4S,Vm.S[lane]                         | Vd.4S -> result | v7/A32/A64              |
| uint16x4_t vmlls_lane_u16(uint16x4_t a, uint16x4_t b, uint16x4_t v, const int lane)      | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLS Vd.4H,Vn.4H,Vm.H[lane]                         | Vd.4H -> result | v7/A32/A64              |
| uint16x8_t vmllsq_lane_u16(uint16x8_t a, uint16x8_t b, uint16x8_t v, const int lane)     | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | MLS Vd.8H,Vn.8H,Vm.H[lane]                         | Vd.8H -> result | v7/A32/A64              |
| uint32x2_t vmlls_lane_u32(uint32x2_t a, uint32x2_t b, uint32x2_t v, const int lane)      | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLS Vd.2S,Vn.2S,Vm.S[lane]                         | Vd.2S -> result | v7/A32/A64              |
| uint32x4_t vmllsq_lane_u32(uint32x4_t a, uint32x4_t b, uint32x4_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | MLS Vd.4S,Vn.4S,Vm.S[lane]                         | Vd.4S -> result | v7/A32/A64              |
| float32x2_t vmlls_lane_f32(float32x2_t a, float32x2_t b, float32x2_t v, const int lane)  | 0 <= lane <= 1                                           | RESULT[i] = a[i] - (b[i] * v[lane]) for i = 0 to 1 | N/A -> result   | v7/A32/A64              |
| float32x4_t vmllsq_lane_f32(float32x4_t a, float32x4_t b, float32x2_t v, const int lane) | 0 <= lane <= 1                                           | RESULT[i] = a[i] - (b[i] * v[lane]) for i = 0 to 3 | N/A -> result   | v7/A32/A64              |
| int16x4_t vmlls_laneq_s16(int16x4_t a, int16x4_t b, int16x8_t v, const int lane)         | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLS Vd.4H,Vn.4H,Vm.H[lane]                         | Vd.4H -> result | A64                     |
| int16x8_t vmllsq_laneq_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane)        | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLS Vd.8H,Vn.8H,Vm.H[lane]                         | Vd.8H -> result | A64                     |

| Intrinsic                                                                                | Argument Preparation                                     | Instruction                                        | Result          | Supported Architectures |
|------------------------------------------------------------------------------------------|----------------------------------------------------------|----------------------------------------------------|-----------------|-------------------------|
| int32x2_t vm1s_laneq_s32(int32x2_t a, int32x2_t b, int32x4_t v, const int lane)          | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLS Vd.2S,Vn.2S,Vm.S[lane]                         | Vd.2S -> result | A64                     |
| int32x4_t vm1sq_laneq_s32(int32x4_t a, int32x4_t b, int32x4_t v, const int lane)         | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLS Vd.4S,Vn.4S,Vm.S[lane]                         | Vd.4S -> result | A64                     |
| uint16x4_t vm1s_laneq_u16(uint16x4_t a, uint16x4_t b, uint16x8_t v, const int lane)      | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLS Vd.4H,Vn.4H,Vm.H[lane]                         | Vd.4H -> result | A64                     |
| uint16x8_t vm1sq_laneq_u16(uint16x8_t a, uint16x8_t b, uint16x8_t v, const int lane)     | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | MLS Vd.8H,Vn.8H,Vm.H[lane]                         | Vd.8H -> result | A64                     |
| uint32x2_t vm1s_laneq_u32(uint32x2_t a, uint32x2_t b, uint32x4_t v, const int lane)      | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLS Vd.2S,Vn.2S,Vm.S[lane]                         | Vd.2S -> result | A64                     |
| uint32x4_t vm1sq_laneq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | MLS Vd.4S,Vn.4S,Vm.S[lane]                         | Vd.4S -> result | A64                     |
| float32x2_t vm1s_laneq_f32(float32x2_t a, float32x2_t b, float32x4_t v, const int lane)  | 0 <= lane <= 3                                           | RESULT[i] = a[i] - (b[i] * v[lane]) for i = 0 to 1 | N/A -> result   | A64                     |
| float32x4_t vm1sq_laneq_f32(float32x4_t a, float32x4_t b, float32x4_t v, const int lane) | 0 <= lane <= 3                                           | RESULT[i] = a[i] - (b[i] * v[lane]) for i = 0 to 3 | N/A -> result   | A64                     |
| int32x4_t vm1sl_lane_s16(int32x4_t a, int16x4_t b, int16x4_t v, const int lane)          | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SMLSL Vd.4S,Vn.4H,Vm.H[lane]                       | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vm1sl_lane_s32(int64x2_t a, int32x2_t b, int32x2_t v, const int lane)          | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SMLSL Vd.2D,Vn.2S,Vm.S[lane]                       | Vd.2D -> result | v7/A32/A64              |
| uint32x4_t vm1sl_lane_u16(uint32x4_t a, uint16x4_t b, uint16x4_t v, const int lane)      | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | UMLSL Vd.4S,Vn.4H,Vm.H[lane]                       | Vd.4S -> result | v7/A32/A64              |
| uint64x2_t vm1sl_lane_u32(uint64x2_t a, uint32x2_t b, uint32x2_t v, const int lane)      | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | UMLSL Vd.2D,Vn.2S,Vm.S[lane]                       | Vd.2D -> result | v7/A32/A64              |
| int32x4_t vm1sl_high_lane_s16(int32x4_t a, int16x8_t b, int16x4_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SMLSL2 Vd.4S,Vn.8H,Vm.H[lane]                      | Vd.4S -> result | A64                     |
| int64x2_t vm1sl_high_lane_s32(int64x2_t a, int32x2_t b, int32x2_t v, const int lane)     | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SMLSL2 Vd.2D,Vn.4S,Vm.S[lane]                      | Vd.2D -> result | A64                     |
| uint32x4_t vm1sl_high_lane_u16(uint32x4_t a, uint16x8_t b, uint16x4_t v, const int lane) | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | UMLSL2 Vd.4S,Vn.8H,Vm.H[lane]                      | Vd.4S -> result | A64                     |
| uint64x2_t vm1sl_high_lane_u32(uint64x2_t a, uint32x2_t b, uint32x2_t v, const int lane) | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | UMLSL2 Vd.2D,Vn.4S,Vm.S[lane]                      | Vd.2D -> result | A64                     |

| Intrinsic                                                                                 | Argument Preparation                                     | Instruction                     | Result          | Supported Architectures |
|-------------------------------------------------------------------------------------------|----------------------------------------------------------|---------------------------------|-----------------|-------------------------|
| int32x4_t vmisl_laneq_s16(int32x4_t a, int16x4_t b, int16x8_t v, const int lane)          | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SMLSL Vd.4S,Vn.4H,Vm.H[lane]    | Vd.4S -> result | A64                     |
| int64x2_t vmisl_laneq_s32(int64x2_t a, int32x2_t b, int32x4_t v, const int lane)          | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SMLSL Vd.2D,Vn.2S,Vm.S[lane]    | Vd.2D -> result | A64                     |
| uint32x4_t vmisl_laneq_u16(uint32x4_t a, uint16x4_t b, uint16x8_t v, const int lane)      | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | UMLSL Vd.4S,Vn.4H,Vm.H[lane]    | Vd.4S -> result | A64                     |
| uint64x2_t vmisl_laneq_u32(uint64x2_t a, uint32x2_t b, uint32x4_t v, const int lane)      | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | UMLSL Vd.2D,Vn.2S,Vm.S[lane]    | Vd.2D -> result | A64                     |
| int32x4_t vmisl_high_laneq_s16(int32x4_t a, int16x8_t b, int16x8_t v, const int lane)     | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SMLSL2 Vd.4S,Vn.8H,Vm.H[lane]   | Vd.4S -> result | A64                     |
| int64x2_t vmisl_high_laneq_s32(int64x2_t a, int32x4_t b, int32x4_t v, const int lane)     | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SMLSL2 Vd.2D,Vn.4S,Vm.S[lane]   | Vd.2D -> result | A64                     |
| uint32x4_t vmisl_high_laneq_u16(uint32x4_t a, uint16x8_t b, uint16x8_t v, const int lane) | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | UMLSL2 Vd.4S,Vn.8H,Vm.H[lane]   | Vd.4S -> result | A64                     |
| uint64x2_t vmisl_high_laneq_u32(uint64x2_t a, uint32x4_t b, uint32x4_t v, const int lane) | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | UMLSL2 Vd.2D,Vn.4S,Vm.S[lane]   | Vd.2D -> result | A64                     |
| int32x4_t vqdmisl_lane_s16(int32x4_t a, int16x4_t b, int16x4_t v, const int lane)         | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMLSL Vd.4S,Vn.4H,Vm.H[lane]  | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmisl_lane_s32(int64x2_t a, int32x2_t b, int32x2_t v, const int lane)         | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMLSL Vd.2D,Vn.2S,Vm.S[lane]  | Vd.2D -> result | v7/A32/A64              |
| int32_t vqdmislh_lane_s16(int32_t a, int16_t b, int16x4_t v, const int lane)              | a -> Sd<br>b -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3       | SQDMLSL Sd,Hn,Vm.H[lane]        | Sd -> result    | A64                     |
| int64_t vqdmislh_lane_s32(int64_t a, int32_t b, int32x2_t v, const int lane)              | a -> Dd<br>b -> Sn<br>v -> Vm.2S<br>0 <= lane <= 1       | SQDMLSL Dd,Sn,Vm.S[lane]        | Dd -> result    | A64                     |
| int32x4_t vqdmisl_high_lane_s16(int32x4_t a, int16x8_t b, int16x4_t v, const int lane)    | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMLSL2 Vd.4S,Vn.8H,Vm.H[lane] | Vd.4S -> result | A64                     |
| int64x2_t vqdmisl_high_lane_s32(int64x2_t a, int32x4_t b, int32x2_t v, const int lane)    | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMLSL2 Vd.2D,Vn.4S,Vm.S[lane] | Vd.2D -> result | A64                     |

| Intrinsic                                                                               | Argument Preparation                                     | Instruction                        | Result          | Supported Architectures |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------|------------------------------------|-----------------|-------------------------|
| int32x4_t vqdmisl_laneq_s16(int32x4_t a, int16x4_t b, int16x8_t v, const int lane)      | a -> Vd.4S<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMLSL<br>Vd.4S,Vn.4H,Vm.H[lane]  | Vd.4S -> result | A64                     |
| int64x2_t vqdmisl_laneq_s32(int64x2_t a, int32x2_t b, int32x4_t v, const int lane)      | a -> Vd.2D<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMLSL<br>Vd.2D,Vn.2S,Vm.S[lane]  | Vd.2D -> result | A64                     |
| int32_t vqdmislh_laneq_s16(int32_t a, int16_t b, int16x8_t v, const int lane)           | a -> Sd<br>b -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7       | SQDMLSL Sd,Hn,Vm.H[lane]           | Sd -> result    | A64                     |
| int64_t vqdmislh_laneq_s32(int64_t a, int32_t b, int32x4_t v, const int lane)           | a -> Dd<br>b -> Sn<br>v -> Vm.4S<br>0 <= lane <= 3       | SQDMLSL Dd,Sn,Vm.S[lane]           | Dd -> result    | A64                     |
| int32x4_t vqdmisl_high_laneq_s16(int32x4_t a, int16x8_t b, int16x8_t v, const int lane) | a -> Vd.4S<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMLSL2<br>Vd.4S,Vn.8H,Vm.H[lane] | Vd.4S -> result | A64                     |
| int64x2_t vqdmisl_high_laneq_s32(int64x2_t a, int32x4_t b, int32x4_t v, const int lane) | a -> Vd.2D<br>b -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMLSL2<br>Vd.2D,Vn.4S,Vm.S[lane] | Vd.2D -> result | A64                     |
| int16x4_t vmul_n_s16(int16x4_t a, int16_t b)                                            | a -> Vn.4H<br>b -> Vm.H[0]                               | MUL Vd.4H,Vn.4H,Vm.H[0]            | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vmulq_n_s16(int16x8_t a, int16_t b)                                           | a -> Vn.8H<br>b -> Vm.H[0]                               | MUL Vd.8H,Vn.8H,Vm.H[0]            | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vmul_n_s32(int32x2_t a, int32_t b)                                            | a -> Vn.2S<br>b -> Vm.S[0]                               | MUL Vd.2S,Vn.2S,Vm.S[0]            | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vmulq_n_s32(int32x4_t a, int32_t b)                                           | a -> Vn.4S<br>b -> Vm.S[0]                               | MUL Vd.4S,Vn.4S,Vm.S[0]            | Vd.4S -> result | v7/A32/A64              |
| uint16x4_t vmul_n_u16(uint16x4_t a, uint16_t b)                                         | a -> Vn.4H<br>b -> Vm.H[0]                               | MUL Vd.4H,Vn.4H,Vm.H[0]            | Vd.4H -> result | v7/A32/A64              |
| uint16x8_t vmulq_n_u16(uint16x8_t a, uint16_t b)                                        | a -> Vn.8H<br>b -> Vm.H[0]                               | MUL Vd.8H,Vn.8H,Vm.H[0]            | Vd.8H -> result | v7/A32/A64              |
| uint32x2_t vmul_n_u32(uint32x2_t a, uint32_t b)                                         | a -> Vn.2S<br>b -> Vm.S[0]                               | MUL Vd.2S,Vn.2S,Vm.S[0]            | Vd.2S -> result | v7/A32/A64              |
| uint32x4_t vmulq_n_u32(uint32x4_t a, uint32_t b)                                        | a -> Vn.4S<br>b -> Vm.S[0]                               | MUL Vd.4S,Vn.4S,Vm.S[0]            | Vd.4S -> result | v7/A32/A64              |
| float32x2_t vmul_n_f32(float32x2_t a, float32_t b)                                      | a -> Vn.2S<br>b -> Vm.S[0]                               | FMUL Vd.2S,Vn.2S,Vm.S[0]           | Vd.2S -> result | v7/A32/A64              |
| float32x4_t vmulq_n_f32(float32x4_t a, float32_t b)                                     | a -> Vn.4S<br>b -> Vm.S[0]                               | FMUL Vd.4S,Vn.4S,Vm.S[0]           | Vd.4S -> result | v7/A32/A64              |
| float64x1_t vmul_n_f64(float64x1_t a, float64_t b)                                      | a -> Dn<br>b -> Vm.D[0]                                  | FMUL Dd,Dn,Vm.D[0]                 | Dd -> result    | A64                     |
| float64x2_t vmulq_n_f64(float64x2_t a, float64_t b)                                     | a -> Vn.2D<br>b -> Vm.D[0]                               | FMUL Vd.2D,Vn.2D,Vm.D[0]           | Vd.2D -> result | A64                     |
| int16x4_t vmul_lane_s16(int16x4_t a, int16x4_t v, const int lane)                       | a -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3               | MUL Vd.4H,Vn.4H,Vm.H[lane]         | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vmulq_lane_s16(int16x8_t a, int16x4_t v, const int lane)                      | a -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3               | MUL Vd.8H,Vn.8H,Vm.H[lane]         | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vmul_lane_s32(int32x2_t a, int32x2_t v, const int lane)                       | a -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1               | MUL Vd.2S,Vn.2S,Vm.S[lane]         | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vmulq_lane_s32(int32x4_t a, int32x2_t v, const int lane)                      | a -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1               | MUL Vd.4S,Vn.4S,Vm.S[lane]         | Vd.4S -> result | v7/A32/A64              |
| uint16x4_t vmul_lane_u16(uint16x4_t a, uint16x4_t v, const int lane)                    | a -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3               | MUL Vd.4H,Vn.4H,Vm.H[lane]         | Vd.4H -> result | v7/A32/A64              |

| Intrinsic                                                                 | Argument Preparation                   | Instruction                 | Result          | Supported Architectures |
|---------------------------------------------------------------------------|----------------------------------------|-----------------------------|-----------------|-------------------------|
| uint16x8_t vmulq_lane_u16(uint16x8_t a, uint16x4_t v, const int lane)     | a->Vn.8H<br>v->Vm.4H<br>0 <= lane <= 3 | MUL Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | v7/A32/A64              |
| uint32x2_t vmul_lane_u32(uint32x2_t a, uint32x2_t v, const int lane)      | a->Vn.2S<br>v->Vm.2S<br>0 <= lane <= 1 | MUL Vd.2S,Vn.2S,Vm.S[lane]  | Vd.2S -> result | v7/A32/A64              |
| uint32x4_t vmulq_lane_u32(uint32x4_t a, uint32x2_t v, const int lane)     | a->Vn.4S<br>v->Vm.2S<br>0 <= lane <= 1 | MUL Vd.4S,Vn.4S,Vm.S[lane]  | Vd.4S -> result | v7/A32/A64              |
| float32x2_t vmul_lane_f32(float32x2_t a, float32x2_t v, const int lane)   | a->Vn.2S<br>v->Vm.2S<br>0 <= lane <= 1 | FMUL Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | v7/A32/A64              |
| float32x4_t vmulq_lane_f32(float32x4_t a, float32x2_t v, const int lane)  | a->Vn.4S<br>v->Vm.2S<br>0 <= lane <= 1 | FMUL Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | v7/A32/A64              |
| float64x1_t vmul_lane_f64(float64x1_t a, float64x1_t v, const int lane)   | a->Dn<br>v->Vm.1D<br>lane == 0         | FMUL Dd,Dn,Vm.D[lane]       | Dd -> result    | A64                     |
| float64x2_t vmulq_lane_f64(float64x2_t a, float64x1_t v, const int lane)  | a->Vn.2D<br>v->Vm.1D<br>lane == 0      | FMUL Vd.2D,Vn.2D,Vm.D[lane] | Vd.2D -> result | A64                     |
| float32_t vmuls_lane_f32(float32_t a, float32x2_t v, const int lane)      | a->Sn<br>v->Vm.2S<br>0 <= lane <= 1    | FMUL Sd,Sn,Vm.S[lane]       | Sd -> result    | A64                     |
| float64_t vmuld_lane_f64(float64_t a, float64x1_t v, const int lane)      | a->Dn<br>v->Vm.1D<br>lane == 0         | FMUL Dd,Dn,Vm.S[lane]       | Dd -> result    | A64                     |
| int16x4_t vmul_laneq_s16(int16x4_t a, int16x8_t v, const int lane)        | a->Vn.4H<br>v->Vm.8H<br>0 <= lane <= 7 | MUL Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A64                     |
| int16x8_t vmulq_laneq_s16(int16x8_t a, int16x8_t v, const int lane)       | a->Vn.8H<br>v->Vm.8H<br>0 <= lane <= 7 | MUL Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A64                     |
| int32x2_t vmul_laneq_s32(int32x2_t a, int32x4_t v, const int lane)        | a->Vn.2S<br>v->Vm.4S<br>0 <= lane <= 3 | MUL Vd.2S,Vn.2S,Vm.S[lane]  | Vd.2S -> result | A64                     |
| int32x4_t vmulq_laneq_s32(int32x4_t a, int32x4_t v, const int lane)       | a->Vn.4S<br>v->Vm.4S<br>0 <= lane <= 3 | MUL Vd.4S,Vn.4S,Vm.S[lane]  | Vd.4S -> result | A64                     |
| uint16x4_t vmul_laneq_u16(uint16x4_t a, uint16x8_t v, const int lane)     | a->Vn.4H<br>v->Vm.8H<br>0 <= lane <= 7 | MUL Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A64                     |
| uint16x8_t vmulq_laneq_u16(uint16x8_t a, uint16x8_t v, const int lane)    | a->Vn.8H<br>v->Vm.8H<br>0 <= lane <= 7 | MUL Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A64                     |
| uint32x2_t vmul_laneq_u32(uint32x2_t a, uint32x4_t v, const int lane)     | a->Vn.2S<br>v->Vm.4S<br>0 <= lane <= 3 | MUL Vd.2S,Vn.2S,Vm.S[lane]  | Vd.2S -> result | A64                     |
| uint32x4_t vmulq_laneq_u32(uint32x4_t a, uint32x4_t v, const int lane)    | a->Vn.4S<br>v->Vm.4S<br>0 <= lane <= 3 | MUL Vd.4S,Vn.4S,Vm.S[lane]  | Vd.4S -> result | A64                     |
| float32x2_t vmul_laneq_f32(float32x2_t a, float32x4_t v, const int lane)  | a->Vn.2S<br>v->Vm.4S<br>0 <= lane <= 3 | FMUL Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | A64                     |
| float32x4_t vmulq_laneq_f32(float32x4_t a, float32x4_t v, const int lane) | a->Vn.4S<br>v->Vm.4S<br>0 <= lane <= 3 | FMUL Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | A64                     |

| Intrinsic                                                                  | Argument Preparation                         | Instruction                        | Result           | Supported Architectures |
|----------------------------------------------------------------------------|----------------------------------------------|------------------------------------|------------------|-------------------------|
| float64x1_t vmull_lane_f64(float64x1_t a, float64x2_t v, const int lane)   | a -> Vn, V -> Vm, ZD<br>0 -> lane <- 1       | FMUL Dd, Dn, Vm, D[lane]           | Dd -> result     | A64                     |
| float64x2_t vmullq_lane_f64(float64x2_t a, float64x2_t v, const int lane)  | a -> Vn, ZD<br>v -> Vm, ZD<br>0 -> lane <- 1 | FMUL Vd, ZD, Vn, ZD, Vm, D[lane]   | Vd, ZD -> result | A64                     |
| float32_t vmullq_lane_f32(float32_t a, float32x4_t v, const int lane)      | a -> Sn<br>v -> Vm, ZS<br>0 -> lane <- 3     | FMUL Sd, Sn, Vm, S[lane]           | Sd -> result     | A64                     |
| float64_t vmull_lane_f64(float64_t a, float64x2_t v, const int lane)       | a -> Dn<br>v -> Vm, ZD<br>0 -> lane <- 1     | FMUL Dd, Dn, Vm, D[lane]           | Dd -> result     | A64                     |
| int32x4_t vmull_n_s16(int32x4_t a, int16_t b)                              | a -> Vn, BH<br>b -> Vm, H[0]                 | SMULL Vd, 4S, Vn, 4H, Vm, H[0]     | Vd, 4S -> result | v7/A32/A64              |
| int64x2_t vmull_n_s32(int32x2_t a, int32_t b)                              | a -> Vn, ZS<br>b -> Vm, S[0]                 | SMULL Vd, ZD, Vn, 2S, Vm, S[0]     | Vd, ZD -> result | v7/A32/A64              |
| uint32x4_t vmull_n_u32(uint32x4_t a, uint32_t b)                           | a -> Vn, BH<br>b -> Vm, H[0]                 | UMULL Vd, 4S, Vn, 4H, Vm, H[0]     | Vd, 4S -> result | v7/A32/A64              |
| uint64x2_t vmull_n_u32(uint32x2_t a, uint32_t b)                           | a -> Vn, ZS<br>b -> Vm, S[0]                 | UMULL Vd, ZD, Vn, 2S, Vm, S[0]     | Vd, ZD -> result | v7/A32/A64              |
| int32x4_t vmull_high_n_s16(uint32x4_t a, int16_t b)                        | a -> Vn, BH<br>b -> Vm, H[0]                 | SMULL2 Vd, 4S, Vn, 8H, Vm, H[0]    | Vd, 4S -> result | A64                     |
| int64x2_t vmull_high_n_s32(uint32x4_t a, int32_t b)                        | a -> Vn, ZS<br>b -> Vm, S[0]                 | SMULL2 Vd, ZD, Vn, 4S, Vm, S[0]    | Vd, ZD -> result | A64                     |
| uint32x4_t vmull_high_n_u32(uint32x4_t a, uint32_t b)                      | a -> Vn, BH<br>b -> Vm, H[0]                 | UMULL2 Vd, 4S, Vn, 8H, Vm, H[0]    | Vd, 4S -> result | A64                     |
| uint64x2_t vmull_high_n_u32(uint32x4_t a, uint32_t b)                      | a -> Vn, ZS<br>b -> Vm, S[0]                 | UMULL2 Vd, ZD, Vn, 4S, Vm, S[0]    | Vd, ZD -> result | A64                     |
| int32x4_t vmull_lane_s16(int16x4_t a, int16x4_t v, const int lane)         | a -> Vn, BH<br>v -> Vm, 4H<br>0 -> lane <- 3 | SMULL Vd, 4S, Vn, 4H, Vm, H[lane]  | Vd, 4S -> result | v7/A32/A64              |
| int64x2_t vmull_lane_s32(int32x2_t a, int32x2_t v, const int lane)         | a -> Vn, ZS<br>v -> Vm, 2S<br>0 -> lane <- 1 | SMULL Vd, ZD, Vn, 2S, Vm, S[lane]  | Vd, ZD -> result | v7/A32/A64              |
| uint32x4_t vmull_lane_u16(uint16x4_t a, uint16x4_t v, const int lane)      | a -> Vn, BH<br>v -> Vm, 4H<br>0 -> lane <- 3 | UMULL Vd, 4S, Vn, 4H, Vm, H[lane]  | Vd, 4S -> result | v7/A32/A64              |
| uint64x2_t vmull_lane_u32(uint32x2_t a, uint32x2_t v, const int lane)      | a -> Vn, ZS<br>v -> Vm, 2S<br>0 -> lane <- 1 | UMULL Vd, ZD, Vn, 2S, Vm, S[lane]  | Vd, ZD -> result | v7/A32/A64              |
| int32x4_t vmull_high_lane_s16(int32x8_t a, int16x4_t v, const int lane)    | a -> Vn, BH<br>v -> Vm, 4H<br>0 -> lane <- 3 | SMULL2 Vd, 4S, Vn, 8H, Vm, H[lane] | Vd, 4S -> result | A64                     |
| int64x2_t vmull_high_lane_s32(int32x4_t a, int32x2_t v, const int lane)    | a -> Vn, ZS<br>v -> Vm, 2S<br>0 -> lane <- 1 | SMULL2 Vd, ZD, Vn, 4S, Vm, S[lane] | Vd, ZD -> result | A64                     |
| uint32x4_t vmull_high_lane_u32(uint16x8_t a, uint16x4_t v, const int lane) | a -> Vn, BH<br>v -> Vm, 4H<br>0 -> lane <- 3 | UMULL2 Vd, 4S, Vn, 8H, Vm, H[lane] | Vd, 4S -> result | A64                     |
| uint64x2_t vmull_high_lane_u32(uint32x4_t a, uint32x2_t v, const int lane) | a -> Vn, ZS<br>v -> Vm, 2S<br>0 -> lane <- 1 | UMULL2 Vd, ZD, Vn, 4S, Vm, S[lane] | Vd, ZD -> result | A64                     |
| int32x4_t vmull_lane_s16(int16x4_t a, int16x8_t v, const int lane)         | a -> Vn, BH<br>v -> Vm, 8H<br>0 -> lane <- 7 | SMULL Vd, 4S, Vn, 8H, Vm, H[lane]  | Vd, 4S -> result | A64                     |
| int64x2_t vmull_lane_s32(int32x2_t a, int32x4_t v, const int lane)         | a -> Vn, ZS<br>v -> Vm, 4S<br>0 -> lane <- 3 | SMULL Vd, ZD, Vn, 2S, Vm, S[lane]  | Vd, ZD -> result | A64                     |

| Intrinsic                                                                   | Argument Preparation                       | Instruction                     | Result          | Supported Architectures |
|-----------------------------------------------------------------------------|--------------------------------------------|---------------------------------|-----------------|-------------------------|
| uint32x4_t vmull_laneq_u16(uint16x4_t a, uint16x8_t v, const int lane)      | a -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | UMULL Vd.4S,Vn.4H,Vm.H[lane]    | Vd.4S -> result | A64                     |
| uint64x2_t vmull_laneq_u32(uint32x2_t a, uint32x4_t v, const int lane)      | a -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | UMULL Vd.2D,Vn.2S,Vm.S[lane]    | Vd.2D -> result | A64                     |
| int32x4_t vmull_high_laneq_s16(int16x8_t a, int16x8_t v, const int lane)    | a -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SMULL2 Vd.4S,Vn.8H,Vm.H[lane]   | Vd.4S -> result | A64                     |
| int64x2_t vmull_high_laneq_s32(int32x4_t a, int32x4_t v, const int lane)    | a -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SMULL2 Vd.2D,Vn.4S,Vm.S[lane]   | Vd.2D -> result | A64                     |
| uint32x4_t vmull_high_laneq_u16(uint16x8_t a, uint16x8_t v, const int lane) | a -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | UMULL2 Vd.4S,Vn.8H,Vm.H[lane]   | Vd.4S -> result | A64                     |
| uint64x2_t vmull_high_laneq_u32(uint32x4_t a, uint32x4_t v, const int lane) | a -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | UMULL2 Vd.2D,Vn.4S,Vm.S[lane]   | Vd.2D -> result | A64                     |
| int32x4_t vqdmull_n_s16(int16x4_t a, int16_t b)                             | a -> Vn.4H<br>b -> Vm.H[0]                 | SQDMULL Vd.4S,Vn.4H,Vm.H[0]     | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmull_n_s32(int32x2_t a, int32_t b)                             | a -> Vn.2S<br>b -> Vm.S[0]                 | SQDMULL Vd.2D,Vn.2S,Vm.S[0]     | Vd.2D -> result | v7/A32/A64              |
| int32x4_t vqdmull_high_n_s16(int16x8_t a, int16_t b)                        | a -> Vn.8H<br>b -> Vm.H[0]                 | SQDMULL2 Vd.4S,Vn.8H,Vm.H[0]    | Vd.4S -> result | A64                     |
| int64x2_t vqdmull_high_n_s32(int32x4_t a, int32_t b)                        | a -> Vn.4S<br>b -> Vm.S[0]                 | SQDMULL2 Vd.2D,Vn.4S,Vm.S[0]    | Vd.2D -> result | A64                     |
| int32x4_t vqdmull_lane_s16(int16x4_t a, int16x4_t v, const int lane)        | a -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMULL Vd.4S,Vn.4H,Vm.H[lane]  | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmull_lane_s32(int32x2_t a, int32x2_t v, const int lane)        | a -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMULL Vd.2D,Vn.2S,Vm.S[lane]  | Vd.2D -> result | v7/A32/A64              |
| int32_t vqdmullh_lane_s16(int16_t a, int16x4_t v, const int lane)           | a -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3    | SQDMULL Sd,Hn,Vm.H[lane]        | Sd -> result    | A64                     |
| int64_t vqdmulls_lane_s32(int32_t a, int32x2_t v, const int lane)           | a -> Sn<br>v -> Vm.2S<br>0 <= lane <= 1    | SQDMULL Dd,Sn,Vm.S[lane]        | Dd -> result    | A64                     |
| int32x4_t vqdmull_high_lane_s16(int16x8_t a, int16x4_t v, const int lane)   | a -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMULL2 Vd.4S,Vn.8H,Vm.H[lane] | Vd.4S -> result | A64                     |
| int64x2_t vqdmull_high_lane_s32(int32x4_t a, int32x2_t v, const int lane)   | a -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMULL2 Vd.2D,Vn.4S,Vm.S[lane] | Vd.2D -> result | A64                     |
| int32x4_t vqdmull_laneq_s16(int16x4_t a, int16x8_t v, const int lane)       | a -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMULL Vd.4S,Vn.4H,Vm.H[lane]  | Vd.4S -> result | A64                     |
| int64x2_t vqdmull_laneq_s32(int32x2_t a, int32x4_t v, const int lane)       | a -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMULL Vd.2D,Vn.2S,Vm.S[lane]  | Vd.2D -> result | A64                     |
| int32_t vqdmullh_laneq_s16(int16_t a, int16x8_t v, const int lane)          | a -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7    | SQDMULL Sd,Hn,Vm.H[lane]        | Sd -> result    | A64                     |
| int64_t vqdmulls_laneq_s32(int32_t a, int32x4_t v, const int lane)          | a -> Sn<br>v -> Vm.4S<br>0 <= lane <= 3    | SQDMULL Dd,Sn,Vm.S[lane]        | Dd -> result    | A64                     |

| Intrinsic                                                                  | Argument Preparation                       | Instruction                        | Result          | Supported Architectures |
|----------------------------------------------------------------------------|--------------------------------------------|------------------------------------|-----------------|-------------------------|
| int32x4_t vqdmull_high_lane_s16(int16x8_t a, int16x8_t v, const int lane)  | a -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMULL2<br>Vd.4S,Vn.8H,Vm.H[lane] | Vd.4S -> result | A64                     |
| int64x2_t vqdmull_high_laneq_s32(int32x4_t a, int32x4_t v, const int lane) | a -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMULL2<br>Vd.2D,Vn.4S,Vm.S[lane] | Vd.2D -> result | A64                     |
| int16x4_t vqdmulh_n_s16(int16x4_t a, int16_t b)                            | a -> Vn.4H<br>b -> Vm.H[0]                 | SQDMULH Vd.4H,Vn.4H,Vm.H[0]        | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vqdmulhq_n_s16(int16x8_t a, int16_t b)                           | a -> Vn.8H<br>b -> Vm.H[0]                 | SQDMULH Vd.8H,Vn.8H,Vm.H[0]        | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vqdmulh_n_s32(int32x2_t a, int32_t b)                            | a -> Vn.2S<br>b -> Vm.S[0]                 | SQDMULH Vd.2S,Vn.2S,Vm.S[0]        | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vqdmulhq_n_s32(int32x4_t a, int32_t b)                           | a -> Vn.4S<br>b -> Vm.S[0]                 | SQDMULH Vd.4S,Vn.4S,Vm.S[0]        | Vd.4S -> result | v7/A32/A64              |
| int16x4_t vqdmulh_lane_s16(int16x4_t a, int16x4_t v, const int lane)       | a -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMULH<br>Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vqdmulhq_lane_s16(int16x8_t a, int16x4_t v, const int lane)      | a -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQDMULH<br>Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vqdmulh_lane_s32(int32x2_t a, int32x2_t v, const int lane)       | a -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMULH<br>Vd.2S,Vn.2S,Vm.S[lane]  | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vqdmulhq_lane_s32(int32x4_t a, int32x2_t v, const int lane)      | a -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQDMULH<br>Vd.4S,Vn.4S,Vm.S[lane]  | Vd.4S -> result | v7/A32/A64              |
| int16_t vqdmulh_lane_s16(int16_t a, int16x4_t v, const int lane)           | a -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3    | SQDMULH Hd,Hn,Vm.H[lane]           | Hd -> result    | A64                     |
| int32_t vqdmulhs_lane_s32(int32_t a, int32x2_t v, const int lane)          | a -> Sn<br>v -> Vm.2S<br>0 <= lane <= 1    | SQDMULH Sd,Sn,Vm.H[lane]           | Sd -> result    | A64                     |
| int16x4_t vqdmulh_laneq_s16(int16x4_t a, int16x8_t v, const int lane)      | a -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMULH<br>Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A64                     |
| int16x8_t vqdmulhq_laneq_s16(int16x8_t a, int16x8_t v, const int lane)     | a -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQDMULH<br>Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A64                     |
| int32x2_t vqdmulh_laneq_s32(int32x2_t a, int32x4_t v, const int lane)      | a -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMULH<br>Vd.2S,Vn.2S,Vm.S[lane]  | Vd.2S -> result | A64                     |
| int32x4_t vqdmulhq_laneq_s32(int32x4_t a, int32x4_t v, const int lane)     | a -> Vn.4S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQDMULH<br>Vd.4S,Vn.4S,Vm.S[lane]  | Vd.4S -> result | A64                     |
| int16_t vqdmulh_laneq_s16(int16_t a, int16x8_t v, const int lane)          | a -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7    | SQDMULH Hd,Hn,Vm.H[lane]           | Hd -> result    | A64                     |
| int32_t vqdmulhs_laneq_s32(int32_t a, int32x4_t v, const int lane)         | a -> Sn<br>v -> Vm.4S<br>0 <= lane <= 3    | SQDMULH Sd,Sn,Vm.H[lane]           | Sd -> result    | A64                     |
| int16x4_t vqrdmulh_n_s16(int16x4_t a, int16_t b)                           | a -> Vn.4H<br>b -> Vm.H[0]                 | SQRDMULH<br>Vd.4H,Vn.4H,Vm.H[0]    | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vqrdmulhq_n_s16(int16x8_t a, int16_t b)                          | a -> Vn.8H<br>b -> Vm.H[0]                 | SQRDMULH<br>Vd.8H,Vn.8H,Vm.H[0]    | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vqrdmulh_n_s32(int32x2_t a, int32_t b)                           | a -> Vn.2S<br>b -> Vm.S[0]                 | SQRDMULH Vd.2S,Vn.2S,Vm.S[0]       | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vqrdmulhq_n_s32(int32x4_t a, int32_t b)                          | a -> Vn.4S<br>b -> Vm.S[0]                 | SQRDMULH Vd.4S,Vn.4S,Vm.S[0]       | Vd.4S -> result | v7/A32/A64              |

| Intrinsic                                                               | Argument Preparation                   | Instruction                        | Result          | Supported Architectures |
|-------------------------------------------------------------------------|----------------------------------------|------------------------------------|-----------------|-------------------------|
| int16x4_t vqrdmulh_lane_s16(int16x4_t a, int16x4_t v, const int lane)   | a->Vn,4H<br>v->Vm,4H<br>0 <= lane <= 3 | SQRDMULH<br>Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vqrdmulhq_lane_s16(int16x8_t a, int16x4_t v, const int lane)  | a->Vn,8H<br>v->Vm,4H<br>0 <= lane <= 3 | SQRDMULH<br>Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vqrdmulh_lane_s32(int32x2_t a, int32x2_t v, const int lane)   | a->Vn,2S<br>v->Vm,2S<br>0 <= lane <= 1 | SQRDMULH<br>Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vqrdmulhq_lane_s32(int32x4_t a, int32x2_t v, const int lane)  | a->Vn,4S<br>v->Vm,2S<br>0 <= lane <= 1 | SQRDMULH<br>Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | v7/A32/A64              |
| int16_t vqrdmulh_lane_s16(int16_t a, int16x4_t v, const int lane)       | a->Hn<br>v->Vm,4H<br>0 <= lane <= 3    | SQRDMULH Hd,Hn,Vm.H[lane]          | Hd -> result    | A64                     |
| int32_t vqrdmulhs_lane_s32(int32_t a, int32x2_t v, const int lane)      | a->Sn<br>v->Vm,2S<br>0 <= lane <= 1    | SQRDMULH Sd,Sn,Vm.S[lane]          | Sd -> result    | A64                     |
| int16x4_t vqrdmulh_laneq_s16(int16x4_t a, int16x8_t v, const int lane)  | a->Vn,4H<br>v->Vm,8H<br>0 <= lane <= 7 | SQRDMULH<br>Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| int16x8_t vqrdmulhq_laneq_s16(int16x8_t a, int16x8_t v, const int lane) | a->Vn,8H<br>v->Vm,8H<br>0 <= lane <= 7 | SQRDMULH<br>Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |
| int32x2_t vqrdmulh_laneq_s32(int32x2_t a, int32x4_t v, const int lane)  | a->Vn,2S<br>v->Vm,4S<br>0 <= lane <= 3 | SQRDMULH<br>Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | A64                     |
| int32x4_t vqrdmulhq_laneq_s32(int32x4_t a, int32x4_t v, const int lane) | a->Vn,4S<br>v->Vm,4S<br>0 <= lane <= 3 | SQRDMULH<br>Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | A64                     |
| int16_t vqrdmulh_laneq_s16(int16_t a, int16x8_t v, const int lane)      | a->Hn<br>v->Vm,8H<br>0 <= lane <= 7    | SQRDMULH Hd,Hn,Vm.H[lane]          | Hd -> result    | A64                     |
| int32_t vqrdmulhs_laneq_s32(int32_t a, int32x4_t v, const int lane)     | a->Sn<br>v->Vm,4S<br>0 <= lane <= 3    | SQRDMULH Sd,Sn,Vm.S[lane]          | Sd -> result    | A64                     |
| int16x4_t vmla_n_s16(int16x4_t a, int16x4_t b, int16_t c)               | a->Vd,4H<br>b->Vn,4H<br>c->Vm,H[0]     | MLA Vd.4H,Vn.4H,Vm.H[0]            | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vmlaq_n_s16(int16x8_t a, int16x8_t b, int16_t c)              | a->Vd,8H<br>b->Vn,8H<br>c->Vm,H[0]     | MLA Vd.8H,Vn.8H,Vm.H[0]            | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vmla_n_s32(int32x2_t a, int32x2_t b, int32_t c)               | a->Vd,2S<br>b->Vn,2S<br>c->Vm,S[0]     | MLA Vd.2S,Vn.2S,Vm.S[0]            | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vmlaq_n_s32(int32x4_t a, int32x4_t b, int32_t c)              | a->Vd,4S<br>b->Vn,4S<br>c->Vm,S[0]     | MLA Vd.4S,Vn.4S,Vm.S[0]            | Vd.4S -> result | v7/A32/A64              |
| uint16x4_t vmla_n_u16(uint16x4_t a, uint16x4_t b, uint16_t c)           | a->Vd,4H<br>b->Vn,4H<br>c->Vm,H[0]     | MLA Vd.4H,Vn.4H,Vm.H[0]            | Vd.4H -> result | v7/A32/A64              |
| uint16x8_t vmlaq_n_u16(uint16x8_t a, uint16x8_t b, uint16_t c)          | a->Vd,8H<br>b->Vn,8H<br>c->Vm,H[0]     | MLA Vd.8H,Vn.8H,Vm.H[0]            | Vd.8H -> result | v7/A32/A64              |
| uint32x2_t vmla_n_u32(uint32x2_t a, uint32x2_t b, uint32_t c)           | a->Vd,2S<br>b->Vn,2S<br>c->Vm,S[0]     | MLA Vd.2S,Vn.2S,Vm.S[0]            | Vd.2S -> result | v7/A32/A64              |
| uint32x4_t vmlaq_n_u32(uint32x4_t a, uint32x4_t b, uint32_t c)          | a->Vd,4S<br>b->Vn,4S<br>c->Vm,S[0]     | MLA Vd.4S,Vn.4S,Vm.S[0]            | Vd.4S -> result | v7/A32/A64              |

| Intrinsic                                                          | Argument Preparation               | Instruction                                  | Result          | Supported Architectures |
|--------------------------------------------------------------------|------------------------------------|----------------------------------------------|-----------------|-------------------------|
| float32x2_t vmul_n_f32(float32x2_t a, float32x2_t b, float32_t c)  | a->N/A<br>b->N/A<br>c->N/A         | RESULT[i] = a[i] + (b[i] * c) for i = 0 to 1 | N/A -> result   | v7/A32/A64              |
| float32x4_t vmulq_n_f32(float32x4_t a, float32x4_t b, float32_t c) | a->N/A<br>b->N/A<br>c->N/A         | RESULT[i] = a[i] + (b[i] * c) for i = 0 to 3 | N/A -> result   | v7/A32/A64              |
| int32x4_t vmul_n_s16(int32x4_t a, int16x4_t b, int16_t c)          | a->Vd.4S<br>b->Vn.4H<br>c->Vn.H[0] | SMLAL Vd.4S,Vn.4H,Vm.H[0]                    | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vmul_n_s32(int64x2_t a, int32x2_t b, int32_t c)          | a->Vd.2D<br>b->Vn.2S<br>c->Vn.S[0] | SMLAL Vd.2D,Vn.2S,Vm.S[0]                    | Vd.2D -> result | v7/A32/A64              |
| uint32x4_t vmul_n_u16(uint32x4_t a, uint16x4_t b, uint16_t c)      | a->Vd.4S<br>b->Vn.4H<br>c->Vn.H[0] | UMLAL Vd.4S,Vn.4H,Vm.H[0]                    | Vd.4S -> result | v7/A32/A64              |
| uint64x2_t vmul_n_u32(uint64x2_t a, uint32x2_t b, uint32_t c)      | a->Vd.2D<br>b->Vn.2S<br>c->Vn.S[0] | UMLAL Vd.2D,Vn.2S,Vm.S[0]                    | Vd.2D -> result | v7/A32/A64              |
| int32x4_t vmul_high_n_s16(int32x4_t a, int16x8_t b, int16_t c)     | a->Vd.4S<br>b->Vn.8H<br>c->Vn.H[0] | SMLAL2 Vd.4S,Vn.8H,Vm.H[0]                   | Vd.4S -> result | A64                     |
| int64x2_t vmul_high_n_s32(int64x2_t a, int32x4_t b, int32_t c)     | a->Vd.2D<br>b->Vn.4S<br>c->Vn.S[0] | SMLAL2 Vd.2D,Vn.4S,Vm.S[0]                   | Vd.2D -> result | A64                     |
| uint32x4_t vmul_high_n_u16(uint32x4_t a, uint16x8_t b, uint16_t c) | a->Vd.4S<br>b->Vn.8H<br>c->Vn.H[0] | UMLAL2 Vd.4S,Vn.8H,Vm.H[0]                   | Vd.4S -> result | A64                     |
| uint64x2_t vmul_high_n_u32(uint64x2_t a, uint32x4_t b, uint32_t c) | a->Vd.2D<br>b->Vn.4S<br>c->Vn.S[0] | UMLAL2 Vd.2D,Vn.4S,Vm.S[0]                   | Vd.2D -> result | A64                     |
| int32x4_t vqdmul_n_s16(int32x4_t a, int16x4_t b, int16_t c)        | a->Vd.4S<br>b->Vn.4H<br>c->Vn.H[0] | SQDMLAL Vd.4S,Vn.4H,Vm.H[0]                  | Vd.4S -> result | v7/A32/A64              |
| int64x2_t vqdmul_n_s32(int64x2_t a, int32x2_t b, int32_t c)        | a->Vd.2D<br>b->Vn.2S<br>c->Vn.S[0] | SQDMLAL Vd.2D,Vn.2S,Vm.S[0]                  | Vd.2D -> result | v7/A32/A64              |
| int32x4_t vqdmul_high_n_s16(int32x4_t a, int16x8_t b, int16_t c)   | a->Vd.4S<br>b->Vn.8H<br>c->Vn.H[0] | SQDMLAL2 Vd.4S,Vn.8H,Vm.H[0]                 | Vd.4S -> result | A64                     |
| int64x2_t vqdmul_high_n_s32(int64x2_t a, int32x4_t b, int32_t c)   | a->Vd.2D<br>b->Vn.4S<br>c->Vn.S[0] | SQDMLAL2 Vd.2D,Vn.4S,Vm.S[0]                 | Vd.2D -> result | A64                     |
| int16x4_t vmuls_n_s16(int16x4_t a, int16x4_t b, int16_t c)         | a->Vd.4H<br>b->Vn.4H<br>c->Vn.H[0] | MLS Vd.4H,Vn.4H,Vm.H[0]                      | Vd.4H -> result | v7/A32/A64              |
| int16x8_t vmlsq_n_s16(int16x8_t a, int16x8_t b, int16_t c)         | a->Vd.8H<br>b->Vn.8H<br>c->Vn.H[0] | MLS Vd.8H,Vn.8H,Vm.H[0]                      | Vd.8H -> result | v7/A32/A64              |
| int32x2_t vmuls_n_s32(int32x2_t a, int32x2_t b, int32_t c)         | a->Vd.2S<br>b->Vn.2S<br>c->Vn.S[0] | MLS Vd.2S,Vn.2S,Vm.S[0]                      | Vd.2S -> result | v7/A32/A64              |
| int32x4_t vmlsq_n_s32(int32x4_t a, int32x4_t b, int32_t c)         | a->Vd.4S<br>b->Vn.4S<br>c->Vn.S[0] | MLS Vd.4S,Vn.4S,Vm.S[0]                      | Vd.4S -> result | v7/A32/A64              |
| uint16x4_t vmuls_n_u16(uint16x4_t a, uint16x4_t b, uint16_t c)     | a->Vd.4H<br>b->Vn.4H<br>c->Vn.H[0] | MLS Vd.4H,Vn.4H,Vm.H[0]                      | Vd.4H -> result | v7/A32/A64              |
| uint16x8_t vmlsq_n_u16(uint16x8_t a, uint16x8_t b, uint16_t c)     | a->Vd.8H<br>b->Vn.8H<br>c->Vn.H[0] | MLS Vd.8H,Vn.8H,Vm.H[0]                      | Vd.8H -> result | v7/A32/A64              |
| uint32x2_t vmuls_n_u32(uint32x2_t a, uint32x2_t b, uint32_t c)     | a->Vd.2S<br>b->Vn.2S<br>c->Vn.S[0] | MLS Vd.2S,Vn.2S,Vm.S[0]                      | Vd.2S -> result | v7/A32/A64              |
| uint32x4_t vmlsq_n_u32(uint32x4_t a, uint32x4_t b, uint32_t c)     | a->Vd.4S<br>b->Vn.4S<br>c->Vn.S[0] | MLS Vd.4S,Vn.4S,Vm.S[0]                      | Vd.4S -> result | v7/A32/A64              |
| float32x2_t vmul_n_f32(float32x2_t a, float32x2_t b, float32_t c)  | a->N/A<br>b->N/A<br>c->N/A         | RESULT[i] = a[i] - (b[i] * c) for i = 0 to 1 | N/A -> result   | v7/A32/A64              |
| float32x4_t vmulq_n_f32(float32x4_t a, float32x4_t b, float32_t c) | a->N/A<br>b->N/A<br>c->N/A         | RESULT[i] = a[i] - (b[i] * c) for i = 0 to 3 | N/A -> result   | v7/A32/A64              |

| Intrinsic                                                           | Argument Preparation                     | Instruction                  | Result           | Supported Architectures |
|---------------------------------------------------------------------|------------------------------------------|------------------------------|------------------|-------------------------|
| int32x4_t vmvsl_n_s16(int32x4_t a, int16x4_t b, int16_t c)          | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.H[0] | SMLSL Vd.4S,Vn.4H,Vm.H[0]    | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vmvsl_n_s32(int64x2_t a, int32x2_t b, int32_t c)          | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.S[0] | SMLSL Vd.2D,Vn.2S,Vm.S[0]    | Vd.2D -> result  | v7/A32/A64              |
| uint32x4_t vmvsl_n_u16(uint32x4_t a, uint16x4_t b, uint16_t c)      | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.H[0] | UMLSL Vd.4S,Vn.4H,Vm.H[0]    | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vmvsl_n_u32(uint64x2_t a, uint32x2_t b, uint32_t c)      | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.S[0] | UMLSL Vd.2D,Vn.2S,Vm.S[0]    | Vd.2D -> result  | v7/A32/A64              |
| int32x4_t vmvsl_high_n_s16(int32x4_t a, int16x8_t b, int16_t c)     | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.H[0] | SMLSL2 Vd.4S,Vn.8H,Vm.H[0]   | Vd.4S -> result  | A64                     |
| int64x2_t vmvsl_high_n_s32(int64x2_t a, int32x4_t b, int32_t c)     | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.S[0] | SMLSL2 Vd.2D,Vn.4S,Vm.S[0]   | Vd.2D -> result  | A64                     |
| uint32x4_t vmvsl_high_n_u16(uint32x4_t a, uint16x8_t b, uint16_t c) | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.H[0] | UMLSL2 Vd.4S,Vn.8H,Vm.H[0]   | Vd.4S -> result  | A64                     |
| uint64x2_t vmvsl_high_n_u32(uint64x2_t a, uint32x4_t b, uint32_t c) | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.S[0] | UMLSL2 Vd.2D,Vn.4S,Vm.S[0]   | Vd.2D -> result  | A64                     |
| int32x4_t vqdmisl_n_s16(int32x4_t a, int16x4_t b, int16_t c)        | a -> Vd.4S<br>b -> Vn.4H<br>c -> Vm.H[0] | SQDMISL Vd.4S,Vn.4H,Vm.H[0]  | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vqdmisl_n_s32(int64x2_t a, int32x2_t b, int32_t c)        | a -> Vd.2D<br>b -> Vn.2S<br>c -> Vm.S[0] | SQDMISL Vd.2D,Vn.2S,Vm.S[0]  | Vd.2D -> result  | v7/A32/A64              |
| int32x4_t vqdmisl_high_n_s16(int32x4_t a, int16x8_t b, int16_t c)   | a -> Vd.4S<br>b -> Vn.8H<br>c -> Vm.H[0] | SQDMISL2 Vd.4S,Vn.8H,Vm.H[0] | Vd.4S -> result  | A64                     |
| int64x2_t vqdmisl_high_n_s32(int64x2_t a, int32x4_t b, int32_t c)   | a -> Vd.2D<br>b -> Vn.4S<br>c -> Vm.S[0] | SQDMISL2 Vd.2D,Vn.4S,Vm.S[0] | Vd.2D -> result  | A64                     |
| int8x8_t vabs_s8(int8x8_t a)                                        | a -> Vn.8B                               | ABS Vd.8B,Vn.8B              | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t tvabsq_s8(int8x16_t a)                                    | a -> Vn.16B                              | ABS Vd.16B,Vn.16B            | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vabs_s16(int16x4_t a)                                     | a -> Vn.4H                               | ABS Vd.4H,Vn.4H              | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t tvabsq_s16(int16x8_t a)                                   | a -> Vn.8H                               | ABS Vd.8H,Vn.8H              | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vabs_s32(int32x2_t a)                                     | a -> Vn.2S                               | ABS Vd.2S,Vn.2S              | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t tvabsq_s32(int32x4_t a)                                   | a -> Vn.4S                               | ABS Vd.4S,Vn.4S              | Vd.4S -> result  | v7/A32/A64              |
| float32x2_t vabs_f32(float32x2_t a)                                 | a -> Vn.2S                               | FABS Vd.2S,Vn.2S             | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t tvabsq_f32(float32x4_t a)                               | a -> Vn.4S                               | FABS Vd.4S,Vn.4S             | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vabs_s64(int64x1_t a)                                     | a -> Dn                                  | ABS Dd,Dn                    | Dd -> result     | A64                     |
| int64_t vabsd_s64(int64_t a)                                        | a -> Dn                                  | ABS Dd,Dn                    | Dd -> result     | A64                     |
| int64x2_t tvabsq_s64(int64x2_t a)                                   | a -> Vn.2D                               | ABS Vd.2D,Vn.2D              | Vd.2D -> result  | A64                     |
| float64x1_t vabsq_f64(float64x1_t a)                                | a -> Dn                                  | FABS Dd,Dn                   | Dd -> result     | A64                     |
| float64x2_t tvabsq_f64(float64x2_t a)                               | a -> Vn.2D                               | FABS Vd.2D,Vn.2D             | Vd.2D -> result  | A64                     |
| int8x8_t vqabs_s8(int8x8_t a)                                       | a -> Vn.8B                               | SQABS Vd.8B,Vn.8B            | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t tvqabsq_s8(int8x16_t a)                                   | a -> Vn.16B                              | SQABS Vd.16B,Vn.16B          | Vd.16B -> result | v7/A32/A64              |
| int16x4_t tvqabs_s16(int16x4_t a)                                   | a -> Vn.4H                               | SQABS Vd.4H,Vn.4H            | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t tvqabsq_s16(int16x8_t a)                                  | a -> Vn.8H                               | SQABS Vd.8H,Vn.8H            | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t tvqabs_s32(int32x2_t a)                                   | a -> Vn.2S                               | SQABS Vd.2S,Vn.2S            | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t tvqabsq_s32(int32x4_t a)                                  | a -> Vn.4S                               | SQABS Vd.4S,Vn.4S            | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t tvqabsq_s64(int64x1_t a)                                  | a -> Dn                                  | SQABS Dd,Dn                  | Dd -> result     | A64                     |
| int64x2_t tvqabsq_s64(int64x2_t a)                                  | a -> Vn.2D                               | SQABS Vd.2D,Vn.2D            | Vd.2D -> result  | A64                     |
| int8_t tvqabsb_s8(int8_t a)                                         | a -> Bn                                  | SQABS Bd,Bn                  | Bd -> result     | A64                     |
| int16_t tvqabsh_s16(int16_t a)                                      | a -> Hn                                  | SQABS Hd,Hn                  | Hd -> result     | A64                     |
| int32_t tvqabbs_s32(int32_t a)                                      | a -> Sn                                  | SQABS Sd,Sn                  | Sd -> result     | A64                     |
| int64_t tvqabbsd_s64(int64_t a)                                     | a -> Dn                                  | SQABS Dd,Dn                  | Dd -> result     | A64                     |
| int8x8_t tvneg_s8(int8x8_t a)                                       | a -> Vn.8B                               | NEG Vd.8B,Vn.8B              | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t tvnegq_s8(int8x16_t a)                                    | a -> Vn.16B                              | NEG Vd.16B,Vn.16B            | Vd.16B -> result | v7/A32/A64              |
| int16x4_t tvneg_s16(int16x4_t a)                                    | a -> Vn.4H                               | NEG Vd.4H,Vn.4H              | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t tvnegq_s16(int16x8_t a)                                   | a -> Vn.8H                               | NEG Vd.8H,Vn.8H              | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t tvneg_s32(int32x2_t a)                                    | a -> Vn.2S                               | NEG Vd.2S,Vn.2S              | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t tvnegq_s32(int32x4_t a)                                   | a -> Vn.4S                               | NEG Vd.4S,Vn.4S              | Vd.4S -> result  | v7/A32/A64              |
| float32x2_t tvneg_f32(float32x2_t a)                                | a -> Vn.2S                               | FNEG Vd.2S,Vn.2S             | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t tvnegq_f32(float32x4_t a)                               | a -> Vn.4S                               | FNEG Vd.4S,Vn.4S             | Vd.4S -> result  | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation | Instruction             | Result         | Supported Architectures |
|-------------------------------------------------------|----------------------|-------------------------|----------------|-------------------------|
| int64x1_t vnegd_s64(int64x1_t a)                      | a->Dn                | NEG Dd,Dn               | Dd->result     | A64                     |
| int64_t vnegd_s64(int64_t a)                          | a->Dn                | NEG Dd,Dn               | Dd->result     | A64                     |
| int64x2_t vnegd_s64(int64x2_t a)                      | a->Vn,2D             | NEG Vd,2D,Vn,2D         | Vd,2D->result  | A64                     |
| float64x1_t vnegf_f64(float64x1_t a)                  | a->Dn                | FNEG Dd,Dn              | Dd->result     | A64                     |
| float64x2_t vnegf_f64(float64x2_t a)                  | a->Vn,2D             | FNEG Vd,2D,Vn,2D        | Vd,2D->result  | A64                     |
| int8x8_t vqneg_s8(int8x8_t a)                         | a->Vn,8B             | SQNEG Vd,8B,Vn,8B       | Vd,8B->result  | v7/A32/A64              |
| int8x16_t vqnegq_s8(int8x16_t a)                      | a->Vn,16B            | SQNEG Vd,16B,Vn,16B     | Vd,16B->result | v7/A32/A64              |
| int16x4_t vqneg_s16(int16x4_t a)                      | a->Vn,4H             | SQNEG Vd,4H,Vn,4H       | Vd,4H->result  | v7/A32/A64              |
| int16x8_t vqnegq_s16(int16x8_t a)                     | a->Vn,8H             | SQNEG Vd,8H,Vn,8H       | Vd,8H->result  | v7/A32/A64              |
| int32x2_t vqneg_s32(int32x2_t a)                      | a->Vn,2S             | SQNEG Vd,2S,Vn,2S       | Vd,2S->result  | v7/A32/A64              |
| int32x4_t vqnegq_s32(int32x4_t a)                     | a->Vn,4S             | SQNEG Vd,4S,Vn,4S       | Vd,4S->result  | v7/A32/A64              |
| int64x1_t vqneg_s64(int64x1_t a)                      | a->Dn                | SQNEG Dd,Dn             | Dd->result     | A64                     |
| int64x2_t vqnegq_s64(int64x2_t a)                     | a->Vn,2D             | SQNEG Vd,2D,Vn,2D       | Vd,2D->result  | A64                     |
| int8_t vqnegb_s8(int8_t a)                            | a->Bn                | SQNEG Bd,Bn             | Bd->result     | A64                     |
| int16_t vqnegh_s16(int16_t a)                         | a->Hn                | SQNEG Hd,Hn             | Hd->result     | A64                     |
| int32_t vqnegs_s32(int32_t a)                         | a->Sn                | SQNEG Sd,Sn             | Sd->result     | A64                     |
| int64_t vqnegd_s64(int64_t a)                         | a->Dn                | SQNEG Dd,Dn             | Dd->result     | A64                     |
| int8x8_t vclvs_s8(int8x8_t a)                         | a->Vn,8B             | CLS Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| int8x16_t vclvsq_s8(int8x16_t a)                      | a->Vn,16B            | CLS Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| int16x4_t vclvs_s16(int16x4_t a)                      | a->Vn,4H             | CLS Vd,4H,Vn,4H         | Vd,4H->result  | v7/A32/A64              |
| int16x8_t vclvsq_s16(int16x8_t a)                     | a->Vn,8H             | CLS Vd,8H,Vn,8H         | Vd,8H->result  | v7/A32/A64              |
| int32x2_t vclvs_s32(int32x2_t a)                      | a->Vn,2S             | CLS Vd,2S,Vn,2S         | Vd,2S->result  | v7/A32/A64              |
| int32x4_t vclvsq_s32(int32x4_t a)                     | a->Vn,4S             | CLS Vd,4S,Vn,4S         | Vd,4S->result  | v7/A32/A64              |
| int8x8_t vclvs_u8(uint8x8_t a)                        | a->Vn,8B             | CLS Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| int8x16_t vclvsq_u8(uint8x16_t a)                     | a->Vn,16B            | CLS Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| int16x4_t vclvs_u16(uint16x4_t a)                     | a->Vn,4H             | CLS Vd,4H,Vn,4H         | Vd,4H->result  | v7/A32/A64              |
| int16x8_t vclvsq_u16(uint16x8_t a)                    | a->Vn,8H             | CLS Vd,8H,Vn,8H         | Vd,8H->result  | v7/A32/A64              |
| int32x2_t vclvs_s32(uint32x2_t a)                     | a->Vn,2S             | CLS Vd,2S,Vn,2S         | Vd,2S->result  | v7/A32/A64              |
| int32x4_t vclvsq_s32(uint32x4_t a)                    | a->Vn,4S             | CLS Vd,4S,Vn,4S         | Vd,4S->result  | v7/A32/A64              |
| int8x8_t vclz_s8(int8x8_t a)                          | a->Vn,8B             | CLZ Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| int8x16_t vclzq_s8(int8x16_t a)                       | a->Vn,16B            | CLZ Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| int16x4_t vclz_s16(uint16x4_t a)                      | a->Vn,4H             | CLZ Vd,4H,Vn,4H         | Vd,4H->result  | v7/A32/A64              |
| int16x8_t vclzq_s16(uint16x8_t a)                     | a->Vn,8H             | CLZ Vd,8H,Vn,8H         | Vd,8H->result  | v7/A32/A64              |
| int32x2_t vclz_s32(uint32x2_t a)                      | a->Vn,2S             | CLZ Vd,2S,Vn,2S         | Vd,2S->result  | v7/A32/A64              |
| int32x4_t vclzq_s32(uint32x4_t a)                     | a->Vn,4S             | CLZ Vd,4S,Vn,4S         | Vd,4S->result  | v7/A32/A64              |
| uint8x8_t vclz_u8(uint8x8_t a)                        | a->Vn,8B             | CLZ Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| uint8x16_t vclzq_u8(uint8x16_t a)                     | a->Vn,16B            | CLZ Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| uint16x4_t vclz_u16(uint16x4_t a)                     | a->Vn,4H             | CLZ Vd,4H,Vn,4H         | Vd,4H->result  | v7/A32/A64              |
| uint16x8_t vclzq_u16(uint16x8_t a)                    | a->Vn,8H             | CLZ Vd,8H,Vn,8H         | Vd,8H->result  | v7/A32/A64              |
| uint32x2_t vclz_s32(uint32x2_t a)                     | a->Vn,2S             | CLZ Vd,2S,Vn,2S         | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vclzq_s32(uint32x4_t a)                    | a->Vn,4S             | CLZ Vd,4S,Vn,4S         | Vd,4S->result  | v7/A32/A64              |
| int8x8_t vcnt_s8(int8x8_t a)                          | a->Vn,8B             | CNT Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| int8x16_t vcntq_s8(int8x16_t a)                       | a->Vn,16B            | CNT Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| uint8x8_t vcnt_u8(uint8x8_t a)                        | a->Vn,8B             | CNT Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| uint8x16_t vcntq_u8(uint8x16_t a)                     | a->Vn,16B            | CNT Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| poly8x8_t vcnt_p8(poly8x8_t a)                        | a->Vn,8B             | CNT Vd,8B,Vn,8B         | Vd,8B->result  | v7/A32/A64              |
| poly8x16_t vcntq_p8(poly8x16_t a)                     | a->Vn,16B            | CNT Vd,16B,Vn,16B       | Vd,16B->result | v7/A32/A64              |
| uint32x2_t vrecpe_u32(uint32x2_t a)                   | a->Vn,2S             | URECPE Vd,2S,Vn,2S      | Vd,2S->result  | v7/A32/A64              |
| uint32x4_t vrecpeq_u32(uint32x4_t a)                  | a->Vn,4S             | URECPE Vd,4S,Vn,4S      | Vd,4S->result  | v7/A32/A64              |
| float32x2_t vrecpe_f32(float32x2_t a)                 | a->Vn,2S             | RECPE Vd,2S,Vn,2S       | Vd,2S->result  | v7/A32/A64              |
| float32x4_t vrecpeq_f32(float32x4_t a)                | a->Vn,4S             | RECPE Vd,4S,Vn,4S       | Vd,4S->result  | v7/A32/A64              |
| float64x1_t vrecpe_f64(float64x1_t a)                 | a->Dn                | RECPE Dd,Dn             | Dd->result     | A64                     |
| float64x2_t vrecpeq_f64(float64x2_t a)                | a->Vn,2D             | RECPE Vd,2D,Vn,2D       | Vd,2D->result  | A64                     |
| float32_t vrecpes_f32(float32_t a)                    | a->Sn                | RECPE Sd,Sn             | Sd->result     | A64                     |
| float64_t vrecped_f64(float64_t a)                    | a->Dn                | RECPE Dd,Dn             | Dd->result     | A64                     |
| float32x2_t vrecps_f32(float32x2_t a, float32x2_t b)  | a->Vn,2S<br>b->Vn,2S | RECPS Vd,2S,Vn,2S,Vm,2S | Vd,2S->result  | v7/A32/A64              |
| float32x4_t vrecpsq_f32(float32x4_t a, float32x4_t b) | a->Vn,4S<br>b->Vn,4S | RECPS Vd,4S,Vn,4S,Vm,4S | Vd,4S->result  | v7/A32/A64              |
| float64x1_t vrecps_f64(float64x1_t a, float64x1_t b)  | a->Dn<br>b->Dm       | RECPS Dd,Dn,Dm          | Dd->result     | A64                     |
| float64x2_t vrecpsq_f64(float64x2_t a, float64x2_t b) | a->Vn,2D<br>b->Vn,2D | RECPS Vd,2D,Vn,2D,Vm,2D | Vd,2D->result  | A64                     |

| Intrinsic                                              | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|--------------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| float32_t vrecps_f32(float32_t a, float32_t b)         | a -> Sn<br>b -> Sm         | FRECPS Sd,Sn,Sm            | Sd -> result     | A64                     |
| float64_t vrecpsd_f64(float64_t a, float64_t b)        | a -> Dm<br>b -> Dm         | FRECPS Dd,Dn,Dm            | Dd -> result     | A64                     |
| float32x2_t vqrst_f32(float32x2_t a)                   | a -> Vn,2S                 | FSQRT Vd,2S,Vn,2S          | Vd,2S -> result  | A64                     |
| float32x4_t vqrstq_f32(float32x4_t a)                  | a -> Vn,4S                 | FSQRT Vd,4S,Vn,4S          | Vd,4S -> result  | A64                     |
| float64x1_t vqrst_f64(float64x1_t a)                   | a -> Dm                    | FSQRT Dd,Dm                | Dd -> result     | A64                     |
| float64x2_t vqrstq_f64(float64x2_t a)                  | a -> Vn,2D                 | FSQRT Vd,2D,Vn,2D          | Vd,2D -> result  | A64                     |
| uint32x2_t vrsqrte_u32(uint32x2_t a)                   | a -> Vn,2S                 | URSQ RTE Vd,2S,Vn,2S       | Vd,2S -> result  | V7/A32/A64              |
| uint32x4_t vrsqrteq_u32(uint32x4_t a)                  | a -> Vn,4S                 | URSQ RTE Vd,4S,Vn,4S       | Vd,4S -> result  | V7/A32/A64              |
| float32x2_t vrsqrte_f32(float32x2_t a)                 | a -> Vn,2S                 | FRSQ RTE Vd,2S,Vn,2S       | Vd,2S -> result  | V7/A32/A64              |
| float32x4_t vrsqrteq_f32(float32x4_t a)                | a -> Vn,4S                 | FRSQ RTE Vd,4S,Vn,4S       | Vd,4S -> result  | V7/A32/A64              |
| float64x1_t vrsqrte_f64(float64x1_t a)                 | a -> Dn                    | FRSQ RTE Dd,Dn             | Dd -> result     | A64                     |
| float64x2_t vrsqrteq_f64(float64x2_t a)                | a -> Vn,2D                 | FRSQ RTE Vd,2D,Vn,2D       | Vd,2D -> result  | A64                     |
| float32x2_t vrsqrtes_f32(float32x2_t a)                | a -> Vn,2S                 | FRSQ RTE S4,Sn             | S4 -> result     | A64                     |
| float64x2_t vrsqrtesq_f64(float64x2_t a)               | a -> Vn,2D                 | FRSQ RTE Dd,Dn             | Dd -> result     | A64                     |
| float32x2_t vrsqrts_f32(float32x2_t a, float32x2_t b)  | a -> Vn,2S<br>b -> Vm,2S   | FRSQ RTS Vd,2S,Vn,2S,Vm,2S | Vd,2S -> result  | V7/A32/A64              |
| float32x4_t vrsqrtsq_f32(float32x4_t a, float32x4_t b) | a -> Vn,4S<br>b -> Vm,4S   | FRSQ RTS Vd,4S,Vn,4S,Vm,4S | Vd,4S -> result  | V7/A32/A64              |
| float64x1_t vrsqrts_f64(float64x1_t a, float64x1_t b)  | a -> Dn<br>b -> Dm         | FRSQ RTS Dd,Dn,Dm          | Dd -> result     | A64                     |
| float64x2_t vrsqrtsq_f64(float64x2_t a, float64x2_t b) | a -> Vn,2D<br>b -> Vm,2D   | FRSQ RTS Vd,2D,Vn,2D,Vm,2D | Vd,2D -> result  | A64                     |
| float32_t vrsqrtsf_f32(float32_t a, float32_t b)       | a -> Sn<br>b -> Sm         | FRSQ RTS Sd,Sn,Sm          | Sd -> result     | A64                     |
| float64_t vrsqrtsdf_f64(float64_t a, float64_t b)      | a -> Dm<br>b -> Dm         | FRSQ RTS Dd,Dn,Dm          | Dd -> result     | A64                     |
| int8x8_t vmnq_s8(int8x8_t a)                           | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| int8x16_t vmnq1_s8(int8x16_t a)                        | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| int16x4_t vmnq_s16(int16x4_t a)                        | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| int16x8_t vmnq1_s16(int16x8_t a)                       | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| int32x2_t vmnq_s32(int32x2_t a)                        | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| int32x4_t vmnq1_s32(int32x4_t a)                       | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| uint8x8_t vmnq_u8(uint8x8_t a)                         | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| uint8x16_t vmnq1_u8(uint8x16_t a)                      | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| uint16x4_t vmnq_u16(uint16x4_t a)                      | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| uint16x8_t vmnq1_u16(uint16x8_t a)                     | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| uint32x2_t vmnq_u32(uint32x2_t a)                      | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| uint32x4_t vmnq1_u32(uint32x4_t a)                     | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| poly8x8_t vmnq_poly8x8_t a                             | a -> Vn,8B                 | MVN Vd,8B,Vn,8B            | Vd,8B -> result  | V7/A32/A64              |
| poly8x16_t vmnq1_poly8x16_t a                          | a -> Vn,16B                | MVN Vd,16B,Vn,16B          | Vd,16B -> result | V7/A32/A64              |
| int8x8_t vand_s8(int8x8_t a, int8x8_t b)               | a -> Vn,8B<br>b -> Vm,8B   | AND Vd,8B,Vn,8B,Vm,8B      | Vd,8B -> result  | V7/A32/A64              |
| int8x16_t vandq_s8(int8x16_t a, int8x16_t b)           | a -> Vn,16B<br>b -> Vm,16B | AND Vd,16B,Vn,16B,Vm,16B   | Vd,16B -> result | V7/A32/A64              |
| int16x4_t vand_s16(int16x4_t a, int16x4_t b)           | a -> Vn,8B<br>b -> Vm,8B   | AND Vd,8B,Vn,8B,Vm,8B      | Vd,8B -> result  | V7/A32/A64              |
| int16x8_t vandq_s16(int16x8_t a, int16x8_t b)          | a -> Vn,16B<br>b -> Vm,16B | AND Vd,16B,Vn,16B,Vm,16B   | Vd,16B -> result | V7/A32/A64              |
| int32x2_t vand_s32(int32x2_t a, int32x2_t b)           | a -> Vn,8B<br>b -> Vm,8B   | AND Vd,8B,Vn,8B,Vm,8B      | Vd,8B -> result  | V7/A32/A64              |
| int32x4_t vandq_s32(int32x4_t a, int32x4_t b)          | a -> Vn,16B<br>b -> Vm,16B | AND Vd,16B,Vn,16B,Vm,16B   | Vd,16B -> result | V7/A32/A64              |
| int64x1_t vand_s64(int64x1_t a, int64x1_t b)           | a -> Dm<br>b -> Dm         | AND Dd,Dn,Dm               | Dd -> result     | V7/A32/A64              |
| int64x2_t vandq_s64(int64x2_t a, int64x2_t b)          | a -> Vn,16B<br>b -> Vm,16B | AND Vd,16B,Vn,16B,Vm,16B   | Vd,16B -> result | V7/A32/A64              |
| uint8x8_t vand_u8(uint8x8_t a, uint8x8_t b)            | a -> Vn,8B<br>b -> Vm,8B   | AND Vd,8B,Vn,8B,Vm,8B      | Vd,8B -> result  | V7/A32/A64              |
| uint8x16_t vandq_u8(uint8x16_t a, uint8x16_t b)        | a -> Vn,16B<br>b -> Vm,16B | AND Vd,16B,Vn,16B,Vm,16B   | Vd,16B -> result | V7/A32/A64              |
| uint16x4_t vand_u16(uint16x4_t a, uint16x4_t b)        | a -> Vn,8B<br>b -> Vm,8B   | AND Vd,8B,Vn,8B,Vm,8B      | Vd,8B -> result  | V7/A32/A64              |

| Intrinsic                                        | Argument Preparation       | Instruction              | Result           | Supported Architectures |
|--------------------------------------------------|----------------------------|--------------------------|------------------|-------------------------|
| uint16x8_t vandq_u16(uint16x8_t a, uint16x8_t b) | a -> Vn.16B<br>b -> Vm.16B | AND Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint32x2_t vand_u32(uint32x2_t a, uint32x2_t b)  | a -> Vn.8B<br>b -> Vm.8B   | AND Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint32x4_t vandq_u32(uint32x4_t a, uint32x4_t b) | a -> Vn.16B<br>b -> Vm.16B | AND Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t vandq_u64(uint64x1_t a, uint64x1_t b) | a -> Vn.8B<br>b -> Vm.8B   | AND Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint64x2_t vandq_u64(uint64x2_t a, uint64x2_t b) | a -> Vn.16B<br>b -> Vm.16B | AND Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int8x8_t vorr_s8(int8x8_t a, int8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vorrq_s8(int8x16_t a, int8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vorr_s16(int16x4_t a, int16x4_t b)     | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int16x8_t vorrq_s16(int16x8_t a, int16x8_t b)    | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int32x2_t vorr_s32(int32x2_t a, int32x2_t b)     | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int32x4_t vorrq_s32(int32x4_t a, int32x4_t b)    | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int64x1_t vorr_s64(int64x1_t a, int64x1_t b)     | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int64x2_t vorrq_s64(int64x2_t a, int64x2_t b)    | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint8x8_t vorr_u8(uint8x8_t a, uint8x8_t b)      | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vorrq_u8(uint8x16_t a, uint8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vorr_u16(uint16x4_t a, uint16x4_t b)  | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x8_t vorrq_u16(uint16x8_t a, uint16x8_t b) | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint32x2_t vorr_u32(uint32x2_t a, uint32x2_t b)  | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint32x4_t vorrq_u32(uint32x4_t a, uint32x4_t b) | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t vorr_u64(uint64x1_t a, uint64x1_t b)  | a -> Vn.8B<br>b -> Vm.8B   | ORR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint64x2_t vorrq_u64(uint64x2_t a, uint64x2_t b) | a -> Vn.16B<br>b -> Vm.16B | ORR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int8x8_t veor_s8(int8x8_t a, int8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t veorq_s8(int8x16_t a, int8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t veor_s16(int16x4_t a, int16x4_t b)     | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int16x8_t veorq_s16(int16x8_t a, int16x8_t b)    | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int32x2_t veor_s32(int32x2_t a, int32x2_t b)     | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int32x4_t veorq_s32(int32x4_t a, int32x4_t b)    | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int64x1_t veor_s64(int64x1_t a, int64x1_t b)     | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int64x2_t veorq_s64(int64x2_t a, int64x2_t b)    | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint8x8_t veor_u8(uint8x8_t a, uint8x8_t b)      | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t veorq_u8(uint8x16_t a, uint8x16_t b)  | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t veor_u16(uint16x4_t a, uint16x4_t b)  | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x8_t veorq_u16(uint16x8_t a, uint16x8_t b) | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint32x2_t veor_u32(uint32x2_t a, uint32x2_t b)  | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint32x4_t veorq_u32(uint32x4_t a, uint32x4_t b) | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t veor_u64(uint64x1_t a, uint64x1_t b)  | a -> Vn.8B<br>b -> Vm.8B   | EOR Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint64x2_t veorq_u64(uint64x2_t a, uint64x2_t b) | a -> Vn.16B<br>b -> Vm.16B | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |

| Intrinsic                                                  | Argument Preparation                      | Instruction              | Result           | Supported Architectures |
|------------------------------------------------------------|-------------------------------------------|--------------------------|------------------|-------------------------|
| uint64x2_t veorq_u64(uint64x2_t a, uint64x2_t b)           | a -> Vn.16B<br>b -> Vm.16B                | EOR Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int8x8_t v bic_s8(int8x8_t a, int8x8_t b)                  | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t v bicq_s8(int8x16_t a, int8x16_t b)              | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t v bic_s16(int16x4_t a, int16x4_t b)              | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int16x8_t v bicq_s16(int16x8_t a, int16x8_t b)             | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int32x2_t v bic_s32(int32x2_t a, int32x2_t b)              | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int32x4_t v bicq_s32(int32x4_t a, int32x4_t b)             | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int64x1_t v bic_s64(int64x1_t a, int64x1_t b)              | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int64x2_t v bicq_s64(int64x2_t a, int64x2_t b)             | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint8x8_t v bic_u8(uint8x8_t a, uint8x8_t b)               | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t v bicq_u8(uint8x16_t a, uint8x16_t b)           | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t v bic_u16(uint16x4_t a, uint16x4_t b)           | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x8_t v bicq_u16(uint16x8_t a, uint16x8_t b)          | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint32x2_t v bic_u32(uint32x2_t a, uint32x2_t b)           | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint32x4_t v bicq_u32(uint32x4_t a, uint32x4_t b)          | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t v bic_u64(uint64x1_t a, uint64x1_t b)           | a -> Vn.8B<br>b -> Vm.8B                  | BIC Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint64x2_t v bicq_u64(uint64x2_t a, uint64x2_t b)          | a -> Vn.16B<br>b -> Vm.16B                | BIC Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int8x8_t vorn_s8(int8x8_t a, int8x8_t b)                   | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vornq_s8(int8x16_t a, int8x16_t b)               | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vorn_s16(int16x4_t a, int16x4_t b)               | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int16x8_t vornq_s16(int16x8_t a, int16x8_t b)              | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int32x2_t vorn_s32(int32x2_t a, int32x2_t b)               | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int32x4_t vornq_s32(int32x4_t a, int32x4_t b)              | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int64x1_t vorn_s64(int64x1_t a, int64x1_t b)               | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int64x2_t vornq_s64(int64x2_t a, int64x2_t b)              | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint8x8_t vorn_u8(uint8x8_t a, uint8x8_t b)                | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vornq_u8(uint8x16_t a, uint8x16_t b)            | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vorn_u16(uint16x4_t a, uint16x4_t b)            | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x8_t vornq_u16(uint16x8_t a, uint16x8_t b)           | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint32x2_t vorn_u32(uint32x2_t a, uint32x2_t b)            | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint32x4_t vornq_u32(uint32x4_t a, uint32x4_t b)           | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t vorn_u64(uint64x1_t a, uint64x1_t b)            | a -> Vn.8B<br>b -> Vm.8B                  | ORN Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint64x2_t vornq_u64(uint64x2_t a, uint64x2_t b)           | a -> Vn.16B<br>b -> Vm.16B                | ORN Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int8x8_t vbsl_s8(uint8x8_t a, int8x8_t b, int8x8_t c)      | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vbslq_s8(uint8x16_t a, int8x16_t b, int8x16_t c) | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |

| Intrinsic                                                         | Argument Preparation                      | Instruction              | Result           | Supported Architectures |
|-------------------------------------------------------------------|-------------------------------------------|--------------------------|------------------|-------------------------|
| int16x4_t vbsl_s16(uint16x4_t a, int16x4_t b, int16x4_t c)        | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int16x8_t vbslq_s16(uint16x8_t a, int16x8_t b, int16x8_t c)       | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int32x2_t vbsl_s32(uint32x2_t a, int32x2_t b, int32x2_t c)        | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int32x4_t vbslq_s32(uint32x4_t a, int32x4_t b, int32x4_t c)       | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| int64x1_t vbsl_s64(uint64x1_t a, int64x1_t b, int64x1_t c)        | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int64x2_t vbslq_s64(uint64x2_t a, int64x2_t b, int64x2_t c)       | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint8x8_t vbsl_u8(uint8x8_t a, uint8x8_t b, uint8x8_t c)          | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vbslq_u8(uint8x16_t a, uint8x16_t b, uint8x16_t c)     | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vbsl_u16(uint16x4_t a, uint16x4_t b, uint16x4_t c)     | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x8_t vbslq_u16(uint16x8_t a, uint16x8_t b, uint16x8_t c)    | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint32x2_t vbsl_u32(uint32x2_t a, uint32x2_t b, uint32x2_t c)     | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint32x4_t vbslq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)    | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| uint64x1_t vbsl_u64(uint64x1_t a, uint64x1_t b, uint64x1_t c)     | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint64x2_t vbslq_u64(uint64x2_t a, uint64x2_t b, uint64x2_t c)    | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| poly64x1_t vbsl_p64(poly64x1_t a, poly64x1_t b, poly64x1_t c)     | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A32/A64                 |
| poly64x2_t vbslq_p64(poly64x2_t a, poly64x2_t b, poly64x2_t c)    | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A32/A64                 |
| float32x2_t vbsl_f32(uint32x2_t a, float32x2_t b, float32x2_t c)  | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| float32x4_t vbslq_f32(uint32x4_t a, float32x4_t b, float32x4_t c) | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| poly8x8_t vbsl_p8(uint8x8_t a, poly8x8_t b, poly8x8_t c)          | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vbslq_p8(uint8x16_t a, poly8x16_t b, poly8x16_t c)     | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vbsl_p16(uint16x4_t a, poly16x4_t b, poly16x4_t c)     | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| poly16x8_t vbslq_p16(uint16x8_t a, poly16x8_t b, poly16x8_t c)    | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | v7/A32/A64              |
| float64x1_t vbsl_f64(uint64x1_t a, float64x1_t b, float64x1_t c)  | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B    | BSL Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| float64x2_t vbslq_f64(uint64x2_t a, float64x2_t b, float64x2_t c) | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B | BSL Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |

| Intrinsic                                                                               | Argument Preparation                                                     | Instruction                     | Result           | Supported Architectures |
|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------------|---------------------------------|------------------|-------------------------|
| int8x8_1 vcopy_lane_s8(int8x8_1 a, const int lane1, int8x8_1 b, const int lane2)        | a -> Vd.BB<br>0 -> lane 1<br><- 7<br>b -> Vn.BB<br>0 -> lane 2<br><- 7   | INS Vd.B[ lane1 ] Vn.B[ lane2 ] | Vd.BB -> result  | A64                     |
| int8x16_1 vcopy_lane_s8(int8x16_1 a, const int lane1, int8x8_1 b, const int lane2)      | a -> Vd16.B<br>0 -> lane 1<br><- 15<br>b -> Vn.BB<br>0 -> lane 2<br><- 7 | INS Vd.B[ lane1 ] Vn.B[ lane2 ] | Vd16.B -> result | A64                     |
| int16x4_1 vcopy_lane_s16(int16x4_1 a, const int lane1, int16x4_1 b, const int lane2)    | a -> Vd4H<br>0 -> lane 1<br><- 3<br>b -> Vn4H<br>0 -> lane 2<br><- 3     | INS Vd.H[ lane1 ] Vn.H[ lane2 ] | Vd4H -> result   | A64                     |
| int16x8_1 vcopy_lane_s16(int16x8_1 a, const int lane1, int16x8_1 b, const int lane2)    | a -> Vd8H<br>0 -> lane 1<br><- 7<br>b -> Vn4H<br>0 -> lane 2<br><- 3     | INS Vd.H[ lane1 ] Vn.H[ lane2 ] | Vd8H -> result   | A64                     |
| int32x2_1 vcopy_lane_s32(int32x2_1 a, const int lane1, int32x2_1 b, const int lane2)    | a -> Vd2S<br>0 -> lane 1<br><- 1<br>b -> Vn2S<br>0 -> lane 2<br><- 1     | INS Vd.S[ lane1 ] Vn.S[ lane2 ] | Vd2S -> result   | A64                     |
| int32x4_1 vcopy_lane_s32(int32x4_1 a, const int lane1, int32x2_1 b, const int lane2)    | a -> Vd4S<br>0 -> lane 1<br><- 3<br>b -> Vn2S<br>0 -> lane 2<br><- 1     | INS Vd.S[ lane1 ] Vn.S[ lane2 ] | Vd4S -> result   | A64                     |
| int64x1_1 vcopy_lane_s64(int64x1_1 a, const int lane1, int64x1_1 b, const int lane2)    | a -> UNUSED<br>lane1 -> 0<br>b -> Vn1D<br>lane2 -> 0                     | DUP Vd, Vn.D[ lane2 ]           | Dd -> result     | A64                     |
| int64x2_1 vcopy_lane_s64(int64x2_1 a, const int lane1, int64x1_1 b, const int lane2)    | a -> Vd2D<br>0 -> lane 1<br><- 1<br>b -> Vn1D<br>lane2 -> 0              | INS Vd.D[ lane1 ] Vn.D[ lane2 ] | Vd2D -> result   | A64                     |
| uint8x8_1 vcopy_lane_u8(uint8x8_1 a, const int lane1, uint8x8_1 b, const int lane2)     | a -> Vd.BB<br>0 -> lane 1<br><- 7<br>b -> Vn.BB<br>0 -> lane 2<br><- 7   | INS Vd.B[ lane1 ] Vn.B[ lane2 ] | Vd.BB -> result  | A64                     |
| uint8x16_1 vcopy_lane_u8(uint8x16_1 a, const int lane1, uint8x8_1 b, const int lane2)   | a -> Vd16.B<br>0 -> lane 1<br><- 15<br>b -> Vn.BB<br>0 -> lane 2<br><- 7 | INS Vd.B[ lane1 ] Vn.B[ lane2 ] | Vd16.B -> result | A64                     |
| uint16x4_1 vcopy_lane_u16(uint16x4_1 a, const int lane1, uint16x4_1 b, const int lane2) | a -> Vd4H<br>0 -> lane 1<br><- 3<br>b -> Vn4H<br>0 -> lane 2<br><- 3     | INS Vd.H[ lane1 ] Vn.H[ lane2 ] | Vd4H -> result   | A64                     |
| uint16x8_1 vcopy_lane_u16(uint16x8_1 a, const int lane1, uint16x4_1 b, const int lane2) | a -> Vd8H<br>0 -> lane 1<br><- 7<br>b -> Vn4H<br>0 -> lane 2<br><- 3     | INS Vd.H[ lane1 ] Vn.H[ lane2 ] | Vd8H -> result   | A64                     |

| Intrinsic                                                                                   | Argument Preparation                                               | Instruction                 | Result          | Supported Architectures |
|---------------------------------------------------------------------------------------------|--------------------------------------------------------------------|-----------------------------|-----------------|-------------------------|
| uint32x2_t vcopy_lane_u32(uint32x2_t a, const int lane1, uint32x2_t b, const int lane2)     | a->Vd,2S<br>0 <= lane1<br><= 1<br>b->Vn,2S<br>0 <= lane2<br><= 1   | INS Vd.S[lane1],Vn.S[lane2] | Vd.2S-> result  | A64                     |
| uint32x4_t vcopyq_lane_u32(uint32x4_t a, const int lane1, uint32x2_t b, const int lane2)    | a->Vd,4S<br>0 <= lane1<br><= 3<br>b->Vn,2S<br>0 <= lane2<br><= 1   | INS Vd.S[lane1],Vn.S[lane2] | Vd.4S-> result  | A64                     |
| uint64x1_t vcopy_lane_u64(uint64x1_t a, const int lane1, uint64x1_t b, const int lane2)     | a-><br>UNUSED<br>lane1 == 0<br>b->Vn,1D<br>lane2 == 0              | DUP Dd,Vn.D[lane2]          | Dd-> result     | A64                     |
| uint64x2_t vcopyq_lane_u64(uint64x2_t a, const int lane1, uint64x1_t b, const int lane2)    | a->Vd,2D<br>0 <= lane1<br><= 1<br>b->Vn,1D<br>lane2 == 0           | INS Vd.D[lane1],Vn.D[lane2] | Vd.2D-> result  | A64                     |
| poly64x1_t vcopy_lane_p64(poly64x1_t a, const int lane1, poly64x1_t b, const int lane2)     | a-><br>UNUSED<br>lane1 == 0<br>b->Vn,1D<br>lane2 == 0              | DUP Dd,Vn.D[lane2]          | Dd-> result     | A32/A64                 |
| poly64x2_t vcopyq_lane_p64(poly64x2_t a, const int lane1, poly64x1_t b, const int lane2)    | a->Vd,2D<br>0 <= lane1<br><= 1<br>b->Vn,1D<br>lane2 == 0           | INS Vd.D[lane1],Vn.D[lane2] | Vd.2D-> result  | A32/A64                 |
| float32x2_t vcopy_lane_f32(float32x2_t a, const int lane1, float32x2_t b, const int lane2)  | a->Vd,2S<br>0 <= lane1<br><= 1<br>b->Vn,2S<br>0 <= lane2<br><= 1   | INS Vd.S[lane1],Vn.S[lane2] | Vd.2S-> result  | A64                     |
| float32x4_t vcopyq_lane_f32(float32x4_t a, const int lane1, float32x2_t b, const int lane2) | a->Vd,4S<br>0 <= lane1<br><= 3<br>b->Vn,2S<br>0 <= lane2<br><= 1   | INS Vd.S[lane1],Vn.S[lane2] | Vd.4S-> result  | A64                     |
| float64x1_t vcopy_lane_f64(float64x1_t a, const int lane1, float64x1_t b, const int lane2)  | a-><br>UNUSED<br>lane1 == 0<br>b->Vn,1D<br>lane2 == 0              | DUP Dd,Vn.D[lane2]          | Dd-> result     | A64                     |
| float64x2_t vcopyq_lane_f64(float64x2_t a, const int lane1, float64x1_t b, const int lane2) | a->Vd,2D<br>0 <= lane1<br><= 1<br>b->Vn,1D<br>lane2 == 0           | INS Vd.D[lane1],Vn.D[lane2] | Vd.2D-> result  | A64                     |
| poly8x8_t vcopy_lane_p8(poly8x8_t a, const int lane1, poly8x8_t b, const int lane2)         | a->Vd,8B<br>0 <= lane1<br><= 7<br>b->Vn,8B<br>0 <= lane2<br><= 7   | INS Vd.B[lane1],Vn.B[lane2] | Vd.8B-> result  | A64                     |
| poly8x16_t vcopyq_lane_p8(poly8x16_t a, const int lane1, poly8x8_t b, const int lane2)      | a->Vd,16B<br>0 <= lane1<br><= 15<br>b->Vn,8B<br>0 <= lane2<br><= 7 | INS Vd.B[lane1],Vn.B[lane2] | Vd.16B-> result | A64                     |
| poly16x4_t vcopy_lane_p16(poly16x4_t a, const int lane1, poly16x4_t b, const int lane2)     | a->Vd,4H<br>0 <= lane1<br><= 3<br>b->Vn,4H<br>0 <= lane2<br><= 3   | INS Vd.H[lane1],Vn.H[lane2] | Vd.4H-> result  | A64                     |

| Intrinsic                                                                                 | Argument Preparation                                                     | Instruction                  | Result           | Supported Architectures |
|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|------------------------------|------------------|-------------------------|
| poly16x8_t vcopyq_lane_p16(poly16x8_t a, const int lane1, poly16x4_t b, const int lane2)  | a -> Vd.8H<br>0 <= lane1<br><= 7<br>b -> Vn.4H<br>0 <= lane2<br><= 3     | INS Vd.H[lane1], Vn.H[lane2] | Vd.8H -> result  | A64                     |
| int8x8_t vcopyq_laneq_s8(int8x8_t a, const int lane1, int8x16_t b, const int lane2)       | a -> Vd.8B<br>0 <= lane1<br><= 7<br>b -> Vn.16B<br>0 <= lane2<br><= 15   | INS Vd.B[lane1], Vn.B[lane2] | Vd.8B -> result  | A64                     |
| int8x16_t vcopyq_laneq_s8(int8x16_t a, const int lane1, int8x16_t b, const int lane2)     | a -> Vd.16B<br>0 <= lane1<br><= 15<br>b -> Vn.16B<br>0 <= lane2<br><= 15 | INS Vd.B[lane1], Vn.B[lane2] | Vd.16B -> result | A64                     |
| int16x4_t vcopyq_laneq_s16(int16x4_t a, const int lane1, int16x8_t b, const int lane2)    | a -> Vd.4H<br>0 <= lane1<br><= 3<br>b -> Vn.8H<br>0 <= lane2<br><= 7     | INS Vd.H[lane1], Vn.H[lane2] | Vd.4H -> result  | A64                     |
| int16x8_t vcopyq_laneq_s16(int16x8_t a, const int lane1, int16x8_t b, const int lane2)    | a -> Vd.8H<br>0 <= lane1<br><= 7<br>b -> Vn.8H<br>0 <= lane2<br><= 7     | INS Vd.H[lane1], Vn.H[lane2] | Vd.8H -> result  | A64                     |
| int32x2_t vcopyq_laneq_s32(int32x2_t a, const int lane1, int32x4_t b, const int lane2)    | a -> Vd.2S<br>0 <= lane1<br><= 1<br>b -> Vn.4S<br>0 <= lane2<br><= 3     | INS Vd.S[lane1], Vn.S[lane2] | Vd.2S -> result  | A64                     |
| int32x4_t vcopyq_laneq_s32(int32x4_t a, const int lane1, int32x4_t b, const int lane2)    | a -> Vd.4S<br>0 <= lane1<br><= 3<br>b -> Vn.4S<br>0 <= lane2<br><= 3     | INS Vd.S[lane1], Vn.S[lane2] | Vd.4S -> result  | A64                     |
| int64x1_t vcopyq_laneq_s64(int64x1_t a, const int lane1, int64x2_t b, const int lane2)    | a -> UNUSED<br>lane1 == 0<br>b -> Vn.2D<br>0 <= lane2<br><= 1            | DUP Dd, Vn.D[lane2]          | Dd -> result     | A64                     |
| int64x2_t vcopyq_laneq_s64(int64x2_t a, const int lane1, int64x2_t b, const int lane2)    | a -> Vd.2D<br>0 <= lane1<br><= 1<br>b -> Vn.2D<br>0 <= lane2<br><= 1     | INS Vd.D[lane1], Vn.D[lane2] | Vd.2D -> result  | A64                     |
| uint8x8_t vcopyq_laneq_u8(uint8x8_t a, const int lane1, uint8x16_t b, const int lane2)    | a -> Vd.8B<br>0 <= lane1<br><= 7<br>b -> Vn.16B<br>0 <= lane2<br><= 15   | INS Vd.B[lane1], Vn.B[lane2] | Vd.8B -> result  | A64                     |
| uint8x16_t vcopyq_laneq_u8(uint8x16_t a, const int lane1, uint8x16_t b, const int lane2)  | a -> Vd.16B<br>0 <= lane1<br><= 15<br>b -> Vn.16B<br>0 <= lane2<br><= 15 | INS Vd.B[lane1], Vn.B[lane2] | Vd.16B -> result | A64                     |
| uint16x4_t vcopyq_laneq_u16(uint16x4_t a, const int lane1, uint16x8_t b, const int lane2) | a -> Vd.4H<br>0 <= lane1<br><= 3<br>b -> Vn.8H<br>0 <= lane2<br><= 7     | INS Vd.H[lane1], Vn.H[lane2] | Vd.4H -> result  | A64                     |

| Intrinsic                                                                                    | Argument Preparation                                               | Instruction                 | Result         | Supported Architectures |
|----------------------------------------------------------------------------------------------|--------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| uint16x8_t vcopyq_laneq_u16(uint16x8_t a, const int lane1, uint16x8_t b, const int lane2)    | a->Vd.8H<br>0 <= lane1<br><= 7<br>b->Vn.8H<br>0 <= lane2<br><= 7   | INS Vd.H[lane1],Vn.H[lane2] | Vd.8H-> result | A64                     |
| uint32x2_t vcopyq_laneq_u32(uint32x2_t a, const int lane1, uint32x4_t b, const int lane2)    | a->Vd.2S<br>0 <= lane1<br><= 1<br>b->Vn.4S<br>0 <= lane2<br><= 3   | INS Vd.S[lane1],Vn.S[lane2] | Vd.2S-> result | A64                     |
| uint32x4_t vcopyq_laneq_u32(uint32x4_t a, const int lane1, uint32x4_t b, const int lane2)    | a->Vd.4S<br>0 <= lane1<br><= 3<br>b->Vn.4S<br>0 <= lane2<br><= 3   | INS Vd.S[lane1],Vn.S[lane2] | Vd.4S-> result | A64                     |
| uint64x1_t vcopyq_laneq_u64(uint64x1_t a, const int lane1, uint64x2_t b, const int lane2)    | a-><br>UNUSED<br>lane1 == 0<br>b->Vn.2D<br>0 <= lane2<br><= 1      | DUP Dd,Vn.D[lane2]          | Dd-> result    | A64                     |
| uint64x2_t vcopyq_laneq_u64(uint64x2_t a, const int lane1, uint64x2_t b, const int lane2)    | a->Vd.2D<br>0 <= lane1<br><= 1<br>b->Vn.2D<br>0 <= lane2<br><= 1   | INS Vd.D[lane1],Vn.D[lane2] | Vd.2D-> result | A64                     |
| poly64x1_t vcopyq_laneq_p64(poly64x1_t a, const int lane1, poly64x2_t b, const int lane2)    | a-><br>UNUSED<br>lane1 == 0<br>b->Vn.2D<br>0 <= lane2<br><= 1      | DUP Dd,Vn.D[lane2]          | Dd-> result    | A32/A64                 |
| poly64x2_t vcopyq_laneq_p64(poly64x2_t a, const int lane1, poly64x2_t b, const int lane2)    | a->Vd.2D<br>0 <= lane1<br><= 1<br>b->Vn.2D<br>0 <= lane2<br><= 1   | INS Vd.D[lane1],Vn.D[lane2] | Vd.2D-> result | A32/A64                 |
| float32x2_t vcopyq_laneq_f32(float32x2_t a, const int lane1, float32x4_t b, const int lane2) | a->Vd.2S<br>0 <= lane1<br><= 1<br>b->Vn.4S<br>0 <= lane2<br><= 3   | INS Vd.S[lane1],Vn.S[lane2] | Vd.2S-> result | A64                     |
| float32x4_t vcopyq_laneq_f32(float32x4_t a, const int lane1, float32x4_t b, const int lane2) | a->Vd.4S<br>0 <= lane1<br><= 3<br>b->Vn.4S<br>0 <= lane2<br><= 3   | INS Vd.S[lane1],Vn.S[lane2] | Vd.4S-> result | A64                     |
| float64x1_t vcopyq_laneq_f64(float64x1_t a, const int lane1, float64x2_t b, const int lane2) | a-><br>UNUSED<br>lane1 == 0<br>b->Vn.2D<br>0 <= lane2<br><= 1      | DUP Dd,Vn.D[lane2]          | Dd-> result    | A64                     |
| float64x2_t vcopyq_laneq_f64(float64x2_t a, const int lane1, float64x2_t b, const int lane2) | a->Vd.2D<br>0 <= lane1<br><= 1<br>b->Vn.2D<br>0 <= lane2<br><= 1   | INS Vd.D[lane1],Vn.D[lane2] | Vd.2D-> result | A64                     |
| poly8x8_t vcopyq_laneq_p8(poly8x8_t a, const int lane1, poly8x16_t b, const int lane2)       | a->Vd.8B<br>0 <= lane1<br><= 7<br>b->Vn.16B<br>0 <= lane2<br><= 15 | INS Vd.B[lane1],Vn.B[lane2] | Vd.8B-> result | A64                     |

| Intrinsic                                                                                 | Argument Preparation                                                     | Instruction                  | Result           | Supported Architectures |
|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|------------------------------|------------------|-------------------------|
| poly8x16_t vcopyq_laneq_p8(poly8x16_t a, const int lane1, poly8x16_t b, const int lane2)  | a -> Vd.16B<br>0 <= lane1<br><= 15<br>b -> Vn.16B<br>0 <= lane2<br><= 15 | INS Vd.B[lane1], Vn.B[lane2] | Vd.16B -> result | A64                     |
| poly16x4_t vcopyq_laneq_p16(poly16x4_t a, const int lane1, poly16x4_t b, const int lane2) | a -> Vd.4H<br>0 <= lane1<br><= 3<br>b -> Vn.8H<br>0 <= lane2<br><= 7     | INS Vd.H[lane1], Vn.H[lane2] | Vd.4H -> result  | A64                     |
| poly16x8_t vcopyq_laneq_p16(poly16x8_t a, const int lane1, poly16x8_t b, const int lane2) | a -> Vd.8H<br>0 <= lane1<br><= 7<br>b -> Vn.8H<br>0 <= lane2<br><= 7     | INS Vd.H[lane1], Vn.H[lane2] | Vd.8H -> result  | A64                     |
| int8x8_t vrbit_s8(int8x8_t a)                                                             | a -> Vn.8B                                                               | RBIT Vd.8B, Vn.8B            | Vd.8B -> result  | A64                     |
| int8x16_t vrbitq_s8(int8x16_t a)                                                          | a -> Vn.16B                                                              | RBIT Vd.16B, Vn.16B          | Vd.16B -> result | A64                     |
| uint8x8_t vrbit_u8(uint8x8_t a)                                                           | a -> Vn.8B                                                               | RBIT Vd.8B, Vn.8B            | Vd.8B -> result  | A64                     |
| uint8x16_t vrbitq_u8(uint8x16_t a)                                                        | a -> Vn.16B                                                              | RBIT Vd.16B, Vn.16B          | Vd.16B -> result | A64                     |
| poly8x8_t vrbit_p8(poly8x8_t a)                                                           | a -> Vn.8B                                                               | RBIT Vd.8B, Vn.8B            | Vd.8B -> result  | A64                     |
| poly8x16_t vrbitq_p8(poly8x16_t a)                                                        | a -> Vn.16B                                                              | RBIT Vd.16B, Vn.16B          | Vd.16B -> result | A64                     |
| int8x8_t vcreate_s8(uint64_t a)                                                           | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.8B -> result  | v7/A32/A64              |
| int16x4_t vcreate_s16(uint64_t a)                                                         | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.4H -> result  | v7/A32/A64              |
| int32x2_t vcreate_s32(uint64_t a)                                                         | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.2S -> result  | v7/A32/A64              |
| int64x1_t vcreate_s64(uint64_t a)                                                         | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.1D -> result  | v7/A32/A64              |
| uint8x8_t vcreate_u8(uint64_t a)                                                          | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.8B -> result  | v7/A32/A64              |
| uint16x4_t vcreate_u16(uint64_t a)                                                        | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.4H -> result  | v7/A32/A64              |
| uint32x2_t vcreate_u32(uint64_t a)                                                        | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.2S -> result  | v7/A32/A64              |
| uint64x1_t vcreate_u64(uint64_t a)                                                        | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.1D -> result  | v7/A32/A64              |
| poly64x1_t vcreate_p64(uint64_t a)                                                        | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.1D -> result  | A32/A64                 |
| float16x4_t vcreate_f16(uint64_t a)                                                       | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.4H -> result  | v7/A32/A64              |
| float32x2_t vcreate_f32(uint64_t a)                                                       | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.2S -> result  | v7/A32/A64              |
| float64x1_t vcreate_f64(uint64_t a)                                                       | a -> Xn                                                                  | INS Vd.D[0], Xn              | Vd.1D -> result  | v7/A32/A64              |
| poly8x8_t vdupq_n_s8(int8_t value)                                                        | value -> rn                                                              | DUP Vd.8B, rn                | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vdupq_n_s8(int8_t value)                                                        | value -> rn                                                              | DUP Vd.16B, rn               | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vdupq_n_s16(int16_t value)                                                      | value -> rn                                                              | DUP Vd.4H, rn                | Vd.4H -> result  | v7/A32/A64              |
| int32x2_t vdupq_n_s32(int32_t value)                                                      | value -> rn                                                              | DUP Vd.2S, rn                | Vd.2S -> result  | v7/A32/A64              |
| int64x1_t vdupq_n_s64(int64_t value)                                                      | value -> rn                                                              | DUP Vd.1D, rn                | Vd.1D -> result  | v7/A32/A64              |
| uint8x8_t vdupq_n_u8(uint8_t value)                                                       | value -> rn                                                              | DUP Vd.8B, rn                | Vd.8B -> result  | v7/A32/A64              |
| uint16x4_t vdupq_n_u16(uint16_t value)                                                    | value -> rn                                                              | DUP Vd.4H, rn                | Vd.4H -> result  | v7/A32/A64              |
| uint32x2_t vdupq_n_u32(uint32_t value)                                                    | value -> rn                                                              | DUP Vd.2S, rn                | Vd.2S -> result  | v7/A32/A64              |
| uint64x1_t vdupq_n_u64(uint64_t value)                                                    | value -> rn                                                              | DUP Vd.1D, rn                | Vd.1D -> result  | v7/A32/A64              |
| poly64x1_t vdupq_n_p64(uint64_t value)                                                    | value -> rn                                                              | DUP Vd.D[0], rn              | Vd.1D -> result  | A32/A64                 |
| float16x4_t vdupq_n_f16(float32_t value)                                                  | value -> rn                                                              | DUP Vd.4H, rn                | Vd.4H -> result  | A32/A64                 |
| float32x2_t vdupq_n_f32(float32_t value)                                                  | value -> rn                                                              | DUP Vd.2S, rn                | Vd.2S -> result  | v7/A32/A64              |
| float64x2_t vdupq_n_f64(float64_t value)                                                  | value -> rn                                                              | DUP Vd.1D, rn                | Vd.1D -> result  | v7/A32/A64              |
| poly8x8_t vdupq_n_p8(poly8_t value)                                                       | value -> rn                                                              | DUP Vd.8B, rn                | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vdupq_n_p8(poly8_t value)                                                      | value -> rn                                                              | DUP Vd.16B, rn               | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vdupq_n_p16(poly16_t value)                                                    | value -> rn                                                              | DUP Vd.4H, rn                | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vdupq_n_p16(poly16_t value)                                                    | value -> rn                                                              | DUP Vd.8H, rn                | Vd.8H -> result  | v7/A32/A64              |
| float64x2_t vdupq_n_f64(float64_t value)                                                  | value -> rn                                                              | INS Dd.D[0], rn              | Vd.1D -> result  | A64                     |
| float64x2_t vdupq_n_f64(float64_t value)                                                  | value -> rn                                                              | DUP Vd.2D, rn                | Vd.2D -> result  | A64                     |
| int8x8_t vmov_n_s8(int8_t value)                                                          | value -> rn                                                              | DUP Vd.8B, rn                | Vd.8B -> result  | v7/A32/A64              |

| Intrinsic                                                 | Argument Preparation            | Instruction           | Result           | Supported Architectures |
|-----------------------------------------------------------|---------------------------------|-----------------------|------------------|-------------------------|
| int8x16_t vmovq_n_s8(int8_t value)                        | value -> rn                     | DUP Vd.16B,rn         | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vmovq_n_s16(int16_t value)                      | value -> rn                     | DUP Vd.4H,rn          | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vmovq_n_s16(int16_t value)                      | value -> rn                     | DUP Vd.8H,rn          | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vmovq_n_s32(int32_t value)                      | value -> rn                     | DUP Vd.2S,rn          | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vmovq_n_s32(int32_t value)                      | value -> rn                     | DUP Vd.4S,rn          | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vmovq_n_s64(int64_t value)                      | value -> rn                     | DUP Vd.1D,rn          | Vd.1D -> result  | v7/A32/A64              |
| int64x2_t vmovq_n_s64(int64_t value)                      | value -> rn                     | DUP Vd.2D,rn          | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vmovq_n_u8(uint8_t value)                       | value -> rn                     | DUP Vd.8B,rn          | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vmovq_n_u8(uint8_t value)                      | value -> rn                     | DUP Vd.16B,rn         | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vmovq_n_u16(uint16_t value)                    | value -> rn                     | DUP Vd.4H,rn          | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vmovq_n_u16(uint16_t value)                    | value -> rn                     | DUP Vd.8H,rn          | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vmovq_n_u32(uint32_t value)                    | value -> rn                     | DUP Vd.2S,rn          | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vmovq_n_u32(uint32_t value)                    | value -> rn                     | DUP Vd.4S,rn          | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vmovq_n_u64(uint64_t value)                    | value -> rn                     | DUP Vd.1D,rn          | Vd.1D -> result  | v7/A32/A64              |
| uint64x2_t vmovq_n_u64(uint64_t value)                    | value -> rn                     | DUP Vd.2D,rn          | Vd.2D -> result  | v7/A32/A64              |
| float32x2_t vmovq_n_f32(float32_t value)                  | value -> rn                     | DUP Vd.2S,rn          | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t vmovq_n_f32(float32_t value)                  | value -> rn                     | DUP Vd.4S,rn          | Vd.4S -> result  | v7/A32/A64              |
| poly8x8_t vmovq_n_p8(poly8_t value)                       | value -> rn                     | DUP Vd.8B,rn          | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vmovq_n_p8(poly8_t value)                      | value -> rn                     | DUP Vd.16B,rn         | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vmovq_n_p16(poly16_t value)                    | value -> rn                     | DUP Vd.4H,rn          | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vmovq_n_p16(poly16_t value)                    | value -> rn                     | DUP Vd.8H,rn          | Vd.8H -> result  | v7/A32/A64              |
| float64x1_t vmovq_n_f64(float64_t value)                  | value -> rn                     | DUP Vd.1D,rn          | Vd.1D -> result  | A64                     |
| float64x2_t vmovq_n_f64(float64_t value)                  | value -> rn                     | DUP Vd.2D,rn          | Vd.2D -> result  | A64                     |
| int8x8_t vdupq_lane_s8(int8x8_t vec, const int lane)      | vec -> Vn, BB<br>0 <= lane <= 7 | DUP Vd.8B,Vn,B[lane]  | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vdupq_lane_s8(int8x8_t vec, const int lane)     | vec -> Vn, BB<br>0 <= lane <= 7 | DUP Vd.16B,Vn,B[lane] | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vdupq_lane_s16(int16x4_t vec, const int lane)   | vec -> Vn,4H<br>0 <= lane <= 3  | DUP Vd.4H,Vn,H[lane]  | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vdupq_lane_s16(int16x4_t vec, const int lane)   | vec -> Vn,4H<br>0 <= lane <= 3  | DUP Vd.8H,Vn,H[lane]  | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vdupq_lane_s32(int32x2_t vec, const int lane)   | vec -> Vn,2S<br>0 <= lane <= 1  | DUP Vd.2S,Vn,S[lane]  | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vdupq_lane_s32(int32x2_t vec, const int lane)   | vec -> Vn,2S<br>0 <= lane <= 1  | DUP Vd.4S,Vn,S[lane]  | Vd.4S -> result  | v7/A32/A64              |
| int64x1_t vdupq_lane_s64(int64x1_t vec, const int lane)   | vec -> Vn,1D<br>lane == 0       | DUP Dd,Vn,D[lane]     | Dd -> result     | v7/A32/A64              |
| int64x2_t vdupq_lane_s64(int64x1_t vec, const int lane)   | vec -> Vn,1D<br>lane == 0       | DUP Vd.2D,Vn,D[lane]  | Vd.2D -> result  | v7/A32/A64              |
| uint8x8_t vdupq_lane_u8(uint8x8_t vec, const int lane)    | vec -> Vn,8B<br>0 <= lane <= 7  | DUP Vd.8B,Vn,B[lane]  | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vdupq_lane_u8(uint8x8_t vec, const int lane)   | vec -> Vn,8B<br>0 <= lane <= 7  | DUP Vd.16B,Vn,B[lane] | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vdupq_lane_u16(uint16x4_t vec, const int lane) | vec -> Vn,4H<br>0 <= lane <= 3  | DUP Vd.4H,Vn,H[lane]  | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vdupq_lane_u16(uint16x4_t vec, const int lane) | vec -> Vn,4H<br>0 <= lane <= 3  | DUP Vd.8H,Vn,H[lane]  | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vdupq_lane_u32(uint32x2_t vec, const int lane) | vec -> Vn,2S<br>0 <= lane <= 1  | DUP Vd.2S,Vn,S[lane]  | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vdupq_lane_u32(uint32x2_t vec, const int lane) | vec -> Vn,2S<br>0 <= lane <= 1  | DUP Vd.4S,Vn,S[lane]  | Vd.4S -> result  | v7/A32/A64              |
| uint64x1_t vdupq_lane_u64(uint64x1_t vec, const int lane) | vec -> Vn,1D<br>lane == 0       | DUP Dd,Vn,D[lane]     | Dd -> result     | v7/A32/A64              |
| uint64x2_t vdupq_lane_u64(uint64x1_t vec, const int lane) | vec -> Vn,1D<br>lane == 0       | DUP Vd.2D,Vn,D[lane]  | Vd.2D -> result  | v7/A32/A64              |
| poly8x4_t vdupq_lane_p8(poly8x4_t vec, const int lane)    | vec -> Vn,1D<br>lane == 0       | DUP Dd,Vn,D[lane]     | Dd -> result     | A32/A64                 |

| Intrinsic                                                   | Argument Preparation             | Instruction           | Result           | Supported Architectures |
|-------------------------------------------------------------|----------------------------------|-----------------------|------------------|-------------------------|
| poly64x2_t vdupq_lane_p64(poly64x1_t vec, const int lane)   | vec -> Vn.1D<br>lane == 0        | DUP Vd.2D,Vn.D[lane]  | Vd.2D -> result  | A32/A64                 |
| float32x2_t vdup_lane_f32(float32x2_t vec, const int lane)  | vec -> Vn.2S<br>0 <= lane <= 1   | DUP Vd.2S,Vn.S[lane]  | Vd.2S -> result  | v7/A32/A64              |
| float32x4_t vdupq_lane_f32(float32x2_t vec, const int lane) | vec -> Vn.2S<br>0 <= lane <= 1   | DUP Vd.4S,Vn.S[lane]  | Vd.4S -> result  | v7/A32/A64              |
| poly8x8_t vdup_lane_p8(poly8x8_t vec, const int lane)       | vec -> Vn.8B<br>0 <= lane <= 7   | DUP Vd.8B,Vn.B[lane]  | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vdupq_lane_p8(poly8x8_t vec, const int lane)     | vec -> Vn.8B<br>0 <= lane <= 7   | DUP Vd.16B,Vn.B[lane] | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vdup_lane_p16(poly16x4_t vec, const int lane)    | vec -> Vn.4H<br>0 <= lane <= 3   | DUP Vd.4H,Vn.H[lane]  | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vdupq_lane_p16(poly16x4_t vec, const int lane)   | vec -> Vn.4H<br>0 <= lane <= 3   | DUP Vd.8H,Vn.H[lane]  | Vd.8H -> result  | v7/A32/A64              |
| float64x1_t vdup_lane_f64(float64x1_t vec, const int lane)  | vec -> Vn.1D<br>lane == 0        | DUP Dd,Vn.D[lane]     | Dd -> result     | A64                     |
| float64x2_t vdupq_lane_f64(float64x1_t vec, const int lane) | vec -> Vn.1D<br>lane == 0        | DUP Vd.2D,Vn.D[lane]  | Vd.2D -> result  | A64                     |
| int8x8_t vdup_laneq_s8(int8x16_t vec, const int lane)       | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Vd.8B,Vn.B[lane]  | Vd.8B -> result  | A64                     |
| int8x16_t vdupq_laneq_s8(int8x16_t vec, const int lane)     | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Vd.16B,Vn.B[lane] | Vd.16B -> result | A64                     |
| int16x4_t vdup_laneq_s16(int16x8_t vec, const int lane)     | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Vd.4H,Vn.H[lane]  | Vd.4H -> result  | A64                     |
| int16x8_t vdupq_laneq_s16(int16x8_t vec, const int lane)    | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Vd.8H,Vn.H[lane]  | Vd.8H -> result  | A64                     |
| int32x2_t vdup_laneq_s32(int32x4_t vec, const int lane)     | vec -> Vn.4S<br>0 <= lane <= 3   | DUP Vd.2S,Vn.S[lane]  | Vd.2S -> result  | A64                     |
| int32x4_t vdupq_laneq_s32(int32x4_t vec, const int lane)    | vec -> Vn.4S<br>0 <= lane <= 3   | DUP Vd.4S,Vn.S[lane]  | Vd.4S -> result  | A64                     |
| int64x1_t vdup_laneq_s64(int64x2_t vec, const int lane)     | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Dd,Vn.D[lane]     | Dd -> result     | A64                     |
| int64x2_t vdupq_laneq_s64(int64x2_t vec, const int lane)    | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Vd.2D,Vn.D[lane]  | Vd.2D -> result  | A64                     |
| uint8x8_t vdup_laneq_u8(uint8x16_t vec, const int lane)     | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Vd.8B,Vn.B[lane]  | Vd.8B -> result  | A64                     |
| uint8x16_t vdupq_laneq_u8(uint8x16_t vec, const int lane)   | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Vd.16B,Vn.B[lane] | Vd.16B -> result | A64                     |
| uint16x4_t vdup_laneq_u16(uint16x8_t vec, const int lane)   | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Vd.4H,Vn.H[lane]  | Vd.4H -> result  | A64                     |
| uint16x8_t vdupq_laneq_u16(uint16x8_t vec, const int lane)  | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Vd.8H,Vn.H[lane]  | Vd.8H -> result  | A64                     |
| uint32x2_t vdup_laneq_u32(uint32x4_t vec, const int lane)   | vec -> Vn.4S<br>0 <= lane <= 3   | DUP Vd.2S,Vn.S[lane]  | Vd.2S -> result  | A64                     |
| uint32x4_t vdupq_laneq_u32(uint32x4_t vec, const int lane)  | vec -> Vn.4S<br>0 <= lane <= 3   | DUP Vd.4S,Vn.S[lane]  | Vd.4S -> result  | A64                     |
| uint64x1_t vdup_laneq_u64(uint64x2_t vec, const int lane)   | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Dd,Vn.D[lane]     | Dd -> result     | A64                     |

| Intrinsic                                                    | Argument Preparation             | Instruction                              | Result           | Supported Architectures |
|--------------------------------------------------------------|----------------------------------|------------------------------------------|------------------|-------------------------|
| uint64x2_t vdupq_laneq_u64(uint64x2_t vec, const int lane)   | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Vd.2D,Vn.D[lane]                     | Vd.2D -> result  | A64                     |
| poly64x1_t vdup_laneq_p64(poly64x2_t vec, const int lane)    | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Dd,Vn.D[lane]                        | Dd -> result     | A64                     |
| poly64x2_t vdupq_laneq_p64(poly64x2_t vec, const int lane)   | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Vd.2D,Vn.D[lane]                     | Vd.2D -> result  | A64                     |
| float32x2_t vdup_laneq_f32(float32x4_t vec, const int lane)  | vec -> Vn.4S<br>0 <= lane <= 3   | DUP Vd.2S,Vn.S[lane]                     | Vd.2S -> result  | A64                     |
| float32x4_t vdupq_laneq_f32(float32x4_t vec, const int lane) | vec -> Vn.4S<br>0 <= lane <= 3   | DUP Vd.4S,Vn.S[lane]                     | Vd.4S -> result  | A64                     |
| poly8x8_t vdup_laneq_p8(poly8x16_t vec, const int lane)      | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Vd.8B,Vn.B[lane]                     | Vd.8B -> result  | A64                     |
| poly8x16_t vdupq_laneq_p8(poly8x16_t vec, const int lane)    | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Vd.16B,Vn.B[lane]                    | Vd.16B -> result | A64                     |
| poly16x4_t vdup_laneq_p16(poly16x8_t vec, const int lane)    | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Vd.4H,Vn.H[lane]                     | Vd.4H -> result  | A64                     |
| poly16x8_t vdupq_laneq_p16(poly16x8_t vec, const int lane)   | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Vd.8H,Vn.H[lane]                     | Vd.8H -> result  | A64                     |
| float64x1_t vdup_laneq_f64(float64x2_t vec, const int lane)  | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Dd,Vn.D[lane]                        | Dd -> result     | A64                     |
| float64x2_t vdupq_laneq_f64(float64x2_t vec, const int lane) | vec -> Vn.2D<br>0 <= lane <= 1   | DUP Vd.2D,Vn.D[lane]                     | Vd.2D -> result  | A64                     |
| int8x16_t vcombine_s8(int8x8_t low, int8x8_t high)           | low -> Vn.8B<br>high -> Vm.8B    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.16B -> result | v7/A32/A64              |
| int16x8_t vcombine_s16(int16x4_t low, int16x4_t high)        | low -> Vn.4H<br>high -> Vm.4H    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vcombine_s32(int32x2_t low, int32x2_t high)        | low -> Vn.2S<br>high -> Vm.2S    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vcombine_s64(int64x1_t low, int64x1_t high)        | low -> Vn.1D<br>high -> Vm.1D    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.2D -> result  | v7/A32/A64              |
| uint8x16_t vcombine_u8(uint8x8_t low, uint8x8_t high)        | low -> Vn.8B<br>high -> Vm.8B    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.16B -> result | v7/A32/A64              |
| uint16x8_t vcombine_u16(uint16x4_t low, uint16x4_t high)     | low -> Vn.4H<br>high -> Vm.4H    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vcombine_u32(uint32x2_t low, uint32x2_t high)     | low -> Vn.2S<br>high -> Vm.2S    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vcombine_u64(uint64x1_t low, uint64x1_t high)     | low -> Vn.1D<br>high -> Vm.1D    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.2D -> result  | v7/A32/A64              |
| poly64x2_t vcombine_p64(poly64x1_t low, poly64x1_t high)     | low -> Vn.1D<br>high -> Vm.1D    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.2D -> result  | A32/A64                 |
| float16x8_t vcombine_f16(float16x4_t low, float16x4_t high)  | low -> Vn.4H<br>high -> Vm.4H    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.8H -> result  | v7/A32/A64              |
| float32x4_t vcombine_f32(float32x2_t low, float32x2_t high)  | low -> Vn.2S<br>high -> Vm.2S    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.4S -> result  | v7/A32/A64              |
| poly8x16_t vcombine_p8(poly8x8_t low, poly8x8_t high)        | low -> Vn.8B<br>high -> Vm.8B    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.16B -> result | v7/A32/A64              |
| poly16x8_t vcombine_p16(poly16x4_t low, poly16x4_t high)     | low -> Vn.4H<br>high -> Vm.4H    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.8H -> result  | v7/A32/A64              |

| Intrinsic                                                   | Argument Preparation             | Instruction                              | Result          | Supported Architectures |
|-------------------------------------------------------------|----------------------------------|------------------------------------------|-----------------|-------------------------|
| float64x2_t vcombine_f64(float64x1_t low, float64x1_t high) | low -> Vn.1D<br>high -> Vm.1D    | DUP Vd.1D,Vn.D[0]<br>INS Vd.D[1],Vm.D[0] | Vd.2D -> result | A64                     |
| int8x8_t vget_high_s8(int8x16_t a)                          | a -> Vn.16B                      | DUP Vd.1D,Vn.D[1]                        | Vd.8B -> result | v7/A32/A64              |
| int16x4_t vget_high_s16(int16x8_t a)                        | a -> Vn.8H                       | DUP Vd.1D,Vn.D[1]                        | Vd.4H -> result | v7/A32/A64              |
| int32x2_t vget_high_s32(int32x4_t a)                        | a -> Vn.4S                       | DUP Vd.1D,Vn.D[1]                        | Vd.2S -> result | v7/A32/A64              |
| int64x1_t vget_high_s64(int64x2_t a)                        | a -> Vn.2D                       | DUP Vd.1D,Vn.D[1]                        | Vd.1D -> result | v7/A32/A64              |
| uint8x8_t vget_high_u8(uint8x16_t a)                        | a -> Vn.16B                      | DUP Vd.1D,Vn.D[1]                        | Vd.8B -> result | v7/A32/A64              |
| uint16x4_t vget_high_u16(uint16x8_t a)                      | a -> Vn.8H                       | DUP Vd.1D,Vn.D[1]                        | Vd.4H -> result | v7/A32/A64              |
| uint32x2_t vget_high_u32(uint32x4_t a)                      | a -> Vn.4S                       | DUP Vd.1D,Vn.D[1]                        | Vd.2S -> result | v7/A32/A64              |
| uint64x1_t vget_high_u64(uint64x2_t a)                      | a -> Vn.2D                       | DUP Vd.1D,Vn.D[1]                        | Vd.1D -> result | v7/A32/A64              |
| poly64x1_t vget_high_p64(poly64x2_t a)                      | a -> Vn.2D                       | DUP Vd.1D,Vn.D[1]                        | Vd.1D -> result | A32/A64                 |
| float16x4_t vget_high_f16(float16x8_t a)                    | a -> Vn.8H                       | DUP Vd.1D,Vn.D[1]                        | Vd.4H -> result | v7/A32/A64              |
| float32x2_t vget_high_f32(float32x4_t a)                    | a -> Vn.4S                       | DUP Vd.1D,Vn.D[1]                        | Vd.2S -> result | v7/A32/A64              |
| poly8x8_t vget_high_p8(poly8x16_t a)                        | a -> Vn.16B                      | DUP Vd.1D,Vn.D[1]                        | Vd.8B -> result | v7/A32/A64              |
| poly16x4_t vget_high_p16(poly16x8_t a)                      | a -> Vn.8H                       | DUP Vd.1D,Vn.D[1]                        | Vd.4H -> result | v7/A32/A64              |
| float64x1_t vget_high_f64(float64x2_t a)                    | a -> Vn.2D                       | DUP Vd.1D,Vn.D[1]                        | Vd.1D -> result | A64                     |
| int8x8_t vget_low_s8(int8x16_t a)                           | a -> Vn.16B                      | DUP Vd.1D,Vn.D[0]                        | Vd.8B -> result | v7/A32/A64              |
| int16x4_t vget_low_s16(int16x8_t a)                         | a -> Vn.8H                       | DUP Vd.1D,Vn.D[0]                        | Vd.4H -> result | v7/A32/A64              |
| int32x2_t vget_low_s32(int32x4_t a)                         | a -> Vn.4S                       | DUP Vd.1D,Vn.D[0]                        | Vd.2S -> result | v7/A32/A64              |
| int64x1_t vget_low_s64(int64x2_t a)                         | a -> Vn.2D                       | DUP Vd.1D,Vn.D[0]                        | Vd.1D -> result | v7/A32/A64              |
| uint8x8_t vget_low_u8(uint8x16_t a)                         | a -> Vn.16B                      | DUP Vd.1D,Vn.D[0]                        | Vd.8B -> result | v7/A32/A64              |
| uint16x4_t vget_low_u16(uint16x8_t a)                       | a -> Vn.8H                       | DUP Vd.1D,Vn.D[0]                        | Vd.4H -> result | v7/A32/A64              |
| uint32x2_t vget_low_u32(uint32x4_t a)                       | a -> Vn.4S                       | DUP Vd.1D,Vn.D[0]                        | Vd.2S -> result | v7/A32/A64              |
| uint64x1_t vget_low_u64(uint64x2_t a)                       | a -> Vn.2D                       | DUP Vd.1D,Vn.D[0]                        | Vd.1D -> result | v7/A32/A64              |
| poly64x1_t vget_low_p64(poly64x2_t a)                       | a -> Vn.2D                       | DUP Vd.1D,Vn.D[0]                        | Vd.1D -> result | A32/A64                 |
| float16x4_t vget_low_f16(float16x8_t a)                     | a -> Vn.8H                       | DUP Vd.1D,Vn.D[0]                        | Vd.4H -> result | v7/A32/A64              |
| float32x2_t vget_low_f32(float32x4_t a)                     | a -> Vn.4S                       | DUP Vd.1D,Vn.D[0]                        | Vd.2S -> result | v7/A32/A64              |
| poly8x8_t vget_low_p8(poly8x16_t a)                         | a -> Vn.16B                      | DUP Vd.1D,Vn.D[0]                        | Vd.8B -> result | v7/A32/A64              |
| poly16x4_t vget_low_p16(poly16x8_t a)                       | a -> Vn.8H                       | DUP Vd.1D,Vn.D[0]                        | Vd.4H -> result | v7/A32/A64              |
| float64x1_t vget_low_f64(float64x2_t a)                     | a -> Vn.2D                       | DUP Vd.1D,Vn.D[0]                        | Vd.1D -> result | A64                     |
| int8_t vdupb_lane_s8(int8x8_t vec, const int lane)          | vec -> Vn.8B<br>0 <= lane <= 7   | DUP Bd,Vn.B[lane]                        | Bd -> result    | A64                     |
| int16_t vduph_lane_s16(int16x4_t vec, const int lane)       | vec -> Vn.4H<br>0 <= lane <= 3   | DUP Hd,Vn.H[lane]                        | Hd -> result    | A64                     |
| int32_t vdup_s_lane_s32(int32x2_t vec, const int lane)      | vec -> Vn.2S<br>0 <= lane <= 1   | DUP Sd,Vn.S[lane]                        | Sd -> result    | A64                     |
| int64_t vdupd_lane_s64(int64x1_t vec, const int lane)       | vec -> Vn.1D<br>lane == 0        | DUP Dd,Vn.D[lane]                        | Dd -> result    | A64                     |
| uint8_t vdupb_lane_u8(uint8x8_t vec, const int lane)        | vec -> Vn.8B<br>0 <= lane <= 7   | DUP Bd,Vn.B[lane]                        | Bd -> result    | A64                     |
| uint16_t vduph_lane_u16(uint16x4_t vec, const int lane)     | vec -> Vn.4H<br>0 <= lane <= 3   | DUP Hd,Vn.H[lane]                        | Hd -> result    | A64                     |
| uint32_t vdup_s_lane_u32(uint32x2_t vec, const int lane)    | vec -> Vn.2S<br>0 <= lane <= 1   | DUP Sd,Vn.S[lane]                        | Sd -> result    | A64                     |
| uint64_t vdupd_lane_u64(uint64x1_t vec, const int lane)     | vec -> Vn.1D<br>lane == 0        | DUP Dd,Vn.D[lane]                        | Dd -> result    | A64                     |
| float32_t vdup_lane_f32(float32x2_t vec, const int lane)    | vec -> Vn.2S<br>0 <= lane <= 1   | DUP Sd,Vn.S[lane]                        | Sd -> result    | A64                     |
| float64_t vdup_lane_f64(float64x1_t vec, const int lane)    | vec -> Vn.1D<br>lane == 0        | DUP Dd,Vn.D[lane]                        | Dd -> result    | A64                     |
| poly8_t vdupb_lane_p8(poly8x8_t vec, const int lane)        | vec -> Vn.8B<br>0 <= lane <= 7   | DUP Bd,Vn.B[lane]                        | Bd -> result    | A64                     |
| poly16_t vduph_lane_p16(poly16x4_t vec, const int lane)     | vec -> Vn.4H<br>0 <= lane <= 3   | DUP Hd,Vn.H[lane]                        | Hd -> result    | A64                     |
| int8_t vdupb_laneq_s8(int8x16_t vec, const int lane)        | vec -> Vn.16B<br>0 <= lane <= 15 | DUP Bd,Vn.B[lane]                        | Bd -> result    | A64                     |
| int16_t vduph_laneq_s16(int16x8_t vec, const int lane)      | vec -> Vn.8H<br>0 <= lane <= 7   | DUP Hd,Vn.H[lane]                        | Hd -> result    | A64                     |

| Intrinsic                                                                  | Argument Preparation                             | Instruction            | Result           | Supported Architectures |
|----------------------------------------------------------------------------|--------------------------------------------------|------------------------|------------------|-------------------------|
| int32_t vdupq_laneq_s32(int32x4_t vec, const int lane)                     | vec -> Vn,4S<br>0 <= lane <=<br>3                | DUP Sd,Vn,S[lane]      | Sd -> result     | A64                     |
| int64_t vdupd_laneq_s64(int64x2_t vec, const int lane)                     | vec -> Vn,2D<br>0 <= lane <=<br>1                | DUP Dd,Vn,D[lane]      | Dd -> result     | A64                     |
| uint8_t vdupb_laneq_u8(uint8x16_t vec, const int lane)                     | vec -> Vn,16B<br>0 <= lane <=<br>15              | DUP Bd,Vn,B[lane]      | Bd -> result     | A64                     |
| uint16_t vduph_laneq_u16(uint16x8_t vec, const int lane)                   | vec -> Vn,8H<br>0 <= lane <=<br>7                | DUP Hd,Vn,H[lane]      | Hd -> result     | A64                     |
| uint32_t vdupq_laneq_u32(uint32x4_t vec, const int lane)                   | vec -> Vn,4S<br>0 <= lane <=<br>3                | DUP Sd,Vn,S[lane]      | Sd -> result     | A64                     |
| uint64_t vdupd_laneq_u64(uint64x2_t vec, const int lane)                   | vec -> Vn,2D<br>0 <= lane <=<br>1                | DUP Dd,Vn,D[lane]      | Dd -> result     | A64                     |
| float32_t vdupq_laneq_f32(float32x4_t vec, const int lane)                 | vec -> Vn,4S<br>0 <= lane <=<br>3                | DUP Sd,Vn,S[lane]      | Sd -> result     | A64                     |
| float64_t vdupd_laneq_f64(float64x2_t vec, const int lane)                 | vec -> Vn,2D<br>0 <= lane <=<br>1                | DUP Dd,Vn,D[lane]      | Dd -> result     | A64                     |
| poly8_t vdupb_laneq_p8(poly8x16_t vec, const int lane)                     | vec -> Vn,16B<br>0 <= lane <=<br>15              | DUP Bd,Vn,B[lane]      | Bd -> result     | A64                     |
| poly16_t vduph_laneq_p16(poly16x8_t vec, const int lane)                   | vec -> Vn,8H<br>0 <= lane <=<br>7                | DUP Hd,Vn,H[lane]      | Hd -> result     | A64                     |
| int8x8_t vld1_s8(int8_t const * ptr)                                       | ptr -> Xn                                        | LD1 [Vt,8B],[Xn]       | Vt,8B -> result  | v7/A32/A64              |
| int8x16_t vld1q_s8(int8_t const * ptr)                                     | ptr -> Xn                                        | LD1 [Vt,16B],[Xn]      | Vt,16B -> result | v7/A32/A64              |
| int16x4_t vld1_s16(int16_t const * ptr)                                    | ptr -> Xn                                        | LD1 [Vt,4H],[Xn]       | Vt,4H -> result  | v7/A32/A64              |
| int16x8_t vld1q_s16(int16_t const * ptr)                                   | ptr -> Xn                                        | LD1 [Vt,8H],[Xn]       | Vt,8H -> result  | v7/A32/A64              |
| int32x2_t vld1_s32(int32_t const * ptr)                                    | ptr -> Xn                                        | LD1 [Vt,2S],[Xn]       | Vt,2S -> result  | v7/A32/A64              |
| int32x4_t vld1q_s32(int32_t const * ptr)                                   | ptr -> Xn                                        | LD1 [Vt,4S],[Xn]       | Vt,4S -> result  | v7/A32/A64              |
| int64x1_t vld1_s64(int64_t const * ptr)                                    | ptr -> Xn                                        | LD1 [Vt,1D],[Xn]       | Vt,1D -> result  | v7/A32/A64              |
| int64x2_t vld1q_s64(int64_t const * ptr)                                   | ptr -> Xn                                        | LD1 [Vt,2D],[Xn]       | Vt,2D -> result  | v7/A32/A64              |
| uint8x8_t vld1_u8(uint8_t const * ptr)                                     | ptr -> Xn                                        | LD1 [Vt,8B],[Xn]       | Vt,8B -> result  | v7/A32/A64              |
| uint8x16_t vld1q_u8(uint8_t const * ptr)                                   | ptr -> Xn                                        | LD1 [Vt,16B],[Xn]      | Vt,16B -> result | v7/A32/A64              |
| uint16x4_t vld1_u16(uint16_t const * ptr)                                  | ptr -> Xn                                        | LD1 [Vt,4H],[Xn]       | Vt,4H -> result  | v7/A32/A64              |
| uint16x8_t vld1q_u16(uint16_t const * ptr)                                 | ptr -> Xn                                        | LD1 [Vt,8H],[Xn]       | Vt,8H -> result  | v7/A32/A64              |
| uint32x2_t vld1_u32(uint32_t const * ptr)                                  | ptr -> Xn                                        | LD1 [Vt,2S],[Xn]       | Vt,2S -> result  | v7/A32/A64              |
| uint32x4_t vld1q_u32(uint32_t const * ptr)                                 | ptr -> Xn                                        | LD1 [Vt,4S],[Xn]       | Vt,4S -> result  | v7/A32/A64              |
| uint64x1_t vld1_u64(uint64_t const * ptr)                                  | ptr -> Xn                                        | LD1 [Vt,1D],[Xn]       | Vt,1D -> result  | v7/A32/A64              |
| uint64x2_t vld1q_u64(uint64_t const * ptr)                                 | ptr -> Xn                                        | LD1 [Vt,2D],[Xn]       | Vt,2D -> result  | v7/A32/A64              |
| poly8x4_t vld1_p8(poly8x4_t const * ptr)                                   | ptr -> Xn                                        | LD1 [Vt,1D],[Xn]       | Vt,1D -> result  | A32/A64                 |
| poly8x8_t vld1q_p8(poly8x8_t const * ptr)                                  | ptr -> Xn                                        | LD1 [Vt,2D],[Xn]       | Vt,2D -> result  | A32/A64                 |
| float32x4_t vld1_f32(float32_t const * ptr)                                | ptr -> Xn                                        | LD1 [Vt,4H],[Xn]       | Vt,4H -> result  | v7/A32/A64              |
| float32x8_t vld1q_f32(float32_t const * ptr)                               | ptr -> Xn                                        | LD1 [Vt,8H],[Xn]       | Vt,8H -> result  | v7/A32/A64              |
| float64x2_t vld1_f64(float64_t const * ptr)                                | ptr -> Xn                                        | LD1 [Vt,2S],[Xn]       | Vt,2S -> result  | v7/A32/A64              |
| float64x4_t vld1q_f64(float64_t const * ptr)                               | ptr -> Xn                                        | LD1 [Vt,4S],[Xn]       | Vt,4S -> result  | v7/A32/A64              |
| poly8x8_t vld1_p8(poly8_t const * ptr)                                     | ptr -> Xn                                        | LD1 [Vt,8B],[Xn]       | Vt,8B -> result  | v7/A32/A64              |
| poly8x16_t vld1q_p8(poly8_t const * ptr)                                   | ptr -> Xn                                        | LD1 [Vt,16B],[Xn]      | Vt,16B -> result | v7/A32/A64              |
| poly16x4_t vld1_p16(poly16_t const * ptr)                                  | ptr -> Xn                                        | LD1 [Vt,4H],[Xn]       | Vt,4H -> result  | v7/A32/A64              |
| poly16x8_t vld1q_p16(poly16_t const * ptr)                                 | ptr -> Xn                                        | LD1 [Vt,8H],[Xn]       | Vt,8H -> result  | v7/A32/A64              |
| float64x1_t vld1_f64(float64_t const * ptr)                                | ptr -> Xn                                        | LD1 [Vt,1D],[Xn]       | Vt,1D -> result  | A64                     |
| float64x2_t vld1q_f64(float64_t const * ptr)                               | ptr -> Xn                                        | LD1 [Vt,2D],[Xn]       | Vt,2D -> result  | A64                     |
| int8x8_t vld1_lane_s8(int8_t const * ptr, int8x8_t src, const int lane)    | ptr -> Xn<br>src -> Vt,8B<br>0 <= lane <=<br>7   | LD1 [Vt,B],[lane],[Xn] | Vt,8B -> result  | v7/A32/A64              |
| int8x16_t vld1q_lane_s8(int8_t const * ptr, int8x16_t src, const int lane) | ptr -> Xn<br>src -> Vt,16B<br>0 <= lane <=<br>15 | LD1 [Vt,B],[lane],[Xn] | Vt,16B -> result | v7/A32/A64              |

| Intrinsic                                                                          | Argument Preparation                          | Instruction          | Result           | Supported Architectures |
|------------------------------------------------------------------------------------|-----------------------------------------------|----------------------|------------------|-------------------------|
| int16x4_t vld1_lane_s16(int16_t const * ptr, int16x4_t src, const int lane)        | ptr -> Xn<br>src -> Vt.4H<br>0 <= lane <= 3   | LD1 {Vt.H}[lane][Xn] | Vt.4H -> result  | v7/A32/A64              |
| int16x8_t vld1q_lane_s16(int16_t const * ptr, int16x8_t src, const int lane)       | ptr -> Xn<br>src -> Vt.8H<br>0 <= lane <= 7   | LD1 {Vt.H}[lane][Xn] | Vt.8H -> result  | v7/A32/A64              |
| int32x2_t vld1_lane_s32(int32_t const * ptr, int32x2_t src, const int lane)        | ptr -> Xn<br>src -> Vt.2S<br>0 <= lane <= 1   | LD1 {Vt.S}[lane][Xn] | Vt.2S -> result  | v7/A32/A64              |
| int32x4_t vld1q_lane_s32(int32_t const * ptr, int32x4_t src, const int lane)       | ptr -> Xn<br>src -> Vt.4S<br>0 <= lane <= 3   | LD1 {Vt.S}[lane][Xn] | Vt.4S -> result  | v7/A32/A64              |
| int64x4_t vld1_lane_s64(int64_t const * ptr, int64x4_t src, const int lane)        | ptr -> Xn<br>src -> Vt.1D<br>lane == 0        | LD1 {Vt.D}[lane][Xn] | Vt.1D -> result  | v7/A32/A64              |
| int64x2_t vld1q_lane_s64(int64_t const * ptr, int64x2_t src, const int lane)       | ptr -> Xn<br>src -> Vt.2D<br>0 <= lane <= 1   | LD1 {Vt.D}[lane][Xn] | Vt.2D -> result  | v7/A32/A64              |
| uint8x8_t vld1_lane_u8(uint8_t const * ptr, uint8x8_t src, const int lane)         | ptr -> Xn<br>src -> Vt.8B<br>0 <= lane <= 7   | LD1 {Vt.B}[lane][Xn] | Vt.8B -> result  | v7/A32/A64              |
| uint8x16_t vld1q_lane_u8(uint8_t const * ptr, uint8x16_t src, const int lane)      | ptr -> Xn<br>src -> Vt.16B<br>0 <= lane <= 15 | LD1 {Vt.B}[lane][Xn] | Vt.16B -> result | v7/A32/A64              |
| uint16x4_t vld1_lane_u16(uint16_t const * ptr, uint16x4_t src, const int lane)     | ptr -> Xn<br>src -> Vt.4H<br>0 <= lane <= 3   | LD1 {Vt.H}[lane][Xn] | Vt.4H -> result  | v7/A32/A64              |
| uint16x8_t vld1q_lane_u16(uint16_t const * ptr, uint16x8_t src, const int lane)    | ptr -> Xn<br>src -> Vt.8H<br>0 <= lane <= 7   | LD1 {Vt.H}[lane][Xn] | Vt.8H -> result  | v7/A32/A64              |
| uint32x2_t vld1_lane_u32(uint32_t const * ptr, uint32x2_t src, const int lane)     | ptr -> Xn<br>src -> Vt.2S<br>0 <= lane <= 1   | LD1 {Vt.S}[lane][Xn] | Vt.2S -> result  | v7/A32/A64              |
| uint32x4_t vld1q_lane_u32(uint32_t const * ptr, uint32x4_t src, const int lane)    | ptr -> Xn<br>src -> Vt.4S<br>0 <= lane <= 3   | LD1 {Vt.S}[lane][Xn] | Vt.4S -> result  | v7/A32/A64              |
| uint64x1_t vld1_lane_u64(uint64_t const * ptr, uint64x1_t src, const int lane)     | ptr -> Xn<br>src -> Vt.1D<br>lane == 0        | LD1 {Vt.D}[lane][Xn] | Vt.1D -> result  | v7/A32/A64              |
| uint64x2_t vld1q_lane_u64(uint64_t const * ptr, uint64x2_t src, const int lane)    | ptr -> Xn<br>src -> Vt.2D<br>0 <= lane <= 1   | LD1 {Vt.D}[lane][Xn] | Vt.2D -> result  | v7/A32/A64              |
| poly64x1_t vld1_lane_p64(poly64_t const * ptr, poly64x1_t src, const int lane)     | ptr -> Xn<br>src -> Vt.1D<br>lane == 0        | LD1 {Vt.D}[lane][Xn] | Vt.1D -> result  | A32/A64                 |
| poly64x2_t vld1q_lane_p64(poly64_t const * ptr, poly64x2_t src, const int lane)    | ptr -> Xn<br>src -> Vt.2D<br>0 <= lane <= 1   | LD1 {Vt.D}[lane][Xn] | Vt.2D -> result  | A32/A64                 |
| float16x4_t vld1_lane_f16(float16_t const * ptr, float16x4_t src, const int lane)  | ptr -> Xn<br>src -> Vt.4H<br>0 <= lane <= 3   | LD1 {Vt.H}[lane][Xn] | Vt.4H -> result  | v7/A32/A64              |
| float16x8_t vld1q_lane_f16(float16_t const * ptr, float16x8_t src, const int lane) | ptr -> Xn<br>src -> Vt.8H<br>0 <= lane <= 7   | LD1 {Vt.H}[lane][Xn] | Vt.8H -> result  | v7/A32/A64              |
| float32x2_t vld1_lane_f32(float32_t const * ptr, float32x2_t src, const int lane)  | ptr -> Xn<br>src -> Vt.2S<br>0 <= lane <= 1   | LD1 {Vt.S}[lane][Xn] | Vt.2S -> result  | v7/A32/A64              |

| Intrinsic                                                                          | Argument Preparation                          | Instruction            | Result           | Supported Architectures |
|------------------------------------------------------------------------------------|-----------------------------------------------|------------------------|------------------|-------------------------|
| float32x4_t vld1q_lane_f32(float32_t const * ptr, float32x4_t src, const int lane) | ptr -> Xn<br>src -> Vt.4S<br>0 <= lane <= 3   | LD1 [Vt.S][lane], [Xn] | Vt.4S -> result  | v7/A32/A64              |
| poly8x8_t vld1_lane_p8(poly8_t const * ptr, poly8x8_t src, const int lane)         | ptr -> Xn<br>src -> Vt.8B<br>0 <= lane <= 7   | LD1 [Vt.B][lane], [Xn] | Vt.8B -> result  | v7/A32/A64              |
| poly8x16_t vld1q_lane_p8(poly8_t const * ptr, poly8x16_t src, const int lane)      | ptr -> Xn<br>src -> Vt.16B<br>0 <= lane <= 15 | LD1 [Vt.B][lane], [Xn] | Vt.16B -> result | v7/A32/A64              |
| poly16x4_t vld1_lane_p16(poly16_t const * ptr, poly16x4_t src, const int lane)     | ptr -> Xn<br>src -> Vt.4H<br>0 <= lane <= 3   | LD1 [Vt.H][lane], [Xn] | Vt.4H -> result  | v7/A32/A64              |
| poly16x8_t vld1q_lane_p16(poly16_t const * ptr, poly16x8_t src, const int lane)    | ptr -> Xn<br>src -> Vt.8H<br>0 <= lane <= 7   | LD1 [Vt.H][lane], [Xn] | Vt.8H -> result  | v7/A32/A64              |
| float64x1_t vld1_lane_f64(float64_t const * ptr, float64x1_t src, const int lane)  | ptr -> Xn<br>src -> Vt.1D<br>lane == 0        | LD1 [Vt.D][lane], [Xn] | Vt.1D -> result  | A64                     |
| float64x2_t vld1q_lane_f64(float64_t const * ptr, float64x2_t src, const int lane) | ptr -> Xn<br>src -> Vt.2D<br>0 <= lane <= 1   | LD1 [Vt.D][lane], [Xn] | Vt.2D -> result  | A64                     |
| int8x8_t vld1_dup_s8(int8_t const * ptr)                                           | ptr -> Xn                                     | LD1R [Vt.8B], [Xn]     | Vt.8B -> result  | v7/A32/A64              |
| int8x16_t vld1q_dup_s8(int8_t const * ptr)                                         | ptr -> Xn                                     | LD1R [Vt.16B], [Xn]    | Vt.16B -> result | v7/A32/A64              |
| int16x4_t vld1_dup_s16(int16_t const * ptr)                                        | ptr -> Xn                                     | LD1R [Vt.4H], [Xn]     | Vt.4H -> result  | v7/A32/A64              |
| int16x8_t vld1q_dup_s16(int16_t const * ptr)                                       | ptr -> Xn                                     | LD1R [Vt.8H], [Xn]     | Vt.8H -> result  | v7/A32/A64              |
| int32x2_t vld1_dup_s32(int32_t const * ptr)                                        | ptr -> Xn                                     | LD1R [Vt.2S], [Xn]     | Vt.2S -> result  | v7/A32/A64              |
| int32x4_t vld1q_dup_s32(int32_t const * ptr)                                       | ptr -> Xn                                     | LD1R [Vt.4S], [Xn]     | Vt.4S -> result  | v7/A32/A64              |
| int64x1_t vld1_dup_s64(int64_t const * ptr)                                        | ptr -> Xn                                     | LD1 [Vt.1D], [Xn]      | Vt.1D -> result  | v7/A32/A64              |
| int64x2_t vld1q_dup_s64(int64_t const * ptr)                                       | ptr -> Xn                                     | LD1 [Vt.2D], [Xn]      | Vt.2D -> result  | v7/A32/A64              |
| uint8x8_t vld1_dup_u8(uint8_t const * ptr)                                         | ptr -> Xn                                     | LD1R [Vt.8B], [Xn]     | Vt.8B -> result  | v7/A32/A64              |
| uint8x16_t vld1q_dup_u8(uint8_t const * ptr)                                       | ptr -> Xn                                     | LD1R [Vt.16B], [Xn]    | Vt.16B -> result | v7/A32/A64              |
| uint16x4_t vld1_dup_u16(uint16_t const * ptr)                                      | ptr -> Xn                                     | LD1R [Vt.4H], [Xn]     | Vt.4H -> result  | v7/A32/A64              |
| uint16x8_t vld1q_dup_u16(uint16_t const * ptr)                                     | ptr -> Xn                                     | LD1R [Vt.8H], [Xn]     | Vt.8H -> result  | v7/A32/A64              |
| uint32x2_t vld1q_dup_u32(uint32_t const * ptr)                                     | ptr -> Xn                                     | LD1R [Vt.2S], [Xn]     | Vt.2S -> result  | v7/A32/A64              |
| uint32x4_t vld1q_dup_u32(uint32_t const * ptr)                                     | ptr -> Xn                                     | LD1R [Vt.4S], [Xn]     | Vt.4S -> result  | v7/A32/A64              |
| uint64x1_t vld1q_dup_u64(uint64_t const * ptr)                                     | ptr -> Xn                                     | LD1 [Vt.1D], [Xn]      | Vt.1D -> result  | v7/A32/A64              |
| uint64x2_t vld1q_dup_u64(uint64_t const * ptr)                                     | ptr -> Xn                                     | LD1 [Vt.2D], [Xn]      | Vt.2D -> result  | v7/A32/A64              |
| poly4x4_t vld1q_dup_p4(poly4_t const * ptr)                                        | ptr -> Xn                                     | LD1 [Vt.1D], [Xn]      | Vt.1D -> result  | A32/A64                 |
| poly64x2_t vld1q_dup_p64(poly64_t const * ptr)                                     | ptr -> Xn                                     | LD1 [Vt.2D], [Xn]      | Vt.2D -> result  | A32/A64                 |
| float16x4_t vld1q_f16(float16_t const * ptr)                                       | ptr -> Xn                                     | LD1R [Vt.4H], [Xn]     | Vt.4H -> result  | v7/A32/A64              |
| float16x8_t vld1q_dup_f16(float16_t const * ptr)                                   | ptr -> Xn                                     | LD1R [Vt.8H], [Xn]     | Vt.8H -> result  | v7/A32/A64              |
| float32x2_t vld1q_f32(float32_t const * ptr)                                       | ptr -> Xn                                     | LD1R [Vt.2S], [Xn]     | Vt.2S -> result  | v7/A32/A64              |
| float32x4_t vld1q_dup_f32(float32_t const * ptr)                                   | ptr -> Xn                                     | LD1R [Vt.4S], [Xn]     | Vt.4S -> result  | v7/A32/A64              |
| poly8x8_t vld1q_dup_p8(poly8_t const * ptr)                                        | ptr -> Xn                                     | LD1R [Vt.8B], [Xn]     | Vt.8B -> result  | v7/A32/A64              |
| poly8x16_t vld1q_dup_p8(poly8_t const * ptr)                                       | ptr -> Xn                                     | LD1R [Vt.16B], [Xn]    | Vt.16B -> result | v7/A32/A64              |
| poly16x4_t vld1q_dup_p16(poly16_t const * ptr)                                     | ptr -> Xn                                     | LD1R [Vt.4H], [Xn]     | Vt.4H -> result  | v7/A32/A64              |
| poly16x8_t vld1q_dup_p16(poly16_t const * ptr)                                     | ptr -> Xn                                     | LD1R [Vt.8H], [Xn]     | Vt.8H -> result  | v7/A32/A64              |
| float64x1_t vld1q_dup_f64(float64_t const * ptr)                                   | ptr -> Xn                                     | LD1 [Vt.1D], [Xn]      | Vt.1D -> result  | A64                     |
| float64x2_t vld1q_dup_f64(float64_t const * ptr)                                   | ptr -> Xn                                     | LD1 [Vt.2D], [Xn]      | Vt.2D -> result  | A64                     |
| void vst1_s8(int8_t * ptr, int8x8_t val)                                           | ptr -> Xn<br>val -> Vt.8B                     | ST1 [Vt.8B], [Xn]      | void -> result   | v7/A32/A64              |
| void vst1q_s8(int8x8_t * ptr, int8x8_t val)                                        | ptr -> Xn<br>val -> Vt.16B                    | ST1 [Vt.16B], [Xn]     | void -> result   | v7/A32/A64              |
| void vst1_s16(int16_t * ptr, int16x4_t val)                                        | ptr -> Xn<br>val -> Vt.4H                     | ST1 [Vt.4H], [Xn]      | void -> result   | v7/A32/A64              |
| void vst1q_s16(int16x8_t * ptr, int16x8_t val)                                     | ptr -> Xn<br>val -> Vt.8H                     | ST1 [Vt.8H], [Xn]      | void -> result   | v7/A32/A64              |
| void vst1_s32(int32_t * ptr, int32x2_t val)                                        | ptr -> Xn<br>val -> Vt.2S                     | ST1 [Vt.2S], [Xn]      | void -> result   | v7/A32/A64              |
| void vst1q_s32(int32x4_t * ptr, int32x4_t val)                                     | ptr -> Xn<br>val -> Vt.4S                     | ST1 [Vt.4S], [Xn]      | void -> result   | v7/A32/A64              |

| Intrinsic                                                         | Argument Preparation                        | Instruction         | Result         | Supported Architectures |
|-------------------------------------------------------------------|---------------------------------------------|---------------------|----------------|-------------------------|
| void vst1_s64(int64_t * ptr, int64x1_t val)                       | ptr -> Xn<br>val -> Vt1D                    | ST1[VL1D][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_s64(int64_t * ptr, int64x2_t val)                      | ptr -> Xn<br>val -> Vt2D                    | ST1[VL2D][Xn]       | void -> result | v7/A32/A64              |
| void vst1_u8(uint8_t * ptr, uint8x8_t val)                        | ptr -> Xn<br>val -> Vt8B                    | ST1[VL8B][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_u8(uint8_t * ptr, uint8x16_t val)                      | ptr -> Xn<br>val -> Vt16B                   | ST1[VL16B][Xn]      | void -> result | v7/A32/A64              |
| void vst1_u16(uint16_t * ptr, uint16x4_t val)                     | ptr -> Xn<br>val -> Vt4H                    | ST1[VL4H][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_u16(uint16_t * ptr, uint16x8_t val)                    | ptr -> Xn<br>val -> Vt8H                    | ST1[VL8H][Xn]       | void -> result | v7/A32/A64              |
| void vst1_u32(uint32_t * ptr, uint32x2_t val)                     | ptr -> Xn<br>val -> Vt2S                    | ST1[VL2S][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_u32(uint32_t * ptr, uint32x4_t val)                    | ptr -> Xn<br>val -> Vt4S                    | ST1[VL4S][Xn]       | void -> result | v7/A32/A64              |
| void vst1_u64(uint64_t * ptr, uint64x1_t val)                     | ptr -> Xn<br>val -> Vt1D                    | ST1[VL1D][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_u64(uint64_t * ptr, uint64x2_t val)                    | ptr -> Xn<br>val -> Vt2D                    | ST1[VL2D][Xn]       | void -> result | v7/A32/A64              |
| void vst1_p64(poly64_t * ptr, poly64x1_t val)                     | ptr -> Xn<br>val -> Vt1D                    | ST1[VL1D][Xn]       | void -> result | A32/A64                 |
| void vst1q_p64(poly64_t * ptr, poly64x2_t val)                    | ptr -> Xn<br>val -> Vt2D                    | ST1[VL2D][Xn]       | void -> result | A32/A64                 |
| void vst1_f16(float16_t * ptr, float16x4_t val)                   | ptr -> Xn<br>val -> Vt4H                    | ST1[VL4H][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_f16(float16_t * ptr, float16x8_t val)                  | ptr -> Xn<br>val -> Vt8H                    | ST1[VL8H][Xn]       | void -> result | v7/A32/A64              |
| void vst1_f32(float32_t * ptr, float32x2_t val)                   | ptr -> Xn<br>val -> Vt2S                    | ST1[VL2S][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_f32(float32_t * ptr, float32x4_t val)                  | ptr -> Xn<br>val -> Vt4S                    | ST1[VL4S][Xn]       | void -> result | v7/A32/A64              |
| void vst1_p8(poly8_t * ptr, poly8x8_t val)                        | ptr -> Xn<br>val -> Vt8B                    | ST1[VL8B][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_p8(poly8_t * ptr, poly8x16_t val)                      | ptr -> Xn<br>val -> Vt16B                   | ST1[VL16B][Xn]      | void -> result | v7/A32/A64              |
| void vst1_p16(poly16_t * ptr, poly16x4_t val)                     | ptr -> Xn<br>val -> Vt4H                    | ST1[VL4H][Xn]       | void -> result | v7/A32/A64              |
| void vst1q_p16(poly16_t * ptr, poly16x8_t val)                    | ptr -> Xn<br>val -> Vt8H                    | ST1[VL8H][Xn]       | void -> result | v7/A32/A64              |
| void vst1_p64(float64_t * ptr, float64x1_t val)                   | ptr -> Xn<br>val -> Vt1D                    | ST1[VL1D][Xn]       | void -> result | A64                     |
| void vst1q_p64(float64_t * ptr, float64x2_t val)                  | ptr -> Xn<br>val -> Vt2D                    | ST1[VL2D][Xn]       | void -> result | A64                     |
| void vst1_lane_s8(int8_t * ptr, int8x8_t val, const int lane)     | ptr -> Xn<br>val -> Vt8B<br>0 -> lane < 7   | ST1[VL8][lane][Xn]  | void -> result | v7/A32/A64              |
| void vst1q_lane_s8(int8_t * ptr, int8x16_t val, const int lane)   | ptr -> Xn<br>val -> Vt16B<br>0 -> lane < 15 | ST1[VL16][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_s16(int16_t * ptr, int16x4_t val, const int lane)  | ptr -> Xn<br>val -> Vt4H<br>0 -> lane < 3   | ST1[VL4][lane][Xn]  | void -> result | v7/A32/A64              |
| void vst1q_lane_s16(int16_t * ptr, int16x8_t val, const int lane) | ptr -> Xn<br>val -> Vt8H<br>0 -> lane < 7   | ST1[VL8][lane][Xn]  | void -> result | v7/A32/A64              |
| void vst1_lane_s32(int32_t * ptr, int32x2_t val, const int lane)  | ptr -> Xn<br>val -> Vt2S<br>0 -> lane < 1   | ST1[VL2][lane][Xn]  | void -> result | v7/A32/A64              |
| void vst1q_lane_s32(int32_t * ptr, int32x4_t val, const int lane) | ptr -> Xn<br>val -> Vt4S<br>0 -> lane < 3   | ST1[VL4][lane][Xn]  | void -> result | v7/A32/A64              |
| void vst1_lane_s64(int64_t * ptr, int64x4_t val, const int lane)  | ptr -> Xn<br>val -> Vt1D<br>lane -> 0       | ST1[VL4][lane][Xn]  | void -> result | v7/A32/A64              |

| Intrinsic                                                            | Argument Preparation                          | Instruction         | Result         | Supported Architectures |
|----------------------------------------------------------------------|-----------------------------------------------|---------------------|----------------|-------------------------|
| void vst1q_lane_s64(int64_t* ptr, int64x2_t val, const int lane)     | ptr -> Xn<br>val -> Vt.2D<br>0 <= lane <= 1   | ST1[Vt.d][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_u8(uint8_t* ptr, uint8x8_t val, const int lane)       | ptr -> Xn<br>val -> Vt.8B<br>0 <= lane <= 7   | ST1[Vt.b][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_u8(uint8_t* ptr, uint8x16_t val, const int lane)     | ptr -> Xn<br>val -> Vt.16B<br>0 <= lane <= 15 | ST1[Vt.b][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_u16(uint16_t* ptr, uint16x4_t val, const int lane)    | ptr -> Xn<br>val -> Vt.4H<br>0 <= lane <= 3   | ST1[Vt.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_u16(uint16_t* ptr, uint16x8_t val, const int lane)   | ptr -> Xn<br>val -> Vt.8H<br>0 <= lane <= 7   | ST1[Vt.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_u32(uint32_t* ptr, uint32x2_t val, const int lane)    | ptr -> Xn<br>val -> Vt.2S<br>0 <= lane <= 1   | ST1[Vt.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_u32(uint32_t* ptr, uint32x4_t val, const int lane)   | ptr -> Xn<br>val -> Vt.4S<br>0 <= lane <= 3   | ST1[Vt.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_u64(uint64_t* ptr, uint64x1_t val, const int lane)    | ptr -> Xn<br>val -> Vt.1D<br>lane == 0        | ST1[Vt.d][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_u64(uint64_t* ptr, uint64x2_t val, const int lane)   | ptr -> Xn<br>val -> Vt.2D<br>0 <= lane <= 1   | ST1[Vt.d][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_p64(poly64_t* ptr, poly64x1_t val, const int lane)    | ptr -> Xn<br>val -> Vt.1D<br>lane == 0        | ST1[Vt.d][lane][Xn] | void -> result | A32/A64                 |
| void vst1q_lane_p64(poly64_t* ptr, poly64x2_t val, const int lane)   | ptr -> Xn<br>val -> Vt.2D<br>0 <= lane <= 1   | ST1[Vt.d][lane][Xn] | void -> result | A32/A64                 |
| void vst1_lane_f16(float16_t* ptr, float16x4_t val, const int lane)  | ptr -> Xn<br>val -> Vt.4H<br>0 <= lane <= 3   | ST1[Vt.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_f16(float16_t* ptr, float16x8_t val, const int lane) | ptr -> Xn<br>val -> Vt.8H<br>0 <= lane <= 7   | ST1[Vt.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_f32(float32_t* ptr, float32x2_t val, const int lane)  | ptr -> Xn<br>val -> Vt.2S<br>0 <= lane <= 1   | ST1[Vt.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_f32(float32_t* ptr, float32x4_t val, const int lane) | ptr -> Xn<br>val -> Vt.4S<br>0 <= lane <= 3   | ST1[Vt.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_p8(poly8_t* ptr, poly8x8_t val, const int lane)       | ptr -> Xn<br>val -> Vt.8B<br>0 <= lane <= 7   | ST1[Vt.b][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_p8(poly8_t* ptr, poly8x16_t val, const int lane)     | ptr -> Xn<br>val -> Vt.16B<br>0 <= lane <= 15 | ST1[Vt.b][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1_lane_p16(poly16_t* ptr, poly16x4_t val, const int lane)    | ptr -> Xn<br>val -> Vt.4H<br>0 <= lane <= 3   | ST1[Vt.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst1q_lane_p16(poly16_t* ptr, poly16x8_t val, const int lane)   | ptr -> Xn<br>val -> Vt.8H<br>0 <= lane <= 7   | ST1[Vt.h][lane][Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                             | Argument Preparation                      | Instruction           | Result                                              | Supported Architectures |
|-----------------------------------------------------------------------|-------------------------------------------|-----------------------|-----------------------------------------------------|-------------------------|
| void vst1_lane_f64(float64_t * ptr, float64x1_t val, const int lane)  | ptr -> Xn<br>val -> VL1D<br>lane -> 0     | ST1[VLd][lane][Xn]    | void -> result                                      | A64                     |
| void vst1q_lane_f64(float64_t * ptr, float64x2_t val, const int lane) | ptr -> Xn<br>val -> VL2D<br>0 <- lane < 1 | ST1[VLd][lane][Xn]    | void -> result                                      | A64                     |
| int8x8x2_vld2_s8(int8_t const * ptr)                                  | ptr -> Xn                                 | LD2[VL8B-VL28B][Xn]   | VL28B -> result[val][1]<br>VL8B -> result[val][0]   | V7/A32/A64              |
| int8x16x2_vld2q_s8(int8_t const * ptr)                                | ptr -> Xn                                 | LD2[VL16B-VL216B][Xn] | VL216B -> result[val][1]<br>VL16B -> result[val][0] | V7/A32/A64              |
| int16x4x2_vld2_s16(int16_t const * ptr)                               | ptr -> Xn                                 | LD2[VL4H-VL24H][Xn]   | VL24H -> result[val][1]<br>VL4H -> result[val][0]   | V7/A32/A64              |
| int16x8x2_vld2q_s16(int16_t const * ptr)                              | ptr -> Xn                                 | LD2[VL8H-VL28H][Xn]   | VL28H -> result[val][1]<br>VL8H -> result[val][0]   | V7/A32/A64              |
| int32x2x2_vld2_s32(int32_t const * ptr)                               | ptr -> Xn                                 | LD2[VL2S-VL22S][Xn]   | VL22S -> result[val][1]<br>VL2S -> result[val][0]   | V7/A32/A64              |
| int32x4x2_vld2q_s32(int32_t const * ptr)                              | ptr -> Xn                                 | LD2[VL4S-VL24S][Xn]   | VL24S -> result[val][1]<br>VL4S -> result[val][0]   | V7/A32/A64              |
| uint8x8x2_vld2_u8(uint8_t const * ptr)                                | ptr -> Xn                                 | LD2[VL8B-VL28B][Xn]   | VL28B -> result[val][1]<br>VL8B -> result[val][0]   | V7/A32/A64              |
| uint8x16x2_vld2q_u8(uint8_t const * ptr)                              | ptr -> Xn                                 | LD2[VL16B-VL216B][Xn] | VL216B -> result[val][1]<br>VL16B -> result[val][0] | V7/A32/A64              |
| uint16x4x2_vld2_u16(uint16_t const * ptr)                             | ptr -> Xn                                 | LD2[VL4H-VL24H][Xn]   | VL24H -> result[val][1]<br>VL4H -> result[val][0]   | V7/A32/A64              |
| uint16x8x2_vld2q_u16(uint16_t const * ptr)                            | ptr -> Xn                                 | LD2[VL8H-VL28H][Xn]   | VL28H -> result[val][1]<br>VL8H -> result[val][0]   | V7/A32/A64              |
| uint32x2x2_vld2_u32(uint32_t const * ptr)                             | ptr -> Xn                                 | LD2[VL2S-VL22S][Xn]   | VL22S -> result[val][1]<br>VL2S -> result[val][0]   | V7/A32/A64              |
| uint32x4x2_vld2q_u32(uint32_t const * ptr)                            | ptr -> Xn                                 | LD2[VL4S-VL24S][Xn]   | VL24S -> result[val][1]<br>VL4S -> result[val][0]   | V7/A32/A64              |
| float16x4x2_vld2_f16(float16_t const * ptr)                           | ptr -> Xn                                 | LD2[VL4H-VL24H][Xn]   | VL24H -> result[val][1]<br>VL4H -> result[val][0]   | V7/A32/A64              |
| float16x8x2_vld2q_f16(float16_t const * ptr)                          | ptr -> Xn                                 | LD2[VL8H-VL28H][Xn]   | VL28H -> result[val][1]<br>VL8H -> result[val][0]   | V7/A32/A64              |
| float32x2x2_vld2_f32(float32_t const * ptr)                           | ptr -> Xn                                 | LD2[VL2S-VL22S][Xn]   | VL22S -> result[val][1]<br>VL2S -> result[val][0]   | V7/A32/A64              |
| float32x4x2_vld2q_f32(float32_t const * ptr)                          | ptr -> Xn                                 | LD2[VL4S-VL24S][Xn]   | VL24S -> result[val][1]<br>VL4S -> result[val][0]   | V7/A32/A64              |

| Intrinsic                                      | Argument Preparation | Instruction                 | Result                                                                                 | Supported Architectures |
|------------------------------------------------|----------------------|-----------------------------|----------------------------------------------------------------------------------------|-------------------------|
| poly8x8x2_t vld2_p8(poly8_t const * ptr)       | ptr -> Xn            | LD2 [Vt.8B - Vt.8B][Xn]     | Vt.8B -> result[val][1]<br>Vt.8B -> result[val][0]                                     | v7/A32/A64              |
| poly8x16x2_t vld2q_p8(poly8_t const * ptr)     | ptr -> Xn            | LD2 [Vt.16B - Vt.16B][Xn]   | Vt.16B -> result[val][1]<br>Vt.16B -> result[val][0]                                   | v7/A32/A64              |
| poly16x4x2_t vld2_p16(poly16_t const * ptr)    | ptr -> Xn            | LD2 [Vt.4H - Vt.4H][Xn]     | Vt.4H -> result[val][1]<br>Vt.4H -> result[val][0]                                     | v7/A32/A64              |
| poly16x8x2_t vld2q_p16(poly16_t const * ptr)   | ptr -> Xn            | LD2 [Vt.8H - Vt.8H][Xn]     | Vt.8H -> result[val][1]<br>Vt.8H -> result[val][0]                                     | v7/A32/A64              |
| int64x1x2_t vld2_s64(int64_t const * ptr)      | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]     | Vt.1D -> result[val][1]<br>Vt.1D -> result[val][0]                                     | v7/A32/A64              |
| uint64x1x2_t vld2_u64(uint64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]     | Vt.1D -> result[val][1]<br>Vt.1D -> result[val][0]                                     | v7/A32/A64              |
| poly64x1x2_t vld2_p64(poly64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]     | Vt.1D -> result[val][1]<br>Vt.1D -> result[val][0]                                     | A32/A64                 |
| int64x2x2_t vld2q_s64(int64_t const * ptr)     | ptr -> Xn            | LD2 [Vt.2D - Vt.2D][Xn]     | Vt.2D -> result[val][1]<br>Vt.2D -> result[val][0]                                     | A64                     |
| uint64x2x2_t vld2q_u64(uint64_t const * ptr)   | ptr -> Xn            | LD2 [Vt.2D - Vt.2D][Xn]     | Vt.2D -> result[val][1]<br>Vt.2D -> result[val][0]                                     | A64                     |
| poly64x2x2_t vld2q_p64(poly64_t const * ptr)   | ptr -> Xn            | LD2 [Vt.2D - Vt.2D][Xn]     | Vt.2D -> result[val][1]<br>Vt.2D -> result[val][0]                                     | A64                     |
| float64x1x2_t vld2_f64(float64_t const * ptr)  | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]     | Vt.1D -> result[val][1]<br>Vt.1D -> result[val][0]                                     | A64                     |
| float64x2x2_t vld2q_f64(float64_t const * ptr) | ptr -> Xn            | LD2 [Vt.2D - Vt.2D][Xn]     | Vt.2D -> result[val][1]<br>Vt.2D -> result[val][0]                                     | A64                     |
| int8x8x3_t vld3_s8(int8_t const * ptr)         | ptr -> Xn            | LD3 [Vt.8B - Vt.3.8B][Xn]   | Vt.3.8B -> result[val][2]<br>Vt.3.8B -> result[val][1]<br>Vt.3.8B -> result[val][0]    | v7/A32/A64              |
| int8x16x3_t vld3q_s8(int8_t const * ptr)       | ptr -> Xn            | LD3 [Vt.16B - Vt.3.16B][Xn] | Vt.3.16B -> result[val][2]<br>Vt.3.16B -> result[val][1]<br>Vt.3.16B -> result[val][0] | v7/A32/A64              |
| int16x4x3_t vld3_s16(int16_t const * ptr)      | ptr -> Xn            | LD3 [Vt.4H - Vt.3.4H][Xn]   | Vt.3.4H -> result[val][2]<br>Vt.3.4H -> result[val][1]<br>Vt.3.4H -> result[val][0]    | v7/A32/A64              |
| int16x8x3_t vld3q_s16(int16_t const * ptr)     | ptr -> Xn            | LD3 [Vt.8H - Vt.3.8H][Xn]   | Vt.3.8H -> result[val][2]<br>Vt.3.8H -> result[val][1]<br>Vt.3.8H -> result[val][0]    | v7/A32/A64              |

| Intrinsic                                       | Argument Preparation | Instruction              | Result                                                                             | Supported Architectures |
|-------------------------------------------------|----------------------|--------------------------|------------------------------------------------------------------------------------|-------------------------|
| int32x2x3_t vld3_s32(int32_t const * ptr)       | ptr -> Xn            | LD3(Vt,2S-Vt,3,2S)[Xn]   | Vt,3,2S -> result_val[2]<br>Vt,2,2S -> result_val[1]<br>Vt,2S -> result_val[0]     | v7/A32/A64              |
| int32x4x3_t vld3q_s32(int32_t const * ptr)      | ptr -> Xn            | LD3(Vt,4S-Vt,3,4S)[Xn]   | Vt,3,4S -> result_val[2]<br>Vt,2,4S -> result_val[1]<br>Vt,4S -> result_val[0]     | v7/A32/A64              |
| uint8x8x3_t vld3_u8(uint8_t const * ptr)        | ptr -> Xn            | LD3(Vt,8B-Vt,3,8B)[Xn]   | Vt,3,8B -> result_val[2]<br>Vt,2,8B -> result_val[1]<br>Vt,8B -> result_val[0]     | v7/A32/A64              |
| uint8x16x3_t vld3q_u8(uint8_t const * ptr)      | ptr -> Xn            | LD3(Vt,16B-Vt,3,16B)[Xn] | Vt,3,16B -> result_val[2]<br>Vt,2,16B -> result_val[1]<br>Vt,1,6B -> result_val[0] | v7/A32/A64              |
| uint16x4x3_t vld3_u16(uint16_t const * ptr)     | ptr -> Xn            | LD3(Vt,4H-Vt,3,4H)[Xn]   | Vt,3,4H -> result_val[2]<br>Vt,2,4H -> result_val[1]<br>Vt,4H -> result_val[0]     | v7/A32/A64              |
| uint16x8x3_t vld3q_u16(uint16_t const * ptr)    | ptr -> Xn            | LD3(Vt,8H-Vt,3,8H)[Xn]   | Vt,3,8H -> result_val[2]<br>Vt,2,8H -> result_val[1]<br>Vt,8H -> result_val[0]     | v7/A32/A64              |
| uint32x2x3_t vld3_u32(uint32_t const * ptr)     | ptr -> Xn            | LD3(Vt,2S-Vt,3,2S)[Xn]   | Vt,3,2S -> result_val[2]<br>Vt,2,2S -> result_val[1]<br>Vt,2S -> result_val[0]     | v7/A32/A64              |
| uint32x4x3_t vld3q_u32(uint32_t const * ptr)    | ptr -> Xn            | LD3(Vt,4S-Vt,3,4S)[Xn]   | Vt,3,4S -> result_val[2]<br>Vt,2,4S -> result_val[1]<br>Vt,4S -> result_val[0]     | v7/A32/A64              |
| float128x4x3_t vld3_f16(float16_t const * ptr)  | ptr -> Xn            | LD3(Vt,4H-Vt,3,4H)[Xn]   | Vt,3,4H -> result_val[2]<br>Vt,2,4H -> result_val[1]<br>Vt,4H -> result_val[0]     | v7/A32/A64              |
| float128x8x3_t vld3q_f16(float16_t const * ptr) | ptr -> Xn            | LD3(Vt,8H-Vt,3,8H)[Xn]   | Vt,3,8H -> result_val[2]<br>Vt,2,8H -> result_val[1]<br>Vt,8H -> result_val[0]     | v7/A32/A64              |
| float32x2x3_t vld3_f32(float32_t const * ptr)   | ptr -> Xn            | LD3(Vt,2S-Vt,3,2S)[Xn]   | Vt,3,2S -> result_val[2]<br>Vt,2,2S -> result_val[1]<br>Vt,2S -> result_val[0]     | v7/A32/A64              |
| float32x4x3_t vld3q_f32(float32_t const * ptr)  | ptr -> Xn            | LD3(Vt,4S-Vt,3,4S)[Xn]   | Vt,3,4S -> result_val[2]<br>Vt,2,4S -> result_val[1]<br>Vt,4S -> result_val[0]     | v7/A32/A64              |

| Intrinsic                                      | Argument Preparation | Instruction               | Result                                                                       | Supported Architectures |
|------------------------------------------------|----------------------|---------------------------|------------------------------------------------------------------------------|-------------------------|
| poly8x8x3_t vld3_p8(poly8_t const * ptr)       | ptr -> Xn            | LD3 [Vt.8B - Vt.8B][Xn]   | Vt.8B -> resultval[2]<br>Vt.2.8B -> resultval[1]<br>Vt.8B -> resultval[0]    | v7/A32/A64              |
| poly8x16x3_t vld3q_p8(poly8_t const * ptr)     | ptr -> Xn            | LD3 [Vt.16B - Vt.16B][Xn] | Vt.16B -> resultval[2]<br>Vt.2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| poly16x4x3_t vld3_p16(poly16_t const * ptr)    | ptr -> Xn            | LD3 [Vt.4H - Vt.4H][Xn]   | Vt.3.4H -> resultval[2]<br>Vt.2.4H -> resultval[1]<br>Vt.4H -> resultval[0]  | v7/A32/A64              |
| poly16x8x3_t vld3q_p16(poly16_t const * ptr)   | ptr -> Xn            | LD3 [Vt.8H - Vt.8H][Xn]   | Vt.3.8H -> resultval[2]<br>Vt.2.8H -> resultval[1]<br>Vt.8H -> resultval[0]  | v7/A32/A64              |
| int64x4x3_t vld3_s64(int64_t const * ptr)      | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]  | v7/A32/A64              |
| uint64x4x3_t vld3_u64(uint64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]  | v7/A32/A64              |
| poly64x1x3_t vld3_p64(poly64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]  | A32/A64                 |
| int64x2x3_t vld3q_s64(int64_t const * ptr)     | ptr -> Xn            | LD3 [Vt.2D - Vt.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]  | A64                     |
| uint64x2x3_t vld3q_u64(uint64_t const * ptr)   | ptr -> Xn            | LD3 [Vt.2D - Vt.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]  | A64                     |
| poly64x2x3_t vld3q_p64(poly64_t const * ptr)   | ptr -> Xn            | LD3 [Vt.2D - Vt.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]  | A64                     |
| float64x1x3_t vld3_f64(float64_t const * ptr)  | ptr -> Xn            | LD1 [Vt.1D - Vt.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]  | A64                     |
| float64x2x3_t vld3q_f64(float64_t const * ptr) | ptr -> Xn            | LD3 [Vt.2D - Vt.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]  | A64                     |

| Intrinsic                                   | Argument Preparation | Instruction                | Result                                                                                                  | Supported Architectures |
|---------------------------------------------|----------------------|----------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| int8x8x4_t vld4_s8(int8_t const * ptr)      | ptr -> Xn            | LD4 [Vt.8B - Vt4.8B][Xn]   | Vt4.8B -> resultval[3]<br>Vt3.8B -> resultval[2]<br>Vt2.8B -> resultval[1]<br>Vt.8B -> resultval[0]     | v7/A32/A64              |
| int8x16x4_t vld4q_s8(int8_t const * ptr)    | ptr -> Xn            | LD4 [Vt.16B - Vt4.16B][Xn] | Vt4.16B -> resultval[3]<br>Vt3.16B -> resultval[2]<br>Vt2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| int16x4x4_t vld4_s16(int16_t const * ptr)   | ptr -> Xn            | LD4 [Vt.4H - Vt4.4H][Xn]   | Vt4.4H -> resultval[3]<br>Vt3.4H -> resultval[2]<br>Vt2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |
| int16x8x4_t vld4q_s16(int16_t const * ptr)  | ptr -> Xn            | LD4 [Vt.8H - Vt4.8H][Xn]   | Vt4.8H -> resultval[3]<br>Vt3.8H -> resultval[2]<br>Vt2.8H -> resultval[1]<br>Vt.8H -> resultval[0]     | v7/A32/A64              |
| int32x2x4_t vld4_s32(int32_t const * ptr)   | ptr -> Xn            | LD4 [Vt.2S - Vt4.2S][Xn]   | Vt4.2S -> resultval[3]<br>Vt3.2S -> resultval[2]<br>Vt2.2S -> resultval[1]<br>Vt.2S -> resultval[0]     | v7/A32/A64              |
| int32x4x4_t vld4q_s32(int32_t const * ptr)  | ptr -> Xn            | LD4 [Vt.4S - Vt4.4S][Xn]   | Vt4.4S -> resultval[3]<br>Vt3.4S -> resultval[2]<br>Vt2.4S -> resultval[1]<br>Vt.4S -> resultval[0]     | v7/A32/A64              |
| uint8x8x4_t vld4_u8(uint8_t const * ptr)    | ptr -> Xn            | LD4 [Vt.8B - Vt4.8B][Xn]   | Vt4.8B -> resultval[3]<br>Vt3.8B -> resultval[2]<br>Vt2.8B -> resultval[1]<br>Vt.8B -> resultval[0]     | v7/A32/A64              |
| uint8x16x4_t vld4q_u8(uint8_t const * ptr)  | ptr -> Xn            | LD4 [Vt.16B - Vt4.16B][Xn] | Vt4.16B -> resultval[3]<br>Vt3.16B -> resultval[2]<br>Vt2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| uint16x4x4_t vld4_u16(uint16_t const * ptr) | ptr -> Xn            | LD4 [Vt.4H - Vt4.4H][Xn]   | Vt4.4H -> resultval[3]<br>Vt3.4H -> resultval[2]<br>Vt2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |

| Intrinsic                                      | Argument Preparation | Instruction                | Result                                                                                                     | Supported Architectures |
|------------------------------------------------|----------------------|----------------------------|------------------------------------------------------------------------------------------------------------|-------------------------|
| uint16x8x4_t vld4q_u16(uint16_t const * ptr)   | ptr -> Xn            | LD4 [Vt.8H - Vt.8H],[Xn]   | Vt.8H -> resultval[3]<br>Vt.3.8H -> resultval[2]<br>Vt.2.8H -> resultval[1]<br>Vt.8H -> resultval[0]       | v7/A32/A64              |
| uint32x2x4_t vld4_u32(uint32_t const * ptr)    | ptr -> Xn            | LD4 [Vt.2S - Vt.2S],[Xn]   | Vt.4.2S -> resultval[3]<br>Vt.3.2S -> resultval[2]<br>Vt.2.2S -> resultval[1]<br>Vt.2S -> resultval[0]     | v7/A32/A64              |
| uint32x4x4_t vld4q_u32(uint32_t const * ptr)   | ptr -> Xn            | LD4 [Vt.4S - Vt.4S],[Xn]   | Vt.4.4S -> resultval[3]<br>Vt.3.4S -> resultval[2]<br>Vt.2.4S -> resultval[1]<br>Vt.4S -> resultval[0]     | v7/A32/A64              |
| float16x4x4_t vld4_f16(float16_t const * ptr)  | ptr -> Xn            | LD4 [Vt.4H - Vt.4H],[Xn]   | Vt.4.4H -> resultval[3]<br>Vt.3.4H -> resultval[2]<br>Vt.2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |
| float16x8x4_t vld4q_f16(float16_t const * ptr) | ptr -> Xn            | LD4 [Vt.8H - Vt.8H],[Xn]   | Vt.4.8H -> resultval[3]<br>Vt.3.8H -> resultval[2]<br>Vt.2.8H -> resultval[1]<br>Vt.8H -> resultval[0]     | v7/A32/A64              |
| float32x2x4_t vld4_f32(float32_t const * ptr)  | ptr -> Xn            | LD4 [Vt.2S - Vt.2S],[Xn]   | Vt.4.2S -> resultval[3]<br>Vt.3.2S -> resultval[2]<br>Vt.2.2S -> resultval[1]<br>Vt.2S -> resultval[0]     | v7/A32/A64              |
| float32x4x4_t vld4q_f32(float32_t const * ptr) | ptr -> Xn            | LD4 [Vt.4S - Vt.4S],[Xn]   | Vt.4.4S -> resultval[3]<br>Vt.3.4S -> resultval[2]<br>Vt.2.4S -> resultval[1]<br>Vt.4S -> resultval[0]     | v7/A32/A64              |
| poly8x8x4_t vld4_p8(poly8_t const * ptr)       | ptr -> Xn            | LD4 [Vt.8B - Vt.8B],[Xn]   | Vt.4.8B -> resultval[3]<br>Vt.3.8B -> resultval[2]<br>Vt.2.8B -> resultval[1]<br>Vt.8B -> resultval[0]     | v7/A32/A64              |
| poly8x16x4_t vld4q_p8(poly8_t const * ptr)     | ptr -> Xn            | LD4 [Vt.16B - Vt.16B],[Xn] | Vt.4.16B -> resultval[3]<br>Vt.3.16B -> resultval[2]<br>Vt.2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |

| Intrinsic                                     | Argument Preparation | Instruction               | Result                                                                                                     | Supported Architectures |
|-----------------------------------------------|----------------------|---------------------------|------------------------------------------------------------------------------------------------------------|-------------------------|
| poly16x4x4_t vld4_p16(poly16_t const * ptr)   | ptr -> Xn            | LD4 [Vt.4H - Vt.4H], [Xn] | Vt.4H -> result.val[3]<br>Vt.3.H -> result.val[2]<br>Vt.2.H -> result.val[1]<br>Vt.4H -> result.val[0]     | v7/A32/A64              |
| poly16x8x4_t vld4q_p16(poly16_t const * ptr)  | ptr -> Xn            | LD4 [Vt.8H - Vt.8H], [Xn] | Vt.4.H -> result.val[3]<br>Vt.3.H -> result.val[2]<br>Vt.2.H -> result.val[1]<br>Vt.8H -> result.val[0]    | v7/A32/A64              |
| int64x4x4_t vld4_s64(int64_t const * ptr)     | ptr -> Xn            | LD1 [Vt.1D - Vt.1D], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | v7/A32/A64              |
| uint64x4x4_t vld4_u64(uint64_t const * ptr)   | ptr -> Xn            | LD1 [Vt.1D - Vt.1D], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | v7/A32/A64              |
| poly64x4x4_t vld4_p64(poly64_t const * ptr)   | ptr -> Xn            | LD1 [Vt.1D - Vt.1D], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A32/A64                 |
| int64x2x4_t vld4q_s64(int64_t const * ptr)    | ptr -> Xn            | LD4 [Vt.2D - Vt.2D], [Xn] | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | A64                     |
| uint64x2x4_t vld4q_u64(uint64_t const * ptr)  | ptr -> Xn            | LD4 [Vt.2D - Vt.2D], [Xn] | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | A64                     |
| poly64x2x4_t vld4q_p64(poly64_t const * ptr)  | ptr -> Xn            | LD4 [Vt.2D - Vt.2D], [Xn] | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | A64                     |
| float64x4x4_t vld4_f64(float64_t const * ptr) | ptr -> Xn            | LD1 [Vt.1D - Vt.1D], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |

| Intrinsic                                        | Argument Preparation | Instruction                | Result                                                                                                  | Supported Architectures |
|--------------------------------------------------|----------------------|----------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| float64x2vd_1vd4q_f64(float64_1 const * ptr)     | ptr -> Xn            | LD4 [Vt.2D - Vt4.2D][Xn]   | Vt4.2D -> result_val[3]<br>Vt2.2D -> result_val[2]<br>Vt2.2D -> result_val[1]<br>Vt.2D -> result_val[0] | A64                     |
| int8x8x2_1vd4z_dup_s8(int8_1 const * ptr)        | ptr -> Xn            | LD2 [Vt.8B - Vt2.8B][Xn]   | Vt2.8B -> result_val[1]<br>Vt.8B -> result_val[0]                                                       | V7/A32/A64              |
| int8x16x2_1vd2q_dup_s8(int8_1 const * ptr)       | ptr -> Xn            | LD2 [Vt.16B - Vt2.16B][Xn] | Vt2.16B -> result_val[1]<br>Vt.16B -> result_val[0]                                                     | V7/A32/A64              |
| int16x4x2_1vd2q_dup_s16(int16_1 const * ptr)     | ptr -> Xn            | LD2 [Vt.4H - Vt2.4H][Xn]   | Vt2.4H -> result_val[1]<br>Vt.4H -> result_val[0]                                                       | V7/A32/A64              |
| int16x8x2_1vd2q_dup_s16(int16_1 const * ptr)     | ptr -> Xn            | LD2 [Vt.8H - Vt2.8H][Xn]   | Vt2.8H -> result_val[1]<br>Vt.8H -> result_val[0]                                                       | V7/A32/A64              |
| int32x2x2_1vd2q_dup_s32(int32_1 const * ptr)     | ptr -> Xn            | LD2 [Vt.2S - Vt2.2S][Xn]   | Vt2.2S -> result_val[1]<br>Vt.2S -> result_val[0]                                                       | V7/A32/A64              |
| int32x4x2_1vd2q_dup_s32(int32_1 const * ptr)     | ptr -> Xn            | LD2 [Vt.4S - Vt2.4S][Xn]   | Vt2.4S -> result_val[1]<br>Vt.4S -> result_val[0]                                                       | V7/A32/A64              |
| uint8x8x2_1vd2q_dup_u8(int8_1 const * ptr)       | ptr -> Xn            | LD2 [Vt.8B - Vt2.8B][Xn]   | Vt2.8B -> result_val[1]<br>Vt.8B -> result_val[0]                                                       | V7/A32/A64              |
| uint8x16x2_1vd2q_dup_u8(int8_1 const * ptr)      | ptr -> Xn            | LD2 [Vt.16B - Vt2.16B][Xn] | Vt2.16B -> result_val[1]<br>Vt.16B -> result_val[0]                                                     | V7/A32/A64              |
| uint16x4x2_1vd2q_dup_u16(uint16_1 const * ptr)   | ptr -> Xn            | LD2 [Vt.4H - Vt2.4H][Xn]   | Vt2.4H -> result_val[1]<br>Vt.4H -> result_val[0]                                                       | V7/A32/A64              |
| uint16x8x2_1vd2q_dup_u16(uint16_1 const * ptr)   | ptr -> Xn            | LD2 [Vt.8H - Vt2.8H][Xn]   | Vt2.8H -> result_val[1]<br>Vt.8H -> result_val[0]                                                       | V7/A32/A64              |
| uint32x2x2_1vd2q_dup_u32(uint32_1 const * ptr)   | ptr -> Xn            | LD2 [Vt.2S - Vt2.2S][Xn]   | Vt2.2S -> result_val[1]<br>Vt.2S -> result_val[0]                                                       | V7/A32/A64              |
| uint32x4x2_1vd2q_dup_u32(uint32_1 const * ptr)   | ptr -> Xn            | LD2 [Vt.4S - Vt2.4S][Xn]   | Vt2.4S -> result_val[1]<br>Vt.4S -> result_val[0]                                                       | V7/A32/A64              |
| float16x4x2_1vd2q_dup_f16(float16_1 const * ptr) | ptr -> Xn            | LD2 [Vt.4H - Vt2.4H][Xn]   | Vt2.4H -> result_val[1]<br>Vt.4H -> result_val[0]                                                       | V7/A32/A64              |
| float16x8x2_1vd2q_dup_f16(float16_1 const * ptr) | ptr -> Xn            | LD2 [Vt.8H - Vt2.8H][Xn]   | Vt2.8H -> result_val[1]<br>Vt.8H -> result_val[0]                                                       | V7/A32/A64              |
| float32x2x2_1vd2q_dup_f32(float32_1 const * ptr) | ptr -> Xn            | LD2 [Vt.2S - Vt2.2S][Xn]   | Vt2.2S -> result_val[1]<br>Vt.2S -> result_val[0]                                                       | V7/A32/A64              |
| float32x4x2_1vd2q_dup_f32(float32_1 const * ptr) | ptr -> Xn            | LD2 [Vt.4S - Vt2.4S][Xn]   | Vt2.4S -> result_val[1]<br>Vt.4S -> result_val[0]                                                       | V7/A32/A64              |

| Intrinsic                                          | Argument Preparation | Instruction                   | Result                                                                       | Supported Architectures |
|----------------------------------------------------|----------------------|-------------------------------|------------------------------------------------------------------------------|-------------------------|
| poly8x8x2_t vld2_dup_p8(poly8_t const * ptr)       | ptr -> Xn            | LD2R [Vt.8B - Vt.2.8B].[Xn]   | Vt.2.8B -> result[val[1] Vt.8B -> result[val[0]]                             | v7/A32/A64              |
| poly8x16x2_t vld2q_dup_p8(poly8_t const * ptr)     | ptr -> Xn            | LD2R [Vt.16B - Vt.2.16B].[Xn] | Vt.2.16B -> result[val[1] Vt.16B -> result[val[0]]                           | v7/A32/A64              |
| poly16x4x2_t vld2_dup_p16(poly16_t const * ptr)    | ptr -> Xn            | LD2R [Vt.4H - Vt.2.4H].[Xn]   | Vt.2.4H -> result[val[1] Vt.4H -> result[val[0]]                             | v7/A32/A64              |
| poly16x8x2_t vld2q_dup_p16(poly16_t const * ptr)   | ptr -> Xn            | LD2R [Vt.8H - Vt.2.8H].[Xn]   | Vt.2.8H -> result[val[1] Vt.8H -> result[val[0]]                             | v7/A32/A64              |
| int64x1x2_t vld2_dup_s64(int64_t const * ptr)      | ptr -> Xn            | LD2R [Vt.1D - Vt.2.1D].[Xn]   | Vt.2.1D -> result[val[1] Vt.1D -> result[val[0]]                             | v7/A32/A64              |
| uint64x1x2_t vld2_dup_u64(uint64_t const * ptr)    | ptr -> Xn            | LD2R [Vt.1D - Vt.2.1D].[Xn]   | Vt.2.1D -> result[val[1] Vt.1D -> result[val[0]]                             | v7/A32/A64              |
| poly64x1x2_t vld2_dup_p64(poly64_t const * ptr)    | ptr -> Xn            | LD2R [Vt.1D - Vt.2.1D].[Xn]   | Vt.2.1D -> result[val[1] Vt.1D -> result[val[0]]                             | A32/A64                 |
| int64x2x2_t vld2q_dup_s64(int64_t const * ptr)     | ptr -> Xn            | LD2R [Vt.2D - Vt.2.2D].[Xn]   | Vt.2.2D -> result[val[1] Vt.2D -> result[val[0]]                             | A64                     |
| uint64x2x2_t vld2q_dup_u64(uint64_t const * ptr)   | ptr -> Xn            | LD2R [Vt.2D - Vt.2.2D].[Xn]   | Vt.2.2D -> result[val[1] Vt.2D -> result[val[0]]                             | A64                     |
| poly64x2x2_t vld2q_dup_p64(poly64_t const * ptr)   | ptr -> Xn            | LD2R [Vt.2D - Vt.2.2D].[Xn]   | Vt.2.2D -> result[val[1] Vt.2D -> result[val[0]]                             | A64                     |
| float64x1x2_t vld2_dup_f64(float64_t const * ptr)  | ptr -> Xn            | LD2R [Vt.1D - Vt.2.1D].[Xn]   | Vt.2.1D -> result[val[1] Vt.1D -> result[val[0]]                             | A64                     |
| float64x2x2_t vld2q_dup_f64(float64_t const * ptr) | ptr -> Xn            | LD2R [Vt.2D - Vt.2.2D].[Xn]   | Vt.2.2D -> result[val[1] Vt.2D -> result[val[0]]                             | A64                     |
| int8x8x3_t vld3_dup_s8(int8_t const * ptr)         | ptr -> Xn            | LD3R [Vt.8B - Vt.3.8B].[Xn]   | Vt.3.8B -> result[val[2] Vt.2.8B -> result[val[1] Vt.8B -> result[val[0]]    | v7/A32/A64              |
| int8x16x3_t vld3q_dup_s8(int8_t const * ptr)       | ptr -> Xn            | LD3R [Vt.16B - Vt.3.16B].[Xn] | Vt.3.16B -> result[val[2] Vt.2.16B -> result[val[1] Vt.16B -> result[val[0]] | v7/A32/A64              |
| int16x4x3_t vld3_dup_s16(int16_t const * ptr)      | ptr -> Xn            | LD3R [Vt.4H - Vt.3.4H].[Xn]   | Vt.3.4H -> result[val[2] Vt.2.4H -> result[val[1] Vt.4H -> result[val[0]]    | v7/A32/A64              |
| int16x8x3_t vld3q_dup_s16(int16_t const * ptr)     | ptr -> Xn            | LD3R [Vt.8H - Vt.3.8H].[Xn]   | Vt.3.8H -> result[val[2] Vt.2.8H -> result[val[1] Vt.8H -> result[val[0]]    | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation | Instruction                | Result                                                                             | Supported Architectures |
|-------------------------------------------------------|----------------------|----------------------------|------------------------------------------------------------------------------------|-------------------------|
| int32x2x3_t vld3_dup_s32(uint32_t const * ptr)        | ptr -> Xn            | LD3R [VL2S - VL3.2S][Xn]   | VL3.2S -> result[val][2]<br>VL2.2S -> result[val][1]<br>VL.2S -> result[val][0]    | v7/A32/A64              |
| int32x4x3_t vld3q_dup_s32(uint32_t const * ptr)       | ptr -> Xn            | LD3R [VL4S - VL3.4S][Xn]   | VL3.4S -> result[val][2]<br>VL2.4S -> result[val][1]<br>VL.4S -> result[val][0]    | v7/A32/A64              |
| uint8x8x3_t vld3_dup_u8(uint8_t const * ptr)          | ptr -> Xn            | LD3R [VL8B - VL3.8B][Xn]   | VL3.8B -> result[val][2]<br>VL2.8B -> result[val][1]<br>VL.8B -> result[val][0]    | v7/A32/A64              |
| uint8x16x3_t vld3q_dup_u8(uint8_t const * ptr)        | ptr -> Xn            | LD3R [VL16B - VL3.16B][Xn] | VL3.16B -> result[val][2]<br>VL2.16B -> result[val][1]<br>VL.16B -> result[val][0] | v7/A32/A64              |
| uint16x4x3_t vld3_dup_u16(uint16_t const * ptr)       | ptr -> Xn            | LD3R [VL4H - VL3.4H][Xn]   | VL3.4H -> result[val][2]<br>VL2.4H -> result[val][1]<br>VL.4H -> result[val][0]    | v7/A32/A64              |
| uint16x8x3_t vld3q_dup_u16(uint16_t const * ptr)      | ptr -> Xn            | LD3R [VL8H - VL3.8H][Xn]   | VL3.8H -> result[val][2]<br>VL2.8H -> result[val][1]<br>VL.8H -> result[val][0]    | v7/A32/A64              |
| uint32x2x3_t vld3q_dup_u32(uint32_t const * ptr)      | ptr -> Xn            | LD3R [VL2S - VL3.2S][Xn]   | VL3.2S -> result[val][2]<br>VL2.2S -> result[val][1]<br>VL.2S -> result[val][0]    | v7/A32/A64              |
| uint32x4x3_t vld3qq_dup_u32(uint32_t const * ptr)     | ptr -> Xn            | LD3R [VL4S - VL3.4S][Xn]   | VL3.4S -> result[val][2]<br>VL2.4S -> result[val][1]<br>VL.4S -> result[val][0]    | v7/A32/A64              |
| float16x4x3_t vld3q_dup_f16(float16_t const * ptr)    | ptr -> Xn            | LD3R [VL4H - VL3.4H][Xn]   | VL3.4H -> result[val][2]<br>VL2.4H -> result[val][1]<br>VL.4H -> result[val][0]    | v7/A32/A64              |
| float16x8x3_t vld3qqq_dup_f16(float16_t const * ptr)  | ptr -> Xn            | LD3R [VL8H - VL3.8H][Xn]   | VL3.8H -> result[val][2]<br>VL2.8H -> result[val][1]<br>VL.8H -> result[val][0]    | v7/A32/A64              |
| float32x2x3_t vld3qq_dup_f32(float32_t const * ptr)   | ptr -> Xn            | LD3R [VL2S - VL3.2S][Xn]   | VL3.2S -> result[val][2]<br>VL2.2S -> result[val][1]<br>VL.2S -> result[val][0]    | v7/A32/A64              |
| float32x4x3_t vld3qqqq_dup_f32(float32_t const * ptr) | ptr -> Xn            | LD3R [VL4S - VL3.4S][Xn]   | VL3.4S -> result[val][2]<br>VL2.4S -> result[val][1]<br>VL.4S -> result[val][0]    | v7/A32/A64              |

| Intrinsic                                          | Argument Preparation | Instruction             | Result                                                                       | Supported Architectures |
|----------------------------------------------------|----------------------|-------------------------|------------------------------------------------------------------------------|-------------------------|
| poly8x8x3_t vld3_dup_p8(poly8_t const * ptr)       | ptr -> Xn            | LD3R [VL8B-VL38B][Xn]   | V138B -> result_val[2]<br>V228B -> result_val[1]<br>V168 -> result_val[0]    | v7/A32/A64              |
| poly8x16x3_t vld3q_dup_p8(poly8_t const * ptr)     | ptr -> Xn            | LD3R [VL16B-VL316B][Xn] | V1316B -> result_val[2]<br>V1216B -> result_val[1]<br>V116B -> result_val[0] | v7/A32/A64              |
| poly16x8x3_t vld3_dup_p16(poly16_t const * ptr)    | ptr -> Xn            | LD3R [VL8H-VL34H][Xn]   | V134H -> result_val[2]<br>V124H -> result_val[1]<br>V114H -> result_val[0]   | v7/A32/A64              |
| poly16x8x3_t vld3q_dup_p16(poly16_t const * ptr)   | ptr -> Xn            | LD3R [VL8H-VL38H][Xn]   | V138H -> result_val[2]<br>V128H -> result_val[1]<br>V118H -> result_val[0]   | v7/A32/A64              |
| int64x4x3_t vld3_dup_s64(int64_t const * ptr)      | ptr -> Xn            | LD3R [VL1D-VL31D][Xn]   | V131D -> result_val[2]<br>V121D -> result_val[1]<br>V11D -> result_val[0]    | v7/A32/A64              |
| uint64x4x3_t vld3_dup_u64(uint64_t const * ptr)    | ptr -> Xn            | LD3R [VL1D-VL31D][Xn]   | V131D -> result_val[2]<br>V121D -> result_val[1]<br>V11D -> result_val[0]    | v7/A32/A64              |
| poly64x1x3_t vld3_dup_p64(poly64_t const * ptr)    | ptr -> Xn            | LD3R [VL1D-VL31D][Xn]   | V131D -> result_val[2]<br>V121D -> result_val[1]<br>V11D -> result_val[0]    | A32/A64                 |
| int64x2x3_t vld3q_dup_s64(int64_t const * ptr)     | ptr -> Xn            | LD3R [VL2D-VL32D][Xn]   | V132D -> result_val[2]<br>V122D -> result_val[1]<br>V12D -> result_val[0]    | A64                     |
| uint64x2x3_t vld3q_dup_u64(uint64_t const * ptr)   | ptr -> Xn            | LD3R [VL2D-VL32D][Xn]   | V132D -> result_val[2]<br>V122D -> result_val[1]<br>V12D -> result_val[0]    | A64                     |
| poly64x2x3_t vld3q_dup_p64(poly64_t const * ptr)   | ptr -> Xn            | LD3R [VL2D-VL32D][Xn]   | V132D -> result_val[2]<br>V122D -> result_val[1]<br>V12D -> result_val[0]    | A64                     |
| float64x1x3_t vld3_dup_f64(float64_t const * ptr)  | ptr -> Xn            | LD3R [VL1D-VL31D][Xn]   | V131D -> result_val[2]<br>V121D -> result_val[1]<br>V11D -> result_val[0]    | A64                     |
| float64x2x3_t vld3q_dup_f64(float64_t const * ptr) | ptr -> Xn            | LD3R [VL2D-VL32D][Xn]   | V132D -> result_val[2]<br>V122D -> result_val[1]<br>V12D -> result_val[0]    | A64                     |

| Intrinsic                                       | Argument Preparation | Instruction                  | Result                                                                                                     | Supported Architectures |
|-------------------------------------------------|----------------------|------------------------------|------------------------------------------------------------------------------------------------------------|-------------------------|
| int8x8x4_t vld4_dup_s8(int8_t const * ptr)      | ptr -> Xn            | LD4R [Vt.8B - Vt.4.8B][Xn]   | Vt.4.8B -> resultval[3]<br>Vt.3.8B -> resultval[2]<br>Vt.2.8B -> resultval[1]<br>Vt.8B -> resultval[0]     | v7/A32/A64              |
| int8x16x4_t vld4q_dup_s8(int8_t const * ptr)    | ptr -> Xn            | LD4R [Vt.16B - Vt.4.16B][Xn] | Vt.4.16B -> resultval[3]<br>Vt.3.16B -> resultval[2]<br>Vt.2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| int16x4x4_t vld4_dup_s16(int16_t const * ptr)   | ptr -> Xn            | LD4R [Vt.4H - Vt.4.4H][Xn]   | Vt.4.4H -> resultval[3]<br>Vt.3.4H -> resultval[2]<br>Vt.2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |
| int16x8x4_t vld4q_dup_s16(int16_t const * ptr)  | ptr -> Xn            | LD4R [Vt.8H - Vt.4.8H][Xn]   | Vt.4.8H -> resultval[3]<br>Vt.3.8H -> resultval[2]<br>Vt.2.8H -> resultval[1]<br>Vt.8H -> resultval[0]     | v7/A32/A64              |
| int32x2x4_t vld4_dup_s32(int32_t const * ptr)   | ptr -> Xn            | LD4R [Vt.2S - Vt.4.2S][Xn]   | Vt.4.2S -> resultval[3]<br>Vt.3.2S -> resultval[2]<br>Vt.2.2S -> resultval[1]<br>Vt.2S -> resultval[0]     | v7/A32/A64              |
| int32x4x4_t vld4q_dup_s32(int32_t const * ptr)  | ptr -> Xn            | LD4R [Vt.4S - Vt.4.4S][Xn]   | Vt.4.4S -> resultval[3]<br>Vt.3.4S -> resultval[2]<br>Vt.2.4S -> resultval[1]<br>Vt.4S -> resultval[0]     | v7/A32/A64              |
| uint8x8x4_t vld4_dup_u8(uint8_t const * ptr)    | ptr -> Xn            | LD4R [Vt.8B - Vt.4.8B][Xn]   | Vt.4.8B -> resultval[3]<br>Vt.3.8B -> resultval[2]<br>Vt.2.8B -> resultval[1]<br>Vt.8B -> resultval[0]     | v7/A32/A64              |
| uint8x16x4_t vld4q_dup_u8(uint8_t const * ptr)  | ptr -> Xn            | LD4R [Vt.16B - Vt.4.16B][Xn] | Vt.4.16B -> resultval[3]<br>Vt.3.16B -> resultval[2]<br>Vt.2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| uint16x4x4_t vld4_dup_u16(uint16_t const * ptr) | ptr -> Xn            | LD4R [Vt.4H - Vt.4.4H][Xn]   | Vt.4.4H -> resultval[3]<br>Vt.3.4H -> resultval[2]<br>Vt.2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |

| Intrinsic                                          | Argument Preparation | Instruction                  | Result                                                                                                         | Supported Architectures |
|----------------------------------------------------|----------------------|------------------------------|----------------------------------------------------------------------------------------------------------------|-------------------------|
| uint16x8x4_t vld4q_dup_u16(uint16_t const * ptr)   | ptr -> Xn            | LD4R [Vt.8H - Vt.4.8H][Xn]   | Vt.4.8H -> result.val[3]<br>Vt.3.8H -> result.val[2]<br>Vt.2.8H -> result.val[1]<br>Vt.8H -> result.val[0]     | v7/A32/A64              |
| uint32x2x4_t vld4q_dup_u32(uint32_t const * ptr)   | ptr -> Xn            | LD4R [Vt.2S - Vt.4.2S][Xn]   | Vt.4.2S -> result.val[3]<br>Vt.3.2S -> result.val[2]<br>Vt.2.2S -> result.val[1]<br>Vt.2S -> result.val[0]     | v7/A32/A64              |
| uint32x4x4_t vld4q_dup_u32(uint32_t const * ptr)   | ptr -> Xn            | LD4R [Vt.4S - Vt.4.4S][Xn]   | Vt.4.4S -> result.val[3]<br>Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]     | v7/A32/A64              |
| float16x4x4_t vld4q_dup_f16(float16_t const * ptr) | ptr -> Xn            | LD4R [Vt.4H - Vt.4.4H][Xn]   | Vt.4.4H -> result.val[3]<br>Vt.3.4H -> result.val[2]<br>Vt.2.4H -> result.val[1]<br>Vt.4H -> result.val[0]     | v7/A32/A64              |
| float16x8x4_t vld4q_dup_f16(float16_t const * ptr) | ptr -> Xn            | LD4R [Vt.8H - Vt.4.8H][Xn]   | Vt.4.8H -> result.val[3]<br>Vt.3.8H -> result.val[2]<br>Vt.2.8H -> result.val[1]<br>Vt.8H -> result.val[0]     | v7/A32/A64              |
| float32x2x4_t vld4q_dup_f32(float32_t const * ptr) | ptr -> Xn            | LD4R [Vt.2S - Vt.4.2S][Xn]   | Vt.4.2S -> result.val[3]<br>Vt.3.2S -> result.val[2]<br>Vt.2.2S -> result.val[1]<br>Vt.2S -> result.val[0]     | v7/A32/A64              |
| float32x4x4_t vld4q_dup_f32(float32_t const * ptr) | ptr -> Xn            | LD4R [Vt.4S - Vt.4.4S][Xn]   | Vt.4.4S -> result.val[3]<br>Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]     | v7/A32/A64              |
| poly8x8x4_t vld4q_dup_p8(poly8_t const * ptr)      | ptr -> Xn            | LD4R [Vt.8B - Vt.4.8B][Xn]   | Vt.4.8B -> result.val[3]<br>Vt.3.8B -> result.val[2]<br>Vt.2.8B -> result.val[1]<br>Vt.8B -> result.val[0]     | v7/A32/A64              |
| poly8x16x4_t vld4q_dup_p8(poly8_t const * ptr)     | ptr -> Xn            | LD4R [Vt.16B - Vt.4.16B][Xn] | Vt.4.16B -> result.val[3]<br>Vt.3.16B -> result.val[2]<br>Vt.2.16B -> result.val[1]<br>Vt.16B -> result.val[0] | v7/A32/A64              |

| Intrinsic                                          | Argument Preparation | Instruction                  | Result                                                                                                           | Supported Architectures |
|----------------------------------------------------|----------------------|------------------------------|------------------------------------------------------------------------------------------------------------------|-------------------------|
| poly16x4x4_t vld4_dup_p16(poly16_t const * ptr)    | ptr -> Xn            | LD4R [Vt.4H - Vt.4.H];[Xn]   | Vt.4.H -> result.val[3]<br>Vt.3.H -> result.val[2]<br>Vt.2.H -> result.val[1]<br>Vt.1.H -> result.val[0]         | v7/A32/A64              |
| poly16x8x4_t vld4q_dup_p16(poly16_t const * ptr)   | ptr -> Xn            | LD4R [Vt.8H - Vt.4.8.H];[Xn] | Vt.4.8.H -> result.val[3]<br>Vt.3.8.H -> result.val[2]<br>Vt.2.8.H -> result.val[1]<br>Vt.1.8.H -> result.val[0] | v7/A32/A64              |
| int64x4x4_t vld4_dup_s64(int64_t const * ptr)      | ptr -> Xn            | LD4R [Vt.1D - Vt.4.1D];[Xn]  | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]       | v7/A32/A64              |
| uint64x4x4_t vld4q_dup_u64(uint64_t const * ptr)   | ptr -> Xn            | LD4R [Vt.1D - Vt.4.1D];[Xn]  | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]       | v7/A32/A64              |
| poly64x4x4_t vld4q_dup_p64(poly64_t const * ptr)   | ptr -> Xn            | LD4R [Vt.1D - Vt.4.1D];[Xn]  | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]       | A32/A64                 |
| int64x2x4_t vld4q_dup_s64(int64_t const * ptr)     | ptr -> Xn            | LD4R [Vt.2D - Vt.4.2D];[Xn]  | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0]       | A64                     |
| uint64x2x4_t vld4qq_dup_u64(uint64_t const * ptr)  | ptr -> Xn            | LD4R [Vt.2D - Vt.4.2D];[Xn]  | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0]       | A64                     |
| poly64x2x4_t vld4qq_dup_p64(poly64_t const * ptr)  | ptr -> Xn            | LD4R [Vt.2D - Vt.4.2D];[Xn]  | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0]       | A64                     |
| float64x4x4_t vld4q_dup_f64(float64_t const * ptr) | ptr -> Xn            | LD4R [Vt.1D - Vt.4.1D];[Xn]  | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]       | A64                     |

| Intrinsic                                    | Argument Preparation                                          | Instruction                 | Result                                                                                                   | Supported Architectures |
|----------------------------------------------|---------------------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------------------|-------------------------|
| float64x2v4_1v4dq_dup_16f4float64_1const_ptr | ptr -> Xn<br>ptr -> Xn<br>V1.8B                               | LD4R [V1.2D - V4.2D][Xn]    | V4.2D -> result[val][3]<br>V2.2D -> result[val][2]<br>V2.2D -> result[val][1]<br>V1.2D -> result[val][0] | A64                     |
| void vst2_88int8_1_ptr_int8x8x2_1val         | ptr -> Xn<br>val[val][1] -> V1.2B<br>val[val][0] -> V1.8B     | ST2 [V1.8B - V1.2B][Xn]     | void -> result                                                                                           | V7/A32/A64              |
| void vst2q_88int8_1_ptr_int8x16x2_1val       | ptr -> Xn<br>val[val][1] -> V1.2.16B<br>val[val][0] -> V1.16B | ST2 [V1.16B - V1.2.16B][Xn] | void -> result                                                                                           | V7/A32/A64              |
| void vst2_16int16_1_ptr_int16x4x2_1val       | ptr -> Xn<br>val[val][1] -> V1.2.4H<br>val[val][0] -> V1.4H   | ST2 [V1.4H - V1.2.4H][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2q_16int16_1_ptr_int16x8x2_1val      | ptr -> Xn<br>val[val][1] -> V1.2.8H<br>val[val][0] -> V1.8H   | ST2 [V1.8H - V1.2.8H][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2_32int32_1_ptr_int32x2x2_1val       | ptr -> Xn<br>val[val][1] -> V1.2.2S<br>val[val][0] -> V1.4S   | ST2 [V1.2S - V1.2.2S][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2q_32int32_1_ptr_int32x4x2_1val      | ptr -> Xn<br>val[val][1] -> V1.2.4S<br>val[val][0] -> V1.4S   | ST2 [V1.4S - V1.2.4S][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2_88uint8_1_ptr_uint8x8x2_1val       | ptr -> Xn<br>val[val][1] -> V1.2B<br>val[val][0] -> V1.8B     | ST2 [V1.8B - V1.2B][Xn]     | void -> result                                                                                           | V7/A32/A64              |
| void vst2q_88uint8_1_ptr_uint8x16x2_1val     | ptr -> Xn<br>val[val][1] -> V1.2.16B<br>val[val][0] -> V1.16B | ST2 [V1.16B - V1.2.16B][Xn] | void -> result                                                                                           | V7/A32/A64              |
| void vst2_16uint16_1_ptr_uint16x4x2_1val     | ptr -> Xn<br>val[val][1] -> V1.2.4H<br>val[val][0] -> V1.4H   | ST2 [V1.4H - V1.2.4H][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2q_16uint16_1_ptr_uint16x8x2_1val    | ptr -> Xn<br>val[val][1] -> V1.2.8H<br>val[val][0] -> V1.8H   | ST2 [V1.8H - V1.2.8H][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2_32uint32_1_ptr_uint32x2x2_1val     | ptr -> Xn<br>val[val][1] -> V1.2.2S<br>val[val][0] -> V1.4S   | ST2 [V1.2S - V1.2.2S][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2q_32uint32_1_ptr_uint32x4x2_1val    | ptr -> Xn<br>val[val][1] -> V1.2.4S<br>val[val][0] -> V1.4S   | ST2 [V1.4S - V1.2.4S][Xn]   | void -> result                                                                                           | V7/A32/A64              |
| void vst2_16float16_1_ptr_float16x4x2_1val   | ptr -> Xn<br>val[val][1] -> V1.2.4H<br>val[val][0] -> V1.4H   | ST2 [V1.4H - V1.2.4H][Xn]   | void -> result                                                                                           | V7/A32/A64              |

| Intrinsic                                          | Argument Preparation                                         | Instruction               | Result         | Supported Architectures |
|----------------------------------------------------|--------------------------------------------------------------|---------------------------|----------------|-------------------------|
| void vst2q_f16f(float16_t* ptr, float16x2x2_t val) | ptr -> Xn<br>val[all] -><br>V12.BH<br>val[all] -><br>V1.BH   | ST2(VL.BH - V12.BH)[Xn]   | void -> result | V7/A32/A64              |
| void vst2_f32f(float32_t* ptr, float32x2x2_t val)  | ptr -> Xn<br>val[all] -><br>V12.2S<br>val[all] -><br>V1.2S   | ST2(VL.2S - V12.2S)[Xn]   | void -> result | V7/A32/A64              |
| void vst2q_f32f(float32_t* ptr, float32x2x2_t val) | ptr -> Xn<br>val[all] -><br>V12.4S<br>val[all] -><br>V1.4S   | ST2(VL.4S - V12.4S)[Xn]   | void -> result | V7/A32/A64              |
| void vst2_p8f(poly8_t* ptr, poly8x2x2_t val)       | ptr -> Xn<br>val[all] -><br>V12.8B<br>val[all] -><br>V1.8B   | ST2(VL.8B - V12.8B)[Xn]   | void -> result | V7/A32/A64              |
| void vst2q_p8f(poly8_t* ptr, poly8x2x2_t val)      | ptr -> Xn<br>val[all] -><br>V12.16B<br>val[all] -><br>V1.16B | ST2(VL.16B - V12.16B)[Xn] | void -> result | V7/A32/A64              |
| void vst2_p16f(poly16_t* ptr, poly16x2x2_t val)    | ptr -> Xn<br>val[all] -><br>V12.4H<br>val[all] -><br>V1.4H   | ST2(VL.4H - V12.4H)[Xn]   | void -> result | V7/A32/A64              |
| void vst2q_p16f(poly16_t* ptr, poly16x2x2_t val)   | ptr -> Xn<br>val[all] -><br>V12.8H<br>val[all] -><br>V1.8H   | ST2(VL.8H - V12.8H)[Xn]   | void -> result | V7/A32/A64              |
| void vst2_s64(int64_t* ptr, int64x2x2_t val)       | ptr -> Xn<br>val[all] -><br>V12.1D<br>val[all] -><br>V1.1D   | ST1(VL.1D - V12.1D)[Xn]   | void -> result | V7/A32/A64              |
| void vst2_u64(uint64_t* ptr, uint64x2x2_t val)     | ptr -> Xn<br>val[all] -><br>V12.1D<br>val[all] -><br>V1.1D   | ST1(VL.1D - V12.1D)[Xn]   | void -> result | V7/A32/A64              |
| void vst2_p64(poly64_t* ptr, poly64x2x2_t val)     | ptr -> Xn<br>val[all] -><br>V12.1D<br>val[all] -><br>V1.1D   | ST1(VL.1D - V12.1D)[Xn]   | void -> result | A32/A64                 |
| void vst2q_s64(int64_t* ptr, int64x2x2_t val)      | ptr -> Xn<br>val[all] -><br>V12.2D<br>val[all] -><br>V1.2D   | ST2(VL.2D - V12.2D)[Xn]   | void -> result | A64                     |
| void vst2q_u64(uint64_t* ptr, uint64x2x2_t val)    | ptr -> Xn<br>val[all] -><br>V12.2D<br>val[all] -><br>V1.2D   | ST2(VL.2D - V12.2D)[Xn]   | void -> result | A64                     |
| void vst2q_p64(poly64_t* ptr, poly64x2x2_t val)    | ptr -> Xn<br>val[all] -><br>V12.2D<br>val[all] -><br>V1.2D   | ST2(VL.2D - V12.2D)[Xn]   | void -> result | A64                     |
| void vst2_f64f(float64_t* ptr, float64x2x2_t val)  | ptr -> Xn<br>val[all] -><br>V12.1D<br>val[all] -><br>V1.1D   | ST1(VL.1D - V12.1D)[Xn]   | void -> result | A64                     |

| Intrinsic                                         | Argument Preparation                                                                  | Instruction                  | Result         | Supported Architectures |
|---------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst2q_f64(float64_t* ptr, float64x2x2_t val) | ptr -> Xn<br>val.val[1] -> Vt.2D<br>val.val[0] -> Vt.2D                               | ST2 [Vt.2D - Vt.2D].[Xn]     | void -> result | A64                     |
| void vst3_s8(int8_t* ptr, int8x8x3_t val)         | ptr -> Xn<br>val.val[2] -> Vt.3BB<br>val.val[1] -> Vt.2BB<br>val.val[0] -> Vt.8B      | ST3 [Vt.8B - Vt.3BB].[Xn]    | void -> result | v7/A32/A64              |
| void vst3q_s8(int8_t* ptr, int8x16x3_t val)       | ptr -> Xn<br>val.val[2] -> Vt.3.16B<br>val.val[1] -> Vt.2.16B<br>val.val[0] -> Vt.4H  | ST3 [Vt.16B - Vt.3.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst3_s16(int16_t* ptr, int16x4x3_t val)      | ptr -> Xn<br>val.val[2] -> Vt.3.4H<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H    | ST3 [Vt.4H - Vt.3.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst3q_s16(int16_t* ptr, int16x8x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt.3.8H<br>val.val[1] -> Vt.2.8H<br>val.val[0] -> Vt.8H    | ST3 [Vt.8H - Vt.3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst3_s32(int32_t* ptr, int32x2x3_t val)      | ptr -> Xn<br>val.val[2] -> Vt.3.2S<br>val.val[1] -> Vt.2.2S<br>val.val[0] -> Vt.2S    | ST3 [Vt.2S - Vt.3.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst3q_s32(int32_t* ptr, int32x4x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt.3.4S<br>val.val[1] -> Vt.2.4S<br>val.val[0] -> Vt.4S    | ST3 [Vt.4S - Vt.3.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst3_u8(uint8_t* ptr, uint8x8x3_t val)       | ptr -> Xn<br>val.val[2] -> Vt.3BB<br>val.val[1] -> Vt.2BB<br>val.val[0] -> Vt.8B      | ST3 [Vt.8B - Vt.3BB].[Xn]    | void -> result | v7/A32/A64              |
| void vst3q_u8(uint8_t* ptr, uint8x16x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt.3.16B<br>val.val[1] -> Vt.2.16B<br>val.val[0] -> Vt.16B | ST3 [Vt.16B - Vt.3.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst3_u16(uint16_t* ptr, uint16x4x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt.3.4H<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H    | ST3 [Vt.4H - Vt.3.4H].[Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation                                                                  | Instruction                  | Result         | Supported Architectures |
|---------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst3q_u16(uint16_t* ptr, uint16x8x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt.3.8H<br>val.val[1] -> Vt.2.8H<br>val.val[0] -> Vt.8H    | ST3 [Vt.8H - Vt.3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst3_u32(uint32_t* ptr, uint32x2x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt.3.2S<br>val.val[1] -> Vt.2.2S<br>val.val[0] -> Vt.2S    | ST3 [Vt.2S - Vt.3.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst3q_u32(uint32_t* ptr, uint32x4x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt.3.4S<br>val.val[1] -> Vt.2.4S<br>val.val[0] -> Vt.4S    | ST3 [Vt.4S - Vt.3.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst3_f16(float16_t* ptr, float16x4x3_t val)  | ptr -> Xn<br>val.val[2] -> Vt.3.4H<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H    | ST3 [Vt.4H - Vt.3.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst3q_f16(float16_t* ptr, float16x8x3_t val) | ptr -> Xn<br>val.val[2] -> Vt.3.8H<br>val.val[1] -> Vt.2.8H<br>val.val[0] -> Vt.8H    | ST3 [Vt.8H - Vt.3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst3_f32(float32_t* ptr, float32x2x3_t val)  | ptr -> Xn<br>val.val[2] -> Vt.3.2S<br>val.val[1] -> Vt.2.2S<br>val.val[0] -> Vt.2S    | ST3 [Vt.2S - Vt.3.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst3q_f32(float32_t* ptr, float32x4x3_t val) | ptr -> Xn<br>val.val[2] -> Vt.3.4S<br>val.val[1] -> Vt.2.4S<br>val.val[0] -> Vt.4S    | ST3 [Vt.4S - Vt.3.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst3_p8(poly8_t* ptr, poly8x8x3_t val)       | ptr -> Xn<br>val.val[2] -> Vt.3.8B<br>val.val[1] -> Vt.2.8B<br>val.val[0] -> Vt.8B    | ST3 [Vt.8B - Vt.3.8B].[Xn]   | void -> result | v7/A32/A64              |
| void vst3q_p8(poly8_t* ptr, poly8x16x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt.3.16B<br>val.val[1] -> Vt.2.16B<br>val.val[0] -> Vt.16B | ST3 [Vt.16B - Vt.3.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst3_p16(poly16_t* ptr, poly16x4x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt.3.4H<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H    | ST3 [Vt.4H - Vt.3.4H].[Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                          | Argument Preparation                                                                                                  | Instruction             | Result         | Supported Architectures |
|----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|-------------------------|----------------|-------------------------|
| void vst3q_p16(poly16_1*, ptr, poly16x3_1 val)     | ptr -> Xn<br>val[val][2] -><br>V13.BH<br>val[val][1] -><br>V12.BH<br>val[val][0] -><br>V1.BH                          | ST3[VL.BH - VL3.BH][Xn] | void -> result | V7/A32/A64              |
| void vst3_s4(int64_1*, ptr, int64x3_1 val)         | ptr -> Xn<br>val[val][2] -><br>V3.1D<br>val[val][1] -><br>V2.1D<br>val[val][0] -><br>V1.1D                            | ST1[VL.1D - VL3.1D][Xn] | void -> result | V7/A32/A64              |
| void vst3_u64(uint64_1*, ptr, uint64x3_1 val)      | ptr -> Xn<br>val[val][2] -><br>V3.1D<br>val[val][1] -><br>V2.1D<br>val[val][0] -><br>V1.1D                            | ST1[VL.1D - VL3.1D][Xn] | void -> result | V7/A32/A64              |
| void vst3_p64(poly64_1*, ptr, poly64x3_1 val)      | ptr -> Xn<br>val[val][2] -><br>V3.1D<br>val[val][1] -><br>V2.1D<br>val[val][0] -><br>V1.1D                            | ST1[VL.1D - VL3.1D][Xn] | void -> result | A32/A64                 |
| void vst3q_s64(int64_1*, ptr, int64x2x3_1 val)     | ptr -> Xn<br>val[val][2] -><br>V3.2D<br>val[val][1] -><br>V1.2D<br>val[val][0] -><br>V1.2D                            | ST3[VL.2D - VL3.2D][Xn] | void -> result | A64                     |
| void vst3q_u64(uint64_1*, ptr, uint64x2x3_1 val)   | ptr -> Xn<br>val[val][2] -><br>V3.2D<br>val[val][1] -><br>V2.2D<br>val[val][0] -><br>V1.2D                            | ST3[VL.2D - VL3.2D][Xn] | void -> result | A64                     |
| void vst3q_p64(poly64_1*, ptr, poly64x2x3_1 val)   | ptr -> Xn<br>val[val][2] -><br>V3.2D<br>val[val][1] -><br>V2.2D<br>val[val][0] -><br>V1.2D                            | ST3[VL.2D - VL3.2D][Xn] | void -> result | A64                     |
| void vst3_f64(float64_1*, ptr, float64x3_1 val)    | ptr -> Xn<br>val[val][2] -><br>V3.1D<br>val[val][1] -><br>V2.1D<br>val[val][0] -><br>V1.1D                            | ST1[VL.1D - VL3.1D][Xn] | void -> result | A64                     |
| void vst3q_f64(float64_1*, ptr, float64x2x3_1 val) | ptr -> Xn<br>val[val][2] -><br>V3.2D<br>val[val][1] -><br>V2.2D<br>val[val][0] -><br>V1.2D                            | ST3[VL.2D - VL3.2D][Xn] | void -> result | A64                     |
| void vst4_s8(int8_1*, ptr, int8x4_1 val)           | ptr -> Xn<br>val[val][3] -><br>V4.BB<br>val[val][2] -><br>V3.BB<br>val[val][1] -><br>V2.BB<br>val[val][0] -><br>V1.BB | ST4[VL.BB - VL4.BB][Xn] | void -> result | V7/A32/A64              |

| Intrinsic                                      | Argument Preparation                                                                                         | Instruction                 | Result         | Supported Architectures |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst4q_s8(int8_t* ptr, int8x16x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B | ST4 [Vt.16B - Vt4.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst4_s16(int16_t* ptr, int16x4x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H     | ST4 [Vt.4H - Vt4.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst4q_s16(int16_t* ptr, int16x8x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H     | ST4 [Vt.8H - Vt4.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst4_s32(int32_t* ptr, int32x2x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S     | ST4 [Vt.2S - Vt4.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst4q_s32(int32_t* ptr, int32x4x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S     | ST4 [Vt.4S - Vt4.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst4_u8(uint8_t* ptr, uint8x8x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.8B<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt.8B     | ST4 [Vt.8B - Vt4.8B].[Xn]   | void -> result | v7/A32/A64              |
| void vst4q_u8(uint8_t* ptr, uint8x16x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B | ST4 [Vt.16B - Vt4.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst4_u16(uint16_t* ptr, uint16x4x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H     | ST4 [Vt.4H - Vt4.4H].[Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation                                                                                     | Instruction               | Result         | Supported Architectures |
|---------------------------------------------------|----------------------------------------------------------------------------------------------------------|---------------------------|----------------|-------------------------|
| void vst4q_u16(uint16_t* ptr, uint16x8x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H | ST4 [Vt.8H - Vt4.8H].[Xn] | void -> result | v7/A32/A64              |
| void vst4_u32(uint32_t* ptr, uint32x2x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S | ST4 [Vt.2S - Vt4.2S].[Xn] | void -> result | v7/A32/A64              |
| void vst4q_u32(uint32_t* ptr, uint32x4x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S | ST4 [Vt.4S - Vt4.4S].[Xn] | void -> result | v7/A32/A64              |
| void vst4_f16(float16_t* ptr, float16x4x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H | ST4 [Vt.4H - Vt4.4H].[Xn] | void -> result | v7/A32/A64              |
| void vst4q_f16(float16_t* ptr, float16x8x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H | ST4 [Vt.8H - Vt4.8H].[Xn] | void -> result | v7/A32/A64              |
| void vst4_f32(float32_t* ptr, float32x2x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S | ST4 [Vt.2S - Vt4.2S].[Xn] | void -> result | v7/A32/A64              |
| void vst4q_f32(float32_t* ptr, float32x4x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S | ST4 [Vt.4S - Vt4.4S].[Xn] | void -> result | v7/A32/A64              |
| void vst4_p8(poly8_t* ptr, poly8x8x4_t val)       | ptr -> Xn<br>val.val[3] -> Vt4.8B<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt.8B | ST4 [Vt.8B - Vt4.8B].[Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                       | Argument Preparation                                                                                         | Instruction                 | Result         | Supported Architectures |
|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst4q_p8(poly8_t* ptr, poly8x16x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B | ST4 [Vt.16B - Vt4.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst4_p16(poly16_t* ptr, poly16x4x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H     | ST4 [Vt.4H - Vt4.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst4q_p16(poly16_t* ptr, poly16x8x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H     | ST4 [Vt.8H - Vt4.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst4_s64(int64_t* ptr, int64x1x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D     | ST1 [Vt.1D - Vt4.1D].[Xn]   | void -> result | v7/A32/A64              |
| void vst4_u64(uint64_t* ptr, uint64x1x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D     | ST1 [Vt.1D - Vt4.1D].[Xn]   | void -> result | v7/A32/A64              |
| void vst4_p64(poly64_t* ptr, poly64x1x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D     | ST1 [Vt.1D - Vt4.1D].[Xn]   | void -> result | A32/A64                 |
| void vst4q_s64(int64_t* ptr, int64x2x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D     | ST4 [Vt.2D - Vt4.2D].[Xn]   | void -> result | A64                     |
| void vst4q_u64(uint64_t* ptr, uint64x2x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D     | ST4 [Vt.2D - Vt4.2D].[Xn]   | void -> result | A64                     |

| Intrinsic                                                                           | Argument Preparation                                                                                     | Instruction                  | Result                                            | Supported Architectures |
|-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|------------------------------|---------------------------------------------------|-------------------------|
| void vst4q_p64(poly64_t * ptr, poly64x2x4_t val)                                    | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D | ST4 [Vt.2D - Vt4.2D][Xn]     | void -> result                                    | A64                     |
| void vst4_f64(float64_t * ptr, float64x1x4_t val)                                   | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D | ST1 [Vt.1D - Vt4.1D][Xn]     | void -> result                                    | A64                     |
| void vst4q_f64(float64_t * ptr, float64x2x4_t val)                                  | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D | ST4 [Vt.2D - Vt4.2D][Xn]     | void -> result                                    | A64                     |
| int16x4x2_t vld2_lane_s16(int16_t const * ptr, int16x4x2_t src, const int lane)     | ptr -> Xn<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3                               | LD2 [Vt.h - Vt2.h][lane][Xn] | Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| int16x8x2_t vld2q_lane_s16(int16_t const * ptr, int16x8x2_t src, const int lane)    | ptr -> Xn<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7                               | LD2 [Vt.h - Vt2.h][lane][Xn] | Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| int32x2x2_t vld2_lane_s32(int32_t const * ptr, int32x2x2_t src, const int lane)     | ptr -> Xn<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 1                               | LD2 [Vt.s - Vt2.s][lane][Xn] | Vt2.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| int32x4x2_t vld2q_lane_s32(int32_t const * ptr, int32x4x2_t src, const int lane)    | ptr -> Xn<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3                               | LD2 [Vt.s - Vt2.s][lane][Xn] | Vt2.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| uint16x4x2_t vld2_lane_u16(uint16_t const * ptr, uint16x4x2_t src, const int lane)  | ptr -> Xn<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3                               | LD2 [Vt.h - Vt2.h][lane][Xn] | Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| uint16x8x2_t vld2q_lane_u16(uint16_t const * ptr, uint16x8x2_t src, const int lane) | ptr -> Xn<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7                               | LD2 [Vt.h - Vt2.h][lane][Xn] | Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |

| Intrinsic                                                                              | Argument Preparation                                                      | Instruction                   | Result                                           | Supported Architectures |
|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------|--------------------------------------------------|-------------------------|
| uint32x2x2_t vld2_lane_u32(uint32_t const * ptr, uint32x2x2_t src, const int lane)     | ptr -> Xn<br>src.val[1] -> Vt.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 1 | LD2 [Vt.s - Vt.2.s][lane][Xn] | Vt.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| uint32x4x2_t vld2q_lane_u32(uint32_t const * ptr, uint32x4x2_t src, const int lane)    | ptr -> Xn<br>src.val[1] -> Vt.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD2 [Vt.s - Vt.2.s][lane][Xn] | Vt.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| float16x4x2_t vld2_lane_f16(float16_t const * ptr, float16x4x2_t src, const int lane)  | ptr -> Xn<br>src.val[1] -> Vt.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD2 [Vt.h - Vt.2.h][lane][Xn] | Vt.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| float16x8x2_t vld2q_lane_f16(float16_t const * ptr, float16x8x2_t src, const int lane) | ptr -> Xn<br>src.val[1] -> Vt.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD2 [Vt.h - Vt.2.h][lane][Xn] | Vt.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| float32x2x2_t vld2_lane_f32(float32_t const * ptr, float32x2x2_t src, const int lane)  | ptr -> Xn<br>src.val[1] -> Vt.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 1 | LD2 [Vt.s - Vt.2.s][lane][Xn] | Vt.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| float32x4x2_t vld2q_lane_f32(float32_t const * ptr, float32x4x2_t src, const int lane) | ptr -> Xn<br>src.val[1] -> Vt.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD2 [Vt.s - Vt.2.s][lane][Xn] | Vt.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| poly16x4x2_t vld2_lane_p16(poly16_t const * ptr, poly16x4x2_t src, const int lane)     | ptr -> Xn<br>src.val[1] -> Vt.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD2 [Vt.h - Vt.2.h][lane][Xn] | Vt.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| poly16x8x2_t vld2q_lane_p16(poly16_t const * ptr, poly16x8x2_t src, const int lane)    | ptr -> Xn<br>src.val[1] -> Vt.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD2 [Vt.h - Vt.2.h][lane][Xn] | Vt.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| int8x8x2_t vld2_lane_s8(int8_t const * ptr, int8x8x2_t src, const int lane)            | ptr -> Xn<br>src.val[1] -> Vt.8B<br>src.val[0] -> Vt.8B<br>0 <= lane <= 7 | LD2 [Vt.b - Vt.2.b][lane][Xn] | Vt.8B -> result.val[1]<br>Vt.8B -> result.val[0] | v7/A32/A64              |
| uint8x8x2_t vld2_lane_u8(uint8_t const * ptr, uint8x8x2_t src, const int lane)         | ptr -> Xn<br>src.val[1] -> Vt.8B<br>src.val[0] -> Vt.8B<br>0 <= lane <= 7 | LD2 [Vt.b - Vt.2.b][lane][Xn] | Vt.8B -> result.val[1]<br>Vt.8B -> result.val[0] | v7/A32/A64              |

| Intrinsic                                                                             | Argument Preparation                                                           | Instruction                     | Result                                                          | Supported Architectures |
|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|---------------------------------|-----------------------------------------------------------------|-------------------------|
| poly8x8x2_t vld2_lane_p8(poly8_t const * ptr, poly8x8x2_t src, const int lane)        | ptr -> Xn<br>src.val[1] -> Vt.2.BB<br>src.val[0] -> Vt.8B<br>0 <= lane <= 7    | LD2 [Vt.b - Vt.2.b][lane], [Xn] | Vt.2.BB -> result.val[1]<br>Vt.8B -> result.val[0]              | v7/A32/A64              |
| int8x16x2_t vld2q_lane_s8(int8_t const * ptr, int8x16x2_t src, const int lane)        | ptr -> Xn<br>src.val[1] -> Vt.2.16B<br>src.val[0] -> Vt.16B<br>0 <= lane <= 15 | LD2 [Vt.b - Vt.2.b][lane], [Xn] | Vt.2.16B -> result.val[1]<br>Vt.16B -> result.val[0]            | A64                     |
| uint8x16x2_t vld2q_lane_u8(uint8_t const * ptr, uint8x16x2_t src, const int lane)     | ptr -> Xn<br>src.val[1] -> Vt.2.16B<br>src.val[0] -> Vt.16B<br>0 <= lane <= 15 | LD2 [Vt.b - Vt.2.b][lane], [Xn] | Vt.2.16B -> result.val[1]<br>Vt.16B -> result.val[0]            | A64                     |
| poly8x16x2_t vld2q_lane_p8(poly8_t const * ptr, poly8x16x2_t src, const int lane)     | ptr -> Xn<br>src.val[1] -> Vt.2.16B<br>src.val[0] -> Vt.16B<br>0 <= lane <= 15 | LD2 [Vt.b - Vt.2.b][lane], [Xn] | Vt.2.16B -> result.val[1]<br>Vt.16B -> result.val[0]            | A64                     |
| int64x1x2_t vld2_lane_s64(int64_t const * ptr, int64x1x2_t src, const int lane)       | ptr -> Xn<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0         | LD2 [Vt.d - Vt.2.d][lane], [Xn] | ptr -> Xn<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| int64x2x2_t vld2q_lane_s64(int64_t const * ptr, int64x2x2_t src, const int lane)      | ptr -> Xn<br>src.val[1] -> Vt.2.2D<br>src.val[0] -> Vt.2D<br>0 <= lane <= 1    | LD2 [Vt.d - Vt.2.d][lane], [Xn] | ptr -> Xn<br>Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | A64                     |
| uint64x1x2_t vld2_lane_u64(uint64_t const * ptr, uint64x1x2_t src, const int lane)    | ptr -> Xn<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0         | LD2 [Vt.d - Vt.2.d][lane], [Xn] | Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]              | A64                     |
| uint64x2x2_t vld2q_lane_u64(uint64_t const * ptr, uint64x2x2_t src, const int lane)   | ptr -> Xn<br>src.val[1] -> Vt.2.2D<br>src.val[0] -> Vt.2D<br>0 <= lane <= 1    | LD2 [Vt.d - Vt.2.d][lane], [Xn] | Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0]              | A64                     |
| poly64x1x2_t vld2_lane_p64(poly64_t const * ptr, poly64x1x2_t src, const int lane)    | ptr -> Xn<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0         | LD2 [Vt.d - Vt.2.d][lane], [Xn] | Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]              | A64                     |
| poly64x2x2_t vld2q_lane_p64(poly64_t const * ptr, poly64x2x2_t src, const int lane)   | ptr -> Xn<br>src.val[1] -> Vt.2.2D<br>src.val[0] -> Vt.2D<br>0 <= lane <= 1    | LD2 [Vt.d - Vt.2.d][lane], [Xn] | Vt.2.2D -> result.val[1]<br>Vt.2D -> result.val[0]              | A64                     |
| float64x1x2_t vld2_lane_f64(float64_t const * ptr, float64x1x2_t src, const int lane) | ptr -> Xn<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0         | LD2 [Vt.d - Vt.2.d][lane], [Xn] | Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0]              | A64                     |

| Intrinsic                                                                              | Argument Preparation                                                                               | Instruction                    | Result                                                                       | Supported Architectures |
|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------|------------------------------------------------------------------------------|-------------------------|
| float64x2x2_t vld2q_lane_f64(float64_t const * ptr, float64x2x2_t src, const int lane) | ptr -> Xn<br>src.val[1] -> Vt2.2D<br>src.val[0] -> Vt2D<br>0 <= lane <= 1                          | LD2 [Vt.d - Vt2.d][lane], [Xn] | Vt2.2D -> result.val[1]<br>Vt2D -> result.val[0]                             | A64                     |
| int16x4x3_t vld3_lane_s16(int16_t const * ptr, int16x4x3_t src, const int lane)        | ptr -> Xn<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD3 [Vt.h - Vt3.h][lane], [Xn] | Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| int16x8x3_t vld3q_lane_s16(int16_t const * ptr, int16x8x3_t src, const int lane)       | ptr -> Xn<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD3 [Vt.h - Vt3.h][lane], [Xn] | Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| int32x2x3_t vld3_lane_s32(int32_t const * ptr, int32x2x3_t src, const int lane)        | ptr -> Xn<br>src.val[2] -> Vt3.2S<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 1 | LD3 [Vt.s - Vt3.s][lane], [Xn] | Vt3.2S -> result.val[2]<br>Vt2.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| int32x4x3_t vld3q_lane_s32(int32_t const * ptr, int32x4x3_t src, const int lane)       | ptr -> Xn<br>src.val[2] -> Vt3.4S<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD3 [Vt.s - Vt3.s][lane], [Xn] | Vt3.4S -> result.val[2]<br>Vt2.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| uint16x4x3_t vld3_lane_u16(uint16_t const * ptr, uint16x4x3_t src, const int lane)     | ptr -> Xn<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD3 [Vt.h - Vt3.h][lane], [Xn] | Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| uint16x8x3_t vld3q_lane_u16(uint16_t const * ptr, uint16x8x3_t src, const int lane)    | ptr -> Xn<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD3 [Vt.h - Vt3.h][lane], [Xn] | Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| uint32x2x3_t vld3_lane_u32(uint32_t const * ptr, uint32x2x3_t src, const int lane)     | ptr -> Xn<br>src.val[2] -> Vt3.2S<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 1 | LD3 [Vt.s - Vt3.s][lane], [Xn] | Vt3.2S -> result.val[2]<br>Vt2.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |

| Intrinsic                                                                              | Argument Preparation                                                                               | Instruction                  | Result                                                                       | Supported Architectures |
|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|------------------------------|------------------------------------------------------------------------------|-------------------------|
| uint32x4x3_t vld3q_lane_u32(uint32_t const * ptr, uint32x4x3_t src, const int lane)    | ptr -> Xn<br>src.val[2] -> Vt3.4S<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD3 [Vt.s - Vt3.s][lane][Xn] | Vt3.4S -> result.val[2]<br>Vt2.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| float16x4x3_t vld3_lane_f16(float16_t const * ptr, float16x4x3_t src, const int lane)  | ptr -> Xn<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD3 [Vt.h - Vt3.h][lane][Xn] | Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| float16x8x3_t vld3q_lane_f16(float16_t const * ptr, float16x8x3_t src, const int lane) | ptr -> Xn<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD3 [Vt.h - Vt3.h][lane][Xn] | Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| float32x2x3_t vld3_lane_f32(float32_t const * ptr, float32x2x3_t src, const int lane)  | ptr -> Xn<br>src.val[2] -> Vt3.2S<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 1 | LD3 [Vt.s - Vt3.s][lane][Xn] | Vt3.2S -> result.val[2]<br>Vt2.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| float32x4x3_t vld3q_lane_f32(float32_t const * ptr, float32x4x3_t src, const int lane) | ptr -> Xn<br>src.val[2] -> Vt3.4S<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD3 [Vt.s - Vt3.s][lane][Xn] | Vt3.4S -> result.val[2]<br>Vt2.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| poly16x4x3_t vld3_lane_p16(poly16_t const * ptr, poly16x4x3_t src, const int lane)     | ptr -> Xn<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD3 [Vt.h - Vt3.h][lane][Xn] | Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| poly16x8x3_t vld3q_lane_p16(poly16_t const * ptr, poly16x8x3_t src, const int lane)    | ptr -> Xn<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD3 [Vt.h - Vt3.h][lane][Xn] | Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| int8x8x3_t vld3_lane_s8(int8_t const * ptr, int8x8x3_t src, const int lane)            | ptr -> Xn<br>src.val[2] -> Vt3.8B<br>src.val[1] -> Vt2.8B<br>src.val[0] -> Vt.8B<br>0 <= lane <= 7 | LD3 [Vt.b - Vt3.b][lane][Xn] | Vt3.8B -> result.val[2]<br>Vt2.8B -> result.val[1]<br>Vt.8B -> result.val[0] | v7/A32/A64              |

| Intrinsic                                                                              | Argument Preparation                                                                                   | Instruction                    | Result                                                                          | Supported Architectures |
|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|--------------------------------|---------------------------------------------------------------------------------|-------------------------|
| uint8x8x3_t vld3_lane_u8(uint8_t const * ptr, uint8x8x3_t src, const int lane)         | ptr -> Xn<br>src.val[2] -> Vt3.BB<br>src.val[1] -> Vt2.BB<br>src.val[0] -> Vt.BB<br>0 <= lane <= 7     | LD3 {Vt.b - Vt3.b}[lane], [Xn] | Vt3.BB -> result.val[2]<br>Vt2.BB -> result.val[1]<br>Vt.BB -> result.val[0]    | v7/A32/A64              |
| poly8x8x3_t vld3_lane_p8(poly8_t const * ptr, poly8x8x3_t src, const int lane)         | ptr -> Xn<br>src.val[2] -> Vt3.BB<br>src.val[1] -> Vt2.BB<br>src.val[0] -> Vt.BB<br>0 <= lane <= 7     | LD3 {Vt.b - Vt3.b}[lane], [Xn] | Vt3.BB -> result.val[2]<br>Vt2.BB -> result.val[1]<br>Vt.BB -> result.val[0]    | v7/A32/A64              |
| int8x16x3_t vld3q_lane_s8(int8_t const * ptr, int8x16x3_t src, const int lane)         | ptr -> Xn<br>src.val[2] -> Vt3.16B<br>src.val[1] -> Vt2.16B<br>src.val[0] -> Vt.16B<br>0 <= lane <= 15 | LD3 {Vt.b - Vt3.b}[lane], [Xn] | Vt3.16B -> result.val[2]<br>Vt2.16B -> result.val[1]<br>Vt.16B -> result.val[0] | A64                     |
| uint8x16x3_t vld3q_lane_u8(uint8_t const * ptr, uint8x16x3_t src, const int lane)      | ptr -> Xn<br>src.val[2] -> Vt3.16B<br>src.val[1] -> Vt2.16B<br>src.val[0] -> Vt.16B<br>0 <= lane <= 15 | LD3 {Vt.b - Vt3.b}[lane], [Xn] | Vt3.16B -> result.val[2]<br>Vt2.16B -> result.val[1]<br>Vt.16B -> result.val[0] | A64                     |
| poly8x16x3_t vld3q_lane_p8(poly8_t const * ptr, poly8x16x3_t src, const int lane)      | ptr -> Xn<br>src.val[2] -> Vt3.16B<br>src.val[1] -> Vt2.16B<br>src.val[0] -> Vt.16B<br>0 <= lane <= 15 | LD3 {Vt.b - Vt3.b}[lane], [Xn] | Vt3.16B -> result.val[2]<br>Vt2.16B -> result.val[1]<br>Vt.16B -> result.val[0] | A64                     |
| int64x4x3_t vld3_lane_s64(int64_t const * ptr, int64x4x3_t src, const int lane)        | ptr -> Xn<br>src.val[2] -> Vt3.1D<br>src.val[1] -> Vt2.1D<br>src.val[0] -> Vt.1D<br>lane == 0          | LD3 {Vt.d - Vt3.d}[lane], [Xn] | Vt3.1D -> result.val[2]<br>Vt2.1D -> result.val[1]<br>Vt.1D -> result.val[0]    | A64                     |
| int64x4x2x3_t vld3q_lane_s64(int64_t const * ptr, int64x4x2x3_t src, const int lane)   | ptr -> Xn<br>src.val[2] -> Vt3.2D<br>src.val[1] -> Vt2.2D<br>src.val[0] -> Vt.2D<br>0 <= lane <= 1     | LD3 {Vt.d - Vt3.d}[lane], [Xn] | Vt3.2D -> result.val[2]<br>Vt2.2D -> result.val[1]<br>Vt.2D -> result.val[0]    | A64                     |
| uint64x4x1x3_t vld3_lane_u64(uint64_t const * ptr, uint64x4x1x3_t src, const int lane) | ptr -> Xn<br>src.val[2] -> Vt3.1D<br>src.val[1] -> Vt2.1D<br>src.val[0] -> Vt.1D<br>lane == 0          | LD3 {Vt.d - Vt3.d}[lane], [Xn] | Vt3.1D -> result.val[2]<br>Vt2.1D -> result.val[1]<br>Vt.1D -> result.val[0]    | A64                     |

| Intrinsic                                                                              | Argument Preparation                                                                                                        | Instruction                    | Result                                                                                               | Supported Architectures |
|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------------------------------------------------------------------------------------------------|-------------------------|
| uint64x2x3_t vld3_lane_u64(uint64_t const * ptr, uint64x2x3_t src, const int lane)     | ptr -> Xn<br>src.val[2] -> Vt3.2D<br>src.val[1] -> Vt2.2D<br>src.val[0] -> Vt1.2D<br>0 <= lane <= 1                         | LD3 [Vt.d - Vt3.d][lane], [Xn] | Vt3.2D -> resultval[2]<br>Vt2.2D -> resultval[1]<br>Vt1.2D -> resultval[0]                           | A64                     |
| poly64x1x3_t vld3_lane_p64(poly64_t const * ptr, poly64x1x3_t src, const int lane)     | ptr -> Xn<br>src.val[2] -> Vt3.1D<br>src.val[1] -> Vt2.1D<br>src.val[0] -> Vt1.1D<br>lane == 0                              | LD3 [Vt.d - Vt3.d][lane], [Xn] | Vt3.1D -> resultval[2]<br>Vt2.1D -> resultval[1]<br>Vt1.1D -> resultval[0]                           | A64                     |
| poly64x2x3_t vld3_lane_p64(poly64_t const * ptr, poly64x2x3_t src, const int lane)     | ptr -> Xn<br>src.val[2] -> Vt3.2D<br>src.val[1] -> Vt2.2D<br>src.val[0] -> Vt1.2D<br>0 <= lane <= 1                         | LD3 [Vt.d - Vt3.d][lane], [Xn] | Vt3.2D -> resultval[2]<br>Vt2.2D -> resultval[1]<br>Vt1.2D -> resultval[0]                           | A64                     |
| float64x1x3_t vld3_lane_f64(float64_t const * ptr, float64x1x3_t src, const int lane)  | ptr -> Xn<br>src.val[2] -> Vt3.1D<br>src.val[1] -> Vt2.1D<br>src.val[0] -> Vt1.1D<br>lane == 0                              | LD3 [Vt.d - Vt3.d][lane], [Xn] | Vt3.1D -> resultval[2]<br>Vt2.1D -> resultval[1]<br>Vt1.1D -> resultval[0]                           | A64                     |
| float64x2x3_t vld3q_lane_f64(float64_t const * ptr, float64x2x3_t src, const int lane) | ptr -> Xn<br>src.val[2] -> Vt3.2D<br>src.val[1] -> Vt2.2D<br>src.val[0] -> Vt1.2D<br>0 <= lane <= 1                         | LD3 [Vt.d - Vt3.d][lane], [Xn] | Vt3.2D -> resultval[2]<br>Vt2.2D -> resultval[1]<br>Vt1.2D -> resultval[0]                           | A64                     |
| int16x4x4_t vld4_lane_s16(int16_t const * ptr, int16x4x4_t src, const int lane)        | ptr -> Xn<br>src.val[3] -> Vt4.H<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt1.4H<br>0 <= lane <= 3  | LD4 [Vt.h - Vt4.h][lane], [Xn] | Vt4.H -> resultval[3]<br>Vt3.4H -> resultval[2]<br>Vt2.4H -> resultval[1]<br>Vt1.4H -> resultval[0]  | v7/A32/A64              |
| int16x8x4_t vld4q_lane_s16(int16_t const * ptr, int16x8x4_t src, const int lane)       | ptr -> Xn<br>src.val[3] -> Vt4.8H<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt1.8H<br>0 <= lane <= 7 | LD4 [Vt.h - Vt4.h][lane], [Xn] | Vt4.8H -> resultval[3]<br>Vt3.8H -> resultval[2]<br>Vt2.8H -> resultval[1]<br>Vt1.8H -> resultval[0] | v7/A32/A64              |

| Intrinsic                                                                           | Argument Preparation                                                                                                       | Instruction                   | Result                                                                                                  | Supported Architectures |
|-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|-------------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| int32x2x4_t vld4_lane_s32(int32_t const * ptr, int32x2x4_t src, const int lane)     | ptr -> Xn<br>src.val[3] -> Vt4.2S<br>src.val[2] -> Vt3.2S<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 3 | LD4 {Vt.s - Vt4.s}[lane],[Xn] | Vt4.2S -> result.val[3]<br>Vt3.2S -> result.val[2]<br>Vt2.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| int32x4x4_t vld4q_lane_s32(int32_t const * ptr, int32x4x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt4.4S<br>src.val[2] -> Vt3.4S<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD4 {Vt.s - Vt4.s}[lane],[Xn] | Vt4.4S -> result.val[3]<br>Vt3.4S -> result.val[2]<br>Vt2.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |
| uint16x4x4_t vld4_lane_u16(uint16_t const * ptr, uint16x4x4_t src, const int lane)  | ptr -> Xn<br>src.val[3] -> Vt4.4H<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD4 {Vt.h - Vt4.h}[lane],[Xn] | Vt4.4H -> result.val[3]<br>Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | v7/A32/A64              |
| uint16x8x4_t vld4q_lane_u16(uint16_t const * ptr, uint16x8x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.8H<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD4 {Vt.h - Vt4.h}[lane],[Xn] | Vt4.8H -> result.val[3]<br>Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| uint32x2x4_t vld4_lane_u32(uint32_t const * ptr, uint32x2x4_t src, const int lane)  | ptr -> Xn<br>src.val[3] -> Vt4.2S<br>src.val[2] -> Vt3.2S<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt.2S<br>0 <= lane <= 3 | LD4 {Vt.s - Vt4.s}[lane],[Xn] | Vt4.2S -> result.val[3]<br>Vt3.2S -> result.val[2]<br>Vt2.2S -> result.val[1]<br>Vt.2S -> result.val[0] | v7/A32/A64              |
| uint32x4x4_t vld4q_lane_u32(uint32_t const * ptr, uint32x4x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.4S<br>src.val[2] -> Vt3.4S<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt.4S<br>0 <= lane <= 3 | LD4 {Vt.s - Vt4.s}[lane],[Xn] | Vt4.4S -> result.val[3]<br>Vt3.4S -> result.val[2]<br>Vt2.4S -> result.val[1]<br>Vt.4S -> result.val[0] | v7/A32/A64              |

| Intrinsic                                                                              | Argument Preparation                                                                                                        | Instruction                  | Result                                                                                                   | Supported Architectures |
|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|------------------------------|----------------------------------------------------------------------------------------------------------|-------------------------|
| float16x4x4_t vld4_lane_f16(float16_t const * ptr, float16x4x4_t src, const int lane)  | ptr -> Xn<br>src.val[3] -> Vt4.H<br>src.val[2] -> Vt3.H<br>src.val[1] -> Vt2.H<br>src.val[0] -> Vt1.H<br>0 <= lane <= 3     | LD4 [Vt.h - Vt4.h][lane][Xn] | Vt4.H -> result.val[3]<br>Vt3.H -> result.val[2]<br>Vt2.H -> result.val[1]<br>Vt1.H -> result.val[0]     | v7/A32/A64              |
| float16x8x4_t vld4q_lane_f16(float16_t const * ptr, float16x8x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.8H<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt1.8H<br>0 <= lane <= 7 | LD4 [Vt.h - Vt4.h][lane][Xn] | Vt4.8H -> result.val[3]<br>Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt1.8H -> result.val[0] | v7/A32/A64              |
| float32x2x4_t vld4_lane_f32(float32_t const * ptr, float32x2x4_t src, const int lane)  | ptr -> Xn<br>src.val[3] -> Vt4.2S<br>src.val[2] -> Vt3.2S<br>src.val[1] -> Vt2.2S<br>src.val[0] -> Vt1.2S<br>0 <= lane <= 1 | LD4 [Vt.s - Vt4.s][lane][Xn] | Vt4.2S -> result.val[3]<br>Vt3.2S -> result.val[2]<br>Vt2.2S -> result.val[1]<br>Vt1.2S -> result.val[0] | v7/A32/A64              |
| float32x4x4_t vld4q_lane_f32(float32_t const * ptr, float32x4x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.4S<br>src.val[2] -> Vt3.4S<br>src.val[1] -> Vt2.4S<br>src.val[0] -> Vt1.4S<br>0 <= lane <= 3 | LD4 [Vt.s - Vt4.s][lane][Xn] | Vt4.4S -> result.val[3]<br>Vt3.4S -> result.val[2]<br>Vt2.4S -> result.val[1]<br>Vt1.4S -> result.val[0] | v7/A32/A64              |
| poly16x4x4_t vld4_lane_p16(poly16_t const * ptr, poly16x4x4_t src, const int lane)     | ptr -> Xn<br>src.val[3] -> Vt4.H<br>src.val[2] -> Vt3.H<br>src.val[1] -> Vt2.H<br>src.val[0] -> Vt1.H<br>0 <= lane <= 3     | LD4 [Vt.h - Vt4.h][lane][Xn] | Vt4.H -> result.val[3]<br>Vt3.H -> result.val[2]<br>Vt2.H -> result.val[1]<br>Vt1.H -> result.val[0]     | v7/A32/A64              |
| poly16x8x4_t vld4q_lane_p16(poly16_t const * ptr, poly16x8x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt4.8H<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt1.8H<br>0 <= lane <= 7 | LD4 [Vt.h - Vt4.h][lane][Xn] | Vt4.8H -> result.val[3]<br>Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt1.8H -> result.val[0] | v7/A32/A64              |

| Intrinsic                                                                         | Argument Preparation                                                                                                             | Instruction                    | Result                                                                                                       | Supported Architectures |
|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|--------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------|
| int8x8x4_t vld4_lane_s8(int8_t const * ptr, int8x8x4_t src, const int lane)       | ptr -> Xn<br>src.val[3] -> Vt4.8B<br>src.val[2] -> Vt3.8B<br>src.val[1] -> Vt2.8B<br>src.val[0] -> Vt1.8B<br>0 <= lane <= 7      | LD4 {Vt.b - Vt4.b}[lane], [Xn] | Vt4.8B -> result.val[3]<br>Vt3.8B -> result.val[2]<br>Vt2.8B -> result.val[1]<br>Vt1.8B -> result.val[0]     | v7/A32/A64              |
| uint8x8x4_t vld4_lane_u8(uint8_t const * ptr, uint8x8x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt4.8B<br>src.val[2] -> Vt3.8B<br>src.val[1] -> Vt2.8B<br>src.val[0] -> Vt1.8B<br>0 <= lane <= 7      | LD4 {Vt.b - Vt4.b}[lane], [Xn] | Vt4.8B -> result.val[3]<br>Vt3.8B -> result.val[2]<br>Vt2.8B -> result.val[1]<br>Vt1.8B -> result.val[0]     | v7/A32/A64              |
| poly8x8x4_t vld4_lane_p8(poly8_t const * ptr, poly8x8x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt4.8B<br>src.val[2] -> Vt3.8B<br>src.val[1] -> Vt2.8B<br>src.val[0] -> Vt1.8B<br>0 <= lane <= 7      | LD4 {Vt.b - Vt4.b}[lane], [Xn] | Vt4.8B -> result.val[3]<br>Vt3.8B -> result.val[2]<br>Vt2.8B -> result.val[1]<br>Vt1.8B -> result.val[0]     | v7/A32/A64              |
| int8x16x4_t vld4q_lane_s8(int8_t const * ptr, int8x16x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt4.16B<br>src.val[2] -> Vt3.16B<br>src.val[1] -> Vt2.16B<br>src.val[0] -> Vt1.16B<br>0 <= lane <= 15 | LD4 {Vt.b - Vt4.b}[lane], [Xn] | Vt4.16B -> result.val[3]<br>Vt3.16B -> result.val[2]<br>Vt2.16B -> result.val[1]<br>Vt1.16B -> result.val[0] | A64                     |
| uint8x16x4_t vld4q_lane_u8(uint8_t const * ptr, uint8x16x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.16B<br>src.val[2] -> Vt3.16B<br>src.val[1] -> Vt2.16B<br>src.val[0] -> Vt1.16B<br>0 <= lane <= 15 | LD4 {Vt.b - Vt4.b}[lane], [Xn] | Vt4.16B -> result.val[3]<br>Vt3.16B -> result.val[2]<br>Vt2.16B -> result.val[1]<br>Vt1.16B -> result.val[0] | A64                     |
| poly8x16x4_t vld4q_lane_p8(poly8_t const * ptr, poly8x16x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.16B<br>src.val[2] -> Vt3.16B<br>src.val[1] -> Vt2.16B<br>src.val[0] -> Vt1.16B<br>0 <= lane <= 15 | LD4 {Vt.b - Vt4.b}[lane], [Xn] | Vt4.16B -> result.val[3]<br>Vt3.16B -> result.val[2]<br>Vt2.16B -> result.val[1]<br>Vt1.16B -> result.val[0] | A64                     |

| Intrinsic                                                                              | Argument Preparation                                                                                                          | Instruction                     | Result                                                                                                     | Supported Architectures |
|----------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------|-------------------------|
| int64x1x4_t vld4_lane_s64(int64_t const * ptr, int64x1x4_t src, const int lane)        | ptr -> Xn<br>src.val[3] -> Vt.4.1D<br>src.val[2] -> Vt.3.1D<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0      | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| int64x2x4_t vld4q_lane_s64(int64_t const * ptr, int64x2x4_t src, const int lane)       | ptr -> Xn<br>src.val[3] -> Vt.4.2D<br>src.val[2] -> Vt.3.2D<br>src.val[1] -> Vt.2.2D<br>src.val[0] -> Vt.1D<br>0 <= lane <= 1 | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| uint64x1x4_t vld4_lane_u64(uint64_t const * ptr, uint64x1x4_t src, const int lane)     | ptr -> Xn<br>src.val[3] -> Vt.4.1D<br>src.val[2] -> Vt.3.1D<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0      | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| uint64x2x4_t vld4q_lane_u64(uint64_t const * ptr, uint64x2x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt.4.2D<br>src.val[2] -> Vt.3.2D<br>src.val[1] -> Vt.2.2D<br>src.val[0] -> Vt.1D<br>0 <= lane <= 1 | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| poly64x1x4_t vld4q_lane_p64(poly64_t const * ptr, poly64x1x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt.4.1D<br>src.val[2] -> Vt.3.1D<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0      | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| poly64x2x4_t vld4q_lane_p64(poly64_t const * ptr, poly64x2x4_t src, const int lane)    | ptr -> Xn<br>src.val[3] -> Vt.4.2D<br>src.val[2] -> Vt.3.2D<br>src.val[1] -> Vt.2.2D<br>src.val[0] -> Vt.1D<br>0 <= lane <= 1 | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.2D -> result.val[3]<br>Vt.3.2D -> result.val[2]<br>Vt.2.2D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| float64x1x4_t vld4q_lane_f64(float64_t const * ptr, float64x1x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt.4.1D<br>src.val[2] -> Vt.3.1D<br>src.val[1] -> Vt.2.1D<br>src.val[0] -> Vt.1D<br>lane == 0      | LD4 [Vt.d - Vt.4.d][lane], [Xn] | Vt.4.1D -> result.val[3]<br>Vt.3.1D -> result.val[2]<br>Vt.2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |

| Intrinsic                                                                              | Argument Preparation                                                                                                              | Instruction                   | Result                                                                                                 | Supported Architectures |
|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------|
| float64x2x4_t vld4q_lane_f64(float64_t const * ptr, float64x2x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.2D<br>src.val[2] -> Vt3.2D<br>src.val[1] -> Vt2.2D<br>src.val[0] -> Vt lane <= 1<br>0 <= lane <= 7 | LD4{Vt.d - Vt4.d}[lane], [Xn] | Vt4.2D -> result.val[3]<br>Vt3.2D -> result.val[2]<br>Vt2.2D -> result.val[1]<br>Vt2D -> result.val[0] | A64                     |
| void vst2_lane_s8(int8_t * ptr, int8x8x2_t val, const int lane)                        | ptr -> Xn<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7                                                 | ST2{Vt.b - Vt2.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |
| void vst2_lane_u8(uint8_t * ptr, uint8x8x2_t val, const int lane)                      | ptr -> Xn<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7                                                 | ST2{Vt.b - Vt2.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |
| void vst2_lane_p8(poly8_t * ptr, poly8x8x2_t val, const int lane)                      | ptr -> Xn<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7                                                 | ST2{Vt.b - Vt2.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |
| void vst3_lane_s8(int8_t * ptr, int8x8x3_t val, const int lane)                        | ptr -> Xn<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7                         | ST3{Vt.b - Vt3.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |
| void vst3_lane_u8(uint8_t * ptr, uint8x8x3_t val, const int lane)                      | ptr -> Xn<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7                         | ST3{Vt.b - Vt3.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |
| void vst3_lane_p8(poly8_t * ptr, poly8x8x3_t val, const int lane)                      | ptr -> Xn<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7                         | ST3{Vt.b - Vt3.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |
| void vst4_lane_s8(int8_t * ptr, int8x8x4_t val, const int lane)                        | ptr -> Xn<br>val.val[3] -> Vt4.8B<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt lane <= 7<br>0 <= lane <= 7 | ST4{Vt.b - Vt4.b}[lane], [Xn] | void -> result                                                                                         | v7/A32/A64              |

| Intrinsic                                                             | Argument Preparation                                                                                                       | Instruction                  | Result         | Supported Architectures |
|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst4_lane_u8(uint8_t * ptr, uint8x8x4_t val, const int lane)     | ptr -> Xn<br>val.val[3] -> Vt4.BB<br>val.val[2] -> Vt3.BB<br>val.val[1] -> Vt2.BB<br>val.val[0] -> Vt.BB<br>0 <= lane <= 7 | ST4 [Vt.b - Vt4.b][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_p8(poly8_t * ptr, poly8x8x4_t val, const int lane)     | ptr -> Xn<br>val.val[3] -> Vt4.BB<br>val.val[2] -> Vt3.BB<br>val.val[1] -> Vt2.BB<br>val.val[0] -> Vt.BB<br>0 <= lane <= 7 | ST4 [Vt.b - Vt4.b][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_s16(int16_t * ptr, int16x4x2_t val, const int lane)    | ptr -> Xn<br>val.val[1] -> Vt2.H<br>val.val[0] -> Vt4H<br>0 <= lane <= 3                                                   | ST2 [Vt.h - Vt2.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_s16(int16_t * ptr, int16x8x2_t val, const int lane)   | ptr -> Xn<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt8H<br>0 <= lane <= 7                                                  | ST2 [Vt.h - Vt2.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_s32(int32_t * ptr, int32x2x2_t val, const int lane)    | ptr -> Xn<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt2S<br>0 <= lane <= 1                                                  | ST2 [Vt.s - Vt2.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_s32(int32_t * ptr, int32x4x2_t val, const int lane)   | ptr -> Xn<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt4S<br>0 <= lane <= 3                                                  | ST2 [Vt.s - Vt2.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_u16(uint16_t * ptr, uint16x4x2_t val, const int lane)  | ptr -> Xn<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt4H<br>0 <= lane <= 3                                                  | ST2 [Vt.h - Vt2.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_u16(uint16_t * ptr, uint16x8x2_t val, const int lane) | ptr -> Xn<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt8H<br>0 <= lane <= 7                                                  | ST2 [Vt.h - Vt2.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_u32(uint32_t * ptr, uint32x2x2_t val, const int lane)  | ptr -> Xn<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt2S<br>0 <= lane <= 1                                                  | ST2 [Vt.s - Vt2.s][lane][Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                            | Argument Preparation                                                       | Instruction                | Result         | Supported Architectures |
|----------------------------------------------------------------------|----------------------------------------------------------------------------|----------------------------|----------------|-------------------------|
| void vst2q_lane_u32(uint32_t* ptr, uint32x2_t val, const int lane)   | ptr -> Xn<br>val[all] -> V12.4S<br>val[all] -> V12.4S<br>0 -< lane <- 3    | ST2[VLs - V12.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_f16(float16_t* ptr, float16x4_t val, const int lane)  | ptr -> Xn<br>val[all] -> V12.4H<br>val[all] -> V12.4H<br>0 -< lane <- 3    | ST2[VLh - V12.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_f16(float16_t* ptr, float16x2_t val, const int lane) | ptr -> Xn<br>val[all] -> V12.8H<br>val[all] -> V12.8H<br>0 -< lane <- 7    | ST2[VLh - V12.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_f32(float32_t* ptr, float32x2_t val, const int lane)  | ptr -> Xn<br>val[all] -> V12.2S<br>val[all] -> V12.2S<br>0 -< lane <- 1    | ST2[VLs - V12.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_f32(float32_t* ptr, float32x2_t val, const int lane) | ptr -> Xn<br>val[all] -> V12.4S<br>val[all] -> V12.4S<br>0 -< lane <- 3    | ST2[VLs - V12.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2_lane_p16(poly16_t* ptr, poly16x4_t val, const int lane)    | ptr -> Xn<br>val[all] -> V12.4H<br>val[all] -> V12.4H<br>0 -< lane <- 3    | ST2[VLh - V12.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_p16(poly16_t* ptr, poly16x2_t val, const int lane)   | ptr -> Xn<br>val[all] -> V12.8H<br>val[all] -> V12.8H<br>0 -< lane <- 7    | ST2[VLh - V12.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst2q_lane_s8(uint8_t* ptr, int8x16x2_t val, const int lane)    | ptr -> Xn<br>val[all] -> V12.16B<br>val[all] -> V12.16B<br>0 -< lane <- 15 | ST2[VLb - V12.b][lane][Xn] | void -> result | A64                     |
| void vst2q_lane_u8(uint8_t* ptr, uint8x16x2_t val, const int lane)   | ptr -> Xn<br>val[all] -> V12.16B<br>val[all] -> V12.16B<br>0 -< lane <- 15 | ST2[VLb - V12.b][lane][Xn] | void -> result | A64                     |
| void vst2q_lane_p8(poly8_t* ptr, poly8x16x2_t val, const int lane)   | ptr -> Xn<br>val[all] -> V12.16B<br>val[all] -> V12.16B<br>0 -< lane <- 15 | ST2[VLb - V12.b][lane][Xn] | void -> result | A64                     |

| Intrinsic                                                              | Argument Preparation                                                                               | Instruction                    | Result         | Supported Architectures |
|------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------|----------------|-------------------------|
| void vst2_lane_s64(int64_t* ptr, int64x1x2_t val, const int lane)      | ptr -> Xn<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0                              | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2q_lane_s64(int64_t* ptr, int64x2x2_t val, const int lane)     | ptr -> Xn<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 1                         | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2_lane_u64(uint64_t* ptr, uint64x1x2_t val, const int lane)    | ptr -> Xn<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0                              | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2q_lane_u64(uint64_t* ptr, uint64x2x2_t val, const int lane)   | ptr -> Xn<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 1                         | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2_lane_p64(poly64_t* ptr, poly64x1x2_t val, const int lane)    | ptr -> Xn<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0                              | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2q_lane_p64(poly64_t* ptr, poly64x2x2_t val, const int lane)   | ptr -> Xn<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 1                         | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2_lane_f64(float64_t* ptr, float64x1x2_t val, const int lane)  | ptr -> Xn<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0                              | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst2q_lane_f64(float64_t* ptr, float64x2x2_t val, const int lane) | ptr -> Xn<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 2                         | ST2 [Vt.d - Vt2.d][lane], [Xn] | void -> result | A64                     |
| void vst3_lane_s16(int16_t* ptr, int16x4x3_t val, const int lane)      | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H<br>0 <= lane <= 3 | ST3 [Vt.h - Vt3.h][lane], [Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_s16(int16_t* ptr, int16x8x3_t val, const int lane)     | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7 | ST3 [Vt.h - Vt3.h][lane], [Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                               | Argument Preparation                                                                              | Instruction                 | Result         | Supported Architectures |
|-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst3_lane_s32(int32_t * ptr, int32x2x3_t val, const int lane)      | ptr -> Xn<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt2S<br>0 <= lane <= 1 | ST3[Vt.s - Vt3.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_s32(int32_t * ptr, int32x4x3_t val, const int lane)     | ptr -> Xn<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt4S<br>0 <= lane <= 3 | ST3[Vt.s - Vt3.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3_lane_u16(uint16_t * ptr, uint16x4x3_t val, const int lane)    | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt4H<br>0 <= lane <= 3 | ST3[Vt.h - Vt3.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_u16(uint16_t * ptr, uint16x8x3_t val, const int lane)   | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt8H<br>0 <= lane <= 7 | ST3[Vt.h - Vt3.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3_lane_u32(uint32_t * ptr, uint32x2x3_t val, const int lane)    | ptr -> Xn<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt2S<br>0 <= lane <= 1 | ST3[Vt.s - Vt3.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_u32(uint32_t * ptr, uint32x4x3_t val, const int lane)   | ptr -> Xn<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt4S<br>0 <= lane <= 3 | ST3[Vt.s - Vt3.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3_lane_f16(float16_t * ptr, float16x4x3_t val, const int lane)  | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt4H<br>0 <= lane <= 3 | ST3[Vt.h - Vt3.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_f16(float16_t * ptr, float16x8x3_t val, const int lane) | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt8H<br>0 <= lane <= 7 | ST3[Vt.h - Vt3.h][lane][Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                              | Argument Preparation                                                                                  | Instruction                 | Result         | Supported Architectures |
|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst3_lane_f32(float32_t* ptr, float32x2x3_t val, const int lane)  | ptr -> Xn<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt2S<br>0 <= lane <= 1     | ST3{Vt.s - Vt3.s}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_f32(float32_t* ptr, float32x4x3_t val, const int lane) | ptr -> Xn<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt4S<br>0 <= lane <= 3     | ST3{Vt.s - Vt3.s}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3_lane_p16(poly16_t* ptr, poly16x4x3_t val, const int lane)    | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt4H<br>0 <= lane <= 3     | ST3{Vt.h - Vt3.h}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_p16(poly16_t* ptr, poly16x8x3_t val, const int lane)   | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt8H<br>0 <= lane <= 7     | ST3{Vt.h - Vt3.h}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_s8(int8_t* ptr, int8x16x3_t val, const int lane)       | ptr -> Xn<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt16B<br>0 <= lane <= 15 | ST3{Vt.b - Vt3.b}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_u8(uint8_t* ptr, uint8x16x3_t val, const int lane)     | ptr -> Xn<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt16B<br>0 <= lane <= 15 | ST3{Vt.b - Vt3.b}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3q_lane_p8(poly8_t* ptr, poly8x16x3_t val, const int lane)     | ptr -> Xn<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt16B<br>0 <= lane <= 15 | ST3{Vt.b - Vt3.b}[lane][Xn] | void -> result | v7/A32/A64              |
| void vst3_lane_s64(int64_t* ptr, int64x1x3_t val, const int lane)      | ptr -> Xn<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt1D<br>lane == 0          | ST3{Vt.d - Vt3.d}[lane][Xn] | void -> result | A64                     |

| Intrinsic                                                               | Argument Preparation                                                                                                       | Instruction                  | Result         | Supported Architectures |
|-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst3q_lane_s64(int64_t * ptr, int64x2x3_t val, const int lane)     | ptr -> Xn<br>val[val[2] -> Vt3.2D<br>val[val[1] -> Vt2.2D<br>val[val[0] -> Vt2D<br>0 <= lane <= 1                          | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst3_lane_u64(uint64_t * ptr, uint64x1x3_t val, const int lane)    | ptr -> Xn<br>val[val[2] -> Vt3.1D<br>val[val[1] -> Vt2.1D<br>val[val[0] -> Vt.1D<br>lane == 0                              | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst3q_lane_u64(uint64_t * ptr, uint64x2x3_t val, const int lane)   | ptr -> Xn<br>val[val[2] -> Vt3.2D<br>val[val[1] -> Vt2.2D<br>val[val[0] -> Vt.2D<br>0 <= lane <= 1                         | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst3_lane_p64(poly64_t * ptr, poly64x1x3_t val, const int lane)    | ptr -> Xn<br>val[val[2] -> Vt3.1D<br>val[val[1] -> Vt2.1D<br>val[val[0] -> Vt.1D<br>lane == 0                              | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst3q_lane_p64(poly64_t * ptr, poly64x2x3_t val, const int lane)   | ptr -> Xn<br>val[val[2] -> Vt3.2D<br>val[val[1] -> Vt2.2D<br>val[val[0] -> Vt.2D<br>0 <= lane <= 1                         | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst3_lane_f64(float64_t * ptr, float64x1x3_t val, const int lane)  | ptr -> Xn<br>val[val[2] -> Vt3.1D<br>val[val[1] -> Vt2.1D<br>val[val[0] -> Vt.1D<br>lane == 0                              | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst3q_lane_f64(float64_t * ptr, float64x2x3_t val, const int lane) | ptr -> Xn<br>val[val[2] -> Vt3.2D<br>val[val[1] -> Vt2.2D<br>val[val[0] -> Vt.2D<br>0 <= lane <= 1                         | ST3[Vt.d - Vt3.d][lane],[Xn] | void -> result | A64                     |
| void vst4_lane_s16(int16_t * ptr, int16x4x4_t val, const int lane)      | ptr -> Xn<br>val[val[3] -> Vt4.4H<br>val[val[2] -> Vt3.4H<br>val[val[1] -> Vt2.4H<br>val[val[0] -> Vt.4H<br>0 <= lane <= 3 | ST4[Vt.h - Vt4.h][lane],[Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                             | Argument Preparation                                                                                                       | Instruction                  | Result         | Supported Architectures |
|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst4q_lane_s16(int16_t * ptr, int16x8x4_t val, const int lane)   | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7 | ST4 [Vt.h - Vt4.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_s32(int32_t * ptr, int32x2x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S<br>0 <= lane <= 1 | ST4 [Vt.s - Vt4.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4q_lane_s32(int32_t * ptr, int32x4x4_t val, const int lane)   | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S<br>0 <= lane <= 3 | ST4 [Vt.s - Vt4.s][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_u16(uint16_t * ptr, uint16x4x4_t val, const int lane)  | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H<br>0 <= lane <= 3 | ST4 [Vt.h - Vt4.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4q_lane_u16(uint16_t * ptr, uint16x8x4_t val, const int lane) | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7 | ST4 [Vt.h - Vt4.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_u32(uint32_t * ptr, uint32x2x4_t val, const int lane)  | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S<br>0 <= lane <= 1 | ST4 [Vt.s - Vt4.s][lane][Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                              | Argument Preparation                                                                                                        | Instruction                  | Result         | Supported Architectures |
|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst4q_lane_u32(uint32_t* ptr, uint32x4_t val, const int lane)     | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt1.4S<br>0 <= lane <= 3 | ST4{Vt.s - Vt4.s}[lane].[Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_f16(float16_t* ptr, float16x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt1.4H<br>0 <= lane <= 3 | ST4{Vt.h - Vt4.h}[lane].[Xn] | void -> result | v7/A32/A64              |
| void vst4q_lane_f16(float16_t* ptr, float16x8_t val, const int lane)   | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt1.8H<br>0 <= lane <= 7 | ST4{Vt.h - Vt4.h}[lane].[Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_f32(float32_t* ptr, float32x2x4_t val, const int lane)  | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt1.2S<br>0 <= lane <= 1 | ST4{Vt.s - Vt4.s}[lane].[Xn] | void -> result | v7/A32/A64              |
| void vst4q_lane_f32(float32_t* ptr, float32x4x4_t val, const int lane) | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt1.4S<br>0 <= lane <= 3 | ST4{Vt.s - Vt4.s}[lane].[Xn] | void -> result | v7/A32/A64              |
| void vst4_lane_p16(poly16_t* ptr, poly16x4x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt1.4H<br>0 <= lane <= 3 | ST4{Vt.h - Vt4.h}[lane].[Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                                             | Argument Preparation                                                                                                            | Instruction                 | Result         | Supported Architectures |
|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst4q_lane_p16(poly16_t * ptr, poly16x8x4_t val, const int lane) | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7      | ST4[Vt.h - Vt4.h][lane][Xn] | void -> result | v7/A32/A64              |
| void vst4q_lane_s8(int8_t * ptr, int8x16x4_t val, const int lane)     | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B<br>0 <= lane <= 15 | ST4[Vt.b - Vt4.b][lane][Xn] | void -> result | A64                     |
| void vst4q_lane_u8(uint8_t * ptr, uint8x16x4_t val, const int lane)   | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B<br>0 <= lane <= 15 | ST4[Vt.b - Vt4.b][lane][Xn] | void -> result | A64                     |
| void vst4q_lane_p8(poly8_t * ptr, poly8x16x4_t val, const int lane)   | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B<br>0 <= lane <= 15 | ST4[Vt.b - Vt4.b][lane][Xn] | void -> result | A64                     |
| void vst4_lane_s64(int64_t * ptr, int64x1x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0           | ST4[Vt.d - Vt4.d][lane][Xn] | void -> result | A64                     |
| void vst4_lane_s64(int64_t * ptr, int64x2x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 1      | ST4[Vt.d - Vt4.d][lane][Xn] | void -> result | A64                     |
| void vst4_lane_u64(uint64_t * ptr, uint64x1x4_t val, const int lane)  | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0           | ST4[Vt.d - Vt4.d][lane][Xn] | void -> result | A64                     |

| Intrinsic                                                               | Argument Preparation                                                                                                       | Instruction                    | Result         | Supported Architectures |
|-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|--------------------------------|----------------|-------------------------|
| void vst4q_lane_u64(uint64_t* ptr, uint64x2x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.1D<br>0 <= lane <= 1 | ST4 [Vt.d - Vt4.d][lane], [Xn] | void -> result | A64                     |
| void vst4_lane_p64(poly64_t* ptr, poly64x4x1x4_t val, const int lane)   | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0      | ST4 [Vt.d - Vt4.d][lane], [Xn] | void -> result | A64                     |
| void vst4q_lane_p64(poly64_t* ptr, poly64x2x4_t val, const int lane)    | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 1 | ST4 [Vt.d - Vt4.d][lane], [Xn] | void -> result | A64                     |
| void vst4_lane_f64(float64_t* ptr, float64x4x1x4_t val, const int lane) | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D<br>lane == 0      | ST4 [Vt.d - Vt4.d][lane], [Xn] | void -> result | A64                     |
| void vst4q_lane_f64(float64_t* ptr, float64x2x4_t val, const int lane)  | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt.2D<br>0 <= lane <= 1 | ST4 [Vt.d - Vt4.d][lane], [Xn] | void -> result | A64                     |
| void vst1_s8_x2(int8_t* ptr, int8x8x2_t val)                            | ptr -> Xn<br>val.val[1] -> Vt.2.8B<br>val.val[0] -> Vt.8B                                                                  | ST1 [Vt.8B - Vt.2.8B], [Xn]    | void -> result | v7/A32/A64              |
| void vst1q_s8_x2(int8_t* ptr, int8x16x2_t val)                          | ptr -> Xn<br>val.val[1] -> Vt.2.16B<br>val.val[0] -> Vt.16B                                                                | ST1 [Vt.16B - Vt.2.16B], [Xn]  | void -> result | v7/A32/A64              |
| void vst1_s16_x2(int16_t* ptr, int16x4x2_t val)                         | ptr -> Xn<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H                                                                  | ST1 [Vt.4H - Vt.2.4H], [Xn]    | void -> result | v7/A32/A64              |
| void vst1q_s16_x2(int16_t* ptr, int16x8x2_t val)                        | ptr -> Xn<br>val.val[1] -> Vt.2.8H<br>val.val[0] -> Vt.8H                                                                  | ST1 [Vt.8H - Vt.2.8H], [Xn]    | void -> result | v7/A32/A64              |

| Intrinsic                                            | Argument Preparation                                         | Instruction              | Result         | Supported Architectures |
|------------------------------------------------------|--------------------------------------------------------------|--------------------------|----------------|-------------------------|
| void vst1_s32_x2(int32_t* ptr, int32x2x2_t val)      | ptr -> Xn<br>val[all] -><br>V12.2S<br>val[all] -><br>V1.2S   | ST1[VL2S - V12.2S][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_s32_x2(int32_t* ptr, int32x4x2_t val)     | ptr -> Xn<br>val[all] -><br>V12.4S<br>val[all] -><br>V1.4S   | ST1[VL4S - V12.4S][Xn]   | void -> result | v7/A32/A64              |
| void vst1_u8_x2(uint8_t* ptr, uint8x2x2_t val)       | ptr -> Xn<br>val[all] -><br>V12.8B<br>val[all] -><br>V1.8B   | ST1[VL8B - V12.8B][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u8_x2(uint8_t* ptr, uint8x4x2_t val)      | ptr -> Xn<br>val[all] -><br>V12.16B<br>val[all] -><br>V1.16B | ST1[VL16B - V12.16B][Xn] | void -> result | v7/A32/A64              |
| void vst1_u16_x2(uint16_t* ptr, uint16x4x2_t val)    | ptr -> Xn<br>val[all] -><br>V12.4H<br>val[all] -><br>V1.4H   | ST1[VL4H - V12.4H][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u16_x2(uint16_t* ptr, uint16x8x2_t val)   | ptr -> Xn<br>val[all] -><br>V12.8H<br>val[all] -><br>V1.8H   | ST1[VL8H - V12.8H][Xn]   | void -> result | v7/A32/A64              |
| void vst1_u32_x2(uint32_t* ptr, uint32x2x2_t val)    | ptr -> Xn<br>val[all] -><br>V12.2S<br>val[all] -><br>V1.2S   | ST1[VL2S - V12.2S][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u32_x2(uint32_t* ptr, uint32x4x2_t val)   | ptr -> Xn<br>val[all] -><br>V12.4S<br>val[all] -><br>V1.4S   | ST1[VL4S - V12.4S][Xn]   | void -> result | v7/A32/A64              |
| void vst1_f16_x2(float16_t* ptr, float16x4x2_t val)  | ptr -> Xn<br>val[all] -><br>V12.4H<br>val[all] -><br>V1.4H   | ST1[VL4H - V12.4H][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_f16_x2(float16_t* ptr, float16x8x2_t val) | ptr -> Xn<br>val[all] -><br>V12.8H<br>val[all] -><br>V1.8H   | ST1[VL8H - V12.8H][Xn]   | void -> result | v7/A32/A64              |
| void vst1_f32_x2(float32_t* ptr, float32x2x2_t val)  | ptr -> Xn<br>val[all] -><br>V12.2S<br>val[all] -><br>V1.2S   | ST1[VL2S - V12.2S][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_f32_x2(float32_t* ptr, float32x4x2_t val) | ptr -> Xn<br>val[all] -><br>V12.4S<br>val[all] -><br>V1.4S   | ST1[VL4S - V12.4S][Xn]   | void -> result | v7/A32/A64              |
| void vst1_p8_x2(poly8_t* ptr, poly8x2x2_t val)       | ptr -> Xn<br>val[all] -><br>V12.8B<br>val[all] -><br>V1.8B   | ST1[VL8B - V12.8B][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_p8_x2(poly8_t* ptr, poly8x4x2_t val)      | ptr -> Xn<br>val[all] -><br>V12.16B<br>val[all] -><br>V1.16B | ST1[VL16B - V12.16B][Xn] | void -> result | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation                                                                          | Instruction             | Result         | Supported Architectures |
|-------------------------------------------------------|-----------------------------------------------------------------------------------------------|-------------------------|----------------|-------------------------|
| void vst1_p16_x2(poly16_1*, ptr, poly16x4x2_1 val)    | ptr -> Xn<br>val[all][1] -><br>V2.4H<br>val[all][0] -><br>Vt.4H                               | ST1[VL4H - V2.4H][Xn]   | void -> result | V7/A32/A64              |
| void vst1q_p16_x2(poly16_1*, ptr, poly16x8x2_1 val)   | ptr -> Xn<br>val[all][1] -><br>V2.8H<br>val[all][0] -><br>Vt.8H                               | ST1[VL8H - V2.8H][Xn]   | void -> result | V7/A32/A64              |
| void vst1_s64_x2(int64_1*, ptr, int64x1x2_1 val)      | ptr -> Xn<br>val[all][1] -><br>V2.1D<br>val[all][0] -><br>Vt.1D                               | ST1[VL1D - V2.1D][Xn]   | void -> result | V7/A32/A64              |
| void vst1_u64_x2(uint64_1*, ptr, uint64x1x2_1 val)    | ptr -> Xn<br>val[all][1] -><br>V2.1D<br>val[all][0] -><br>Vt.1D                               | ST1[VL1D - V2.1D][Xn]   | void -> result | V7/A32/A64              |
| void vst1_p64_x2(poly64_1*, ptr, poly64x1x2_1 val)    | ptr -> Xn<br>val[all][1] -><br>V2.1D<br>val[all][0] -><br>Vt.1D                               | ST1[VL1D - V2.1D][Xn]   | void -> result | A32/A64                 |
| void vst1q_s64_x2(int64_1*, ptr, int64x2x2_1 val)     | ptr -> Xn<br>val[all][1] -><br>V2.2D<br>val[all][0] -><br>Vt.2D                               | ST1[VL2D - V2.2D][Xn]   | void -> result | V7/A32/A64              |
| void vst1q_u64_x2(uint64_1*, ptr, uint64x2x2_1 val)   | ptr -> Xn<br>val[all][1] -><br>V2.2D<br>val[all][0] -><br>Vt.2D                               | ST1[VL2D - V2.2D][Xn]   | void -> result | V7/A32/A64              |
| void vst1q_p64_x2(poly64_1*, ptr, poly64x2x2_1 val)   | ptr -> Xn<br>val[all][1] -><br>V2.2D<br>val[all][0] -><br>Vt.2D                               | ST1[VL2D - V2.2D][Xn]   | void -> result | A32/A64                 |
| void vst1_f64_x2(float64_1*, ptr, float64x1x2_1 val)  | ptr -> Xn<br>val[all][1] -><br>V2.1D<br>val[all][0] -><br>Vt.1D                               | ST1[VL1D - V2.1D][Xn]   | void -> result | A64                     |
| void vst1q_f64_x2(float64_1*, ptr, float64x2x2_1 val) | ptr -> Xn<br>val[all][1] -><br>V2.2D<br>val[all][0] -><br>Vt.2D                               | ST1[VL2D - V2.2D][Xn]   | void -> result | A64                     |
| void vst1_s8_x3(int8_1*, ptr, int8x3x3_1 val)         | ptr -> Xn<br>val[all][2] -><br>V3.8B<br>val[all][1] -><br>V2.8B<br>val[all][0] -><br>Vt.8B    | ST1[VL8B - V3.8B][Xn]   | void -> result | V7/A32/A64              |
| void vst1q_s8_x3(int8_1*, ptr, int8x16x3_1 val)       | ptr -> Xn<br>val[all][2] -><br>V3.16B<br>val[all][1] -><br>V2.16B<br>val[all][0] -><br>Vt.16B | ST1[VL16B - V3.16B][Xn] | void -> result | V7/A32/A64              |
| void vst1_f32_x3(int16_1*, ptr, int16x4x3_1 val)      | ptr -> Xn<br>val[all][2] -><br>V3.4H<br>val[all][1] -><br>V2.4H<br>val[all][0] -><br>Vt.4H    | ST1[VL4H - V3.4H][Xn]   | void -> result | V7/A32/A64              |

| Intrinsic                                           | Argument Preparation                                                                  | Instruction                  | Result         | Supported Architectures |
|-----------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------|----------------|-------------------------|
| void vst1q_s16_x3(int16_t* ptr, int16x8x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt.3.8H<br>val.val[1] -> Vt.2.8H<br>val.val[0] -> Vt.8H    | ST1 [Vt.8H - Vt.3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_s32_x3(int32_t* ptr, int32x2x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt.3.2S<br>val.val[1] -> Vt.2.2S<br>val.val[0] -> Vt.2S    | ST1 [Vt.2S - Vt.3.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_s32_x3(int32_t* ptr, int32x4x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt.3.4S<br>val.val[1] -> Vt.2.4S<br>val.val[0] -> Vt.4S    | ST1 [Vt.4S - Vt.3.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_u8_x3(uint8_t* ptr, uint8x8x3_t val)      | ptr -> Xn<br>val.val[2] -> Vt.3.8B<br>val.val[1] -> Vt.2.8B<br>val.val[0] -> Vt.8B    | ST1 [Vt.8B - Vt.3.8B].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u8_x3(uint8_t* ptr, uint8x16x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt.3.16B<br>val.val[1] -> Vt.2.16B<br>val.val[0] -> Vt.16B | ST1 [Vt.16B - Vt.3.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst1_u16_x3(uint16_t* ptr, uint16x4x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt.3.4H<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H    | ST1 [Vt.4H - Vt.3.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u16_x3(uint16_t* ptr, uint16x8x3_t val)  | ptr -> Xn<br>val.val[2] -> Vt.3.8H<br>val.val[1] -> Vt.2.8H<br>val.val[0] -> Vt.8H    | ST1 [Vt.8H - Vt.3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_u32_x3(uint32_t* ptr, uint32x2x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt.3.2S<br>val.val[1] -> Vt.2.2S<br>val.val[0] -> Vt.2S    | ST1 [Vt.2S - Vt.3.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u32_x3(uint32_t* ptr, uint32x4x3_t val)  | ptr -> Xn<br>val.val[2] -> Vt.3.4S<br>val.val[1] -> Vt.2.4S<br>val.val[0] -> Vt.4S    | ST1 [Vt.4S - Vt.3.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_f16_x3(float16_t* ptr, float16x4x3_t val) | ptr -> Xn<br>val.val[2] -> Vt.3.4H<br>val.val[1] -> Vt.2.4H<br>val.val[0] -> Vt.4H    | ST1 [Vt.4H - Vt.3.4H].[Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation                                                                | Instruction                 | Result         | Supported Architectures |
|-------------------------------------------------------|-------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst1q_f16_x3(float16_t * ptr, float16x8x3_t val) | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H    | ST1 [Vt.8H - Vt3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_f32_x3(float32_t * ptr, float32x2x3_t val)  | ptr -> Xn<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S    | ST1 [Vt.2S - Vt3.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_f32_x3(float32_t * ptr, float32x4x3_t val) | ptr -> Xn<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S    | ST1 [Vt.4S - Vt3.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_p8_x3(poly8_t * ptr, poly8x8x3_t val)       | ptr -> Xn<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt.8B    | ST1 [Vt.8B - Vt3.8B].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_p8_x3(poly8_t * ptr, poly8x16x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B | ST1 [Vt.16B - Vt3.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst1_p16_x3(poly16_t * ptr, poly16x4x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H    | ST1 [Vt.4H - Vt3.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_p16_x3(poly16_t * ptr, poly16x8x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H    | ST1 [Vt.8H - Vt3.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_s64_x3(int64_t * ptr, int64x1x3_t val)      | ptr -> Xn<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D    | ST1 [Vt.1D - Vt3.1D].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_u64_x3(uint64_t * ptr, uint64x1x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D    | ST1 [Vt.1D - Vt3.1D].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_p64_x3(poly64_t * ptr, poly64x1x3_t val)    | ptr -> Xn<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt.1D    | ST1 [Vt.1D - Vt3.1D].[Xn]   | void -> result | A32/A64                 |

| Intrinsic                                            | Argument Preparation                                                                                        | Instruction               | Result         | Supported Architectures |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|---------------------------|----------------|-------------------------|
| void vst1q_s64_x3(int64_t* ptr, int64x2x3_t val)     | ptr -> Xn<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt2D                             | ST1{Vt.2D - Vt3.2D}[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u64_x3(uint64_t* ptr, uint64x2x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt2D                             | ST1{Vt.2D - Vt3.2D}[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_p64_x3(poly64_t* ptr, poly64x2x3_t val)   | ptr -> Xn<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt2D                             | ST1{Vt.2D - Vt3.2D}[Xn]   | void -> result | v7/A32/A64              |
| void vst1_f64_x3(float64_t* ptr, float64x1x3_t val)  | ptr -> Xn<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt1D                             | ST1{Vt.1D - Vt3.1D}[Xn]   | void -> result | A64                     |
| void vst1q_f64_x3(float64_t* ptr, float64x2x3_t val) | ptr -> Xn<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt2D                             | ST1{Vt.2D - Vt3.2D}[Xn]   | void -> result | A64                     |
| void vst1_s8_x4(int8_t* ptr, int8x8x4_t val)         | ptr -> Xn<br>val.val[3] -> Vt4.8B<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt8B     | ST1{Vt.8B - Vt4.8B}[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_s8_x4(int8_t* ptr, int8x16x4_t val)       | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt16B | ST1{Vt.16B - Vt4.16B}[Xn] | void -> result | v7/A32/A64              |
| void vst1_s16_x4(int16_t* ptr, int16x4x4_t val)      | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt4H     | ST1{Vt.4H - Vt4.4H}[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_s16_x4(int16_t* ptr, int16x8x4_t val)     | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt8H     | ST1{Vt.8H - Vt4.8H}[Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                           | Argument Preparation                                                                                         | Instruction                 | Result         | Supported Architectures |
|-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst1_s32_x4(int32_t * ptr, int32x4_t val)      | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S     | ST1 [Vt.2S - Vt4.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_s32_x4(int32_t * ptr, int32x4x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S     | ST1 [Vt.4S - Vt4.4S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_u8_x4(uint8_t * ptr, uint8x8x4_t val)     | ptr -> Xn<br>val.val[3] -> Vt4.8B<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt.8B     | ST1 [Vt.8B - Vt4.8B].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u8_x4(uint8_t * ptr, uint8x16x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B | ST1 [Vt.16B - Vt4.16B].[Xn] | void -> result | v7/A32/A64              |
| void vst1_u16_x4(uint16_t * ptr, uint16x4x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H     | ST1 [Vt.4H - Vt4.4H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u16_x4(uint16_t * ptr, uint16x8x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H     | ST1 [Vt.8H - Vt4.8H].[Xn]   | void -> result | v7/A32/A64              |
| void vst1_u32_x4(uint32_t * ptr, uint32x2x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S     | ST1 [Vt.2S - Vt4.2S].[Xn]   | void -> result | v7/A32/A64              |
| void vst1q_u32_x4(uint32_t * ptr, uint32x4x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S     | ST1 [Vt.4S - Vt4.4S].[Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation                                                                                         | Instruction               | Result         | Supported Architectures |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------|----------------|-------------------------|
| void vst1_f16_x4(float16_t * ptr, float16x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.H<br>val.val[2] -> Vt3.H<br>val.val[1] -> Vt2.H<br>val.val[0] -> Vt.4H        | ST1[Vt.4H - Vt4.H][Xn]    | void -> result | v7/A32/A64              |
| void vst1q_f16_x4(float16_t * ptr, float16x8x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.BH<br>val.val[2] -> Vt3.BH<br>val.val[1] -> Vt2.BH<br>val.val[0] -> Vt.8H     | ST1[Vt.8H - Vt4.8H][Xn]   | void -> result | v7/A32/A64              |
| void vst1_f32_x4(float32_t * ptr, float32x2x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.2S<br>val.val[2] -> Vt3.2S<br>val.val[1] -> Vt2.2S<br>val.val[0] -> Vt.2S     | ST1[Vt.2S - Vt4.2S][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_f32_x4(float32_t * ptr, float32x4x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.4S<br>val.val[2] -> Vt3.4S<br>val.val[1] -> Vt2.4S<br>val.val[0] -> Vt.4S     | ST1[Vt.4S - Vt4.4S][Xn]   | void -> result | v7/A32/A64              |
| void vst1_p8_x4(poly8_t * ptr, poly8x8x4_t val)       | ptr -> Xn<br>val.val[3] -> Vt4.8B<br>val.val[2] -> Vt3.8B<br>val.val[1] -> Vt2.8B<br>val.val[0] -> Vt.8B     | ST1[Vt.8B - Vt4.8B][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_p8_x4(poly8_t * ptr, poly8x16x4_t val)     | ptr -> Xn<br>val.val[3] -> Vt4.16B<br>val.val[2] -> Vt3.16B<br>val.val[1] -> Vt2.16B<br>val.val[0] -> Vt.16B | ST1[Vt.16B - Vt4.16B][Xn] | void -> result | v7/A32/A64              |
| void vst1_p16_x4(poly16_t * ptr, poly16x4x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H     | ST1[Vt.4H - Vt4.4H][Xn]   | void -> result | v7/A32/A64              |
| void vst1q_p16_x4(poly16_t * ptr, poly16x8x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H     | ST1[Vt.8H - Vt4.8H][Xn]   | void -> result | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation                                                                                      | Instruction             | Result         | Supported Architectures |
|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|-------------------------|----------------|-------------------------|
| void vst1_s64_x4(int64_t * ptr, int64x1x4_t val)      | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt1.1D | ST1[Vt.1D - Vt4.1D][Xn] | void -> result | v7/A32/A64              |
| void vst1_u64_x4(uint64_t * ptr, uint64x1x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt1.1D | ST1[Vt.1D - Vt4.1D][Xn] | void -> result | v7/A32/A64              |
| void vst1_p64_x4(poly64_t * ptr, poly64x1x4_t val)    | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt1.1D | ST1[Vt.1D - Vt4.1D][Xn] | void -> result | A32/A64                 |
| void vst1q_s64_x4(int64_t * ptr, int64x2x4_t val)     | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt1.2D | ST1[Vt.2D - Vt4.2D][Xn] | void -> result | v7/A32/A64              |
| void vst1q_u64_x4(uint64_t * ptr, uint64x2x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt1.2D | ST1[Vt.2D - Vt4.2D][Xn] | void -> result | v7/A32/A64              |
| void vst1q_p64_x4(poly64_t * ptr, poly64x2x4_t val)   | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt1.2D | ST1[Vt.2D - Vt4.2D][Xn] | void -> result | A32/A64                 |
| void vst1_f64_x4(float64_t * ptr, float64x1x4_t val)  | ptr -> Xn<br>val.val[3] -> Vt4.1D<br>val.val[2] -> Vt3.1D<br>val.val[1] -> Vt2.1D<br>val.val[0] -> Vt1.1D | ST1[Vt.1D - Vt4.1D][Xn] | void -> result | A64                     |
| void vst1q_f64_x4(float64_t * ptr, float64x2x4_t val) | ptr -> Xn<br>val.val[3] -> Vt4.2D<br>val.val[2] -> Vt3.2D<br>val.val[1] -> Vt2.2D<br>val.val[0] -> Vt1.2D | ST1[Vt.2D - Vt4.2D][Xn] | void -> result | A64                     |

| Intrinsic                                         | Argument Preparation | Instruction                 | Result                                                 | Supported Architectures |
|---------------------------------------------------|----------------------|-----------------------------|--------------------------------------------------------|-------------------------|
| int8x8x2_t vld1_s8_x2(int8_t const * ptr)         | ptr -> Xn            | LD1 [Vt.8B - Vt.2.8B][Xn]   | Vt.2.8B -> result[val][1]<br>Vt.8B -> result[val][0]   | v7/A32/A64              |
| int8x16x2_t vld1q_s8_x2(int8_t const * ptr)       | ptr -> Xn            | LD1 [Vt.16B - Vt.2.16B][Xn] | Vt.2.16B -> result[val][1]<br>Vt.16B -> result[val][0] | v7/A32/A64              |
| int16x4x2_t vld1_s16_x2(int16_t const * ptr)      | ptr -> Xn            | LD1 [Vt.4H - Vt.2.4H][Xn]   | Vt.2.4H -> result[val][1]<br>Vt.4H -> result[val][0]   | v7/A32/A64              |
| int16x8x2_t vld1q_s16_x2(int16_t const * ptr)     | ptr -> Xn            | LD1 [Vt.8H - Vt.2.8H][Xn]   | Vt.2.8H -> result[val][1]<br>Vt.8H -> result[val][0]   | v7/A32/A64              |
| int32x2x2_t vld1_s32_x2(int32_t const * ptr)      | ptr -> Xn            | LD1 [Vt.2S - Vt.2.2S][Xn]   | Vt.2.2S -> result[val][1]<br>Vt.2S -> result[val][0]   | v7/A32/A64              |
| int32x4x2_t vld1q_s32_x2(int32_t const * ptr)     | ptr -> Xn            | LD1 [Vt.4S - Vt.2.4S][Xn]   | Vt.2.4S -> result[val][1]<br>Vt.4S -> result[val][0]   | v7/A32/A64              |
| uint8x8x2_t vld1_u8_x2(uint8_t const * ptr)       | ptr -> Xn            | LD1 [Vt.8B - Vt.2.8B][Xn]   | Vt.2.8B -> result[val][1]<br>Vt.8B -> result[val][0]   | v7/A32/A64              |
| uint8x16x2_t vld1q_u8_x2(uint8_t const * ptr)     | ptr -> Xn            | LD1 [Vt.16B - Vt.2.16B][Xn] | Vt.2.16B -> result[val][1]<br>Vt.16B -> result[val][0] | v7/A32/A64              |
| uint16x4x2_t vld1_u16_x2(uint16_t const * ptr)    | ptr -> Xn            | LD1 [Vt.4H - Vt.2.4H][Xn]   | Vt.2.4H -> result[val][1]<br>Vt.4H -> result[val][0]   | v7/A32/A64              |
| uint16x8x2_t vld1q_u16_x2(uint16_t const * ptr)   | ptr -> Xn            | LD1 [Vt.8H - Vt.2.8H][Xn]   | Vt.2.8H -> result[val][1]<br>Vt.8H -> result[val][0]   | v7/A32/A64              |
| uint32x2x2_t vld1_u32_x2(uint32_t const * ptr)    | ptr -> Xn            | LD1 [Vt.2S - Vt.2.2S][Xn]   | Vt.2.2S -> result[val][1]<br>Vt.2S -> result[val][0]   | v7/A32/A64              |
| uint32x4x2_t vld1q_u32_x2(uint32_t const * ptr)   | ptr -> Xn            | LD1 [Vt.4S - Vt.2.4S][Xn]   | Vt.2.4S -> result[val][1]<br>Vt.4S -> result[val][0]   | v7/A32/A64              |
| float16x4x2_t vld1_f16_x2(float16_t const * ptr)  | ptr -> Xn            | LD1 [Vt.4H - Vt.2.4H][Xn]   | Vt.2.4H -> result[val][1]<br>Vt.4H -> result[val][0]   | v7/A32/A64              |
| float16x8x2_t vld1q_f16_x2(float16_t const * ptr) | ptr -> Xn            | LD1 [Vt.8H - Vt.2.8H][Xn]   | Vt.2.8H -> result[val][1]<br>Vt.8H -> result[val][0]   | v7/A32/A64              |
| float32x2x2_t vld1_f32_x2(float32_t const * ptr)  | ptr -> Xn            | LD1 [Vt.2S - Vt.2.2S][Xn]   | Vt.2.2S -> result[val][1]<br>Vt.2S -> result[val][0]   | v7/A32/A64              |
| float32x4x2_t vld1q_f32_x2(float32_t const * ptr) | ptr -> Xn            | LD1 [Vt.4S - Vt.2.4S][Xn]   | Vt.2.4S -> result[val][1]<br>Vt.4S -> result[val][0]   | v7/A32/A64              |
| poly8x8x2_t vld1_p8_x2(poly8_t const * ptr)       | ptr -> Xn            | LD1 [Vt.8B - Vt.2.8B][Xn]   | Vt.2.8B -> result[val][1]<br>Vt.8B -> result[val][0]   | v7/A32/A64              |
| poly8x16x2_t vld1q_p8_x2(poly8_t const * ptr)     | ptr -> Xn            | LD1 [Vt.16B - Vt.2.16B][Xn] | Vt.2.16B -> result[val][1]<br>Vt.16B -> result[val][0] | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation | Instruction                  | Result                                                                          | Supported Architectures |
|---------------------------------------------------|----------------------|------------------------------|---------------------------------------------------------------------------------|-------------------------|
| poly16x4x2_t vld1_p16_x2(poly16_t const * ptr)    | ptr -> Xn            | LD1 [Vt.4H - Vt2.4H], [Xn]   | Vt2.4H -> result[val[1]<br>Vt.4H -> result[val[0]                               | v7/A32/A64              |
| poly16x8x2_t vld1q_p16_x2(poly16_t const * ptr)   | ptr -> Xn            | LD1 [Vt.8H - Vt2.8H], [Xn]   | Vt2.8H -> result[val[1]<br>Vt.8H -> result[val[0]                               | v7/A32/A64              |
| int64x1x2_t vld1_s64_x2(int64_t const * ptr)      | ptr -> Xn            | LD1 [Vt.1D - Vt2.1D], [Xn]   | Vt2.1D -> result[val[1]<br>Vt.1D -> result[val[0]                               | v7/A32/A64              |
| uint64x1x2_t vld1_u64_x2(uint64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt2.1D], [Xn]   | Vt2.1D -> result[val[1]<br>Vt.1D -> result[val[0]                               | v7/A32/A64              |
| poly64x1x2_t vld1_p64_x2(poly64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt2.1D], [Xn]   | Vt2.1D -> result[val[1]<br>Vt.1D -> result[val[0]                               | A32/A64                 |
| int64x2x2_t vld1q_s64_x2(int64_t const * ptr)     | ptr -> Xn            | LD1 [Vt.2D - Vt2.2D], [Xn]   | Vt2.2D -> result[val[1]<br>Vt.2D -> result[val[0]                               | v7/A32/A64              |
| uint64x2x2_t vld1q_u64_x2(uint64_t const * ptr)   | ptr -> Xn            | LD1 [Vt.2D - Vt2.2D], [Xn]   | Vt2.2D -> result[val[1]<br>Vt.2D -> result[val[0]                               | v7/A32/A64              |
| poly64x2x2_t vld1q_p64_x2(poly64_t const * ptr)   | ptr -> Xn            | LD1 [Vt.2D - Vt2.2D], [Xn]   | Vt2.2D -> result[val[1]<br>Vt.2D -> result[val[0]                               | A32/A64                 |
| float64x1x2_t vld1_f64_x2(float64_t const * ptr)  | ptr -> Xn            | LD1 [Vt.1D - Vt2.1D], [Xn]   | Vt2.1D -> result[val[1]<br>Vt.1D -> result[val[0]                               | A64                     |
| float64x2x2_t vld1q_f64_x2(float64_t const * ptr) | ptr -> Xn            | LD1 [Vt.2D - Vt2.2D], [Xn]   | Vt2.2D -> result[val[1]<br>Vt.2D -> result[val[0]                               | A64                     |
| int8x8x3_t vld1_s8_x3(int8_t const * ptr)         | ptr -> Xn            | LD1 [Vt.8B - Vt3.8B], [Xn]   | Vt3.8B -> result[val[2]<br>Vt2.8B -> result[val[1]<br>Vt.8B -> result[val[0]    | v7/A32/A64              |
| int8x16x3_t vld1q_s8_x3(int8_t const * ptr)       | ptr -> Xn            | LD1 [Vt.16B - Vt3.16B], [Xn] | Vt3.16B -> result[val[2]<br>Vt2.16B -> result[val[1]<br>Vt.16B -> result[val[0] | v7/A32/A64              |
| int16x4x3_t vld1_s16_x3(int16_t const * ptr)      | ptr -> Xn            | LD1 [Vt.4H - Vt3.4H], [Xn]   | Vt3.4H -> result[val[2]<br>Vt2.4H -> result[val[1]<br>Vt.4H -> result[val[0]    | v7/A32/A64              |
| int16x8x3_t vld1q_s16_x3(int16_t const * ptr)     | ptr -> Xn            | LD1 [Vt.8H - Vt3.8H], [Xn]   | Vt3.8H -> result[val[2]<br>Vt2.8H -> result[val[1]<br>Vt.8H -> result[val[0]    | v7/A32/A64              |
| int32x2x3_t vld1_s32_x3(int32_t const * ptr)      | ptr -> Xn            | LD1 [Vt.2S - Vt3.2S], [Xn]   | Vt3.2S -> result[val[2]<br>Vt2.2S -> result[val[1]<br>Vt.2S -> result[val[0]    | v7/A32/A64              |

| Intrinsic                                        | Argument Preparation | Instruction               | Result                                                                            | Supported Architectures |
|--------------------------------------------------|----------------------|---------------------------|-----------------------------------------------------------------------------------|-------------------------|
| int32x4x3_t vld1q_s32_x3int32_t const * ptr)     | ptr -> Xn            | LD1 (Vt.4S-Vt.3.4S)[Xn]   | Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]    | v7/A32/A64              |
| uint8x8x3_t vld1_u8_x3uint8_t const * ptr)       | ptr -> Xn            | LD1 (Vt.8B-Vt.3.8B)[Xn]   | Vt.3.8B -> result.val[2]<br>Vt.2.8B -> result.val[1]<br>Vt.8B -> result.val[0]    | v7/A32/A64              |
| uint8x16x3_t vld1q_u8_x3uint8_t const * ptr)     | ptr -> Xn            | LD1 (Vt.16B-Vt.3.16B)[Xn] | Vt.3.16B -> result.val[2]<br>Vt.2.16B -> result.val[1]<br>Vt.16B -> result.val[0] | v7/A32/A64              |
| uint16x4x3_t vld1_u16_x3uint16_t const * ptr)    | ptr -> Xn            | LD1 (Vt.4H-Vt.3.4H)[Xn]   | Vt.3.4H -> result.val[2]<br>Vt.2.4H -> result.val[1]<br>Vt.4H -> result.val[0]    | v7/A32/A64              |
| uint16x8x3_t vld1q_u16_x3uint16_t const * ptr)   | ptr -> Xn            | LD1 (Vt.8H-Vt.3.8H)[Xn]   | Vt.3.8H -> result.val[2]<br>Vt.2.8H -> result.val[1]<br>Vt.8H -> result.val[0]    | v7/A32/A64              |
| uint32x2x3_t vld1q_x3uint32_t const * ptr)       | ptr -> Xn            | LD1 (Vt.2S-Vt.3.2S)[Xn]   | Vt.3.2S -> result.val[2]<br>Vt.2.2S -> result.val[1]<br>Vt.2S -> result.val[0]    | v7/A32/A64              |
| uint32x4x3_t vld1q_x32_x3uint32_t const * ptr)   | ptr -> Xn            | LD1 (Vt.4S-Vt.3.4S)[Xn]   | Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]    | v7/A32/A64              |
| float16x4x3_t vld1_f16_x3float16_t const * ptr)  | ptr -> Xn            | LD1 (Vt.4H-Vt.3.4H)[Xn]   | Vt.3.4H -> result.val[2]<br>Vt.2.4H -> result.val[1]<br>Vt.4H -> result.val[0]    | v7/A32/A64              |
| float16x8x3_t vld1q_f16_x3float16_t const * ptr) | ptr -> Xn            | LD1 (Vt.8H-Vt.3.8H)[Xn]   | Vt.3.8H -> result.val[2]<br>Vt.2.8H -> result.val[1]<br>Vt.8H -> result.val[0]    | v7/A32/A64              |
| float32x2x3_t vld1_f32_x3float32_t const * ptr)  | ptr -> Xn            | LD1 (Vt.2S-Vt.3.2S)[Xn]   | Vt.3.2S -> result.val[2]<br>Vt.2.2S -> result.val[1]<br>Vt.2S -> result.val[0]    | v7/A32/A64              |
| float32x4x3_t vld1q_f32_x3float32_t const * ptr) | ptr -> Xn            | LD1 (Vt.4S-Vt.3.4S)[Xn]   | Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]    | v7/A32/A64              |
| poly8x8x3_t vld1_p8_x3poly8_t const * ptr)       | ptr -> Xn            | LD1 (Vt.8B-Vt.3.8B)[Xn]   | Vt.3.8B -> result.val[2]<br>Vt.2.8B -> result.val[1]<br>Vt.8B -> result.val[0]    | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation | Instruction                 | Result                                                                                                 | Supported Architectures |
|---------------------------------------------------|----------------------|-----------------------------|--------------------------------------------------------------------------------------------------------|-------------------------|
| poly8x16x3_t vld1q_p8_x3(poly8_t const * ptr)     | ptr -> Xn            | LD1 [Vt.16B - Vt.3.16B][Xn] | Vt.3.16B -> resultval[2]<br>Vt.2.16B -> resultval[1]<br>Vt.1.16B -> resultval[0]                       | v7/A32/A64              |
| poly16x4x3_t vld1_p16_x3(poly16_t const * ptr)    | ptr -> Xn            | LD1 [Vt.4H - Vt.3.4H][Xn]   | Vt.3.4H -> resultval[2]<br>Vt.2.4H -> resultval[1]<br>Vt.4H -> resultval[0]                            | v7/A32/A64              |
| poly16x8x3_t vld1q_p16_x3(poly16_t const * ptr)   | ptr -> Xn            | LD1 [Vt.8H - Vt.3.8H][Xn]   | Vt.3.8H -> resultval[2]<br>Vt.2.8H -> resultval[1]<br>Vt.8H -> resultval[0]                            | v7/A32/A64              |
| int64x1x3_t vld1_s64_x3(int64_t const * ptr)      | ptr -> Xn            | LD1 [Vt.1D - Vt.3.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]                            | v7/A32/A64              |
| uint64x1x3_t vld1_u64_x3(uint64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt.3.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]                            | v7/A32/A64              |
| poly64x1x3_t vld1_p64_x3(poly64_t const * ptr)    | ptr -> Xn            | LD1 [Vt.1D - Vt.3.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]                            | A32/A64                 |
| int64x2x3_t vld1q_s64_x3(int64_t const * ptr)     | ptr -> Xn            | LD1 [Vt.2D - Vt.3.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]                            | v7/A32/A64              |
| uint64x2x3_t vld1q_u64_x3(uint64_t const * ptr)   | ptr -> Xn            | LD1 [Vt.2D - Vt.3.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]                            | v7/A32/A64              |
| poly64x2x3_t vld1q_p64_x3(poly64_t const * ptr)   | ptr -> Xn            | LD1 [Vt.2D - Vt.3.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]                            | A32/A64                 |
| float64x1x3_t vld1_f64_x3(float64_t const * ptr)  | ptr -> Xn            | LD1 [Vt.1D - Vt.3.1D][Xn]   | Vt.3.1D -> resultval[2]<br>Vt.2.1D -> resultval[1]<br>Vt.1D -> resultval[0]                            | A64                     |
| float64x2x3_t vld1q_f64_x3(float64_t const * ptr) | ptr -> Xn            | LD1 [Vt.2D - Vt.3.2D][Xn]   | Vt.3.2D -> resultval[2]<br>Vt.2.2D -> resultval[1]<br>Vt.2D -> resultval[0]                            | A64                     |
| int8x8x4_t vld1_s8_x4(int8_t const * ptr)         | ptr -> Xn            | LD1 [Vt.8B - Vt.4.8B][Xn]   | Vt.4.8B -> resultval[3]<br>Vt.3.8B -> resultval[2]<br>Vt.2.8B -> resultval[1]<br>Vt.8B -> resultval[0] | v7/A32/A64              |

| Intrinsic                                       | Argument Preparation | Instruction                | Result                                                                                                  | Supported Architectures |
|-------------------------------------------------|----------------------|----------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| int8x16x4_t vld1q_s8_x4(int8_t const * ptr)     | ptr -> Xn            | LD1 [Vt.16B - Vt4.16B][Xn] | Vt4.16B -> resultval[3]<br>Vt3.16B -> resultval[2]<br>Vt2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| int16x4x4_t vld1_s16_x4(int16_t const * ptr)    | ptr -> Xn            | LD1 [Vt.4H - Vt4.4H][Xn]   | Vt4.4H -> resultval[3]<br>Vt3.4H -> resultval[2]<br>Vt2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |
| int16x8x4_t vld1q_s16_x4(int16_t const * ptr)   | ptr -> Xn            | LD1 [Vt.8H - Vt4.8H][Xn]   | Vt4.8H -> resultval[3]<br>Vt3.8H -> resultval[2]<br>Vt2.8H -> resultval[1]<br>Vt.8H -> resultval[0]     | v7/A32/A64              |
| int32x2x4_t vld1_s32_x4(int32_t const * ptr)    | ptr -> Xn            | LD1 [Vt.2S - Vt4.2S][Xn]   | Vt4.2S -> resultval[3]<br>Vt3.2S -> resultval[2]<br>Vt2.2S -> resultval[1]<br>Vt.2S -> resultval[0]     | v7/A32/A64              |
| int32x4x4_t vld1q_s32_x4(int32_t const * ptr)   | ptr -> Xn            | LD1 [Vt.4S - Vt4.4S][Xn]   | Vt4.4S -> resultval[3]<br>Vt3.4S -> resultval[2]<br>Vt2.4S -> resultval[1]<br>Vt.4S -> resultval[0]     | v7/A32/A64              |
| uint8x8x4_t vld1_u8_x4(uint8_t const * ptr)     | ptr -> Xn            | LD1 [Vt.8B - Vt4.8B][Xn]   | Vt4.8B -> resultval[3]<br>Vt3.8B -> resultval[2]<br>Vt2.8B -> resultval[1]<br>Vt.8B -> resultval[0]     | v7/A32/A64              |
| uint8x16x4_t vld1q_u8_x4(uint8_t const * ptr)   | ptr -> Xn            | LD1 [Vt.16B - Vt4.16B][Xn] | Vt4.16B -> resultval[3]<br>Vt3.16B -> resultval[2]<br>Vt2.16B -> resultval[1]<br>Vt.16B -> resultval[0] | v7/A32/A64              |
| uint16x4x4_t vld1_u16_x4(uint16_t const * ptr)  | ptr -> Xn            | LD1 [Vt.4H - Vt4.4H][Xn]   | Vt4.4H -> resultval[3]<br>Vt3.4H -> resultval[2]<br>Vt2.4H -> resultval[1]<br>Vt.4H -> resultval[0]     | v7/A32/A64              |
| uint16x8x4_t vld1q_u16_x4(uint16_t const * ptr) | ptr -> Xn            | LD1 [Vt.8H - Vt4.8H][Xn]   | Vt4.8H -> resultval[3]<br>Vt3.8H -> resultval[2]<br>Vt2.8H -> resultval[1]<br>Vt.8H -> resultval[0]     | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation | Instruction               | Result                                                                                                       | Supported Architectures |
|---------------------------------------------------|----------------------|---------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------|
| uint32x2x4_t vld1_u32_x4(uint32_t const * ptr)    | ptr -> Xn            | LD1 [Vt.2S - Vt.2S][Xn]   | Vt.2S -> result.val[3]<br>Vt.3.2S -> result.val[2]<br>Vt.2.2S -> result.val[1]<br>Vt.2S -> result.val[0]     | v7/A32/A64              |
| uint32x4x4_t vld1q_u32_x4(uint32_t const * ptr)   | ptr -> Xn            | LD1 [Vt.4S - Vt.4S][Xn]   | Vt.4S -> result.val[3]<br>Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]     | v7/A32/A64              |
| float16x4x4_t vld1_f16_x4(float16_t const * ptr)  | ptr -> Xn            | LD1 [Vt.4H - Vt.4H][Xn]   | Vt.4H -> result.val[3]<br>Vt.3.4H -> result.val[2]<br>Vt.2.4H -> result.val[1]<br>Vt.4H -> result.val[0]     | v7/A32/A64              |
| float16x8x4_t vld1q_f16_x4(float16_t const * ptr) | ptr -> Xn            | LD1 [Vt.8H - Vt.8H][Xn]   | Vt.8H -> result.val[3]<br>Vt.3.8H -> result.val[2]<br>Vt.2.8H -> result.val[1]<br>Vt.8H -> result.val[0]     | v7/A32/A64              |
| float32x2x4_t vld1_f32_x4(float32_t const * ptr)  | ptr -> Xn            | LD1 [Vt.2S - Vt.2S][Xn]   | Vt.2S -> result.val[3]<br>Vt.3.2S -> result.val[2]<br>Vt.2.2S -> result.val[1]<br>Vt.2S -> result.val[0]     | v7/A32/A64              |
| float32x4x4_t vld1q_f32_x4(float32_t const * ptr) | ptr -> Xn            | LD1 [Vt.4S - Vt.4S][Xn]   | Vt.4S -> result.val[3]<br>Vt.3.4S -> result.val[2]<br>Vt.2.4S -> result.val[1]<br>Vt.4S -> result.val[0]     | v7/A32/A64              |
| poly8x8x4_t vld1_p8_x4(poly8_t const * ptr)       | ptr -> Xn            | LD1 [Vt.8B - Vt.8B][Xn]   | Vt.8B -> result.val[3]<br>Vt.3.8B -> result.val[2]<br>Vt.2.8B -> result.val[1]<br>Vt.8B -> result.val[0]     | v7/A32/A64              |
| poly8x16x4_t vld1q_p8_x4(poly8_t const * ptr)     | ptr -> Xn            | LD1 [Vt.16B - Vt.16B][Xn] | Vt.16B -> result.val[3]<br>Vt.3.16B -> result.val[2]<br>Vt.2.16B -> result.val[1]<br>Vt.16B -> result.val[0] | v7/A32/A64              |
| poly16x4x4_t vld1_p16_x4(poly16_t const * ptr)    | ptr -> Xn            | LD1 [Vt.4H - Vt.4H][Xn]   | Vt.4H -> result.val[3]<br>Vt.3.4H -> result.val[2]<br>Vt.2.4H -> result.val[1]<br>Vt.4H -> result.val[0]     | v7/A32/A64              |

| Intrinsic                                         | Argument Preparation     | Instruction                | Result                                                                                                  | Supported Architectures |
|---------------------------------------------------|--------------------------|----------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| poly16x8x4_t vld1q_p16_x4(poly16_t const * ptr)   | ptr -> Xn                | LD1 [Vt.8H - Vt4.8H], [Xn] | Vt4.8H -> result.val[3]<br>Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | v7/A32/A64              |
| int64x1x4_t vld1_s64_x4(int64_t const * ptr)      | ptr -> Xn                | LD1 [Vt.1D - Vt4.1D], [Xn] | Vt4.1D -> result.val[3]<br>Vt3.1D -> result.val[2]<br>Vt2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | v7/A32/A64              |
| uint64x1x4_t vld1_u64_x4(uint64_t const * ptr)    | ptr -> Xn                | LD1 [Vt.1D - Vt4.1D], [Xn] | Vt4.1D -> result.val[3]<br>Vt3.1D -> result.val[2]<br>Vt2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | v7/A32/A64              |
| poly64x1x4_t vld1_p64_x4(poly64_t const * ptr)    | ptr -> Xn                | LD1 [Vt.1D - Vt4.1D], [Xn] | Vt4.1D -> result.val[3]<br>Vt3.1D -> result.val[2]<br>Vt2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A32/A64                 |
| int64x2x4_t vld1q_s64_x4(int64_t const * ptr)     | ptr -> Xn                | LD1 [Vt.2D - Vt4.2D], [Xn] | Vt4.2D -> result.val[3]<br>Vt3.2D -> result.val[2]<br>Vt2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | v7/A32/A64              |
| uint64x2x4_t vld1q_u64_x4(uint64_t const * ptr)   | ptr -> Xn                | LD1 [Vt.2D - Vt4.2D], [Xn] | Vt4.2D -> result.val[3]<br>Vt3.2D -> result.val[2]<br>Vt2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | v7/A32/A64              |
| poly64x2x4_t vld1q_p64_x4(poly64_t const * ptr)   | ptr -> Xn                | LD1 [Vt.2D - Vt4.2D], [Xn] | Vt4.2D -> result.val[3]<br>Vt3.2D -> result.val[2]<br>Vt2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | A32/A64                 |
| float64x1x4_t vld1_f64_x4(float64_t const * ptr)  | ptr -> Xn                | LD1 [Vt.1D - Vt4.1D], [Xn] | Vt4.1D -> result.val[3]<br>Vt3.1D -> result.val[2]<br>Vt2.1D -> result.val[1]<br>Vt.1D -> result.val[0] | A64                     |
| float64x2x4_t vld1q_f64_x4(float64_t const * ptr) | ptr -> Xn                | LD1 [Vt.2D - Vt4.2D], [Xn] | Vt4.2D -> result.val[3]<br>Vt3.2D -> result.val[2]<br>Vt2.2D -> result.val[1]<br>Vt.2D -> result.val[0] | A64                     |
| int8x8_t vpadd_s8(int8x8_t a, int8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B | ADDP Vd.8B, Vn.8B, Vm.8B   | Vd.8B -> result                                                                                         | v7/A32/A64              |

| Intrinsic                                            | Argument Preparation       | Instruction               | Result           | Supported Architectures |
|------------------------------------------------------|----------------------------|---------------------------|------------------|-------------------------|
| int16x4_t vpadd_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | ADDP Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| int32x2_t vpadd_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | ADDP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint8x8_t vpadd_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | ADDP Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x4_t vpadd_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | ADDP Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint32x2_t vpadd_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | ADDP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| float32x2_t vpadd_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | FADDP Vd.2S,Vn.2S,Vm.2S   | Vd.2S -> result  | v7/A32/A64              |
| int8x16_t vpaddq_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | ADDP Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x8_t vpaddq_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | ADDP Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x4_t vpaddq_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | ADDP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| int64x2_t vpaddq_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | ADDP Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint8x16_t vpaddq_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ADDP Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x8_t vpaddq_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ADDP Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x4_t vpaddq_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | ADDP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint64x2_t vpaddq_u64(uint64x2_t a, uint64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | ADDP Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x4_t vpaddq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FADDP Vd.4S,Vn.4S,Vm.4S   | Vd.4S -> result  | A64                     |
| float64x2_t vpaddq_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FADDP Vd.2D,Vn.2D,Vm.2D   | Vd.2D -> result  | A64                     |
| int16x4_t vpaddl_s8(int8x8_t a)                      | a -> Vn.8B                 | SADDLP Vd.4H,Vn.8B        | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vpaddlq_s8(int8x16_t a)                    | a -> Vn.16B                | SADDLP Vd.8H,Vn.16B       | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vpaddl_s16(int16x4_t a)                    | a -> Vn.4H                 | SADDLP Vd.2S,Vn.4H        | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vpaddlq_s16(int16x8_t a)                   | a -> Vn.8H                 | SADDLP Vd.4S,Vn.8H        | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vpaddl_s32(int32x2_t a)                    | a -> Vn.2D                 | SADDLP Vd.1D,Vn.2D        | Vd.1D -> result  | v7/A32/A64              |
| int64x4_t vpaddlq_s32(int32x4_t a)                   | a -> Vn.4S                 | SADDLP Vd.2D,Vn.4S        | Vd.2D -> result  | v7/A32/A64              |
| uint16x4_t vpaddl_u8(uint8x8_t a)                    | a -> Vn.8B                 | UADDLP Vd.4H,Vn.8B        | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vpaddlq_u8(uint8x16_t a)                  | a -> Vn.16B                | UADDLP Vd.8H,Vn.16B       | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vpaddl_u16(uint16x4_t a)                  | a -> Vn.4H                 | UADDLP Vd.2S,Vn.4H        | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vpaddlq_u16(uint16x8_t a)                 | a -> Vn.8H                 | UADDLP Vd.4S,Vn.8H        | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vpaddl_u32(uint32x2_t a)                  | a -> Vn.2D                 | UADDLP Vd.1D,Vn.2D        | Vd.1D -> result  | v7/A32/A64              |
| uint64x4_t vpaddlq_u32(uint32x4_t a)                 | a -> Vn.4S                 | UADDLP Vd.2D,Vn.4S        | Vd.2D -> result  | v7/A32/A64              |
| int16x4_t vpaddl_s8(int16x4_t a, int8x8_t b)         | a -> Vd.4H<br>b -> Vn.8B   | SADALP Vd.4H,Vn.8B        | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vpaddlq_s8(int16x8_t a, int8x16_t b)       | a -> Vd.8H<br>b -> Vn.16B  | SADALP Vd.8H,Vn.16B       | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vpaddl_s16(int32x2_t a, int16x4_t b)       | a -> Vd.2S<br>b -> Vn.4H   | SADALP Vd.2S,Vn.4H        | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vpaddlq_s16(int32x4_t a, int16x8_t b)      | a -> Vd.4S<br>b -> Vn.8H   | SADALP Vd.4S,Vn.8H        | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vpaddl_s32(int64x2_t a, int32x4_t b)       | a -> Vd.1D<br>b -> Vn.2S   | SADALP Vd.1D,Vn.2S        | Vd.1D -> result  | v7/A32/A64              |
| int64x4_t vpaddlq_s32(int64x4_t a, int32x8_t b)      | a -> Vd.2D<br>b -> Vn.4S   | SADALP Vd.2D,Vn.4S        | Vd.2D -> result  | v7/A32/A64              |
| uint16x4_t vpaddl_u8(uint16x4_t a, uint8x8_t b)      | a -> Vd.4H<br>b -> Vn.8B   | UADALP Vd.4H,Vn.8B        | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vpaddlq_u8(uint16x8_t a, uint8x16_t b)    | a -> Vd.8H<br>b -> Vn.16B  | UADALP Vd.8H,Vn.16B       | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vpaddl_u16(uint32x2_t a, uint16x4_t b)    | a -> Vd.2S<br>b -> Vn.4H   | UADALP Vd.2S,Vn.4H        | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vpaddlq_u16(uint32x4_t a, uint16x8_t b)   | a -> Vd.4S<br>b -> Vn.8H   | UADALP Vd.4S,Vn.8H        | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vpaddl_u32(uint64x2_t a, uint32x4_t b)    | a -> Vd.1D<br>b -> Vn.2S   | UADALP Vd.1D,Vn.2S        | Vd.1D -> result  | v7/A32/A64              |
| uint64x4_t vpaddlq_u32(uint64x4_t a, uint32x8_t b)   | a -> Vd.2D<br>b -> Vn.4S   | UADALP Vd.2D,Vn.4S        | Vd.2D -> result  | v7/A32/A64              |
| int8x8_t vpmax_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | SMAXP Vd.8B,Vn.8B,Vm.8B   | Vd.8B -> result  | v7/A32/A64              |
| int16x4_t vpmax_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | SMAXP Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result  | v7/A32/A64              |

| Intrinsic                                              | Argument Preparation       | Instruction                | Result           | Supported Architectures |
|--------------------------------------------------------|----------------------------|----------------------------|------------------|-------------------------|
| int32x2_t vpmax_s32(int32x2_t a, int32x2_t b)          | a -> Vn.2S<br>b -> Vm.2S   | SMAXP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint8x8_t vpmax_u8(uint8x8_t a, uint8x8_t b)           | a -> Vn.8B<br>b -> Vm.8B   | UMAXP Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x4_t vpmax_u16(uint16x4_t a, uint16x4_t b)       | a -> Vn.4H<br>b -> Vm.4H   | UMAXP Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint32x2_t vpmax_u32(uint32x2_t a, uint32x2_t b)       | a -> Vn.2S<br>b -> Vm.2S   | UMAXP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| float32x2_t vpmax_f32(float32x2_t a, float32x2_t b)    | a -> Vn.2S<br>b -> Vm.2S   | FMAXP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| int8x16_t vpmaxq_s8(int8x16_t a, int8x16_t b)          | a -> Vn.16B<br>b -> Vm.16B | SMAXP Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x8_t vpmaxq_s16(int16x8_t a, int16x8_t b)         | a -> Vn.8H<br>b -> Vm.8H   | SMAXP Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x4_t vpmaxq_s32(int32x4_t a, int32x4_t b)         | a -> Vn.4S<br>b -> Vm.4S   | SMAXP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint8x16_t vpmaxq_u8(uint8x16_t a, uint8x16_t b)       | a -> Vn.16B<br>b -> Vm.16B | UMAXP Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x8_t vpmaxq_u16(uint16x8_t a, uint16x8_t b)      | a -> Vn.8H<br>b -> Vm.8H   | UMAXP Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x4_t vpmaxq_u32(uint32x4_t a, uint32x4_t b)      | a -> Vn.4S<br>b -> Vm.4S   | UMAXP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float32x4_t vpmaxq_f32(float32x4_t a, float32x4_t b)   | a -> Vn.4S<br>b -> Vm.4S   | FMAXP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vpmaxq_f64(float64x2_t a, float64x2_t b)   | a -> Vn.2D<br>b -> Vm.2D   | FMAXP Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| int8x8_t vpminq_s8(int8x8_t a, int8x8_t b)             | a -> Vn.8B<br>b -> Vm.8B   | SMINP Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| int16x4_t vpminq_s16(int16x4_t a, int16x4_t b)         | a -> Vn.4H<br>b -> Vm.4H   | SMINP Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| int32x2_t vpminq_s32(int32x2_t a, int32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S   | SMINP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| uint8x8_t vpminq_u8(uint8x8_t a, uint8x8_t b)          | a -> Vn.8B<br>b -> Vm.8B   | UMINP Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | v7/A32/A64              |
| uint16x4_t vpminq_u16(uint16x4_t a, uint16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | UMINP Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | v7/A32/A64              |
| uint32x2_t vpminq_u32(uint32x2_t a, uint32x2_t b)      | a -> Vn.2S<br>b -> Vm.2S   | UMINP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| float32x2_t vpminq_f32(float32x2_t a, float32x2_t b)   | a -> Vn.2S<br>b -> Vm.2S   | FMINP Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | v7/A32/A64              |
| int8x16_t vpminq_s8(int8x16_t a, int8x16_t b)          | a -> Vn.16B<br>b -> Vm.16B | SMINP Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x8_t vpminq_s16(int16x8_t a, int16x8_t b)         | a -> Vn.8H<br>b -> Vm.8H   | SMINP Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x4_t vpminq_s32(int32x4_t a, int32x4_t b)         | a -> Vn.4S<br>b -> Vm.4S   | SMINP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint8x16_t vpminq_u8(uint8x16_t a, uint8x16_t b)       | a -> Vn.16B<br>b -> Vm.16B | UMINP Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x8_t vpminq_u16(uint16x8_t a, uint16x8_t b)      | a -> Vn.8H<br>b -> Vm.8H   | UMINP Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x4_t vpminq_u32(uint32x4_t a, uint32x4_t b)      | a -> Vn.4S<br>b -> Vm.4S   | UMINP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float32x4_t vpminq_f32(float32x4_t a, float32x4_t b)   | a -> Vn.4S<br>b -> Vm.4S   | FMINP Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vpminq_f64(float64x2_t a, float64x2_t b)   | a -> Vn.2D<br>b -> Vm.2D   | FMINP Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x2_t vpmaxnm_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | FMAXNMP Vd.2S,Vn.2S,Vm.2S  | Vd.2S -> result  | A64                     |
| float32x4_t vpmaxnmq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FMAXNMP Vd.4S,Vn.4S,Vm.4S  | Vd.4S -> result  | A64                     |
| float64x2_t vpmaxnmq_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FMAXNMP Vd.2D,Vn.2D,Vm.2D  | Vd.2D -> result  | A64                     |
| float32x2_t vpminnm_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | FMINNMP Vd.2S,Vn.2S,Vm.2S  | Vd.2S -> result  | A64                     |
| float32x4_t vpminnmq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | FMINNMP Vd.4S,Vn.4S,Vm.4S  | Vd.4S -> result  | A64                     |
| float64x2_t vpminnmq_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | FMINNMP Vd.2D,Vn.2D,Vm.2D  | Vd.2D -> result  | A64                     |
| int64_t vppadd_s64(int64x2_t a)                        | a -> Vn.2D                 | ADDP Dd,Vn.2D              | Dd -> result     | A64                     |
| uint64_t vppadd_u64(uint64x2_t a)                      | a -> Vn.2D                 | ADDP Dd,Vn.2D              | Dd -> result     | A64                     |
| float32_t vppadd_f32(float32x2_t a)                    | a -> Vn.2S                 | FADDP Sd,Vn.2S             | Sd -> result     | A64                     |
| float64_t vppadd_f64(float64x2_t a)                    | a -> Vn.2D                 | FADDP Dd,Vn.2D             | Dd -> result     | A64                     |
| float32_t vpmaxs_f32(float32x2_t a)                    | a -> Vn.2S                 | FMAXP Sd,Vn.2S             | Sd -> result     | A64                     |

| Intrinsic                              | Argument Preparation | Instruction             | Result          | Supported Architectures |
|----------------------------------------|----------------------|-------------------------|-----------------|-------------------------|
| float64_t vpmaxqd_f64(float64x2_t a)   | a->Vn,2D             | FMAXP Dd,Vn,2D          | Dd->result      | A64                     |
| float32_t vpmins_f32(float32x2_t a)    | a->Vn,2S             | FMINP Sd,Vn,2S          | Sd->result      | A64                     |
| float64_t vpminqd_f64(float64x2_t a)   | a->Vn,2D             | FMINP Dd,Vn,2D          | Dd->result      | A64                     |
| float32_t vpmaxnms_f32(float32x2_t a)  | a->Vn,2S             | FMAXNMP Sd,Vn,2S        | Sd->result      | A64                     |
| float64_t vpmaxnqmd_f64(float64x2_t a) | a->Vn,2D             | FMAXNMP Dd,Vn,2D        | Dd->result      | A64                     |
| float32_t vpminnms_f32(float32x2_t a)  | a->Vn,2S             | FMINNMP Sd,Vn,2S        | Sd->result      | A64                     |
| float64_t vpminnqm_f64(float64x2_t a)  | a->Vn,2D             | FMINNMP Dd,Vn,2D        | Dd->result      | A64                     |
| int8_t vaddv_s8(int8x8_t a)            | a->Vn,8B             | ADDV Bd,Vn,8B           | Bd->result      | A64                     |
| int8_t vaddvq_s8(int8x16_t a)          | a->Vn,16B            | ADDV Bd,Vn,16B          | Bd->result      | A64                     |
| int16_t vaddv_s16(int16x4_t a)         | a->Vn,4H             | ADDV Hd,Vn,4H           | Hd->result      | A64                     |
| int16_t vaddvq_s16(int16x8_t a)        | a->Vn,8H             | ADDV Hd,Vn,8H           | Hd->result      | A64                     |
| int32_t vaddv_s32(int32x2_t a)         | a->Vn,2S             | ADDP Vd,2S,Vn,2S,Vm,2S  | Vd,S[0]->result | A64                     |
| int32_t vaddvq_s32(int32x4_t a)        | a->Vn,4S             | ADDV Sd,Vn,4S           | Sd->result      | A64                     |
| int64_t vaddvq_s64(int64x2_t a)        | a->Vn,2D             | ADDP Dd,Vn,2D           | Dd->result      | A64                     |
| uint8_t vaddv_u8(uint8x8_t a)          | a->Vn,8B             | ADDV Bd,Vn,8B           | Bd->result      | A64                     |
| uint8_t vaddvq_u8(uint8x16_t a)        | a->Vn,16B            | ADDV Bd,Vn,16B          | Bd->result      | A64                     |
| uint16_t vaddv_u16(uint16x4_t a)       | a->Vn,4H             | ADDV Hd,Vn,4H           | Hd->result      | A64                     |
| uint16_t vaddvq_u16(uint16x8_t a)      | a->Vn,8H             | ADDV Hd,Vn,8H           | Hd->result      | A64                     |
| uint32_t vaddvq_u32(uint32x2_t a)      | a->Vn,2S             | ADDP Vd,2S,Vn,2S,Vm,2S  | Vd,S[0]->result | A64                     |
| uint32_t vaddvq_u32(uint32x4_t a)      | a->Vn,4S             | ADDV Sd,Vn,4S           | Sd->result      | A64                     |
| uint64_t vaddvq_u64(uint64x2_t a)      | a->Vn,2D             | ADDP Dd,Vn,2D           | Dd->result      | A64                     |
| float32_t vaddv_f32(float32x2_t a)     | a->Vn,2S             | FADDP Sd,Vn,2S          | Sd->result      | A64                     |
| float32_t vaddvq_f32(float32x4_t a)    | a->Vn,4S             | FADDP Vt,4S,Vn,4S,Vm,4S | Sd->result      | A64                     |
| float64_t vaddvq_f64(float64x2_t a)    | a->Vn,2D             | FADDP Sd,Vn,2D          | Sd->result      | A64                     |
| int16_t vaddlv_s16(int16x8_t a)        | a->Vn,8H             | SADDLV Hd,Vn,8B         | Hd->result      | A64                     |
| int16_t vaddlvq_s16(int16x16_t a)      | a->Vn,16B            | SADDLV Hd,Vn,16B        | Hd->result      | A64                     |
| int32_t vaddlv_s32(int32x2_t a)        | a->Vn,4H             | SADDLV Sd,Vn,4H         | Sd->result      | A64                     |
| int32_t vaddlvq_s32(int32x4_t a)       | a->Vn,8H             | SADDLV Sd,Vn,8H         | Sd->result      | A64                     |
| int64_t vaddlvq_s32(int32x4_t a)       | a->Vn,2S             | SADDLP Vd,1D,Vn,2S      | Vd->result      | A64                     |
| int64_t vaddlvq_s32(int32x4_t a)       | a->Vn,4S             | SADDLV Dd,Vn,4S         | Dd->result      | A64                     |
| uint16_t vaddlv_u16(uint16x8_t a)      | a->Vn,8B             | UADDLV Hd,Vn,8B         | Hd->result      | A64                     |
| uint16_t vaddlvq_u16(uint16x16_t a)    | a->Vn,16B            | UADDLV Hd,Vn,16B        | Hd->result      | A64                     |
| uint32_t vaddlvq_u32(uint32x2_t a)     | a->Vn,4H             | UADDLV Sd,Vn,4H         | Sd->result      | A64                     |
| uint32_t vaddlvq_u32(uint32x4_t a)     | a->Vn,8H             | UADDLV Sd,Vn,8H         | Sd->result      | A64                     |
| uint64_t vaddlvq_u32(uint32x4_t a)     | a->Vn,2S             | UADDLP Vd,1D,Vn,2S      | Vd->result      | A64                     |
| uint64_t vaddlvq_u32(uint32x4_t a)     | a->Vn,4S             | UADDLV Dd,Vn,4S         | Dd->result      | A64                     |
| int8_t vmavx_s8(int8x8_t a)            | a->Vn,8B             | SMAXV Bd,Vn,8B          | Bd->result      | A64                     |
| int8_t vmavxq_s8(int8x16_t a)          | a->Vn,16B            | SMAXV Bd,Vn,16B         | Bd->result      | A64                     |
| int16_t vmavx_s16(int16x4_t a)         | a->Vn,4H             | SMAXV Hd,Vn,4H          | Hd->result      | A64                     |
| int16_t vmavxq_s16(int16x8_t a)        | a->Vn,8H             | SMAXV Hd,Vn,8H          | Hd->result      | A64                     |
| int32_t vmavx_s32(int32x2_t a)         | a->Vn,2S             | SMAXP Vd,2S,Vn,2S,Vm,2S | Vd,S[0]->result | A64                     |
| int32_t vmavxq_s32(int32x4_t a)        | a->Vn,4S             | SMAXV Sd,Vn,4S          | Sd->result      | A64                     |
| uint8_t vmavx_u8(uint8x8_t a)          | a->Vn,8B             | UMAXV Bd,Vn,8B          | Bd->result      | A64                     |
| uint8_t vmavxq_u8(uint8x16_t a)        | a->Vn,16B            | UMAXV Bd,Vn,16B         | Bd->result      | A64                     |
| uint16_t vmavx_u16(uint16x4_t a)       | a->Vn,4H             | UMAXV Hd,Vn,4H          | Hd->result      | A64                     |
| uint16_t vmavxq_u16(uint16x8_t a)      | a->Vn,8H             | UMAXV Hd,Vn,8H          | Hd->result      | A64                     |
| uint32_t vmavxq_u32(uint32x2_t a)      | a->Vn,2S             | UMAXP Vd,2S,Vn,2S,Vm,2S | Vd,S[0]->result | A64                     |
| uint32_t vmavxq_u32(uint32x4_t a)      | a->Vn,4S             | UMAXV Sd,Vn,4S          | Sd->result      | A64                     |
| float32_t vmavx_f32(float32x2_t a)     | a->Vn,2S             | FMAXP Sd,Vn,2S          | Sd->result      | A64                     |
| float32_t vmavxq_f32(float32x4_t a)    | a->Vn,4S             | FMAXP Sd,Vn,4S          | Sd->result      | A64                     |
| float64_t vmavxq_f64(float64x2_t a)    | a->Vn,2D             | FMAXP Dd,Vn,2D          | Dd->result      | A64                     |
| int8_t vminv_s8(int8x8_t a)            | a->Vn,8B             | SMINV Bd,Vn,8B          | Bd->result      | A64                     |
| int8_t vminvq_s8(int8x16_t a)          | a->Vn,16B            | SMINV Bd,Vn,16B         | Bd->result      | A64                     |
| int16_t vminv_s16(int16x4_t a)         | a->Vn,4H             | SMINV Hd,Vn,4H          | Hd->result      | A64                     |
| int16_t vminvq_s16(int16x8_t a)        | a->Vn,8H             | SMINV Hd,Vn,8H          | Hd->result      | A64                     |
| int32_t vminv_s32(int32x2_t a)         | a->Vn,2S             | SMINP Vd,2S,Vn,2S,Vm,2S | Vd,S[0]->result | A64                     |
| int32_t vminvq_s32(int32x4_t a)        | a->Vn,4S             | SMINV Sd,Vn,4S          | Sd->result      | A64                     |
| uint8_t vminvq_u8(uint8x8_t a)         | a->Vn,8B             | UMINV Bd,Vn,8B          | Bd->result      | A64                     |
| uint8_t vminvq_u8(uint8x16_t a)        | a->Vn,16B            | UMINV Bd,Vn,16B         | Bd->result      | A64                     |
| uint16_t vminvq_u16(uint16x4_t a)      | a->Vn,4H             | UMINV Hd,Vn,4H          | Hd->result      | A64                     |
| uint16_t vminvq_u16(uint16x8_t a)      | a->Vn,8H             | UMINV Hd,Vn,8H          | Hd->result      | A64                     |
| uint32_t vminvq_u32(uint32x2_t a)      | a->Vn,2S             | UMINP Vd,2S,Vn,2S,Vm,2S | Vd,S[0]->result | A64                     |
| uint32_t vminvq_u32(uint32x4_t a)      | a->Vn,4S             | UMINV Sd,Vn,4S          | Sd->result      | A64                     |
| float32_t vminv_f32(float32x2_t a)     | a->Vn,2S             | FMINP Sd,Vn,2S          | Sd->result      | A64                     |
| float32_t vminvq_f32(float32x4_t a)    | a->Vn,4S             | FMINP Sd,Vn,4S          | Sd->result      | A64                     |
| float64_t vminvq_f64(float64x2_t a)    | a->Vn,2D             | FMINP Dd,Vn,2D          | Dd->result      | A64                     |

| Intrinsic                                                        | Argument Preparation                       | Instruction                      | Result           | Supported Architectures |
|------------------------------------------------------------------|--------------------------------------------|----------------------------------|------------------|-------------------------|
| float32_t vmlmqd_f32(float32x4_t a)                              | a -> Vn,4S                                 | FMINM Sd,Vn,4S                   | Sd -> result     | A64                     |
| float64_t vmlmqd_f64(float64x2_t a)                              | a -> Vn,2D                                 | FMINM Dd,Vn,2D                   | Dd -> result     | A64                     |
| float32_t vmnmmqd_f32(float32x2_t a)                             | a -> Vn,2S                                 | FMAXNM Mp,Vn,2S                  | Sd -> result     | A64                     |
| float32_t vmnmmqd_f32(float32x4_t a)                             | a -> Vn,4S                                 | FMAXNM Sd,Vn,4S                  | Sd -> result     | A64                     |
| float64_t vmnmmqd_f64(float64x2_t a)                             | a -> Vn,2D                                 | FMAXNM Dd,Vn,2D                  | Dd -> result     | A64                     |
| float32_t vmnmmqd_f32(float32x2_t a)                             | a -> Vn,2S                                 | FMINMMP Sd,Vn,2S                 | Sd -> result     | A64                     |
| float32_t vmnmmqd_f32(float32x4_t a)                             | a -> Vn,4S                                 | FMINMMP Sd,Vn,4S                 | Sd -> result     | A64                     |
| float64_t vmnmmqd_f64(float64x2_t a)                             | a -> Vn,2D                                 | FMINMMP Dd,Vn,2D                 | Dd -> result     | A64                     |
| int8x8_t vextq_s8(int8x8_t a, int8x8_t b, const int n)           | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 7    | EXT Vd,BB,Vn,BB,Vm,BB,#n         | Vd,BB -> result  | V7/A32/A64              |
| int8x16_t vextq_s8(int8x16_t a, int8x16_t b, const int n)        | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 15 | EXT Vd,16B,Vn,16B,Vm,16B,#n      | Vd,16B -> result | V7/A32/A64              |
| int16x4_t vextq_s16(int16x4_t a, int16x4_t b, const int n)       | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 3    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<1)    | Vd,BB -> result  | V7/A32/A64              |
| int16x8_t vextq_s16(int16x8_t a, int16x8_t b, const int n)       | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 7  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<1) | Vd,16B -> result | V7/A32/A64              |
| int32x2_t vextq_s32(int32x2_t a, int32x2_t b, const int n)       | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<2)    | Vd,BB -> result  | V7/A32/A64              |
| int32x4_t vextq_s32(int32x4_t a, int32x4_t b, const int n)       | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 3  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<2) | Vd,16B -> result | V7/A32/A64              |
| int64x1_t vextq_s64(int64x1_t a, int64x1_t b, const int n)       | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<3)    | Vd,BB -> result  | V7/A32/A64              |
| int64x2_t vextq_s64(int64x2_t a, int64x2_t b, const int n)       | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 3  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<3) | Vd,16B -> result | V7/A32/A64              |
| uint8x8_t vextq_u8(uint8x8_t a, uint8x8_t b, const int n)        | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 7    | EXT Vd,BB,Vn,BB,Vm,BB,#n         | Vd,BB -> result  | V7/A32/A64              |
| uint8x16_t vextq_u8(uint8x16_t a, uint8x16_t b, const int n)     | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 15 | EXT Vd,16B,Vn,16B,Vm,16B,#n      | Vd,16B -> result | V7/A32/A64              |
| uint16x4_t vextq_u16(uint16x4_t a, uint16x4_t b, const int n)    | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 3    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<1)    | Vd,BB -> result  | V7/A32/A64              |
| uint16x8_t vextq_u16(uint16x8_t a, uint16x8_t b, const int n)    | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 7  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<1) | Vd,16B -> result | V7/A32/A64              |
| uint32x2_t vextq_u32(uint32x2_t a, uint32x2_t b, const int n)    | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<2)    | Vd,BB -> result  | V7/A32/A64              |
| uint32x4_t vextq_u32(uint32x4_t a, uint32x4_t b, const int n)    | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 3  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<2) | Vd,16B -> result | V7/A32/A64              |
| uint64x1_t vextq_u64(uint64x1_t a, uint64x1_t b, const int n)    | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<3)    | Vd,BB -> result  | V7/A32/A64              |
| uint64x2_t vextq_u64(uint64x2_t a, uint64x2_t b, const int n)    | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 3  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<3) | Vd,16B -> result | V7/A32/A64              |
| poly64x1_t vextq_p64(poly64x1_t a, poly64x1_t b, const int n)    | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<3)    | Vd,BB -> result  | A32/A64                 |
| poly64x2_t vextq_p64(poly64x2_t a, poly64x2_t b, const int n)    | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 3  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<3) | Vd,16B -> result | A32/A64                 |
| float32x2_t vext_f32(float32x2_t a, float32x2_t b, const int n)  | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<2)    | Vd,BB -> result  | V7/A32/A64              |
| float32x4_t vextq_f32(float32x4_t a, float32x4_t b, const int n) | a -> Vn,16B<br>b -> Vm,16B<br>0 <= n <= 3  | EXT Vd,16B,Vn,16B,Vm,16B,#(n<<2) | Vd,16B -> result | V7/A32/A64              |
| float64x1_t vext_f64(float64x1_t a, float64x1_t b, const int n)  | a -> Vn,BB<br>b -> Vm,BB<br>0 <= n <= 1    | EXT Vd,BB,Vn,BB,Vm,BB,#(n<<3)    | Vd,BB -> result  | A64                     |

| Intrinsic                                                        | Argument Preparation                       | Instruction                     | Result           | Supported Architectures |
|------------------------------------------------------------------|--------------------------------------------|---------------------------------|------------------|-------------------------|
| float64x2_t vextq_f64(float64x2_t a, float64x2_t b, const int n) | a -> Vn.16B<br>b -> Vm.16B<br>0 <= n <= 7  | EXT Vd.16B.Vn.16B.Vm.16B.#(n<3) | Vd.16B -> result | A64                     |
| poly8x8_t vext_p8(poly8x8_t a, poly8x8_t b, const int n)         | a -> Vn.8B<br>b -> Vm.8B<br>0 <= n <= 7    | EXT V0.8B.Vn.8B.Vm.8B.#n        | V0.8B -> result  | v7/A32/A64              |
| poly8x16_t vextq_p8(poly8x16_t a, poly8x16_t b, const int n)     | a -> Vn.16B<br>b -> Vm.16B<br>0 <= n <= 15 | EXT Vd.16B.Vn.16B.Vm.16B.#n     | Vd.16B -> result | v7/A32/A64              |
| poly16x8_t vext_p16(poly16x8_t a, poly16x8_t b, const int n)     | a -> Vn.8B<br>b -> Vm.8B<br>0 <= n <= 7    | EXT V0.8B.Vn.8B.Vm.8B.#(n<1)    | V0.8B -> result  | v7/A32/A64              |
| poly16x8_t vextq_p16(poly16x8_t a, poly16x8_t b, const int n)    | a -> Vn.16B<br>b -> Vm.16B<br>0 <= n <= 7  | EXT Vd.16B.Vn.16B.Vm.16B.#(n<1) | Vd.16B -> result | v7/A32/A64              |
| int8x8_t vrevd_8(int8x8_t vec)                                   | vec -> Vn.8B                               | REVd Vd.8B.Vn.8B                | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vrevd_8q_8q(int8x16_t vec)                             | Vn.16B                                     | REVd Vd.16B.Vn.16B              | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vrevd_4(int16x4_t vec)                                 | vec -> Vn.4H                               | REVd Vd.4H.Vn.4H                | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vrevd_4q_4q(int16x8_t vec)                             | vec -> Vn.8H                               | REVd Vd.8H.Vn.8H                | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vrevd_4(int32x2_t vec)                                 | vec -> Vn.2S                               | REVd Vd.2S.Vn.2S                | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vrevd_4q_4q(int32x4_t vec)                             | vec -> Vn.4S                               | REVd Vd.4S.Vn.4S                | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vrevd_8(uint8x8_t vec)                                 | vec -> Vn.8B                               | REVd Vd.8B.Vn.8B                | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vrevd_8q_8q(uint8x16_t vec)                           | vec -> Vn.16B                              | REVd Vd.16B.Vn.16B              | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vrevd_4(uint16x4_t vec)                               | vec -> Vn.4H                               | REVd Vd.4H.Vn.4H                | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vrevd_4q_4q(uint16x8_t vec)                           | vec -> Vn.8H                               | REVd Vd.8H.Vn.8H                | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vrevd_4(uint32x2_t vec)                               | vec -> Vn.2S                               | REVd Vd.2S.Vn.2S                | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vrevd_4q_4q(uint32x4_t vec)                           | vec -> Vn.4S                               | REVd Vd.4S.Vn.4S                | Vd.4S -> result  | v7/A32/A64              |
| poly8x8_t vrevd_8(poly8x8_t vec)                                 | vec -> Vn.8B                               | REVd Vd.8B.Vn.8B                | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vrevd_8q_8q(poly8x16_t vec)                           | Vn.16B                                     | REVd Vd.16B.Vn.16B              | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vrevd_4(poly16x4_t vec)                               | vec -> Vn.4H                               | REVd Vd.4H.Vn.4H                | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vrevd_4q_4q(poly16x8_t vec)                           | vec -> Vn.8H                               | REVd Vd.8H.Vn.8H                | Vd.8H -> result  | v7/A32/A64              |
| int8x8_t vrev32_8(int8x8_t vec)                                  | vec -> Vn.8B                               | REV32 Vd.8B.Vn.8B               | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vrev32_8q_8q(int8x16_t vec)                            | Vn.16B                                     | REV32 Vd.16B.Vn.16B             | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vrev32_4(int16x4_t vec)                                | vec -> Vn.4H                               | REV32 Vd.4H.Vn.4H               | Vd.4H -> result  | v7/A32/A64              |
| int16x8_t vrev32_4q_4q(int16x8_t vec)                            | vec -> Vn.8H                               | REV32 Vd.8H.Vn.8H               | Vd.8H -> result  | v7/A32/A64              |
| int32x2_t vrev32_2(int32x2_t vec)                                | vec -> Vn.2S                               | REV32 Vd.2S.Vn.2S               | Vd.2S -> result  | v7/A32/A64              |
| int32x4_t vrev32_4q_4q(int32x4_t vec)                            | vec -> Vn.4S                               | REV32 Vd.4S.Vn.4S               | Vd.4S -> result  | v7/A32/A64              |
| uint8x8_t vrev32_8(uint8x8_t vec)                                | vec -> Vn.8B                               | REV32 Vd.8B.Vn.8B               | Vd.8B -> result  | v7/A32/A64              |
| uint8x16_t vrev32_8q_8q(uint8x16_t vec)                          | Vn.16B                                     | REV32 Vd.16B.Vn.16B             | Vd.16B -> result | v7/A32/A64              |
| uint16x4_t vrev32_4(uint16x4_t vec)                              | vec -> Vn.4H                               | REV32 Vd.4H.Vn.4H               | Vd.4H -> result  | v7/A32/A64              |
| uint16x8_t vrev32_4q_4q(uint16x8_t vec)                          | vec -> Vn.8H                               | REV32 Vd.8H.Vn.8H               | Vd.8H -> result  | v7/A32/A64              |
| uint32x2_t vrev32_2(uint32x2_t vec)                              | vec -> Vn.2S                               | REV32 Vd.2S.Vn.2S               | Vd.2S -> result  | v7/A32/A64              |
| uint32x4_t vrev32_4q_4q(uint32x4_t vec)                          | vec -> Vn.4S                               | REV32 Vd.4S.Vn.4S               | Vd.4S -> result  | v7/A32/A64              |
| poly8x8_t vrev32_8(poly8x8_t vec)                                | vec -> Vn.8B                               | REV32 Vd.8B.Vn.8B               | Vd.8B -> result  | v7/A32/A64              |
| poly8x16_t vrev32_8q_8q(poly8x16_t vec)                          | Vn.16B                                     | REV32 Vd.16B.Vn.16B             | Vd.16B -> result | v7/A32/A64              |
| poly16x4_t vrev32_4(poly16x4_t vec)                              | vec -> Vn.4H                               | REV32 Vd.4H.Vn.4H               | Vd.4H -> result  | v7/A32/A64              |
| poly16x8_t vrev32_4q_4q(poly16x8_t vec)                          | vec -> Vn.8H                               | REV32 Vd.8H.Vn.8H               | Vd.8H -> result  | v7/A32/A64              |
| int8x8_t vextv_8(int8x8_t vec)                                   | vec -> Vn.8B                               | EXT Vd.8B.Vn.8B                 | Vd.8B -> result  | v7/A32/A64              |
| int8x16_t vextv_16_8(int8x16_t vec)                              | vec -> Vn.16B                              | EXT Vd.16B.Vn.16B               | Vd.16B -> result | v7/A32/A64              |
| int16x4_t vextq_16(int16x4_t a, int16x4_t b)                     | a -> Vn.4H<br>b -> Vm.4H                   | ZIP1 Vd.4H.Vn.4H.Vm.4H          | Vd.4H -> result  | A64                     |
| int16x8_t vextq_16_16(int16x8_t a, int16x8_t b)                  | a -> Vn.8H<br>b -> Vm.8H                   | ZIP1 Vd.8H.Vn.8H.Vm.8H          | Vd.8H -> result  | A64                     |
| int32x2_t vextq_16_16(int32x2_t a, int32x2_t b)                  | a -> Vn.2S<br>b -> Vm.2S                   | ZIP1 Vd.2S.Vn.2S.Vm.2S          | Vd.2S -> result  | A64                     |
| int32x4_t vextq_16_16(int32x4_t a, int32x4_t b)                  | a -> Vn.4S<br>b -> Vm.4S                   | ZIP1 Vd.4S.Vn.4S.Vm.4S          | Vd.4S -> result  | A64                     |

| Intrinsic                                            | Argument Preparation       | Instruction               | Result           | Supported Architectures |
|------------------------------------------------------|----------------------------|---------------------------|------------------|-------------------------|
| int64x2_t vzip1q_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | ZIP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint8x8_t vzip1_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | ZIP1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| uint8x16_t vzip1q_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ZIP1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x4_t vzip1_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | ZIP1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| uint16x8_t vzip1q_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ZIP1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x2_t vzip1_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | ZIP1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| uint32x4_t vzip1q_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | ZIP1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint64x2_t vzip1q_u64(uint64x2_t a, uint64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | ZIP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly64x2_t vzip1p64(poly64x2_t a, poly64x2_t b)      | a -> Vn.2D<br>b -> Vm.2D   | ZIP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x2_t vzip1_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | ZIP1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| float32x4_t vzip1q_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | ZIP1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vzip1q_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | ZIP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly8x8_t vzip1_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | ZIP1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| poly8x16_t vzip1q_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ZIP1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| poly16x4_t vzip1p16(poly16x4_t a, poly16x4_t b)      | a -> Vn.4H<br>b -> Vm.4H   | ZIP1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| poly16x8_t vzip1q_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ZIP1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int8x8_t vzip2_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | ZIP2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| int8x16_t vzip2q_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | ZIP2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x4_t vzip2_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | ZIP2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| int16x8_t vzip2q_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | ZIP2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x2_t vzip2_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | ZIP2 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| int32x4_t vzip2q_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | ZIP2 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| int64x2_t vzip2q_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | ZIP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint8x8_t vzip2_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | ZIP2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| uint8x16_t vzip2q_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ZIP2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x4_t vzip2_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | ZIP2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| uint16x8_t vzip2q_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ZIP2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x2_t vzip2_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | ZIP2 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| uint32x4_t vzip2q_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | ZIP2 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint64x2_t vzip2q_u64(uint64x2_t a, uint64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | ZIP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly64x2_t vzip2p64(poly64x2_t a, poly64x2_t b)      | a -> Vn.2D<br>b -> Vm.2D   | ZIP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x2_t vzip2_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | ZIP2 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| float32x4_t vzip2q_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | ZIP2 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vzip2q_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | ZIP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly8x8_t vzip2_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | ZIP2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| poly8x16_t vzip2q_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ZIP2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |

| Intrinsic                                            | Argument Preparation       | Instruction               | Result           | Supported Architectures |
|------------------------------------------------------|----------------------------|---------------------------|------------------|-------------------------|
| poly16x4_t vzip2_p16(poly16x4_t a, poly16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | ZIP2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| poly16x8_t vzip2q_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ZIP2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int8x8_t vuzp1_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | UZP1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| int8x16_t vuzp1q_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | UZP1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x4_t vuzp1_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | UZP1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| int16x8_t vuzp1q_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | UZP1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x2_t vuzp1_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | UZP1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| int32x4_t vuzp1q_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | UZP1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| int64x2_t vuzp1q_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | UZP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint8x8_t vuzp1_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UZP1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| uint8x16_t vuzp1q_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UZP1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x4_t vuzp1_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UZP1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| uint16x8_t vuzp1q_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UZP1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x2_t vuzp1_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | UZP1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| uint32x4_t vuzp1q_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | UZP1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint64x2_t vuzp1q_u64(uint64x2_t a, uint64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | UZP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly64x2_t vuzp1q_p64(poly64x2_t a, poly64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | UZP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x2_t vuzp1_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | UZP1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| float32x4_t vuzp1q_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | UZP1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vuzp1q_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | UZP1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly8x8_t vuzp1_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UZP1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| poly8x16_t vuzp1q_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UZP1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| poly16x4_t vuzp1_p16(poly16x4_t a, poly16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UZP1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| poly16x8_t vuzp1q_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UZP1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int8x8_t vuzp2_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | UZP2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| int8x16_t vuzp2q_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | UZP2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x4_t vuzp2_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | UZP2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| int16x8_t vuzp2q_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | UZP2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x2_t vuzp2_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | UZP2 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| int32x4_t vuzp2q_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | UZP2 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| int64x2_t vuzp2q_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | UZP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint8x8_t vuzp2_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UZP2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| uint8x16_t vuzp2q_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UZP2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x4_t vuzp2_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UZP2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| uint16x8_t vuzp2q_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UZP2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x2_t vuzp2_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | UZP2 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |

| Intrinsic                                            | Argument Preparation       | Instruction               | Result           | Supported Architectures |
|------------------------------------------------------|----------------------------|---------------------------|------------------|-------------------------|
| uint32x4_t vuzp2q_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | UZP2 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint64x2_t vuzp2q_u64(uint64x2_t a, uint64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | UZP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly64x2_t vuzp2q_p64(poly64x2_t a, poly64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | UZP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x2_t vuzp2_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | UZP2 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| float32x4_t vuzp2q_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | UZP2 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vuzp2q_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | UZP2 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly8x8_t vuzp2_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UZP2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| poly8x16_t vuzp2q_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UZP2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| poly16x4_t vuzp2_p16(poly16x4_t a, poly16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UZP2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| poly16x8_t vuzp2q_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UZP2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int8x8_t vtrn1_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | TRN1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| int8x16_t vtrn1q_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | TRN1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x4_t vtrn1_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | TRN1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| int16x8_t vtrn1q_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | TRN1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int32x2_t vtrn1_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | TRN1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| int32x4_t vtrn1q_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | TRN1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| int64x2_t vtrn1q_s64(int64x2_t a, int64x2_t b)       | a -> Vn.2D<br>b -> Vm.2D   | TRN1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| uint8x8_t vtrn1_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | TRN1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| uint8x16_t vtrn1q_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | TRN1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| uint16x4_t vtrn1_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | TRN1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| uint16x8_t vtrn1q_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | TRN1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| uint32x2_t vtrn1_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | TRN1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| uint32x4_t vtrn1q_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | TRN1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| uint64x2_t vtrn1q_u64(uint64x2_t a, uint64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | TRN1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly64x2_t vtrn1q_p64(poly64x2_t a, poly64x2_t b)    | a -> Vn.2D<br>b -> Vm.2D   | TRN1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| float32x2_t vtrn1_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | TRN1 Vd.2S,Vn.2S,Vm.2S    | Vd.2S -> result  | A64                     |
| float32x4_t vtrn1q_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | TRN1 Vd.4S,Vn.4S,Vm.4S    | Vd.4S -> result  | A64                     |
| float64x2_t vtrn1q_f64(float64x2_t a, float64x2_t b) | a -> Vn.2D<br>b -> Vm.2D   | TRN1 Vd.2D,Vn.2D,Vm.2D    | Vd.2D -> result  | A64                     |
| poly8x8_t vtrn1_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | TRN1 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| poly8x16_t vtrn1q_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | TRN1 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| poly16x4_t vtrn1_p16(poly16x4_t a, poly16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | TRN1 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| poly16x8_t vtrn1q_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | TRN1 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |
| int8x8_t vtrn2_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | TRN2 Vd.8B,Vn.8B,Vm.8B    | Vd.8B -> result  | A64                     |
| int8x16_t vtrn2q_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | TRN2 Vd.16B,Vn.16B,Vm.16B | Vd.16B -> result | A64                     |
| int16x4_t vtrn2_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | TRN2 Vd.4H,Vn.4H,Vm.4H    | Vd.4H -> result  | A64                     |
| int16x8_t vtrn2q_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | TRN2 Vd.8H,Vn.8H,Vm.8H    | Vd.8H -> result  | A64                     |

| Intrinsic                                                   | Argument Preparation                                          | Instruction                                                                                                | Result           | Supported Architectures |
|-------------------------------------------------------------|---------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|------------------|-------------------------|
| int32x2_t vtrn2_s32(int32x2_t a, int32x2_t b)               | a -> Vn.2S<br>b -> Vm.2S                                      | TRN2 Vd.2S,Vn.2S,Vm.2S                                                                                     | Vd.2S -> result  | A64                     |
| int32x4_t vtrn2q_s32(int32x4_t a, int32x4_t b)              | a -> Vn.4S<br>b -> Vm.4S                                      | TRN2 Vd.4S,Vn.4S,Vm.4S                                                                                     | Vd.4S -> result  | A64                     |
| int64x2_t vtrn2q_s64(int64x2_t a, int64x2_t b)              | a -> Vn.2D<br>b -> Vm.2D                                      | TRN2 Vd.2D,Vn.2D,Vm.2D                                                                                     | Vd.2D -> result  | A64                     |
| uint8x8_t vtrn2_u8(uint8x8_t a, uint8x8_t b)                | a -> Vn.8B<br>b -> Vm.8B                                      | TRN2 Vd.8B,Vn.8B,Vm.8B                                                                                     | Vd.8B -> result  | A64                     |
| uint8x16_t vtrn2q_u8(uint8x16_t a, uint8x16_t b)            | a -> Vn.16B<br>b -> Vm.16B                                    | TRN2 Vd.16B,Vn.16B,Vm.16B                                                                                  | Vd.16B -> result | A64                     |
| uint16x4_t vtrn2_u16(uint16x4_t a, uint16x4_t b)            | a -> Vn.4H<br>b -> Vm.4H                                      | TRN2 Vd.4H,Vn.4H,Vm.4H                                                                                     | Vd.4H -> result  | A64                     |
| uint16x8_t vtrn2q_u16(uint16x8_t a, uint16x8_t b)           | a -> Vn.8H<br>b -> Vm.8H                                      | TRN2 Vd.8H,Vn.8H,Vm.8H                                                                                     | Vd.8H -> result  | A64                     |
| uint32x2_t vtrn2_u32(uint32x2_t a, uint32x2_t b)            | a -> Vn.2S<br>b -> Vm.2S                                      | TRN2 Vd.2S,Vn.2S,Vm.2S                                                                                     | Vd.2S -> result  | A64                     |
| uint32x4_t vtrn2q_u32(uint32x4_t a, uint32x4_t b)           | a -> Vn.4S<br>b -> Vm.4S                                      | TRN2 Vd.4S,Vn.4S,Vm.4S                                                                                     | Vd.4S -> result  | A64                     |
| uint64x2_t vtrn2q_u64(uint64x2_t a, uint64x2_t b)           | a -> Vn.2D<br>b -> Vm.2D                                      | TRN2 Vd.2D,Vn.2D,Vm.2D                                                                                     | Vd.2D -> result  | A64                     |
| poly64x2_t vtrn2q_p64(poly64x2_t a, poly64x2_t b)           | a -> Vn.2D<br>b -> Vm.2D                                      | TRN2 Vd.2D,Vn.2D,Vm.2D                                                                                     | Vd.2D -> result  | A64                     |
| float32x2_t vtrn2_f32(float32x2_t a, float32x2_t b)         | a -> Vn.2S<br>b -> Vm.2S                                      | TRN2 Vd.2S,Vn.2S,Vm.2S                                                                                     | Vd.2S -> result  | A64                     |
| float32x4_t vtrn2q_f32(float32x4_t a, float32x4_t b)        | a -> Vn.4S<br>b -> Vm.4S                                      | TRN2 Vd.4S,Vn.4S,Vm.4S                                                                                     | Vd.4S -> result  | A64                     |
| float64x2_t vtrn2q_f64(float64x2_t a, float64x2_t b)        | a -> Vn.2D<br>b -> Vm.2D                                      | TRN2 Vd.2D,Vn.2D,Vm.2D                                                                                     | Vd.2D -> result  | A64                     |
| poly8x8_t vtrn2_p8(poly8x8_t a, poly8x8_t b)                | a -> Vn.8B<br>b -> Vm.8B                                      | TRN2 Vd.8B,Vn.8B,Vm.8B                                                                                     | Vd.8B -> result  | A64                     |
| poly8x16_t vtrn2q_p8(poly8x16_t a, poly8x16_t b)            | a -> Vn.16B<br>b -> Vm.16B                                    | TRN2 Vd.16B,Vn.16B,Vm.16B                                                                                  | Vd.16B -> result | A64                     |
| poly16x4_t vtrn2_p16(poly16x4_t a, poly16x4_t b)            | a -> Vn.4H<br>b -> Vm.4H                                      | TRN2 Vd.4H,Vn.4H,Vm.4H                                                                                     | Vd.4H -> result  | A64                     |
| poly16x8_t vtrn2q_p16(poly16x8_t a, poly16x8_t b)           | a -> Vn.8H<br>b -> Vm.8H                                      | TRN2 Vd.8H,Vn.8H,Vm.8H                                                                                     | Vd.8H -> result  | A64                     |
| int8x8_t vtbl1_s8(int8x8_t a, int8x8_t idx)                 | Zeros(64):a -> Vn.16B                                         | TBL Vd.8B,[Vn.16B],Vm.8B                                                                                   | Vd.8B -> result  | V7/A32/A64              |
| uint8x8_t vtbl1_u8(uint8x8_t a, uint8x8_t idx)              | Zeros(64):a -> Vn.16B                                         | TBL Vd.8B,[Vn.16B],Vm.8B                                                                                   | Vd.8B -> result  | V7/A32/A64              |
| poly8x8_t vtbl1_p8(poly8x8_t a, uint8x8_t idx)              | Zeros(64):a -> Vn.16B                                         | TBL Vd.8B,[Vn.16B],Vm.8B                                                                                   | Vd.8B -> result  | V7/A32/A64              |
| int8x8_t vtbx1_s8(int8x8_t a, int8x8_t idx)                 | Zeros(64):b -> Vn.16B                                         | MOVI Vtmp.BB.#8<br>CMHS Vtmp.BB,Vm.8B,Vtmp.BB<br>TBL Vtmp1.8B,[Vn.16B],Vm.8B<br>BIF Vd.8B,Vtmp1.8B,Vtmp.BB | Vd.8B -> result  | V7/A32/A64              |
| uint8x8_t vtbx1_u8(uint8x8_t a, uint8x8_t b, uint8x8_t idx) | Zeros(64):b -> Vn.16B                                         | MOVI Vtmp.BB.#8<br>CMHS Vtmp.BB,Vm.8B,Vtmp.BB<br>TBL Vtmp1.8B,[Vn.16B],Vm.8B<br>BIF Vd.8B,Vtmp1.8B,Vtmp.BB | Vd.8B -> result  | V7/A32/A64              |
| poly8x8_t vtbx1_p8(poly8x8_t a, poly8x8_t b, uint8x8_t idx) | Zeros(64):b -> Vn.16B                                         | MOVI Vtmp.BB.#8<br>CMHS Vtmp.BB,Vm.8B,Vtmp.BB<br>TBL Vtmp1.8B,[Vn.16B],Vm.8B<br>BIF Vd.8B,Vtmp1.8B,Vtmp.BB | Vd.8B -> result  | V7/A32/A64              |
| int8x8_t vtbl2_s8(int8x8x2_t a, int8x8_t idx)               | avall[1]:avall[0] -> Vn.16B                                   | TBL Vd.8B,[Vn.16B],Vm.8B                                                                                   | Vd.8B -> result  | V7/A32/A64              |
| uint8x8_t vtbl2_u8(uint8x8x2_t a, uint8x8_t idx)            | avall[1]:avall[0] -> Vn.16B                                   | TBL Vd.8B,[Vn.16B],Vm.8B                                                                                   | Vd.8B -> result  | V7/A32/A64              |
| poly8x8_t vtbl2_p8(poly8x8x2_t a, uint8x8_t idx)            | avall[1]:avall[0] -> Vn.16B                                   | TBL Vd.8B,[Vn.16B],Vm.8B                                                                                   | Vd.8B -> result  | V7/A32/A64              |
| int8x8_t vtbl3_s8(int8x8x3_t a, int8x8_t idx)               | avall[1]:avall[0] -> Vn.16B<br>Zeros(64):a.val[2] -> Vn+1.16B | TBL Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                                          | Vd.8B -> result  | V7/A32/A64              |
| uint8x8_t vtbl3_u8(uint8x8x3_t a, uint8x8_t idx)            | avall[1]:avall[0] -> Vn.16B<br>Zeros(64):a.val[2] -> Vn+1.16B | TBL Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                                          | Vd.8B -> result  | V7/A32/A64              |

| Intrinsic                                                     | Argument Preparation                                              | Instruction                                                                               | Result           | Supported Architectures |
|---------------------------------------------------------------|-------------------------------------------------------------------|-------------------------------------------------------------------------------------------|------------------|-------------------------|
| poly8x8_t vtbi3_8(poly8x8x3_t a, uint8x8_t idx)               | avval[1]:avval[0] -> Vn.16B<br>Zeros(64):a.<br>val[2] -> Vn+1.16B | TBL<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| int8x8_t vtbi4_s8(int8x8x4_t a, int8x8_t idx)                 | avval[1]:avval[0] -> Vn.16B<br>avval[3]:avval[2] -> Vn+1.16B      | TBL<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| uint8x8_t vtbi4_u8(uint8x8x4_t a, uint8x8_t idx)              | avval[1]:avval[0] -> Vn.16B<br>avval[3]:avval[2] -> Vn+1.16B      | TBL<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| poly8x8_t vtbi4_p8(poly8x8x4_t a, uint8x8_t idx)              | avval[1]:avval[0] -> Vn.16B<br>avval[3]:avval[2] -> Vn+1.16B      | TBL<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| int8x8_t vtbx2_s8(int8x8_t a, int8x8x2_t b, int8x8_t idx)     | bval[1]:bval[0] -> Vn.16B                                         | TBX<br>Vd.8B,[Vn.16B],Vm.8B                                                               | Vd.8B -> result  | v7/A32/A64              |
| uint8x8_t vtbx2_u8(uint8x8_t a, uint8x8x2_t b, uint8x8_t idx) | bval[1]:bval[0] -> Vn.16B                                         | TBX<br>Vd.8B,[Vn.16B],Vm.8B                                                               | Vd.8B -> result  | v7/A32/A64              |
| poly8x8_t vtbx2_p8(poly8x8_t a, poly8x8x2_t b, uint8x8_t idx) | bval[1]:bval[0] -> Vn.16B                                         | TBX<br>Vd.8B,[Vn.16B],Vm.8B                                                               | Vd.8B -> result  | v7/A32/A64              |
| int8x8_t vtbx3_s8(int8x8_t a, int8x8x3_t b, int8x8_t idx)     | bval[1]:bval[0] -> Vn.16B<br>Zeros(64):b.<br>val[2] -> Vn+1.16B   | MOVI Vtmp.8B,#24<br>CMHS Vtmp.8B,Vm.8B,Vtmp.8B<br>TBL<br>Vtmp1.8B,[Vn.16B,Vn+1.16B],Vm.8B | Vd.8B -> result  | v7/A32/A64              |
| uint8x8_t vtbx3_u8(uint8x8_t a, uint8x8x3_t b, uint8x8_t idx) | bval[1]:bval[0] -> Vn.16B<br>Zeros(64):b.<br>val[2] -> Vn+1.16B   | MOVI Vtmp.8B,#24<br>CMHS Vtmp.8B,Vm.8B,Vtmp.8B<br>TBL<br>Vtmp1.8B,[Vn.16B,Vn+1.16B],Vm.8B | Vd.8B -> result  | v7/A32/A64              |
| poly8x8_t vtbx3_p8(poly8x8_t a, poly8x8x3_t b, uint8x8_t idx) | bval[1]:bval[0] -> Vn.16B<br>Zeros(64):b.<br>val[2] -> Vn+1.16B   | MOVI Vtmp.8B,#24<br>CMHS Vtmp.8B,Vm.8B,Vtmp.8B<br>TBL<br>Vtmp1.8B,[Vn.16B,Vn+1.16B],Vm.8B | Vd.8B -> result  | v7/A32/A64              |
| int8x8_t vtbx4_s8(int8x8_t a, int8x8x4_t b, int8x8_t idx)     | bval[1]:bval[0] -> Vn.16B<br>Zeros(64):b.<br>val[2] -> Vn+1.16B   | TBX<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| uint8x8_t vtbx4_u8(uint8x8_t a, uint8x8x4_t b, uint8x8_t idx) | bval[1]:bval[0] -> Vn.16B<br>bval[3]:bval[2] -> Vn+1.16B          | TBX<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| poly8x8_t vtbx4_p8(poly8x8_t a, poly8x8x4_t b, uint8x8_t idx) | bval[1]:bval[0] -> Vn.16B<br>bval[3]:bval[2] -> Vn+1.16B          | TBX<br>Vd.8B,[Vn.16B,Vn+1.16B],Vm.8B                                                      | Vd.8B -> result  | v7/A32/A64              |
| int8x8_t vqtb1_s8(int8x16_t t, uint8x8_t idx)                 | t -> Vn.16B<br>idx -> Vm.8B                                       | TBL<br>Vd.8B,[Vn.16B],Vm.8B                                                               | Vd.8B -> result  | A64                     |
| int8x16_t vqtb1q1_s8(int8x16_t t, uint8x16_t idx)             | t -> Vn.16B<br>idx -> Vm.16B                                      | TBL<br>Vd.16B,[Vn.16B],Vm.16B                                                             | Vd.16B -> result | A64                     |
| uint8x8_t vqtb1_u8(uint8x16_t t, uint8x8_t idx)               | t -> Vn.16B<br>idx -> Vm.8B                                       | TBL<br>Vd.8B,[Vn.16B],Vm.8B                                                               | Vd.8B -> result  | A64                     |

| Intrinsic                                                          | Argument Preparation                                                               | Instruction                           | Result           | Supported Architectures |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------|---------------------------------------|------------------|-------------------------|
| uint8x16_t vqtbl1q_u8(uint8x16_t t, uint8x16_t idx)                | t -> Vn.16B<br>idx -> Vm.16B                                                       | TBL Vd.16B,[Vn.16B].Vm.16B            | Vd.16B -> result | A64                     |
| poly8x8_t vqtbl1_p8(poly8x16_t t, uint8x8_t idx)                   | t -> Vn.16B<br>idx -> Vm.8B                                                        | TBL Vd.8B,[Vn.16B].Vm.8B              | Vd.8B -> result  | A64                     |
| poly8x16_t vqtbl1q_p8(poly8x16_t t, uint8x16_t idx)                | t -> Vn.16B<br>idx -> Vm.16B                                                       | TBL Vd.16B,[Vn.16B].Vm.16B            | Vd.16B -> result | A64                     |
| int8x8_t vqtbl1_s8(int8x8_t a, int8x16_t t, uint8x8_t idx)         | a -> Vd.8B<br>t -> Vn.16B<br>idx -> Vm.8B                                          | TBX Vd.8B,[Vn.16B].Vm.8B              | Vd.8B -> result  | A64                     |
| int8x16_t vqtbl1q_s8(int8x16_t a, int8x16_t t, uint8x16_t idx)     | a -> Vd.16B<br>t -> Vn.16B<br>idx -> Vm.16B                                        | TBX Vd.16B,[Vn.16B].Vm.16B            | Vd.16B -> result | A64                     |
| uint8x8_t vqtblx1_u8(uint8x8_t a, uint8x16_t t, uint8x8_t idx)     | a -> Vd.8B<br>t -> Vn.16B<br>idx -> Vm.8B                                          | TBX Vd.8B,[Vn.16B].Vm.8B              | Vd.8B -> result  | A64                     |
| uint8x16_t vqtblx1q_u8(uint8x16_t a, uint8x16_t t, uint8x16_t idx) | a -> Vd.16B<br>t -> Vn.16B<br>idx -> Vm.16B                                        | TBX Vd.16B,[Vn.16B].Vm.16B            | Vd.16B -> result | A64                     |
| poly8x8_t vqtblx1_p8(poly8x8_t a, poly8x16_t t, uint8x8_t idx)     | a -> Vd.8B<br>t -> Vn.16B<br>idx -> Vm.8B                                          | TBX Vd.8B,[Vn.16B].Vm.8B              | Vd.8B -> result  | A64                     |
| poly8x16_t vqtblx1q_p8(poly8x16_t a, poly8x16_t t, uint8x16_t idx) | a -> Vd.16B<br>t -> Vn.16B<br>idx -> Vm.16B                                        | TBX Vd.16B,[Vn.16B].Vm.16B            | Vd.16B -> result | A64                     |
| int8x8_t vqtbl2_s8(int8x16x2_t t, uint8x8_t idx)                   | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>idx -> Vm.8B                         | TBL Vd.8B,[Vn.16B - Vn+1.16B].Vm.8B   | Vd.8B -> result  | A64                     |
| int8x16_t vqtbl2q_s8(int8x16x2_t t, uint8x16_t idx)                | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>idx -> Vm.16B                        | TBL Vd.16B,[Vn.16B - Vn+1.16B].Vm.16B | Vd.16B -> result | A64                     |
| uint8x8_t vqtbl2_u8(uint8x16x2_t t, uint8x8_t idx)                 | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>idx -> Vm.8B                         | TBL Vd.8B,[Vn.16B - Vn+1.16B].Vm.8B   | Vd.8B -> result  | A64                     |
| uint8x16_t vqtbl2q_u8(uint8x16x2_t t, uint8x16_t idx)              | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>idx -> Vm.16B                        | TBL Vd.16B,[Vn.16B - Vn+1.16B].Vm.16B | Vd.16B -> result | A64                     |
| poly8x8_t vqtbl2_p8(poly8x16x2_t t, uint8x8_t idx)                 | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>idx -> Vm.8B                         | TBL Vd.8B,[Vn.16B - Vn+1.16B].Vm.8B   | Vd.8B -> result  | A64                     |
| poly8x16_t vqtbl2q_p8(poly8x16x2_t t, uint8x16_t idx)              | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>idx -> Vm.16B                        | TBL Vd.16B,[Vn.16B - Vn+1.16B].Vm.16B | Vd.16B -> result | A64                     |
| int8x8_t vqtbl3_s8(int8x16x3_t t, uint8x8_t idx)                   | t.val[0] -> Vn.16B<br>t.val[1] -> Vn+1.16B<br>t.val[2] -> Vn+2.16B<br>idx -> Vm.8B | TBL Vd.8B,[Vn.16B - Vn+2.16B].Vm.8B   | Vd.8B -> result  | A64                     |

| Intrinsic                                             | Argument Preparation                                                                               | Instruction                           | Result           | Supported Architectures |
|-------------------------------------------------------|----------------------------------------------------------------------------------------------------|---------------------------------------|------------------|-------------------------|
| int8x16_t vqtbl3q_s8(int8x16x3_t t, uint8x16_t idx)   | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>idx-> Vm.16B                       | TBL Vd.16B,[Vn.16B - Vn+2.16B],Vm.16B | Vd.16B -> result | A64                     |
| uint8x8_t vqtbl3_u8(uint8x16x3_t t, uint8x8_t idx)    | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>idx-> Vm.8B                        | TBL Vd.8B,[Vn.16B - Vn+2.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| uint8x16_t vqtbl3q_u8(uint8x16x3_t t, uint8x16_t idx) | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>idx-> Vm.16B                       | TBL Vd.16B,[Vn.16B - Vn+2.16B],Vm.16B | Vd.16B -> result | A64                     |
| poly8x8_t vqtbl3_p8(poly8x16x3_t t, uint8x8_t idx)    | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>idx-> Vm.8B                        | TBL Vd.8B,[Vn.16B - Vn+2.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| poly8x16_t vqtbl3q_p8(poly8x16x3_t t, uint8x16_t idx) | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>idx-> Vm.16B                       | TBL Vd.16B,[Vn.16B - Vn+2.16B],Vm.16B | Vd.16B -> result | A64                     |
| int8x8_t vqtbl4_s8(int8x16x4_t t, uint8x8_t idx)      | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>tval[3]-> Vn+3.16B<br>idx-> Vm.8B  | TBL Vd.8B,[Vn.16B - Vn+3.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| int8x16_t vqtbl4q_s8(int8x16x4_t t, uint8x16_t idx)   | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>tval[3]-> Vn+3.16B<br>idx-> Vm.16B | TBL Vd.16B,[Vn.16B - Vn+3.16B],Vm.16B | Vd.16B -> result | A64                     |
| uint8x8_t vqtbl4_u8(uint8x16x4_t t, uint8x8_t idx)    | tval[0]-> Vn.16B<br>tval[1]-> Vn+1.16B<br>tval[2]-> Vn+2.16B<br>tval[3]-> Vn+3.16B<br>idx-> Vm.8B  | TBL Vd.8B,[Vn.16B - Vn+3.16B],Vm.8B   | Vd.8B -> result  | A64                     |

| Intrinsic                                                           | Argument Preparation                                                                                    | Instruction                           | Result           | Supported Architectures |
|---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|---------------------------------------|------------------|-------------------------|
| uint8x16_t vqtbl4q_u8(uint8x16x4_t t, uint8x16_t idx)               | tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>tval[2] -> Vn+2.16B<br>tval[3] -> Vn+3.16B<br>idx -> Vm.16B | TBL Vd.16B,[Vn.16B - Vn+3.16B],Vm.16B | Vd.16B -> result | A64                     |
| poly8x8_t vqtbl4_p8(poly8x16x4_t t, uint8x8_t idx)                  | tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>tval[2] -> Vn+2.16B<br>tval[3] -> Vn+3.16B<br>idx -> Vm.8B  | TBL Vd.8B,[Vn.16B - Vn+3.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| poly8x16_t vqtbl4q_p8(poly8x16x4_t t, uint8x16_t idx)               | tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>tval[2] -> Vn+2.16B<br>tval[3] -> Vn+3.16B<br>idx -> Vm.16B | TBL Vd.16B,[Vn.16B - Vn+3.16B],Vm.16B | Vd.16B -> result | A64                     |
| int8x8_t vqtbx2_s8(int8x8_t a, int8x16x2_t t, uint8x8_t idx)        | a -> Vd.8B<br>tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>idx -> Vm.8B                                  | TBX Vd.8B,[Vn.16B - Vn+1.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| int8x16_t vqtbx2q_s8(int8x16_t a, int8x16x2_t t, uint8x16_t idx)    | a -> Vd.16B<br>tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>idx -> Vm.16B                                | TBX Vd.16B,[Vn.16B - Vn+1.16B],Vm.16B | Vd.16B -> result | A64                     |
| uint8x8_t vqtbx2_u8(uint8x8_t a, uint8x16x2_t t, uint8x8_t idx)     | a -> Vd.8B<br>tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>idx -> Vm.8B                                  | TBX Vd.8B,[Vn.16B - Vn+1.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| uint8x16_t vqtbx2q_u8(uint8x16_t a, uint8x16x2_t t, uint8x16_t idx) | a -> Vd.16B<br>tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>idx -> Vm.16B                                | TBX Vd.16B,[Vn.16B - Vn+1.16B],Vm.16B | Vd.16B -> result | A64                     |
| poly8x8_t vqtbx2_p8(poly8x8_t a, poly8x16x2_t t, uint8x8_t idx)     | a -> Vd.8B<br>tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>idx -> Vm.8B                                  | TBX Vd.8B,[Vn.16B - Vn+1.16B],Vm.8B   | Vd.8B -> result  | A64                     |
| poly8x16_t vqtbx2q_p8(poly8x16_t a, poly8x16x2_t t, uint8x16_t idx) | a -> Vd.16B<br>tval[0] -> Vn.16B<br>tval[1] -> Vn+1.16B<br>idx -> Vm.16B                                | TBX Vd.16B,[Vn.16B - Vn+1.16B],Vm.16B | Vd.16B -> result | A64                     |

| Intrinsic                                                           | Argument Preparation                                                                                           | Instruction                         | Result         | Supported Architectures |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|-------------------------------------|----------------|-------------------------|
| int8x8_t vqtbx3_s8(int8x8_t a, int8x16x3_t t, uint8x8_t idx)        | a->Vd.BB<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>idx->Vm.BB                         | TBX Vd.BB,[Vn.16B-Vn+2.16B].Vm.BB   | Vd.BB->result  | A64                     |
| int8x16_t vqtbx3q_s8(int8x16_t a, int8x16x3_t t, uint8x16_t idx)    | a->Vd.16B<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>idx->Vm.16B                       | TBX Vd.16B,[Vn.16B-Vn+2.16B].Vm.16B | Vd.16B->result | A64                     |
| uint8x8_t vqtbx3_u8(uint8x8_t a, uint8x16x3_t t, uint8x8_t idx)     | a->Vd.BB<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>idx->Vm.BB                         | TBX Vd.BB,[Vn.16B-Vn+2.16B].Vm.BB   | Vd.BB->result  | A64                     |
| uint8x16_t vqtbx3q_u8(uint8x16_t a, uint8x16x3_t t, uint8x16_t idx) | a->Vd.16B<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>idx->Vm.16B                       | TBX Vd.16B,[Vn.16B-Vn+2.16B].Vm.16B | Vd.16B->result | A64                     |
| poly8x8_t vqtbx3_p8(poly8x8_t a, poly8x16x3_t t, uint8x8_t idx)     | a->Vd.BB<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>idx->Vm.BB                         | TBX Vd.BB,[Vn.16B-Vn+2.16B].Vm.BB   | Vd.BB->result  | A64                     |
| poly8x16_t vqtbx3q_p8(poly8x16_t a, poly8x16x3_t t, uint8x16_t idx) | a->Vd.16B<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>idx->Vm.16B                       | TBX Vd.16B,[Vn.16B-Vn+2.16B].Vm.16B | Vd.16B->result | A64                     |
| int8x8_t vqtbx4_s8(int8x8_t a, int8x16x4_t t, uint8x8_t idx)        | a->Vd.BB<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>tvall[3]->Vn+3.16B<br>idx->Vm.BB   | TBX Vd.BB,[Vn.16B-Vn+3.16B].Vm.BB   | Vd.BB->result  | A64                     |
| int8x16_t vqtbx4q_s8(int8x16_t a, int8x16x4_t t, uint8x16_t idx)    | a->Vd.16B<br>tvall[0]->Vn.16B<br>tvall[1]->Vn+1.16B<br>tvall[2]->Vn+2.16B<br>tvall[3]->Vn+3.16B<br>idx->Vm.16B | TBX Vd.16B,[Vn.16B-Vn+3.16B].Vm.16B | Vd.16B->result | A64                     |

| Intrinsic                                                           | Argument Preparation                                                                                                           | Instruction                           | Result           | Supported Architectures |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|---------------------------------------|------------------|-------------------------|
| uint8x8_t vqtbx4_u8(uint8x8_t a, uint8x16x4_t t, uint8x8_t idx)     | a->Vd.8B<br>tvall[0]-><br>Vn.16B<br>tvall[1]-><br>Vn+1.16B<br>tvall[2]-><br>Vn+2.16B<br>tvall[3]-><br>Vn+3.16B<br>idx->Vm.8B   | TBX Vd.8B,[Vn.16B - Vn+3.16B].Vm.8B   | Vd.8B -> result  | A64                     |
| uint8x16_t vqtbx4q_u8(uint8x16_t a, uint8x16x4_t t, uint8x16_t idx) | a->Vd.16B<br>tvall[0]-><br>Vn.16B<br>tvall[1]-><br>Vn+1.16B<br>tvall[2]-><br>Vn+2.16B<br>tvall[3]-><br>Vn+3.16B<br>idx->Vm.16B | TBX Vd.16B,[Vn.16B - Vn+3.16B].Vm.16B | Vd.16B -> result | A64                     |
| poly8x8_t vqtbx4_p8(poly8x8_t a, poly8x16x4_t t, uint8x8_t idx)     | a->Vd.8B<br>tvall[0]-><br>Vn.16B<br>tvall[1]-><br>Vn+1.16B<br>tvall[2]-><br>Vn+2.16B<br>tvall[3]-><br>Vn+3.16B<br>idx->Vm.8B   | TBX Vd.8B,[Vn.16B - Vn+3.16B].Vm.8B   | Vd.8B -> result  | A64                     |
| poly8x16_t vqtbx4q_p8(poly8x16_t a, poly8x16x4_t t, uint8x16_t idx) | a->Vd.16B<br>tvall[0]-><br>Vn.16B<br>tvall[1]-><br>Vn+1.16B<br>tvall[2]-><br>Vn+2.16B<br>tvall[3]-><br>Vn+3.16B<br>idx->Vm.16B | TBX Vd.16B,[Vn.16B - Vn+3.16B].Vm.16B | Vd.16B -> result | A64                     |
| uint8_t vget_lane_u8(uint8x8_t v, const int lane)                   | v->Vn.8B<br>0 <= lane <= 7                                                                                                     | UMOV Rd,Vn.B[lane]                    | Rd -> result     | v7/A32/A64              |
| uint16_t vget_lane_u16(uint16x4_t v, const int lane)                | v->Vn.4H<br>0 <= lane <= 3                                                                                                     | UMOV Rd,Vn.H[lane]                    | Rd -> result     | v7/A32/A64              |
| uint32_t vget_lane_u32(uint32x2_t v, const int lane)                | v->Vn.2S<br>0 <= lane <= 1                                                                                                     | UMOV Rd,Vn.S[lane]                    | Rd -> result     | v7/A32/A64              |
| uint64_t vget_lane_u64(uint64x1_t v, const int lane)                | v->Vn.1D<br>lane == 0                                                                                                          | UMOV Rd,Vn.D[lane]                    | Rd -> result     | v7/A32/A64              |
| poly64_t vget_lane_p64(poly64x1_t v, const int lane)                | v->Vn.1D<br>lane == 0                                                                                                          | UMOV Rd,Vn.D[lane]                    | Rd -> result     | A32/A64                 |
| int8_t vget_lane_s8(int8x8_t v, const int lane)                     | v->Vn.8B<br>0 <= lane <= 7                                                                                                     | SMOV Rd,Vn.B[lane]                    | Rd -> result     | v7/A32/A64              |
| int16_t vget_lane_s16(int16x4_t v, const int lane)                  | v->Vn.4H<br>0 <= lane <= 3                                                                                                     | SMOV Rd,Vn.H[lane]                    | Rd -> result     | v7/A32/A64              |
| int32_t vget_lane_s32(int32x2_t v, const int lane)                  | v->Vn.2S<br>0 <= lane <= 1                                                                                                     | SMOV Rd,Vn.S[lane]                    | Rd -> result     | v7/A32/A64              |
| int64_t vget_lane_s64(int64x1_t v, const int lane)                  | v->Vn.1D<br>lane == 0                                                                                                          | UMOV Rd,Vn.D[lane]                    | Rd -> result     | v7/A32/A64              |
| poly8_t vget_lane_p8(poly8x8_t v, const int lane)                   | v->Vn.8B<br>0 <= lane <= 7                                                                                                     | UMOV Rd,Vn.B[lane]                    | Rd -> result     | v7/A32/A64              |
| poly16_t vget_lane_p16(poly16x4_t v, const int lane)                | v->Vn.4H<br>0 <= lane <= 3                                                                                                     | UMOV Rd,Vn.H[lane]                    | Rd -> result     | v7/A32/A64              |

| Intrinsic                                                          | Argument Preparation                   | Instruction        | Result         | Supported Architectures |
|--------------------------------------------------------------------|----------------------------------------|--------------------|----------------|-------------------------|
| float32_t vget_lane_f32(float32x2_t v, const int lane)             | v->Vn,2S<br>0 <= lane <=<br>1          | DUP Sd,Vn,S[lane]  | Sd-> result    | v7/A32/A64              |
| float64_t vget_lane_f64(float64x1_t v, const int lane)             | v->Vn,1D<br>lane==0                    | DUP Dd,Vn,D[lane]  | Dd-> result    | A64                     |
| uint8_t vgetq_lane_u8(uint8x16_t v, const int lane)                | v->Vn,16B<br>0 <= lane <=<br>15        | UMOV Rd,Vn,B[lane] | Rd-> result    | v7/A32/A64              |
| uint16_t vgetq_lane_u16(uint16x8_t v, const int lane)              | v->Vn,8H<br>0 <= lane <=<br>7          | UMOV Rd,Vn,H[lane] | Rd-> result    | v7/A32/A64              |
| uint32_t vgetq_lane_u32(uint32x4_t v, const int lane)              | v->Vn,4S<br>0 <= lane <=<br>3          | UMOV Rd,Vn,S[lane] | Rd-> result    | v7/A32/A64              |
| uint64_t vgetq_lane_u64(uint64x2_t v, const int lane)              | v->Vn,2D<br>0 <= lane <=<br>1          | UMOV Rd,Vn,D[lane] | Rd-> result    | v7/A32/A64              |
| poly64_t vgetq_lane_p64(poly64x2_t v, const int lane)              | v->Vn,2D<br>0 <= lane <=<br>1          | UMOV Rd,Vn,D[lane] | Rd-> result    | A32/A64                 |
| int8_t vgetq_lane_s8(int8x16_t v, const int lane)                  | v->Vn,16B<br>0 <= lane <=<br>15        | SMOV Rd,Vn,B[lane] | Rd-> result    | v7/A32/A64              |
| int16_t vgetq_lane_s16(int16x8_t v, const int lane)                | v->Vn,8H<br>0 <= lane <=<br>7          | SMOV Rd,Vn,H[lane] | Rd-> result    | v7/A32/A64              |
| int32_t vgetq_lane_s32(int32x4_t v, const int lane)                | v->Vn,4S<br>0 <= lane <=<br>3          | SMOV Rd,Vn,S[lane] | Rd-> result    | v7/A32/A64              |
| int64_t vgetq_lane_s64(int64x2_t v, const int lane)                | v->Vn,2D<br>0 <= lane <=<br>1          | UMOV Rd,Vn,D[lane] | Rd-> result    | v7/A32/A64              |
| poly8_t vgetq_lane_p8(poly8x16_t v, const int lane)                | v->Vn,16B<br>0 <= lane <=<br>15        | UMOV Rd,Vn,B[lane] | Rd-> result    | v7/A32/A64              |
| poly16_t vgetq_lane_p16(poly16x8_t v, const int lane)              | v->Vn,8H<br>0 <= lane <=<br>7          | UMOV Rd,Vn,H[lane] | Rd-> result    | v7/A32/A64              |
| float16_t vget_lane_f16(float16x4_t v, const int lane)             | v->Vn,4H<br>0 <= lane <=<br>3          | DUP Hd,Vn,H[lane]  | Hd-> result    | v7/A32/A64              |
| float16_t vgetq_lane_f16(float16x8_t v, const int lane)            | v->Vn,8H<br>0 <= lane <=<br>7          | DUP Hd,Vn,H[lane]  | Hd-> result    | v7/A32/A64              |
| float32_t vgetq_lane_f32(float32x4_t v, const int lane)            | v->Vn,4S<br>0 <= lane <=<br>3          | DUP Sd,Vn,S[lane]  | Sd-> result    | v7/A32/A64              |
| float64_t vgetq_lane_f64(float64x2_t v, const int lane)            | v->Vn,2D<br>0 <= lane <=<br>1          | DUP Dd,Vn,D[lane]  | Dd-> result    | A64                     |
| uint8x8_t vset_lane_u8(uint8_t a, uint8x8_t v, const int lane)     | a->Rn<br>v->Vd,8B<br>0 <= lane <=<br>7 | MOV Vd,B[lane],Rn  | Vd,8B-> result | v7/A32/A64              |
| uint16x4_t vset_lane_u16(uint16_t a, uint16x4_t v, const int lane) | a->Rn<br>v->Vd,4H<br>0 <= lane <=<br>3 | MOV Vd,H[lane],Rn  | Vd,4H-> result | v7/A32/A64              |
| uint32x2_t vset_lane_u32(uint32_t a, uint32x2_t v, const int lane) | a->Rn<br>v->Vd,2S<br>0 <= lane <=<br>1 | MOV Vd,S[lane],Rn  | Vd,2S-> result | v7/A32/A64              |
| uint64x1_t vset_lane_u64(uint64_t a, uint64x1_t v, const int lane) | a->Rn<br>v->Vd,1D<br>lane==0           | MOV Vd,D[lane],Rn  | Vd,1D-> result | v7/A32/A64              |
| poly64x1_t vset_lane_p64(poly64_t a, poly64x1_t v, const int lane) | a->Rn<br>v->Vd,1D<br>lane==0           | MOV Vd,D[lane],Rn  | Vd,1D-> result | A32/A64                 |
| int8x8_t vset_lane_s8(int8_t a, int8x8_t v, const int lane)        | a->Rn<br>v->Vd,8B<br>0 <= lane <=<br>7 | MOV Vd,B[lane],Rn  | Vd,8B-> result | v7/A32/A64              |

| Intrinsic                                                              | Argument Preparation                  | Instruction            | Result           | Supported Architectures |
|------------------------------------------------------------------------|---------------------------------------|------------------------|------------------|-------------------------|
| int16x4_t vset_lane_s16(int16_t a, int16x4_t v, const int lane)        | a->Rn<br>v->Vd,4H<br>0 <= lane <= 3   | MOV Vd.H[lane],Rn      | Vd.4H -> result  | v7/A32/A64              |
| int32x2_t vset_lane_s32(int32_t a, int32x2_t v, const int lane)        | a->Rn<br>v->Vd,2S<br>0 <= lane <= 1   | MOV Vd.S[lane],Rn      | Vd.2S -> result  | v7/A32/A64              |
| int64x1_t vset_lane_s64(int64_t a, int64x1_t v, const int lane)        | a->Rn<br>v->Vd,1D<br>lane == 0        | MOV Vd.D[lane],Rn      | Vd.1D -> result  | v7/A32/A64              |
| poly8x8_t vset_lane_p8(poly8_t a, poly8x8_t v, const int lane)         | a->Rn<br>v->Vd,8B<br>0 <= lane <= 7   | MOV Vd.B[lane],Rn      | Vd.8B -> result  | v7/A32/A64              |
| poly16x4_t vset_lane_p16(poly16_t a, poly16x4_t v, const int lane)     | a->Rn<br>v->Vd,4H<br>0 <= lane <= 3   | MOV Vd.H[lane],Rn      | Vd.4H -> result  | v7/A32/A64              |
| float16x4_t vset_lane_f16(float16_t a, float16x4_t v, const int lane)  | a->VnH<br>v->Vd,4H<br>0 <= lane <= 3  | MOV Vd.H[lane],Vn.H[0] | Vd.4H -> result  | v7/A32/A64              |
| float16x8_t vsetq_lane_f16(float16_t a, float16x8_t v, const int lane) | a->VnH<br>v->Vd,8H<br>0 <= lane <= 7  | MOV Vd.H[lane],Vn.H[0] | Vd.8H -> result  | v7/A32/A64              |
| float32x2_t vset_lane_f32(float32_t a, float32x2_t v, const int lane)  | a->Rn<br>v->Vd,2S<br>0 <= lane <= 1   | MOV Vd.S[lane],Rn      | Vd.2S -> result  | v7/A32/A64              |
| float64x1_t vset_lane_f64(float64_t a, float64x1_t v, const int lane)  | a->Rn<br>v->Vd,1D<br>lane == 0        | MOV Vd.D[lane],Rn      | Vd.1D -> result  | A64                     |
| uint8x16_t vsetq_lane_u8(uint8_t a, uint8x16_t v, const int lane)      | a->Rn<br>v->Vd,16B<br>0 <= lane <= 15 | MOV Vd.B[lane],Rn      | Vd.16B -> result | v7/A32/A64              |
| uint16x8_t vsetq_lane_u16(uint16_t a, uint16x8_t v, const int lane)    | a->Rn<br>v->Vd,8H<br>0 <= lane <= 7   | MOV Vd.H[lane],Rn      | Vd.8H -> result  | v7/A32/A64              |
| uint32x4_t vsetq_lane_u32(uint32_t a, uint32x4_t v, const int lane)    | a->Rn<br>v->Vd,4S<br>0 <= lane <= 3   | MOV Vd.S[lane],Rn      | Vd.4S -> result  | v7/A32/A64              |
| uint64x2_t vsetq_lane_u64(uint64_t a, uint64x2_t v, const int lane)    | a->Rn<br>v->Vd,2D<br>0 <= lane <= 1   | MOV Vd.D[lane],Rn      | Vd.2D -> result  | v7/A32/A64              |
| poly64x2_t vsetq_lane_p64(poly64_t a, poly64x2_t v, const int lane)    | a->Rn<br>v->Vd,2D<br>0 <= lane <= 1   | MOV Vd.D[lane],Rn      | Vd.2D -> result  | A32/A64                 |
| int8x16_t vsetq_lane_s8(int8_t a, int8x16_t v, const int lane)         | a->Rn<br>v->Vd,16B<br>0 <= lane <= 15 | MOV Vd.B[lane],Rn      | Vd.16B -> result | v7/A32/A64              |
| int16x8_t vsetq_lane_s16(int16_t a, int16x8_t v, const int lane)       | a->Rn<br>v->Vd,8H<br>0 <= lane <= 7   | MOV Vd.H[lane],Rn      | Vd.8H -> result  | v7/A32/A64              |
| int32x4_t vsetq_lane_s32(int32_t a, int32x4_t v, const int lane)       | a->Rn<br>v->Vd,4S<br>0 <= lane <= 3   | MOV Vd.S[lane],Rn      | Vd.4S -> result  | v7/A32/A64              |
| int64x2_t vsetq_lane_s64(int64_t a, int64x2_t v, const int lane)       | a->Rn<br>v->Vd,2D<br>0 <= lane <= 1   | MOV Vd.D[lane],Rn      | Vd.2D -> result  | v7/A32/A64              |
| poly8x16_t vsetq_lane_p8(poly8_t a, poly8x16_t v, const int lane)      | a->Rn<br>v->Vd,16B<br>0 <= lane <= 15 | MOV Vd.B[lane],Rn      | Vd.16B -> result | v7/A32/A64              |

| Intrinsic                                                              | Argument Preparation                     | Instruction                                        | Result                                               | Supported Architectures |
|------------------------------------------------------------------------|------------------------------------------|----------------------------------------------------|------------------------------------------------------|-------------------------|
| poly16x8_t vsetq_lane_p16(poly16_t a, poly16x8_t v, const int lane)    | a -> Rn<br>v -> Vd,8H<br>0 <= lane <= 7  | MOV Vd,[lane],Rn                                   | Vd,8H -> result                                      | v7/A32/A64              |
| float32x4_t vsetq_lane_f32(float32_t a, float32x4_t v, const int lane) | a -> Rn<br>v -> Vd,4S<br>0 <= lane <= 3  | MOV Vd,S[lane],Rn                                  | Vd,4S -> result                                      | v7/A32/A64              |
| float64x2_t vsetq_lane_f64(float64_t a, float64x2_t v, const int lane) | a -> Rn<br>v -> Vd,2D<br>0 <= lane <= 1  | MOV Vd,D[lane],Rn                                  | Vd,2D -> result                                      | A64                     |
| float32_t vrecpxs_f32(float32_t a)                                     | a -> Sn                                  | FRECXP \$d,Sn                                      | \$d -> result                                        | A64                     |
| float64_t vrecpxd_f64(float64_t a)                                     | a -> Dn                                  | FRECXP \$d,Dn                                      | \$d -> result                                        | A64                     |
| float32x2_t vfma_n_f32(float32x2_t a, float32x2_t b, float32_t n)      | a -> Vd,2S<br>b -> Vn,2S<br>n -> Vm,S[0] | FMLA Vd,2S,Vn,2S,Vm,S[0]                           | Vd,2S -> result                                      | v7/A32/A64              |
| float32x4_t vfmaq_n_f32(float32x4_t a, float32x4_t b, float32_t n)     | a -> Vd,4S<br>b -> Vn,4S<br>n -> Vm,S[0] | FMLA Vd,4S,Vn,4S,Vm,S[0]                           | Vd,4S -> result                                      | v7/A32/A64              |
| float32x2_t vfms_n_f32(float32x2_t a, float32x2_t b, float32_t n)      | a -> Vd,2S<br>b -> Vn,2S<br>n -> Vm,S[0] | FMLS Vd,2S,Vn,2S,Vm,S[0]                           | Vd,2S -> result                                      | A64                     |
| float32x4_t vfmsq_n_f32(float32x4_t a, float32x4_t b, float32_t n)     | a -> Vd,4S<br>b -> Vn,4S<br>n -> Vm,S[0] | FMLS Vd,4S,Vn,4S,Vm,S[0]                           | Vd,4S -> result                                      | A64                     |
| float64x1_t vfma_n_f64(float64x1_t a, float64x1_t b, float64_t n)      | a -> Da<br>b -> Dn<br>n -> Dm            | FMADD Dd,Dn,Dm,Da                                  | Dd -> result                                         | A64                     |
| float64x2_t vfmaq_n_f64(float64x2_t a, float64x2_t b, float64_t n)     | a -> Vd,2D<br>b -> Vn,2D<br>n -> Vm,D[0] | FMLA Vd,2D,Vn,2D,Vm,D[0]                           | Vd,2D -> result                                      | A64                     |
| float64x1_t vfms_n_f64(float64x1_t a, float64x1_t b, float64_t n)      | a -> Da<br>b -> Dn<br>n -> Dm            | FMSUB Dd,Dn,Dm,Da                                  | Dd -> result                                         | A64                     |
| float64x2_t vfmsq_n_f64(float64x2_t a, float64x2_t b, float64_t n)     | a -> Vd,2D<br>b -> Vn,2D<br>n -> Vm,D[0] | FMLS Vd,2D,Vn,2D,Vm,D[0]                           | Vd,2D -> result                                      | A64                     |
| int8x8x2_t vtrn_s8(int8x8_t a, int8x8_t b)                             | a -> Vn,8B<br>b -> Vm,8B                 | TRN1 Vd1,8B,Vn,8B,Vm,8B<br>TRN2 Vd2,8B,Vn,8B,Vm,8B | Vd1,8B -> result,vall[0]<br>Vd2,8B -> result,vall[1] | v7/A32/A64              |
| int16x4x2_t vtrn_s16(int16x4_t a, int16x4_t b)                         | a -> Vn,4H<br>b -> Vm,4H                 | TRN1 Vd1,4H,Vn,4H,Vm,4H<br>TRN2 Vd2,4H,Vn,4H,Vm,4H | Vd1,4H -> result,vall[0]<br>Vd2,4H -> result,vall[1] | v7/A32/A64              |
| uint8x8x2_t vtrn_u8(uint8x8_t a, uint8x8_t b)                          | a -> Vn,8B<br>b -> Vm,8B                 | TRN1 Vd1,8B,Vn,8B,Vm,8B<br>TRN2 Vd2,8B,Vn,8B,Vm,8B | Vd1,8B -> result,vall[0]<br>Vd2,8B -> result,vall[1] | v7/A32/A64              |
| uint16x4x2_t vtrn_u16(uint16x4_t a, uint16x4_t b)                      | a -> Vn,4H<br>b -> Vm,4H                 | TRN1 Vd1,4H,Vn,4H,Vm,4H<br>TRN2 Vd2,4H,Vn,4H,Vm,4H | Vd1,4H -> result,vall[0]<br>Vd2,4H -> result,vall[1] | v7/A32/A64              |
| poly8x8x2_t vtrn_p8(poly8x8_t a, poly8x8_t b)                          | a -> Vn,8B<br>b -> Vm,8B                 | TRN1 Vd1,8B,Vn,8B,Vm,8B<br>TRN2 Vd2,8B,Vn,8B,Vm,8B | Vd1,8B -> result,vall[0]<br>Vd2,8B -> result,vall[1] | v7/A32/A64              |
| poly16x4x2_t vtrn_p16(poly16x4_t a, poly16x4_t b)                      | a -> Vn,4H<br>b -> Vm,4H                 | TRN1 Vd1,4H,Vn,4H,Vm,4H<br>TRN2 Vd2,4H,Vn,4H,Vm,4H | Vd1,4H -> result,vall[0]<br>Vd2,4H -> result,vall[1] | v7/A32/A64              |
| int32x2x2_t vtrn_s32(int32x2_t a, int32x2_t b)                         | a -> Vn,2S<br>b -> Vm,2S                 | TRN1 Vd1,2S,Vn,2S,Vm,2S<br>TRN2 Vd2,2S,Vn,2S,Vm,2S | Vd1,2S -> result,vall[0]<br>Vd2,2S -> result,vall[1] | v7/A32/A64              |
| float32x2x2_t vtrn_f32(float32x2_t a, float32x2_t b)                   | a -> Vn,2S<br>b -> Vm,2S                 | TRN1 Vd1,2S,Vn,2S,Vm,2S<br>TRN2 Vd2,2S,Vn,2S,Vm,2S | Vd1,2S -> result,vall[0]<br>Vd2,2S -> result,vall[1] | v7/A32/A64              |
| uint32x2x2_t vtrn_u32(uint32x2_t a, uint32x2_t b)                      | a -> Vn,2S<br>b -> Vm,2S                 | TRN1 Vd1,2S,Vn,2S,Vm,2S<br>TRN2 Vd2,2S,Vn,2S,Vm,2S | Vd1,2S -> result,vall[0]<br>Vd2,2S -> result,vall[1] | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation     | Instruction                                              | Result                                               | Supported Architectures |
|-------------------------------------------------------|--------------------------|----------------------------------------------------------|------------------------------------------------------|-------------------------|
| int8x16x2_1 vtrnq_s8(int8x16_1 a, int8x16_1 b)        | a -> Vn.BH<br>b -> Vm.BH | TRN1 Vq1.16B.Vn.16B.Vm.16B<br>TRN2 Vq2.16B.Vn.16B.Vm.16B | Vq1.16B -> result.val[0]<br>Vq2.16B -> result.val[1] | V7/A32/A64              |
| int16x8x2_1 vtrnq_s16(int16x8_1 a, int16x8_1 b)       | a -> Vn.BH<br>b -> Vm.BH | TRN1 Vq1.8H.Vn.8H.Vm.8H<br>TRN2 Vq2.8H.Vn.8H.Vm.8H       | Vq1.8H -> result.val[0]<br>Vq2.8H -> result.val[1]   | V7/A32/A64              |
| int32x4x2_1 vtrnq_s32(int32x4_1 a, int32x4_1 b)       | a -> Vn.4S<br>b -> Vm.4S | TRN1 Vq1.4S.Vn.4S.Vm.4S<br>TRN2 Vq2.4S.Vn.4S.Vm.4S       | Vq1.4S -> result.val[0]<br>Vq2.4S -> result.val[1]   | V7/A32/A64              |
| float32x4x2_1 vtrnq_f32(float32x4_1 a, float32x4_1 b) | a -> Vn.4S<br>b -> Vm.4S | TRN1 Vq1.4S.Vn.4S.Vm.4S<br>TRN2 Vq2.4S.Vn.4S.Vm.4S       | Vq1.4S -> result.val[0]<br>Vq2.4S -> result.val[1]   | V7/A32/A64              |
| uint8x16x2_1 vtrnq_u8(uint8x16_1 a, uint8x16_1 b)     | a -> Vn.BH<br>b -> Vm.BH | TRN1 Vq1.16B.Vn.16B.Vm.16B<br>TRN2 Vq2.16B.Vn.16B.Vm.16B | Vq1.16B -> result.val[0]<br>Vq2.16B -> result.val[1] | V7/A32/A64              |
| uint16x8x2_1 vtrnq_u16(uint16x8_1 a, uint16x8_1 b)    | a -> Vn.BH<br>b -> Vm.BH | TRN1 Vq1.8H.Vn.8H.Vm.8H<br>TRN2 Vq2.8H.Vn.8H.Vm.8H       | Vq1.8H -> result.val[0]<br>Vq2.8H -> result.val[1]   | V7/A32/A64              |
| uint32x4x2_1 vtrnq_u32(uint32x4_1 a, uint32x4_1 b)    | a -> Vn.4S<br>b -> Vm.4S | TRN1 Vq1.4S.Vn.4S.Vm.4S<br>TRN2 Vq2.4S.Vn.4S.Vm.4S       | Vq1.4S -> result.val[0]<br>Vq2.4S -> result.val[1]   | V7/A32/A64              |
| poly8x16x2_1 vtrnq_p8(poly8x16_1 a, poly8x16_1 b)     | a -> Vn.BH<br>b -> Vm.BH | TRN1 Vq1.16B.Vn.16B.Vm.16B<br>TRN2 Vq2.16B.Vn.16B.Vm.16B | Vq1.16B -> result.val[0]<br>Vq2.16B -> result.val[1] | V7/A32/A64              |
| poly16x8x2_1 vtrnq_p16(poly16x8_1 a, poly16x8_1 b)    | a -> Vn.BH<br>b -> Vm.BH | TRN1 Vq1.8H.Vn.8H.Vm.8H<br>TRN2 Vq2.8H.Vn.8H.Vm.8H       | Vq1.8H -> result.val[0]<br>Vq2.8H -> result.val[1]   | V7/A32/A64              |
| int8x8x2_1 vzip_s8(int8x8_1 a, int8x8_1 b)            | a -> Vn.BB<br>b -> Vm.BB | ZIP1 Vq1.8B.Vn.8B.Vm.8B<br>ZIP2 Vq2.8B.Vn.8B.Vm.8B       | Vq1.8B -> result.val[0]<br>Vq2.8B -> result.val[1]   | V7/A32/A64              |
| int16x4x2_1 vzip_s16(int16x4_1 a, int16x4_1 b)        | a -> Vn.4H<br>b -> Vm.4H | ZIP1 Vq1.4H.Vn.4H.Vm.4H<br>ZIP2 Vq2.4H.Vn.4H.Vm.4H       | Vq1.4H -> result.val[0]<br>Vq2.4H -> result.val[1]   | V7/A32/A64              |
| uint8x8x2_1 vzip_u8(uint8x8_1 a, uint8x8_1 b)         | a -> Vn.BB<br>b -> Vm.BB | ZIP1 Vq1.8B.Vn.8B.Vm.8B<br>ZIP2 Vq2.8B.Vn.8B.Vm.8B       | Vq1.8B -> result.val[0]<br>Vq2.8B -> result.val[1]   | V7/A32/A64              |
| uint16x4x2_1 vzip_u16(uint16x4_1 a, uint16x4_1 b)     | a -> Vn.4H<br>b -> Vm.4H | ZIP1 Vq1.4H.Vn.4H.Vm.4H<br>ZIP2 Vq2.4H.Vn.4H.Vm.4H       | Vq1.4H -> result.val[0]<br>Vq2.4H -> result.val[1]   | V7/A32/A64              |
| poly8x8x2_1 vzip_p8(poly8x8_1 a, poly8x8_1 b)         | a -> Vn.BB<br>b -> Vm.BB | ZIP1 Vq1.8B.Vn.8B.Vm.8B<br>ZIP2 Vq2.8B.Vn.8B.Vm.8B       | Vq1.8B -> result.val[0]<br>Vq2.8B -> result.val[1]   | V7/A32/A64              |
| poly16x4x2_1 vzip_p16(poly16x4_1 a, poly16x4_1 b)     | a -> Vn.4H<br>b -> Vm.4H | ZIP1 Vq1.4H.Vn.4H.Vm.4H<br>ZIP2 Vq2.4H.Vn.4H.Vm.4H       | Vq1.4H -> result.val[0]<br>Vq2.4H -> result.val[1]   | V7/A32/A64              |
| int32x2x2_1 vzip_s32(int32x2_1 a, int32x2_1 b)        | a -> Vn.2S<br>b -> Vm.2S | ZIP1 Vq1.2S.Vn.2S.Vm.2S<br>ZIP2 Vq2.2S.Vn.2S.Vm.2S       | Vq1.2S -> result.val[0]<br>Vq2.2S -> result.val[1]   | V7/A32/A64              |
| float32x2x2_1 vzip_f32(float32x2_1 a, float32x2_1 b)  | a -> Vn.2S<br>b -> Vm.2S | ZIP1 Vq1.2S.Vn.2S.Vm.2S<br>ZIP2 Vq2.2S.Vn.2S.Vm.2S       | Vq1.2S -> result.val[0]<br>Vq2.2S -> result.val[1]   | V7/A32/A64              |
| uint32x2x2_1 vzip_u32(uint32x2_1 a, uint32x2_1 b)     | a -> Vn.2S<br>b -> Vm.2S | ZIP1 Vq1.2S.Vn.2S.Vm.2S<br>ZIP2 Vq2.2S.Vn.2S.Vm.2S       | Vq1.2S -> result.val[0]<br>Vq2.2S -> result.val[1]   | V7/A32/A64              |

| Intrinsic                                             | Argument Preparation       | Instruction                                              | Result                                             | Supported Architectures |
|-------------------------------------------------------|----------------------------|----------------------------------------------------------|----------------------------------------------------|-------------------------|
| int8x16x2_t vzipq_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | ZIP1 Vd1.16B,Vn.16B,Vm.16B<br>ZIP2 Vd2.16B,Vn.16B,Vm.16B | Vd1.16B -> resultVal[0]<br>Vd2.16B -> resultVal[1] | v7/A32/A64              |
| int16x8x2_t vzipq_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | ZIP1 Vd1.8H,Vn.8H,Vm.8H<br>ZIP2 Vd2.8H,Vn.8H,Vm.8H       | Vd1.8H -> resultVal[0]<br>Vd2.8H -> resultVal[1]   | v7/A32/A64              |
| int32x4x2_t vzipq_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | ZIP1 Vd1.4S,Vn.4S,Vm.4S<br>ZIP2 Vd2.4S,Vn.4S,Vm.4S       | Vd1.4S -> resultVal[0]<br>Vd2.4S -> resultVal[1]   | v7/A32/A64              |
| float32x4x2_t vzipq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | ZIP1 Vd1.4S,Vn.4S,Vm.4S<br>ZIP2 Vd2.4S,Vn.4S,Vm.4S       | Vd1.4S -> resultVal[0]<br>Vd2.4S -> resultVal[1]   | v7/A32/A64              |
| uint8x16x2_t vzipq_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ZIP1 Vd1.16B,Vn.16B,Vm.16B<br>ZIP2 Vd2.16B,Vn.16B,Vm.16B | Vd1.16B -> resultVal[0]<br>Vd2.16B -> resultVal[1] | v7/A32/A64              |
| uint16x8x2_t vzipq_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ZIP1 Vd1.8H,Vn.8H,Vm.8H<br>ZIP2 Vd2.8H,Vn.8H,Vm.8H       | Vd1.8H -> resultVal[0]<br>Vd2.8H -> resultVal[1]   | v7/A32/A64              |
| uint32x4x2_t vzipq_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | ZIP1 Vd1.4S,Vn.4S,Vm.4S<br>ZIP2 Vd2.4S,Vn.4S,Vm.4S       | Vd1.4S -> resultVal[0]<br>Vd2.4S -> resultVal[1]   | v7/A32/A64              |
| poly8x16x2_t vzipq_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | ZIP1 Vd1.16B,Vn.16B,Vm.16B<br>ZIP2 Vd2.16B,Vn.16B,Vm.16B | Vd1.16B -> resultVal[0]<br>Vd2.16B -> resultVal[1] | v7/A32/A64              |
| poly16x8x2_t vzipq_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | ZIP1 Vd1.8H,Vn.8H,Vm.8H<br>ZIP2 Vd2.8H,Vn.8H,Vm.8H       | Vd1.8H -> resultVal[0]<br>Vd2.8H -> resultVal[1]   | v7/A32/A64              |
| int8x8x2_t vuzp_s8(int8x8_t a, int8x8_t b)            | a -> Vn.8B<br>b -> Vm.8B   | UZP1 Vd1.8B,Vn.8B,Vm.8B<br>UZP2 Vd2.8B,Vn.8B,Vm.8B       | Vd1.8B -> resultVal[0]<br>Vd2.8B -> resultVal[1]   | v7/A32/A64              |
| int16x4x2_t vuzp_s16(int16x4_t a, int16x4_t b)        | a -> Vn.4H<br>b -> Vm.4H   | UZP1 Vd1.4H,Vn.4H,Vm.4H<br>UZP2 Vd2.4H,Vn.4H,Vm.4H       | Vd1.4H -> resultVal[0]<br>Vd2.4H -> resultVal[1]   | v7/A32/A64              |
| int32x2x2_t vuzp_s32(int32x2_t a, int32x2_t b)        | a -> Vn.2S<br>b -> Vm.2S   | UZP1 Vd1.2S,Vn.2S,Vm.2S<br>UZP2 Vd2.2S,Vn.2S,Vm.2S       | Vd1.2S -> resultVal[0]<br>Vd2.2S -> resultVal[1]   | v7/A32/A64              |
| float32x2x2_t vuzp_f32(float32x2_t a, float32x2_t b)  | a -> Vn.2S<br>b -> Vm.2S   | UZP1 Vd1.2S,Vn.2S,Vm.2S<br>UZP2 Vd2.2S,Vn.2S,Vm.2S       | Vd1.2S -> resultVal[0]<br>Vd2.2S -> resultVal[1]   | v7/A32/A64              |
| uint8x8x2_t vuzp_u8(uint8x8_t a, uint8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UZP1 Vd1.8B,Vn.8B,Vm.8B<br>UZP2 Vd2.8B,Vn.8B,Vm.8B       | Vd1.8B -> resultVal[0]<br>Vd2.8B -> resultVal[1]   | v7/A32/A64              |
| uint16x4x2_t vuzp_u16(uint16x4_t a, uint16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UZP1 Vd1.4H,Vn.4H,Vm.4H<br>UZP2 Vd2.4H,Vn.4H,Vm.4H       | Vd1.4H -> resultVal[0]<br>Vd2.4H -> resultVal[1]   | v7/A32/A64              |
| uint32x2x2_t vuzp_u32(uint32x2_t a, uint32x2_t b)     | a -> Vn.2S<br>b -> Vm.2S   | UZP1 Vd1.2S,Vn.2S,Vm.2S<br>UZP2 Vd2.2S,Vn.2S,Vm.2S       | Vd1.2S -> resultVal[0]<br>Vd2.2S -> resultVal[1]   | v7/A32/A64              |
| poly8x8x2_t vuzp_p8(poly8x8_t a, poly8x8_t b)         | a -> Vn.8B<br>b -> Vm.8B   | UZP1 Vd1.8B,Vn.8B,Vm.8B<br>UZP2 Vd2.8B,Vn.8B,Vm.8B       | Vd1.8B -> resultVal[0]<br>Vd2.8B -> resultVal[1]   | v7/A32/A64              |
| poly16x4x2_t vuzp_p16(poly16x4_t a, poly16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | UZP1 Vd1.4H,Vn.4H,Vm.4H<br>UZP2 Vd2.4H,Vn.4H,Vm.4H       | Vd1.4H -> resultVal[0]<br>Vd2.4H -> resultVal[1]   | v7/A32/A64              |

| Intrinsic                                             | Argument Preparation       | Instruction                                              | Result                                               | Supported Architectures |
|-------------------------------------------------------|----------------------------|----------------------------------------------------------|------------------------------------------------------|-------------------------|
| int8x16x2_t vuzpq_s8(int8x16_t a, int8x16_t b)        | a -> Vn.16B<br>b -> Vm.16B | UZP1 Vd1.16B.Vn.16B.Vm.16B<br>UZP2 Vd2.16B.Vn.16B.Vm.16B | Vd1.16B -> result.val[0]<br>Vd2.16B -> result.val[1] | v7/A32/A64              |
| int16x8x2_t vuzpq_s16(int16x8_t a, int16x8_t b)       | a -> Vn.8H<br>b -> Vm.8H   | UZP1 Vd1.8H.Vn.8H.Vm.8H<br>UZP2 Vd2.8H.Vn.8H.Vm.8H       | Vd1.8H -> result.val[0]<br>Vd2.8H -> result.val[1]   | v7/A32/A64              |
| int32x4x2_t vuzpq_s32(int32x4_t a, int32x4_t b)       | a -> Vn.4S<br>b -> Vm.4S   | UZP1 Vd1.4S.Vn.4S.Vm.4S<br>UZP2 Vd2.4S.Vn.4S.Vm.4S       | Vd1.4S -> result.val[0]<br>Vd2.4S -> result.val[1]   | v7/A32/A64              |
| float32x4x2_t vuzpq_f32(float32x4_t a, float32x4_t b) | a -> Vn.4S<br>b -> Vm.4S   | UZP1 Vd1.4S.Vn.4S.Vm.4S<br>UZP2 Vd2.4S.Vn.4S.Vm.4S       | Vd1.4S -> result.val[0]<br>Vd2.4S -> result.val[1]   | v7/A32/A64              |
| uint8x16x2_t vuzpq_u8(uint8x16_t a, uint8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UZP1 Vd1.16B.Vn.16B.Vm.16B<br>UZP2 Vd2.16B.Vn.16B.Vm.16B | Vd1.16B -> result.val[0]<br>Vd2.16B -> result.val[1] | v7/A32/A64              |
| uint16x8x2_t vuzpq_u16(uint16x8_t a, uint16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UZP1 Vd1.8H.Vn.8H.Vm.8H<br>UZP2 Vd2.8H.Vn.8H.Vm.8H       | Vd1.8H -> result.val[0]<br>Vd2.8H -> result.val[1]   | v7/A32/A64              |
| uint32x4x2_t vuzpq_u32(uint32x4_t a, uint32x4_t b)    | a -> Vn.4S<br>b -> Vm.4S   | UZP1 Vd1.4S.Vn.4S.Vm.4S<br>UZP2 Vd2.4S.Vn.4S.Vm.4S       | Vd1.4S -> result.val[0]<br>Vd2.4S -> result.val[1]   | v7/A32/A64              |
| poly8x16x2_t vuzpq_p8(poly8x16_t a, poly8x16_t b)     | a -> Vn.16B<br>b -> Vm.16B | UZP1 Vd1.16B.Vn.16B.Vm.16B<br>UZP2 Vd2.16B.Vn.16B.Vm.16B | Vd1.16B -> result.val[0]<br>Vd2.16B -> result.val[1] | v7/A32/A64              |
| poly16x8x2_t vuzpq_p16(poly16x8_t a, poly16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | UZP1 Vd1.8H.Vn.8H.Vm.8H<br>UZP2 Vd2.8H.Vn.8H.Vm.8H       | Vd1.8H -> result.val[0]<br>Vd2.8H -> result.val[1]   | v7/A32/A64              |
| int16x4_t vreinterpret_s16_s8(int8x8_t a)             | a -> Vd.8B                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| int32x2_t vreinterpret_s32_s8(int8x8_t a)             | a -> Vd.8B                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| float32x2_t vreinterpret_f32_s8(int8x8_t a)           | a -> Vd.8B                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_s8(int8x8_t a)              | a -> Vd.8B                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_s8(int8x8_t a)            | a -> Vd.8B                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_s8(int8x8_t a)            | a -> Vd.8B                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_s8(int8x8_t a)              | a -> Vd.8B                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| poly16x4_t vreinterpret_p16_s8(int8x8_t a)            | a -> Vd.8B                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint64x1_t vreinterpret_u64_s8(int8x8_t a)            | a -> Vd.8B                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |
| int64x1_t vreinterpret_s64_s8(int8x8_t a)             | a -> Vd.8B                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |
| float64x1_t vreinterpret_f64_s8(int8x8_t a)           | a -> Vd.8B                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |
| poly64x1_t vreinterpret_p64_s8(int8x8_t a)            | a -> Vd.8B                 | NOP                                                      | Vd.1D -> result                                      | A32/A64                 |
| float16x4_t vreinterpret_f16_s8(int8x8_t a)           | a -> Vd.8B                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| int8x8_t vreinterpret_s8_s16(int16x4_t a)             | a -> Vd.4H                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| int32x2_t vreinterpret_s32_s16(int16x4_t a)           | a -> Vd.4H                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| float32x2_t vreinterpret_f32_s16(int16x4_t a)         | a -> Vd.4H                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_s16(int16x4_t a)            | a -> Vd.4H                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_s16(int16x4_t a)          | a -> Vd.4H                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_s16(int16x4_t a)          | a -> Vd.4H                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_s16(int16x4_t a)            | a -> Vd.4H                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| poly16x4_t vreinterpret_p16_s16(int16x4_t a)          | a -> Vd.4H                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint64x1_t vreinterpret_u64_s16(int16x4_t a)          | a -> Vd.4H                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |
| int64x1_t vreinterpret_s64_s16(int16x4_t a)           | a -> Vd.4H                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |
| float64x1_t vreinterpret_f64_s16(int16x4_t a)         | a -> Vd.4H                 | NOP                                                      | Vd.1D -> result                                      | A64                     |
| poly64x1_t vreinterpret_p64_s16(int16x4_t a)          | a -> Vd.4H                 | NOP                                                      | Vd.1D -> result                                      | A32/A64                 |
| float16x4_t vreinterpret_f16_s16(int16x4_t a)         | a -> Vd.4H                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| int16x4_t vreinterpret_s16_s32(int32x2_t a)           | a -> Vd.2S                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| float32x2_t vreinterpret_f32_s32(int32x2_t a)         | a -> Vd.2S                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_s32(int32x2_t a)            | a -> Vd.2S                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_s32(int32x2_t a)          | a -> Vd.2S                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_s32(int32x2_t a)          | a -> Vd.2S                 | NOP                                                      | Vd.2S -> result                                      | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_s32(int32x2_t a)            | a -> Vd.2S                 | NOP                                                      | Vd.8B -> result                                      | v7/A32/A64              |
| poly16x4_t vreinterpret_p16_s32(int32x2_t a)          | a -> Vd.2S                 | NOP                                                      | Vd.4H -> result                                      | v7/A32/A64              |
| uint64x1_t vreinterpret_u64_s32(int32x2_t a)          | a -> Vd.2S                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |
| int64x1_t vreinterpret_s64_s32(int32x2_t a)           | a -> Vd.2S                 | NOP                                                      | Vd.1D -> result                                      | v7/A32/A64              |

| Intrinsic                                      | Argument Preparation | Instruction | Result        | Supported Architectures |
|------------------------------------------------|----------------------|-------------|---------------|-------------------------|
| float64x1_tvreinterpret_f64_s32(int32x2_t a)   | a->Vd,2S             | NOP         | Vd,1D->result | A64                     |
| poly64x1_tvreinterpret_p64_s32(int32x2_t a)    | a->Vd,2S             | NOP         | Vd,1D->result | A32/A64                 |
| float16x4_tvreinterpret_f16_s32(int32x2_t a)   | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| int8x8_tvreinterpret_s8_f32(float32x2_t a)     | a->Vd,2S             | NOP         | Vd,8B->result | v7/A32/A64              |
| int16x4_tvreinterpret_s16_f32(float32x2_t a)   | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| int32x2_tvreinterpret_s32_f32(float32x2_t a)   | a->Vd,2S             | NOP         | Vd,2S->result | v7/A32/A64              |
| uint8x8_tvreinterpret_u8_f32(float32x2_t a)    | a->Vd,2S             | NOP         | Vd,8B->result | v7/A32/A64              |
| uint16x4_tvreinterpret_u16_f32(float32x2_t a)  | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint32x2_tvreinterpret_u32_f32(float32x2_t a)  | a->Vd,2S             | NOP         | Vd,2S->result | v7/A32/A64              |
| poly8x8_tvreinterpret_p8_f32(float32x2_t a)    | a->Vd,2S             | NOP         | Vd,8B->result | v7/A32/A64              |
| poly16x4_tvreinterpret_p16_f32(float32x2_t a)  | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint64x1_tvreinterpret_u64_f32(float32x2_t a)  | a->Vd,2S             | NOP         | Vd,1D->result | v7/A32/A64              |
| int64x1_tvreinterpret_s64_f32(float32x2_t a)   | a->Vd,2S             | NOP         | Vd,1D->result | v7/A32/A64              |
| float64x1_tvreinterpret_f64_f32(float32x2_t a) | a->Vd,2S             | NOP         | Vd,1D->result | A64                     |
| poly64x1_tvreinterpret_p64_f32(float32x2_t a)  | a->Vd,2S             | NOP         | Vd,1D->result | A32/A64                 |
| poly64x1_tvreinterpret_p64_f64(float64x1_t a)  | a->Vd,1D             | NOP         | Vd,1D->result | A64                     |
| float16x4_tvreinterpret_f16_f32(float32x2_t a) | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| int8x8_tvreinterpret_s8_u8(uint8x8_t a)        | a->Vd,8B             | NOP         | Vd,8B->result | v7/A32/A64              |
| int16x4_tvreinterpret_s16_u8(uint8x8_t a)      | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| int32x2_tvreinterpret_s32_u8(uint8x8_t a)      | a->Vd,8B             | NOP         | Vd,2S->result | v7/A32/A64              |
| float32x2_tvreinterpret_f32_u8(uint8x8_t a)    | a->Vd,8B             | NOP         | Vd,2S->result | v7/A32/A64              |
| uint16x4_tvreinterpret_u16_u8(uint8x8_t a)     | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint32x2_tvreinterpret_u32_u8(uint8x8_t a)     | a->Vd,8B             | NOP         | Vd,2S->result | v7/A32/A64              |
| poly8x8_tvreinterpret_p8_u8(uint8x8_t a)       | a->Vd,8B             | NOP         | Vd,8B->result | v7/A32/A64              |
| poly16x4_tvreinterpret_p16_u8(uint8x8_t a)     | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint64x1_tvreinterpret_u64_u8(uint8x8_t a)     | a->Vd,8B             | NOP         | Vd,1D->result | v7/A32/A64              |
| int64x1_tvreinterpret_s64_u8(uint8x8_t a)      | a->Vd,8B             | NOP         | Vd,1D->result | v7/A32/A64              |
| float64x1_tvreinterpret_f64_u8(uint8x8_t a)    | a->Vd,8B             | NOP         | Vd,1D->result | A64                     |
| poly64x1_tvreinterpret_p64_u8(uint8x8_t a)     | a->Vd,8B             | NOP         | Vd,1D->result | A32/A64                 |
| float16x4_tvreinterpret_f16_u8(uint8x8_t a)    | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| int8x8_tvreinterpret_s8_u16(uint16x4_t a)      | a->Vd,4H             | NOP         | Vd,8B->result | v7/A32/A64              |
| int16x4_tvreinterpret_s16_u16(uint16x4_t a)    | a->Vd,4H             | NOP         | Vd,4H->result | v7/A32/A64              |
| int32x2_tvreinterpret_s32_u16(uint16x4_t a)    | a->Vd,4H             | NOP         | Vd,2S->result | v7/A32/A64              |
| float32x2_tvreinterpret_f32_u16(uint16x4_t a)  | a->Vd,4H             | NOP         | Vd,2S->result | v7/A32/A64              |
| uint8x8_tvreinterpret_u8_u16(uint16x4_t a)     | a->Vd,4H             | NOP         | Vd,8B->result | v7/A32/A64              |
| uint32x2_tvreinterpret_u32_u16(uint16x4_t a)   | a->Vd,4H             | NOP         | Vd,2S->result | v7/A32/A64              |
| poly8x8_tvreinterpret_p8_u16(uint16x4_t a)     | a->Vd,4H             | NOP         | Vd,8B->result | v7/A32/A64              |
| poly16x4_tvreinterpret_p16_u16(uint16x4_t a)   | a->Vd,4H             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint64x1_tvreinterpret_u64_u16(uint16x4_t a)   | a->Vd,4H             | NOP         | Vd,1D->result | v7/A32/A64              |
| int64x1_tvreinterpret_s64_u16(uint16x4_t a)    | a->Vd,4H             | NOP         | Vd,1D->result | v7/A32/A64              |
| float64x1_tvreinterpret_f64_u16(uint16x4_t a)  | a->Vd,4H             | NOP         | Vd,1D->result | A64                     |
| poly64x1_tvreinterpret_p64_u16(uint16x4_t a)   | a->Vd,4H             | NOP         | Vd,1D->result | A32/A64                 |
| float16x4_tvreinterpret_f16_u16(uint16x4_t a)  | a->Vd,4H             | NOP         | Vd,4H->result | v7/A32/A64              |
| int8x8_tvreinterpret_s8_u32(uint32x2_t a)      | a->Vd,2S             | NOP         | Vd,8B->result | v7/A32/A64              |
| int16x4_tvreinterpret_s16_u32(uint32x2_t a)    | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| int32x2_tvreinterpret_s32_u32(uint32x2_t a)    | a->Vd,2S             | NOP         | Vd,2S->result | v7/A32/A64              |
| float32x2_tvreinterpret_f32_u32(uint32x2_t a)  | a->Vd,2S             | NOP         | Vd,2S->result | v7/A32/A64              |
| uint8x8_tvreinterpret_u8_u32(uint32x2_t a)     | a->Vd,2S             | NOP         | Vd,8B->result | v7/A32/A64              |
| uint16x4_tvreinterpret_u16_u32(uint32x2_t a)   | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint32x2_tvreinterpret_u32_u32(uint32x2_t a)   | a->Vd,2S             | NOP         | Vd,2S->result | v7/A32/A64              |
| poly8x8_tvreinterpret_p8_u32(uint32x2_t a)     | a->Vd,2S             | NOP         | Vd,8B->result | v7/A32/A64              |
| poly16x4_tvreinterpret_p16_u32(uint32x2_t a)   | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint64x1_tvreinterpret_u64_u32(uint32x2_t a)   | a->Vd,2S             | NOP         | Vd,1D->result | v7/A32/A64              |
| int64x1_tvreinterpret_s64_u32(uint32x2_t a)    | a->Vd,2S             | NOP         | Vd,1D->result | v7/A32/A64              |
| float64x1_tvreinterpret_f64_u32(uint32x2_t a)  | a->Vd,2S             | NOP         | Vd,1D->result | A64                     |
| poly64x1_tvreinterpret_p64_u32(uint32x2_t a)   | a->Vd,2S             | NOP         | Vd,1D->result | A32/A64                 |
| float16x4_tvreinterpret_f16_u32(uint32x2_t a)  | a->Vd,2S             | NOP         | Vd,4H->result | v7/A32/A64              |
| int8x8_tvreinterpret_s8_p8(poly8x8_t a)        | a->Vd,8B             | NOP         | Vd,8B->result | v7/A32/A64              |
| int16x4_tvreinterpret_s16_p8(poly8x8_t a)      | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| int32x2_tvreinterpret_s32_p8(poly8x8_t a)      | a->Vd,8B             | NOP         | Vd,2S->result | v7/A32/A64              |
| float32x2_tvreinterpret_f32_p8(poly8x8_t a)    | a->Vd,8B             | NOP         | Vd,2S->result | v7/A32/A64              |
| uint8x8_tvreinterpret_u8_p8(poly8x8_t a)       | a->Vd,8B             | NOP         | Vd,8B->result | v7/A32/A64              |
| uint16x4_tvreinterpret_u16_p8(poly8x8_t a)     | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint32x2_tvreinterpret_u32_p8(poly8x8_t a)     | a->Vd,8B             | NOP         | Vd,2S->result | v7/A32/A64              |
| poly16x4_tvreinterpret_p16_p8(poly8x8_t a)     | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| uint64x1_tvreinterpret_u64_p8(poly8x8_t a)     | a->Vd,8B             | NOP         | Vd,1D->result | v7/A32/A64              |
| int64x1_tvreinterpret_s64_p8(poly8x8_t a)      | a->Vd,8B             | NOP         | Vd,1D->result | v7/A32/A64              |
| float64x1_tvreinterpret_f64_p8(poly8x8_t a)    | a->Vd,8B             | NOP         | Vd,1D->result | A64                     |
| poly64x1_tvreinterpret_p64_p8(poly8x8_t a)     | a->Vd,8B             | NOP         | Vd,1D->result | A32/A64                 |
| float16x4_tvreinterpret_f16_p8(poly8x8_t a)    | a->Vd,8B             | NOP         | Vd,4H->result | v7/A32/A64              |
| int8x8_tvreinterpret_s8_p16(poly16x4_t a)      | a->Vd,4H             | NOP         | Vd,8B->result | v7/A32/A64              |
| int16x4_tvreinterpret_s16_p16(poly16x4_t a)    | a->Vd,4H             | NOP         | Vd,4H->result | v7/A32/A64              |

| Intrinsic                                       | Argument Preparation | Instruction | Result         | Supported Architectures |
|-------------------------------------------------|----------------------|-------------|----------------|-------------------------|
| int32x2_t vreinterpret_s32_p16(poly16x4_t a)    | a->Vd.4H             | NOP         | Vd.2S->result  | v7/A32/A64              |
| float32x2_t vreinterpret_f32_p16(poly16x4_t a)  | a->Vd.4H             | NOP         | Vd.2S->result  | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_p16(poly16x4_t a)     | a->Vd.4H             | NOP         | Vd.8B->result  | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_p16(poly16x4_t a)   | a->Vd.4H             | NOP         | Vd.4H->result  | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_p16(poly16x4_t a)   | a->Vd.4H             | NOP         | Vd.2S->result  | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_p16(poly16x4_t a)     | a->Vd.4H             | NOP         | Vd.8B->result  | v7/A32/A64              |
| uint64x1_t vreinterpret_u64_p16(poly16x4_t a)   | a->Vd.4H             | NOP         | Vd.1D->result  | v7/A32/A64              |
| int64x1_t vreinterpret_s64_p16(poly16x4_t a)    | a->Vd.4H             | NOP         | Vd.1D->result  | v7/A32/A64              |
| float64x1_t vreinterpret_f64_p16(poly16x4_t a)  | a->Vd.4H             | NOP         | Vd.1D->result  | A64                     |
| poly64x1_t vreinterpret_p64_p16(poly16x4_t a)   | a->Vd.4H             | NOP         | Vd.1D->result  | A32/A64                 |
| float16x4_t vreinterpret_f16_p16(poly16x4_t a)  | a->Vd.4H             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int8x8_t vreinterpret_s8_u64(uint64x1_t a)      | a->Vd.1D             | NOP         | Vd.8B->result  | v7/A32/A64              |
| int16x4_t vreinterpret_s16_u64(uint64x1_t a)    | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int32x2_t vreinterpret_s32_u64(uint64x1_t a)    | a->Vd.1D             | NOP         | Vd.2S->result  | v7/A32/A64              |
| float32x2_t vreinterpret_f32_u64(uint64x1_t a)  | a->Vd.1D             | NOP         | Vd.2S->result  | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_u64(uint64x1_t a)     | a->Vd.1D             | NOP         | Vd.8B->result  | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_u64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_u64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.2S->result  | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_u64(uint64x1_t a)     | a->Vd.1D             | NOP         | Vd.8B->result  | v7/A32/A64              |
| poly16x4_t vreinterpret_p16_u64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int64x1_t vreinterpret_s64_u64(uint64x1_t a)    | a->Vd.1D             | NOP         | Vd.1D->result  | v7/A32/A64              |
| float64x1_t vreinterpret_f64_u64(uint64x1_t a)  | a->Vd.1D             | NOP         | Vd.1D->result  | A64                     |
| poly64x1_t vreinterpret_p64_u64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.1D->result  | A32/A64                 |
| float16x4_t vreinterpret_f16_u64(uint64x1_t a)  | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int8x8_t vreinterpret_s8_s64(uint64x1_t a)      | a->Vd.1D             | NOP         | Vd.8B->result  | v7/A32/A64              |
| int16x4_t vreinterpret_s16_s64(uint64x1_t a)    | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int32x2_t vreinterpret_s32_s64(uint64x1_t a)    | a->Vd.1D             | NOP         | Vd.2S->result  | v7/A32/A64              |
| float32x2_t vreinterpret_f32_s64(uint64x1_t a)  | a->Vd.1D             | NOP         | Vd.2S->result  | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_s64(uint64x1_t a)     | a->Vd.1D             | NOP         | Vd.8B->result  | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_s64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_s64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.2S->result  | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_s64(uint64x1_t a)     | a->Vd.1D             | NOP         | Vd.8B->result  | v7/A32/A64              |
| poly16x4_t vreinterpret_p16_s64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| uint64x1_t vreinterpret_u64_s64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.1D->result  | v7/A32/A64              |
| int64x1_t vreinterpret_s64_s64(uint64x1_t a)    | a->Vd.1D             | NOP         | Vd.1D->result  | A64                     |
| float64x1_t vreinterpret_f64_s64(uint64x1_t a)  | a->Vd.1D             | NOP         | Vd.1D->result  | A32/A64                 |
| poly64x1_t vreinterpret_p64_s64(uint64x1_t a)   | a->Vd.1D             | NOP         | Vd.1D->result  | v7/A32/A64              |
| float16x4_t vreinterpret_f16_s64(uint64x1_t a)  | a->Vd.1D             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int8x8_t vreinterpret_s8_f16(float16x4_t a)     | a->Vd.4H             | NOP         | Vd.8B->result  | v7/A32/A64              |
| int16x4_t vreinterpret_s16_f16(float16x4_t a)   | a->Vd.4H             | NOP         | Vd.4H->result  | v7/A32/A64              |
| int32x2_t vreinterpret_s32_f16(float16x4_t a)   | a->Vd.4H             | NOP         | Vd.2S->result  | v7/A32/A64              |
| float32x2_t vreinterpret_f32_f16(float16x4_t a) | a->Vd.4H             | NOP         | Vd.2S->result  | v7/A32/A64              |
| uint8x8_t vreinterpret_u8_f16(float16x4_t a)    | a->Vd.4H             | NOP         | Vd.8B->result  | v7/A32/A64              |
| uint16x4_t vreinterpret_u16_f16(float16x4_t a)  | a->Vd.4H             | NOP         | Vd.4H->result  | v7/A32/A64              |
| uint32x2_t vreinterpret_u32_f16(float16x4_t a)  | a->Vd.4H             | NOP         | Vd.2S->result  | v7/A32/A64              |
| poly8x8_t vreinterpret_p8_f16(float16x4_t a)    | a->Vd.4H             | NOP         | Vd.8B->result  | v7/A32/A64              |
| poly16x4_t vreinterpret_p16_f16(float16x4_t a)  | a->Vd.4H             | NOP         | Vd.4H->result  | v7/A32/A64              |
| uint64x1_t vreinterpret_u64_f16(float16x4_t a)  | a->Vd.4H             | NOP         | Vd.1D->result  | v7/A32/A64              |
| int64x1_t vreinterpret_s64_f16(float16x4_t a)   | a->Vd.4H             | NOP         | Vd.1D->result  | v7/A32/A64              |
| float64x1_t vreinterpret_f64_f16(float16x4_t a) | a->Vd.4H             | NOP         | Vd.1D->result  | A64                     |
| poly64x1_t vreinterpret_p64_f16(float16x4_t a)  | a->Vd.4H             | NOP         | Vd.1D->result  | A32/A64                 |
| int16x8_t vreinterpret_s16_s8(int8x16_t a)      | a->Vd.16B            | NOP         | Vd.8H->result  | v7/A32/A64              |
| int32x4_t vreinterpret_s32_s8(int8x16_t a)      | a->Vd.16B            | NOP         | Vd.4S->result  | v7/A32/A64              |
| float32x4_t vreinterpret_f32_s8(int8x16_t a)    | a->Vd.16B            | NOP         | Vd.4S->result  | v7/A32/A64              |
| uint8x16_t vreinterpret_u8_s8(int8x16_t a)      | a->Vd.16B            | NOP         | Vd.16B->result | v7/A32/A64              |
| uint16x8_t vreinterpret_u16_s8(int8x16_t a)     | a->Vd.16B            | NOP         | Vd.8H->result  | v7/A32/A64              |
| uint32x4_t vreinterpret_u32_s8(int8x16_t a)     | a->Vd.16B            | NOP         | Vd.4S->result  | v7/A32/A64              |
| poly8x16_t vreinterpret_p8_s8(int8x16_t a)      | a->Vd.16B            | NOP         | Vd.16B->result | v7/A32/A64              |
| poly16x8_t vreinterpret_p16_s8(int8x16_t a)     | a->Vd.16B            | NOP         | Vd.8H->result  | v7/A32/A64              |
| uint64x2_t vreinterpret_u64_s8(int8x16_t a)     | a->Vd.16B            | NOP         | Vd.2D->result  | v7/A32/A64              |
| int64x2_t vreinterpret_s64_s8(int8x16_t a)      | a->Vd.16B            | NOP         | Vd.2D->result  | v7/A32/A64              |
| float64x2_t vreinterpret_f64_s8(int8x16_t a)    | a->Vd.16B            | NOP         | Vd.2D->result  | A64                     |
| poly64x2_t vreinterpret_p64_s8(int8x16_t a)     | a->Vd.16B            | NOP         | Vd.2D->result  | A32/A64                 |
| poly8x16_t vreinterpret_p8_s8(int8x16_t a)      | a->Vd.16B            | NOP         | Vd.1Q->result  | A32/A64                 |
| float16x8_t vreinterpret_f16_s8(int8x16_t a)    | a->Vd.16B            | NOP         | Vd.8H->result  | v7/A32/A64              |
| int8x16_t vreinterpret_s8_s16(int16x8_t a)      | a->Vd.8H             | NOP         | Vd.16B->result | v7/A32/A64              |
| int32x4_t vreinterpret_s32_s16(int16x8_t a)     | a->Vd.8H             | NOP         | Vd.4S->result  | v7/A32/A64              |
| float32x4_t vreinterpret_f32_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.4S->result  | v7/A32/A64              |

| Intrinsic                                       | Argument Preparation | Instruction | Result          | Supported Architectures |
|-------------------------------------------------|----------------------|-------------|-----------------|-------------------------|
| uint8x16_t vreinterpretq_u8_s16(int16x8_t a)    | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_s16(int16x8_t a)    | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_s16(int16x8_t a)    | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_s16(int16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_s16(int16x8_t a)   | a->Vd.8H             | NOP         | Vd.1Q-> result  | A32/A64                 |
| float16x8_t vreinterpretq_f16_s16(int16x8_t a)  | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int8x16_t vreinterpretq_s8_s32(int32x4_t a)     | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| int16x8_t vreinterpretq_s16_s32(int32x4_t a)    | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| float32x4_t vreinterpretq_f32_s32(int32x4_t a)  | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_s32(int32x4_t a)    | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_s32(int32x4_t a)   | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_s32(int32x4_t a)   | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_s32(int32x4_t a)    | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_s32(int32x4_t a)   | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_s32(int32x4_t a)   | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_s32(int32x4_t a)    | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_s32(int32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_s32(int32x4_t a)   | a->Vd.4S             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_s32(int32x4_t a)   | a->Vd.4S             | NOP         | Vd.1Q-> result  | A32/A64                 |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f32(float32x4_t a)  | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f32(float32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f32(float32x4_t a) | a->Vd                |             |                 |                         |

| Intrinsic                                       | Argument Preparation | Instruction | Result          | Supported Architectures |
|-------------------------------------------------|----------------------|-------------|-----------------|-------------------------|
| uint8x16_t vreinterpretq_u8_u16(uint16x8_t a)   | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_u16(uint16x8_t a)  | a->Vd.8H             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_u16(uint16x8_t a)   | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_u16(uint16x8_t a)  | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_u16(uint16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_u16(uint16x8_t a)   | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_u16(uint16x8_t a) | a->Vd.8H             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_u16(uint16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_u16(uint16x8_t a)  | a->Vd.8H             | NOP         | Vd.1Q-> result  | A32/A64                 |
| float16x8_t vreinterpretq_f16_u16(uint16x8_t a) | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int8x16_t vreinterpretq_s8_u32(uint32x4_t a)    | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| int16x8_t vreinterpretq_s16_u32(uint32x4_t a)   | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_u32(uint32x4_t a)   | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| float32x4_t vreinterpretq_f32_u32(uint32x4_t a) | a->Vd.4S             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_u32(uint32x4_t a)   | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_u32(uint32x4_t a)  | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_u32(uint32x4_t a)   | a->Vd.4S             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_u32(uint32x4_t a)  | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_u32(uint32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_u32(uint32x4_t a)   | a->Vd.4S             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_u32(uint32x4_t a) | a->Vd.4S             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_u32(uint32x4_t a)  | a->Vd.4S             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_u32(uint32x4_t a)  | a->Vd.4S             | NOP         | Vd.1Q-> result  | A32/A64                 |
| float16x8_t vreinterpretq_f16_u32(uint32x4_t a) | a->Vd.4S             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int8x16_t vreinterpretq_s8_p8(poly8x16_t a)     | a->Vd.16B            | NOP         | Vd.16B-> result | v7/A32/A64              |
| int16x8_t vreinterpretq_s16_p8(poly8x16_t a)    | a->Vd.16B            | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_p8(poly8x16_t a)    | a->Vd.16B            | NOP         | Vd.4S-> result  | v7/A32/A64              |
| float32x4_t vreinterpretq_f32_p8(poly8x16_t a)  | a->Vd.16B            | NOP         | Vd.4S-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_p8(poly8x16_t a)    | a->Vd.16B            | NOP         | Vd.2D-> result  | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_p8(poly8x16_t a)   | a->Vd.16B            | NOP         | Vd.2D-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_p16(poly16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | A32/A64                 |
| int32x4_t vreinterpretq_s32_p16(poly16x8_t a)   | a->Vd.8H             | NOP         | Vd.1Q-> result  | A32/A64                 |
| float32x4_t vreinterpretq_f32_p16(poly16x8_t a) | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_p16(poly16x8_t a)   | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_p16(poly16x8_t a)  | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_p16(poly16x8_t a)  | a->Vd.8H             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_p16(poly16x8_t a)   | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_p16(poly16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_p16(poly16x8_t a)   | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_p16(poly16x8_t a) | a->Vd.8H             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_p16(poly16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_p16(poly16x8_t a)  | a->Vd.8H             | NOP         | Vd.1Q-> result  | A32/A64                 |
| float16x8_t vreinterpretq_f16_p16(poly16x8_t a) | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int8x16_t vreinterpretq_s8_u64(uint64x2_t a)    | a->Vd.2D             | NOP         | Vd.16B-> result | v7/A32/A64              |
| int16x8_t vreinterpretq_s16_u64(uint64x2_t a)   | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_u64(uint64x2_t a)   | a->Vd.2D             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| float32x4_t vreinterpretq_f32_u64(uint64x2_t a) | a->Vd.2D             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_u64(uint64x2_t a)   | a->Vd.2D             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_u64(uint64x2_t a)  | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_u64(uint64x2_t a)  | a->Vd.2D             | NOP         | Vd.4S-> result  | v7/A32/A64              |

| Intrinsic                                        | Argument Preparation | Instruction | Result          | Supported Architectures |
|--------------------------------------------------|----------------------|-------------|-----------------|-------------------------|
| poly8x16_t vreinterpretq_p8_u64(uint64x2_t a)    | a->Vd.2D             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_u64(uint64x2_t a)   | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_u64(uint64x2_t a)    | a->Vd.2D             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_u64(uint64x2_t a)  | a->Vd.2D             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_s64(uint64x2_t a)  | a->Vd.2D             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_s64(int64x2_t a)    | a->Vd.2D             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_s64(int64x2_t a)    | a->Vd.1Q             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly64x2_t vreinterpretq_p64_u64(uint64x2_t a)   | a->Vd.2D             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_u64(uint64x2_t a)   | a->Vd.1Q             | NOP         | Vd.2D-> result  | A32/A64                 |
| float16x8_t vreinterpretq_f16_u64(uint64x2_t a)  | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int8x16_t vreinterpretq_s8_s64(int64x2_t a)      | a->Vd.2D             | NOP         | Vd.16B-> result | v7/A32/A64              |
| int16x8_t vreinterpretq_s16_s64(int64x2_t a)     | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_s64(int64x2_t a)     | a->Vd.2D             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| float32x4_t vreinterpretq_f32_s64(int64x2_t a)   | a->Vd.2D             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_s64(int64x2_t a)     | a->Vd.2D             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_s64(int64x2_t a)    | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_s64(int64x2_t a)    | a->Vd.2D             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_s64(int64x2_t a)     | a->Vd.2D             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_s64(int64x2_t a)    | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_s64(int64x2_t a)    | a->Vd.2D             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_p64(poly64x2_t a)   | a->Vd.2D             | NOP         | Vd.2D-> result  | A32/A64                 |
| float16x8_t vreinterpretq_f16_s64(int64x2_t a)   | a->Vd.2D             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int8x16_t vreinterpretq_s8_f16(float16x8_t a)    | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| int16x8_t vreinterpretq_s16_f16(float16x8_t a)   | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| int32x4_t vreinterpretq_s32_f16(float16x8_t a)   | a->Vd.8H             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| float32x4_t vreinterpretq_f32_f16(float16x8_t a) | a->Vd.8H             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| uint8x16_t vreinterpretq_u8_f16(float16x8_t a)   | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| uint16x8_t vreinterpretq_u16_f16(float16x8_t a)  | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint32x4_t vreinterpretq_u32_f16(float16x8_t a)  | a->Vd.8H             | NOP         | Vd.4S-> result  | v7/A32/A64              |
| poly8x16_t vreinterpretq_p8_f16(float16x8_t a)   | a->Vd.8H             | NOP         | Vd.16B-> result | v7/A32/A64              |
| poly16x8_t vreinterpretq_p16_f16(float16x8_t a)  | a->Vd.8H             | NOP         | Vd.8H-> result  | v7/A32/A64              |
| uint64x2_t vreinterpretq_u64_f16(float16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| int64x2_t vreinterpretq_s64_f16(float16x8_t a)   | a->Vd.8H             | NOP         | Vd.2D-> result  | v7/A32/A64              |
| float64x2_t vreinterpretq_f64_f16(float16x8_t a) | a->Vd.8H             | NOP         | Vd.2D-> result  | A64                     |
| poly64x2_t vreinterpretq_p64_f16(float16x8_t a)  | a->Vd.8H             | NOP         | Vd.2D-> result  | A32/A64                 |
| poly128_t vreinterpretq_p128_f16(float16x8_t a)  | a->Vd.8H             | NOP         | Vd.1Q-> result  | A32/A64                 |
| int8x8_t vreinterpretq_s8_f64(float64x1_t a)     | a->Vd.1D             | NOP         | Vd.8B-> result  | A64                     |
| int16x4_t vreinterpretq_s16_f64(float64x1_t a)   | a->Vd.1D             | NOP         | Vd.4H-> result  | A64                     |
| int32x2_t vreinterpretq_s32_f64(float64x1_t a)   | a->Vd.1D             | NOP         | Vd.2S-> result  | A64                     |
| uint8x8_t vreinterpretq_u8_f64(float64x1_t a)    | a->Vd.1D             | NOP         | Vd.8B-> result  | A64                     |
| uint16x4_t vreinterpretq_u16_f64(float64x1_t a)  | a->Vd.1D             | NOP         | Vd.4H-> result  | A64                     |
| uint32x2_t vreinterpretq_u32_f64(float64x1_t a)  | a->Vd.1D             | NOP         | Vd.2S-> result  | A64                     |
| poly8x8_t vreinterpretq_p8_f64(float64x1_t a)    | a->Vd.1D             | NOP         | Vd.8B-> result  | A64                     |
| poly16x4_t vreinterpretq_p16_f64(float64x1_t a)  | a->Vd.1D             | NOP         | Vd.4H-> result  | A64                     |
| uint64x4_t vreinterpretq_u64_f64(float64x1_t a)  | a->Vd.1D             | NOP         | Vd.1D-> result  | A64                     |
| int64x4_t vreinterpretq_s64_f64(float64x1_t a)   | a->Vd.1D             | NOP         | Vd.1D-> result  | A64                     |
| float16x4_t vreinterpretq_f16_f64(float64x1_t a) | a->Vd.1D             | NOP         | Vd.4H-> result  | A64                     |
| float32x2_t vreinterpretq_f32_f64(float64x1_t a) | a->Vd.1D             | NOP         | Vd.2S-> result  | A64                     |
| int8x16_t vreinterpretq_s8_f64(float64x2_t a)    | a->Vd.2D             | NOP         | Vd.16B-> result | A64                     |
| int16x8_t vreinterpretq_s16_f64(float64x2_t a)   | a->Vd.2D             | NOP         | Vd.8H-> result  | A64                     |
| int32x4_t vreinterpretq_s32_f64(float64x2_t a)   | a->Vd.2D             | NOP         | Vd.4S-> result  | A64                     |
| uint8x16_t vreinterpretq_u8_f64(float64x2_t a)   | a->Vd.2D             | NOP         | Vd.16B-> result | A64                     |
| uint16x8_t vreinterpretq_u16_f64(float64x2_t a)  | a->Vd.2D             | NOP         | Vd.8H-> result  | A64                     |
| uint32x4_t vreinterpretq_u32_f64(float64x2_t a)  | a->Vd.2D             | NOP         | Vd.4S-> result  | A64                     |
| poly8x16_t vreinterpretq_p8_f64(float64x2_t a)   | a->Vd.2D             | NOP         | Vd.16B-> result | A64                     |
| poly16x8_t vreinterpretq_p16_f64(float64x2_t a)  | a->Vd.2D             | NOP         | Vd.8H-> result  | A64                     |
| uint64x2_t vreinterpretq_u64_f64(float64x2_t a)  | a->Vd.2D             | NOP         | Vd.2D-> result  | A64                     |
| int64x2_t vreinterpretq_s64_f64(float64x2_t a)   | a->Vd.2D             | NOP         | Vd.2D-> result  | A64                     |
| float16x8_t vreinterpretq_f16_f64(float64x2_t a) | a->Vd.2D             | NOP         | Vd.8H-> result  | A64                     |
| float32x4_t vreinterpretq_f32_f64(float64x2_t a) | a->Vd.2D             | NOP         | Vd.4S-> result  | A64                     |
| int8x8_t vreinterpretq_s8_p64(poly64x1_t a)      | a->Vd.1D             | NOP         | Vd.8B-> result  | A32/A64                 |

| Intrinsic                                                                    | Argument Preparation                    | Instruction         | Result         | Supported Architectures |
|------------------------------------------------------------------------------|-----------------------------------------|---------------------|----------------|-------------------------|
| int16x4_t vreinterpret_s16_p64(poly64x1_t a)                                 | a->Vd1D                                 | NOP                 | Vd.4H->result  | A32/A64                 |
| int32x2_t vreinterpret_s32_p64(poly64x1_t a)                                 | a->Vd1D                                 | NOP                 | Vd.2S->result  | A32/A64                 |
| uint8x8_t vreinterpret_u8_p64(poly64x1_t a)                                  | a->Vd1D                                 | NOP                 | Vd.8B->result  | A32/A64                 |
| uint16x4_t vreinterpret_u16_p64(poly64x1_t a)                                | a->Vd1D                                 | NOP                 | Vd.4H->result  | A32/A64                 |
| uint32x2_t vreinterpret_u32_p64(poly64x1_t a)                                | a->Vd1D                                 | NOP                 | Vd.2S->result  | A32/A64                 |
| poly8x8_t vreinterpret_p8_p64(poly64x1_t a)                                  | a->Vd1D                                 | NOP                 | Vd.8B->result  | A32/A64                 |
| poly16x4_t vreinterpret_p16_p64(poly64x1_t a)                                | a->Vd1D                                 | NOP                 | Vd.4H->result  | A32/A64                 |
| poly64x1_t vreinterpret_p64_p64(poly64x1_t a)                                | a->Vd1D                                 | NOP                 | Vd.1D->result  | A32/A64                 |
| float64x1_t vreinterpret_f64_p64(poly64x1_t a)                               | a->Vd1D                                 | NOP                 | Vd.1D->result  | A64                     |
| float16x4_t vreinterpret_f16_p64(poly64x1_t a)                               | a->Vd1D                                 | NOP                 | Vd.4H->result  | A32/A64                 |
| int8x16_t vreinterpret_s8_p64(poly64x1_t a)                                  | a->Vd2D                                 | NOP                 | Vd.16B->result | A32/A64                 |
| int16x8_t vreinterpret_s16_p64(poly64x2_t a)                                 | a->Vd2D                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| int32x4_t vreinterpret_s32_p64(poly64x2_t a)                                 | a->Vd2D                                 | NOP                 | Vd.4S->result  | A32/A64                 |
| uint8x8_t vreinterpret_u8_p64(poly64x2_t a)                                  | a->Vd2D                                 | NOP                 | Vd.16B->result | A32/A64                 |
| uint16x4_t vreinterpret_u16_p64(poly64x2_t a)                                | a->Vd2D                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| uint32x2_t vreinterpret_u32_p64(poly64x2_t a)                                | a->Vd2D                                 | NOP                 | Vd.4S->result  | A32/A64                 |
| poly8x8_t vreinterpret_p8_p64(poly64x2_t a)                                  | a->Vd2D                                 | NOP                 | Vd.16B->result | A32/A64                 |
| poly16x4_t vreinterpret_p16_p64(poly64x2_t a)                                | a->Vd2D                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| poly64x1_t vreinterpret_p64_p64(poly64x2_t a)                                | a->Vd2D                                 | NOP                 | Vd.2D->result  | A64                     |
| float16x8_t vreinterpret_f16_p64(poly64x2_t a)                               | a->Vd2D                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| int8x16_t vreinterpret_s8_p128(poly128_t a)                                  | a->Vd1Q                                 | NOP                 | Vd.16B->result | A32/A64                 |
| int16x8_t vreinterpret_s16_p128(poly128_t a)                                 | a->Vd1Q                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| int32x4_t vreinterpret_s32_p128(poly128_t a)                                 | a->Vd1Q                                 | NOP                 | Vd.4S->result  | A32/A64                 |
| uint8x8_t vreinterpret_u8_p128(poly128_t a)                                  | a->Vd1Q                                 | NOP                 | Vd.16B->result | A32/A64                 |
| uint16x4_t vreinterpret_u16_p128(poly128_t a)                                | a->Vd1Q                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| uint32x2_t vreinterpret_u32_p128(poly128_t a)                                | a->Vd1Q                                 | NOP                 | Vd.4S->result  | A32/A64                 |
| poly8x8_t vreinterpret_p8_p128(poly128_t a)                                  | a->Vd1Q                                 | NOP                 | Vd.16B->result | A32/A64                 |
| poly16x4_t vreinterpret_p16_p128(poly128_t a)                                | a->Vd1Q                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| poly64x1_t vreinterpret_p64_p128(poly128_t a)                                | a->Vd1Q                                 | NOP                 | Vd.2D->result  | A32/A64                 |
| float16x8_t vreinterpret_f16_p128(poly128_t a)                               | a->Vd1Q                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| float32x4_t vreinterpret_f32_p128(poly128_t a)                               | a->Vd1Q                                 | NOP                 | Vd.2D->result  | A64                     |
| float64x2_t vreinterpret_f64_p128(poly128_t a)                               | a->Vd1Q                                 | NOP                 | Vd.2D->result  | A32/A64                 |
| float128x1_t vreinterpret_f128_p128(poly128_t a)                             | a->Vd1Q                                 | NOP                 | Vd.8H->result  | A32/A64                 |
| poly128_t v1dq_p128(poly128_t const * ptr)                                   | ptr->Xn                                 | LDR Qd[Xn]          | Cd->result     | A32/A64                 |
| vqrdmullhq_s16(v128(poly128_t * ptr, poly128_t val)                          | ptr->Xn<br>val->Qd                      | STR Qd[Xn]          | vqrd->result   | A32/A64                 |
| uint8x16_t vsemsq_u8(uint8x16_t data, uint8x16_t key)                        | data->Vd16B<br>key->Vn16B               | AESD Vd.16B,Vn.16B  | Vd.16B->result | A32/A64                 |
| uint8x16_t vsemdq_u8(uint8x16_t data, uint8x16_t key)                        | data->Vd16B<br>key->Vn16B               | AESD Vd.16B,Vn.16B  | Vd.16B->result | A32/A64                 |
| uint8x16_t vsemscq_u8(uint8x16_t data)                                       | data->Vn16B                             | AESMC Vd.16B,Vn.16B | Vd.16B->result | A32/A64                 |
| uint8x16_t vsemsmo_u8(uint8x16_t data)                                       | data->Vn16B                             | AESMC Vd.16B,Vn.16B | Vd.16B->result | A32/A64                 |
| uint32x4_t vsha1sq_u32(uint32x4_t hash_abcd, uint32_t hash_e, uint32x4_t wk) | hash_abcd->Qd<br>hash_e->Sn<br>wk->Vn4S | SHA1C Qd,Sn,Vn.4S   | Qd->result     | A32/A64                 |
| uint32x4_t vsha1pq_u32(uint32x4_t hash_abcd, uint32_t hash_e, uint32x4_t wk) | hash_abcd->Qd<br>hash_e->Sn<br>wk->Vn4S | SHA1P Qd,Sn,Vn.4S   | Qd->result     | A32/A64                 |
| uint32x4_t vsha1mq_u32(uint32x4_t hash_abcd, uint32_t hash_e, uint32x4_t wk) | hash_abcd->Qd<br>hash_e->Sn<br>wk->Vn4S | SHA1M Qd,Sn,Vn.4S   | Qd->result     | A32/A64                 |
| uint32_t vsha1h_u32(uint32_t hash_e)                                         | hash_e->Sn                              | SHA1H Sn            | Sn->result     | A32/A64                 |

| Intrinsic                                                                             | Argument Preparation                              | Instruction                 | Result           | Supported Architectures |
|---------------------------------------------------------------------------------------|---------------------------------------------------|-----------------------------|------------------|-------------------------|
| uint32x4_t vsha1su0q_u32(uint32x4_t tw_0_3, uint32x4_t tw_4_7, uint32x4_t tw_8_11)    | w0_3-> Vd,4S<br>w4_7-> Vn,4S<br>w8_11-> Vm,4S     | SHA1SU0 Vd,4S,Vn,4S,Vm,4S   | Vd,4S -> result  | A32/A64                 |
| uint32x4_t vsha1su1q_u32(uint32x4_t tw_0_3, uint32x4_t tw12_15)                       | tw0_3-> Vd,4S<br>w12_15-> Vn,4S                   | SHA1SU1 Vd,4S,Vn,4S         | Vd,4S -> result  | A32/A64                 |
| uint32x4_t vsha256hq_u32(uint32x4_t hash_abcd, uint32x4_t hash_efgh, uint32x4_t twk)  | hash_abcd -> Qd<br>hash_efgh -> Qn<br>wk -> Vm,4S | SHA256H Qd,Qn,Vm,4S         | Qd -> result     | A32/A64                 |
| uint32x4_t vsha256h2q_u32(uint32x4_t hash_efgh, uint32x4_t hash_abcd, uint32x4_t twk) | hash_efgh -> Qd<br>hash_abcd -> Qn<br>wk -> Vm,4S | SHA256H2 Qd,Qn,Vm,4S        | Qd -> result     | A32/A64                 |
| uint32x4_t vsha256su0q_u32(uint32x4_t tw_0_3, uint32x4_t tw_4_7)                      | w0_3-> Vd,4S<br>w4_7-> Vn,4S                      | SHA256SU0 Vd,4S,Vn,4S       | Vd,4S -> result  | A32/A64                 |
| uint32x4_t vsha256su1q_u32(uint32x4_t tw_0_3, uint32x4_t tw_8_11, uint32x4_t tw12_15) | tw0_3-> Vd,4S<br>w8_11-> Vn,4S<br>w12_15-> Vm,4S  | SHA256SU1 Vd,4S,Vn,4S,Vm,4S | Vd,4S -> result  | A32/A64                 |
| poly128_t vmull_p64(poly64_t a, poly64_t b)                                           | a-> Vn,1D<br>b-> Vm,1D                            | PMULL Vd,1Q,Vn,1D,Vm,1D     | Vd,1Q -> result  | A32/A64                 |
| poly128_t vmull_high_p64(poly64x2_t a, poly64x2_t b)                                  | a-> Vn,2D<br>b-> Vm,2D                            | PMULL2 Vd,1Q,Vn,2D,Vm,2D    | Vd,1Q -> result  | A32/A64                 |
| poly8x8_t vadd_p8(poly8x8_t a, poly8x8_t b)                                           | a-> Vn,8B<br>b-> Vm,8B                            | EOR Vd,8B,Vn,8B,Vm,8B       | Vd,8B -> result  | v7/A32/A64              |
| poly16x4_t vadd_p16(poly16x4_t a, poly16x4_t b)                                       | a-> Vn,8B<br>b-> Vm,8B                            | EOR Vd,8B,Vn,8B,Vm,8B       | Vd,8B -> result  | v7/A32/A64              |
| poly64x1_t vadd_p64(poly64x1_t a, poly64x1_t b)                                       | a-> Vn,8B<br>b-> Vm,8B                            | EOR Vd,8B,Vn,8B,Vm,8B       | Vd,8B -> result  | v7/A32/A64              |
| poly8x16_t vaddq_p8(poly8x16_t a, poly8x16_t b)                                       | a-> Vn,16B<br>b-> Vm,16B                          | EOR Vd,16B,Vn,16B,Vm,16B    | Vd,16B -> result | v7/A32/A64              |
| poly16x8_t vaddq_p16(poly16x8_t a, poly16x8_t b)                                      | a-> Vn,16B<br>b-> Vm,16B                          | EOR Vd,16B,Vn,16B,Vm,16B    | Vd,16B -> result | v7/A32/A64              |
| poly64x2_t vaddq_p64(poly64x2_t a, poly64x2_t b)                                      | a-> Vn,16B<br>b-> Vm,16B                          | EOR Vd,16B,Vn,16B,Vm,16B    | Vd,16B -> result | v7/A32/A64              |
| poly128_t vaddq_p128(poly128_t a, poly128_t b)                                        | a-> Vn,16B<br>b-> Vm,16B                          | EOR Vd,16B,Vn,16B,Vm,16B    | Vd,16B -> result | v7/A32/A64              |
| uint32_t __crc32b(uint32_t a, uint8_t b)                                              | a-> Wn<br>b-> Wm                                  | CRC32B Wd,Wn,Wm             | Wd -> result     | A32/A64                 |
| uint32_t __crc32h(uint32_t a, uint16_t b)                                             | a-> Wn<br>b-> Wm                                  | CRC32H Wd,Wn,Wm             | Wd -> result     | A32/A64                 |
| uint32_t __crc32w(uint32_t a, uint32_t b)                                             | a-> Wn<br>b-> Wm                                  | CRC32W Wd,Wn,Wm             | Wd -> result     | A32/A64                 |
| uint32_t __crc32d(uint32_t a, uint64_t b)                                             | a-> Wn<br>b-> Xn                                  | CRC32X Wd,Wn,Xn             | Wd -> result     | A32/A64                 |
| uint32_t __crc32cb(uint32_t a, uint8_t b)                                             | a-> Wn<br>b-> Wm                                  | CRC32CB Wd,Wn,Wm            | Wd -> result     | A32/A64                 |
| uint32_t __crc32ch(uint32_t a, uint16_t b)                                            | a-> Wn<br>b-> Wm                                  | CRC32CH Wd,Wn,Wm            | Wd -> result     | A32/A64                 |
| uint32_t __crc32cw(uint32_t a, uint32_t b)                                            | a-> Wn<br>b-> Wm                                  | CRC32CW Wd,Wn,Wm            | Wd -> result     | A32/A64                 |
| uint32_t __crc32cd(uint32_t a, uint64_t b)                                            | a-> Wn<br>b-> Xn                                  | CRC32CX Wd,Wn,Xn            | Wd -> result     | A32/A64                 |
| int16x4_t vqrdmlah_s16(int16x4_t a, int16x4_t b, int16x4_t c)                         | a-> Vd,4H<br>b-> Vn,4H<br>c-> Vm,4H               | SQRDMLAH Vd,4H,Vn,4H,Vm,4H  | Vd,4H -> result  | A64                     |
| int32x2_t vqrdmlah_s32(int32x2_t a, int32x2_t b, int32x2_t c)                         | a-> Vd,2S<br>b-> Vn,2S<br>c-> Vm,2S               | SQRDMLAH Vd,2S,Vn,2S,Vm,2S  | Vd,2S -> result  | A64                     |
| int16x8_t vqrdmlahq_s16(int16x8_t a, int16x8_t b, int16x8_t c)                        | a-> Vd,8H<br>b-> Vn,8H<br>c-> Vm,8H               | SQRDMLAH Vd,8H,Vn,8H,Vm,8H  | Vd,8H -> result  | A64                     |

| Intrinsic                                                                            | Argument Preparation                                     | Instruction                     | Result          | Supported Architectures |
|--------------------------------------------------------------------------------------|----------------------------------------------------------|---------------------------------|-----------------|-------------------------|
| int32x4_t vqrdmlahq_s32(int32x4_t a, int32x4_t b, int32x4_t c)                       | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S                   | SQRDMLAH Vd.4S,Vn.4S,Vm.4S      | Vd.4S -> result | A64                     |
| int16x4_t vqrdmlsh_s16(int16x4_t a, int16x4_t b, int16x4_t c)                        | a -> Vd.4H<br>b -> Vn.4H<br>c -> Vm.4H                   | SQRDMLSH Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result | A64                     |
| int32x2_t vqrdmlsh_s32(int32x2_t a, int32x2_t b, int32x2_t c)                        | a -> Vd.2S<br>b -> Vn.2S<br>c -> Vm.2S                   | SQRDMLSH Vd.2S,Vn.2S,Vm.2S      | Vd.2S -> result | A64                     |
| int16x8_t vqrdmlshq_s16(int16x8_t a, int16x8_t b, int16x8_t c)                       | a -> Vd.8H<br>b -> Vn.8H<br>c -> Vm.8H                   | SQRDMLSH Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result | A64                     |
| int32x4_t vqrdmlshq_s32(int32x4_t a, int32x4_t b, int32x4_t c)                       | a -> Vd.4S<br>b -> Vn.4S<br>c -> Vm.4S                   | SQRDMLSH Vd.4S,Vn.4S,Vm.4S      | Vd.4S -> result | A64                     |
| int16x4_t vqrdmlah_lane_s16(int16x4_t a, int16x4_t b, int16x4_t v, const int lane)   | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQRDMLAH Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| int16x8_t vqrdmlahq_lane_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane)  | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 3 | SQRDMLAH Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |
| int16x4_t vqrdmlah_laneq_s16(int16x4_t a, int16x4_t b, int16x4_t v, const int lane)  | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQRDMLAH Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| int16x8_t vqrdmlahq_laneq_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane) | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQRDMLAH Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |
| int32x2_t vqrdmlah_lane_s32(int32x2_t a, int32x2_t b, int32x2_t v, const int lane)   | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQRDMLAH Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | A64                     |
| int32x4_t vqrdmlahq_lane_s32(int32x4_t a, int32x4_t b, int32x4_t v, const int lane)  | a -> Vd.4S<br>b -> Vn.4S<br>v -> Vm.2S<br>0 <= lane <= 1 | SQRDMLAH Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | A64                     |
| int32x2_t vqrdmlah_laneq_s32(int32x2_t a, int32x2_t b, int32x2_t v, const int lane)  | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQRDMLAH Vd.2S,Vn.2S,Vm.S[lane] | Vd.2S -> result | A64                     |
| int32x4_t vqrdmlahq_laneq_s32(int32x4_t a, int32x4_t b, int32x4_t v, const int lane) | a -> Vd.2S<br>b -> Vn.2S<br>v -> Vm.4S<br>0 <= lane <= 3 | SQRDMLAH Vd.4S,Vn.4S,Vm.S[lane] | Vd.4S -> result | A64                     |
| int16x4_t vqrdmlsh_lane_s16(int16x4_t a, int16x4_t b, int16x4_t v, const int lane)   | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQRDMLSH Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| int16x8_t vqrdmlshq_lane_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane)  | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | SQRDMLSH Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |
| int16x4_t vqrdmlsh_laneq_s16(int16x4_t a, int16x4_t b, int16x4_t v, const int lane)  | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | SQRDMLSH Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |

| Intrinsic                                                                         | Argument Preparation                                     | Instruction                      | Result         | Supported Architectures |
|-----------------------------------------------------------------------------------|----------------------------------------------------------|----------------------------------|----------------|-------------------------|
| int16x8_t vrdmlsh_lane_s16(int16x8_t a, int16x8_t b, int16x8_t v, const int lane) | a -> Vd4H<br>b -> Vn4H<br>v -> Vm8H<br>0 -> lane <-<br>7 | SQRDMLSH<br>Vd8H.Vn8H.Vm8H[lane] | Vd8H -> result | A64                     |
| int32x2_t vrdmlsh_lane_s32(int32x2_t a, int32x2_t b, int32x2_t v, const int lane) | a -> Vd2S<br>b -> Vn2S<br>v -> Vm2S<br>0 -> lane <-<br>1 | SQRDMLSH<br>Vd2S.Vn2S.Vm2S[lane] | Vd2S -> result | A64                     |
| int32x4_t vrdmlsh_lane_s32(int32x4_t a, int32x4_t b, int32x2_t v, const int lane) | a -> Vd4S<br>b -> Vn4S<br>v -> Vm2S<br>0 -> lane <-<br>1 | SQRDMLSH<br>Vd4S.Vn4S.Vm2S[lane] | Vd4S -> result | A64                     |
| int32x2_t vrdmlsh_lane_s32(int32x2_t a, int32x2_t b, int32x4_t v, const int lane) | a -> Vd2S<br>b -> Vn2S<br>v -> Vm4S<br>0 -> lane <-<br>3 | SQRDMLSH<br>Vd2S.Vn2S.Vm4S[lane] | Vd2S -> result | A64                     |
| int32x4_t vrdmlsh_lane_s32(int32x4_t a, int32x4_t b, int32x4_t v, const int lane) | a -> Vd2S<br>b -> Vn2S<br>v -> Vm4S<br>0 -> lane <-<br>3 | SQRDMLSH<br>Vd4S.Vn4S.Vm4S[lane] | Vd4S -> result | A64                     |
| int16_t vrdmlah_lane_s16(int16_t a, int16_t b, int16_t c)                         | a -> Hd<br>b -> Hn<br>c -> Hm                            | SQRDMLAH Hd.Hn.Hm                | Hd -> result   | A64                     |
| int32_t vrdmlah_lane_s32(int32_t a, int32_t b, int32_t c)                         | a -> Sd<br>b -> Sn<br>c -> Sm                            | SQRDMLAH Sd.Sn.Sm                | Sd -> result   | A64                     |
| int16_t vrdmlsh_lane_s16(int16_t a, int16_t b, int16_t c)                         | a -> Hd<br>b -> Hn<br>c -> Hm                            | SQRDMLAH Hd.Hn.Hm                | Hd -> result   | A64                     |
| int32_t vrdmlsh_lane_s32(int32_t a, int32_t b, int32_t c)                         | a -> Sd<br>b -> Sn<br>c -> Sm                            | SQRDMLAH Sd.Sn.Sm                | Sd -> result   | A64                     |
| int16_t vrdmlah_lane_s16(int16_t a, int16_t b, int16x4_t v, const int lane)       | a -> Hd<br>b -> Hn<br>v -> Vm4H<br>0 -> lane <-<br>3     | SQRDMLAH Hd.Hn.Vm4H[lane]        | Hd -> result   | A64                     |
| int16_t vrdmlah_lane_s16(int16_t a, int16_t b, int16x8_t v, const int lane)       | a -> Hd<br>b -> Hn<br>v -> Vm8H<br>0 -> lane <-<br>7     | SQRDMLAH Hd.Hn.Vm8H[lane]        | Hd -> result   | A64                     |
| int32_t vrdmlah_lane_s32(int32_t a, int32_t b, int32x2_t v, const int lane)       | a -> Sd<br>b -> Sn<br>v -> Vm2S<br>0 -> lane <-<br>1     | SQRDMLAH Sd.Sn.Vm2S[lane]        | Sd -> result   | A64                     |
| int32_t vrdmlah_lane_s32(int32_t a, int32_t b, int32x4_t v, const int lane)       | a -> Sd<br>b -> Sn<br>v -> Vm4S<br>0 -> lane <-<br>3     | SQRDMLAH Sd.Sn.Vm4S[lane]        | Sd -> result   | A64                     |
| int16_t vrdmlsh_lane_s16(int16_t a, int16_t b, int16x4_t v, const int lane)       | a -> Hd<br>b -> Hn<br>v -> Vm4H<br>0 -> lane <-<br>3     | SQRDMLSH Hd.Hn.Vm4H[lane]        | Hd -> result   | A64                     |
| int16_t vrdmlsh_lane_s16(int16_t a, int16_t b, int16x8_t v, const int lane)       | a -> Hd<br>b -> Hn<br>v -> Vm8H<br>0 -> lane <-<br>7     | SQRDMLSH Hd.Hn.Vm8H[lane]        | Hd -> result   | A64                     |
| int32_t vrdmlsh_lane_s32(int32_t a, int32_t b, int32x2_t v, const int lane)       | a -> Sd<br>b -> Sn<br>v -> Vm2S<br>0 -> lane <-<br>1     | SQRDMLSH Sd.Sn.Vm2S[lane]        | Sd -> result   | A64                     |

| Intrinsic                                                                      | Argument Preparation                         | Instruction               | Result     | Supported Architectures |
|--------------------------------------------------------------------------------|----------------------------------------------|---------------------------|------------|-------------------------|
| int32_t vqrdmlshs_laneq_s32(int32_t a, int32_t b, int32x4_t v, const int lane) | a->Sd<br>b->Sn<br>v->Vm,4S<br>0 <= lane <= 3 | SQRDMLSH Sd,Sn,Vm,S[lane] | Sd->result | A64                     |
| float16_t vabsb_f16(float16_t a)                                               | a->Hn                                        | FABS Hd,Hn                | Hd->result | A32/A64                 |
| uint16_t vceqzh_f16(float16_t a)                                               | a->Hn                                        | FCMEQ Hd,Hn,#0            | Hd->result | A64                     |
| uint16_t vceqzh_f16(float16_t a)                                               | a->Hn                                        | FCMGE Hd,Hn,#0            | Hd->result | A64                     |
| uint16_t vceqzh_f16(float16_t a)                                               | a->Hn                                        | FCMGT Hd,Hn,#0            | Hd->result | A64                     |
| uint16_t vclezh_f16(float16_t a)                                               | a->Hn                                        | FCMLE Hd,Hn,#0            | Hd->result | A64                     |
| uint16_t vcltzb_f16(float16_t a)                                               | a->Hn                                        | FCMLT Hd,Hn,#0            | Hd->result | A64                     |
| float16_t vcvth_f16_s16(int16_t a)                                             | a->Hn                                        | SCVTF Hd,Hn               | Hd->result | A64                     |
| float16_t vcvth_f16_s32(int32_t a)                                             | a->Hn                                        | SCVTF Hd,Hn               | Hd->result | A32/A64                 |
| float16_t vcvth_f16_s64(int64_t a)                                             | a->Hn                                        | SCVTF Hd,Hn               | Hd->result | A64                     |
| float16_t vcvth_f16_u16(uint16_t a)                                            | a->Hn                                        | UCVTF Hd,Hn               | Hd->result | A64                     |
| float16_t vcvth_f16_u32(uint32_t a)                                            | a->Hn                                        | UCVTF Hd,Hn               | Hd->result | A32/A64                 |
| float16_t vcvth_f16_u64(uint64_t a)                                            | a->Hn                                        | UCVTF Hd,Hn               | Hd->result | A64                     |
| int16_t vcvth_s16_f16(float16_t a)                                             | a->Hn                                        | FCVTZS Hd,Hn              | Hd->result | A64                     |
| int32_t vcvth_s32_f16(float16_t a)                                             | a->Hn                                        | FCVTZS Hd,Hn              | Hd->result | A32/A64                 |
| int64_t vcvth_s64_f16(float16_t a)                                             | a->Hn                                        | FCVTZS Hd,Hn              | Hd->result | A64                     |
| uint16_t vcvth_u16_f16(float16_t a)                                            | a->Hn                                        | FCVTZU Hd,Hn              | Hd->result | A64                     |
| uint32_t vcvth_u32_f16(float16_t a)                                            | a->Hn                                        | FCVTZU Hd,Hn              | Hd->result | A32/A64                 |
| uint64_t vcvth_u64_f16(float16_t a)                                            | a->Hn                                        | FCVTZU Hd,Hn              | Hd->result | A64                     |
| int16_t vcvth_s16_f16(float16_t a)                                             | a->Hn                                        | FCVTAS Hd,Hn              | Hd->result | A64                     |
| int32_t vcvth_s32_f16(float16_t a)                                             | a->Hn                                        | FCVTAS Hd,Hn              | Hd->result | A32/A64                 |
| int64_t vcvth_s64_f16(float16_t a)                                             | a->Hn                                        | FCVTAS Hd,Hn              | Hd->result | A64                     |
| uint16_t vcvth_u16_f16(float16_t a)                                            | a->Hn                                        | FCVTAU Hd,Hn              | Hd->result | A64                     |
| uint32_t vcvth_u32_f16(float16_t a)                                            | a->Hn                                        | FCVTAU Hd,Hn              | Hd->result | A32/A64                 |
| uint64_t vcvth_u64_f16(float16_t a)                                            | a->Hn                                        | FCVTAU Hd,Hn              | Hd->result | A64                     |
| int16_t vcvthm_s16_f16(float16_t a)                                            | a->Hn                                        | FCVTMS Hd,Hn              | Hd->result | A64                     |
| int32_t vcvthm_s32_f16(float16_t a)                                            | a->Hn                                        | FCVTMS Hd,Hn              | Hd->result | A32/A64                 |
| int64_t vcvthm_s64_f16(float16_t a)                                            | a->Hn                                        | FCVTMS Hd,Hn              | Hd->result | A64                     |
| uint16_t vcvthm_u16_f16(float16_t a)                                           | a->Hn                                        | FCVTMU Hd,Hn              | Hd->result | A64                     |
| uint32_t vcvthm_u32_f16(float16_t a)                                           | a->Hn                                        | FCVTMU Hd,Hn              | Hd->result | A32/A64                 |
| uint64_t vcvthm_u64_f16(float16_t a)                                           | a->Hn                                        | FCVTMU Hd,Hn              | Hd->result | A64                     |
| int16_t vcvthn_s16_f16(float16_t a)                                            | a->Hn                                        | FCVTNS Hd,Hn              | Hd->result | A64                     |
| int32_t vcvthn_s32_f16(float16_t a)                                            | a->Hn                                        | FCVTNS Hd,Hn              | Hd->result | A32/A64                 |
| int64_t vcvthn_s64_f16(float16_t a)                                            | a->Hn                                        | FCVTNS Hd,Hn              | Hd->result | A64                     |
| uint16_t vcvthn_u16_f16(float16_t a)                                           | a->Hn                                        | FCVTNU Hd,Hn              | Hd->result | A64                     |
| uint32_t vcvthn_u32_f16(float16_t a)                                           | a->Hn                                        | FCVTNU Hd,Hn              | Hd->result | A32/A64                 |
| uint64_t vcvthn_u64_f16(float16_t a)                                           | a->Hn                                        | FCVTNU Hd,Hn              | Hd->result | A64                     |
| int16_t vcvthp_s16_f16(float16_t a)                                            | a->Hn                                        | FCVTPS Hd,Hn              | Hd->result | A64                     |
| int32_t vcvthp_s32_f16(float16_t a)                                            | a->Hn                                        | FCVTPS Hd,Hn              | Hd->result | A32/A64                 |
| int64_t vcvthp_s64_f16(float16_t a)                                            | a->Hn                                        | FCVTPS Hd,Hn              | Hd->result | A64                     |
| uint16_t vcvthp_u16_f16(float16_t a)                                           | a->Hn                                        | FCVTPU Hd,Hn              | Hd->result | A64                     |
| uint32_t vcvthp_u32_f16(float16_t a)                                           | a->Hn                                        | FCVTPU Hd,Hn              | Hd->result | A32/A64                 |
| uint64_t vcvthp_u64_f16(float16_t a)                                           | a->Hn                                        | FCVTPU Hd,Hn              | Hd->result | A64                     |
| float16_t vrecph_f16(float16_t a)                                              | a->Hn                                        | FNEG Hd,Hn                | Hd->result | A32/A64                 |
| float16_t vrecpeh_f16(float16_t a)                                             | a->Hn                                        | FCPCPE Hd,Hn              | Hd->result | A64                     |
| float16_t vrecpxh_f16(float16_t a)                                             | a->Hn                                        | FCPCPX Hd,Hn              | Hd->result | A64                     |
| float16_t vrndh_f16(float16_t a)                                               | a->Hn                                        | FRINTZ Hd,Hn              | Hd->result | A32/A64                 |
| float16_t vrndah_f16(float16_t a)                                              | a->Hn                                        | FRINTA Hd,Hn              | Hd->result | A32/A64                 |
| float16_t vrndlh_f16(float16_t a)                                              | a->Hn                                        | FRINTI Hd,Hn              | Hd->result | A32/A64                 |
| float16_t vrndnh_f16(float16_t a)                                              | a->Hn                                        | FRINTN Hd,Hn              | Hd->result | A32/A64                 |
| float16_t vrndph_f16(float16_t a)                                              | a->Hn                                        | FRINTP Hd,Hn              | Hd->result | A32/A64                 |
| float16_t vrndxh_f16(float16_t a)                                              | a->Hn                                        | FRINTX Hd,Hn              | Hd->result | A32/A64                 |
| float16_t vsqrteh_f16(float16_t a)                                             | a->Hn                                        | FSQRTE Hd,Hn              | Hd->result | A64                     |
| float16_t vsqrth_f16(float16_t a)                                              | a->Hn                                        | FSQRT Hd,Hn               | Hd->result | A32/A64                 |
| float16_t vaddh_f16(float16_t a, float16_t b)                                  | a->Hn<br>b->Hm                               | FADD Hd,Hn,Hm             | Hd->result | A32/A64                 |
| float16_t vabdh_f16(float16_t a, float16_t b)                                  | a->Hn<br>b->Hm                               | FABD (scalar) Hd,Hn,Hm    | Hd->result | A64                     |
| uint16_t vceagh_f16(float16_t a, float16_t b)                                  | a->Hn<br>b->Hm                               | FACCGE Hd,Hn,Hm           | Hd->result | A64                     |
| uint16_t vceagth_f16(float16_t a, float16_t b)                                 | a->Hn<br>b->Hm                               | FACCGT Hd,Hn,Hm           | Hd->result | A64                     |
| uint16_t vcaleh_f16(float16_t a, float16_t b)                                  | a->Hn<br>b->Hm                               | FACCGE Hd,Hn,Hm           | Hd->result | A64                     |
| uint16_t vcalth_f16(float16_t a, float16_t b)                                  | a->Hn<br>b->Hm                               | FACCGT Hd,Hn,Hm           | Hd->result | A64                     |

| Intrinsic                                                 | Argument Preparation    | Instruction           | Result         | Supported Architectures |
|-----------------------------------------------------------|-------------------------|-----------------------|----------------|-------------------------|
| uint16_t vceqh_f16(float16_t a, float16_t b)              | a->Hn<br>b->Hm          | FCMEQ Hd,Hn,Hm        | Hd-> result    | A64                     |
| uint16_t vcegh_f16(float16_t a, float16_t b)              | a->Hn<br>b->Hm          | FCMGE Hd,Hn,Hm        | Hd-> result    | A64                     |
| uint16_t vcgth_f16(float16_t a, float16_t b)              | a->Hn<br>b->Hm          | FCMGT Hd,Hn,Hm        | Hd-> result    | A64                     |
| uint16_t vcleh_f16(float16_t a, float16_t b)              | a->Hn<br>b->Hm          | FCMGE Hd,Hn,Hm        | Hd-> result    | A64                     |
| uint16_t vclth_f16(float16_t a, float16_t b)              | a->Hn<br>b->Hm          | FCMGT Hd,Hn,Hm        | Hd-> result    | A64                     |
| float16_t vcvth_n_f16_s16(int16_t a, const int n)         | a->Hn<br>1 <= n <= 16   | SCVTF Hd,Hn,#n        | Hd-> result    | A64                     |
| float16_t vcvth_n_f16_s32(int32_t a, const int n)         | a->Hn<br>1 <= n <= 16   | SCVTF Hd,Hn,#n        | Hd-> result    | A32/A64                 |
| float16_t vcvth_n_f16_s64(int64_t a, const int n)         | a->Hn<br>1 <= n <= 16   | SCVTF Hd,Hn,#n        | Hd-> result    | A64                     |
| float16_t vcvth_n_f16_u16(uint16_t a, const int n)        | a->Hn<br>1 <= n <= 16   | UCVTF Hd,Hn,#n        | Hd-> result    | A64                     |
| float16_t vcvth_n_f16_u32(uint32_t a, const int n)        | a->Hn<br>1 <= n <= 16   | UCVTF Hd,Hn,#n        | Hd-> result    | A32/A64                 |
| float16_t vcvth_n_f16_u64(uint64_t a, const int n)        | a->Hn<br>1 <= n <= 16   | UCVTF Hd,Hn,#n        | Hd-> result    | A64                     |
| int16_t vcvth_n_s16_f16(float16_t a, const int n)         | a->Hn<br>1 <= n <= 16   | FCVTZS Hd,Hn,#n       | Hd-> result    | A64                     |
| int32_t vcvth_n_s32_f16(float16_t a, const int n)         | a->Hn<br>1 <= n <= 16   | FCVTZS Hd,Hn,#n       | Hd-> result    | A32/A64                 |
| int64_t vcvth_n_s64_f16(float16_t a, const int n)         | a->Hn<br>1 <= n <= 16   | FCVTZS Hd,Hn,#n       | Hd-> result    | A64                     |
| uint16_t vcvth_n_u16_f16(float16_t a, const int n)        | a->Hn<br>1 <= n <= 16   | FCVTZU Hd,Hn,#n       | Hd-> result    | A64                     |
| uint32_t vcvth_n_u32_f16(float16_t a, const int n)        | a->Hn<br>1 <= n <= 16   | FCVTZU Hd,Hn,#n       | Hd-> result    | A32/A64                 |
| uint64_t vcvth_n_u64_f16(float16_t a, const int n)        | a->Hn<br>1 <= n <= 16   | FCVTZU Hd,Hn,#n       | Hd-> result    | A64                     |
| float16_t vdivh_f16(float16_t a, float16_t b)             | a->Hn<br>b->Hm          | FDIV Hd,Hn,Hm         | Hd-> result    | A32/A64                 |
| float16_t vmaxh_f16(float16_t a, float16_t b)             | a->Hn<br>b->Hm          | FMAX Hd,Hn,Hm         | Hd-> result    | A64                     |
| float16_t vmaxnmh_f16(float16_t a, float16_t b)           | a->Hn<br>b->Hm          | FMAXNM Hd,Hn,Hm       | Hd-> result    | A32/A64                 |
| float16_t vminh_f16(float16_t a, float16_t b)             | a->Hn<br>b->Hm          | FMIN Hd,Hn,Hm         | Hd-> result    | A64                     |
| float16_t vminnmh_f16(float16_t a, float16_t b)           | a->Hn<br>b->Hm          | FMINNM Hd,Hn,Hm       | Hd-> result    | A32/A64                 |
| float16_t vmulh_f16(float16_t a, float16_t b)             | a->Hn<br>b->Hm          | FMUL Hd,Hn,Hm         | Hd-> result    | A32/A64                 |
| float16_t vmulxh_f16(float16_t a, float16_t b)            | a->Hn<br>b->Hm          | FMULX Hd,Hn,Hm        | Hd-> result    | A64                     |
| float16_t vrecph_f16(float16_t a, float16_t b)            | a->Hn<br>b->Hm          | FCREPS Hd,Hn,Hm       | Hd-> result    | A64                     |
| float16_t vsqrts_f16(float16_t a, float16_t b)            | a->Hn<br>b->Hm          | FRSQRTS Hd,Hn,Hm      | Hd-> result    | A64                     |
| float16_t vsubh_f16(float16_t a, float16_t b)             | a->Hn<br>b->Hm          | FSUB Hd,Hn,Hm         | Hd-> result    | A32/A64                 |
| float16_t vmah_f16(float16_t a, float16_t b, float16_t c) | a->Ha<br>b->Hn<br>c->Hm | FMADD Hd,Hn,Hm,Ha     | Hd-> result    | A32/A64                 |
| float16_t vmsh_f16(float16_t a, float16_t b, float16_t c) | a->Ha<br>b->Hn<br>c->Hm | FMSUB Hd,Hn,Hm,Ha     | Hd-> result    | A32/A64                 |
| float16x4_t vabs_f16(float16x4_t a)                       | a->Vn,4H                | FABS Vd,4H,Vn,4H      | Vd,4H-> result | A32/A64                 |
| float16x8_t vabsq_f16(float16x8_t a)                      | a->Vn,8H                | FABS Vd,8H,Vn,8H      | Vd,8H-> result | A32/A64                 |
| uint16x4_t vceqz_f16(float16x4_t a)                       | a->Vn,4H                | FCMEQ Vd,4H,Vn,4H,#0  | Vd,4H-> result | A32/A64                 |
| uint16x8_t vceqz_f16(float16x8_t a)                       | a->Vn,8H                | FCMEQ Vd,8H,Vn,8H,#0  | Vd,8H-> result | A32/A64                 |
| uint16x4_t vceqz_f16(float16x4_t a)                       | a->Vn,4H                | FCMGE Vd,4H,Vn,4H,#0  | Vd,4H-> result | A32/A64                 |
| uint16x8_t vceqz_f16(float16x8_t a)                       | a->Vn,8H                | FCMGE Vd,8H,Vn,8H,#0  | Vd,8H-> result | A32/A64                 |
| uint16x4_t vceqz_f16(float16x4_t a)                       | a->Vn,4H                | FCMGTV Vd,4H,Vn,4H,#0 | Vd,4H-> result | A32/A64                 |
| uint16x8_t vceqz_f16(float16x8_t a)                       | a->Vn,8H                | FCMGTV Vd,8H,Vn,8H,#0 | Vd,8H-> result | A32/A64                 |
| uint16x4_t vclez_f16(float16x4_t a)                       | a->Vn,4H                | FCMLE Vd,4H,Vn,4H,#0  | Vd,4H-> result | A32/A64                 |
| uint16x8_t vclez_f16(float16x8_t a)                       | a->Vn,8H                | FCMLE Vd,8H,Vn,8H,#0  | Vd,8H-> result | A32/A64                 |
| uint16x4_t vcltz_f16(float16x4_t a)                       | a->Vn,4H                | FCMLT Vd,4H,Vn,4H,#0  | Vd,4H-> result | A32/A64                 |
| uint16x8_t vcltz_f16(float16x8_t a)                       | a->Vn,8H                | FCMLT Vd,8H,Vn,8H,#0  | Vd,8H-> result | A32/A64                 |

| Intrinsic                                            | Argument Preparation | Instruction             | Result        | Supported Architectures |
|------------------------------------------------------|----------------------|-------------------------|---------------|-------------------------|
| float16x4_t vcvf_f16_s16(int16x4_t a)                | a->Vn.4H             | SCVTF Vd.4H,Vn.4H,#0    | Vd.4H->result | A32/A64                 |
| float16x8_t vcvq_f16_s16(int16x8_t a)                | a->Vn.8H             | SCVTF Vd.8H,Vn.8H,#0    | Vd.8H->result | A32/A64                 |
| float16x4_t vcvf_f16_u16(uint16x4_t a)               | a->Vn.4H             | UCVTF Vd.4H,Vn.4H,#0    | Vd.4H->result | A32/A64                 |
| float16x8_t vcvq_f16_u16(uint16x8_t a)               | a->Vn.8H             | UCVTF Vd.8H,Vn.8H       | Vd.8H->result | A32/A64                 |
| int16x4_t tcvf_s16_f16(float16x4_t a)                | a->Vn.4H             | FCVITZS Vd.4H,Vn.4H     | Vd.4H->result | A32/A64                 |
| int16x8_t tcvq_s16_f16(float16x8_t a)                | a->Vn.8H             | FCVITZS Vd.8H,Vn.8H     | Vd.8H->result | A32/A64                 |
| uint16x4_t tcvf_u16_f16(float16x4_t a)               | a->Vn.4H             | FCVITZS Vd.4H,Vn.4H     | Vd.4H->result | A32/A64                 |
| uint16x8_t tcvq_u16_f16(float16x8_t a)               | a->Vn.8H             | FCVITZS Vd.8H,Vn.8H     | Vd.8H->result | A32/A64                 |
| int16x4_t tcvta_s16_f16(float16x4_t a)               | a->Vn.4H             | FCVTAS Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| int16x8_t tcvtaq_s16_f16(float16x8_t a)              | a->Vn.8H             | FCVTAS Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| uint16x4_t tcvta_u16_f16(float16x4_t a)              | a->Vn.4H             | FCVTAU Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| uint16x8_t tcvtaq_u16_f16(float16x8_t a)             | a->Vn.8H             | FCVTAU Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| int16x4_t tcvtm_s16_f16(float16x4_t a)               | a->Vn.4H             | FCVTMS Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| int16x8_t tcvtmq_s16_f16(float16x8_t a)              | a->Vn.8H             | FCVTMS Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| uint16x4_t tcvtm_u16_f16(float16x4_t a)              | a->Vn.4H             | FCVTMU Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| uint16x8_t tcvtmq_u16_f16(float16x8_t a)             | a->Vn.8H             | FCVTMU Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| int16x4_t tcvtn_s16_f16(float16x4_t a)               | a->Vn.4H             | FCVTNS Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| int16x8_t tcvtnq_s16_f16(float16x8_t a)              | a->Vn.8H             | FCVTNS Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| uint16x4_t tcvtn_u16_f16(float16x4_t a)              | a->Vn.4H             | FCVTNU Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| uint16x8_t tcvtnq_u16_f16(float16x8_t a)             | a->Vn.8H             | FCVTNU Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| int16x4_t tcvtp_s16_f16(float16x4_t a)               | a->Vn.4H             | FCVTPS Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| int16x8_t tcvtpq_s16_f16(float16x8_t a)              | a->Vn.8H             | FCVTPS Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| uint16x4_t tcvtp_u16_f16(float16x4_t a)              | a->Vn.4H             | FCVTPU Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| uint16x8_t tcvtpq_u16_f16(float16x8_t a)             | a->Vn.8H             | FCVTPU Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvneg_f16(float16x4_t a)                 | a->Vn.4H             | FNEG Vd.4H,Vn.4H        | Vd.4H->result | A32/A64                 |
| float16x8_t tvnegq_f16(float16x8_t a)                | a->Vn.8H             | FNEG Vd.8H,Vn.8H        | Vd.8H->result | A32/A64                 |
| float16x4_t tvrecpe_f16(float16x4_t a)               | a->Vn.4H             | FREEPE Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrecpeq_f16(float16x8_t a)              | a->Vn.8H             | FREEPE Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrd_f16(float16x4_t a)                  | a->Vn.4H             | FRINTZ Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrdq_f16(float16x8_t a)                 | a->Vn.8H             | FRINTZ Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrdm_f16(float16x4_t a)                 | a->Vn.4H             | FRINTA Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrdmq_f16(float16x8_t a)                | a->Vn.8H             | FRINTA Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrdi_f16(float16x4_t a)                 | a->Vn.4H             | FRINTI Vd.4H,Vn.4H      | Vd.4H->result | A64                     |
| float16x8_t tvrdiq_f16(float16x8_t a)                | a->Vn.8H             | FRINTI Vd.8H,Vn.8H      | Vd.8H->result | A64                     |
| float16x4_t tvrdm_f16(float16x4_t a)                 | a->Vn.4H             | FRINTM Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrdmq_f16(float16x8_t a)                | a->Vn.8H             | FRINTM Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrdn_f16(float16x4_t a)                 | a->Vn.4H             | FRINTN Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrdnq_f16(float16x8_t a)                | a->Vn.8H             | FRINTN Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrdp_f16(float16x4_t a)                 | a->Vn.4H             | FRINTP Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrdpq_f16(float16x8_t a)                | a->Vn.8H             | FRINTP Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrdx_f16(float16x4_t a)                 | a->Vn.4H             | FRINTX Vd.4H,Vn.4H      | Vd.4H->result | A32/A64                 |
| float16x8_t tvrdxq_f16(float16x8_t a)                | a->Vn.8H             | FRINTX Vd.8H,Vn.8H      | Vd.8H->result | A32/A64                 |
| float16x4_t tvrsqte_f16(float16x4_t a)               | a->Vn.4H             | FRSQ RTE Vd.4H,Vn.4H    | Vd.4H->result | A32/A64                 |
| float16x8_t tvrsqteq_f16(float16x8_t a)              | a->Vn.8H             | FRSQ RTE Vd.8H,Vn.8H    | Vd.8H->result | A32/A64                 |
| float16x4_t tvsrt_f16(float16x4_t a)                 | a->Vn.4H             | FSQRT Vd.4H,Vn.4H       | Vd.4H->result | A64                     |
| float16x8_t tvsrtq_f16(float16x8_t a)                | a->Vn.8H             | FSQRT Vd.8H,Vn.8H       | Vd.8H->result | A64                     |
| float16x4_t vadd_f16(float16x4_t a, float16x4_t b)   | a->Vn.4H<br>b->Vn.4H | FADD Vd.4H,Vn.4H,Vm.4H  | Vd.4H->result | A32/A64                 |
| float16x8_t vaddq_f16(float16x8_t a, float16x8_t b)  | a->Vn.8H<br>b->Vn.8H | FADD Vd.8H,Vn.8H,Vm.8H  | Vd.8H->result | A32/A64                 |
| float16x4_t vabd_f16(float16x4_t a, float16x4_t b)   | a->Vn.4H<br>b->Vn.4H | FABD Vd.4H,Vn.4H,Vm.4H  | Vd.4H->result | A32/A64                 |
| float16x8_t vabdq_f16(float16x8_t a, float16x8_t b)  | a->Vn.8H<br>b->Vn.8H | FABD Vd.8H,Vn.8H,Vm.8H  | Vd.8H->result | A32/A64                 |
| uint16x4_t vcache_f16(float16x4_t a, float16x4_t b)  | a->Vn.4H<br>b->Vn.4H | FACGE Vd.4H,Vn.4H,Vm.4H | Vd.4H->result | A32/A64                 |
| uint16x8_t vcacheq_f16(float16x8_t a, float16x8_t b) | a->Vn.8H<br>b->Vn.8H | FACGE Vd.8H,Vn.8H,Vm.8H | Vd.8H->result | A32/A64                 |
| uint16x4_t vcgat_f16(float16x4_t a, float16x4_t b)   | a->Vn.4H<br>b->Vn.4H | FACGT Vd.4H,Vn.4H,Vm.4H | Vd.4H->result | A32/A64                 |
| uint16x8_t vcgatq_f16(float16x8_t a, float16x8_t b)  | a->Vn.8H<br>b->Vn.8H | FACGT Vd.8H,Vn.8H,Vm.8H | Vd.8H->result | A32/A64                 |
| uint16x4_t vcale_f16(float16x4_t a, float16x4_t b)   | a->Vn.4H<br>b->Vn.4H | FACGE Vd.4H,Vn.4H,Vm.4H | Vd.4H->result | A32/A64                 |
| uint16x8_t vcaleq_f16(float16x8_t a, float16x8_t b)  | a->Vn.8H<br>b->Vn.8H | FACGE Vd.8H,Vn.8H,Vm.8H | Vd.8H->result | A32/A64                 |
| uint16x4_t vcal_f16(float16x4_t a, float16x4_t b)    | a->Vn.4H<br>b->Vn.4H | FACGT Vd.4H,Vn.4H,Vm.4H | Vd.4H->result | A32/A64                 |
| uint16x8_t vcalq_f16(float16x8_t a, float16x8_t b)   | a->Vn.8H<br>b->Vn.8H | FACGT Vd.8H,Vn.8H,Vm.8H | Vd.8H->result | A32/A64                 |

| Intrinsic                                             | Argument Preparation       | Instruction              | Result          | Supported Architectures |
|-------------------------------------------------------|----------------------------|--------------------------|-----------------|-------------------------|
| uint16x4_t vceq_f16(float16x4_t a, float16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | FCMEQ Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| uint16x8_t vceqq_f16(float16x8_t a, float16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | FCMEQ Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A32/A64                 |
| uint16x4_t vcge_f16(float16x4_t a, float16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | FCMGE Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| uint16x8_t vcgeq_f16(float16x8_t a, float16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | FCMGE Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A32/A64                 |
| uint16x4_t vcgt_f16(float16x4_t a, float16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | FCMGT Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| uint16x8_t vcgtq_f16(float16x8_t a, float16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | FCMGT Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A32/A64                 |
| uint16x4_t vcle_f16(float16x4_t a, float16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | FCMGE Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| uint16x8_t vcleq_f16(float16x8_t a, float16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | FCMGE Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A32/A64                 |
| uint16x4_t vclt_f16(float16x4_t a, float16x4_t b)     | a -> Vn.4H<br>b -> Vm.4H   | FCMGT Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| uint16x8_t vcltq_f16(float16x8_t a, float16x8_t b)    | a -> Vn.8H<br>b -> Vm.8H   | FCMGT Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A32/A64                 |
| float16x4_t vcvq_n_f16_s16(int16x4_t a, const int n)  | a -> Vn.4H<br>1 <= n <= 16 | SCVTF Vd.4H,Vn.4H,#n     | Vd.4H -> result | A32/A64                 |
| float16x8_t vcvq_n_f16_s16(int16x8_t a, const int n)  | a -> Vn.8H<br>1 <= n <= 16 | SCVTF Vd.8H,Vn.8H,#n     | Vd.8H -> result | A32/A64                 |
| float16x4_t vcvq_n_f16_u16(uint16x4_t a, const int n) | a -> Vn.4H<br>1 <= n <= 16 | UCVTF Vd.4H,Vn.4H,#n     | Vd.4H -> result | A32/A64                 |
| float16x8_t vcvq_n_f16_u16(uint16x8_t a, const int n) | a -> Vn.8H<br>1 <= n <= 16 | UCVTF Vd.8H,Vn.8H,#n     | Vd.8H -> result | A32/A64                 |
| int16x4_t vcvq_n_s16_f16(float16x4_t a, const int n)  | a -> Vn.4H<br>1 <= n <= 16 | FCVTZS Vd.4H,Vn.4H,#n    | Vd.4H -> result | A32/A64                 |
| int16x8_t vcvq_n_s16_f16(float16x8_t a, const int n)  | a -> Vn.8H<br>1 <= n <= 16 | FCVTZS Vd.8H,Vn.8H,#n    | Vd.8H -> result | A32/A64                 |
| uint16x4_t vcvq_n_u16_f16(float16x4_t a, const int n) | a -> Vn.4H<br>1 <= n <= 16 | FCVTZU Vd.4H,Vn.4H,#n    | Vd.4H -> result | A32/A64                 |
| uint16x8_t vcvq_n_u16_f16(float16x8_t a, const int n) | a -> Vn.8H<br>1 <= n <= 16 | FCVTZU Vd.8H,Vn.8H,#n    | Vd.8H -> result | A32/A64                 |
| float16x4_t vdiv_f16(float16x4_t a, float16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | FDIV Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A64                     |
| float16x8_t vdivq_f16(float16x8_t a, float16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | FDIV Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A64                     |
| float16x4_t vmax_f16(float16x4_t a, float16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | FMAX Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A32/A64                 |
| float16x8_t vmaxq_f16(float16x8_t a, float16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | FMAX Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A32/A64                 |
| float16x4_t vmaxm_f16(float16x4_t a, float16x4_t b)   | a -> Vn.4H<br>b -> Vm.4H   | FMAXNM Vd.4H,Vn.4H,Vm.4H | Vd.4H -> result | A32/A64                 |
| float16x8_t vmaxmq_f16(float16x8_t a, float16x8_t b)  | a -> Vn.8H<br>b -> Vm.8H   | FMAXNM Vd.8H,Vn.8H,Vm.8H | Vd.8H -> result | A32/A64                 |
| float16x4_t vmin_f16(float16x4_t a, float16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | FMIN Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A32/A64                 |
| float16x8_t vminq_f16(float16x8_t a, float16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | FMIN Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A32/A64                 |
| float16x4_t vminm_f16(float16x4_t a, float16x4_t b)   | a -> Vn.4H<br>b -> Vm.4H   | FMINNM Vd.4H,Vn.4H,Vm.4H | Vd.4H -> result | A32/A64                 |
| float16x8_t vminmq_f16(float16x8_t a, float16x8_t b)  | a -> Vn.8H<br>b -> Vm.8H   | FMINNM Vd.8H,Vn.8H,Vm.8H | Vd.8H -> result | A32/A64                 |
| float16x4_t vmul_f16(float16x4_t a, float16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | FMUL Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A32/A64                 |
| float16x8_t vmulq_f16(float16x8_t a, float16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | FMUL Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A32/A64                 |
| float16x4_t vmulx_f16(float16x4_t a, float16x4_t b)   | a -> Vn.4H<br>b -> Vm.4H   | FMULX Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A64                     |
| float16x8_t vmulxq_f16(float16x8_t a, float16x8_t b)  | a -> Vn.8H<br>b -> Vm.8H   | FMULX Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A64                     |
| float16x4_t vpadd_f16(float16x4_t a, float16x4_t b)   | a -> Vn.4H<br>b -> Vm.4H   | FADDP Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| float16x8_t vpaddq_f16(float16x8_t a, float16x8_t b)  | a -> Vn.8H<br>b -> Vm.8H   | FADDP Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A64                     |
| float16x4_t vmax_f16(float16x4_t a, float16x4_t b)    | a -> Vn.4H<br>b -> Vm.4H   | FMAXP Vd.4H,Vn.4H,Vm.4H  | Vd.4H -> result | A32/A64                 |
| float16x8_t vmaxq_f16(float16x8_t a, float16x8_t b)   | a -> Vn.8H<br>b -> Vm.8H   | FMAXP Vd.8H,Vn.8H,Vm.8H  | Vd.8H -> result | A64                     |

| Intrinsic                                                                              | Argument Preparation                                    | Instruction                 | Result          | Supported Architectures |
|----------------------------------------------------------------------------------------|---------------------------------------------------------|-----------------------------|-----------------|-------------------------|
| float16x4_1 vpmmax_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FMAXNMP Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A64                     |
| float16x4_1 vpmmax_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FMAXNMP Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A64                     |
| float16x4_1 vpmmin_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FMINP Vd.4H,Vn.4H,Vm.4H     | Vd.4H -> result | A32/A64                 |
| float16x4_1 vpmmin_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FMINP Vd.8H,Vn.8H,Vm.8H     | Vd.8H -> result | A64                     |
| float16x4_1 vpmmin_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FMINNMP Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A64                     |
| float16x4_1 vpmmin_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FMINNMP Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A64                     |
| float16x4_1 vrecps_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FREECPS Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A32/A64                 |
| float16x4_1 vrecps_1f16float16x4_1 a, float16x4_1 b                                    | a -> Vn.BH<br>b -> Vm.BH                                | FREECPS Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A32/A64                 |
| float16x4_1 vrsqrts_1f16float16x4_1 a, float16x4_1 b                                   | a -> Vn.BH<br>b -> Vm.BH                                | FRSQRTS Vd.4H,Vn.4H,Vm.4H   | Vd.4H -> result | A32/A64                 |
| float16x4_1 vrsqrts_1f16float16x4_1 a, float16x4_1 b                                   | a -> Vn.BH<br>b -> Vm.BH                                | FRSQRTS Vd.8H,Vn.8H,Vm.8H   | Vd.8H -> result | A32/A64                 |
| float16x4_1 vsdb_1f16float16x4_1 a, float16x4_1 b                                      | a -> Vn.BH<br>b -> Vm.BH                                | FSUB Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result | A32/A64                 |
| float16x4_1 vsdb_1f16float16x4_1 a, float16x4_1 b                                      | a -> Vn.BH<br>b -> Vm.BH                                | FSUB Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result | A32/A64                 |
| float16x4_1 vmsa_1f16float16x4_1 a, float16x4_1 b, float16x4_1 c                       | a -> Vd.BH<br>b -> Vn.BH<br>c -> Vm.BH                  | FMLA Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result | A32/A64                 |
| float16x4_1 vmsaq_1f16float16x4_1 a, float16x4_1 b, float16x4_1 c                      | a -> Vd.BH<br>b -> Vn.BH<br>c -> Vm.BH                  | FMLA Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result | A32/A64                 |
| float16x4_1 vmsa_1f16float16x4_1 a, float16x4_1 b, float16x4_1 c                       | a -> Vd.BH<br>b -> Vn.BH<br>c -> Vm.BH                  | FMLS Vd.4H,Vn.4H,Vm.4H      | Vd.4H -> result | A32/A64                 |
| float16x4_1 vmsaq_1f16float16x4_1 a, float16x4_1 b, float16x4_1 c                      | a -> Vd.BH<br>b -> Vn.BH<br>c -> Vm.BH                  | FMLS Vd.8H,Vn.8H,Vm.8H      | Vd.8H -> result | A32/A64                 |
| float16x4_1 vmsa_lane_1f16float16x4_1 a, float16x4_1 b, float16x4_1 v, const int lane  | a -> Vd.BH<br>b -> Vn.BH<br>v -> Vm.BH<br>0 -> lane < 3 | FMLA Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| float16x4_1 vmsaq_lane_1f16float16x4_1 a, float16x4_1 b, float16x4_1 v, const int lane | a -> Vd.BH<br>b -> Vn.BH<br>v -> Vm.BH<br>0 -> lane < 3 | FMLA Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |
| float16x4_1 vmsa_lane_1f16float16x4_1 a, float16x4_1 b, float16x4_1 v, const int lane  | a -> Vd.BH<br>b -> Vn.BH<br>v -> Vm.BH<br>0 -> lane < 7 | FMLA Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| float16x4_1 vmsaq_lane_1f16float16x4_1 a, float16x4_1 b, float16x4_1 v, const int lane | a -> Vd.BH<br>b -> Vn.BH<br>v -> Vm.BH<br>0 -> lane < 7 | FMLA Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |
| float16x4_1 vmsa_n_1f16float16x4_1 a, float16x4_1 b, float16x4_1 n                     | a -> Vd.BH<br>b -> Vn.BH<br>n -> Vm.H[0]                | FMLA Vd.4H,Vn.4H,Vm.H[0]    | Vd.4H -> result | A64                     |
| float16x4_1 vmsaq_n_1f16float16x4_1 a, float16x4_1 b, float16x4_1 n                    | a -> Vd.BH<br>b -> Vn.BH<br>n -> Vm.H[0]                | FMLA Vd.8H,Vn.8H,Vm.H[0]    | Vd.8H -> result | A64                     |
| float16x4_1 vmsa_lane_1f16float16x4_1 a, float16x4_1 b, float16x4_1 v, const int lane  | a -> Hd<br>b -> Hn<br>v -> Vm.H<br>0 -> lane < 3        | FMLA Hd.Hn,Vm.H[lane]       | Hd -> result    | A64                     |
| float16x4_1 vmsaq_lane_1f16float16x4_1 a, float16x4_1 b, float16x4_1 v, const int lane | a -> Hd<br>b -> Hn<br>v -> Vm.H<br>0 -> lane < 7        | FMLA Hd.Hn,Vm.H[lane]       | Hd -> result    | A64                     |

| Intrinsic                                                                                | Argument Preparation                                     | Instruction                  | Result          | Supported Architectures |
|------------------------------------------------------------------------------------------|----------------------------------------------------------|------------------------------|-----------------|-------------------------|
| float16x4_t vfms_lane_f16(float16x4_t a, float16x4_t b, float16x4_t v, const int lane)   | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3 | FMLS Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A64                     |
| float16x8_t vfmsq_lane_f16(float16x8_t a, float16x8_t b, float16x4_t v, const int lane)  | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3 | FMLS Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A64                     |
| float16x4_t vfms_laneq_f16(float16x4_t a, float16x4_t b, float16x8_t v, const int lane)  | a -> Vd.4H<br>b -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | FMLS Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A64                     |
| float16x8_t vfmsq_laneq_f16(float16x8_t a, float16x8_t b, float16x8_t v, const int lane) | a -> Vd.8H<br>b -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | FMLS Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A64                     |
| float16x4_t vfms_n_f16(float16x4_t a, float16x4_t b, float16_t n)                        | a -> Vd.4H<br>b -> Vn.4H<br>n -> Vm.H[0]                 | FMLS Vd.4H,Vn.4H,Vm.H[0]     | Vd.4H -> result | A64                     |
| float16x8_t vfmsq_n_f16(float16x8_t a, float16x8_t b, float16_t n)                       | a -> Vd.8H<br>b -> Vn.8H<br>n -> Vm.H[0]                 | FMLS Vd.8H,Vn.8H,Vm.H[0]     | Vd.8H -> result | A64                     |
| float16_t vfms_lane_f16(float16_t a, float16_t b, float16x4_t v, const int lane)         | a -> Hd<br>b -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3       | FMLS Hd,Hn,Vm.H[lane]        | Hd -> result    | A64                     |
| float16_t vfmsq_laneq_f16(float16_t a, float16_t b, float16x8_t v, const int lane)       | a -> Hd<br>b -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7       | FMLS Hd,Hn,Vm.H[lane]        | Hd -> result    | A64                     |
| float16x4_t vmul_lane_f16(float16x4_t a, float16x4_t v, const int lane)                  | a -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3               | FMUL Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A32/A64                 |
| float16x8_t vmulq_lane_f16(float16x8_t a, float16x4_t v, const int lane)                 | a -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3               | FMUL Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A32/A64                 |
| float16x4_t vmul_laneq_f16(float16x4_t a, float16x8_t v, const int lane)                 | a -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7               | FMUL Vd.4H,Vn.4H,Vm.H[lane]  | Vd.4H -> result | A64                     |
| float16x8_t vmulq_laneq_f16(float16x8_t a, float16x8_t v, const int lane)                | a -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7               | FMUL Vd.8H,Vn.8H,Vm.H[lane]  | Vd.8H -> result | A64                     |
| float16x4_t vmul_n_f16(float16x4_t a, float16_t n)                                       | a -> Vn.4H<br>n -> Vm.H[0]                               | FMUL Vd.4H,Vn.4H,Vm.H[0]     | Vd.4H -> result | A32/A64                 |
| float16x8_t vmulq_n_f16(float16x8_t a, float16_t n)                                      | a -> Vn.8H<br>n -> Vm.H[0]                               | FMUL Vd.8H,Vn.8H,Vm.H[0]     | Vd.8H -> result | A32/A64                 |
| float16_t vmulh_lane_f16(float16_t a, float16x4_t v, const int lane)                     | a -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3                  | FMUL Hd,Hn,Vm.H[lane]        | Hd -> result    | A64                     |
| float16_t vmulh_laneq_f16(float16_t a, float16x8_t v, const int lane)                    | a -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7                  | FMUL Hd,Hn,Vm.H[lane]        | Hd -> result    | A64                     |
| float16x4_t vmulx_lane_f16(float16x4_t a, float16x4_t v, const int lane)                 | a -> Vn.4H<br>v -> Vm.4H<br>0 <= lane <= 3               | FMULX Vd.4H,Vn.4H,Vm.H[lane] | Vd.4H -> result | A64                     |
| float16x8_t vmulxq_lane_f16(float16x8_t a, float16x4_t v, const int lane)                | a -> Vn.8H<br>v -> Vm.4H<br>0 <= lane <= 3               | FMULX Vd.8H,Vn.8H,Vm.H[lane] | Vd.8H -> result | A64                     |

| Intrinsic                                                                  | Argument Preparation                       | Instruction                                        | Result                                               | Supported Architectures |
|----------------------------------------------------------------------------|--------------------------------------------|----------------------------------------------------|------------------------------------------------------|-------------------------|
| float16x4_t vmulx_laneq_f16(float16x4_t a, float16x8_t v, const int lane)  | a -> Vn.4H<br>v -> Vm.8H<br>0 <= lane <= 7 | FMULX Vd.4H,Vn.4H,Vm.H[lane]                       | Vd.4H -> result                                      | A64                     |
| float16x8_t vmulxq_laneq_f16(float16x8_t a, float16x8_t v, const int lane) | a -> Vn.8H<br>v -> Vm.8H<br>0 <= lane <= 7 | FMULX Vd.8H,Vn.8H,Vm.H[lane]                       | Vd.8H -> result                                      | A64                     |
| float16x4_t vmulx_n_f16(float16x4_t a, float16_t n)                        | a -> Vn.4H<br>n -> Vm.H[0]                 | FMULX Vd.4H,Vn.4H,Vm.H[0]                          | Vd.4H -> result                                      | A64                     |
| float16x8_t vmulx_n_f16(float16x8_t a, float16_t n)                        | a -> Vn.8H<br>n -> Vm.H[0]                 | FMULX Vd.8H,Vn.8H,Vm.H[0]                          | Vd.8H -> result                                      | A64                     |
| float16_t vmulxh_lane_f16(float16_t a, float16x4_t v, const int lane)      | a -> Hn<br>v -> Vm.4H<br>0 <= lane <= 3    | FMULX Hd.Hn,Vm.H[lane]                             | Hd -> result                                         | A64                     |
| float16_t vmulxh_laneq_f16(float16_t a, float16x8_t v, const int lane)     | a -> Hn<br>v -> Vm.8H<br>0 <= lane <= 7    | FMULX Hd.Hn,Vm.H[lane]                             | Hd -> result                                         | A64                     |
| float16_t vmavx_f16(float16x4_t a)                                         | a -> Vn.4H                                 | FMAXP Hd,Vn.4H                                     | Hd -> result                                         | A64                     |
| float16_t vmavxq_f16(float16x8_t a)                                        | a -> Vn.8H                                 | FMAXP Hd,Vn.8H                                     | Hd -> result                                         | A64                     |
| float16_t vminv_f16(float16x4_t a)                                         | a -> Vn.4H                                 | FMINP Hd,Vn.4H                                     | Hd -> result                                         | A64                     |
| float16_t vminvq_f16(float16x8_t a)                                        | a -> Vn.8H                                 | FMINP Hd,Vn.8H                                     | Hd -> result                                         | A64                     |
| float16_t vmaxnmv_f16(float16x4_t a)                                       | a -> Vn.4H                                 | FMAXNMP Hd,Vn.4H                                   | Hd -> result                                         | A64                     |
| float16_t vmaxnmvq_f16(float16x8_t a)                                      | a -> Vn.8H                                 | FMAXNMP Hd,Vn.8H                                   | Hd -> result                                         | A64                     |
| float16_t vminnmv_f16(float16x4_t a)                                       | a -> Vn.4H                                 | FMINNMP Hd,Vn.4H                                   | Hd -> result                                         | A64                     |
| float16_t vminnmvq_f16(float16x8_t a)                                      | a -> Vn.8H                                 | FMINNMP Hd,Vn.8H                                   | Hd -> result                                         | A64                     |
| float16x4_t tvbsl_f16(uint16x4_t a, float16x4_t b, float16x4_t c)          | a -> Vd.8B<br>b -> Vn.8B<br>c -> Vm.8B     | BSL Vd.8B,Vn.8B,Vm.8B                              | Vd.8B -> result                                      | v7/A32/A64              |
| float16x8_t tvbslq_f16(uint16x8_t a, float16x8_t b, float16x8_t c)         | a -> Vd.16B<br>b -> Vn.16B<br>c -> Vm.16B  | BSL Vd.16B,Vn.16B,Vm.16B                           | Vd.16B -> result                                     | v7/A32/A64              |
| float16x4x2_t vzip_f16(float16x4_t a, float16x4_t b)                       | a -> Vn.4H<br>b -> Vm.4H                   | ZIP1 Vd1.4H,Vn.4H,Vm.4H<br>ZIP2 Vd2.4H,Vn.4H,Vm.4H | Vd1.4H -> result[val[0]]<br>Vd2.4H -> result[val[1]] | v7/A32/A64              |
| float16x8x2_t vzipq_f16(float16x8_t a, float16x8_t b)                      | a -> Vn.8H<br>b -> Vm.8H                   | ZIP1 Vd1.8H,Vn.8H,Vm.8H<br>ZIP2 Vd2.8H,Vn.8H,Vm.8H | Vd1.8H -> result[val[0]]<br>Vd2.8H -> result[val[1]] | v7/A32/A64              |
| float16x4x2_t vuzpq_f16(float16x4_t a, float16x4_t b)                      | a -> Vn.4H<br>b -> Vm.4H                   | UZP1 Vd1.4H,Vn.4H,Vm.4H<br>UZP2 Vd2.4H,Vn.4H,Vm.4H | Vd1.4H -> result[val[0]]<br>Vd2.4H -> result[val[1]] | v7/A32/A64              |
| float16x8x2_t vuzpq_f16(float16x8_t a, float16x8_t b)                      | a -> Vn.8H<br>b -> Vm.8H                   | UZP1 Vd1.8H,Vn.8H,Vm.8H<br>UZP2 Vd2.8H,Vn.8H,Vm.8H | Vd1.8H -> result[val[0]]<br>Vd2.8H -> result[val[1]] | v7/A32/A64              |
| float16x4x2_t vtrn_f16(float16x4_t a, float16x4_t b)                       | a -> Vn.4H<br>b -> Vm.4H                   | TRN1 Vd1.4H,Vn.4H,Vm.4H<br>TRN2 Vd2.4H,Vn.4H,Vm.4H | Vd1.4H -> result[val[0]]<br>Vd2.4H -> result[val[1]] | v7/A32/A64              |
| float16x8x2_t vtrnq_f16(float16x8_t a, float16x8_t b)                      | a -> Vn.8H<br>b -> Vm.8H                   | TRN1 Vd1.8H,Vn.8H,Vm.8H<br>TRN2 Vd2.8H,Vn.8H,Vm.8H | Vd1.8H -> result[val[0]]<br>Vd2.8H -> result[val[1]] | v7/A32/A64              |
| float16x4_t vmov_n_f16(float16_t value)                                    | value -> rn                                | DUP Vd.4H,rn                                       | Vd.4H -> result                                      | v7/A32/A64              |
| float16x8_t vmovq_n_f16(float16_t value)                                   | value -> rn                                | DUP Vd.8H,rn                                       | Vd.8H -> result                                      | v7/A32/A64              |
| float16x4_t vdup_n_f16(float16_t value)                                    | value -> rn                                | DUP Vd.4H,rn                                       | Vd.4H -> result                                      | v7/A32/A64              |
| float16x8_t vdupq_n_f16(float16_t value)                                   | value -> rn                                | DUP Vd.8H,rn                                       | Vd.8H -> result                                      | v7/A32/A64              |
| float16x4_t vdup_lane_f16(float16x4_t v, vec, const int lane)              | vec -> Vn.4H<br>0 <= lane <= 3             | DUP Vd.4H,Vn.H[lane]                               | Vd.4H -> result                                      | v7/A32/A64              |
| float16x8_t vdupq_lane_f16(float16x4_t vec, const int lane)                | vec -> Vn.4H<br>0 <= lane <= 3             | DUP Vd.8H,Vn.H[lane]                               | Vd.8H -> result                                      | v7/A32/A64              |
| float16x4_t vext_f16(float16x4_t a, float16x4_t b, const int n)            | a -> Vn.8B<br>b -> Vm.8B<br>0 <= n <= 3    | EXT Vd.8B,Vn.8B,Vm.8B,#(n<1)                       | Vd.8B -> result                                      | v7/A32/A64              |

| Intrinsic                                                                            | Argument Preparation                                      | Instruction                     | Result           | Supported Architectures |
|--------------------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------|------------------|-------------------------|
| float16x8_t vextq_f16(float16x8_t a, float16x8_t b, const int n)                     | a -> Vn.16B<br>b -> Vm.16B<br>0 <= n <= 7                 | EXT Vd.16B,Vn.16B,Vm.16B,#(n<1) | Vd.16B -> result | v7/A32/A64              |
| float16x4_t vrev64_f16(float16x4_t vec)                                              | vec -> Vn.4H                                              | REV64 Vd.4H,Vn.4H               | Vd.4H -> result  | v7/A32/A64              |
| float16x8_t vrev64q_f16(float16x8_t vec)                                             | vec -> Vn.8H                                              | REV64 Vd.8H,Vn.8H               | Vd.8H -> result  | v7/A32/A64              |
| float16x4_t vzip1_f16(float16x4_t a, float16x4_t b)                                  | a -> Vn.4H<br>b -> Vm.4H                                  | ZIP1 Vd.4H,Vn.4H,Vm.4H          | Vd.4H -> result  | A64                     |
| float16x8_t vzip1q_f16(float16x8_t a, float16x8_t b)                                 | a -> Vn.8H<br>b -> Vm.8H                                  | ZIP1 Vd.8H,Vn.8H,Vm.8H          | Vd.8H -> result  | A64                     |
| float16x4_t vzip2_f16(float16x4_t a, float16x4_t b)                                  | a -> Vn.4H<br>b -> Vm.4H                                  | ZIP2 Vd.4H,Vn.4H,Vm.4H          | Vd.4H -> result  | A64                     |
| float16x8_t vzip2q_f16(float16x8_t a, float16x8_t b)                                 | a -> Vn.8H<br>b -> Vm.8H                                  | ZIP2 Vd.8H,Vn.8H,Vm.8H          | Vd.8H -> result  | A64                     |
| float16x4_t vuzp1_f16(float16x4_t a, float16x4_t b)                                  | a -> Vn.4H<br>b -> Vm.4H                                  | UZP1 Vd.4H,Vn.4H,Vm.4H          | Vd.4H -> result  | A64                     |
| float16x8_t vuzp1q_f16(float16x8_t a, float16x8_t b)                                 | a -> Vn.8H<br>b -> Vm.8H                                  | UZP1 Vd.8H,Vn.8H,Vm.8H          | Vd.8H -> result  | A64                     |
| float16x4_t vuzp2_f16(float16x4_t a, float16x4_t b)                                  | a -> Vn.4H<br>b -> Vm.4H                                  | UZP2 Vd.4H,Vn.4H,Vm.4H          | Vd.4H -> result  | A64                     |
| float16x8_t vuzp2q_f16(float16x8_t a, float16x8_t b)                                 | a -> Vn.8H<br>b -> Vm.8H                                  | UZP2 Vd.8H,Vn.8H,Vm.8H          | Vd.8H -> result  | A64                     |
| float16x4_t vtrn1_f16(float16x4_t a, float16x4_t b)                                  | a -> Vn.4H<br>b -> Vm.4H                                  | TRN1 Vd.4H,Vn.4H,Vm.4H          | Vd.4H -> result  | A64                     |
| float16x8_t vtrn1q_f16(float16x8_t a, float16x8_t b)                                 | a -> Vn.8H<br>b -> Vm.8H                                  | TRN1 Vd.8H,Vn.8H,Vm.8H          | Vd.8H -> result  | A64                     |
| float16x4_t vtrn2_f16(float16x4_t a, float16x4_t b)                                  | a -> Vn.4H<br>b -> Vm.4H                                  | TRN2 Vd.4H,Vn.4H,Vm.4H          | Vd.4H -> result  | A64                     |
| float16x8_t vtrn2q_f16(float16x8_t a, float16x8_t b)                                 | a -> Vn.8H<br>b -> Vm.8H                                  | TRN2 Vd.8H,Vn.8H,Vm.8H          | Vd.8H -> result  | A64                     |
| float16x4_t vdup_laneq_f16(float16x8_t vec, const int lane)                          | vec -> Vn.8H<br>0 <= lane <= 7                            | DUP Vd.4H,Vn.H[lane]            | Vd.4H -> result  | A64                     |
| float16x8_t vdupq_laneq_f16(float16x8_t vec, const int lane)                         | vec -> Vn.8H<br>0 <= lane <= 7                            | DUP Vd.8H,Vn.H[lane]            | Vd.8H -> result  | A64                     |
| float16_t vduph_lane_f16(float16x4_t vec, const int lane)                            | vec -> Vn.4H<br>0 <= lane <= 3                            | DUP Hd,Vn.H[lane]               | Hd -> result     | A64                     |
| float16_t vduph_laneq_f16(float16x8_t vec, const int lane)                           | vec -> Vn.8H<br>0 <= lane <= 7                            | DUP Hd,Vn.H[lane]               | Hd -> result     | A64                     |
| uint32x2_t vdot_u32(uint32x2_t r, uint8x8_t a, uint8x8_t b)                          | r -> Vd.2S<br>a -> Vn.8B<br>b -> Vm.8B                    | UDOT Vd.2S,Vn.8B,Vm.8B          | Vd.2S -> result  | A32/A64                 |
| int32x2_t vdot_s32(int32x2_t r, int8x8_t a, int8x8_t b)                              | r -> Vd.2S<br>a -> Vn.8B<br>b -> Vm.8B                    | SDOT Vd.2S,Vn.8B,Vm.8B          | Vd.2S -> result  | A32/A64                 |
| uint32x4_t vdotq_u32(uint32x4_t r, uint8x16_t a, uint8x16_t b)                       | r -> Vd.4S<br>a -> Vn.16B<br>b -> Vm.16B                  | UDOT Vd.4S,Vn.16B,Vm.16B        | Vd.4S -> result  | A32/A64                 |
| int32x4_t vdotq_s32(int32x4_t r, int8x16_t a, int8x16_t b)                           | r -> Vd.4S<br>a -> Vn.16B<br>b -> Vm.16B                  | SDOT Vd.4S,Vn.16B,Vm.16B        | Vd.4S -> result  | A32/A64                 |
| uint32x2_t vdot_lane_u32(uint32x2_t r, uint8x8_t a, uint8x8_t b, const int lane)     | r -> Vd.2S<br>a -> Vn.8B<br>b -> Vm.4B<br>0 <= lane <= 1  | UDOT Vd.2S,Vn.8B,Vm.4B[lane]    | Vd.2S -> result  | A32/A64                 |
| int32x2_t vdot_lane_s32(int32x2_t r, int8x8_t a, int8x8_t b, const int lane)         | r -> Vd.2S<br>a -> Vn.8B<br>b -> Vm.4B<br>0 <= lane <= 1  | SDOT Vd.2S,Vn.8B,Vm.4B[lane]    | Vd.2S -> result  | A32/A64                 |
| uint32x4_t vdotq_laneq_u32(uint32x4_t r, uint8x16_t a, uint8x16_t b, const int lane) | r -> Vd.4S<br>a -> Vn.16B<br>b -> Vm.4B<br>0 <= lane <= 3 | UDOT Vd.4S,Vn.16B,Vm.4B[lane]   | Vd.4S -> result  | A64                     |
| int32x4_t vdotq_laneq_s32(int32x4_t r, int8x16_t a, int8x16_t b, const int lane)     | r -> Vd.4S<br>a -> Vn.16B<br>b -> Vm.4B<br>0 <= lane <= 3 | SDOT Vd.4S,Vn.16B,Vm.4B[lane]   | Vd.4S -> result  | A64                     |

| Intrinsic                                                                              | Argument Preparation                                      | Instruction                         | Result           | Supported Architectures |
|----------------------------------------------------------------------------------------|-----------------------------------------------------------|-------------------------------------|------------------|-------------------------|
| uint32x2_t vdot_lane_u32(uint32x2_t r, uint8x8_t a, uint8x16_t b, const int lane)      | r -> Vd.2S<br>a -> Vn.8B<br>b -> Vm.4B<br>0 <= lane <= 3  | UDOT Vd.2S,Vn.8B,Vm.4B[lane]        | Vd.2S -> result  | A64                     |
| int32x2_t vdot_lane_s32(int32x2_t r, int8x8_t a, int8x16_t b, const int lane)          | r -> Vd.2S<br>a -> Vn.8B<br>b -> Vm.4B<br>0 <= lane <= 3  | SDOT Vd.2S,Vn.8B,Vm.4B[lane]        | Vd.2S -> result  | A64                     |
| uint32x4_t vdotq_lane_u32(uint32x4_t r, uint8x16_t a, uint8x8_t b, const int lane)     | r -> Vd.4S<br>a -> Vn.16B<br>b -> Vm.4B<br>0 <= lane <= 1 | UDOT Vd.4S,Vn.16B,Vm.4B[lane]       | Vd.4S -> result  | A32/A64                 |
| int32x4_t vdotq_lane_s32(int32x4_t r, int8x16_t a, int8x8_t b, const int lane)         | r -> Vd.4S<br>a -> Vn.16B<br>b -> Vm.4B<br>0 <= lane <= 1 | SDOT Vd.4S,Vn.16B,Vm.4B[lane]       | Vd.4S -> result  | A32/A64                 |
| uint64x2_t vsha512hq_u64(uint64x2_t hash, ed, uint64x2_t hash_gf, uint64x2_t kwh_kwh2) | hash_ed -> Qd<br>hash_gf -> Qn                            | SHA512H Qd,Qn,Vm.2D                 | Qd -> result     | A64                     |
| uint64x2_t vsha512h2q_u64(uint64x2_t sum_ab, uint64x2_t hash_c, uint64x2_t hash_ab)    | sum_ab -> Qd<br>hash_c -> Qn                              | SHA512H2 Qd,Qn,Vm.2D                | Qd -> result     | A64                     |
| uint64x2_t vsha512su0q_u64(uint64x2_t w0_1, uint64x2_t w2_)                            | w0_1 -> Vd.2D<br>w2 -> Vn.2D                              | SHA512SU0 Vd.2D,Vn.2D               | Vd.2D -> result  | A64                     |
| uint64x2_t vsha512su1q_u64(uint64x2_t s01_s02, uint64x2_t w14_15, uint64x2_t w9_10)    | s01_s02 -> Vd.2D<br>w14_15 -> Vn.2D                       | SHA512SU1 Vd.2D,Vn.2D,Vm.2D         | Vd.2D -> result  | A64                     |
| uint8x16_t veor_3q_u8(uint8x16_t a, uint8x16_t b, uint8x16_t c)                        | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint16x8_t veor_3q_u16(uint16x8_t a, uint16x8_t b, uint16x8_t c)                       | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint32x4_t veor_3q_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)                       | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint64x2_t veor_3q_u64(uint64x2_t a, uint64x2_t b, uint64x2_t c)                       | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int8x16_t veor_3q_s8(int8x16_t a, int8x16_t b, int8x16_t c)                            | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int16x8_t veor_3q_s16(int16x8_t a, int16x8_t b, int16x8_t c)                           | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int32x4_t veor_3q_s32(int32x4_t a, int32x4_t b, int32x4_t c)                           | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int64x2_t veor_3q_s64(int64x2_t a, int64x2_t b, int64x2_t c)                           | a -> Vn.16B                                               | EOR3<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint64x2_t vraxq_u64(uint64x2_t a, uint64x2_t b)                                       | a -> Vn.2D<br>b -> Vn.2D<br>0 <= imm6 <= 63               | RAX1 Vd.2D,Vn.2D,Vm.2D              | Vd.2D -> result  | A64                     |
| uint64x2_t vaxrq_u64(uint64x2_t a, uint64x2_t b, const int imm6)                       | a -> Vn.2D<br>b -> Vn.2D<br>0 <= imm6 <= 63               | XAR Vd.2D,Vn.2D,Vm.2D,Imm6          | Vd.2D -> result  | A64                     |
| uint8x16_t vbcaxq_u8(uint8x16_t a, uint8x16_t b, uint8x16_t c)                         | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint16x8_t vbcaxq_u16(uint16x8_t a, uint16x8_t b, uint16x8_t c)                        | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint32x4_t vbcaxq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)                        | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| uint64x2_t vbcaxq_u64(uint64x2_t a, uint64x2_t b, uint64x2_t c)                        | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int8x16_t vbcaxq_s8(int8x16_t a, int8x16_t b, int8x16_t c)                             | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int16x8_t vbcaxq_s16(int16x8_t a, int16x8_t b, int16x8_t c)                            | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int32x4_t vbcaxq_s32(int32x4_t a, int32x4_t b, int32x4_t c)                            | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |
| int64x2_t vbcaxq_s64(int64x2_t a, int64x2_t b, int64x2_t c)                            | a -> Vn.16B                                               | BCAX<br>Vd.16B,Vn.16B,Vm.16B,Va.16B | Vd.16B -> result | A64                     |

| Intrinsic                                                                                      | Argument Preparation          | Instruction                        | Result          | Supported Architectures |
|------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------|-----------------|-------------------------|
| uint32x4_t vsm3ss1q_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)                              | a->Vn,4S                      | SM3SS1 Vd,4S,Vn,4S,Vm,4S,Va,4S     | Vd,4S -> result | A64                     |
| uint32x4_t vsm3tt1aq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c, const int imm2)             | a->Vd,4S<br>0 <= imm2<br><= 3 | SM3TT1A<br>Vd,4S,Vn,4S,Vm,4S[imm2] | Vd,4S -> result | A64                     |
| uint32x4_t vsm3tt1bq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c, const int imm2)             | a->Vd,4S<br>0 <= imm2<br><= 3 | SM3TT1B<br>Vd,4S,Vn,4S,Vm,4S[imm2] | Vd,4S -> result | A64                     |
| uint32x4_t vsm3tt2aq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c, const int imm2)             | a->Vd,4S<br>0 <= imm2<br><= 3 | SM3TT2A<br>Vd,4S,Vn,4S,Vm,4S[imm2] | Vd,4S -> result | A64                     |
| uint32x4_t vsm3tt2bq_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c, const int imm2)             | a->Vd,4S<br>0 <= imm2<br><= 3 | SM3TT2B<br>Vd,4S,Vn,4S,Vm,4S[imm2] | Vd,4S -> result | A64                     |
| uint32x4_t vsm3partw1q_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)                           | a->Vd,4S                      | SM3PARTW1 Vd,4S,Vn,4S,Vm,4S        | Vd,4S -> result | A64                     |
| uint32x4_t vsm3partw2q_u32(uint32x4_t a, uint32x4_t b, uint32x4_t c)                           | a->Vd,4S                      | SM3PARTW2 Vd,4S,Vn,4S,Vm,4S        | Vd,4S -> result | A64                     |
| uint32x4_t vsm4eq_u32(uint32x4_t a, uint32x4_t b)                                              | a->Vd,4S                      | SM4E Vd,4S,Vn,4S                   | Vd,4S -> result | A64                     |
| uint32x4_t vsm4keyq_u32(uint32x4_t a, uint32x4_t b)                                            | a->Vn,4S                      | SM4KEY Vd,4S,Vn,4S,Vm,4S           | Vd,4S -> result | A64                     |
| float32x2_t vfmlal_low_f16(float32x2_t r, float16x4_t a, float16x4_t b)                        | r->Vd,2S                      | FMLAL Vd,2S,Vn,2H,Vm,2H            | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlsl_low_f16(float32x2_t r, float16x4_t a, float16x4_t b)                        | r->Vd,2S                      | FMLSL Vd,2S,Vn,2H,Vm,2H            | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlalq_low_f16(float32x2_t r, float16x8_t a, float16x8_t b)                       | r->Vd,4S                      | FMLAL Vd,4S,Vn,4H,Vm,4H            | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlslq_low_f16(float32x2_t r, float16x8_t a, float16x8_t b)                       | r->Vd,4S                      | FMLSL Vd,4S,Vn,4H,Vm,4H            | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlal_high_f16(float32x2_t r, float16x8_t a, float16x8_t b)                       | r->Vd,2S                      | FMLAL2 Vd,2S,Vn,2H,Vm,2H           | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlsl_high_f16(float32x2_t r, float16x8_t a, float16x8_t b)                       | r->Vd,2S                      | FMLSL2 Vd,2S,Vn,2H,Vm,2H           | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlalq_high_f16(float32x2_t r, float16x8_t a, float16x8_t b)                      | r->Vd,4S                      | FMLAL2 Vd,4S,Vn,4H,Vm,4H           | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlslq_high_f16(float32x2_t r, float16x8_t a, float16x8_t b)                      | r->Vd,4S                      | FMLSL2 Vd,4S,Vn,4H,Vm,4H           | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlal_lane_low_f16(float32x2_t r, float16x4_t a, float16x4_t b, const int lane)   | r->Vd,2S<br>0 <= lane <= 3    | FMLAL Vd,2S,Vn,2H,Vm,H[lane]       | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlsl_lane_low_f16(float32x2_t r, float16x4_t a, float16x4_t b, const int lane)   | r->Vd,2S<br>0 <= lane <= 3    | FMLSL Vd,2S,Vn,2H,Vm,H[lane]       | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlalq_lane_low_f16(float32x2_t r, float16x8_t a, float16x8_t b, const int lane)  | r->Vd,4S<br>0 <= lane <= 3    | FMLAL Vd,4S,Vn,4H,Vm,H[lane]       | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlslq_lane_low_f16(float32x2_t r, float16x8_t a, float16x8_t b, const int lane)  | r->Vd,4S<br>0 <= lane <= 3    | FMLSL Vd,4S,Vn,4H,Vm,H[lane]       | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlal_lane_high_f16(float32x2_t r, float16x4_t a, float16x4_t b, const int lane)  | r->Vd,2S<br>0 <= lane <= 3    | FMLAL2 Vd,2S,Vn,2H,Vm,H[lane]      | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlsl_lane_high_f16(float32x2_t r, float16x4_t a, float16x4_t b, const int lane)  | r->Vd,2S<br>0 <= lane <= 3    | FMLSL2 Vd,2S,Vn,2H,Vm,H[lane]      | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmlalq_lane_high_f16(float32x2_t r, float16x8_t a, float16x8_t b, const int lane) | r->Vd,4S<br>0 <= lane <= 3    | FMLAL2 Vd,4S,Vn,4H,Vm,H[lane]      | Vd,4S -> result | A32/A64                 |
| float32x2_t vfmlslq_lane_high_f16(float32x2_t r, float16x8_t a, float16x8_t b, const int lane) | r->Vd,4S<br>0 <= lane <= 3    | FMLSL2 Vd,4S,Vn,4H,Vm,H[lane]      | Vd,4S -> result | A32/A64                 |

| Intrinsic                                                                                       | Argument Preparation         | Instruction                                              | Result          | Supported Architectures |
|-------------------------------------------------------------------------------------------------|------------------------------|----------------------------------------------------------|-----------------|-------------------------|
| float32x2_t vfmmla_laneq_high_f16(float32x2_t r, float16x4_t a, float16x8_t b, const int lane)  | r -> Vd,2S<br>0 <= lane <= 7 | FMLAL2 Vd,2S,Vn,2H,Vm,H[lane]                            | Vd,2S -> result | A32/A64                 |
| float32x2_t vfmisq_laneq_high_f16(float32x2_t r, float16x4_t a, float16x8_t b, const int lane)  | r -> Vd,2S<br>0 <= lane <= 7 | FMLSL2 Vd,2S,Vn,2H,Vm,H[lane]                            | Vd,2S -> result | A32/A64                 |
| float32x4_t vfmmlaq_laneq_high_f16(float32x4_t r, float16x8_t a, float16x8_t b, const int lane) | r -> Vd,4S<br>0 <= lane <= 7 | FMLAL2 Vd,4S,Vn,4H,Vm,H[lane]                            | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmisq_laneq_high_f16(float32x4_t r, float16x8_t a, float16x8_t b, const int lane)  | r -> Vd,4S<br>0 <= lane <= 7 | FMLSL2 Vd,4S,Vn,4H,Vm,H[lane]                            | Vd,4S -> result | A32/A64                 |
| float16x4_t vccadd_rot90_f16(float16x4_t a, float16x4_t b)                                      | a -> Vn,4H<br>b -> Vm,4H     | FCADD Vd,4H,Vn,4H,Vm,4H,#90                              | Vd,4H -> result | A32/A64                 |
| float32x2_t vccadd_rot90_f32(float32x2_t a, float32x2_t b)                                      | a -> Vn,2S<br>b -> Vm,2S     | FCADD Vd,2S,Vn,2S,Vm,2S,#90                              | Vd,2S -> result | A32/A64                 |
| float16x8_t vccaddq_rot90_f16(float16x8_t a, float16x8_t b)                                     | a -> Vn,8H<br>b -> Vm,8H     | FCADD Vd,8H,Vn,8H,Vm,8H,#90                              | Vd,8H -> result | A32/A64                 |
| float32x4_t vccaddq_rot90_f32(float32x4_t a, float32x4_t b)                                     | a -> Vn,4S<br>b -> Vm,4S     | FCADD Vd,4S,Vn,4S,Vm,4S,#90                              | Vd,4S -> result | A32/A64                 |
| float64x2_t vccaddq_rot90_f64(float64x2_t a, float64x2_t b)                                     | a -> Vn,2D<br>b -> Vm,2D     | FCADD Vd,2D,Vn,2D,Vm,2D,#90                              | Vd,2D -> result | A64                     |
| float16x4_t vccaddq_rot270_f16(float16x4_t a, float16x4_t b)                                    | a -> Vn,4H<br>b -> Vm,4H     | FCADD Vd,4H,Vn,4H,Vm,4H,#270                             | Vd,4H -> result | A32/A64                 |
| float32x2_t vccaddq_rot270_f32(float32x2_t a, float32x2_t b)                                    | a -> Vn,2S<br>b -> Vm,2S     | FCADD Vd,2S,Vn,2S,Vm,2S,#270                             | Vd,2S -> result | A32/A64                 |
| float16x8_t vccaddq_rot270_f16(float16x8_t a, float16x8_t b)                                    | a -> Vn,8H<br>b -> Vm,8H     | FCADD Vd,8H,Vn,8H,Vm,8H,#270                             | Vd,8H -> result | A32/A64                 |
| float32x4_t vccaddq_rot270_f32(float32x4_t a, float32x4_t b)                                    | a -> Vn,4S<br>b -> Vm,4S     | FCADD Vd,4S,Vn,4S,Vm,4S,#270                             | Vd,4S -> result | A32/A64                 |
| float64x2_t vccaddq_rot270_f64(float64x2_t a, float64x2_t b)                                    | a -> Vn,2D<br>b -> Vm,2D     | FCADD Vd,2D,Vn,2D,Vm,2D,#270                             | Vd,2D -> result | A64                     |
| float16x4_t vcmia_f16(float16x4_t r, float16x4_t a, float16x4_t b)                              | r -> Vd,4H                   | FCMLA Vd,4H,Vn,4H,Vm,4H,#0                               | Vd,4H -> result | A32/A64                 |
| float32x2_t vcmia_f32(float32x2_t r, float32x2_t a, float32x2_t b)                              | r -> Vd,2S                   | FCMLA Vd,2S,Vn,2S,Vm,2S,#0                               | Vd,2S -> result | A32/A64                 |
| float16x4_t vcmia_lane_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)         | r -> Vd,4H<br>0 <= lane <= 1 | FCMLA Vd,4H,Vn,4H,Vm,H[lane],#0                          | Vd,4H -> result | A32/A64                 |
| float32x2_t vcmia_lane_f32(float32x2_t r, float32x2_t a, float32x2_t b, const int lane)         | r -> Vd,2S<br>lane == 0      | FCMLA Vd,2S,Vn,2S,Vm,2S,#0                               | Vd,2S -> result | A32/A64                 |
| float16x4_t vcmia_laneq_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)        | r -> Vd,4H<br>0 <= lane <= 1 | FCMLA Vd,4H,Vn,4H,Vm,H[lane],#0                          | Vd,4H -> result | A32/A64                 |
| float16x4_t vcmia_laneq_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)        | r -> Vd,4H<br>2 <= lane <= 3 | DUP Dm,Vm,D[1]<br>FCMLA Vd,4H,Vn,4H,Vm,4H,H[lane % 2],#0 | Vd,4H -> result | A32/A64                 |
| float32x2_t vcmia_laneq_f32(float32x2_t r, float32x2_t a, float32x2_t b, const int lane)        | r -> Vd,2S<br>0 <= lane <= 1 | DUP Dm,Vm,D[1]<br>FCMLA Vd,2S,Vn,2S,Vm,2S,#0             | Vd,2S -> result | A32/A64                 |
| float16x8_t vcmiaq_f16(float16x8_t r, float16x8_t a, float16x8_t b)                             | r -> Vd,8H                   | FCMLA Vd,8H,Vn,8H,Vm,8H,#0                               | Vd,8H -> result | A32/A64                 |
| float32x4_t vcmiaq_f32(float32x4_t r, float32x4_t a, float32x4_t b)                             | r -> Vd,4S                   | FCMLA Vd,4S,Vn,4S,Vm,4S,#0                               | Vd,4S -> result | A32/A64                 |
| float64x2_t vcmiaq_f64(float64x2_t r, float64x2_t a, float64x2_t b)                             | r -> Vd,2D                   | FCMLA Vd,2D,Vn,2D,Vm,2D,#0                               | Vd,2D -> result | A64                     |
| float16x8_t vcmiaq_lane_f16(float16x8_t r, float16x8_t a, float16x8_t b, const int lane)        | r -> Vd,8H<br>0 <= lane <= 1 | FCMLA Vd,8H,Vn,8H,Vm,H[lane],#0                          | Vd,8H -> result | A32/A64                 |
| float32x4_t vcmiaq_lane_f32(float32x4_t r, float32x4_t a, float32x4_t b, const int lane)        | r -> Vd,4S<br>lane == 0      | FCMLA Vd,4S,Vn,4S,Vm,S[lane],#0                          | Vd,4S -> result | A32/A64                 |
| float16x8_t vcmiaq_laneq_f16(float16x8_t r, float16x8_t a, float16x8_t b, const int lane)       | r -> Vd,8H<br>0 <= lane <= 3 | FCMLA Vd,8H,Vn,8H,Vm,H[lane],#0                          | Vd,8H -> result | A32/A64                 |
| float32x4_t vcmiaq_laneq_f32(float32x4_t r, float32x4_t a, float32x4_t b, const int lane)       | r -> Vd,4S<br>0 <= lane <= 1 | FCMLA Vd,4S,Vn,4S,Vm,S[lane],#0                          | Vd,4S -> result | A32/A64                 |
| float16x4_t vcmia_rot90_f16(float16x4_t r, float16x4_t a, float16x4_t b)                        | r -> Vd,4H                   | FCMLA Vd,4H,Vn,4H,Vm,4H,#90                              | Vd,4H -> result | A32/A64                 |
| float32x2_t vcmia_rot90_f32(float32x2_t r, float32x2_t a, float32x2_t b)                        | r -> Vd,2S                   | FCMLA Vd,2S,Vn,2S,Vm,2S,#90                              | Vd,2S -> result | A32/A64                 |

| Intrinsic                                                                                         | Argument Preparation         | Instruction                                             | Result          | Supported Architectures |
|---------------------------------------------------------------------------------------------------|------------------------------|---------------------------------------------------------|-----------------|-------------------------|
| float16x4_t vcmia, rot90_lane_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)    | r -> Vd.4H<br>0 <= lane <= 1 | FCMLA<br>Vd.4H,Vn.4H,Vm.H[lane],#90                     | Vd.4H -> result | A32/A64                 |
| float32x2_t vcmia, rot90_lane_f32(float32x2_t r, float32x2_t a, float32x2_t b, const int lane)    | r -> Vd.2S<br>lane == 0      | FCMLA Vd.2S,Vn.2S,Vm.2S,#90                             | Vd.2S -> result | A32/A64                 |
| float16x4_t vcmia, rot90_laneq_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)   | r -> Vd.4H<br>0 <= lane <= 1 | FCMLA<br>Vd.4H,Vn.4H,Vm.H[lane],#90                     | Vd.4H -> result | A32/A64                 |
| float16x4_t vcmia, rot90_laneq_f16(float16x4_t r, float16x4_t a, float16x8_t b, const int lane)   | r -> Vd.4H<br>2 <= lane <= 3 | DUP Dm,Vm.D[1]<br>FCMLA Vd.4H,Vn.4H,Vm.H[lane % 2],#90  | Vd.4H -> result | A32/A64                 |
| float32x2_t vcmia, rot90_laneq_f32(float32x2_t r, float32x2_t a, float32x4_t b, const int lane)   | r -> Vd.2S<br>0 <= lane <= 1 | DUP Dm,Vm.D[1]<br>FCMLA Vd.2S,Vn.2S,Vm.2S,#90           | Vd.2S -> result | A32/A64                 |
| float16x8_t vcmiaq, rot90_f16(float16x8_t r, float16x8_t a, float16x8_t b)                        | r -> Vd.8H                   | FCMLA Vd.8H,Vn.8H,Vm.8H,#90                             | Vd.8H -> result | A32/A64                 |
| float32x4_t vcmiaq, rot90_f32(float32x4_t r, float32x4_t a, float32x4_t b)                        | r -> Vd.4S                   | FCMLA Vd.4S,Vn.4S,Vm.4S,#90                             | Vd.4S -> result | A32/A64                 |
| float64x2_t vcmiaq, rot90_f64(float64x2_t r, float64x2_t a, float64x2_t b)                        | r -> Vd.2D                   | FCMLA Vd.2D,Vn.2D,Vm.2D,#90                             | Vd.2D -> result | A64                     |
| float16x8_t vcmiaq, rot90_lane_f16(float16x8_t r, float16x8_t a, float16x4_t b, const int lane)   | r -> Vd.8H<br>0 <= lane <= 1 | FCMLA<br>Vd.8H,Vn.8H,Vm.H[lane],#90                     | Vd.8H -> result | A32/A64                 |
| float32x4_t vcmiaq, rot90_lane_f32(float32x4_t r, float32x4_t a, float32x2_t b, const int lane)   | r -> Vd.4S<br>lane == 0      | FCMLA<br>Vd.4S,Vn.4S,Vm.S[lane],#90                     | Vd.4S -> result | A32/A64                 |
| float16x8_t vcmiaq, rot90_laneq_f16(float16x8_t r, float16x8_t a, float16x8_t b, const int lane)  | r -> Vd.8H<br>0 <= lane <= 3 | FCMLA<br>Vd.8H,Vn.8H,Vm.H[lane],#90                     | Vd.8H -> result | A32/A64                 |
| float32x4_t vcmiaq, rot90_laneq_f32(float32x4_t r, float32x4_t a, float32x4_t b, const int lane)  | r -> Vd.4S<br>0 <= lane <= 1 | FCMLA<br>Vd.4S,Vn.4S,Vm.S[lane],#90                     | Vd.4S -> result | A32/A64                 |
| float16x4_t vcmia, rot180_f16(float16x4_t r, float16x4_t a, float16x4_t b)                        | r -> Vd.4H                   | FCMLA<br>Vd.4H,Vn.4H,Vm.4H,#180                         | Vd.4H -> result | A32/A64                 |
| float32x2_t vcmia, rot180_f32(float32x2_t r, float32x2_t a, float32x2_t b)                        | r -> Vd.2S                   | FCMLA Vd.2S,Vn.2S,Vm.2S,#180                            | Vd.2S -> result | A32/A64                 |
| float16x4_t vcmia, rot180_lane_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)   | r -> Vd.4H<br>0 <= lane <= 1 | FCMLA<br>Vd.4H,Vn.4H,Vm.H[lane],#180                    | Vd.4H -> result | A32/A64                 |
| float32x2_t vcmia, rot180_lane_f32(float32x2_t r, float32x2_t a, float32x2_t b, const int lane)   | r -> Vd.2S<br>lane == 0      | FCMLA Vd.2S,Vn.2S,Vm.2S,#180                            | Vd.2S -> result | A32/A64                 |
| float16x4_t vcmia, rot180_laneq_f16(float16x4_t r, float16x4_t a, float16x8_t b, const int lane)  | r -> Vd.4H<br>0 <= lane <= 1 | FCMLA<br>Vd.4H,Vn.4H,Vm.H[lane],#180                    | Vd.4H -> result | A32/A64                 |
| float16x4_t vcmia, rot180_laneq_f16(float16x4_t r, float16x4_t a, float16x8_t b, const int lane)  | r -> Vd.4H<br>2 <= lane <= 3 | DUP Dm,Vm.D[1]<br>FCMLA Vd.4H,Vn.4H,Vm.H[lane % 2],#180 | Vd.4H -> result | A32/A64                 |
| float32x2_t vcmia, rot180_laneq_f32(float32x2_t r, float32x2_t a, float32x4_t b, const int lane)  | r -> Vd.2S<br>0 <= lane <= 1 | DUP Dm,Vm.D[1]<br>FCMLA Vd.2S,Vn.2S,Vm.2S,#180          | Vd.2S -> result | A32/A64                 |
| float16x8_t vcmiaq, rot180_f16(float16x8_t r, float16x8_t a, float16x8_t b)                       | r -> Vd.8H                   | FCMLA<br>Vd.8H,Vn.8H,Vm.8H,#180                         | Vd.8H -> result | A32/A64                 |
| float32x4_t vcmiaq, rot180_f32(float32x4_t r, float32x4_t a, float32x4_t b)                       | r -> Vd.4S                   | FCMLA Vd.4S,Vn.4S,Vm.4S,#180                            | Vd.4S -> result | A32/A64                 |
| float64x2_t vcmiaq, rot180_f64(float64x2_t r, float64x2_t a, float64x2_t b)                       | r -> Vd.2D                   | FCMLA<br>Vd.2D,Vn.2D,Vm.2D,#180                         | Vd.2D -> result | A64                     |
| float16x8_t vcmiaq, rot180_lane_f16(float16x8_t r, float16x8_t a, float16x4_t b, const int lane)  | r -> Vd.8H<br>0 <= lane <= 1 | FCMLA<br>Vd.8H,Vn.8H,Vm.H[lane],#180                    | Vd.8H -> result | A32/A64                 |
| float32x4_t vcmiaq, rot180_lane_f32(float32x4_t r, float32x4_t a, float32x2_t b, const int lane)  | r -> Vd.4S<br>lane == 0      | FCMLA<br>Vd.4S,Vn.4S,Vm.S[lane],#180                    | Vd.4S -> result | A32/A64                 |
| float16x8_t vcmiaq, rot180_laneq_f16(float16x8_t r, float16x8_t a, float16x8_t b, const int lane) | r -> Vd.8H<br>0 <= lane <= 3 | FCMLA<br>Vd.8H,Vn.8H,Vm.H[lane],#180                    | Vd.8H -> result | A32/A64                 |
| float32x4_t vcmiaq, rot180_laneq_f32(float32x4_t r, float32x4_t a, float32x4_t b, const int lane) | r -> Vd.4S<br>0 <= lane <= 1 | FCMLA<br>Vd.4S,Vn.4S,Vm.S[lane],#180                    | Vd.4S -> result | A32/A64                 |
| float16x4_t vcmia, rot270_f16(float16x4_t r, float16x4_t a, float16x4_t b)                        | r -> Vd.4H                   | FCMLA<br>Vd.4H,Vn.4H,Vm.4H,#270                         | Vd.4H -> result | A32/A64                 |
| float32x2_t vcmia, rot270_f32(float32x2_t r, float32x2_t a, float32x2_t b)                        | r -> Vd.2S                   | FCMLA Vd.2S,Vn.2S,Vm.2S,#270                            | Vd.2S -> result | A32/A64                 |
| float16x4_t vcmia, rot270_lane_f16(float16x4_t r, float16x4_t a, float16x4_t b, const int lane)   | r -> Vd.4H<br>0 <= lane <= 1 | FCMLA<br>Vd.4H,Vn.4H,Vm.H[lane],#270                    | Vd.4H -> result | A32/A64                 |

| Intrinsic                                                                                    | Argument Preparation        | Instruction                                            | Result         | Supported Architectures |
|----------------------------------------------------------------------------------------------|-----------------------------|--------------------------------------------------------|----------------|-------------------------|
| float32x2_t vmla, r0270 lane, f32float32x2_tr, float32x2_t a, float32x2_tb, const int lane)  | r -> Vd2S<br>lane == 0      | FCMLA Vd4S.Vn4S.Vn4S.Vn4S.#270                         | Vd2S -> result | A32/A64                 |
| float16x4_t vmla, r0270 lane, f16float16x4_tr, float16x4_t a, float16x4_tb, const int lane)  | r -> Vd4H<br>0 <- lane <- 1 | FCMLA Vd4H.Vn4H.Vn4H.[lane]#270                        | Vd4H -> result | A32/A64                 |
| float16x4_t vmla, r0270 lane, f16float16x4_tr, float16x4_t a, float16x4_tb, const int lane)  | r -> Vd4H<br>2 <- lane <- 3 | DUP Db.Vn.D1[1]<br>FCMLA Vd4H.Vn4H.Vn4H.[lane] %21#270 | Vd4H -> result | A32/A64                 |
| float32x2_t vmla, r0270 lane, f32float32x2_tr, float32x2_t a, float32x2_tb, const int lane)  | r -> Vd2S<br>0 <- lane <- 1 | DUP Db.Vn.D1[1]<br>FCMLA Vd2S.Vn2S.Vn2S.#270           | Vd2S -> result | A32/A64                 |
| float16x8_t vmlaq, r0270 f16float16x8_tr, float16x8_t a, float16x8_tb, const int lane)       | r -> Vd8H<br>0 <- lane <- 1 | FCMLA Vd8H.Vn8H.Vn8H.#270                              | Vd8H -> result | A32/A64                 |
| float32x4_t vmlaq, r0270 f32float32x4_tr, float32x4_t a, float32x4_tb, const int lane)       | r -> Vd4S<br>0 <- lane <- 1 | FCMLA Vd4S.Vn4S.Vn4S.#270                              | Vd4S -> result | A32/A64                 |
| float64x2_t vmlaq, r0270 r64float64x2_tr, float64x2_t a, float64x2_tb, const int lane)       | r -> Vd2D<br>0 <- lane <- 1 | FCMLA Vd2D.Vn2D.Vn2D.#270                              | Vd2D -> result | A64                     |
| float16x8_t vmlaq, r0270 lane, f16float16x8_tr, float16x8_t a, float16x8_tb, const int lane) | r -> Vd8H<br>0 <- lane <- 1 | FCMLA Vd8H.Vn8H.Vn8H.[lane]#270                        | Vd8H -> result | A32/A64                 |
| float32x4_t vmlaq, r0270 lane, f32float32x4_tr, float32x4_t a, float32x4_tb, const int lane) | r -> Vd4S<br>0 <- lane <- 1 | FCMLA Vd4S.Vn4S.Vn4S.[lane]#270                        | Vd4S -> result | A32/A64                 |
| float16x8_t vmlaq, r0270 lane, f16float16x8_tr, float16x8_t a, float16x8_tb, const int lane) | r -> Vd8H<br>0 <- lane <- 3 | FCMLA Vd8H.Vn8H.Vn8H.[lane]#270                        | Vd8H -> result | A32/A64                 |
| float32x4_t vmlaq, r0270 lane, f32float32x4_tr, float32x4_t a, float32x4_tb, const int lane) | r -> Vd4S<br>0 <- lane <- 1 | FCMLA Vd4S.Vn4S.Vn4S.[lane]#270                        | Vd4S -> result | A32/A64                 |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float32x2_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd2S.Vn2S                                     | Vd -> result   | A64                     |
| float32x4_t vmlsq, f32float32x4_t a, float32x4_t b, const int lane)                          | a -> Vn<br>0 <- Vn <- 1     | FRINT32Z Vd4S.Vn4S                                     | Vd -> result   | A64                     |
| float64x2_t vmlsq, f64float64x2_t a, float64x2_t b, const int lane)                          | a -> Dn<br>0 <- Dn <- 1     | FRINT32Z Dd0Dn                                         | Dd -> result   | A64                     |
| float32x2_t vmlsq, f32float32x2_t a, float                                                   |                             |                                                        |                |                         |

| Intrinsic                                                                             | Argument Preparation                                        | Instruction                                | Result          | Supported Architectures |
|---------------------------------------------------------------------------------------|-------------------------------------------------------------|--------------------------------------------|-----------------|-------------------------|
| int32x4_t vsubdqt_lane_s32int32x4_t, int8x8_1.t, uint8x16_t, b, const int lane)       | r -> Vd2S<br>a -> Vn,8B<br>b -> Vm,4B<br>0 -> lane <-<br>3  | SUDOT Vd2S.Vn,8B.Vm,4B[lane]               | Vd,2S -> result | A64                     |
| int32x4_t vsubdqt_s32int32x4_t, uint8x16_1.t, int8x16_t, b)                           | r -> Vd4S<br>a -> Vn,16B<br>b -> Vm,4B<br>0 -> lane <-<br>1 | USDOT Vd4S.Vn,16B.Vm,16B                   | Vd,4S -> result | A64                     |
| int32x4_t vsubdqt_lane_s32int32x4_t, uint8x16_1.t, int8x8_1.t, b, const int lane)     | r -> Vd4S<br>a -> Vn,16B<br>b -> Vm,4B<br>0 -> lane <-<br>1 | SUDOT Vd4S.Vn,16B.Vm,4B[lane]              | Vd,4S -> result | A32/A64                 |
| int32x4_t vsubdqt_lane_s32int32x4_t, int8x16_1.t, uint8x16_1.t, b, const int lane)    | r -> Vd4S<br>a -> Vn,16B<br>b -> Vm,4B<br>0 -> lane <-<br>1 | SUDOT Vd4S.Vn,16B.Vm,4B[lane]              | Vd,4S -> result | A32/A64                 |
| int32x4_t vsubdqt_lane_s32int32x4_t, uint8x16_1.t, a, int8x16_1.t, b, const int lane) | r -> Vd4S<br>a -> Vn,16B<br>b -> Vm,4B<br>0 -> lane <-<br>3 | USDOT Vd4S.Vn,16B.Vm,4B[lane]              | Vd,4S -> result | A64                     |
| int32x4_t vsubdqt_lane_s32int32x4_t, int8x16_1.t, a, uint8x16_1.t, b, const int lane) | r -> Vd4S<br>a -> Vn,16B<br>b -> Vm,4B<br>0 -> lane <-<br>3 | SUDOT Vd4S.Vn,16B.Vm,4B[lane]              | Vd,4S -> result | A64                     |
| bfloat16x4_t vrecare_bf16(uint64_t a)                                                 | a -> Xn                                                     | INS Vd(D)[0],Xn                            | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vdup_n_bf16(float16_t v, vrec)                                           | value -> m                                                  | DUP Vd,4H,m                                | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vdup_n_bf16(float16_t v, vrec)                                           | value -> m                                                  | DUP Vd,8H,m                                | Vd,8H -> result | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,4H<br>0 -> lane <-<br>3                           | DUP Vd,4H,[VnH][lane]                      | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,4H<br>0 -> lane <-<br>3                           | DUP Vd,4H,[VnH][lane]                      | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,8H<br>0 -> lane <-<br>7                           | DUP Vd,4H,[VnH][lane]                      | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,8H<br>0 -> lane <-<br>7                           | DUP Vd,8H,[VnH][lane]                      | Vd,8H -> result | A32/A64                 |
| bfloat16x4_t vcombine_bf16(float16x4_t v, low, bfloat16x4_t, high)                    | low -> Vn,4H<br>high -> Vm,4H                               | DUP Vd,1D,[VnD][0]<br>INS Vd(D)[1],Vm,D[0] | Vd,8H -> result | A32/A64                 |
| bfloat16x4_t vget_high_bf16(float16x4_t v, lane)                                      | a -> Vn,8H                                                  | DUP Vd,1D,[VnD][1]                         | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vget_low_bf16(float16x4_t v, lane)                                       | a -> Vn,8H<br>v -> Vn,4H<br>0 -> lane <-<br>3               | DUP Vd,1D,[VnD][0]                         | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vget_lane_bf16(float16x4_t v, const int lane)                            | v -> Vn,8H<br>0 -> lane <-<br>7                             | DUP Vd,4H,[VnH][lane]                      | Vd -> result    | A32/A64                 |
| bfloat16x4_t vget_lane_bf16(float16x4_t v, const int lane)                            | v -> Vn,8H<br>0 -> lane <-<br>7                             | DUP Vd,8H,[VnH][lane]                      | Vd -> result    | A32/A64                 |
| bfloat16x4_t vget_lane_bf16(float16x4_t v, const int lane)                            | a -> VnH<br>v -> Vd,4H<br>0 -> lane <-<br>3                 | INS Vd(H)[lane],VnH[0]                     | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vget_lane_bf16(float16x4_t v, const int lane)                            | a -> VnH<br>v -> Vd,8H<br>0 -> lane <-<br>7                 | INS Vd(H)[lane],VnH[0]                     | Vd,8H -> result | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,4H<br>0 -> lane <-<br>3                           | DUP Vd,4H,[VnH][lane]                      | Vd -> result    | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,8H<br>0 -> lane <-<br>7                           | DUP Vd,4H,[VnH][lane]                      | Vd -> result    | A32/A64                 |
| bfloat16x4_t vdup_lane_bf16(float16x4_t v, vrec, const int lane)                      | vec -> Vn,8H<br>0 -> lane <-<br>7                           | DUP Vd,8H,[VnH][lane]                      | Vd -> result    | A32/A64                 |
| bfloat16x4_t vld1_bf16(float16x4_t const * ptr)                                       | ptr -> Xn                                                   | LD1 Vd,4H,[Xn]                             | Vd,4H -> result | A32/A64                 |
| bfloat16x4_t vld1q_bf16(float16x4_t const * ptr)                                      | ptr -> Xn                                                   | LD1 Vd,8H,[Xn]                             | Vd,8H -> result | A32/A64                 |

| Intrinsic                                                                              | Argument Preparation                        | Instruction               | Result                                                                                                      | Supported Architectures |
|----------------------------------------------------------------------------------------|---------------------------------------------|---------------------------|-------------------------------------------------------------------------------------------------------------|-------------------------|
| bfloat16x4_t vld1_lane_bf16(bfloat16_t const * ptr, bfloat16x4_t src, const int lane)  | ptr -> Xn<br>src -> Vt.4H<br>0 <= lane <= 3 | LD1 [Vt.H][lane][Xn]      | Vt.4H -> result                                                                                             | A32/A64                 |
| bfloat16x8_t vld1q_lane_bf16(bfloat16_t const * ptr, bfloat16x8_t src, const int lane) | ptr -> Xn<br>src -> Vt.8H<br>0 <= lane <= 7 | LD1 [Vt.H][lane][Xn]      | Vt.8H -> result                                                                                             | A32/A64                 |
| bfloat16x4_t vld1_dup_bf16(bfloat16_t const * ptr)                                     | ptr -> Xn                                   | LD1R [Vt.4H][Xn]          | Vt.4H -> result                                                                                             | A32/A64                 |
| bfloat16x8_t vld1q_dup_bf16(bfloat16_t const * ptr)                                    | ptr -> Xn                                   | LD1R [Vt.8H][Xn]          | Vt.8H -> result                                                                                             | A32/A64                 |
| void vst1_bf16(bfloat16_t * ptr, bfloat16x4_t val)                                     | ptr -> Xn<br>val -> Vt.4H                   | ST1 [Vt.4H][Xn]           | void -> result                                                                                              | A32/A64                 |
| void vst1q_bf16(bfloat16_t * ptr, bfloat16x8_t val)                                    | ptr -> Xn<br>val -> Vt.8H                   | ST1 [Vt.8H][Xn]           | void -> result                                                                                              | A32/A64                 |
| void vst1_lane_bf16(bfloat16_t * ptr, bfloat16x4_t val, const int lane)                | ptr -> Xn<br>val -> Vt.4H<br>0 <= lane <= 3 | ST1 [Vt.H][lane][Xn]      | void -> result                                                                                              | A32/A64                 |
| void vst1q_lane_bf16(bfloat16_t * ptr, bfloat16x8_t val, const int lane)               | ptr -> Xn<br>val -> Vt.8H<br>0 <= lane <= 7 | ST1 [Vt.H][lane][Xn]      | void -> result                                                                                              | A32/A64                 |
| bfloat16x4x2_t vld2_bf16(bfloat16_t const * ptr)                                       | ptr -> Xn                                   | LD2 [Vt.4H - Vt2.4H][Xn]  | Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0]                                                         | A32/A64                 |
| bfloat16x8x2_t vld2q_bf16(bfloat16_t const * ptr)                                      | ptr -> Xn                                   | LD2 [Vt.8H - Vt2.8H][Xn]  | Vt2.8H -> result[val][1]<br>Vt.8H -> result[val][0]                                                         | A32/A64                 |
| bfloat16x4x3_t vld3_bf16(bfloat16_t const * ptr)                                       | ptr -> Xn                                   | LD3 [Vt.4H - Vt3.4H][Xn]  | Vt3.4H -> result[val][2]<br>Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0]                             | A32/A64                 |
| bfloat16x8x3_t vld3q_bf16(bfloat16_t const * ptr)                                      | ptr -> Xn                                   | LD3 [Vt.8H - Vt3.8H][Xn]  | Vt3.8H -> result[val][2]<br>Vt2.8H -> result[val][1]<br>Vt.8H -> result[val][0]                             | A32/A64                 |
| bfloat16x4x4_t vld4_bf16(bfloat16_t const * ptr)                                       | ptr -> Xn                                   | LD4 [Vt.4H - Vt4.4H][Xn]  | Vt4.4H -> result[val][3]<br>Vt3.4H -> result[val][2]<br>Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0] | A32/A64                 |
| bfloat16x8x4_t vld4q_bf16(bfloat16_t const * ptr)                                      | ptr -> Xn                                   | LD4 [Vt.8H - Vt4.8H][Xn]  | Vt4.8H -> result[val][3]<br>Vt3.8H -> result[val][2]<br>Vt2.8H -> result[val][1]<br>Vt.8H -> result[val][0] | A32/A64                 |
| bfloat16x4x2_t vld2_dup_bf16(bfloat16_t const * ptr)                                   | ptr -> Xn                                   | LD2R [Vt.4H - Vt2.4H][Xn] | Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0]                                                         | A32/A64                 |
| bfloat16x8x2_t vld2q_dup_bf16(bfloat16_t const * ptr)                                  | ptr -> Xn                                   | LD2R [Vt.8H - Vt2.8H][Xn] | Vt2.8H -> result[val][1]<br>Vt.8H -> result[val][0]                                                         | A32/A64                 |
| bfloat16x4x3_t vld3_dup_bf16(bfloat16_t const * ptr)                                   | ptr -> Xn                                   | LD3R [Vt.4H - Vt3.4H][Xn] | Vt3.4H -> result[val][2]<br>Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0]                             | A32/A64                 |

| Intrinsic                                                                                 | Argument Preparation                                                                                         | Instruction                  | Result                                                                                                      | Supported Architectures |
|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|------------------------------|-------------------------------------------------------------------------------------------------------------|-------------------------|
| bfloat16x8x3_t vld3q_dup_bf16(bfloat16_t const * ptr)                                     | ptr -> Xn                                                                                                    | LD3R [Vt.8H - Vt3.8H][Xn]    | Vt3.8H -> result[val][2]<br>Vt2.8H -> result[val][1]<br>Vt.8H -> result[val][0]                             | A32/A64                 |
| bfloat16x4x4_t vld4_dup_bf16(bfloat16_t const * ptr)                                      | ptr -> Xn                                                                                                    | LD4R [Vt.4H - Vt4.4H][Xn]    | Vt4.4H -> result[val][3]<br>Vt3.4H -> result[val][2]<br>Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0] | A32/A64                 |
| bfloat16x8x4_t vld4q_dup_bf16(bfloat16_t const * ptr)                                     | ptr -> Xn                                                                                                    | LD4R [Vt.8H - Vt4.8H][Xn]    | Vt4.8H -> result[val][3]<br>Vt3.8H -> result[val][2]<br>Vt2.8H -> result[val][1]<br>Vt.8H -> result[val][0] | A32/A64                 |
| void vst2_bf16(bfloat16_t * ptr, bfloat16x4x2_t val)                                      | ptr -> Xn<br>val[val][1] -> Vt2.4H<br>val[val][0] -> Vt.4H                                                   | ST2 [Vt.4H - Vt2.4H][Xn]     | void -> result                                                                                              | A32/A64                 |
| void vst2q_bf16(bfloat16_t * ptr, bfloat16x8x2_t val)                                     | ptr -> Xn<br>val[val][1] -> Vt2.8H<br>val[val][0] -> Vt.8H                                                   | ST2 [Vt.8H - Vt2.8H][Xn]     | void -> result                                                                                              | A32/A64                 |
| void vst3_bf16(bfloat16_t * ptr, bfloat16x4x3_t val)                                      | ptr -> Xn<br>val[val][2] -> Vt3.4H<br>val[val][1] -> Vt2.4H<br>val[val][0] -> Vt.4H                          | ST3 [Vt.4H - Vt3.4H][Xn]     | void -> result                                                                                              | A32/A64                 |
| void vst3q_bf16(bfloat16_t * ptr, bfloat16x8x3_t val)                                     | ptr -> Xn<br>val[val][2] -> Vt3.8H<br>val[val][1] -> Vt2.8H<br>val[val][0] -> Vt.8H                          | ST3 [Vt.8H - Vt3.8H][Xn]     | void -> result                                                                                              | A32/A64                 |
| void vst4_bf16(bfloat16_t * ptr, bfloat16x4x4_t val)                                      | ptr -> Xn<br>val[val][3] -> Vt4.4H<br>val[val][2] -> Vt3.4H<br>val[val][1] -> Vt2.4H<br>val[val][0] -> Vt.4H | ST4 [Vt.4H - Vt4.4H][Xn]     | void -> result                                                                                              | A32/A64                 |
| void vst4q_bf16(bfloat16_t * ptr, bfloat16x8x4_t val)                                     | ptr -> Xn<br>val[val][3] -> Vt4.8H<br>val[val][2] -> Vt3.8H<br>val[val][1] -> Vt2.8H<br>val[val][0] -> Vt.8H | ST4 [Vt.8H - Vt4.8H][Xn]     | void -> result                                                                                              | A32/A64                 |
| bfloat16x4x2_t vld2_lane_bf16(bfloat16_t const * ptr, bfloat16x4x2_t src, const int lane) | ptr -> Xn<br>src[val][1] -> Vt2.4H<br>src[val][0] -> Vt.4H<br>0 <= lane <= 3                                 | LD2 [Vt.h - Vt2.h][lane][Xn] | Vt2.4H -> result[val][1]<br>Vt.4H -> result[val][0]                                                         | A32/A64                 |

| Intrinsic                                                                                  | Argument Preparation                                                                                                       | Instruction                    | Result                                                                                                  | Supported Architectures |
|--------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|--------------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| bfloat16x8x2_t vld2q_lane_bf16(bfloat16_t const * ptr, bfloat16x8x2_t src, const int lane) | ptr -> Xn<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7                                                 | LD2 [Vt.h - Vt2.h][lane], [Xn] | Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0]                                                       | A32/A64                 |
| bfloat16x4x3_t vld3_lane_bf16(bfloat16_t const * ptr, bfloat16x4x3_t src, const int lane)  | ptr -> Xn<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3                         | LD3 [Vt.h - Vt3.h][lane], [Xn] | Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0]                            | A32/A64                 |
| bfloat16x8x3_t vld3q_lane_bf16(bfloat16_t const * ptr, bfloat16x8x3_t src, const int lane) | ptr -> Xn<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7                         | LD3 [Vt.h - Vt3.h][lane], [Xn] | Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0]                            | A32/A64                 |
| bfloat16x4x4_t vld4_lane_bf16(bfloat16_t const * ptr, bfloat16x4x4_t src, const int lane)  | ptr -> Xn<br>src.val[3] -> Vt4.4H<br>src.val[2] -> Vt3.4H<br>src.val[1] -> Vt2.4H<br>src.val[0] -> Vt.4H<br>0 <= lane <= 3 | LD4 [Vt.h - Vt4.h][lane], [Xn] | Vt4.4H -> result.val[3]<br>Vt3.4H -> result.val[2]<br>Vt2.4H -> result.val[1]<br>Vt.4H -> result.val[0] | A32/A64                 |
| bfloat16x8x4_t vld4q_lane_bf16(bfloat16_t const * ptr, bfloat16x8x4_t src, const int lane) | ptr -> Xn<br>src.val[3] -> Vt4.8H<br>src.val[2] -> Vt3.8H<br>src.val[1] -> Vt2.8H<br>src.val[0] -> Vt.8H<br>0 <= lane <= 7 | LD4 [Vt.h - Vt4.h][lane], [Xn] | Vt4.8H -> result.val[3]<br>Vt3.8H -> result.val[2]<br>Vt2.8H -> result.val[1]<br>Vt.8H -> result.val[0] | A32/A64                 |
| void vst2_lane_bf16(bfloat16_t * ptr, bfloat16x4x2_t val, const int lane)                  | ptr -> Xn<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H<br>0 <= lane <= 3                                                 | ST2 [Vt.h - Vt2.h][lane], [Xn] | void -> result                                                                                          | A32/A64                 |
| void vst2q_lane_bf16(bfloat16_t * ptr, bfloat16x8x2_t val, const int lane)                 | ptr -> Xn<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7                                                 | ST2 [Vt.h - Vt2.h][lane], [Xn] | void -> result                                                                                          | A32/A64                 |
| void vst3_lane_bf16(bfloat16_t * ptr, bfloat16x4x3_t val, const int lane)                  | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H<br>0 <= lane <= 3                         | ST3 [Vt.h - Vt3.h][lane], [Xn] | void -> result                                                                                          | A32/A64                 |

| Intrinsic                                                                 | Argument Preparation                                                                                                       | Instruction                 | Result         | Supported Architectures |
|---------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|-----------------------------|----------------|-------------------------|
| void vst3q_lane_bf16(bfloat16_t* ptr, bfloat16x8x3_t val, const int lane) | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7                         | ST3[Vt.h - Vt3.h][lane][Xn] | void -> result | A32/A64                 |
| void vst4_lane_bf16(bfloat16_t* ptr, bfloat16x4x4_t val, const int lane)  | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H<br>0 <= lane <= 3 | ST4[Vt.h - Vt4.h][lane][Xn] | void -> result | A32/A64                 |
| void vst4q_lane_bf16(bfloat16_t* ptr, bfloat16x8x4_t val, const int lane) | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H<br>0 <= lane <= 7 | ST4[Vt.h - Vt4.h][lane][Xn] | void -> result | A32/A64                 |
| void vst1_bf16_x2(bfloat16_t* ptr, bfloat16x4x2_t val)                    | ptr -> Xn<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H                                                                   | ST1[Vt.4H - Vt2.4H][Xn]     | void -> result | A32/A64                 |
| void vst1q_bf16_x2(bfloat16_t* ptr, bfloat16x8x2_t val)                   | ptr -> Xn<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H                                                                   | ST1[Vt.8H - Vt2.8H][Xn]     | void -> result | A32/A64                 |
| void vst1_bf16_x3(bfloat16_t* ptr, bfloat16x4x3_t val)                    | ptr -> Xn<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H                                           | ST1[Vt.4H - Vt3.4H][Xn]     | void -> result | A32/A64                 |
| void vst1q_bf16_x3(bfloat16_t* ptr, bfloat16x8x3_t val)                   | ptr -> Xn<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H                                           | ST1[Vt.8H - Vt3.8H][Xn]     | void -> result | A32/A64                 |
| void vst1_bf16_x4(bfloat16_t* ptr, bfloat16x4x4_t val)                    | ptr -> Xn<br>val.val[3] -> Vt4.4H<br>val.val[2] -> Vt3.4H<br>val.val[1] -> Vt2.4H<br>val.val[0] -> Vt.4H                   | ST1[Vt.4H - Vt4.4H][Xn]     | void -> result | A32/A64                 |
| void vst1q_bf16_x4(bfloat16_t* ptr, bfloat16x8x4_t val)                   | ptr -> Xn<br>val.val[3] -> Vt4.8H<br>val.val[2] -> Vt3.8H<br>val.val[1] -> Vt2.8H<br>val.val[0] -> Vt.8H                   | ST1[Vt.8H - Vt4.8H][Xn]     | void -> result | A32/A64                 |

| Intrinsic                                            | Argument Preparation | Instruction                | Result                                                                                                  | Supported Architectures |
|------------------------------------------------------|----------------------|----------------------------|---------------------------------------------------------------------------------------------------------|-------------------------|
| bfloat16x4x2_t vld1_bf16_x2(bfloat16_t const * ptr)  | ptr -> Xn            | LD1 [Vt.4H - Vt2.4H], [Xn] | Vt2.4H -> result[val[1]<br>Vt.4H -> result[val[0]                                                       | A32/A64                 |
| bfloat16x8x2_t vld1q_bf16_x2(bfloat16_t const * ptr) | ptr -> Xn            | LD1 [Vt.8H - Vt2.8H], [Xn] | Vt2.8H -> result[val[1]<br>Vt.8H -> result[val[0]                                                       | A32/A64                 |
| bfloat16x4x3_t vld1_bf16_x3(bfloat16_t const * ptr)  | ptr -> Xn            | LD1 [Vt.4H - Vt3.4H], [Xn] | Vt3.4H -> result[val[2]<br>Vt2.4H -> result[val[1]<br>Vt.4H -> result[val[0]                            | v7/A32/A64              |
| bfloat16x8x3_t vld1q_bf16_x3(bfloat16_t const * ptr) | ptr -> Xn            | LD1 [Vt.8H - Vt3.8H], [Xn] | Vt3.8H -> result[val[2]<br>Vt2.8H -> result[val[1]<br>Vt.8H -> result[val[0]                            | v7/A32/A64              |
| bfloat16x4x4_t vld1_bf16_x4(bfloat16_t const * ptr)  | ptr -> Xn            | LD1 [Vt.4H - Vt4.4H], [Xn] | Vt4.4H -> result[val[3]<br>Vt3.4H -> result[val[2]<br>Vt2.4H -> result[val[1]<br>Vt.4H -> result[val[0] | A32/A64                 |
| bfloat16x8x4_t vld1q_bf16_x4(bfloat16_t const * ptr) | ptr -> Xn            | LD1 [Vt.8H - Vt4.8H], [Xn] | Vt4.8H -> result[val[3]<br>Vt3.8H -> result[val[2]<br>Vt2.8H -> result[val[1]<br>Vt.8H -> result[val[0] | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_s8(int8x8_t a)        | a -> Vd.8B           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_s16(int16x4_t a)      | a -> Vd.4H           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_s32(int32x2_t a)      | a -> Vd.2S           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_f32(float32x2_t a)    | a -> Vd.2S           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_u8(uint8x8_t a)       | a -> Vd.8B           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_u16(uint16x4_t a)     | a -> Vd.4H           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_u32(uint32x2_t a)     | a -> Vd.2S           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_p8(poly8x8_t a)       | a -> Vd.8B           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_p16(poly16x4_t a)     | a -> Vd.4H           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_u64(uint64x1_t a)     | a -> Vd.1D           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_s64(int64x1_t a)      | a -> Vd.1D           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_s8(int8x8_t a)       | a -> Vd.16B          | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_s16(int16x4_t a)     | a -> Vd.8H           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_s32(int32x2_t a)     | a -> Vd.4S           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_f32(float32x4_t a)   | a -> Vd.4S           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_u8(uint8x8_t a)      | a -> Vd.16B          | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_u16(uint16x4_t a)    | a -> Vd.8H           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_u32(uint32x2_t a)    | a -> Vd.4S           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_p8(poly8x8_t a)      | a -> Vd.16B          | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_p16(poly16x4_t a)    | a -> Vd.8H           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_u64(uint64x2_t a)    | a -> Vd.2D           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_s64(int64x2_t a)     | a -> Vd.2D           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x4_t vreinterpret_bf16_f64(float64x1_t a)    | a -> Vd.1D           | NOP                        | Vd.4H -> result                                                                                         | A64                     |
| bfloat16x8_t vreinterpretq_bf16_f64(float64x2_t a)   | a -> Vd.2D           | NOP                        | Vd.8H -> result                                                                                         | A64                     |
| bfloat16x4_t vreinterpret_bf16_p64(poly64x1_t a)     | a -> Vd.1D           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_p64(poly64x2_t a)    | a -> Vd.2D           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| bfloat16x8_t vreinterpretq_bf16_p128(poly128_t a)    | a -> Vd.1Q           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| int8x8_t vreinterpret_s8_bf16(bfloat16x4_t a)        | a -> Vd.4H           | NOP                        | Vd.8H -> result                                                                                         | A32/A64                 |
| int16x4_t vreinterpret_s16_bf16(bfloat16x4_t a)      | a -> Vd.4H           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| int32x2_t vreinterpret_s32_bf16(bfloat16x4_t a)      | a -> Vd.4H           | NOP                        | Vd.2S -> result                                                                                         | A32/A64                 |
| float32x2_t vreinterpret_f32_bf16(bfloat16x4_t a)    | a -> Vd.4H           | NOP                        | Vd.2S -> result                                                                                         | A32/A64                 |
| uint8x8_t vreinterpret_u8_bf16(bfloat16x4_t a)       | a -> Vd.4H           | NOP                        | Vd.8B -> result                                                                                         | A32/A64                 |
| uint16x4_t vreinterpret_u16_bf16(bfloat16x4_t a)     | a -> Vd.4H           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |
| uint32x2_t vreinterpret_u32_bf16(bfloat16x4_t a)     | a -> Vd.4H           | NOP                        | Vd.2S -> result                                                                                         | A32/A64                 |
| poly8x8_t vreinterpret_p8_bf16(bfloat16x4_t a)       | a -> Vd.4H           | NOP                        | Vd.8B -> result                                                                                         | A32/A64                 |
| poly16x4_t vreinterpret_p16_bf16(bfloat16x4_t a)     | a -> Vd.4H           | NOP                        | Vd.4H -> result                                                                                         | A32/A64                 |

| Intrinsic                                                                                        | Argument Preparation                                             | Instruction                   | Result         | Supported Architectures |
|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------|-------------------------------|----------------|-------------------------|
| uint64x1_t reinterpret_u64_f16(bfloat16x4_t a)                                                   | a->Vd.4H                                                         | NOP                           | Vd.1D->result  | A32/A64                 |
| int64x1_t reinterpret_s64_f16(bfloat16x4_t a)                                                    | a->Vd.4H                                                         | NOP                           | Vd.1D->result  | A32/A64                 |
| float64x1_t reinterpret_f64_f16(bfloat16x4_t a)                                                  | a->Vd.4H                                                         | NOP                           | Vd.1D->result  | A64                     |
| poly64x1_t reinterpret_p64_f16(bfloat16x4_t a)                                                   | a->Vd.4H                                                         | NOP                           | Vd.1D->result  | A32/A64                 |
| int8x16_t reinterpretq_s8_f16(bfloat16x8_t a)                                                    | a->Vd.8H                                                         | NOP                           | Vd.16B->result | A32/A64                 |
| int16x8_t reinterpretq_s16_f16(bfloat16x8_t a)                                                   | a->Vd.8H                                                         | NOP                           | Vd.8H->result  | A32/A64                 |
| int32x4_t reinterpretq_s32_f16(bfloat16x8_t a)                                                   | a->Vd.8H                                                         | NOP                           | Vd.4S->result  | A32/A64                 |
| float32x4_t reinterpretq_f32_f16(bfloat16x8_t a)                                                 | a->Vd.8H                                                         | NOP                           | Vd.4S->result  | A32/A64                 |
| uint8x16_t reinterpretq_u8_f16(bfloat16x8_t a)                                                   | a->Vd.8H                                                         | NOP                           | Vd.16B->result | A32/A64                 |
| uint16x8_t reinterpretq_u16_f16(bfloat16x8_t a)                                                  | a->Vd.8H                                                         | NOP                           | Vd.8H->result  | A32/A64                 |
| uint32x4_t reinterpretq_u32_f16(bfloat16x8_t a)                                                  | a->Vd.8H                                                         | NOP                           | Vd.4S->result  | A32/A64                 |
| poly8x16_t reinterpretq_p8_f16(bfloat16x8_t a)                                                   | a->Vd.8H                                                         | NOP                           | Vd.16B->result | A32/A64                 |
| poly16x8_t reinterpretq_p16_f16(bfloat16x8_t a)                                                  | a->Vd.8H                                                         | NOP                           | Vd.8H->result  | A32/A64                 |
| uint64x2_t reinterpretq_u64_f16(bfloat16x8_t a)                                                  | a->Vd.8H                                                         | NOP                           | Vd.2D->result  | A32/A64                 |
| int64x2_t reinterpretq_s64_f16(bfloat16x8_t a)                                                   | a->Vd.8H                                                         | NOP                           | Vd.2D->result  | A32/A64                 |
| float64x2_t reinterpretq_f64_f16(bfloat16x8_t a)                                                 | a->Vd.8H                                                         | NOP                           | Vd.2D->result  | A64                     |
| poly64x2_t reinterpretq_p64_f16(bfloat16x8_t a)                                                  | a->Vd.8H                                                         | NOP                           | Vd.2D->result  | A32/A64                 |
| poly128_t reinterpretq_p128_f16(bfloat16x8_t a)                                                  | a->Vd.8H                                                         | NOP                           | Vd.1Q->result  | A32/A64                 |
| float32x4_t vcvq_f32_f16(bfloat16x4_t a)                                                         | a->Vn.8H                                                         | SHLL Vd.4S,Vn.8H,#16          | Vd.4S->result  | A32/A64                 |
| float32x4_t vcvq_low_f32_f16(bfloat16x8_t a)                                                     | a->Vn.8H                                                         | SHLL Vd.4S,Vn.8H,#16          | Vd.4S->result  | A32/A64                 |
| float32x4_t vcvq_high_f32_f16(bfloat16x8_t a)                                                    | a->Vn.8H                                                         | SHLL Vd.4S,Vn.8H,#16          | Vd.4S->result  | A32/A64                 |
| bfloat16x4_t vcvq_f16_f32(bfloat32x4_t a)                                                        | a->Vn.4S                                                         | BFCVTN Vd.4H,Vn.4S            | Vd.4H->result  | A32/A64                 |
| bfloat16x8_t vcvq_high_f16_f32(bfloat32x4_t a)                                                   | a->Vn.4S                                                         | BFCVTN Vd.8H,Vn.4S            | Vd.8H->result  | A32/A64                 |
| bfloat16x8_t vcvq_high_f16_f32(bfloat16x8_t a)                                                   | inactive->Vd.8H                                                  | BFCVTN2 Vd.8H,Vn.4S           | Vd.8H->result  | A32/A64                 |
| bfloat16x8_t vcvq_low_f16_f32(bfloat32x4_t a)                                                    | inactive->Vd.8H                                                  | BFCVTN2 Vd.8H,Vn.4S           | Vd.8H->result  | A32/A64                 |
| bfloat16_t vcvth_f16_f32(float32_t a)                                                            | a->Sn                                                            | BFCVT Hd,Sn                   | Hd->result     | A32/A64                 |
| float32_t vcvth_f32_f16(bfloat16_t a)                                                            | a->Hn                                                            | SHL Dd,Dn,#16                 | Dd->result     | A32/A64                 |
| bfloat16x4_t vcopy_lane_bf16(bfloat16x4_t a, const int lane1, bfloat16x4_t b, const int lane2)   | a->Vd.4H<br>0 <= lane1<br><= 3<br>b->Vn.4H<br>0 <= lane2<br><= 3 | INS Vd.H[lane1],Vn.H[lane2]   | Vd.4H->result  | A64                     |
| bfloat16x8_t vcopyq_lane_bf16(bfloat16x8_t a, const int lane1, bfloat16x8_t b, const int lane2)  | a->Vd.8H<br>0 <= lane1<br><= 7<br>b->Vn.8H<br>0 <= lane2<br><= 7 | INS Vd.H[lane1],Vn.H[lane2]   | Vd.8H->result  | A64                     |
| bfloat16x4_t vcopy_laneq_bf16(bfloat16x4_t a, const int lane1, bfloat16x8_t b, const int lane2)  | a->Vd.4H<br>0 <= lane1<br><= 3<br>b->Vn.8H<br>0 <= lane2<br><= 7 | INS Vd.H[lane1],Vn.H[lane2]   | Vd.4H->result  | A64                     |
| bfloat16x8_t vcopyq_laneq_bf16(bfloat16x8_t a, const int lane1, bfloat16x8_t b, const int lane2) | a->Vd.8H<br>0 <= lane1<br><= 7<br>b->Vn.8H<br>0 <= lane2<br><= 7 | INS Vd.H[lane1],Vn.H[lane2]   | Vd.8H->result  | A64                     |
| float32x2_t vbfdot_f32(float32x2_t r, bfloat16x4_t a, bfloat16x4_t b)                            | r->Vd.2S<br>a->Vn.4H<br>b->Vm.4H                                 | BFDOT Vd.2S,Vn.4H,Vm.4H       | Vd.2S->result  | A32/A64                 |
| float32x4_t vbfdotq_f32(float32x4_t r, bfloat16x8_t a, bfloat16x8_t b)                           | r->Vd.4S<br>a->Vn.8H<br>b->Vm.8H                                 | BFDOT Vd.4S,Vn.8H,Vm.8H       | Vd.4S->result  | A32/A64                 |
| float32x2_t vbfdot_lane_f32(float32x2_t r, bfloat16x4_t a, bfloat16x4_t b, const int lane)       | r->Vd.2S<br>a->Vn.4H<br>b->Vm.4H<br>0 <= lane <= 1               | BFDOT Vd.2S,Vn.4H,Vm.2H[lane] | Vd.2S->result  | A32/A64                 |
| float32x4_t vbfdotq_laneq_f32(float32x4_t r, bfloat16x8_t a, bfloat16x8_t b, const int lane)     | r->Vd.4S<br>a->Vn.8H<br>b->Vm.8H<br>0 <= lane <= 3               | BFDOT Vd.4S,Vn.8H,Vm.2H[lane] | Vd.4S->result  | A32/A64                 |

| Intrinsic                                                                                   | Argument Preparation                                        | Instruction                     | Result          | Supported Architectures |
|---------------------------------------------------------------------------------------------|-------------------------------------------------------------|---------------------------------|-----------------|-------------------------|
| float32x2_t vfloatq_lane_f32(float32x2_t r, float16x4_t a, float16x8_t b, const int lane)   | r -> Vd,2S<br>a -> Vn,4H<br>b -> Vm,8H<br>0 -> lane <-<br>3 | BFDOT Vd,2S,Vn,4H,Vm,2H[lane]   | Vd,2S -> result | A32/A64                 |
| float32x4_t vfloatq_lane_f32(float32x4_t r, float16x8_t a, float16x16_t b, const int lane)  | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,4H<br>0 -> lane <-<br>1 | BFDOT Vd,4S,Vn,8H,Vm,2H[lane]   | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlaq_f32(float32x4_t r, float16x8_t a, float16x16_t b)                       | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,8H                      | BFMMLA Vd,4S,Vn,8H,Vm,8H        | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlabq_f32(float32x4_t r, float16x8_t a, float16x16_t b)                      | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,8H                      | BFMMLAB Vd,4S,Vn,8H,Vm,8H       | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlatq_f32(float32x4_t r, float16x8_t a, float16x16_t b)                      | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,8H                      | BFMMLAT Vd,4S,Vn,8H,Vm,8H       | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlabq_lane_f32(float32x4_t r, float16x8_t a, float16x16_t b, const int lane) | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,4H<br>0 -> lane <-<br>3 | BFMMLAB Vd,4S,Vn,8H,Vm,4H[lane] | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlabq_lane_f32(float32x4_t r, float16x8_t a, float16x16_t b, const int lane) | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,8H<br>0 -> lane <-<br>7 | BFMMLAB Vd,4S,Vn,8H,Vm,8H[lane] | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlatq_lane_f32(float32x4_t r, float16x8_t a, float16x16_t b, const int lane) | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,4H<br>0 -> lane <-<br>3 | BFMMLAT Vd,4S,Vn,8H,Vm,4H[lane] | Vd,4S -> result | A32/A64                 |
| float32x4_t vfmmlatq_lane_f32(float32x4_t r, float16x8_t a, float16x16_t b, const int lane) | r -> Vd,4S<br>a -> Vn,8H<br>b -> Vm,8H<br>0 -> lane <-<br>7 | BFMMLAT Vd,4S,Vn,8H,Vm,8H[lane] | Vd,4S -> result | A32/A64                 |