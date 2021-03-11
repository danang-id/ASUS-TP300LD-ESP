# ASUS TP300LD EFI System Partition

This repository contains files and folder inside the EFI System Partition (ESP) on my ASUS TP300LD notebook. This ESP contains some bootloaders and UEFI tools to boot to the operating systems I used, which are mainly macOS and Windows.

## List of Contents
* [ASUS TP300LD EFI System Partition](#asus-tp300ld-efi-system-partition)
  * [List of Contents](#list-of-contents)
  * [Specification of ASUS TP300LD](#specification-of-asus-tp300ld)
  * [Bootloader Information](#bootloader-information)
    * [UEFI Drivers Used](#uefi-drivers-used)
  * [[OS] macOS (Hackintosh) Information](#os-macos-hackintosh-information)
    * [macOS Version](#macos-version)
    * [Works on macOS](#works-on-macos)
    * [Not Works / Problems on macOS](#not-works--problems-on-macos)
    * [macOS Kernel Extensions (Kext) Used](#macos-kernel-extensions-kext-used)
  * [[OS] Windows Information](#os-windows-information)
    * [Windows Version](#windows-version)
    * [Works on Windows](#works-on-windows)
  * [Authors](#authors)
  * [License](#license)

## Specification of ASUS TP300LD
- **Processor**: Intel® Core™ i7-4510U
- **Chipset**: Intel® 8 Series Chipset
- **Integrated Graphic**: Intel® HD Graphics 4400 
- **Discrette Graphic**: NVIDIA® GeForce® 820M with 2GB DDR3 VRAM
- **Memory**: 
  - 1 x on-board Micron 4 GB DDR3L 1600Mhz SDRAM 
  - 1 x Vgen Secure 4 GB DDR3L 1600Mhz SDRAM
- **Storage**: 1 x Adata SSD 250GB
- **Audio**: Realtek ALC233
- **Wi-Fi**: Broadcom BCM94352HMB (Bluetooth Combo)
- **Touchpad**: ELAN ETD PS/2 Interface
- **Touchscreen**: Atmel Touchscreen USB Interface
- **Screen Size**: 13.1 inches
- **Native Display Resolution**: 1366x768 
- **Input/Output (I/O)**: 
  - 2 x USB 3.0 (Type A)
  - 1 x USB 2.0 (Type A)
  - 1 x HDMI out
  - 1 x AC adapter plug
  - 1 x Combo audio jack
  - 1 x Volume up/down
- **Battery**: 3 cells polymer battery, 50 watthours
- **BIOS Version**: TP300LD.300 (25 June 2019)

## Bootloader Information
This ESP contains these bootloaders.

- **[PRIMARY BOOTLOADER]** [OpenCore](https://github.com/acidanthera/OpenCorePkg) 0.6.3
- Windows Boot Manager

The boot mode used is **UEFI** with **CSM disabled** on **GUID Partition Table (GPT)** storage scheme.

### UEFI Drivers Used 
These are the UEFI drivers used by OpenCore.

- HfsPlus
- OpenRuntime
- OpenCanopy
 
## [OS] macOS (Hackintosh) Information
This ESP contains bootloader configured to run the following macOS, including what are works and what are not works.

### macOS Version
- **OS Version**: macOS Mojave Version 10.14.6 (Build 18G6032)
- **Installer**: Retail from the App Store, created using createinstallmedia

### Works on macOS
- [x] QE/CI Enabled Graphics of Intel® HD Graphics 4400 
- [x] Wi-Fi
- [x] Bluetooth
- [x] Touchpad
- [x] Touchscreen (on macOS 10.15+, should use [Touch-Base UPDD](https://touch-base.com/drivers))
- [x] Camera
- [x] Audio output (internal speaker + external jack)
- [x] Audio input (external jack)
- [x] Volume *fn* and side keys (for volume up, volume down, and mute)
- [x] Screen brightness *fn* keys (for brightness up and down)
- [x] All USB Ports (2.0 & 3.0)
- [x] Battery status indicator
- [x] HDMI out (video + audio)
- [x] Sleep, Shutdown, and Restart
- [x] Sleep and Wake with Lid

### Not Works / Problems on macOS
- [ ] Discrette Graphic of NVIDIA® GeForce® 820M (NVIDIA Optimus switchable graphic is not supported by hackintosh)
- [ ] Audio jack headset/speaker detection
- [ ] Audio input (internal mic)
- [ ] Audio output (external jack) distorted after sleep; must select an audio input in the Sound Preference Pane and keep the Sound Preference Pane open (otherwise, it will be distorted back when the Sound Preference Pane window is closed)

### macOS Kernel Extensions (Kext) Used
The OpenCore bootloader loads the kexts with a configured order.

1. USBMap
2. Lilu
3. VoodooPS2Controller
4. VoodooInput
5. VoodooPS2Mouse
6. VoodooPS2Trackpad
7. VoodooPS2Keyboard
8. VirtualSMC
9. AsusSMC
10. SMCProcessor
11. SMCBatteryManager
12. SMCLightSensor
13. WhateverGreen
14. AppleALC
15. NoTouchID
16. AirportBrcmFixup
17. AirPortBrcmNIC_Injector
18. BrcmBluetoothInjector
19. BrcmFirmwareData
20. BrcmPatchRAM2 (applied on macOS 10.14 and earlier)
21. BrcmPatchRAM3 (applied on macOS 10.15+)
22. HibernationFixup

## [OS] Windows Information
This ESP contains bootloader configured to run the following Windows.

### Windows Version
- **OS Version**: Windows 10 Home Single-Language 20H2 (Build 19042.610)
- **Installer**: Directly downloaded from Windows website 

### Works on Windows
All components are obviously working okay.

## Authors
- **Danang Galuh Tegar Prasetyo** - [danang-id](https://github.com/danang-id)

## License
This project is licensed under the BSD 3-Clause License - see the [LICENSE.md](LICENSE.md) file for details.
