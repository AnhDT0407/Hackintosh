## Configuration

- Mainboard: **ROG STRIX B450-I GAMING**
- CPU:       **AMD Ryzen™ 5 2600 Processor**
- Ram:       **Aorus RGB 16GB (2 x 8GB) 3200Mhz DDR4**
- GPU:       **ROG STRIX Radeon™ RX 5700 XT O8G GAMING**
- SSD:       **240GB WD Green M2**


## MacOS

- Catalina 10.15.3.00
- [Download](https://github.com/AnhDT0407/Hackintosh/edit/master/readme.md)


## OpenCore

- Version: 0.5.5
- [OpenCorePkg release](https://github.com/acidanthera/OpenCorePkg/releases)

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


## Gathering files

### Firmware Drivers

These are the drivers used for OpenCore, for the majority of systems you only need 3 .efi drivers to get up and running:

- [ApfsDriverLoader.efi](https://github.com/acidanthera/AppleSupportPkg/releases)
  - _Needed for seeing APFS volumes._
- [VboxHfs.efi](https://github.com/acidanthera/AppleSupportPkg/releases) or [HfsPlus.efi](https://cdn.discordapp.com/attachments/606452360495104000/633621011887292416/HFSPlus.efi)
  - _Needed for seeing HFS volumes. **Do not mix HFS drivers**._
- [FwRuntimeServices.efi](https://github.com/acidanthera/OpenCorePkg/releases) _(Available in OpenCore/EFI/OC/Drivers)_
  - _Used for patching boot.efi for NVRAM fixes and better memory management._

### Kexts

A kext is a kernel extension, you can think of this as a driver for macOS, these files will go into the Kexts folder in your EFI.

**Must haves:**

- [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases)
  - _Emulates the SMC chip found on real macs, without this macOS will not boot._
  - _Alternative is **FakeSMC** which can have better or worse support, most commonly used on legacy hardware._
- [Lilu](https://github.com/acidanthera/Lilu/releases)
  - _A kext to patch many processes, required for **AppleALC** and **WhateverGreen** and recommended for **VirtualSMC**._
  
**VirtualSMC Plugins:**

- SMCProcessor.kext
  - _Used for monitoring CPU temperature, **doesn't work AMD CPU based systems**._
- SMCSuperIO.kext
  - _Used for monitoring fan speed, **doesn't work AMD CPU based systems**._
- SMCLightSensor.kext
  - _Used for the ambient light sensor on laptops, **desktops can ignore**._
- SMCBatteryManager.kext
  - _Used for measuring battery readouts on laptops, **desktops can ignore**._
  
**Graphics:**

- [WhateverGreen](https://github.com/acidanthera/WhateverGreen/releases)
  - _Used for graphics patching, all GPUs benefit from this kext._
  
**Audio:**

  - [AppleALC](https://github.com/acidanthera/AppleALC/releases)
    - _Used for AppleHDA patching, used for giving you onboard audio. AMD 15h/16h may have issues with this and Ryzen/Threadripper systems rarely have mic support._
    
**Ethernet:**

  - [IntelMausiEthernet](https://github.com/Mieze/IntelMausiEthernet)
    - _Required for Intel NICs, newer chipsets are based off of I211-AT will need the [SmallTreeIntel82576](https://github.com/khronokernel/Opencore-Vanilla-Desktop-Guide/blob/master/extra-files/SmallTreeIntel82576.kext.zip). AMD motherboards with intel NICs generally run I211-AT._
  - [AtherosE2200Ethernet](https://github.com/Mieze/AtherosE2200Ethernet/releases)
    - _Required for Atheros and Killer NICs._
  - [RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases)
    - _Required for Realtek NICs._

**USB:**

  - [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)
    - _Used for injecting intel USB controllers, H370, B360, H310 and X79/X99/X299 systems will likely need [XHCI-unsupported](https://github.com/RehabMan/OS-X-USB-Inject-All) as well. **Does not work on AMD CPU based systems**._
  
**WiFi and Bluetooth:**
 
  - None.
  
**AMD CPU Specific kexts:**

  - [NullCPUPowerManagment](https://github.com/corpnewt/NullCPUPowerManagement)
    - _OpenCore 0.5.5, we have a much better solution known as `DummyPowerManagement` found under `Kernel` -> `Quirks`._


