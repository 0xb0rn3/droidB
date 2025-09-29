# droidB

<div align="center">

![droidB Banner](https://img.shields.io/badge/droidB-Advanced%20Android%20Tool-blue?style=for-the-badge)

**Advanced ADB, Fastboot & Samsung Device Management Tool**

[![Version](https://img.shields.io/badge/version-0.1.1-blue.svg)](https://github.com/0xb0rn3/droidB/releases)
[![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey.svg)](https://github.com/0xb0rn3/droidB)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Shell](https://img.shields.io/badge/shell-bash-yellow.svg)](https://github.com/0xb0rn3/droidB)

*A security-focused, beginner-friendly automation tool for Android and Samsung devices*

[Features](#-features) • [Quick Start](#-quick-start) • [Installation](#-installation) • [Documentation](#-documentation) • [Support](#-support)

</div>

---

## ⚠️ Critical Safety Notice

> **WARNING:** This tool can permanently modify device firmware. **Always backup your data** before use and ensure you have official recovery images available.
>
> **Improper use can brick your device.** Read documentation carefully before proceeding.

---

## 🎯 What is droidB?

**droidB** is a powerful command-line tool that simplifies Android device management, debugging, and firmware operations. Whether you're a developer, security researcher, or power user, droidB provides an intuitive interface for:

- **Device Management**: Full ADB control with visual file explorer
- **Firmware Operations**: Flash custom ROMs, stock firmware, and recoveries
- **Samsung Specialization**: Native Odin4 and Heimdall support for Samsung devices
- **Backup & Recovery**: Complete device backups and app management
- **Security Operations**: Bootloader management and diagnostics

### Why Choose droidB?

✅ **Beginner-Friendly** - Menu-driven interface, no command memorization  
✅ **Drag & Drop** - Simply drag files into terminal for instant operations  
✅ **Safety First** - Multiple confirmations for dangerous operations  
✅ **Cross-Platform** - Works on Linux, macOS, and Windows (WSL)  
✅ **Samsung Expert** - Complete Odin/Download mode support  
✅ **Open Source** - MIT licensed, community-driven development

---

## ✨ Features

### 🔧 Core Capabilities

<table>
<tr>
<td width="50%">

**ADB Operations**
- Device information & diagnostics
- File push/pull with drag & drop
- APK installation & management
- Screenshot & screen recording
- System logs & debugging
- Wi-Fi debugging setup
- Backup & restore operations

</td>
<td width="50%">

**Fastboot Operations**
- Partition flashing & management
- Bootloader unlock/lock
- GSI (Generic System Image) flashing
- A/B slot management
- Custom recovery installation
- Wipe & format operations
- OEM-specific commands

</td>
</tr>
<tr>
<td width="50%">

**Samsung Operations**
- Complete firmware flashing (BL/AP/CP/CSC)
- Download mode auto-detection
- Odin4 & Heimdall integration
- Knox status checking
- PIT file operations
- Custom recovery flashing
- Bootloader management

</td>
<td width="50%">

**File Management**
- Interactive visual file explorer
- Batch push/pull operations
- Directory synchronization
- Real-time file browsing
- Permission management
- Path copying & navigation
- Multi-file selection

</td>
</tr>
</table>

---

## 🚀 Quick Start

### For Complete Beginners

**Step 1: Enable Developer Options on Your Device**

1. Go to **Settings** → **About Phone**
2. Tap **Build Number** 7 times rapidly
3. You'll see a message: "You are now a developer!"

**Step 2: Enable USB Debugging**

1. Go to **Settings** → **Developer Options**
2. Enable **USB Debugging**
3. Connect your device via USB cable
4. Authorize your computer on the device screen (important!)

**Step 3: Install and Run droidB**

```bash
# Download droidB
git clone https://github.com/0xb0rn3/droidB.git
cd droidB

# Make it executable
chmod +x droidB

# Run the tool
./droidB
```

That's it! The tool will guide you through the rest.

---

## 📥 Installation

### Method 1: Quick Install (Recommended)

```bash
# Clone the repository
git clone https://github.com/0xb0rn3/droidB.git
cd droidB

# Install system-wide (requires sudo)
sudo ./droidB --install

# Now run from anywhere
droidB
```

### Method 2: Portable Use

```bash
# Clone and make executable
git clone https://github.com/0xb0rn3/droidB.git
cd droidB
chmod +x droidB

# Run directly
./droidB
```

### Dependencies

droidB automatically installs missing dependencies. Manual installation:

**Debian/Ubuntu:**
```bash
sudo apt update
sudo apt install android-tools-adb android-tools-fastboot curl wget unzip
```

**Arch Linux:**
```bash
sudo pacman -S android-tools curl wget unzip
```

**macOS:**
```bash
brew install android-platform-tools curl wget
```

**Windows (WSL):**
```bash
# Install WSL first, then use Ubuntu commands above
```

---

## 📖 Beginner's Guide

### Understanding the Interface

When you launch droidB, you'll see a menu like this:

```
╔══════════════════════════════════════════════════════════╗
║                    droidB v0.1.1                         ║
║     Advanced Android & Samsung Device Manager            ║
╚══════════════════════════════════════════════════════════╝

Device: Samsung Galaxy S21 (device)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Main Menu:
  1. Device Information
  2. File Explorer (Visual)
  3. File Operations
  4. App Management
  5. System Operations
  6. Fastboot Mode
  7. Samsung Operations
  8. Device Backup/Restore
  9. Shell Access
  0. Settings & Tools
  q. Exit
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Common Tasks for Beginners

#### 📱 View Device Information
1. Select **Option 1** from main menu
2. See model, Android version, battery level, IP address

#### 📂 Browse Device Files
1. Select **Option 2** (File Explorer)
2. Navigate with numbers
3. **[p]** to push files (drag & drop supported)
4. **[..]** to go back, **[~]** for home directory

#### 📲 Install an APK
1. Select **Option 4** (App Management)
2. Choose **Option 1** (Install APK)
3. Drag the APK file into terminal OR type the path
4. Press Enter - done!

#### 📸 Take a Screenshot
1. Select **Option 3** (File Operations)
2. Choose **Option 5** (Screenshot)
3. File automatically saved to current directory

#### 💾 Backup Your Device
1. Select **Option 8** (Backup/Restore)
2. Choose **Option 1** (Full backup)
3. Wait for completion (may take 10-30 minutes)

---

## 🔧 Advanced Operations

### Samsung Device Operations

#### Entering Download Mode

**Method 1: Via ADB**
```bash
adb reboot download
```

**Method 2: Manual Entry**
1. Power off device completely
2. **Older devices**: Hold Volume Down + Home + Power
3. **Newer devices**: Hold Volume Down + Power
4. Press Volume Up when prompted

#### Flashing Samsung Firmware

1. Launch droidB: `./droidB --samsung`
2. Select **Option 1** (Flash Complete Firmware)
3. Drag and drop firmware files when prompted:
   - **BL** (Bootloader) - Optional
   - **AP** (System/PDA) - Required
   - **CP** (Modem) - Optional
   - **CSC** (Region) - Optional
   - **HOME_CSC** - Use this to keep data

4. Confirm warnings and wait for completion

**Important Notes:**
- Wrong firmware = bricked device
- Verify model number matches exactly
- Keep device charged above 50%
- Use original USB cable
- Don't interrupt the process

### Fastboot Operations

#### Unlocking Bootloader

```bash
./droidB --fastboot
# Select Option 3 → Option 1 (Unlock)
```

⚠️ **Warning:** Unlocking wipes ALL data!

#### Flashing Custom Recovery

```bash
./droidB --fastboot
# Select Option 2 (Boot image)
# Drag recovery.img file
```

#### Installing GSI (Generic System Image)

1. Prepare files:
   - GSI system image (ARM64 A/B)
   - Stock vbmeta.img
2. Boot to fastboot mode
3. Launch droidB: `./droidB --fastboot`
4. Select **Option 7** (Flash GSI)
5. Follow on-screen instructions

---

## 🛡️ Safety Features

### Built-in Protection

- **Triple Confirmation** for bootloader operations
- **Knox Bit Warnings** for Samsung devices
- **Region Mismatch Detection** prevents wrong firmware
- **Automatic Backup Reminders** before major operations
- **Model Verification** before flashing
- **USB Connection Stability** monitoring

### Understanding Warnings

| Warning | Meaning | Action |
|---------|---------|--------|
| 🔴 WIPES DATA | Operation deletes everything | Backup first |
| 🟡 Knox 0x1 | Samsung warranty void (permanent) | Understand implications |
| 🟠 BRICK RISK | Wrong firmware can kill device | Verify model number |
| 🔵 ROOT REQUIRED | Needs elevated permissions | Accept sudo prompt |

---

## 📚 Command Reference

### Basic Commands

```bash
droidB                    # Start interactive mode
droidB --help             # Show help information
droidB --version          # Show version
droidB --install          # Install system-wide
droidB --device SERIAL    # Connect to specific device
```

### Direct Access Commands

```bash
droidB --fastboot         # Jump to fastboot menu
droidB --samsung          # Jump to Samsung menu
droidB --shell            # Open ADB shell directly
```

### Device Preparation

```bash
# Check if device is connected
adb devices

# Reboot to different modes
adb reboot                # Normal reboot
adb reboot recovery       # Recovery mode
adb reboot bootloader     # Fastboot mode
adb reboot download       # Download mode (Samsung)
```

---

## 🔍 Troubleshooting

### Device Not Detected

**Problem:** `adb devices` shows empty or "unauthorized"

**Solutions:**
1. Check USB cable (use data cable, not charge-only)
2. Enable USB Debugging in Developer Options
3. Accept authorization prompt on device screen
4. Try different USB port (USB 2.0 works better)
5. Restart ADB server:
   ```bash
   adb kill-server
   adb start-server
   ```

### Samsung Download Mode Issues

**Problem:** Device not detected in download mode

**Solutions:**
1. Install Samsung USB drivers:
   ```bash
   droidB
   # Select 0 → 3 (Setup udev rules)
   ```
2. Try different USB port (direct motherboard connection)
3. Check cable quality (original Samsung cable recommended)
4. Verify download mode entry (screen should show warning)

### Fastboot Not Working

**Problem:** Device not showing in `fastboot devices`

**Solutions:**
1. Ensure device is in bootloader/fastboot mode
2. Some devices need `fastboot oem unlock` first
3. Windows users: Install fastboot drivers
4. Try: `sudo fastboot devices` (Linux/Mac)

### Flash Failed Errors

| Error | Cause | Solution |
|-------|-------|----------|
| FAIL! (Auth) | Wrong firmware region | Get correct region firmware |
| FAIL! (Remote) | Incompatible version | Check security patch level |
| Connection Lost | USB issue | Use different port/cable |
| Knox 0x1 | Already unlocked | Normal, continue |
| PIT Read Error | Corrupted partition | May need professional unbrick |

---

## 🎓 Learning Resources

### Understanding ADB

ADB (Android Debug Bridge) is a command-line tool for communicating with Android devices. droidB automates ADB commands with an easy interface.

**Key Concepts:**
- **Push**: Send files from computer to device
- **Pull**: Get files from device to computer
- **Shell**: Access device command line
- **Install**: Install APK applications
- **Logcat**: View system logs

### Understanding Fastboot

Fastboot is a protocol for modifying device firmware. Used for:
- Flashing system images
- Unlocking bootloader
- Installing custom recoveries
- Advanced device repair

### Samsung Download Mode

Samsung's proprietary firmware flashing mode. Features:
- Complete firmware installation
- Individual partition updates
- PIT (Partition Information Table) operations
- Emergency recovery

---

## 📱 Device Compatibility

### Samsung Devices

#### Fully Supported (Odin4 + Heimdall)
- Galaxy S7/S7 Edge through S10 series
- Galaxy Note 8 through Note 10
- Galaxy A series (A10-A50)
- Galaxy Tab A series

#### Odin4 Preferred
- Galaxy S20/S21/S22/S23/S24 series
- Galaxy Note 20 series
- Galaxy A series (A51+)
- Galaxy Tab S series

#### Important Notes
- **Knox 0x0**: Locked bootloader, warranty intact
- **Knox 0x1**: Custom software detected, warranty void (permanent)
- Exynos vs Snapdragon: Both supported with correct firmware

### Standard Android Devices

Works with all Android devices supporting:
- ADB over USB
- Fastboot protocol (for bootloader operations)
- Standard Android partition layout

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Reporting Issues
1. Check existing issues first
2. Provide device model and Android version
3. Include error messages and logs
4. Describe steps to reproduce

### Adding Device Support
1. Fork the repository
2. Test on your device
3. Update compatibility matrix
4. Submit pull request with results

### Code Contributions
1. Follow bash best practices
2. Add comments for complex operations
3. Test on multiple platforms
4. Update documentation

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) file for details.

### You are free to:
✅ Use commercially  
✅ Modify the code  
✅ Distribute  
✅ Use privately  

### You must:
📋 Include copyright notice  
📋 Include license text  

### Limitations:
❌ No liability from author  
❌ No warranty provided  

---

## 💬 Support & Community

### Get Help

- **General Issues**: [GitHub Issues](https://github.com/0xb0rn3/droidB/issues)
- **Samsung Support**: [Samsung Issues](https://github.com/0xb0rn3/droidB/issues?q=label%3Asamsung)
- **Discussions**: [GitHub Discussions](https://github.com/0xb0rn3/droidB/discussions)

### Useful Resources

**Firmware Sources:**
- [SamMobile](https://www.sammobile.com/firmware/) - Samsung firmware database
- [Frija Tool](https://forum.xda-developers.com/t/tool-frija-samsung-firmware-downloader-checker.3910594/) - Firmware downloader

**Community:**
- [XDA Developers](https://forum.xda-developers.com/) - Android development forum
- [Full Wiki](https://github.com/0xb0rn3/droidB/wiki) - Complete documentation

---

## ⚖️ Legal Disclaimer

### Intended Use
This tool is provided for:
- ✅ Educational purposes
- ✅ Software development
- ✅ Authorized device testing
- ✅ Personal device modification
- ✅ Security research

### User Responsibility
Users are responsible for:
- ⚠️ Compliance with local laws
- ⚠️ Device warranty status
- ⚠️ Data backup and loss
- ⚠️ Any device damage
- ⚠️ Proper authorization for device access

### Warranty Notice
- Samsung Knox 0x1 **permanently voids warranty**
- Bootloader unlocking voids warranty on most devices
- Flashing custom firmware may void warranty
- Check manufacturer policies before proceeding

---

## 🎯 Quick Tips for Success

### ✅ Best Practices

1. **Always Backup** - Before any major operation
2. **Verify Model Numbers** - Double-check firmware matches device
3. **Charge Device** - Keep above 50% battery
4. **Use Good Cables** - Original manufacturer cables preferred
5. **Be Patient** - Some operations take 20+ minutes
6. **Read Warnings** - Every warning is there for a reason
7. **Test with Simple Tasks First** - Get comfortable before advanced operations

### ❌ Common Mistakes to Avoid

1. ❌ Interrupting firmware flash
2. ❌ Wrong firmware region
3. ❌ Insufficient battery charge
4. ❌ Poor quality USB cables
5. ❌ Not backing up data
6. ❌ Ignoring error messages
7. ❌ Rushing through confirmations

---

## 📊 Version History

### v0.1.1 (Current)
- ✨ Rebranded from PyDroidB to droidB
- 🎨 Enhanced UI with improved banner
- 📝 Updated developer information
- 💅 Polished user interface elements
- 🐛 Improved error messages
- 📢 Better visual feedback
- 📚 Enhanced documentation

### v0.1.0
- 🎉 Initial public release
- ⚡ Complete Odin4 integration
- 🔧 Heimdall support
- 📱 Samsung download mode auto-detection
- 🔐 Security-focused design
- 📂 Visual file explorer
- 🖱️ Drag & drop support

---

## 🙏 Acknowledgments

- **Samsung Open Source** - Download mode protocols
- **Odin4Linux Team** - Modern Odin implementation
- **Heimdall Project** - Cross-platform Samsung support
- **XDA Developers** - Android development community
- **SamMobile** - Firmware database and tools
- **AOSP** - Android Debug Bridge and Fastboot tools

---

## 👨‍💻 Developer

**Created by:** 0xbv1 | 0xb0rn3  
**GitHub:** [@0xb0rn3](https://github.com/0xb0rn3)  
**Project:** [droidB Repository](https://github.com/0xb0rn3/droidB)

---

<div align="center">

**Made with ❤️ by the Android security community**

[⬆ Back to Top](#droidb)

</div>
