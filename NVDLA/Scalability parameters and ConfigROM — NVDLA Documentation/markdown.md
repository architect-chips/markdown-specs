

# Scalability parameters and ConfigROM

## Scalability parameters

Note that the current source code has only been tested for the nv\_small configuration, and while the nv\_small configuration passes many tests, additional coverage is necessary to get it to tapeout quality.

| Scalability Parameter                                                              | Description                                                                                                         | INT8 Large Config(nv_large ) | INT8 Small Config(nv_small ) |
|------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|------------------------------|------------------------------|
| NVDLA_FEATURE_D<br>ATA_TYPE_BINARY<br>/INT4/INT8/INT16<br>INT32/FP16/FP32<br>/FP64 | Identify the data type of input feature data                                                                        | INT8                         | INT8                         |
| NVDLA_WEIGHT_D<br>ATA_TYPE_BINARY<br>/INT4/INT8/INT16<br>INT32/FP16/FP32<br>/FP64  | Identify the data type of input weight data                                                                         | INT8                         | INT8                         |
| NVDLA_WEIGHT_COMPRESSION_ENABLE                                                    | Support of the feature of weight compression.<br>Disable this can save area in CBUF                                 | YES                          | NO                           |
| NVDLA_WINOG<br>RAD_ENABLE                                                          | Support of the optimization feature of weight compression.<br>Disable this can save area of CSC/CMAC/CACC           | YES                          | NO                           |
| NVDLA_MAC_ATOMI<br>C_C_SIZE                                                        | MAC atomic size of input channel number                                                                             | 64                           | 8                            |
| NVDLA_MAC_ATOMI<br>C_K_SIZE                                                        | MAC atomic size of output kernel number                                                                             | 32                           | 8                            |
| NVDLA_MEMORY_A<br>TOMIC_SIZE                                                       | Memory smallest access size, also the data cube is aligned with this size. Note: the size is # of feature data type | 32                           | 8                            |

| Scalability Parameter        | Description                                                                                   | INT8 Large Config(nv_large) | INT8 Small Config(nv_small) |
|------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------|-----------------------------|
| NVDLA_BATCH_ENA BLE          | Support of optimization feature of batch.<br>Disable this can save area in SDP/CACC/CSC/CD MA | YES                         | No                          |
| NVDLA_MAX_BATCH_SIZE         | Maximum batch size, this will directly impact the local buffer size                           | 32                          | •                           |
| NVDLA_CBUF_BANK_NUMBER       | Convolutional buffer bank number                                                              | 16                          | 32                          |
| NVDLA_CBUF_BANK_WIDTH        | Convolutional buffer bank data width                                                          | 64B                         | 8B                          |
| NVDLA_CBUF_BANK_DEPTH        | Convolutional buffer bank depth                                                               | 512                         | 512                         |
| NVDLA_SECONDARY_MEMIF_ENABLE | Support the secondary memory interface (SRAMIF)                                               | Yes                         | No                          |
| NVDLA_SDP_LUT_ENABLE         | SDP support Look-up-Table for non-linear function                                             | Yes                         | No                          |
| NVDLA_SDP_BS_ENABLE          | SDP support Bias/Scaling function                                                             | Yes                         | Yes                         |
| NVDLA_SDP_BN_ENABLE          | SDP support Batch-Normalization function                                                      | Yes                         | Yes                         |
| NVDLA_SDP_EW_ENABLE          | SDP support Element-wise-operation function                                                   | Yes                         | No                          |
| NVDLA_SDP_BS_THROUGHPUT      | Throughput of SDP Bias/Scaling function                                                       | 16                          | 1                           |
| NVDLA_SDP_BN_THROUGHPUT      | Throughput of SDP Batch-Normalization function                                                | 16                          | 1                           |
| NVDLA_SDP_EW_THROUGHPUT      | Throughput of SDP Element-wise-operation function                                             | 4                           | •                           |
| NVDLA_BDMA_ENABLE            | Support the bridge DMA engine function                                                        | Yes                         | No                          |
| NVDLA_RUBIK_ENABLE           | Support the rubik engine function                                                             | Yes                         | No                          |
| NVDLA_PDP_ENABLE             | Support PDP engine function                                                                   | Yes                         | Yes                         |
| NVDLA_PDP_THROUGHPUT         | Throughput of PDP engine function                                                             | 8                           | 1                           |

