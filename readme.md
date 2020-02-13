## Configuration

- Mainboard: **ROG STRIX B450-I GAMING**
- CPU:       **AMD Ryzen™ 5 2600 Processor**
- Ram:       **Aorus RGB 16GB (2 x 8GB) 3200Mhz DDR4**
- GPU:       **ROG STRIX Radeon™ RX 5700 XT O8G GAMING**
- SSD:       **240GB WD Green M2**

## MacOS

- Catalina 10.15.3.00

## OpenCore

- Version: 0.5.5
- [OpenCorePkg release](https://github.com/acidanthera/OpenCorePkg/releases)

### Directory Structure

When directory boot is used the directory structure used should follow the description on Directory Structure figure. Available entries include:

- BOOT
  - BOOTx64.efi

- OC

## Gathering files

### Firmware Drivers

These are the drivers used for OpenCore, for the majority of systems you only need 3 .efi drivers to get up and running:

- [ApfsDriverLoader.efi](https://github.com/acidanthera/AppleSupportPkg/releases)
  - _Needed for seeing APFS volumes._
- [VboxHfs.efi](https://github.com/acidanthera/AppleSupportPkg/releases) or [HfsPlus.efi](https://cdn.discordapp.com/attachments/606452360495104000/633621011887292416/HFSPlus.efi)
  - _Needed for seeing HFS volumes. **Do not mix HFS drivers**._
- [FwRuntimeServices.efi](https://github.com/acidanthera/OpenCorePkg/releases) _(Available in OpenCore/EFI/OC/Drivers)_
  - _Used for patching boot.efi for NVRAM fixes and better memory management._
