### AXI-4 JPEG Decoder

Github:   [https://github.com/ultraembedded/core_jpeg_decoder](https://github.com/ultraembedded/core_jpeg_decoder)

This component is a HW JPEG decoder (in Verilog) with AXI-4 DMA.  
It is based around my [JPEG Decoder core](https://github.com/ultraembedded/core_jpeg) and adds a register interface and DMA for offloading data input and output transfers to and from the JPEG decoder core.

#### Cloning
This repo contains submodules.
Make sure to clone them all with the following command;

```
git clone --recursive https://github.com/ultraembedded/core_jpeg_decoder.git
```

#### Features
* HW JPEG decoder.
* AXI-4 lite configuration interface.
* AXI-4 DMA for JPEG fetch, and RGB data writeback.
* RGB565 output format.
* ISO/IEC 10918-1 compliant JPEG Baseline decoding.
* Up to 64K x 64K image resolution.

##### Register Map

| Offset | Name | Description   |
| ------ | ---- | ------------- |
| 0x00 | JPEG_CTRL | [RW] JPEG Control Register |
| 0x04 | JPEG_STATUS | [R] Status Register |
| 0x08 | JPEG_SRC | [RW] DMA Source Address |
| 0x0c | JPEG_DST | [RW] DMA Target Address |

##### Register: JPEG_CTRL

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 31 | START | Start transfer. |
| 30 | ABORT | Abort transfer. |
| 23:0 | LENGTH | Source buffer length in bytes. |

##### Register: JPEG_STATUS

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 0 | BUSY | Core busy. |

##### Register: JPEG_SRC

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 31:0 | ADDR | Address (must be 32-byte aligned). |

##### Register: JPEG_DST

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 31:0 | ADDR | Address |

#### Testing
Tested on a Xilinx Artix 7 (Digilent Arty A7).

