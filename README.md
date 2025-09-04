# Pydroidb - Advanced ADB, Fastboot & Samsung Automation Tool

![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Shell](https://img.shields.io/badge/shell-bash-yellow.svg)
![Samsung](https://img.shields.io/badge/Samsung-Odin4%20%7C%20Heimdall-orange.svg)

> **⚠️ SAFETY WARNING**  
> This tool modifies device firmware and can cause permanent damage if used incorrectly. Always back up your data and have official recovery images available. **USE AT YOUR OWN RISK.**

## 🚀 Overview

**Pydroidb** is a comprehensive command-line automation tool for Android Debug Bridge (ADB), Fastboot operations, and **specialized Samsung device management**. It provides an intuitive menu-driven interface with integrated **Odin4** and **Heimdall** support for complete Samsung ecosystem control.

### ✨ Key Features

- **🔧 Complete ADB Integration** - Full device management and debugging capabilities
- **⚡ Advanced Fastboot Operations** - Bootloader manipulation, partition flashing, and recovery
- **📱 Samsung Device Mastery** - Integrated Odin4 and Heimdall for complete Samsung control
- **🔥 Download Mode Support** - Full Samsung download/Odin mode operations
- **📄 Firmware Management** - Flash stock firmware, custom ROMs, and recovery images
- **🛡️ Bootloader Operations** - Unlock, lock, and manage Samsung bootloaders safely
- **📁 Intelligent File Management** - Batch operations, APK installation, and directory synchronization
- **🖥️ System Diagnostics** - Battery monitoring, logcat analysis, and device information
- **🔒 Security-First Design** - Multiple confirmation prompts for dangerous operations
- **🌐 Cross-Platform Support** - Works on Linux, macOS, and Windows (with WSL)
- **📱 Multi-Device Support** - Automatic detection and selection of multiple connected devices

## 📋 Prerequisites

- **Operating System**: Linux, macOS, or Windows with WSL
- **Shell**: Bash 4.0 or later
- **Dependencies**: `adb`, `fastboot`, `odin4`, `heimdall` (auto-installed if missing)
- **Device Requirements**: Android device with USB debugging enabled OR Samsung device in download mode
- **Permissions**: Root/sudo access for initial setup and Samsung operations

## 🛠️ Installation

### Quick Start

```bash
# Clone the repository
git clone https://github.com/0xb0rn3/pydroidb.git

# Navigate to directory
cd pydroidb

# Make executable
chmod +x pydroidb

# Run the tool
./pydroidb
```

### Samsung Tools Installation

The tool automatically installs required Samsung utilities:

- **Odin4Linux** - Modern Odin implementation for Linux
- **Heimdall** - Cross-platform Samsung flashing tool
- **Samsung USB drivers** - Proper device recognition
- **udev rules** - Correct permissions for Samsung devices

## 🎯 Usage

### Basic Usage

```bash
# Standard execution
./pydroidb

# With verbose output
./pydroidb --verbose

# Samsung-specific mode
./pydroidb --samsung

# Check version
./pydroidb --version
```

### Device Preparation

#### Standard Android Devices
1. **Enable Developer Options:**
   - Go to Settings → About Phone
   - Tap "Build Number" 7 times

2. **Enable USB Debugging:**
   - Settings → Developer Options → USB Debugging

#### Samsung Download Mode
1. **Enter Download Mode:**
   - Power off device completely
   - Hold Volume Down + Power + Home (older devices)
   - Hold Volume Down + Power (newer devices)
   - Press Volume Up when prompted

2. **Connect via USB** - Tool will auto-detect Samsung devices

## 📖 Samsung Feature Documentation

### 🔥 Samsung Download Mode Operations

#### Firmware Flashing (Odin4 + Heimdall)
- **Complete firmware installation** with BL/AP/CP/CSC files
- **Selective partition flashing** - Individual component updates
- **Custom ROM installation** - LineageOS, OneUI modifications
- **Recovery flashing** - TWRP, CWM, Stock recovery
- **Bootloader management** - Version updates and downgrades

#### Advanced Samsung Features
- **PIT file support** - Partition table modifications
- **Combo firmware** - Engineering firmware for unbrick
- **Multi-CSC handling** - Region-specific firmware management
- **NAND operations** - Chip erase, bad block handling
- **Secure download** - Encrypted firmware support

### 🛡️ Samsung Security Operations

#### Bootloader Management
- **Bootloader unlock** - Enable custom firmware (⚠️ WIPES DATA)
- **Bootloader lock** - Restore security (⚠️ DANGEROUS WITH CUSTOM SOFTWARE)
- **Knox bit checking** - Warranty status verification
- **FRP unlock** - Factory Reset Protection bypass (authorized use only)
- **Binary counter** - Custom firmware installation tracking

#### Samsung-Specific Diagnostics
- **Download mode info** - Bootloader version, security status
- **Knox status** - Hardware fuse state verification
- **Warranty bit** - Tamper detection status
- **Region detection** - CSC and carrier information
- **Hardware revision** - Board version and manufacturing data

### 📱 Device-Specific Support

#### Tested Samsung Devices
- **Galaxy S Series** - S7 through S24 (including Edge/Plus variants)
- **Galaxy Note Series** - Note 8 through Note 20 Ultra
- **Galaxy A Series** - A10 through A54
- **Galaxy Tab Series** - Tab A, Tab S series
- **Galaxy Watch** - Watch 4, Watch 5 series

#### Bootloader Compatibility
- **Snapdragon variants** - US carrier models
- **Exynos variants** - International models
- **Legacy devices** - Galaxy S3 through S6
- **Modern devices** - A/B partition schemes
- **Secure boot** - Knox-enabled devices

## 🔧 Samsung Configuration

### Environment Variables

```bash
# Samsung-specific paths
export ODIN4_PATH="/usr/local/bin/odin4"
export HEIMDALL_PATH="/usr/local/bin/heimdall"
export SAMSUNG_DRIVERS_PATH="/usr/lib/samsung/"

# Download mode timeouts
export SAMSUNG_FLASH_TIMEOUT=1800
export SAMSUNG_PIT_TIMEOUT=300
export SAMSUNG_NAND_TIMEOUT=3600
```

### Samsung Device Profiles

Create `.pydroidb_samsung` config:

```bash
# Device-specific Samsung configurations
SAMSUNG_PROFILES=(
    "SM-G975F:timeout=1800:region=EUR:knox=enabled"
    "SM-N975F:timeout=2400:region=USA:knox=enabled"
    "SM-A515F:timeout=1200:region=ASIA:knox=disabled"
)

# Default flash settings
SAMSUNG_DEFAULT_NAND_ERASE=false
SAMSUNG_AUTO_REBOOT=true
SAMSUNG_VERIFY_FLASH=true
```

## 🛡️ Samsung Safety Features

### Critical Operation Protection
- **Triple confirmation** for bootloader operations
- **Knox bit warnings** - Warranty implications clearly stated
- **Region mismatch detection** - Prevents wrong firmware installation
- **Automatic backup suggestions** - Before major Samsung operations
- **Brick prevention** - Model verification before flashing

### Samsung-Specific Error Handling
- **Download mode recovery** - Automatic retry mechanisms
- **USB connection stability** - Advanced reconnection logic
- **Firmware verification** - Checksum validation before flash
- **Partition table backup** - PIT file preservation
- **Emergency download** - Recovery from soft bricks

## 📊 Samsung Operation Examples

### Complete Firmware Flash
```bash
# Using integrated Odin4
./pydroidb --samsung --operation=flash-firmware \
  --bl=BL_G975FXXS4CTL4.tar.md5 \
  --ap=AP_G975FXXS4CTL4.tar.md5 \
  --cp=CP_G975FXXS4CTL4.tar.md5 \
  --csc=CSC_OXM_G975FOXM4CTL4.tar.md5
```

### Custom Recovery Installation
```bash
# TWRP installation with vbmeta patching
./pydroidb --samsung --operation=flash-recovery \
  --recovery=twrp-3.7.0-galaxy-s10.img \
  --patch-vbmeta=true
```

### Bootloader Operations
```bash
# Unlock bootloader (advanced users)
./pydroidb --samsung --operation=unlock-bootloader \
  --confirm-data-wipe=true

# Check Knox status
./pydroidb --samsung --operation=knox-status
```

## 🔍 Samsung Troubleshooting

### Download Mode Issues
```bash
# Check Samsung drivers
./pydroidb --samsung --check-drivers

# Test download mode connection
sudo odin4 --detect

# Manual driver installation
sudo ./pydroidb --install-samsung-drivers
```

### Common Samsung Problems

| Issue | Solution |
|-------|----------|
| Device not detected | Check download mode entry, install drivers |
| Flash fails at 0% | Try different USB port, check cable |
| FAIL! (Auth) | Wrong firmware region or security version |
| Knox 0x1 | Bootloader already unlocked (permanent) |
| PIT read error | Device may need unbrick via recovery |

## 🚀 Samsung Integration Features

### Unified Tool Benefits
- **Single interface** - No need to switch between ADB, Odin, Heimdall
- **Automatic detection** - Tool selects best Samsung method
- **Cross-compatibility** - Odin4 and Heimdall backends
- **Safety checks** - Model verification across all Samsung operations
- **Progress tracking** - Real-time flash progress and status

### Advanced Samsung Workflows
```bash
# Complete Samsung restore workflow
1. Device info gathering
2. Firmware download and verification
3. Bootloader preparation
4. Partition backup (PIT)
5. Firmware flash with progress
6. Post-flash verification
7. Automatic reboot and setup
```

## 📱 Samsung Device Compatibility Matrix

### Galaxy S Series Support
| Model | Odin4 | Heimdall | Download Mode | Knox | Status |
|-------|--------|----------|---------------|------|--------|
| S7/S7 Edge | ✅ | ✅ | ✅ | ✅ | Full Support |
| S8/S8+ | ✅ | ✅ | ✅ | ✅ | Full Support |
| S9/S9+ | ✅ | ✅ | ✅ | ✅ | Full Support |
| S10 Series | ✅ | ✅ | ✅ | ✅ | Full Support |
| S20 Series | ✅ | ⚠️ | ✅ | ✅ | Odin4 Preferred |
| S21 Series | ✅ | ⚠️ | ✅ | ✅ | Odin4 Preferred |
| S22 Series | ✅ | ❌ | ✅ | ✅ | Odin4 Only |
| S23 Series | ✅ | ❌ | ✅ | ✅ | Odin4 Only |

### Samsung Tablet Support
- **Galaxy Tab A Series** - Full support both tools
- **Galaxy Tab S Series** - Odin4 preferred for newer models
- **Galaxy Tab Active** - Complete support with rugged features

## 🔒 Samsung Security Considerations

### Knox and Warranty
- **Knox 0x0** - Bootloader locked, warranty intact
- **Knox 0x1** - Custom software detected, warranty void
- **E-fuse blown** - Hardware-level modification marker
- **Rolling back** - Impossible to restore Knox 0x0 status

### Regional Firmware
- **CSC matching** - Critical for modem functionality
- **Multi-CSC** - Supports multiple regions
- **Binary version** - Security patch level requirements
- **Downgrade protection** - Prevents rollback attacks

## 🤝 Contributing

We welcome contributions, especially for Samsung device support!

### Samsung-Specific Development
```bash
git clone https://github.com/0xb0rn3/pydroidb.git
cd pydroidb
chmod +x pydroidb

# Test Samsung features
./pydroidb --test-samsung
./pydroidb --samsung --dry-run
```

### Adding New Samsung Models
1. Update device detection logic
2. Add model-specific flash parameters
3. Test download mode compatibility
4. Update documentation and compatibility matrix

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Samsung-Specific Support

- **Samsung Issues**: [Samsung Support Thread](https://github.com/0xb0rn3/pydroidb/issues?q=label%3Asamsung)
- **Download Mode Help**: [Download Mode Guide](https://github.com/0xb0rn3/pydroidb/wiki/Download-Mode)
- **Firmware Sources**: [SamMobile](https://www.sammobile.com/firmware/), [Frija](https://forum.xda-developers.com/t/tool-frija-samsung-firmware-downloader-checker.3910594/)

## 📈 Samsung Changelog

### v0.1.0 (Current - Samsung Integration)
- Added complete Odin4 integration
- Integrated Heimdall cross-platform support
- Samsung download mode auto-detection
- Unified Samsung firmware flashing
- Knox status checking and management
- Samsung-specific safety features
- Advanced partition management
- Multi-tool compatibility layer

## 🙏 Samsung Acknowledgments

- **Samsung Open Source** - For download mode protocols
- **Odin4Linux Team** - Modern Odin implementation
- **Heimdall Project** - Cross-platform Samsung support
- **XDA Developers** - Samsung development community
- **SamMobile** - Firmware database and tools

## 📱 Samsung Quick Reference

### Essential Samsung Commands
```bash
# Check download mode devices
./pydroidb --samsung --list-devices

# Flash complete firmware
./pydroidb --samsung --flash-firmware

# Install custom recovery
./pydroidb --samsung --flash-recovery

# Check bootloader status
./pydroidb --samsung --bootloader-info

# Emergency unbrick
./pydroidb --samsung --emergency-flash
```

---

**Made with ❤️ by [0xbv1 | 0xb0rn3](https://github.com/0xb0rn3)**

> **Samsung Disclaimer**: Samsung-specific operations may void warranty and trigger Knox security features. This tool is for educational, development, and authorized repair purposes. Always backup your device and understand the risks before performing any Samsung operations.
