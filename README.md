# Pydroidb - Advanced ADB & Fastboot Automation Tool

![Version](https://img.shields.io/badge/version-0.0.1-blue.svg)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Shell](https://img.shields.io/badge/shell-bash-yellow.svg)

> **⚠️ SAFETY WARNING**  
> This tool modifies device firmware and can cause permanent damage if used incorrectly. Always back up your data and have official recovery images available. **USE AT YOUR OWN RISK.**

## 🚀 Overview

**Pydroidb** is a comprehensive command-line automation tool for Android Debug Bridge (ADB) and Fastboot operations. It provides an intuitive menu-driven interface for managing Android devices, performing file operations, system diagnostics, and advanced bootloader manipulation.

### ✨ Key Features

- **🔧 Complete ADB Integration** - Full device management and debugging capabilities
- **⚡ Advanced Fastboot Operations** - Bootloader manipulation, partition flashing, and recovery
- **📁 Intelligent File Management** - Batch operations, APK installation, and directory synchronization
- **🖥️ System Diagnostics** - Battery monitoring, logcat analysis, and device information
- **🔒 Security-First Design** - Multiple confirmation prompts for dangerous operations
- **🌐 Cross-Platform Support** - Works on Linux, macOS, and Windows (with WSL)
- **📱 Multi-Device Support** - Automatic detection and selection of multiple connected devices

## 📋 Prerequisites

- **Operating System**: Linux, macOS, or Windows with WSL
- **Shell**: Bash 4.0 or later
- **Dependencies**: `adb` and `fastboot` (auto-installed if missing)
- **Device Requirements**: Android device with USB debugging enabled
- **Permissions**: Root/sudo access for initial setup

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

### Manual Installation

1. **Download the script:**
   ```bash
   wget https://raw.githubusercontent.com/0xb0rn3/pydroidb/main/pydroidb
   chmod +x pydroidb
   ```

2. **Install dependencies (if needed):**
   - **Ubuntu/Debian**: `sudo apt install android-tools-adb android-tools-fastboot`
   - **Fedora/CentOS**: `sudo dnf install android-tools`
   - **Arch Linux**: `sudo pacman -S android-tools`
   - **macOS**: `brew install android-platform-tools`

## 🎯 Usage

### Basic Usage

```bash
# Standard execution
./pydroidb

# With verbose output
./pydroidb --verbose

# Check version
./pydroidb --version
```

### Device Preparation

1. **Enable Developer Options:**
   - Go to Settings → About Phone
   - Tap "Build Number" 7 times

2. **Enable USB Debugging:**
   - Settings → Developer Options → USB Debugging

3. **Connect Device:**
   - Connect via USB cable
   - Authorize the computer when prompted

## 📖 Feature Documentation

### 🔍 Device Information

- **Real-time device detection** with automatic authorization status
- **Comprehensive device profiling** including:
  - Model, manufacturer, and serial number
  - Android version and SDK level
  - Bootloader and kernel information
  - Hardware architecture and specifications
  - Connection state and authorization status

### 📁 File Operations

#### Single File Operations
- **Push files to device** with progress tracking
- **Pull files from device** with size validation
- **APK installation** with package verification
- **Package uninstallation** with safety confirmations

#### Batch Operations
- **Directory synchronization** - Push/pull entire directories
- **Multiple APK installation** - Install all APKs in a directory
- **Smart file filtering** - Automatic file type detection
- **Progress tracking** - Real-time operation status

#### Package Management
- **List installed packages** with filtering options:
  - All packages
  - System packages only
  - User-installed packages
  - Enabled/disabled packages
- **Package information** extraction and display

### ⚙️ System Operations

#### Device Control
- **Reboot options:**
  - Normal system reboot
  - Recovery mode
  - Bootloader/fastboot mode
- **Wi-Fi management** - Enable/disable wireless connectivity
- **Battery monitoring** - Detailed power consumption analysis

#### Media Capture
- **Screenshots** - High-quality screen capture with timestamp
- **Screen recording** - Configurable quality and duration:
  - Standard quality (default)
  - High quality (8Mbps)
  - Low quality (2Mbps)
  - Duration: 1-180 seconds

#### System Diagnostics
- **Live logcat** with filtering options:
  - Filter by tag
  - Filter by priority level
  - Real-time log streaming
- **Interactive shell access** - Direct command execution
- **System property inspection** - Complete device configuration
- **Network information** - IP address detection and connectivity

### 🔥 Fastboot Operations

> **⚠️ EXTREME CAUTION REQUIRED**  
> Fastboot operations can permanently damage your device. Ensure you have:
> - Correct firmware files for your exact device model
> - Official recovery images
> - Complete device backup

#### Partition Management
- **Flash individual partitions** - Boot, recovery, system, etc.
- **Erase partitions** - Selective data removal
- **Format partitions** - Filesystem recreation (ext4, f2fs)
- **Flash all partitions** - Complete firmware installation

#### Bootloader Operations
- **Unlock bootloader** - Enable custom firmware (⚠️ WIPES DATA)
- **Lock bootloader** - Restore stock security (⚠️ DANGEROUS WITH CUSTOM SOFTWARE)
- **A/B slot management** - Set active boot slot
- **Device variable inspection** - Complete bootloader information

#### Advanced Features
- **Boot images** - Test kernels without flashing
- **Device wipe** - Factory reset via fastboot
- **OEM commands** - Manufacturer-specific operations
- **Recovery operations** - Custom recovery management

### 🚀 Advanced ADB Operations

#### Backup & Restore
- **Complete device backup** - Full system and data backup
- **Selective restore** - Choose specific components to restore
- **Bug report generation** - Comprehensive system diagnostics

#### Development Features
- **Wi-Fi debugging** - Wireless ADB connection setup
- **Screen mirroring** - Integration with scrcpy
- **Input simulation** - Automated testing support
- **Activity launching** - Direct app component access

## 🔧 Configuration

### Environment Variables

```bash
# Custom ADB path
export ADB_PATH="/custom/path/to/adb"

# Custom Fastboot path
export FASTBOOT_PATH="/custom/path/to/fastboot"

# Default timeouts (seconds)
export PYDROIDB_DEFAULT_TIMEOUT=60
export PYDROIDB_FILE_TIMEOUT=300
export PYDROIDB_BACKUP_TIMEOUT=3600
export PYDROIDB_FASTBOOT_TIMEOUT=600
```

### Device-Specific Settings

Create a `.pydroidb_config` file in your home directory:

```bash
# Device-specific configurations
DEVICE_CONFIGS=(
    "serial1:timeout=120:quality=high"
    "serial2:timeout=60:quality=standard"
)

# Default screenshot quality
SCREENSHOT_QUALITY="high"

# Default recording settings
RECORDING_QUALITY="standard"
RECORDING_DURATION=30
```

## 🛡️ Safety Features

### Multi-Layer Confirmations
- **Double confirmation** for destructive operations
- **Partition-specific warnings** for critical system areas
- **Automatic backup suggestions** before major operations

### Error Handling
- **Timeout protection** - Prevents infinite hanging
- **Command validation** - Syntax checking before execution
- **Graceful failure recovery** - Clean exit on errors

### Security Measures
- **Device authorization checking** - Prevents unauthorized access
- **File existence validation** - Prevents invalid operations
- **Permission verification** - Ensures proper access levels

## 🔍 Troubleshooting

### Common Issues

#### Device Not Detected
```bash
# Check USB debugging
adb devices

# Restart ADB server
adb kill-server
adb start-server

# Check device authorization
./pydroidb  # Will show authorization status
```

#### Permission Denied
```bash
# Check udev rules (Linux)
sudo usermod -a -G plugdev $USER

# Reload rules
sudo udevadm control --reload-rules
```

#### Fastboot Issues
```bash
# Check fastboot devices
fastboot devices

# Verify bootloader unlock
fastboot oem device-info
```

### Error Codes

| Code | Description | Solution |
|------|-------------|----------|
| 124  | Command timeout | Check device connection |
| 1    | Command failed | Review command syntax |
| 2    | File not found | Verify file paths |
| 3    | Permission denied | Check device authorization |

## 📊 Performance Optimization

### File Transfer Optimization
- **Automatic compression** for large files
- **Parallel transfers** where supported
- **Resume capability** for interrupted transfers
- **Bandwidth throttling** for network operations

### Memory Management
- **Efficient buffering** for large operations
- **Automatic cleanup** of temporary files
- **Memory monitoring** during intensive operations

## 🔗 Integration

### CI/CD Integration
```yaml
# GitHub Actions example
- name: Setup Android Device
  run: |
    chmod +x pydroidb
    ./pydroidb --batch --operation=install --file=app.apk
```

### Script Integration
```bash
#!/bin/bash
# Automated testing script
./pydroidb --batch --operation=screenshot --output=test_results/
./pydroidb --batch --operation=logcat --filter=TestTag > test.log
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Setup
```bash
git clone https://github.com/0xb0rn3/pydroidb.git
cd pydroidb
chmod +x pydroidb
./pydroidb --test  # Run test suite
```

### Code Style
- Follow bash best practices
- Use meaningful variable names
- Add comments for complex operations
- Test on multiple platforms

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔐 Security Policy

Please report security vulnerabilities to [security@example.com](mailto:security@example.com).

## 🆘 Support

- **Issues**: [GitHub Issues](https://github.com/0xb0rn3/pydroidb/issues)
- **Discussions**: [GitHub Discussions](https://github.com/0xb0rn3/pydroidb/discussions)
- **Documentation**: [Wiki](https://github.com/0xb0rn3/pydroidb/wiki)

## 📈 Changelog

### v0.0.1 (Current)
- Initial release
- Complete ADB and Fastboot integration
- Multi-device support
- Cross-platform compatibility
- Safety features and confirmations

## 🙏 Acknowledgments

- **Android Open Source Project** - For ADB and Fastboot tools
- **Community Contributors** - For testing and feedback
- **Security Researchers** - For vulnerability disclosure

## 📱 Device Compatibility

### Tested Devices
- Google Pixel series
- Samsung Galaxy series
- OnePlus devices
- Xiaomi devices
- Generic Android devices

### Bootloader Support
- Unlocked bootloaders
- Custom recovery (TWRP, CWM)
- A/B partition schemes
- Legacy partition layouts

---

**Made with ❤️ by [0xbv1 | 0xb0rn3](https://github.com/0xb0rn3)**

> **Disclaimer**: This tool is for educational and development purposes. Always backup your data and understand the risks before performing any operations on your device.