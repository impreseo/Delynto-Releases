# Delynto v0.1.1 — Stability & Connectivity Update
### Powered by IMPRESEO LABS
**Tagline:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*

We are pleased to announce the official release of **Delynto** (`v0.1.1`), our dedicated **Stability & Connectivity Update** for **Windows 10/11** and **Android 8.0+**.

This release resolves the root causes of automatic nearby-device discovery failures, eliminates kernel-level multicast packet filtering on mobile chipsets, restores multi-adapter subnet broadcasts across Windows network interfaces, and adds strict defensive bounds checks to the QUIC transfer receiver pipeline.

---

## 📦 Official Distribution Packages & Checksums

| Package Filename | Platform & Architecture | Format | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| [**`Delynto-0.1.1-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.1/Delynto-0.1.1-Setup.exe) | Windows 10 / 11 (`x86_64`) | NSIS Standalone Installer | 11,640,083 bytes (~11.10 MiB) | `724f75520c492495543c29f9132fbbcc414d658e8e43731643a1e94a9a699a2c` |
| [**`Delynto-0.1.1.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.1/Delynto-0.1.1.apk) | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK | 27,415,905 bytes (~26.14 MiB) | `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b` |
| [**`SHA256SUMS.txt`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.1/SHA256SUMS.txt) | All Platforms | Plain Text Manifest | 174 bytes | Manifest containing all verified hashes |

### Checksum Verification Commands
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\Delynto-0.1.1-Setup.exe -Algorithm SHA256
  ```
  Expected: `724f75520c492495543c29f9132fbbcc414d658e8e43731643a1e94a9a699a2c`

- **Linux / macOS / Android Termux (Bash):**
  ```bash
  sha256sum Delynto-0.1.1.apk
  # Or verify manifest
  sha256sum -c SHA256SUMS.txt
  ```
  Expected: `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b`

---

## 🔧 Root-Cause Engineering Fixes in v0.1.1

1. **Subnet-Directed Broadcast Calculation (`crates/relaymesh-discovery/src/service.rs`):**
   - *Problem:* When OS network enumeration APIs (notably Windows `GetAdaptersAddresses` and Android `getifaddrs`) leave the `broadcast` field as `None`, previous discovery logic fell back to transmitting solely to `255.255.255.255`. In Windows Winsock, `255.255.255.255` is routed only to the interface with the lowest route metric (frequently a virtual adapter, VPN, or Ethernet rather than the active Wi-Fi interface).
   - *Fix:* Added active computation of directed subnet broadcast addresses `(ip | !netmask)` for all active physical LAN interfaces, while properly excluding loopback and unconfigured APIPA (`169.254.x.x`) links.

2. **Multicast Physical Adapter Binding (`crates/relaymesh-discovery/src/service.rs`):**
   - *Problem:* Calling `join_multicast_v4(MULTICAST_IPV4_ADDR, Ipv4Addr::UNSPECIFIED)` only joins the multicast group on the operating system default interface. If the primary peer Wi-Fi interface has a higher metric than a local bridge or VPN, multicast discovery packets are ignored.
   - *Fix:* Explicitly iterated all active non-loopback IPv4 adapters and called `join_multicast_v4(MULTICAST_IPV4_ADDR, v4.ip)` on each individual interface, ensuring discovery beacons are captured across all network adapters.

3. **Android Hardware Multicast Lock (`apps/android`):**
   - *Problem:* Android Wi-Fi chipsets filter out incoming multicast UDP datagrams at the hardware/kernel driver level to conserve battery unless an explicit `WifiManager.MulticastLock` is held.
   - *Fix:* Integrated `multicastLock` acquisition and release across `MainActivity` and `TransferForegroundService`, allowing discovery beacons on UDP port `53317` to reach the RelayMesh engine unimpeded.

4. **Dynamic Peer Event Notification (`crates/relaymesh-discovery/src/service.rs`):**
   - *Problem:* `record_device()` previously emitted events only when a device was first seen (`is_new == true`). When a device refreshed its candidate IP addresses or initiated pairing (providing an ephemeral PIN or session ID), the UI never received an update.
   - *Fix:* Enhanced `record_device()` to emit real-time updates whenever candidate addresses, pairing codes, or session IDs update.

5. **Receiver Bounds & Chunk Safety (`crates/relaymesh-transfer/src/receiver.rs`):**
   - *Problem:* Incoming chunk streams could theoretically allocate unbounded memory or panic if a malformed packet specified an invalid chunk index.
   - *Fix:* Implemented defensive assertions: verifying `chunk_index < self.manifest.chunk_count` and enforcing a strict 16 MiB upper bound per chunk buffer before memory allocation.

---

## 🌟 Core Product Features

- **100% Zero-Cloud Architecture:** Operates completely over local Wi-Fi, Ethernet, or mobile hotspot networks. No accounts, central servers, cloud relays, or telemetry.
- **Wire-Speed QUIC Transport:** Built on the custom Rust **RelayMesh** engine. Multiplexed 4 MiB chunk streaming over QUIC with TLS 1.3 encryption on UDP port `41820`.
- **Active OS Interface Discovery:** Automatically enumerates operating system network adapters to discover peers on Wi-Fi, LAN, and offline hotspots without requiring an active internet connection (UDP port `53317`).
- **Human-Friendly Cryptographic Pairing:**
  - **One-Tap Local Connect:** Instant pairing invitation to discovered peers.
  - **Ephemeral 6-Digit PIN:** Temporary passcode linking for cross-VLAN or manual pairing.
  - **QR Optical Fallback:** High-contrast camera token scanning for camera-equipped devices.
  - **Short Authentication String (SAS):** Matching 6-digit visual code confirmation on both screens to eliminate machine-in-the-middle attacks.
- **Resumable Chunk Pipeline:** Large transfers divide into 4 MiB blocks; interrupted transfers automatically resume from the last verified block without re-transmitting completed data.
- **Directory & Batch Jobs:** Seamlessly transmit multi-file collections and nested folder structures with built-in path traversal (`../`) protection, Windows reserved name sanitization, and automatic collision avoidance (`File (1).ext`).
- **Pearl × Obsidian Aesthetic:** Polished light and dark themes with subtle liquid glass depth, custom Windows frameless window title bar, and native Android Jetpack Compose 5-tab interface.

---

## 📸 Genuine Application Screenshot Gallery

Explore unedited captures from the active Delynto runtime on Windows 11 and Android in the [Screenshots Catalog](https://github.com/impreseo/Delynto-Releases/tree/main/documentation/screenshots):

- [Desktop Home Hub](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-home.png) — Drag-and-drop staging zone and active throughput monitors.
- [Nearby Devices Radar](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-nearby-devices.png) — Real-time peer discovery showing verified platform types.
- [Active Transfers Monitor](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-transfers.png) — Multi-file transfer progress, chunk status, and speedometers.
- [Settings & Diagnostics](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-settings.png) — Obsidian × Pearl theme toggle and Ed25519 node fingerprint.
- [Android Nearby Radar](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/android/android-nearby.png) — 5-tab mobile interface with foreground transfer service.
- [Mutual Pairing Modal](https://raw.githubusercontent.com/impreseo/Delynto-Releases/main/documentation/screenshots/desktop/desktop-pairing.png) — 6-digit PIN and Short Authentication String (SAS) verification.

---

## 🚀 Installation Quick Guide

### Windows Desktop:
1. Download [**`Delynto-0.1.1-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.1/Delynto-0.1.1-Setup.exe).
2. Double-click the installer.
3. *Windows Defender SmartScreen:* Because this open-source binary is unsigned, SmartScreen may display an alert (*"Windows protected your PC"*). Click **"More info"** followed by **"Run anyway"**.
4. When prompted by Windows Defender Firewall, allow access on **Private networks** to permit local UDP discovery and QUIC transfer streaming.
5. Delynto installs to `%LOCALAPPDATA%\Programs\Delynto` with Start Menu and Desktop shortcuts.

