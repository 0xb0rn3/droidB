<p align="center">
  <a href="https://github.com/0xb0rn3/droidB/releases"><img src="https://img.shields.io/badge/version-0.3.1-00d4ff?style=for-the-badge&logo=semver&logoColor=white"/></a>
  <a href="https://github.com/0xb0rn3/droidB/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-00ff88?style=for-the-badge&logo=open-source-initiative&logoColor=white"/></a>
  <a href="https://github.com/0xb0rn3/droidB/stargazers"><img src="https://img.shields.io/github/stars/0xb0rn3/droidB?style=for-the-badge&logo=github&color=ffbb00&logoColor=white"/></a>
  <a href="https://github.com/0xb0rn3/droidB/network/members"><img src="https://img.shields.io/github/forks/0xb0rn3/droidB?style=for-the-badge&logo=git&color=ff6b6b&logoColor=white"/></a>
</p>

<p align="center">
  <a href="https://github.com/0xb0rn3/droidB/issues"><img src="https://img.shields.io/github/issues/0xb0rn3/droidB?style=for-the-badge&logo=github&color=ea4aaa&logoColor=white"/></a>
  <img src="https://img.shields.io/badge/shellcheck-passing-success?style=for-the-badge&logo=gnu-bash&logoColor=white"/>
  <img src="https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20WSL-blueviolet?style=for-the-badge&logo=linux&logoColor=white"/>
  <a href="#-legal"><img src="https://img.shields.io/badge/⚖️_Ethical_Use-READ_FIRST-ff0000?style=for-the-badge"/></a>
</p>

---

Started as a debloater. I got sick of typing `adb shell pm uninstall` thirty times per device setup. Then I kept bolting things on. Now it's 6,400+ lines of bash that handles everything from ripping Samsung firmware to invisible iptables MITM proxies.

v0.3.1 adds a full security testing toolkit — APK analysis, Frida lifecycle management, secrets scanning, traffic interception, TLS cert injection. Pure bash. No Python runtime. Menu-driven. One file.

---

## Structure

```
droidB v0.3.1
├── 1.  Device Information
├── 2.  Universal Debloater          (300+ packages)
├── 3.  App Management
├── 4.  File Operations
├── 5.  System Operations
├── 6.  Fastboot Operations
├── 7.  Samsung Operations           (Odin/Heimdall)
├── 8.  Full Device Backup           (SMS, contacts, media, APKs, .ab clone)
├── 9.  System-Wide Install
└── 10. Security Toolkit
    ├── APK Analysis                 (decompile, recompile, pinning hints, root detection)
    ├── Secrets Scanner              (100+ regex patterns)
    ├── Frida Integration            (server push, script selector, attach/spawn)
    ├── Proxy & Traffic Interception (system, invisible iptables, DNS spoofing)
    ├── TLS Certificate Management   (Burp/ZAP/mitmproxy CA → system cacerts)
    ├── App Logging                  (PID-filtered logcat, crash-only, launch-and-log)
    ├── Deep Link Analysis           (extract + test intents from APK/manifest)
    ├── Connectivity Controls        (WiFi, airplane, DND, tcpdump, WiFi ADB)
    ├── Emulator Management          (AVD create/launch/delete)
    ├── APK Merge                    (split APKs via apkeditor)
    ├── Interactive Shell            (ADB shell with persistent cd, download/upload, su)
    ├── App Backup & Data            (.ab format, /data/data pull, reset)
    ├── Force Stop                   (active process picker)
    └── Security Tools Checker       (audit 21 PC + 4 device-side tools)
```

182 functions. Single file.

---

## Setup

Enable USB debugging first — Settings → About Phone → tap Build Number 7× → Developer Options → USB Debugging → plug in → accept the RSA prompt.

```bash
git clone https://github.com/0xb0rn3/droidB.git
cd droidB && chmod +x droidB
./droidB

# system-wide install
sudo ./droidB --install
droidB
```

One-liner:
```bash
curl -fsSL https://raw.githubusercontent.com/0xb0rn3/droidB/main/droidB | sudo bash -s -- --install
```

### Dependencies

droidB detects and installs what it needs on first run. To do it manually:

| Distro | Command |
|--------|---------|
| Debian/Ubuntu | `sudo apt install android-tools-adb android-tools-fastboot` |
| Arch | `sudo pacman -S android-tools` |
| Fedora | `sudo dnf install android-tools` |
| macOS | `brew install android-platform-tools` |

