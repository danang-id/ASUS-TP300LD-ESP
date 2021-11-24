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
This ESP contains [OpenCore](https://github.com/acidanthera/OpenCorePkg) version 0.7.5. The boot mode used 
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

If support for **macOS Monterey (12)** is required, **MacBookPro11,4** can be used as the SMBIOS instead.

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

1. USBPorts-MacBookPro11,2 (for macOS Big Sur and earlier)
2. USBPorts-MacBookPro11,4 (for macOS Monterey and later)
3. AX88179-178A (for macOS Big Sur and later)
4. AX88179-178A-Legacy (for macOS Catalina and earlier)
5. Lilu
6. ECEnabler
7. WhateverGreen
8. VirtualSMC
9. SMCProcessor
10. SMCBatteryManager
11. SMCLightSensor
12. SMCSuperIO
13. AsusSMC
14. CPUFriend
15. CPUFriendDataProvider
16. VoodooPS2Controller
17. VoodooInput
18. VoodooPS2Mouse
19. VoodooPS2Trackpad
20. VoodooPS2Keyboard
21. NoTouchID (for macOS Mojave and earlier)
22. AppleALC
23. AirportBrcmFixup
24. AirPortBrcmNIC_Injector
25. BlueToolFixup (for macOS Monterey and later)
26. BrcmFirmwareData
27. BrcmBluetoothInjector (for macOS Catalina and later)
28. BrcmPatchRAM2 (for macOS Mojave and earlier)
29. BrcmPatchRAM3 (for macOS Catalina and later)

## [OS] Other Operating Systems
OpenCore is configured to support other operating systems as well. Tested on Windows, Ubuntu, and Fedora, all 
components are working okay.

## Legal
This repository is owned and authored by **Danang Galuh Tegar Prasetyo** - [danang-id](https://github.com/danang-id),
and is licensed under the BSD 3-Clause License - see the [LICENSE.md](LICENSE.md) file for details.
