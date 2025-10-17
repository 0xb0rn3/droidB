# droidB

<div align="center">

![droidB Banner](https://img.shields.io/badge/droidB-Advanced%20Android%20Tool-blue?style=for-the-badge)

**Advanced ADB, Fastboot & Samsung Device Management Tool with Universal Debloater**

[![Version](https://img.shields.io/badge/version-0.2.0-blue.svg)](https://github.com/0xb0rn3/droidB/releases)
[![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey.svg)](https://github.com/0xb0rn3/droidB)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Shell](https://img.shields.io/badge/shell-bash-yellow.svg)](https://github.com/0xb0rn3/droidB)

*A security-focused, beginner-friendly automation tool for Android and Samsung devices*

[Features](#-features) • [Quick Start](#-quick-start) • [Installation](#-installation) • [Debloater](#-universal-debloater) • [Documentation](#-documentation) • [Support](#-support)

</div>

---

## ⚠️ Critical Safety Notice

> **WARNING:** This tool can permanently modify device firmware and remove system applications. **Always backup your data** before use and ensure you have official recovery images available.
>
> **Improper use can brick your device.** Read documentation carefully before proceeding.

---

## 🎯 What is droidB?

**droidB** is a powerful command-line tool that simplifies Android device management, debugging, and firmware operations. Whether you're a developer, security researcher, or power user, droidB provides an intuitive interface for:

- **Universal Debloater**: Remove 100+ bloatware packages with one click
- **Device Management**: Full ADB control with visual file explorer
- **Firmware Operations**: Flash custom ROMs, stock firmware, GSI, and recoveries
- **Samsung Specialization**: Native Odin4 and Heimdall support for Samsung devices
- **Backup & Recovery**: Complete device backups and app management
- **Security Operations**: Bootloader management and diagnostics

### Why Choose droidB?

✅ **Beginner-Friendly** - Menu-driven interface, no command memorization  
✅ **Universal Debloater** - Remove bloatware with embedded lists (100+ packages)  
✅ **Drag & Drop** - Simply drag files into terminal for instant operations  
✅ **Safety First** - Multiple confirmations for dangerous operations  
✅ **Cross-Platform** - Works on Linux, macOS, and Windows (WSL)  
✅ **Samsung Expert** - Complete Odin/Download mode support  
✅ **GSI Support** - Full Generic System Image flashing with Treble detection  
✅ **Open Source** - MIT licensed, community-driven development

---

## ✨ Features

### 🗑️ Universal Debloater (NEW!)

<table>
<tr>
<td width="50%">

**One-Click Bloatware Removal**
- 100+ embedded bloatware packages
- Amazon, Facebook, Google apps
- Samsung bloat (Bixby, Knox, etc.)
- Microsoft Office suite
- Carrier bloatware
- Social media & streaming apps
- Game services & fonts

</td>
<td width="50%">

**Smart Debloat Features**
- Preview packages before removal
- Category-based selective removal
- Scan device for bloatware
- One-click revert/restore
- Backup creation
- Custom list support
- Non-destructive (keeps data)
- Safe uninstall (user-level only)

</td>
</tr>
</table>

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
- Project Treble detection
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
sudo apt install android-tools-adb android-tools-fastboot curl wget unzip xz-utils
```

**Arch Linux:**
```bash
sudo pacman -S android-tools curl wget unzip xz
```

**macOS:**
```bash
brew install android-platform-tools curl wget xz
```

**Windows (WSL):**
```bash
# Install WSL first, then use Ubuntu commands above
```

---

## 🗑️ Universal Debloater

### What is Bloatware?

Bloatware refers to pre-installed apps that:
- Cannot be uninstalled normally
- Consume system resources
- Run in the background
- Drain battery
- Take up storage space
- May collect data

### Using the Debloater

#### Quick Start: One-Click Debloat

```bash
./droidB

# Select Option 2: Universal Debloater
# Then Option 1: Debloat with embedded list
```

This removes all 100+ bloatware packages in one go!

#### Menu Structure

When you open the Universal Debloater, you'll see:

```
🗑️  UNIVERSAL DEBLOATER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Device: Samsung Galaxy S21 (device)
Serial: 1234567890ABCDEF
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Embedded bloatware list: 100 packages

1. Debloat with embedded list (recommended)
2. Debloat with custom list file
3. Preview embedded debloat list
4. Selective debloat (choose apps)
5. Scan device for bloatware
6. Revert/Restore debloated apps
7. Create backup before debloat
8. Export embedded list to file
9. Back to main menu
```

### Debloat Options Explained

#### 1. Debloat with Embedded List (Recommended)

**What it does:** Removes all 100+ bloatware packages automatically

**Perfect for:** Users who want to clean their device quickly

**Process:**
```bash
# Select option 1
# Confirm the action
# Wait for completion (1-5 minutes)
# Optionally reboot device
```

**Example Output:**
```
Starting debloat process...
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Processing: com.facebook.katana... [✓ REMOVED]
Processing: com.samsung.android.bixby.agent... [✓ REMOVED]
Processing: com.google.android.apps.docs... [✓ REMOVED]
Processing: com.amazon.kindle... [- NOT FOUND]
...

Debloat Summary:
  ✓ Successfully removed: 67 packages
  ✗ Failed to remove: 3 packages
  - Not found on device: 30 packages
```

#### 2. Debloat with Custom List

**What it does:** Use your own list of packages to remove

**Perfect for:** Advanced users with specific needs

**Usage:**
```bash
# Create a text file with package names (one per line)
# Example: my_bloat.txt
com.example.app1
com.example.app2
# Lines starting with # are comments

# Select option 2
# Drag and drop your file or type the path
```

#### 3. Preview Embedded List

**What it does:** View all packages that will be removed

**Perfect for:** Checking before you debloat

**Categories included:**
- Amazon bloatware (Kindle, Shopping, etc.)
- Facebook apps (Facebook, Messenger, services)
- Google apps (Docs, Maps, Photos, YouTube, etc.)
- Microsoft Office (Excel, Word, PowerPoint, Outlook)
- Samsung bloat (Bixby, Game Launcher, Tips, etc.)
- Social media (LinkedIn, Spotify, Netflix, etc.)
- System bloat (ANT+, Print services, etc.)

#### 4. Selective Debloat

**What it does:** Remove specific categories of bloatware

**Perfect for:** Users who want fine control

**Categories available:**
```
1. Amazon bloatware (5 packages)
2. Facebook apps (4 packages)
3. Google apps (20+ packages)
4. Microsoft Office (7 packages)
5. Samsung bloatware (30+ packages)
6. Bixby services (4 packages)
7. Custom package names (manual entry)
```

**Example:**
```bash
# Select option 4
# Choose "2" for Facebook apps
# Confirms removal of:
#   - com.facebook.appmanager
#   - com.facebook.katana
#   - com.facebook.services
#   - com.facebook.system
```

#### 5. Scan Device for Bloatware

**What it does:** Checks which bloatware is on your device

**Perfect for:** Seeing what you can remove

**Example Output:**
```
Scanning device...
[FOUND] com.amazon.kindle
[FOUND] com.facebook.katana
[FOUND] com.samsung.android.bixby.agent
[FOUND] com.google.android.apps.docs
...

Found 67 bloatware packages on device
```

#### 6. Revert/Restore

**What it does:** Restore previously removed apps

**Perfect for:** If you removed something you needed

**Options:**
- Restore all from embedded list
- Restore specific packages

**Important Notes:**
- Only system apps can be restored
- Third-party apps need reinstallation
- Some apps may require factory reset to restore

#### 7. Create Backup

**What it does:** Saves list of all installed packages

**Perfect for:** Safety before debloating

**Creates:** Text file with all package names and device info

#### 8. Export List

**What it does:** Save embedded list to a file

**Perfect for:** Creating your own custom list

**Usage:**
```bash
# Select option 8
# File saved as: droidb_debloat_list_20250117.txt
# Edit this file to customize your debloat list
```

### Safety & Considerations

#### ✅ Safe to Remove

The embedded list contains only bloatware that is generally safe to remove:
- Pre-installed apps from manufacturers
- Carrier apps
- Promotional apps
- Redundant system services
- Social media apps

#### ⚠️ What's NOT Removed

droidB will NOT remove critical system components:
- Core Android services
- System UI
- Phone/Dialer apps
- Settings
- System frameworks
- Device-specific drivers

#### 🔒 How It Works

```bash
# Command used: pm uninstall -k --user 0 <package>
# This means:
# - Uninstalls for current user only (not system-wide)
# - Keeps app data (-k flag)
# - Non-destructive removal
# - Can be restored later
```

#### 💡 Best Practices

1. **Always backup first** (use option 7)
2. **Preview the list** (use option 3)
3. **Scan your device** (use option 5) to see what you have
4. **Start selective** (use option 4) if unsure
5. **Reboot after debloat** for best results
6. **Keep notes** of what you removed

#### 🚨 If Something Goes Wrong

```bash
# Option 1: Restore apps
./droidB
# Select Option 2 → Option 6 → Restore

# Option 2: Factory reset
# Settings → System → Reset → Factory reset

# Option 3: Re-flash firmware
# (Only if device won't boot)
```

### Bloatware Categories Explained

#### Amazon Bloatware
- **com.amazon.kindle** - Kindle e-reader app
- **com.amazon.mp3** - Amazon Music
- **com.amazon.mShop.android** - Amazon Shopping

#### Facebook Bloatware
- **com.facebook.katana** - Facebook app
- **com.facebook.services** - Facebook background services
- **com.facebook.appmanager** - Facebook app manager
- **com.facebook.system** - Facebook system integration

#### Google Bloatware
- **Gmail, Maps, Photos, YouTube** - Google apps
- **Google Play Books, Music, Movies**
- **Google Assistant services**
- **Google Feedback & Analytics**

#### Samsung Bloatware
- **Bixby** - Samsung voice assistant (4 services)
- **Samsung Browser** - Alternative to Chrome
- **Samsung Email** - Email client
- **Samsung Calendar** - Calendar app
- **Game Launcher** - Gaming features
- **Samsung Pass** - Password manager
- **Samsung Pay** - Mobile payment

#### Microsoft Bloatware
- **Office apps** - Excel, Word, PowerPoint, Outlook
- **OneDrive** - Cloud storage
- **App Manager** - Microsoft services

---

## 📖 Beginner's Guide

### Understanding the Interface

When you launch droidB, you'll see a menu like this:

```
╔══════════════════════════════════════════════════════════╗
║                                                          ║
║     ██████╗ ██████╗  ██████╗ ██╗██████╗ ██████╗        ║
║     ██╔══██╗██╔══██╗██╔═══██╗██║██╔══██╗██╔══██╗       ║
║     ██║  ██║██████╔╝██║   ██║██║██║  ██║██████╔╝       ║
║     ██║  ██║██╔══██╗██║   ██║██║██║  ██║██╔══██╗       ║
║     ██████╔╝██║  ██║╚██████╔╝██║██████╔╝██████╔╝       ║
║     ╚═════╝ ╚═╝  ╚═╝ ╚═════╝ ╚═╝╚═════╝ ╚═════╝        ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝
    Advanced Android Device Manager v0.2.1
    Universal Debloater | Samsung Tools | Security-Focused
    Developer: 0xbv1 | 0xb0rn3
    GitHub: https://github.com/0xb0rn3/droidB
════════════════════════════════════════════════════════════
Device: Samsung Galaxy S21 (device)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Main Menu:
  1. Device Information
  2. Universal Debloater 🗑️
  3. App Management
  4. File Operations
  5. System Operations
  6. Fastboot Operations
  7. Samsung Operations
  8. Install System-Wide
  q. Exit
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Common Tasks for Beginners

#### 🗑️ Remove Bloatware (NEW!)
1. Select **Option 2** (Universal Debloater)
2. Choose **Option 5** to scan your device first
3. Review what bloatware you have
4. Select **Option 1** to remove all bloatware
5. Reboot device when prompted

#### 📱 View Device Information
1. Select **Option 1** from main menu
2. See model, Android version, battery level, IP address

#### 📲 Install an APK
1. Select **Option 3** (App Management)
2. Choose **Option 1** (Install APK)
3. Drag the APK file into terminal OR type the path
4. Press Enter - done!

#### 📸 Take a Screenshot
1. Select **Option 4** (File Operations)
2. Choose **Option 3** (Screenshot)
3. File automatically saved to current directory

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

1. Launch droidB: `./droidB`
2. Select **Option 7** (Samsung Operations)
3. Select **Option 1** (Flash Complete Firmware)
4. Drag and drop firmware files when prompted:
   - **BL** (Bootloader) - Optional
   - **AP** (System/PDA) - Required
   - **CP** (Modem) - Optional
   - **CSC** (Region) - Optional
   - **HOME_CSC** - Use this to keep data
5. Confirm warnings and wait for completion

**Important Notes:**
- Wrong firmware = bricked device
- Verify model number matches exactly
- Keep device charged above 50%
- Use original USB cable
- Don't interrupt the process

### Fastboot Operations

#### Unlocking Bootloader

```bash
./droidB
# Select Option 6 (Fastboot Operations)
# Select Option 3 (Unlock bootloader)
```

⚠️ **Warning:** Unlocking wipes ALL data!

#### Flashing Custom Recovery

```bash
./droidB
# Select Option 6 (Fastboot Operations)
# Select Option 2 (Boot image)
# Drag recovery.img file
```

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

### Debloater Issues

| Problem | Solution |
|---------|----------|
| "Failed to remove" packages | Package may be protected, try selective removal |
| Can't restore apps | Some apps require factory reset |
| Device sluggish after debloat | Reboot device |
| Removed wrong app | Use Option 6 to restore |

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

---

## 📱 Device Compatibility

### Universal Debloater Compatibility

**Works on ALL Android devices with:**
- ✅ USB Debugging enabled
- ✅ ADB access
- ✅ Android 4.4+

**Tested on:**
- Samsung Galaxy series
- Google Pixel devices
- OnePlus devices
- Xiaomi devices
- Motorola devices
- Most Android devices

### Samsung Devices

#### Fully Supported (Odin4 + Heimdall)
- Galaxy S7/S7 Edge through S24 series
- Galaxy Note 8 through Note 20
- Galaxy A series (A10-A73)
- Galaxy Tab A series

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Reporting Issues

1. Check existing issues first
2. Provide device model and Android version
3. Include error messages and logs
4. Describe steps to reproduce

### Adding Bloatware Packages

Found bloatware not in our list?

1. Fork the repository
2. Add package name to embedded list
3. Test on your device
4. Submit pull request

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) file for details.

---

## 💬 Support & Community

### Get Help

- **General Issues**: [GitHub Issues](https://github.com/0xb0rn3/droidB/issues)
- **Debloater Support**: [Debloater Issues](https://github.com/0xb0rn3/droidB/issues?q=label%3Adebloater)
- **Samsung Support**: [Samsung Issues](https://github.com/0xb0rn3/droidB/issues?q=label%3Asamsung)
- **Discussions**: [GitHub Discussions](https://github.com/0xb0rn3/droidB/discussions)

### Useful Resources

**Bloatware Info:**
- [Android Bloatware List](https://github.com/0xb0rn3/android-debloat-list) - Comprehensive package database
- [XDA Debloat Guide](https://forum.xda-developers.com/) - Community debloat threads

**Firmware Sources:**
- [SamMobile](https://www.sammobile.com/firmware/) - Samsung firmware database
- [XDA Developers](https://forum.xda-developers.com/) - Android development forum

---

## 📊 Version History

### v0.2.1 (Current - Latest | Stable)
- 🗑️ **NEW: Universal Debloater**
  - 100+ embedded bloatware packages
  - One-click removal
  - Category-based selective removal
  - Scan & preview features
  - Revert/restore functionality
  - Custom list support
  - Safe, non-destructive removal
- 🔧 Enhanced Samsung operations
- 📱 Improved device detection
- 🐛 Bug fixes and stability improvements
- 📚 Comprehensive documentation

### v0.1.1
- ✨ Complete GSI flashing system
- 🔍 Automatic Project Treble detection
- 🛡️ Pre-flight safety checks
- 📦 Compressed image support (.img.xz)
- 🎨 Step-by-step progress indicators
- 📝 Comprehensive flash logging

### v0.1.0
- 🎉 Initial public release
- ⚡ Complete Odin4 integration
- 🔧 Heimdall support
- 📱 Samsung download mode auto-detection
- 🔐 Security-focused design
- 📂 Visual file explorer

---

## 🎯 Quick Tips for Success

### ✅ Best Practices

1. **Backup First** - Create package backup before debloating
2. **Preview List** - Review what will be removed
3. **Start Selective** - Try category removal first if unsure
4. **Reboot After** - Always reboot after debloating
5. **Take Notes** - Remember what you removed
6. **Test Apps** - Ensure everything works after debloat

### ❌ Common Mistakes to Avoid

1. ❌ Not backing up package list
2. ❌ Removing apps without knowing what they do
3. ❌ Not rebooting after debloat
4. ❌ Panicking if something doesn't work (just restore!)

---

## 🙏 Acknowledgments

- **Samsung Open Source** - Download mode protocols
- **Odin4Linux Team** - Modern Odin implementation
- **Heimdall Project** - Cross-platform Samsung support
- **XDA Developers** - Android development community
- **Android Debloat Community** - Bloatware package lists
- **AOSP** - Android Debug Bridge and Fastboot tools

---

## 👨‍💻 Developer

**Created by:** 0xbv1 | 0xb0rn3  
**GitHub:** [@0xb0rn3](https://github.com/0xb0rn3)  
**Project:** [droidB Repository](https://github.com/0xb0rn3/droidB)

---

<div align="center">

**Made with ❤️ for the Android community**

**Star ⭐ this repo if droidB helped clean your device!**

[⬆ Back to Top](#droidb)

</div>
