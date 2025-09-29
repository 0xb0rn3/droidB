# droidB - Advanced ADB, Fastboot & Samsung Automation Tool

![Version](https://img.shields.io/badge/version-0.1.1-blue.svg)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Shell](https://img.shields.io/badge/shell-bash-yellow.svg)
![Samsung](https://img.shields.io/badge/Samsung-Odin4%20%7C%20Heimdall-orange.svg)

> **⚠️ SAFETY WARNING**  
> This tool modifies device firmware and can cause permanent damage if used incorrectly. Always back up your data and have official recovery images available. **USE AT YOUR OWN RISK.**

## 🚀 Overview

**droidB** is a comprehensive command-line automation tool for Android Debug Bridge (ADB), Fastboot operations, and **specialized Samsung device management**. It provides an intuitive menu-driven interface with integrated **Odin4** and **Heimdall** support for complete Samsung ecosystem control.

### ✨ Key Features

- **🔧 Complete ADB Integration** - Full device management and debugging capabilities
- **⚡ Advanced Fastboot Operations** - Bootloader manipulation, partition flashing, and recovery
- **📱 Samsung Device Mastery** - Integrated Odin4 and Heimdall for complete Samsung control
- **🔥 Download Mode Support** - Full Samsung download/Odin mode operations
- **📄 Firmware Management** - Flash stock firmware, custom ROMs, and recovery images
- **🛡️ Bootloader Operations** - Unlock, lock, and manage Samsung bootloaders safely
- **📁 Intelligent File Management** - Batch operations, APK installation, and directory synchronization
- **🖼️ Visual File Explorer** - Interactive device file browser with drag & drop support
- **🖥️ System Diagnostics** - Battery monitoring, logcat analysis, and device information
- **🔒 Security-First Design** - Multiple confirmation prompts for dangerous operations
- **🌐 Cross-Platform Support** - Works on Linux, macOS, and Windows (with WSL)
- **📱 Multi-Device Support** - Automatic detection and selection of multiple connected devices

## 👨‍💻 Developer

**Created by:** 0xbv1 | 0xb0rn3  
**GitHub:** [@0xb0rn3](https://github.com/0xb0rn3)  
**Project:** [droidB Repository](https://github.com/0xb0rn3/droidB)  
**License:** MIT

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
git clone https://github.com/0xb0rn3/droidB.git

# Navigate to directory
cd droidB

# Make executable
chmod +x droidB

# Run the tool
./droidB
```

### System-Wide Installation

```bash
# Install system-wide (recommended)
sudo ./droidB --install

# Now run from anywhere
droidB
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
./droidB

# With verbose output
./droidB --verbose

# Samsung-specific mode
./droidB --samsung

# Direct fastboot access
./droidB --fastboot

# Open ADB shell directly
./droidB --shell

# Check version
./droidB --version

# Show help
./droidB --help
```

### Device Preparation

#### Standard Android Devices
1. **Enable Developer Options:**
   - Go to Settings → About Phone
   - Tap "Build Number" 7 times

2. **Enable USB Debugging:**
   - Settings → Developer Options → USB Debugging

3. **Authorize Computer:**
   - Connect device via USB
   - Accept the authorization prompt on device screen

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

## 🔧 Configuration

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

### Device Profiles

Create `.droidB_config` for custom settings:

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

## 🛡️ Safety Features

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

## 📊 Operation Examples

### Complete Firmware Flash
```bash
# Interactive mode with drag & drop
droidB --samsung
# Select option 1: Flash Complete Firmware
# Drag & drop BL, AP, CP, CSC files when prompted
```

### Custom Recovery Installation
```bash
# Direct Samsung menu access
droidB --samsung
# Select option 2: Flash Custom Recovery
# Drag & drop TWRP/CWM image file
```

### File Management
```bash
# Launch file explorer
droidB
# Select option 2: File Explorer (Visual)
# Navigate with numbers, drag & drop files to push
```

### Fastboot Operations
```bash
# Direct fastboot access
droidB --fastboot
# Follow on-screen menu for flashing, unlocking, etc.
```

## 🔍 Troubleshooting

### Download Mode Issues
```bash
# Check Samsung drivers
droidB --samsung
# Select option 4: Detect Samsung Devices

# Test download mode connection
sudo odin4 --detect

# Reinstall drivers
droidB
# Select option 0: Settings & Tools
# Select option 3: Setup udev rules
```

### Common Problems

| Issue | Solution |
|-------|----------|
| Device not detected | Check download mode entry, install drivers |
| Flash fails at 0% | Try different USB port, check cable |
| FAIL! (Auth) | Wrong firmware region or security version |
| Knox 0x1 | Bootloader already unlocked (permanent) |
| PIT read error | Device may need unbrick via recovery |
| ADB unauthorized | Check device screen for authorization prompt |
| Fastboot not detected | Ensure device is in bootloader mode |

### ADB Connection Issues
```bash
# Restart ADB server
adb kill-server
adb start-server

# Check device authorization
adb devices

# Enable Wi-Fi debugging (Android 11+)
droidb
# Select option 3: System Operations
# Select option 9: Advanced ADB Operations
# Select option 10: Enable Wi-Fi Debugging
```

## 🚀 Advanced Features

### Drag & Drop Support
- **File pushing** - Simply drag files into terminal when prompted
- **APK installation** - Drag APK files for instant installation
- **Firmware flashing** - Drag Samsung firmware packages
- **Batch operations** - Drag entire directories

### Visual File Explorer
```bash
# Interactive device file browser
droidB
# Select option 2: File Explorer (Visual)

Features:
- Navigate with numbers
- Create directories with [m]
- Delete files/folders with [d]
- Push files with [p] or drag & drop
- Pull files by selecting them
- View file contents
- Copy paths to clipboard
```

### Batch Operations
```bash
# Batch push directory
droidB
# Select option 3: File Operations
# Select option 3: Batch Push Directory

# Batch pull directory
# Select option 4: Batch Pull Directory

# Install multiple APKs
# Select option 3: System Operations
# Select option 9: Advanced ADB Operations
# Select option 3: Install Multiple APKs
```

## 📱 Samsung Device Compatibility Matrix

### Galaxy S Series Support
| Model | Odin4 | Heimdall | Download Mode | Knox | Status |
|-------|--------|----------|---------------|------|--------|
| S7/S7 Edge | ✅ | ✅ | ✅ | ✅ | Full Support |
| S9/S9+ | ✅ | ✅ | ✅ | ✅ | Full Support |
| S10 Series | ✅ | ✅ | ✅ | ✅ | Full Support |
| S20 Series | ✅ | ⚠️ | ✅ | ✅ | Odin4 Preferred |
| S21 Series | ✅ | ⚠️ | ✅ | ✅ | Odin4 Preferred |
| S22 Series | ✅ | ❌ | ✅ | ✅ | Odin4 Only |
| S23 Series | ✅ | ❌ | ✅ | ✅ | Odin4 Only |
| S24 Series | ✅ | ❌ | ✅ | ✅ | Odin4 Only |

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

## 📚 Feature List

### ADB Operations
- Device information gathering
- File push/pull (single & batch)
- APK installation/uninstallation
- Package management
- Screenshot capture
- Screen recording
- Logcat viewing
- Shell access
- Battery information
- Network diagnostics
- System properties
- Backup/restore operations
- Wi-Fi debugging setup

### Fastboot Operations
- Partition flashing
- Partition erasing
- Partition formatting
- Temporary boot images
- Bootloader unlock/lock
- A/B slot management
- Device variable inspection
- Wipe operations
- OEM commands
- GSI flashing support

### Samsung Operations
- Complete firmware flashing (BL/AP/CP/CSC)
- Custom recovery installation
- Single partition updates
- PIT file operations
- Download mode detection
- Knox status checking
- Bootloader operations
- Emergency unbrick support

### File Management
- Interactive visual file explorer
- Drag & drop support
- Directory creation
- File deletion
- Path copying
- File viewing
- Permission checking
- Size reporting

## 🤝 Contributing

We welcome contributions, especially for Samsung device support!

### Development Setup
```bash
git clone https://github.com/0xb0rn3/droidB.git
cd droidB
chmod +x droidB

# Test Samsung features
./droidB --test-samsung
./droidB --samsung --dry-run
```

### Adding New Samsung Models
1. Update device detection logic in `detect_samsung_download_mode()`
2. Add model-specific flash parameters
3. Test download mode compatibility
4. Update documentation and compatibility matrix
5. Submit pull request with test results

### Code Style
- Use bash best practices
- Add comments for complex operations
- Maintain error handling
- Test on multiple platforms
- Follow existing naming conventions

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **General Issues**: [GitHub Issues](https://github.com/0xb0rn3/droidB/issues)
- **Samsung Support**: [Samsung Issues](https://github.com/0xb0rn3/droidB/issues?q=label%3Asamsung)
- **Download Mode Help**: [Download Mode Wiki](https://github.com/0xb0rn3/droidB/wiki/Download-Mode)
- **Discussions**: [GitHub Discussions](https://github.com/0xb0rn3/droidB/discussions)

### Useful Resources
- **Firmware Sources**: 
  - [SamMobile](https://www.sammobile.com/firmware/)
  - [Frija Tool](https://forum.xda-developers.com/t/tool-frija-samsung-firmware-downloader-checker.3910594/)
- **XDA Forums**: [droidB Thread](https://forum.xda-developers.com/)
- **Documentation**: [Full Wiki](https://github.com/0xb0rn3/droidB/wiki)

## 📈 Changelog

### v0.1.1 (Current)
- Rebranded from PyDroidB to droidB
- Enhanced UI with improved banner
- Updated developer information
- Polished user interface elements
- Improved error messages
- Better visual feedback
- Enhanced documentation

### v0.1.0 (Previous)
- Complete Odin4 integration
- Integrated Heimdall cross-platform support
- Samsung download mode auto-detection
- Unified Samsung firmware flashing
- Knox status checking and management
- Samsung-specific safety features
- Advanced partition management
- Multi-tool compatibility layer
- Visual file explorer
- Drag & drop support
- System-wide installation
- Bash completion

## 🙏 Acknowledgments

- **Samsung Open Source** - For download mode protocols
- **Odin4Linux Team** - Modern Odin implementation
- **Heimdall Project** - Cross-platform Samsung support
- **XDA Developers** - Samsung development community
- **SamMobile** - Firmware database and tools
- **Android Open Source Project** - ADB/Fastboot tools

## 📱 Quick Reference

### Essential Commands
```bash
# Installation
sudo ./droidB --install

# Check version
droidB --version

# Show help
droidB --help

# Direct modes
droidB --samsung        # Samsung operations
droidB --fastboot       # Fastboot operations
droidB --shell          # ADB shell

# Check device
adb devices
fastboot devices
```

### Samsung Quick Commands
```bash
# List Samsung download mode devices
droidB --samsung
# Select option 4

# Flash complete firmware
droidB --samsung
# Select option 1

# Install custom recovery
droidB --samsung
# Select option 2

# Check bootloader status
# Enter download mode first
droidB --samsung
```

### Emergency Procedures
```bash
# Soft brick recovery
1. Boot to download mode
2. droidB --samsung
3. Flash stock firmware

# Hard brick prevention
- Always verify firmware matches model
- Keep stock firmware available
- Never interrupt flash process
- Use correct USB ports (USB 2.0 preferred)
```

## 🎯 Best Practices

### Before Flashing
1. **Backup everything** - Use built-in backup features
2. **Verify firmware** - Check model number matches exactly
3. **Charge device** - Minimum 50% battery
4. **Use good cable** - Original Samsung cable preferred
5. **Disable antivirus** - May interfere with USB communication

### During Operations
1. **Don't interrupt** - Never disconnect during flash
2. **Watch for errors** - Monitor terminal output
3. **Be patient** - Some operations take 20+ minutes
4. **Keep device still** - Don't move or touch device

### After Flashing
1. **First boot** - May take 10-15 minutes
2. **Factory reset** - Often required after firmware change
3. **Verify functionality** - Test all features
4. **Re-root if needed** - Custom kernels/Magisk
5. **Restore data** - From backup

## ⚠️ Important Warnings

### Critical Safety Information
- **Data Loss**: Bootloader operations ALWAYS wipe data
- **Warranty**: Custom software voids Samsung warranty (Knox)
- **Brick Risk**: Wrong firmware = permanent damage
- **Irreversible**: Knox 0x1 cannot be reverted to 0x0
- **Region Lock**: Flashing wrong region may lock device

### Legal Disclaimer
This tool is provided for:
- Educational purposes
- Development and testing
- Authorized device repair
- Personal device modification

Users are responsible for:
- Compliance with local laws
- Device warranty status
- Data backup and loss
- Any device damage

## 🔗 Links

- **GitHub**: https://github.com/0xb0rn3/droidB
- **Developer**: [@0xb0rn3](https://github.com/0xb0rn3)
- **Issues**: https://github.com/0xb0rn3/droidB/issues
- **Wiki**: https://github.com/0xb0rn3/droidB/wiki
- **Releases**: https://github.com/0xb0rn3/droidB/releases

---

**Made with ❤️ by [0xbv1 | 0xb0rn3](https://github.com/0xb0rn3)**

> **Disclaimer**: Samsung-specific operations may void warranty and trigger Knox security features. This tool is for educational, development, and authorized repair purposes. Always backup your device and understand the risks before performing any operations. The developer is not responsible for any damage to your device. | ✅ | ✅ | Full Support |
| S8/S8+ | ✅ | ✅
