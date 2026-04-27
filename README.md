# Asus ROG Strix GL503GE Hackintosh - OpenCore

![Screenshot](https://imgur.com/6C59RBT.png)

> [!WARNING]
> I take no responsibility if your laptop or hardware is damaged when using this config. Proceed at your own risk.

---

## System Specs

| Component | Details |
| ---: | :--- |
| `CPU` | Intel Core i7-8750H (Coffee Lake) |
| `iGPU` | Intel UHD Graphics 630 |
| `dGPU` | NVIDIA GTX 1050 Ti (disabled, unsupported in macOS) |
| `RAM` | 16GB DDR4 |
| `Storage` | (fill in your SSD model) |
| `WiFi / BT` | (fill in your card model) |
| `Audio` | Realtek ALC294 |
| `Display` | 15.6" 1080p IPS |

---

## Versions

| | Version |
| ---: | :--- |
| `OpenCore` | 0.7.2 (RELEASE) |
| `macOS` | Big Sur 11.6.2 (20G314) |

> **Note:** This EFI was built for Big Sur and has not been tested on Monterey or newer. Coffee Lake hardware (i7-8750H + UHD 630) is theoretically compatible up to macOS Ventura with OpenCore 0.9.x+. Upgrading requires updating all kexts and the bootloader. Do your own research before attempting.

---

## What's Working

| Feature | Status |
| ---: | :--- |
| `iGPU (UHD 630)` | Working, with hardware acceleration |
| `CPU Power Management` | Working |
| `Sleep / Wake` | Working (see known issues below) |
| `USB Ports` | Working (mapped) |
| `Ethernet` | Working |
| `WiFi` | Working (itlwm.kext) |
| `Bluetooth` | Working (IntelBluetoothFirmware) |
| `Audio (speakers)` | Working (AppleALC) |
| `Audio (headphone jack)` | Working, requires sleep workaround first |
| `USB DAC / USB Headphone` | Working, no workaround needed |
| `Trackpad` | Working |
| `Battery Status` | Working |
| `HDMI Output` | Working, requires sleep workaround first |
| `iCloud / iMessage / FaceTime` | Working (requires valid SMBIOS serials) |

---

## Not Working / Disabled

| Feature | Status |
| ---: | :--- |
| `NVIDIA GTX 1050 Ti` | Disabled -- NVIDIA Optimus unsupported in macOS since Mojave |
| `Function Keys` | Not working (except volume keys) |
| `Mini DisplayPort` | Untested |
| `SD Card Reader` | (fill in if tested) |
| `Fingerprint Reader` | Not supported in macOS |

---

## Known Issues

1. **HDMI and headphone jack** -- the laptop must go to sleep and wake up at least once before these work correctly after a cold boot. USB audio devices work without this workaround.
2. **Function keys** -- all Fn keys are non-functional except the volume buttons.
3. **Mini DP** -- untested, status unknown.

---

## Post-Install Notes

- Generate your own SMBIOS serials using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) -- do not use the serials in this repo.
- Create a custom USBMap using [Hackintool](https://github.com/benbaker76/Hackintool) for your specific unit. You can disable `SSDT-USBX-LAPTOP` in `config.plist` once you have your own USB mapping kext.
- To enable WiFi: enable `itlwm.kext` in `config.plist`.
- To enable Bluetooth: enable `IntelBluetoothFirmware.kext` + `IntelBluetoothInjector.kext` in `config.plist`.

---

## Useful Resources

- [Dortania OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [Dortania Post-Install Guide](https://dortania.github.io/OpenCore-Post-Install/)
- [Dortania GPU Buyers Guide](https://dortania.github.io/GPU-Buyers-Guide/)
- [Olarila Forums](https://www.olarila.com/)
- [Mr. Macintosh](https://mrmacintosh.com/)
- [r/hackintosh (Reddit)](https://www.reddit.com/r/hackintosh/)
- [tonymacx86](https://www.tonymacx86.com/)
- [OpenCore Releases (Acidanthera)](https://github.com/acidanthera/OpenCorePkg/releases)
