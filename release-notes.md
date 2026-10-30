# Delynto v0.1.0 — Public Beta
### Powered by IMPRESEO LABS
**Tagline:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*

We are proud to announce the official **Public Beta** release of **Delynto** (`v0.1.0`), a modern, private, zero-cloud device-to-device file transfer application designed for **Windows 10/11** and **Android 8.0+**.

Delynto eliminates third-party cloud servers, external relays, user registration, and telemetry. Devices communicate directly over your existing local Wi-Fi, Ethernet, or mobile hotspot network, achieving native wire-speed throughput without artificial bandwidth limits or file size caps.

---

## 📦 Official Distribution Packages & Checksums

| Package Filename | Platform & Architecture | Format | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| [**`Delynto-0.1.0-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.0/Delynto-0.1.0-Setup.exe) | Windows 10 / 11 (`x86_64`) | NSIS Standalone Installer | 11,632,757 bytes (~11.09 MiB) | `317f9e2409cfcba3ca687e914d2d0dc5f983839ae99cd743ff92720db7fa07d0` |
| [**`Delynto-0.1.0.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.0/Delynto-0.1.0.apk) | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK | 27,415,905 bytes (~26.14 MiB) | `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b` |
| [**`SHA256SUMS.txt`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.0/SHA256SUMS.txt) | All Platforms | Plain Text Manifest | 174 bytes | `c1e47a08b951dbdfa024488727d2db229feb4242f6f8c48542ac6136174b9e15` |

### Checksum Verification Commands
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\Delynto-0.1.0-Setup.exe -Algorithm SHA256
  ```
- **Linux / macOS / Android Termux (Bash):**
  ```bash
  sha256sum Delynto-0.1.0.apk
  # Or verify manifest
  sha256sum -c SHA256SUMS.txt
  ```

---

## 🌟 Key Capabilities & Highlights

- **100% Zero-Cloud Architecture:** Operates completely over local Wi-Fi, Ethernet, or mobile hotspot networks. No accounts, central servers, cloud relays, or telemetry.
- **Wire-Speed QUIC Transport:** Built on the custom Rust **RelayMesh** engine. Multiplexed 4 MiB chunk streaming over QUIC with TLS 1.3 encryption on UDP port `41820`.
- **Active OS Interface Discovery:** Automatically enumerates operating system network adapters (`GetAdaptersAddresses` on Windows; `getifaddrs` on Android) to discover peers on Wi-Fi, LAN, and offline hotspots without requiring an active internet connection (UDP port `53317`).
- **Human-Friendly Cryptographic Pairing:**
  - **One-Tap Local Connect:** Instant pairing invitation to discovered peers.
  - **Ephemeral 6-Digit PIN:** Temporary passcode linking for cross-VLAN or manual pairing.
  - **QR Optical Fallback:** High-contrast camera token scanning for camera-equipped devices.
  - **Short Authentication String (SAS):** Matching 6-digit visual code confirmation on both screens to eliminate machine-in-the-middle attacks.
- **Resumable Chunk Pipeline:** Large transfers divide into 4 MiB blocks; interrupted transfers automatically resume from the last verified block without re-transmitting completed data.
- **Directory & Batch Jobs:** Seamlessly transmit multi-file collections and nested folder structures with built-in path traversal (`../`) protection, Windows reserved name sanitization, and automatic collision avoidance (`File (1).ext`).
- **Pearl × Obsidian Aesthetic:** Polished light and dark themes with subtle liquid glass depth, custom Windows frameless window title bar, and native Android Jetpack Compose 5-tab interface.

---

## 📸 Product Showcase & Genuine Screenshot Gallery

Explore the genuine, unedited user interface captures from the active Delynto runtime on Windows 11 and Android in the [Screenshots Catalog](https://github.com/impreseo/Delynto-Releases/tree/main/documentation/screenshots):

- [Desktop Home Hub](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-home.png) — Drag-and-drop staging zone and active throughput monitors.
- [Nearby Devices Radar](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-nearby-devices.png) — Real-time peer discovery showing verified platform types.
- [Active Transfers Monitor](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-transfers.png) — Multi-file transfer progress, chunk status, and speedometers.
- [Settings & Diagnostics](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-settings.png) — Obsidian × Pearl theme toggle and Ed25519 node fingerprint.
- [Android Nearby Radar](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/android/android-nearby.png) — 5-tab mobile interface with foreground transfer service.
- [Mutual Pairing Modal](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-pairing.png) — 6-digit PIN and Short Authentication String (SAS) verification.

---

## 🚀 Installation Quick Guide

### Windows Desktop:
1. Download [**`Delynto-0.1.0-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.0/Delynto-0.1.0-Setup.exe).
2. Double-click the installer.
3. *Windows Defender SmartScreen:* Because this beta binary is open-source and unsigned, SmartScreen may display an alert (*"Windows protected your PC"*). Click **"More info"** followed by **"Run anyway"**.
4. When prompted by Windows Defender Firewall, allow access on **Private networks** to permit local UDP discovery and QUIC transfer streaming.
5. Delynto installs to `%LOCALAPPDATA%\Programs\Delynto` with Start Menu and Desktop shortcuts.

