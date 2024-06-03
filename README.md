# Computer Configuration

- **Model:** Dell Optiplex 7060 Desktop
- **Processor:** Intel Core i5-8500T
- **Memory:** 
  - 16 GB (Kingston DDR4 2666MHz 8GB / Micron DDR4 2400MHz 4GB x 2)
- **Graphics Card:** Intel UHD Graphics 630 (128 MB / Dell)
- **Motherboard:** Dell ONC2VH (Q370 Chipset)
- **Hard Drive:** Western Digital WD BLACK SN770.500GB (500 GB / Solid State Drive)
- **Network Card:** Intel Ethernet Connection 1219-LM / Dell
- **Audio Card:** Intel High Definition Audio (ALC255)

## BIOS Settings

- **System Configuration**
  - SATA Operation: AHCI
- **Secure Boot**
  - Secure Boot Enable: Disabled
- **Intel Software Guard Extensions**
  - Intel SGX: Disabled

## Modifying DVMT using modGRUBShell

To enable graphics driver, execute the following commands using modGRUBShell (modGRUBShell is already included in the boot):

- `setup_var 0x8DC 0x02` (Modify DVMT to 64MB)
- `setup_var 0x5BE 0x00` (Disable CFG Lock)

## Boot Configuration

- Perfectly Supported:
  - Audio Card
  - Network Card
  - Integrated Graphics
  - DisplayPort Interface
  - 3.5mm Headphone Jack
  - Sleep/Wake Functionality

Please let me know if you have any further questions or need additional assistance!