### Android Mobile:
1. Download [**`Delynto-0.1.1.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.1/Delynto-0.1.1.apk) to your device.
2. Tap the APK to install. If prompted, toggle **"Allow from this source"** in your settings.
3. Open Delynto and grant notification and storage permissions to enable background foreground service transfers.

---

## 🔒 Security & Privacy Principles

- **Zero Cloud & Zero Telemetry:** Transferred bytes never leave your local physical or wireless network. Delynto includes no telemetry collectors, crash analytics, ad networks, tracking pixels, or third-party SDKs.
- **Self-Sovereign Identity:** Device identities are self-generated Ed25519 cryptographic keypairs generated using local CSPRNG.
- **Protected File Keypair Integrity:** `crates/relaymesh-identity/src/keypair.rs` has been cryptographically preserved (`72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`).
- **Explicit Recipient Consent:** No device can push data directly onto your disk without explicit confirmation. Every transfer displays file names, total size, and sender identity before transfer begins.
- **Collision Avoidance:** Existing files are protected from overwriting. If a collision occurs, a non-destructive numbered suffix (e.g. `Report (1).pdf`) is applied automatically.

---

## 📚 Complete Documentation Library

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

[Official Release](https://github.com/impreseo/Delynto-Releases/releases/tag/v0.1.1) • [Distribution Repository](https://github.com/impreseo/Delynto-Releases) • [Source Repository](https://github.com/impreseo/Delynto) • [Report Issues](https://github.com/impreseo/Delynto/issues)

</div>