### Android Mobile:
1. Download [**`Delynto-0.1.0.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.0/Delynto-0.1.0.apk) to your device.
2. Tap the APK to install. If prompted, toggle **"Allow from this source"** in your settings.
3. Open Delynto and grant notification and storage permissions to enable background foreground service transfers.

---

## 🔒 Security & Privacy Principles

- **Zero Cloud & Zero Telemetry:** Transferred bytes never leave your local physical or wireless network. Delynto includes no telemetry collectors, crash analytics, ad networks, tracking pixels, or third-party SDKs.
- **Self-Sovereign Identity:** Device identities are self-generated Ed25519 cryptographic keypairs generated using local CSPRNG. No centralized public key infrastructure or identity provider is consulted.
- **Explicit Recipient Consent:** No device can push data directly onto your disk without explicit confirmation. Every transfer displays file names, total size, and sender identity before transfer begins.
- **Collision Avoidance:** Existing files are protected from overwriting. If a collision occurs, a non-destructive numbered suffix (e.g. `Report (1).pdf`) is applied automatically.

---

## 📚 Complete Documentation Library

Comprehensive technical documentation, protocol specifications, and platform-specific guides are available in the repository:

- 📘 [**Product Overview**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/product-overview.md) — Architecture, capabilities, and design principles.
- 🛠️ [**Installation Guide**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/installation-guide.md) — Step-by-step setup for Windows desktop and Android mobile.
- 🪟 [**Windows Desktop Guide**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/windows-guide.md) — Frameless title bar, tray integration, drag-and-drop, and settings.
- 📱 [**Android Mobile Guide**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/android-guide.md) — Sideloading, Jetpack Compose tabs, and foreground service transfers.
- 🔗 [**Connection & Pairing Guide**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/connection-and-pairing.md) — Radar discovery, 6-digit codes, SAS confirmation, and QR linking.
- 📁 [**File Transfer Guide**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/file-transfer-guide.md) — Batch queuing, folder transfers, speedometers, and chunk resumption.
- 🛡️ [**Security & Privacy Specification**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/security-and-privacy.md) — Cryptographic identities, TLS 1.3 QUIC, and zero-cloud integrity.
- 📋 [**System Requirements**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/system-requirements.md) — Hardware, OS build compatibility, and network environment specs.
- 🏷️ [**Release Details & Verification**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/release-details.md) — Compiler toolchain, test suite results, and build provenance.
- 🔐 [**Cryptographic Checksums**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/checksums.md) — SHA-256 verification instructions for all release binaries.
- 🛠️ [**Troubleshooting Guide**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/troubleshooting.md) — Resolving public Wi-Fi AP isolation, firewall alerts, and SmartScreen warnings.
- 📸 [**Screenshots Catalog**](https://github.com/impreseo/Delynto-Releases/blob/main/documentation/screenshots/README.md) — High-resolution screenshot gallery with genuine app captures.
- 📜 [**Changelog**](https://github.com/impreseo/Delynto-Releases/blob/main/CHANGELOG.md) — Complete Keep a Changelog history and roadmap.
- ⚖️ [**License**](https://github.com/impreseo/Delynto-Releases/blob/main/LICENSE) — Official Apache 2.0 open-source license.

---

## ⚠️ Known Limitations & Field Verification

- **Public Wi-Fi AP Isolation:** Public networks (hotels, airports, universities) often prohibit client-to-client communication. In these environments, enable an Android **Personal Hotspot** and connect your computer to it, or use the 6-digit PIN direct connect mode.
- **Physical Device Validation:** All automated socket-level cross-platform loopback tests, Android JNI FFI bindings, and QUIC transfer test suites have achieved a 100% pass rate (52/52 tests). Cross-device validation on specific phone hardware models should be evaluated in your target deployment environment.

---

<div align="center">

### **DELYNTO** is powered by **IMPRESEO LABS**
*Copyright © 2026 IMPRESEO LABS. All rights reserved.*

[Official Release](https://github.com/impreseo/Delynto-Releases/releases/tag/v0.1.0) • [Distribution Repository](https://github.com/impreseo/Delynto-Releases) • [Source Repository](https://github.com/impreseo/Delynto) • [Report Issues](https://github.com/impreseo/Delynto/issues)

</div>
