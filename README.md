# DELL Optiplex 7060 · OpenCore Hackintosh

Intel Core i5-8500T | UHD 630 | 16 GB DDR4 | Q370 Chipset

![CPU](https://img.shields.io/badge/CPU-Intel_Core_i5_8500T-0071C5)
![GPU](https://img.shields.io/badge/GPU-Intel_UHD_630-0071C5)
![RAM](https://img.shields.io/badge/RAM-16_GB_DDR4-8B5CF6)
![Chipset](https://img.shields.io/badge/Chipset-Q370-00A3E0)
![Status](https://img.shields.io/badge/Status-Working-success)

---

## Hardware

| Component | Specification |
|:----------|:--------------|
| Model | DELL Optiplex 7060 Desktop |
| CPU | Intel Core i5-8500T |
| RAM | 16 GB (Kingston DDR4 2666 MHz 8 GB + Micron DDR4 2400 MHz 4 GB × 2) |
| GPU | Intel UHD Graphics 630 (128 MB) |
| Motherboard | Dell 0NC2VH (Q370 Chipset) |
| Storage | WD BLACK SN770 (500 GB NVMe) |
| Ethernet | Intel I219-LM |
| Audio | Realtek ALC255 |

## BIOS Settings

| Setting | Value |
|:--------|:-----:|
| SATA Operation | AHCI |
| Secure Boot | Disabled |
| Intel SGX | Disabled |

## DVMT Modification

Run the following in modGRUBShell (included in EFI):

```
setup_var 0x8DC 0x02    (DVMT → 64 MB)
setup_var 0x5BE 0x00    (CFG Lock → Disabled)
```

## Driver Status

| Feature | Status | Feature | Status |
|:--------|:------:|:--------|:------:|
| Audio | ✅ Working | GPU | ✅ Working |
| Ethernet | ✅ Working | DisplayPort | ✅ Working |
| USB | ✅ Working | Sleep | ✅ Working |

## Installation

1. Configure BIOS per above
2. Modify DVMT using modGRUBShell
3. Mount EFI partition, copy EFI to USB
4. Boot from USB → Install macOS
