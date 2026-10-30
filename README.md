# Delynto Releases

Official binary distribution repository for **Delynto** — private, zero-cloud device-to-device file transfer powered by **IMPRESEO LABS**.

- **Primary Source Code Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)
- **Current Version:** `v0.1.0` (Public Beta)
- **Product Principle:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*
- **Visual Identity:** Pearl × Obsidian × Liquid Glass
- **Complete Documentation:** [`documentation/`](documentation/README.md)

---

## 📥 Official Application Packages

All binary packages are cryptographically hashed and published below:

| Platform | Package File | Format | Architecture | Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Windows Desktop** | [Delynto-0.1.0-Setup.exe](Delynto-0.1.0-Setup.exe) | NSIS Setup | x86_64 / x64 | 11,632,472 bytes (~11.09 MiB) | `F8C47D9328FE30A138E9A1CB5CA8614E865B41EEC6648D4D58A14B089D3CE55E` |
| **Android Mobile** | [Delynto-0.1.0.apk](Delynto-0.1.0.apk) | Android APK | arm64-v8a, x86_64 | 27,379,041 bytes (~26.11 MiB) | `C0C1C1CFC3F1D96F9399225FEC338FAE3419D5EAC77DDDFB5CF05A75E9DEE3F8` |
| **Checksum Manifest** | [SHA256SUMS.txt](SHA256SUMS.txt) | Plain Text | All | 174 bytes | — |

---

## 🔒 Checksum Verification

Verify binary integrity before running:

### Windows (PowerShell):
```powershell
Get-FileHash .\Delynto-0.1.0-Setup.exe -Algorithm SHA256
```
Expected: `F8C47D9328FE30A138E9A1CB5CA8614E865B41EEC6648D4D58A14B089D3CE55E`

### Linux / macOS / Android Termux (Bash):
```bash
sha256sum -c SHA256SUMS.txt
```

---

## 📖 Product & Technical Documentation

Explore our comprehensive release documentation directory:

- 📘 **[Product Overview](documentation/product-overview.md)** — Architecture, philosophy, and platform support
- 💻 **[Windows Guide](documentation/windows-guide.md)** — Installation, firewall configuration, and features
- 📱 **[Android Guide](documentation/android-guide.md)** — APK sideloading, permissions, and background services
- 🔗 **[Connection & Pairing Guide](documentation/connection-and-pairing.md)** — Automatic discovery, 6-digit codes, and SAS verification
- 📁 **[File Transfer Guide](documentation/file-transfer-guide.md)** — Single files, batches, collision handling, and QUIC streaming
- 🛡️ **[Security & Privacy Specification](documentation/security-and-privacy.md)** — Ed25519 authentication, zero telemetry, local-first
- 🛠️ **[Troubleshooting Guide](documentation/troubleshooting.md)** — Resolving network isolation, firewall, and permission issues
- 📋 **[System Requirements](documentation/system-requirements.md)** — Hardware and OS compatibility matrices
- 🏷️ **[Release Details](documentation/release-details.md)** — Build environment, compilation flags, and verified metrics
- 📸 **[Screenshots Gallery](documentation/screenshots/README.md)** — Genuine UI captures across Windows and Android

---

## 🚀 Quick Start Guide

### Windows 10 / 11 (64-bit)
1. Download **`Delynto-0.1.0-Setup.exe`**.
2. Run the installer to setup Delynto in `%LOCALAPPDATA%\Programs\Delynto`.
3. *SmartScreen Notice:* Because this beta release is unsigned (lacks an expensive commercial EV certificate), Windows SmartScreen will display an unrecognized app alert. Click **"More info"** and then **"Run anyway"**.
4. When prompted by Windows Defender Firewall, allow local UDP communication so RelayMesh can discover peers and stream transfers.

### Android 8.0+ (API 26+)
1. Download **`Delynto-0.1.0.apk`** to your device.
2. Tap the APK file to install. If prompted, allow installation from unknown sources for your browser or file manager.
3. Open Delynto and grant storage/notification permissions when requested.

---

## 🏗️ Source Code & Community

- **Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)
- **Issue Tracker:** [https://github.com/impreseo/Delynto/issues](https://github.com/impreseo/Delynto/issues)
- **Official Attribution:** Powered by **IMPRESEO LABS**