| Scalability Parameter                  | Description                                                                    | INT8 Large Config(nv_large) | INT8 Small Config(nv_small) |
|----------------------------------------|--------------------------------------------------------------------------------|-----------------------------|-----------------------------|
| NVDLA_CDP_ENAB_LE                      | Support CDP engine function                                                    | Yes                         | Yes                         |
| NVDLA_CDP_THROUGHPUT                   | Throughput of CDP engine function                                              | 8                           | 1                           |
| NVDLA_PRIMARY_MEMIF_MAX_BURST_LENGTH   | Primary memory interface maximum burst length number                           | 1                           | 4                           |
| NVDLA_PRIMARY_MEMIF_WIDTH              | Primary memory interface data width                                            | 64B                         | 8B                          |
| NVDLA_PRIMARY_MEMIF_LATENCY            | Primary memory interface data return latency cycles for read access            | 1200                        | 50                          |
| NVDLA_SECONDARY_MEMIF_MAX_BURST_LENGTH | Secondary memory interface (SRAMIF) maximum burst length number                | 4                           | •                           |
| NVDLA_SECONDARY_MEMIF_WIDTH            | Secondary memory interface (SRAMIF) data width                                 | 64B                         | •                           |
| NVDLA_SECONDARY_MEMIF_LATENCY          | Secondary memory interface (SRAMIF) data return latency cycles for read access | 128                         | •                           |
| NVDLA_MEMIF_ADDRESS_WIDTH              | Address bit width for external memory interface                                | 64                          | 32                          |

## More Details

### NVDLA\_MAC\_ATOMIC\_C\_SIZE and NVDLA\_MAC\_ATOMIC\_K\_SIZE

These two parameters affect determine the number of mac cells and number of multipliers in each mac cell. The total number of multipliers is  $NVDLA\_MAC\_ATOMIC\_C\_SIZE \times NVDLA\_MAC\_ATOMIC\_K\_SIZE$ . The number of kernels in one kernel group is  $NVDLA\_MAC\_ATOMIC\_C\_SIZE$ .

### NVDLA\_MEMORY\_atomic\_size

This parameter determines the size of one atomic cube which is  $1 \times 1 \times NVDLA\_MEMORY\_ATOMIC\_SIZE$ . Feature, Weight, Bias, PReLU, Batch Normalization and Element-Wise data cubes are split into atomic cubes before loaded or stored into memory. In nvdla1 and nv\_large configurations, size of atomic cube is  $1 \times 1 \times 32$ . In nv\_small configuration, it's  $1 \times 1 \times 8$ . Line stride and surface stride should also align to  $NVDLA\_MEMORY\_ATOMIC\_SIZE$ .

### NVDLA\_CBUF\_BANK\_NUMBER, NVDLA\_CBUF\_BANK\_WIDTH and NVDLA\_CBUF\_BANK\_DEPTH

These parameters determine the size of cbuf. (NVDLA\_CBUF\_BANK\_NUMBER \* NVDLA\_CBUF\_BANK\_WIDTH \* NVDLA\_CBUF\_BANK\_DEPTH) For nv\_small, the size is 32\*8\*512 = 128KB. For nv\_small\_256, the size is 32\*32\*128 = 128KB.

## Config nv\_small\_256

This config is created for higher convolution performance than nv\_small. Comparing with nv\_small, the difference is that CMAC has 256 multipliers, not 64. In this configuration NVDLA\_MAC\_ATOMIC\_C\_SIZE is 32 and NVDLA\_MAC\_ATOMIC\_C\_K\_SIZE is 8. Accordingly, NVDLA\_CBUF\_BANK\_WIDTH is 32 and NVDLA\_CBUF\_BANK\_DEPTH is 128.

### Sub-unit identifier table

| Sub-unit Identifier | Sub-unit Name |
|---------------------|---------------|
| 0x0000              | End of list   |
| 0x0001              | GLB           |
| 0x0002              | CIF           |
| 0x0003              | CDMA          |
| 0x0004              | CBUF          |
| 0x0005              | CSC           |
| 0x0006              | CMAC          |
| 0x0007              | CACC          |
| 0x0008              | SDP_RDMA      |
| 0x0009              | SDP           |
| 0x000a              | PDP_RDMA      |
| 0x000b              | PDP           |
| 0x000c              | CDP_RDMA      |
| 0x000d              | CDP           |
| 0x000e              | BDMA          |
| 0x000f              | RUBIK         |

