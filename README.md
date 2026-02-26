<![CDATA[<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=250&section=header&text=droidB&fontSize=100&fontAlignY=40&animation=twinkling&fontColor=fff&desc=Android%20Security%20Testing%20%26%20Device%20Management&descAlignY=60&descSize=25" width="100%"/>
</p>

<p align="center">
  <a href="https://github.com/0xb0rn3/droidB/releases"><img src="https://img.shields.io/badge/version-0.3.1-00d4ff?style=for-the-badge&logo=semver&logoColor=white" alt="Version"/></a>
  <a href="https://github.com/0xb0rn3/droidB/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-00ff88?style=for-the-badge&logo=open-source-initiative&logoColor=white" alt="License"/></a>
  <a href="https://github.com/0xb0rn3/droidB/stargazers"><img src="https://img.shields.io/github/stars/0xb0rn3/droidB?style=for-the-badge&logo=github&color=ffbb00&logoColor=white" alt="Stars"/></a>
  <a href="https://github.com/0xb0rn3/droidB/network/members"><img src="https://img.shields.io/github/forks/0xb0rn3/droidB?style=for-the-badge&logo=git&color=ff6b6b&logoColor=white" alt="Forks"/></a>
</p>

<p align="center">
  <a href="https://github.com/0xb0rn3/droidB/issues"><img src="https://img.shields.io/github/issues/0xb0rn3/droidB?style=for-the-badge&logo=github&color=ea4aaa&logoColor=white" alt="Issues"/></a>
  <a href="https://www.shellcheck.net/"><img src="https://img.shields.io/badge/shellcheck-passing-success?style=for-the-badge&logo=gnu-bash&logoColor=white" alt="ShellCheck"/></a>
  <img src="https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20WSL-blueviolet?style=for-the-badge&logo=linux&logoColor=white" alt="Platform"/>
  <a href="#%EF%B8%8F-ethical-use--legal-notice"><img src="https://img.shields.io/badge/⚖️_Ethical_Use_Policy-READ_FIRST-ff0000?style=for-the-badge" alt="Ethical Use"/></a>
</p>

---

droidB started as a debloater script I wrote because I got tired of typing the same `adb shell pm uninstall` commands over and over. Then I kept adding things. Now it's 6,400+ lines of bash that handles everything from ripping Samsung firmware to intercepting app traffic with invisible iptables proxies.

v0.3.1 bolts on a full **security testing toolkit** — APK analysis, Frida integration, secrets scanning, proxy/traffic interception, TLS cert management, and more. All native bash (no Python runtime needed), all menu-driven, all from a single script.

---

## What's in the box

```
droidB v0.3.1
├── 1.  Device Information
├── 2.  Universal Debloater (300+ packages)
├── 3.  App Management
├── 4.  File Operations
├── 5.  System Operations
├── 6.  Fastboot Operations
├── 7.  Samsung Operations (Odin/Heimdall)
├── 8.  Full Device Backup (SMS, contacts, media, APKs, .ab clone)
├── 9.  System-Wide Install
└── 10. Security Toolkit        ← NEW in 0.3.1
    ├── APK Analysis (decompile, recompile, cert pinning hints, root detection)
    ├── Secrets Scanner (100+ regex patterns — AWS, Slack, GitHub, JWT, etc.)
    ├── Frida Integration (server push, script selector, attach/spawn)
    ├── Proxy & Traffic (system proxy, invisible iptables proxy, DNS spoofing)
    ├── TLS Certificates (Burp/ZAP/mitmproxy CA install to system cacerts)
    ├── App Logging (PID-filtered logcat, crash-only mode, launch-and-log)
    ├── Deep Link Analysis (extract & test intents from APK/manifest)
    ├── Connectivity & Device Controls (WiFi, airplane, DND, tcpdump, WiFi ADB)
    ├── Emulator Management (AVD create/launch/delete)
    ├── APK Merge (split APKs via apkeditor)
    ├── Interactive Shell (enhanced ADB shell with download/upload/cd/su)
    ├── App Backup & Data (.ab format, /data/data collection, reset)
    ├── Force Stop (active process picker)
    ├── Play Store (open by package or search)
    └── Security Tools Checker (audit 21 PC + 4 device-side tools)
```

182 functions. Single file. No dependencies beyond what your package manager already has (adb, fastboot, optionally apktool/frida/openssl for the security stuff).

---

## Quick start

**Enable USB debugging on the phone first** — Settings → About Phone → tap Build Number 7 times → Developer Options → USB Debugging → plug in → accept the RSA prompt.

```bash
# clone and run
git clone https://github.com/0xb0rn3/droidB.git
cd droidB && chmod +x droidB
./droidB

# or install system-wide
sudo ./droidB --install
droidB  # run from anywhere
```

One-liner if you're feeling brave:

```bash
curl -fsSL https://raw.githubusercontent.com/0xb0rn3/droidB/main/droidB | sudo bash -s -- --install
```

### Dependencies

droidB auto-detects and installs what it needs on first run. If you want to do it yourself:

| Platform | Command |
|----------|---------|
| Debian/Ubuntu | `sudo apt install android-tools-adb android-tools-fastboot` |
| Arch | `sudo pacman -S android-tools` |
| Fedora | `sudo dnf install android-tools` |
| macOS | `brew install android-platform-tools` |

For the security toolkit (optional — you only need what you actually use):

| Tool | What it's for |
|------|---------------|
| `apktool` | Decompile/recompile APKs |
| `jadx` / `jadx-gui` | Java decompilation |
| `apksigner` + `keytool` | APK signing, cert inspection |
| `frida` + `frida-tools` | Dynamic instrumentation (pip install) |
| `openssl` | Certificate conversion, hash calculation |
| `scrcpy` | Screen mirroring |
| `bundletool` | AAB → APK conversion |
| `apkeditor` | Split APK merging |
| `tcpdump` (on device) | Packet capture |

Run **Security Toolkit → Check Security Tools** (option 15) to see what you have and what's missing.

---

## Security Toolkit (v0.3.1)

This is the big addition. Everything below lives under main menu option 10.

### APK Analysis

Decompile with apktool, scan smali for certificate pinning indicators (OkHTTP, HttpsURLConnection, TrustManager, network_security_config.xml, embedded SHA hashes), scan for root detection (RootBeer, Magisk checks, SafetyNet/Play Integrity, su binary paths, system property checks). Full analysis mode runs everything and dumps a report to `droidB_results/<package>/full_analysis/`.

Also: recompile modified APKs, sign with test keys, verify signature schemes (v1/v2/v3 with color-coded output), extract APKs directly from device, launch JADX-GUI, convert AAB bundles, and inspect app components (activities, services, receivers, providers, permissions).

### Secrets Scanner

Regex-based scanner with 100+ patterns. Two modes:

- **Full** — everything including high-entropy base64, hex blobs, JWT tokens, generic password assignments
- **Light** — high-confidence only (AWS keys, Bearer tokens, private keys, API key assignments, Firebase/Slack/Discord/GitHub tokens)

Also does custom string search (including hex byte patterns with `0x` prefix) and in-place find & replace across directories.

### Frida

Manages the full Frida lifecycle without leaving the menu:

1. Install frida + frida-tools on your PC (pip)
2. Download the correct frida-server binary for your device arch (arm64/arm/x86_64/x86)
3. Push to `/data/local/tmp/frida-servers/`, chmod, start/stop
4. Select scripts from your `frida_scripts/` directory, merge multiple scripts, attach to running processes or spawn with `--no-pause`

You bring your own `.js` scripts — the tool handles the plumbing.

### Proxy & Traffic Interception

Three proxy modes:

| Mode | How it works | Root? |
|------|-------------|-------|
| **System proxy** | `settings put global http_proxy` — simple, app-visible | No |
| **Invisible proxy** | iptables NAT rules (DNAT + MASQUERADE on 80/443) — app can't detect it | Yes |
| **DNS spoofing** | Python dnslib server, all queries resolve to your IP | Yes (for device DNS config) |

Invisible proxy supports per-app filtering (by UID) or global. WiFi SSID comparison warns you if your PC and phone aren't on the same network before you waste time debugging why the proxy isn't working.

The enhanced iptables display parses DNAT rules and resolves UIDs back to package names so you can actually read what's going on.

### TLS Certificate Installation

Downloads proxy CA certs and installs them to `/system/etc/security/cacerts/` (the system trust store, so apps that ignore user certs still trust your proxy). Supports:

- Burp Suite (`http://<ip>:<port>/cert`)
- ZAP Proxy (`/OTHER/network/other/rootCaCert/`)
- mitmproxy (`http://mitm.it/cert/cer` through the proxy)
- Custom certs with auto-format detection (PEM, DER, PKCS#12 with password prompt)

Calculates `subject_hash_old` (the MD5-based filename Android expects) and pushes with correct permissions. Checks if the cert already exists before overwriting.

### Network Capture

Live tcpdump with interface and filter selection, or timed capture to `.pcap` file that gets pulled to your PC ready for Wireshark.

### WiFi ADB

Enable `adb tcpip`, auto-detect device IP, connect wirelessly, disconnect. Updates the active serial automatically so the rest of the tool keeps working over WiFi.

### Everything else

- **App Logging** — PID-filtered logcat, crash-only mode (`*:E`), launch-and-log (clear buffer → start app → capture), dumpsys meminfo
- **Deep Links** — extract scheme://host/path patterns from AndroidManifest.xml (from APK, from device, or from a manifest file), test intents directly
- **Connectivity** — WiFi on/off, airplane mode, DND modes, battery saver, screen lock toggle
- **Emulator** — AVD list/create/launch/delete via avdmanager, writable-system flag for testing
- **Interactive Shell** — readline-based ADB shell with `download`/`upload` commands, `cd` that actually persists, `su` context tracking
- **App Backup** — `.ab` backup/restore, extract to TAR (with ABE or dd+zlib fallback), pull `/data/data/<package>/` with root, clear app data

---

## Debloater

Still here, still works. 300+ packages across Amazon, Facebook, Google, Samsung, Microsoft, carrier pre-installs, and OEM garbage. Uses `pm disable-user --user 0` by default (reversible). Hard uninstall available with extra confirmation.

Scan your device first, pick categories or go nuclear with one-click. Restore anything you removed.

---

## Samsung Operations

Native Odin4/Heimdall support. Flash BL/AP/CP/CSC partitions, enter download mode, PIT operations, recovery flash. droidB detects Samsung devices and unlocks the menu automatically.

---

## Full Device Backup

Pre-flash safety net. Backs up SMS/MMS, contacts (vCard), call logs (CSV), all media (DCIM, Music, Documents, Downloads, WhatsApp, Telegram), installed APKs, and a full ADB system clone. Everything goes to `~/droidB_backups/<timestamp>_<serial>/` with a manifest file.

Automatically prompted before any destructive operation — firmware flash, bootloader unlock, partition wipe. You either run the backup or explicitly acknowledge you already have one.

---

## Tinkerer Toolkit

Push APKs as system apps (`/system/app`, `/system/priv-app`, `/system/product/app`), auto-grant permissions (7 preset profiles or auto-detect from manifest), generate `privapp-permissions` XML for privileged apps, sign with test keys or custom keystores, clone signatures from existing system apps, and silently grant root via Magisk/KernelSU policy database.

The signature cloning workflow pulls an installed system APK, extracts and analyzes its X.509 certificate, and can import AOSP/LineageOS/CalyxOS pk8+pem key pairs to produce bit-for-bit identical signatures. OEM production keys (Samsung, Google) are saved for reference but can't be cloned without vendor HSM access — droidB tells you this upfront instead of wasting your time.

---

## ⚖️ Ethical Use & Legal Notice

**Read this. It's not decoration.**

droidB's security testing features exist for people working on their own devices — pentesters with authorization, researchers with their own hardware, developers testing their own apps. That's it.

### This tool is for

- Developers testing apps on their own devices
- Security researchers with explicit written authorization
- ROM tinkerers customizing personal hardware
- IT admins managing devices they're responsible for

### This tool is NOT for

- **Unauthorized access** to any device you don't own or don't have documented permission to modify. This includes partners, family, employees, and devices handed to you for repair. Violations fall under CFAA (US), Computer Misuse Act (UK), Cybercrime Convention (EU), and equivalents worldwide.

- **Stalkerware** — using system app push, silent permission grants, or invisible proxy features to install tracking/monitoring software without the device owner's informed consent. This is intimate partner abuse. It's a criminal offense. droidB was not built for this.

- **Malware distribution** — pushing malicious APKs, deploying backdoors, establishing persistence on devices you don't own.

- **Signature fraud** — cloning signatures to impersonate legitimate publishers (banks, Google, government services) for deception or fraud.

- **Data theft** — using backup/extraction features to steal data you're not authorized to access.

### Specific warnings

**Invisible proxy + TLS cert install** = full MITM capability. On your own device for testing, that's the whole point. On someone else's device, that's wiretapping.

**Silent permission grants** (location, camera, mic, contacts) + **system app push** (survives factory reset) + **root grant** (no popup) = the technical foundation of commercial spyware. On your own test device, it's a development shortcut. On someone else's device, it's a felony.

**Secrets scanner** is for finding leaked credentials in APKs you're authorized to test. Not for harvesting credentials from apps you downloaded.

### No warranty

```
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
THE AUTHORS ARE NOT LIABLE FOR BRICKED DEVICES, DATA LOSS,
VOIDED WARRANTIES, CARRIER BANS, OR LEGAL CONSEQUENCES.

YOU ACCEPT FULL RESPONSIBILITY FOR EVERY OPERATION YOU PERFORM.
IGNORANCE OF THE LAW IS NOT A DEFENSE.
```

---

## Contributing

Found a bug? Open an issue. Want to add something? PRs welcome. The code is a single bash file — read it, understand it, hack on it. No build system, no framework, no abstractions. Just bash.

Things that would be useful:
- Device-specific quirks and workarounds
- Additional bloatware package lists
- Frida script contributions
- Testing on devices I don't have access to

---

## About

<p align="center">
  <a href="https://github.com/0xb0rn3"><img src="https://github.com/0xb0rn3.png" width="100" style="border-radius:50%"/></a>
</p>

<p align="center">
  <strong>0xb0rn3</strong> · security researcher · android tinkerer<br/>
  <a href="https://github.com/0xb0rn3"><img src="https://img.shields.io/badge/GitHub-0xb0rn3-181717?style=flat-square&logo=github" alt="GitHub"/></a>
  <a href="https://twitter.com/oxbv1"><img src="https://img.shields.io/badge/X-@oxbv1-1DA1F2?style=flat-square&logo=x" alt="Twitter"/></a>
</p>

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=120&section=footer&text=&fontSize=0" width="100%"/>
</p>

<p align="center">
  <a href="https://github.com/0xb0rn3/droidB/stargazers"><img src="https://img.shields.io/github/stars/0xb0rn3/droidB?style=social" alt="Stars"/></a>
  <a href="https://github.com/0xb0rn3/droidB/network/members"><img src="https://img.shields.io/github/forks/0xb0rn3/droidB?style=social" alt="Forks"/></a>
</p>

<p align="center"><sub>v0.3.1 · MIT · February 2026</sub></p>
]]>