Security toolkit optionals (install only what you'll actually use):

| Tool | Purpose |
|------|---------|
| `apktool` | Decompile/recompile APKs |
| `jadx` / `jadx-gui` | Java decompilation |
| `apksigner` + `keytool` | APK signing, cert inspection |
| `frida` + `frida-tools` | Dynamic instrumentation |
| `openssl` | Cert conversion, hash calculation |
| `scrcpy` | Screen mirroring |
| `bundletool` | AAB → APK |
| `apkeditor` | Split APK merging |
| `tcpdump` | On-device packet capture |

Run **Security Toolkit → Check Security Tools** to audit what you have.

---

## Security Toolkit

Everything below is under main menu option 10.

### APK Analysis

Decompiles with apktool and scans smali for:
- **Certificate pinning** — OkHTTP, HttpsURLConnection, TrustManager, network_security_config.xml, embedded SHA hashes
- **Root detection** — RootBeer, Magisk checks, SafetyNet/Play Integrity, su binary paths, system property checks

Full analysis mode runs everything and writes a report to `droidB_results/<package>/full_analysis/`.

Also handles: recompile modified APKs, sign with test keys, verify signature schemes (v1/v2/v3), extract APKs from device, launch JADX-GUI, convert AAB bundles, inspect app components (activities, services, receivers, providers, permissions).

### Secrets Scanner

Regex-based scanner, 100+ patterns, two modes:

**Full** — everything: high-entropy base64, hex blobs, JWT tokens, generic password assignments, the lot.

**Light** — high-confidence hits only: AWS keys, Bearer tokens, private keys, API key assignments, Firebase/Slack/Discord/GitHub tokens.

Also does custom string search (supports hex byte patterns with `0x` prefix) and in-place find & replace across directories.

### Frida

Manages the full lifecycle without leaving the menu:

1. Install frida + frida-tools on your machine (pip)
2. Pull the correct frida-server binary for your device arch (arm64/arm/x86_64/x86)
3. Push to `/data/local/tmp/frida-servers/`, chmod, start/stop
4. Select scripts from your `frida_scripts/` dir, merge multiple, attach to running process or spawn with `--no-pause`

Bring your own `.js` — droidB handles the plumbing.

### Proxy & Traffic Interception

Three modes:

| Mode | Mechanism | Root |
|------|-----------|------|
| System proxy | `settings put global http_proxy` | No |
| Invisible proxy | iptables DNAT + MASQUERADE on 80/443 | Yes |
| DNS spoofing | Python dnslib, all queries → your IP | Yes |

Invisible proxy supports per-app UID filtering or global. Compares WiFi SSIDs before you waste time debugging a proxy that isn't reachable. The iptables display resolves UIDs back to package names.

### TLS Certificate Installation

Installs proxy CA certs directly to `/system/etc/security/cacerts/` — the system trust store, so apps ignoring user certs still trust your proxy.

Supports Burp Suite, ZAP, mitmproxy, and custom certs (auto-detects PEM/DER/PKCS#12, prompts for password if needed). Calculates `subject_hash_old` (the MD5-based filename Android expects) and pushes with correct permissions. Checks for existing cert before overwriting.

### Network Capture

Live tcpdump with interface and filter selection, or timed capture to `.pcap` pulled to your machine ready for Wireshark.

### WiFi ADB

Enable `adb tcpip`, auto-detect device IP, connect wirelessly, disconnect. Updates active serial automatically so the rest of the tool stays functional over WiFi.

### App Logging

PID-filtered logcat, crash-only mode (`*:E`), launch-and-log (clear buffer → start app → capture), dumpsys meminfo.

### Deep Links

Extracts scheme://host/path patterns from AndroidManifest.xml — from an APK, from a device, or from a raw manifest file. Tests intents directly.

### Emulator

AVD list/create/launch/delete via avdmanager. Writable system flag for testing.

### Interactive Shell

readline-based ADB shell with `download`/`upload` commands, `cd` that persists between commands, `su` context tracking.

### App Backup

`.ab` backup/restore, extract to TAR (with ABE or dd+zlib fallback), pull `/data/data/<package>/` with root, clear app data.

---

## Debloater

300+ packages across Amazon, Facebook, Google, Samsung, Microsoft, carrier pre-installs, and OEM garbage. Uses `pm disable-user --user 0` by default — reversible. Hard uninstall available with extra confirmation.

Scan the device first, pick by category, or nuke everything at once. Restore is a menu option.

---

## Samsung Operations

Odin4/Heimdall support. Flash BL/AP/CP/CSC partitions, download mode, PIT operations, recovery flash. droidB detects Samsung devices and unlocks the menu.

---

## Full Device Backup

Backs up SMS/MMS, contacts (vCard), call logs (CSV), all media (DCIM, Music, Documents, Downloads, WhatsApp, Telegram), installed APKs, and a full ADB system clone. Everything goes to `~/droidB_backups/<timestamp>_<serial>/` with a manifest.

Auto-prompted before any destructive operation — firmware flash, bootloader unlock, partition wipe.

---

## Tinkerer Toolkit

Push APKs as system apps (`/system/app`, `/system/priv-app`, `/system/product/app`), auto-grant permissions (7 preset profiles or manifest auto-detect), generate `privapp-permissions` XML, sign with test keys or custom keystores, clone signatures from existing system apps, grant root silently via Magisk/KernelSU policy DB.

Signature cloning pulls an installed system APK, extracts and analyzes its X.509 cert, and can import AOSP/LineageOS/CalyxOS pk8+pem key pairs for identical signatures. OEM production keys (Samsung, Google) are documented for reference — you can't clone them without vendor HSM access, and droidB tells you that upfront.

---

## ⚖️ Legal

droidB's security features exist for authorized use — pentesters with written scope, researchers on their own hardware, developers testing their own apps.

**Authorized use:**
- Your own devices
- Devices you have documented written permission to test
- Apps you developed
- Devices you're responsible for as an IT admin

**Not authorized:**
- Any device you don't own and don't have explicit written permission to access — this includes partners, family, employees, repair customers. CFAA (US), Computer Misuse Act (UK), Cybercrime Convention (EU) all apply.
- Installing monitoring software without the device owner's informed consent. That's stalkerware. It's a criminal offense.
- Pushing malicious APKs, deploying backdoors, establishing persistence on devices you don't own.
- Cloning signatures to impersonate legitimate publishers for fraud.
- Using backup/extraction to access data you're not authorized to touch.

**Invisible proxy + TLS cert install** = full MITM capability. On your own test device, that's the point. On someone else's device without consent, that's wiretapping.

**Silent permission grants + system app push + root grant** = commercial spyware stack. On your own test device, it's a dev shortcut. On someone else's device, it's a felony.

```
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
THE AUTHORS ARE NOT LIABLE FOR BRICKED DEVICES, DATA LOSS,
VOIDED WARRANTIES, CARRIER BANS, OR LEGAL CONSEQUENCES.
YOU ACCEPT FULL RESPONSIBILITY FOR EVERY OPERATION YOU PERFORM.
```

---

## Contributing

Open an issue for bugs. PRs welcome for everything else. The codebase is a single bash file — read it, understand it, modify it. No build system, no framework.

What's useful:
- Device-specific quirks and workarounds
- Bloatware package lists for devices I don't test on
- Frida scripts
- Bug reports with adb output

---

<p align="center">
  <a href="https://github.com/0xb0rn3"><img src="https://github.com/0xb0rn3.png" width="80" style="border-radius:50%"/></a><br/>
  <strong>0xb0rn3</strong><br/>
  <a href="https://github.com/0xb0rn3"><img src="https://img.shields.io/badge/GitHub-0xb0rn3-181717?style=flat-square&logo=github"/></a>
  <a href="https://twitter.com/oxbv1"><img src="https://img.shields.io/badge/X-@oxbv1-1DA1F2?style=flat-square&logo=x"/></a>
</p>

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=120&section=footer" width="100%"/>
</p>

<p align="center">
  <a href="https://github.com/0xb0rn3/droidB/stargazers"><img src="https://img.shields.io/github/stars/0xb0rn3/droidB?style=social"/></a>
  <a href="https://github.com/0xb0rn3/droidB/network/members"><img src="https://img.shields.io/github/forks/0xb0rn3/droidB?style=social"/></a>
</p>

<p align="center"><sub>v0.3.1 · MIT · February 2026</sub></p>