Note:

1. CIF(ID=0x0002) can be configured to MCIF or SRAMIF.
2. There are two CMACs in nv\_small and nv\_large. (CMAC\_A and CMAC\_B)
3. CBUF doesn't have registers.

### Descriptors and payloads of sub-units in ConfigROM

The reg offset in bellow tables are the relative offset to the beginning of current descriptor.

#### GLB

| Reg offset (in Byte) | Reg name | Reg fields                                         | Value in nv_small config | Value in nv_large config |
|----------------------|----------|----------------------------------------------------|--------------------------|--------------------------|
| 0x0                  | GLB_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x00000001               | 0x00000001               |

#### CIF

| Reg offset (in Byte)      | Reg name                        | Reg fields                                         | Value in nv_small config                                                        | Value in nv_large config (MCIF) | Value in nv_large config (SRAMIF) |
|---------------------------|---------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------|---------------------------------|-----------------------------------|
| 0x0                       | CIF_DESC                        | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x00180002                                                                      | 0x00180002                      | 0x00180002                        |
| Incompatible capabilities | 0x4                             | CIF_CAP_INCOMPAT                                   | 0x0                                                                             | 0x0                             | 0x0                               |
| Compatible capabilities   | 0x8                             | CIF_CAP_COMPAT                                     | bit 0: CIF_IS_SRAM. Set to 1 if this CIF is connected to a separate SRAM block. | 0x0                             | 0x1                               |
| Baseline parameters       | 0xc                             | CIF_BASE_WIDTH                                     | bits 0-7: width (max 256B)                                                      | 0x8                             | 0x40                              |
| 0x10                      | CIF_BASE_LATENCY                | bits 0-15: latency (max 65535 cycles)              | 0x32                                                                            | 0x4b0                           | 0x80                              |
| 0x14                      | CIF_BASE_BURST_LENGTH_MAX       | bits 0-7: max burst length (max 256B)              | 0x4                                                                             | 0x4                             | 0x4                               |
| 0x18                      | CIF_BASE_MEMORY_INTERFACE_WIDTH | memory interface width                             | 0x20                                                                            | 0x40                            | 0x40                              |

#### CDMA

| Reg offset (in Byte)      | Reg name                | Reg fields                                                                                                                                            | Value in nv_small config | Value in nv_large config |
|---------------------------|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|--------------------------|
| 0x0                       | CDMA_DESC               | Bits 0-15: unit id.<br>Bits 16-31: payload length.                                                                                                    | 0x003400 03              | 0x003400 03              |
| Incompatible capabilities | CDMA_CAP_INCOMPAT       |                                                                                                                                                       | 0x0                      | 0x0                      |
| Compatible capabilities   | CDMA_CAP_COMPAT         | bit 0:<br>WINOGRAD<br>bit 1:<br>MULTI_BA TCH<br>bit 2:<br>FEATURE_COMPRESS ION<br>bit 3:<br>WEIGHT_COMPRESS ION<br>bit 4:<br>IMAGE_IN<br>bit 31: 1'b0 | 0x10                     | 0x1b                     |
| Baseline parameters       | CDMA_BASE_FEATURE_TYPES | Supported data types of input feature data                                                                                                            | 0x10                     | 0x10                     |
| 0x10                      | CDMA_BASE_WEIGHT_TYPES  | Supported data types of input weight data                                                                                                             | 0x10                     | 0x10                     |
| 0x14                      | CDMA_BASE_ATOMIC_C      | atomic_c                                                                                                                                              | 0x8                      | 0x40                     |
| 0x18                      | CDMA_BASE_atomic_K      | atomic_k                                                                                                                                              | 0x8                      | 0x20                     |
| 0x1c                      | CDMA_BASE_atomic_M      | atomic_m                                                                                                                                              | 0x8                      | 0x20                     |

