# Pydroidb 🤖

**A comprehensive ADB automation tool for Android device management**

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey.svg)](https://github.com/0xb0rn3/pydroidb)

> **⚠️ IMPORTANT SAFETY WARNING**  
> This tool deals with device firmware and system partitions. Incorrect usage can result in device boot loops or permanent damage. Always ensure you have proper recovery images before flashing and test commands on non-critical devices first.

## 🎯 Overview

Pydroidb is a powerful Python-based wrapper for ADB (Android Debug Bridge) and Fastboot commands, designed to simplify and safeguard Android device operations. Built with extensive safety checks and user-friendly interfaces, it provides both novice and advanced users with a comprehensive toolkit for Android device management.

### ✨ Key Features

- **🛡️ Safety First**: Built-in safety checks for critical operations
- **📱 Multi-Device Support**: Handle multiple connected devices seamlessly  
- **🔧 Comprehensive Operations**: File transfer, app management, system operations, and more
- **⚡ Fastboot Integration**: Full bootloader and firmware management capabilities
- **📊 Device Information**: Detailed device specs and system properties
- **💾 Backup & Restore**: Complete device backup and restore functionality
- **🔍 Advanced Debugging**: Logcat monitoring and shell access
- **📸 Media Capture**: Screenshots and screen recordings
- **🌐 Network Operations**: TCP/IP connections and port forwarding

## 🚀 Installation

### Prerequisites

- Python 3.7 or higher
- Android SDK Platform Tools (ADB and Fastboot)
- USB debugging enabled on target device

### Quick Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/0xb0rn3/pydroidb.git
   cd pydroidb
   ```

2. **Install Android SDK Platform Tools**
   
   **Linux/macOS:**
   ```bash
   # Using package manager
   sudo apt install android-tools-adb android-tools-fastboot  # Ubuntu/Debian
   yay -S android-sdk-platform-tools android-bash-completion  # ARCHLINUX
   brew install android-platform-tools  # macOS
   ```
   
   **Windows/Manual Installation:**
   - Download from [Android Developer Site](https://developer.android.com/studio/releases/platform-tools)
   - Extract and add to system PATH

3. **Enable USB Debugging**
   - Go to Settings > About Phone
   - Tap "Build Number" 7 times to enable Developer Options
   - Go to Settings > Developer Options > Enable USB Debugging

4. **Run Pydroidb**
   ```bash
   chmod +x pydroidb
   ./pydroidb
   ```

## 📋 Features Overview

### 🔌 Device Management
- **Auto-detection** of connected devices
- **Multi-device support** with device selection
- **Comprehensive device information** display
- **Connection state monitoring**

### 📁 File Operations
- **Push/Pull files** between device and computer
- **Directory listing** with detailed permissions
- **APK installation** and management
- **Package listing** and uninstallation
- **Batch file operations**

### ⚙️ System Operations
- **Device reboot** (normal, recovery, bootloader)
- **System properties** retrieval
- **Screenshot capture** with timestamp
- **Screen recording** with configurable duration
- **Real-time logcat** monitoring
- **Interactive shell access**

### 🔥 Fastboot Operations
> **⚠️ CRITICAL WARNING**: Fastboot operations modify bootloader and firmware. Incorrect usage can permanently damage your device!

- **Partition flashing** with safety checks
- **Partition erasing** with confirmation prompts
- **Bootloader unlock/lock** operations
- **Temporary boot** from images
- **Device variable** inspection
- **Critical partition** protection

### 💾 Backup & Restore
- **Full device backup** creation
- **Application-specific backups**
- **Backup restoration** with safety checks
- **Backup content** analysis
- **Progress monitoring** for large backups

### 🌐 Advanced Operations
- **TCP/IP connection** setup
- **Port forwarding** (local and reverse)
- **ADB server** management
- **Device architecture** information
- **Memory and CPU** statistics
- **USB debugging** status checks

## 🛡️ Safety Features

### Multi-Layer Protection
1. **Critical Partition Detection**: Automatic identification of system-critical partitions
2. **Confirmation Prompts**: Multi-step confirmation for dangerous operations
3. **File Validation**: Extension and size checks for firmware files
4. **Command Timeouts**: Automatic timeout for long-running operations
5. **Error Handling**: Comprehensive error catching and reporting

### Safety Mode
- **Always enabled** by default
- **Cannot be disabled** for critical operations
- **Extensive warnings** for dangerous commands
- **Automatic backups** before major operations

## 📖 Usage Examples

### Basic Device Information
```bash
# Launch Pydroidb
chmod +x pydroidb
./pydroidb

# Select option 1 to view device information
# The tool will display:
# - Device model and serial
# - Android version and SDK level
# - Bootloader version
# - Connection state
```

### File Operations
```bash
# Push file to device
Select: File Operations > Push file to device
Local file path: /home/user/file.txt
Device path: /sdcard/file.txt

# Install APK
Select: File Operations > Install APK
APK path: /home/user/app.apk
```

### System Operations
```bash
# Take screenshot
Select: System Operations > Take screenshot
# Screenshot saved as screenshot_[timestamp].png

# Screen recording
Select: System Operations > Screen recording
Duration: 30 seconds
# Recording saved as screenrecord_[timestamp].mp4
```

### Fastboot Operations
```bash
# WARNING: Only use if you understand the risks!
Select: Fastboot Operations > Flash partition
Partition: recovery
Image path: /path/to/recovery.img
# Multiple confirmation prompts will appear
```

## 🔧 Advanced Configuration

### Custom ADB/Fastboot Paths
The tool automatically detects ADB and Fastboot in common locations:
- `/usr/bin/adb` (Linux)
- `/usr/local/bin/adb` (macOS)
- `~/Android/Sdk/platform-tools/adb` (Manual installation)

### Timeout Configuration
Default timeouts can be adjusted in the source code:
- Standard commands: 30 seconds
- File operations: 120 seconds
- Backup operations: 3600 seconds (1 hour)
- Fastboot operations: 300 seconds

### Device Selection
For multiple devices, the tool provides an interactive selection menu:
```
Multiple devices connected:
1. ABC123456789 (device)
2. XYZ987654321 (device)
Select device (number): 1
```

## 🐛 Troubleshooting

### Common Issues

**"ADB not found" Error**
```bash
# Install Android SDK Platform Tools
sudo apt install android-tools-adb  # Linux
brew install android-platform-tools  # macOS
```

**"No devices connected"**
- Check USB cable and connection
- Verify USB debugging is enabled
- Try different USB port
- Check device authorization prompt

**"Device unauthorized"**
- Check device screen for authorization prompt
- Tap "OK" to authorize computer
- Ensure "Always allow from this computer" is checked

**Fastboot device not detected**
- Reboot device to bootloader mode
- Check device drivers (Windows)
- Try different USB cable
- Verify bootloader is unlocked (if required)

### Debug Mode
Enable verbose output by modifying the source:
```python
# In run_command method
print(f"Executing: {' '.join(command)}")  # Already enabled
```

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit your changes** (`git commit -m 'Add amazing feature'`)
4. **Push to the branch** (`git push origin feature/amazing-feature`)
5. **Open a Pull Request**

### Development Setup
```bash
git clone https://github.com/0xb0rn3/pydroidb.git
cd pydroidb
python3 -m venv venv
source venv/bin/activate  # Linux/macOS
# or
venv\Scripts\activate  # Windows
```

### Code Style
- Follow PEP 8 guidelines
- Use type hints where appropriate
- Add docstrings for all functions
- Include safety checks for dangerous operations

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

**USE AT YOUR OWN RISK**

This tool is provided as-is without any warranties. The authors are not responsible for any damage to devices, data loss, or other issues that may arise from using this tool. Always:

- Test on non-critical devices first
- Create backups before major operations
- Understand the commands you're executing
- Have recovery images available

## 🙏 Acknowledgments

- **Android Open Source Project** for ADB and Fastboot tools
- **Python Community** for excellent libraries and documentation
- **Android Developer Community** for extensive documentation and guides

## 📞 Support

- **GitHub Issues**: [Report bugs and request features](https://github.com/0xb0rn3/pydroidb/issues)
- **Discussions**: [Community discussions and help](https://github.com/0xb0rn3/pydroidb/discussions)
- **Documentation**: [Wiki and detailed guides](https://github.com/0xb0rn3/pydroidb/wiki)

## 🔗 Related Projects

- [Android SDK Platform Tools](https://developer.android.com/studio/releases/platform-tools)
- [ADB Documentation](https://developer.android.com/studio/command-line/adb)
- [Fastboot Documentation](https://android.googlesource.com/platform/system/core/+/master/fastboot/)

---

<div align="center">

**Made with ❤️ by [0xbv1 | 0xb0rn3](https://github.com/0xb0rn3)**

*If you find this tool helpful, please consider giving it a ⭐ star!*

</div>
