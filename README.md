# ASUS TP300LD EFI System Partition (ESP)

This repository contains files and folder inside the EFI System Partition (ESP) on my ASUS TP300LD notebook. 
This ESP contains OpenCore and other UEFI tools to boot to the operating systems I used, which are mainly macOS. 
Other operating systems, like Windows or Linux, are also supported with this OpenCore configuration.

## Disclaimer!
The OpenCore configuration used in *this ESP is tightly linked with my machine's BIOS firmware version and configuration*.
Any attempts to use this ESP &mdash;even on the same exact brand, model, hardware configuration, and BIOS firmware 
version&mdash; are **not guaranteed** to work as well as describe here.

## List of Contents
- [ASUS TP300LD EFI System Partition (ESP)](#asus-tp300ld-efi-system-partition-esp)
  - [Disclaimer!](#disclaimer)
  - [List of Contents](#list-of-contents)
  - [Specification of ASUS TP300LD](#specification-of-asus-tp300ld)
  - [OpenCore Information](#opencore-information)
    - [UEFI Drivers Used](#uefi-drivers-used)
  - [[OS] macOS (Hackintosh)](#os-macos-hackintosh)
    - [SMBIOS and Supported macOS](#smbios-and-supported-macos)
    - [Works on macOS](#works-on-macos)
    - [Not Works / Problems on macOS](#not-works--problems-on-macos)
    - [macOS Kernel Extensions (Kext) Used](#macos-kernel-extensions-kext-used)
  - [[OS] Other Operating Systems](#os-other-operating-systems)
  - [Legal](#legal)

## Specification of ASUS TP300LD
- **Processor**: Intel® Core™ i7-4510U
- **Chipset**: Intel® 8 Series Chipset
- **Integrated Graphic**: Intel® HD Graphics 4400 
- **Discrette Graphic**: NVIDIA® GeForce® 820M with 2GB DDR3 VRAM
- **Memory**: _running on dual-channels_
  - 1 x on-board Micron 4 GB 1600Mhz DDR3L SDRAM 
  - 1 x Vgen Secure 4 GB 1600Mhz DDR3L SDRAM
- **Storage**: 1 x Samsung 870 EVO 500 GB
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
- **Battery**: 3 cells polymer battery, 50 watt-hours
- **BIOS Version**: TP300LD.300 (released 25 June 2019)

## OpenCore Information
This ESP contains [OpenCore](https://github.com/acidanthera/OpenCorePkg) version 0.7.6. The boot mode used 
is **UEFI** with **CSM disabled** on **GUID Partition Table (GPT)** storage scheme.

### UEFI Drivers Used 
These are the UEFI drivers used by OpenCore.

- btrfs_x64
- ext4_x64
- ExFatDxe
- NTFS
- HfsPlus
- OpenRuntime
- OpenLinuxBoot
- OpenCanopy
 
## [OS] macOS (Hackintosh)
This ESP contains OpenCore configured to run the following macOS, including what are works and what are not works.

### SMBIOS and Supported macOS
This OpenCore configuration only support **macOS Big Sur (11)**. The reasons are:

- APFS minimal version and minimal date are configured to support **at least macOS Big Sur and later**; and
- **MacBookPro11,2** is used as the SMBIOS, which support **only up to macOS Big Sur**.

If support for **macOS Catalina (10.15) or earlier** is required, set the APFS minimal version and minimal date
to the target macOS (the configuration value is available on OpenCore official documentation).

### Works on macOS
- [x] QE/CI Enabled Graphics of Intel® HD Graphics 4400 
- [x] Wi-Fi
- [x] Bluetooth
- [x] Touchpad
- [x] Touchscreen (on macOS Catalina and later, should use [Touch-Base UPDD](https://touch-base.com/drivers))
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
- [ ] Discrete Graphic of NVIDIA® GeForce® 820M (NVIDIA Optimus switchable graphic is not supported by hackintosh)
- [ ] Audio jack sensing for headset/speaker detection
- [ ] Audio input (internal mic)
- [ ] Audio output (external jack) distorted after sleep; must select an audio input in the Sound Preference Pane and 
keep the Sound Preference Pane open (otherwise, it will be distorted back when the Sound Preference Pane window is 
closed)

### macOS Kernel Extensions (Kext) Used
OpenCore loads the kernel extensions with a configured order. Unless specified, this kernel extensions are loaded for 
macOS Sierra (10.12) up to the latest macOS Monterey (12).

1. USBMap-MBP11,4 (for macOS Catalina and later)
2. USBMapLegacy-MBP11,4 (for macOS Mojave and earlier)
3. USBMap-MBP11,2 (for macOS Catalina and macOS Big Sur, **disabled** in favor of USBMap-MBP11,4)
4. USBMapLegacy-MBP11,2 (for macOS Mojave and earlier, **disabled** in favor of USBMapLegacy-MBP11,4)
5. AX88179-178A (for macOS Big Sur and later)
6. AX88179-178A-Legacy (for macOS Catalina and earlier)
7. Lilu
8. ECEnabler
9. WhateverGreen
10. VirtualSMC
11. SMCProcessor
12. SMCBatteryManager
13. SMCLightSensor
14. SMCSuperIO
15. AsusSMC
16. CPUFriend
17. CPUFriendDataProvider
18. VoodooPS2Controller
19. VoodooInput
20. VoodooPS2Mouse
21. VoodooPS2Trackpad
22. VoodooPS2Keyboard
23. NoTouchID (for macOS Mojave and earlier)
24. AppleALC
25. AirportBrcmFixup
26. AirPortBrcmNIC_Injector
27. BlueToolFixup (for macOS Monterey and later)
28. BrcmFirmwareData
29. BrcmBluetoothInjector (for macOS Catalina and later)
30. BrcmPatchRAM2 (for macOS Mojave and earlier)
31. BrcmPatchRAM3 (for macOS Catalina and later)
32. FeatureUnlock

**Note**: if **MacBookPro11,2** SMBIOS is used, enable USBMap-MBP11,2 or USBMapLegacy-MBP11,2 instead (and disable 
USBMap-MBP11,4 and USBMapLegacy-MBP11,4).

## [OS] Other Operating Systems
OpenCore is configured to support other operating systems as well. Tested on Windows 10, Windows 11, Fedora 34, 
Fedora 35, Ubuntu 20.04, Ubuntu 21.10 and Zorin OS 16, all components are working okay.

## Legal
This repository is owned and authored by **Danang Galuh Tegar Prasetyo** - [danang-id](https://github.com/danang-id),
and is licensed under the BSD 3-Clause License - see the [LICENSE.md](LICENSE.md) file for details.