| Reg offset (in Byte)     | Reg name                                 | Reg fields                           | Value in nv_small config | Value in nv_large config |
|--------------------------|------------------------------------------|--------------------------------------|--------------------------|--------------------------|
| 0x20                     | CDMA_BAS<br>E_CBUF_B<br>ANK_NUM          | cbuf_ban<br>k_number                 | 0x20                     | 0x10                     |
| 0x24                     | CDMA_BAS<br>E_CBUF_B<br>ANK_WIDT H       | cbuf_ban<br>k_width                  | 0x8                      | 0x40                     |
| 0x28                     | CDMA_BAS<br>E_CBUF_B<br>ANK_DEPT H       | cbuf_ban<br>k_depth                  | 0x200                    | 0x200                    |
| Capabilities' parameters | 0x2c<br>CDMA_MUL<br>TI_BATCH<br>_MAX     | max_batc h                           | 0x0                      | 0x20                     |
| 0x30                     | CDMA_IMA<br>GE_IN_FO<br>RMATS_PA<br>CKED | Supported packed image formats       | 0x0cff0 01               | 0x0cff0 01               |
| 0x34                     | CDMA_IMA<br>GE_IN_FO<br>RMATS_SE MI      | Supported semi-pla nar image formats | 0x3                      | 0x3                      |

#### CBUF

| Reg offset (in Byte)      | Reg name                       | Reg fields                                         | Value in nv_small config | Value in nv_large config |
|---------------------------|--------------------------------|----------------------------------------------------|--------------------------|--------------------------|
| 0x0                       | CBUF_DESC                      | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x001800 04              | 0x001800 04              |
| Incompatible capabilities | 0x4<br>CBUF_CAP<br>_INCOMPA T  |                                                    | 0x0                      | 0x0                      |
| Compatible capabilities   | 0x8<br>CBUF_CAP<br>_COMPAT     |                                                    | 0x0                      | 0x0                      |
| Baseline parameters       | 0xc<br>CBUF_BAS<br>E_BANK_N UM | cbuf_ban<br>k_number                               | 0x20                     | 0x10                     |
| 0x10                      | CBUF_BAS<br>E_BANK_W<br>IDTH   | cbuf_ban<br>k_width                                | 0x8                      | 0x40                     |
| 0x14                      | CBUF_BAS<br>E_BANK_D<br>EPTH   | cbuf_ban<br>k_depth                                | 0x200                    | 0x200                    |
| 0x18                      | CBUF_BAS<br>E_CDMA_I D         | cdma_id                                            | 0x3                      | 0x4                      |

#### CSC

| Reg offset (in Byte)      | Reg name | Reg fields                                         | Value in nv_small config                                                                                                                | Value in nv_large config |      |
|---------------------------|----------|----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|--------------------------|------|
| 0x0                       | CSC_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x003000 05                                                                                                                             | 0x003000 05              |      |
| Incompatible capabilities | 0x4      | CSC_CAP_INCOMPAT                                   | 0x0                                                                                                                                     | 0x0                      |      |
| Compatible capabilities   | 0x8      | CSC_CAP_COMPAT                                     | bit 0: WINOGRAD<br>bit 1: MULTI_BA TCH<br>bit 2: FEATURE_COMPRESS ION<br>bit 3: WEIGHT_C OMPRESSI ON<br>bit 4: IMAGE_IN<br>bit 31: 1'b0 | 0x10                     | 0x1b |
| Baseline parameters       | 0xc      | CSC_BASE_FEATURE_TYPES                             | Supported data types of input feature data                                                                                              | 0x10                     | 0x10 |
|                           | 0x10     | CSC_BASE_WEIGHT_TYPES                              | Supported data types of input weight data                                                                                               | 0x10                     | 0x10 |
|                           | 0x14     | CSC_BASE_ATOMIC_C                                  | atomic_c                                                                                                                                | 0x8                      | 0x40 |
|                           | 0x18     | CSC_BASE_ATOMIC_K                                  | atomic_k                                                                                                                                | 0x8                      | 0x20 |
|                           | 0x1c     | CSC_BASE_ATOMIC_M                                  | atomic_m                                                                                                                                | 0x8                      | 0x20 |

