## Update (9/5/2020)

## Configuration

- Mainboard: **ROG STRIX B450-I GAMING**
- CPU:       **AMD Ryzen™ 5 2600 Processor**
- Ram:       **Aorus RGB 16GB (2 x 8GB) 3200Mhz DDR4**
- GPU:       **ROG STRIX Radeon™ RX 5700 XT O8G GAMING**
- SSD:       **240GB WD Green M2**


## MacOS

- Big Sur (20B29)
- [Download](https://github.com/AnhDT0407/Hackintosh/edit/master/readme.md)


## OpenCore

- Version: 0.6.3
- [OpenCorePkg release](https://github.com/acidanthera/OpenCorePkg/releases)

## SMCAMDProcessor

[Homepage](https://github.com/trulyspinach/SMCAMDProcessor)

### Directory Structure

When directory boot is used the directory structure used should follow the description on Directory Structure figure. Available entries include:

- BOOT
  - BOOTx64.efi
    - _Initial booter, which loads OpenCore.efi unless it was already started as a driver._
- OC
  - ACPI
    - _Directory used for storing supplemental ACPI information for ACPI section._
  - Drivers
    - _Directory used for storing supplemental UEFI drivers for UEFI section._
  - Kexts
    - _Directory used for storing supplemental kernel information for Kernel section._
  - Tools
    - _Directory used for storing supplemental tools._
  - OpenCore.efi
    - _Main booter driver responsible for operating system loading._
  - config.plist
    - _OC Config._
- nvram.plist (_OpenCore variable import file._)


### Kexts

 Please refer to [Kexts.md](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Kexts.md) for a full list of supported kexts