| Reg offset (in Byte)          | Reg name                           | Reg fields           | Value in nv_small config | Value in nv_large config |
|-------------------------------|------------------------------------|----------------------|--------------------------|--------------------------|
| 0x20                          | CSC_BASE<br>_CBUF_BA<br>NK_NUM     | cbuf_ban<br>k_number | 0x20                     | 0x10                     |
| 0x24                          | CSC_BASE<br>_CBUF_BA<br>NK_WIDTH   | cbuf_ban<br>k_width  | 0x8                      | 0x40                     |
| 0x28                          | CSC_BASE<br>_CBUF_BA<br>NK_DEPGT_H | cbuf_ban<br>k_depth  | 0x200                    | 0x200                    |
| 0x2c                          | CSC_BASE<br>_CDMA_ID               | cdma_id              | 0x3                      | 0x4                      |
| Capabili ties'<br>paramete rs | 0x30<br>CSC_MULT<br>I_BATCH_MAX    | max_batc h           | 0x0                      | 0x20                     |

#### CMAC

There are two CMAC (CMAC\_A and CMAC\_B) in NVDLA nv\_small and nv\_large design. Their descriptors and payloads are same. They use different slots of address space.

| Reg offset (in Byte)           | Reg name                               | Reg fields                                           | Value in nv_small config | Value in nv_large config |
|--------------------------------|----------------------------------------|------------------------------------------------------|--------------------------|--------------------------|
| 0x0                            | CMAC_DESC                              | Bits 0-15: unit id.<br>Bits 16-31: payload length.   | 0x001c00 06              | 0x001c00 06              |
| Incompat ible<br>capabili ties | 0x4<br>CMAC_CAP<br>_INCOMPA T          |                                                      | 0x0                      | 0x0                      |
| Compatib le<br>capabili ties   | 0x8<br>CMAC_CAP<br>_COMPAT             | bit 0:<br>WINOGRAD<br>bit 31: 1'b0                   | 0x0                      | 0x0                      |
| Baseline<br>paramete rs        | 0xc<br>CMAC_BAS<br>E_FEATUR<br>E_TYPES | Supporte d<br>data types of<br>input feature<br>data | 0x10                     | 0x10                     |
| 0x14                           | CMAC_BAS<br>E_ATOMIC_C                 | atomic_c                                             | 0x8                      | 0x40                     |
| 0x18                           | CMAC_BAS<br>E_atomic_K                 | atomic_k                                             | 0x8                      | 0x20                     |
| 0x1c                           | CMAC_BAS<br>E_CDMA_ID                  | cdma_id                                              | 0x3                      | 0x4                      |

#### CACC

| Reg offset (in Byte)      | Reg name  | Reg fields                                         | Value in nv_small config                               | Value in nv_large config |      |
|---------------------------|-----------|----------------------------------------------------|--------------------------------------------------------|--------------------------|------|
| 0x0                       | CACC_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x002000 07                                            | 0x002000 07              |      |
| Incompatible capabilities | 0x4       | CACC_CAP_INCOMPAT                                  | 0x0                                                    | 0x0                      |      |
| Compatible capabilities   | 0x8       | CACC_CAP_COMPAT                                    | bit 0: WINOGRAD<br>bit 1: MULTI_BA_TCH<br>bit 31: 1'b0 | 0x0                      | 0x3  |
| VBaseline parameters      | 0xc       | CACC_BASE_FEATURES                                 | Supported data types of input feature data             | 0x10                     | 0x10 |
|                           | 0x10      | CACC_BASE_WEIGHTS                                  | Supported data types of input weight data              | 0x10                     | 0x10 |
|                           | 0x14      | CACC_BASE_ATOMIC_C                                 | atomic_k                                               | 0x8                      | 0x20 |
|                           | 0x18      | CACC_BASE atomic_K                                 | atomic_m                                               | 0x8                      | 0x20 |
|                           | 0x1c      | CACC_BASE CDMA_ID                                  | cdma_id                                                | 0x3                      | 0x4  |
| Capabilities parameters   | 0x20      | CACC_MULTI_BATCH_MAX                               | max_batch                                              | 0x0                      | 0x20 |

#### SDP\_RDMA

| Reg offset (in Byte) | Reg name      | Reg fields                                         | Value in nv_small config | Value in nv_large config |
|----------------------|---------------|----------------------------------------------------|--------------------------|--------------------------|
| 0x0                  | SDP_RDMA_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x000e00 08              | 0x000e00 08              |

|                           | Reg offset (in Byte) | Reg name               | Reg fields                            | Value in nv_small config | Value in nv_large config |
|---------------------------|----------------------|------------------------|---------------------------------------|--------------------------|--------------------------|
| Incompatible capabilities | 0x4                  | SDP_RDMA_CAP_INCOMPAT  |                                       | 0x0                      | 0x0                      |
| Compatible capabilities   | 0x8                  | SDP_RDMA_CAP_COMPAT    |                                       | 0x0                      | 0x0                      |
| Baseline parameters       | 0xc                  | SDP_RDMA_BASE_ATOMIC_M | atomic_m                              | 0x8                      | 0x20                     |
|                           | 0xe                  | SDP_RDMA_BASE_SDP_ID   | sdp_id (slot id of corresponding sdp) | 0x9                      | 0xa                      |

#### SDP

|                           | Reg offset (in Byte) | Reg name               | Reg fields                                                                                                  | Value in nv_small config | Value in nv_large config |
|---------------------------|----------------------|------------------------|-------------------------------------------------------------------------------------------------------------|--------------------------|--------------------------|
|                           | 0x0                  | SDP_DESC               | Bits 0-15: unit id.<br>Bits 16-31: payload length.                                                          | 0x002000 09              | 0x002000 09              |
| Incompatible capabilities | 0x4                  | SDP_CAP_INCOMPAT       |                                                                                                             | 0x0                      | 0x0                      |
| Compatible capabilities   | 0x8                  | SDP_CAP_COMPAT         | bit 0: WINOGRAD<br>bit 1: MULTI_BA_TCH<br>bit 2: LUT<br>bit 3: BS<br>bit 4: BN<br>bit 5: EW<br>bit 31: 1'b0 | 0x18                     | 0x3f                     |
| Baseline parameters       | 0xc                  | SDP_BASE_FEATURE_TYPES | Supported data types of input feature data                                                                  | 0x10                     | 0x10                     |
|                           | 0x10                 | SDP_BASE_CDMA_ID       | cdma_id                                                                                                     | 0x3                      | 0x4                      |

| Reg offset (in Byte)      | Reg name                          | Reg fields        | Value in nv_small config | Value in nv_large config |
|---------------------------|-----------------------------------|-------------------|--------------------------|--------------------------|
| Capabili ties' parameters | 0x14<br>SDP_MULT<br>I_BATCH_MAX   | max_batch         | 0x0                      | 0x20                     |
|                           | 0x18<br>SDP_<br>BS_THROU<br>GHPUT | bs_throu<br>ghput | 0x1                      | 0x10                     |
|                           | 0x1c<br>SDP_<br>BN_THROU<br>GHPUT | bn_throu<br>ghput | 0x1                      | 0x10                     |
|                           | 0x20<br>SDP_<br>EW_THROU<br>GHPUT | ew_throu<br>ghput | 0x0                      | 0x4                      |

#### PDP\_RDMA

| Reg offset (in Byte)           | Reg name                              | Reg fields                                               | Value in nv_small config | Value in nv_large config |
|--------------------------------|---------------------------------------|----------------------------------------------------------|--------------------------|--------------------------|
| 0x0                            | PDP_<br>RDMA_DES_C                    | Bits 0-15: unit<br>id.<br>Bits 16-31:<br>payload length. | 0x000e00 0a              | 0x000e00 0a              |
| Incompat ible<br>capabili ties | 0x4<br>PDP_<br>RDMA_CAP<br>_INCOMPA T |                                                          | 0x0                      | 0x0                      |
| Compatib le<br>capabili ties   | 0x8<br>PDP_<br>RDMA_CAP<br>_COMPAT    |                                                          | 0x0                      | 0x0                      |
| Baseline<br>paramete rs        | 0xc<br>PDP_RDMA<br>_BASE_AT<br>OMIC_M | atomic_m                                                 | 0x8                      | 0x20                     |
| 0xe                            | PDP_RDMA<br>_BASE_PD<br>P_ID          | pdp_id (slot id<br>of correspo<br>nding pdp)             | 0xb                      | 0xc                      |

#### PDP

| Reg offset (in Byte)      | Reg name | Reg fields                                         | Value in nv_small config                   | Value in nv_large config |      |
|---------------------------|----------|----------------------------------------------------|--------------------------------------------|--------------------------|------|
| 0x0                       | PDP_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x001000 0b                                | 0x001000 0b              |      |
| Incompatible capabilities | 0x4      | PDP_CAP_INCOMPAT                                   | 0x0                                        | 0x0                      |      |
| Compatible capabilities   | 0x8      | PDP_CAP_COMPAT                                     | 0x0                                        | 0x0                      |      |
| Baseline parameters       | 0xc      | PDP_BASE_FEATURE_TYPES                             | Supported data types of input feature data | 0x10                     | 0x10 |
|                           | 0x10     | PDP_BASE_THROUGHPUT                                | throughput                                 | 0x1                      | 0x8  |

#### CDP\_RDMA

| Reg offset (in Byte)      | Reg name | Reg fields                                         | Value in nv_small config              | Value in nv_large config |      |
|---------------------------|----------|----------------------------------------------------|---------------------------------------|--------------------------|------|
| 0x0                       | CDP_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x000e00 0c                           | 0x000e00 0c              |      |
| Incompatible capabilities | 0x4      | CDP_RDMA_CAP_INCOMPAT                              | 0x0                                   | 0x0                      |      |
| Compatible capabilities   | 0x8      | CDP_RDMA_CAP_COMPAT                                | 0x0                                   | 0x0                      |      |
| Baseline parameters       | 0xc      | CDP_RDMA_BASE_ATOMICOMIC_M                         | atomic_m                              | 0x8                      | 0x20 |
|                           | 0xe      | CDP_RDMA_BASE_P_ID                                 | cdp_id (slot id of corresponding cdp) | 0xd                      | 0xe  |

#### CDP

| Reg offset (in Byte)      | Reg name            | Reg fields                                         | Value in nv_small config                   | Value in nv_large config |      |
|---------------------------|---------------------|----------------------------------------------------|--------------------------------------------|--------------------------|------|
| 0x0                       | CDP_DESC            | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x001000 0d                                | 0x001000 0d              |      |
| Incompatible capabilities | 0x4                 | CDP_CAP_INCOMPAT                                   | 0x0                                        | 0x0                      |      |
| Compatible capabilities   | 0x8                 | CDP_CAP_COMPAT                                     | 0x0                                        | 0x0                      |      |
| Baseline parameters       | 0xc                 | CDP_BASE_FEATURE_TYPES                             | Supported data types of input feature data | 0x10                     | 0x10 |
| 0x10                      | CDP_BASE_THROUGHPUT | throughput                                         | 0x1                                        | 0x8                      |      |

#### BDMA

| Reg offset (in Byte) | Reg name  | Reg fields                                         | Value in nv_small config | Value in nv_large config |
|----------------------|-----------|----------------------------------------------------|--------------------------|--------------------------|
| 0x0                  | BDMA_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x0004000e               | 0x0004000e               |

#### RUBIK

| Reg offset (in Byte) | Reg name   | Reg fields                                         | Value in nv_small config | Value in nv_large config |
|----------------------|------------|----------------------------------------------------|--------------------------|--------------------------|
| 0x0                  | RUBIK_DESC | Bits 0-15: unit id.<br>Bits 16-31: payload length. | 0x0004000f               | 0x0004000f               |

## Supported data types or weight types

Below table lists the fields of registers of supported data types or weight types in above sections

| Bit | Data type or Weight type |
|-----|--------------------------|
| 0   | Binary                   |
| 1   | INT4                     |
| 2   | UINT4                    |

| Bit | Data type or Weight type |
|-----|--------------------------|
| 3   | INT8                     |
| 4   | UINT8                    |
| 5   | INT16                    |
| 6   | UINT16                   |
| 7   | INT32                    |
| 8   | UINT32                   |
| 9   | FP16                     |
| 10  | FP32                     |
| 11  | FP64                     |

### Supported packed image formats

Below table lists the fields of registers of supported packed image formats in above sections

| Bit | Image format   |
|-----|----------------|
| 0   | R8             |
| 1   | R10            |
| 2   | R12            |
| 3   | R16            |
| 4   | R16_I          |
| 5   | R16_F          |
| 6   | A16B16G16R16   |
| 7   | X16B16G16R16   |
| 8   | A16B16G16R16_F |
| 9   | A16Y16U16V16   |
| 10  | V16U16Y16A16   |
| 11  | A16Y16U16V16_F |
| 12  | A8B8G8R8       |
| 13  | A8R8G8B8       |
| 14  | B8G8R8A8       |
| 15  | R8G8B8A8       |
| 16  | X8B8G8R8       |
| 17  | X8R8G8B8       |
| 18  | B8G8R8X8       |
| 19  | R8G8B8X8       |
| 20  | A2B10G10R10    |
| 21  | A2R10G10B10    |
| 22  | B10G10R10A2    |
| 23  | R10G10B10A2    |
| 24  | A2Y10U10V10    |
| 25  | V10U10Y10A2    |
| 26  | A8Y8U8V8       |

#### **Bit Image format**

| 27 | V8U8Y8A8 |
|----|----------|
|----|----------|

### Supported semi-planar image formats

Below table lists the fields of registers of supported semi-planar image formats in above sections

#### **Bit Image format**

| 0 | Y8__U8V8_N444    |
|---|------------------|
| 1 | Y8__V8U8_N444    |
| 2 | Y10__U10V10_N444 |
| 3 | Y10__V10U10_N444 |
| 4 | Y12__U12V12_N444 |
| 5 | Y12__V12U12_N444 |
| 6 | Y16__U16V16_N444 |
| 7 | Y16__V16U16_N444 |

### Address space layout

In the address space layout, the order of sub-units is same as the order of the descriptors in Configuration ROM. The size of one slot is 4KB.

nv\_small:



![](7bed2d7c96d86bf922295a1252da52a5_img.jpg)

Diagram illustrating the memory layout of the ConfigROM, showing memory addresses (0, 4KB, 8KB, 12KB, 16KB, 20KB, 24KB, 28KB, 32KB, 36KB, 40KB, 44KB, 48KB, 52KB) and corresponding memory segments:

| Address | Segment           |
|---------|-------------------|
| 0       | Configuration ROM |
| 4KB     | GLB               |
| 8KB     | MCIF              |
| 12KB    | CDMA              |
| 16KB    | CSC               |
| 20KB    | CMAC_A            |
| 24KB    | CMAC_B            |
| 28KB    | CACC              |
| 32KB    | SDP_RDMA          |
| 36KB    | SDP               |
| 40KB    | PDP_RDMA          |
| 44KB    | PDP               |
| 48KB    | CDP_RDMA          |
| 52KB    |                   |

Configuration ROM contains the following fields (indicated by a dashed box):

| HW Version                          |
|-------------------------------------|
| Sub-units' descriptors and payloads |
| End of list                         |

56KB

CDP

nv\_large:



![](9b5411fa2d169b66f6185fbf67b49766_img.jpg)

Diagram illustrating the memory layout of the ConfigROM, showing memory addresses (0, 4KB, 8KB, 12KB, 16KB, 20KB, 24KB, 28KB, 32KB, 36KB, 40KB, 44KB, 48KB, 52KB) and corresponding memory blocks:

| Address | Block             | Details                                                          |
|---------|-------------------|------------------------------------------------------------------|
| 0       | Configuration ROM | HW Version<br>Sub-units' descriptors and payloads<br>End of list |
| 4KB     | GLB               |                                                                  |
| 8KB     | MCIF              |                                                                  |
| 12KB    | SRAMIF            |                                                                  |
| 16KB    | CDMA              |                                                                  |
| 20KB    | CSC               |                                                                  |
| 24KB    | CMAC_A            |                                                                  |
| 28KB    | CMAC_B            |                                                                  |
| 32KB    | CACC              |                                                                  |
| 36KB    | SDP_RDMA          |                                                                  |
| 40KB    | SDP               |                                                                  |
| 44KB    | PDP_RDMA          |                                                                  |
| 48KB    | PDP               |                                                                  |
| 52KB    |                   |                                                                  |

![](485c57a6add7e0bd7898009db1179ee6_img.jpg)

| 56KB | CDP_RDMA |
|------|----------|
| 60KB | CDP      |
| 64KB | BDMA     |
| 68KB | RUBIK    |