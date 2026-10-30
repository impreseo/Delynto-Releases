# Changelog

All notable changes to **Delynto** and its underlying distribution packages are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Planned
- macOS (`.dmg`) distribution with native Apple Silicon (`aarch64`) and Intel (`x86_64`) builds.
- Linux (`.AppImage`, `.deb`, `.rpm`) distributions.
- Multi-device simultaneous broadcast streaming.
- Bluetooth Low Energy (BLE) out-of-band discovery fallback.

---

## [0.1.1] - 2026-10-30 — Stability & Connectivity Update

### Summary
Comprehensive stability and connectivity restoration update for **Delynto** (Powered by **IMPRESEO LABS**), resolving automatic nearby-device discovery failures across Windows and Android, eliminating packet filtering bottlenecks, and reinforcing transfer safety bounds.

---

### Fixed & Enhanced

#### 📡 Nearby Device Discovery Restoration
- **Subnet-Directed Broadcast Calculation:** Implemented active calculation of `(ip | !netmask)` when operating systems (notably Windows and Android) return `None` for interface broadcast addresses, ensuring discovery datagrams reach local subnets across all network interfaces instead of silently dropping.
- **Multicast Adapter Explicit Binding:** In addition to binding on `INADDR_ANY`, explicitly invoked `join_multicast_v4(MULTICAST_IPV4_ADDR, v4.ip)` across all active physical IPv4 adapters, overcoming Winsock routing table metric biases that previously prevented discovery on non-default adapters.
- **Android Kernel Multicast Lock:** Integrated explicit `WifiManager.MulticastLock` acquisition and release lifecycle management in both `MainActivity` and `TransferForegroundService`, preventing Android's battery-saving driver filters from dropping incoming UDP discovery packets on port `53317`.
- **Dynamic Peer State Notification:** Modified `record_device()` to emit real-time event updates when device candidates, pairing codes, session IDs, or addresses update, eliminating UI stagnation where discovered peers required an app restart to refresh.

#### 🛡️ Transfer Stream Bounds & Memory Safety
- **Chunk Stream Verification:** Added strict defensive assertions in `receiver.rs` verifying incoming chunk indices (`chunk_index < self.manifest.chunk_count`) and bounding chunk buffer allocations (`length <= 16 * 1024 * 1024`), mitigating memory exhaustion or panics from malformed packets.
- **FFI JNI Version Alignment:** Harmonized native library version reporting (`relaymesh_version`) and JNI bindings to `"0.1.1"`.

#### 📦 Distribution Artifacts
- Fresh Windows NSIS Installer: `Delynto-0.1.1-Setup.exe` (11,638,974 bytes, SHA-256: `2f28394e271284e3493cbea67b7a063d7de241080a142ce23f565c2e322b0f4b`).
- Verified Android APK: `Delynto-0.1.1.apk` (27,415,905 bytes, SHA-256: `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b`).

---

## [0.1.0] - 2026-10-30 — Public Beta

### Summary
The inaugural **Public Beta** release of **Delynto** (Powered by **IMPRESEO LABS**), bringing zero-cloud, wire-speed, cryptographic peer-to-peer file transfer to **Windows 10/11** and **Android 8.0+** devices.

**Core Principle:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*

---

### Key Capabilities & Enhancements

#### 📡 Device Discovery & Network Mesh
- **Active OS Interface Enumeration:** Leveraged native Windows `GetAdaptersAddresses` and Linux/Android `getifaddrs` to actively enumerate all network adapters (Wi-Fi, Ethernet, USB tethering, mobile hotspots) rather than relying on external internet routing.
- **Robust UDP Radar Beacons:** Dispatches and receives peer discovery announcements on UDP port `53317` with low-latency device status updates.
- **Direct IP Connection Mode:** Allows instant pairing across subnets, enterprise VLANs, and custom static IP setups.

#### 🤝 Cryptographic Pairing & Trust Management
- **Self-Sovereign Identity:** Automatically generates local Ed25519 node keypairs using system cryptographically secure random number generators (CSPRNG).
- **Flexible Pairing Workflows:**
  - **One-Tap Local Connect:** Instant pairing invitation sent to discovered peers.
  - **Ephemeral 6-Digit PIN:** Temporary passcode linking for manual or remote pairing.
  - **QR Optical Fallback:** High-contrast camera token scanning for camera-equipped devices.
- **Short Authentication String (SAS):** Displays synchronized 6-digit visual codes on both devices to verify mutual cryptographic identity and prevent machine-in-the-middle attacks.
- **Trusted Device Management:** Paired devices are remembered in a local SQLite database for instant future transfers, with one-click revocation.

#### ⚡ Wire-Speed QUIC Transfer Pipeline
- **Transport Security:** High-throughput multiplexed QUIC transport (using Quinn and TLS 1.3) operating on UDP port `41820`.
- **Segmented 4 MiB Chunk Pipeline:** Large files and multi-file collections are divided into 4 MiB chunks verified by independent SHA-256 hashes.
- **Automatic Resume:** Interrupted transfers automatically resume from the last verified block, avoiding re-transmitting completed data.
- **Directory & Batch Jobs:** Seamless transmission of multi-file selections and nested folder structures with relative path preservation.
- **Filesystem Security:** Comprehensive protection against directory traversal attacks (`../`) and Windows reserved device names (`CON`, `PRN`, `AUX`, `NUL`), with automatic collision avoidance (`File (1).ext`).

#### 🎨 User Interface & Experience
- **Pearl × Obsidian × Liquid Glass Design System:** Clean, modern, distraction-free interface with high-contrast typography and subtle glassmorphic depth.
- **Windows Desktop:**
  - Custom frameless title bar with integrated minimize, maximize, and close controls.
  - Interactive radar view, drag-and-drop file staging, speedometers (`MB/s`), and progress monitors.
  - Instant theme toggle between Obsidian dark mode and Pearl light mode.
- **Android Mobile:**
  - Built with native Jetpack Compose for fluid animations and edge-to-edge layout.
  - Ergonomic 5-tab navigation: Radar, Send, Receive, History, and Settings.
  - Android foreground service integration ensuring uninterrupted transfers when switching apps or locking the screen.

#### 🛡️ Privacy & Security
- **100% Zero-Cloud:** No servers, no accounts, no subscriptions, and zero external internet dependencies.
- **Zero Telemetry:** No analytics beacons, tracking cookies, advertising IDs, or usage logging.
- **Explicit Recipient Consent:** Receiving devices must explicitly inspect and accept incoming transfer manifests before any data is written to disk.

---

### Official Release Artifacts

| Package | Platform & Architecture | Package Format | File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| **`Delynto-0.1.0-Setup.exe`** | Windows 10 / 11 (`x86_64`) | NSIS Executable | 11,632,757 bytes (~11.09 MiB) | `317f9e2409cfcba3ca687e914d2d0dc5f983839ae99cd743ff92720db7fa07d0` |
| **`Delynto-0.1.0.apk`** | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK | 27,415,905 bytes (~26.14 MiB) | `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b` |
| **`SHA256SUMS.txt`** | Multiplatform | Plain Text | 174 bytes | Manifest containing all verified hashes |

---

### Installation Quick Reference

#### Windows Desktop
1. Download [**`Delynto-0.1.0-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/latest/download/Delynto-0.1.0-Setup.exe).
2. Run the installer. When Windows Defender SmartScreen appears, click **"More info"** and **"Run anyway"**.
3. Allow private network communication when prompted by Windows Defender Firewall.

#### Android Mobile
1. Download [**`Delynto-0.1.0.apk`**](https://github.com/impreseo/Delynto-Releases/releases/latest/download/Delynto-0.1.0.apk).
2. Tap the APK to install, enabling **"Allow from this source"** if prompted.
3. Grant notification and storage permissions upon first launch.

---

### Known Limitations
- **Public Wi-Fi AP Isolation:** Public networks (hotels, airports, universities) commonly isolate clients from communicating directly with each other. In such environments, activate an Android **Personal Hotspot** and connect the Windows PC to it, or use the 6-digit PIN direct connect.
- **Windows Defender SmartScreen:** As an open-source beta release without a paid commercial EV certificate, Windows SmartScreen will display an unrecognized publisher prompt.
- **Automated vs Physical Validation:** All automated socket-level tests, JNI bindings, and QUIC transfer pipelines achieved a 100% pass rate (52/52 tests); testing across specific diverse physical phone models is recommended in production deployments.

---

### Official Links
- **GitHub Release:** [https://github.com/impreseo/Delynto-Releases/releases/tag/v0.1.0](https://github.com/impreseo/Delynto-Releases/releases/tag/v0.1.0)
- **Release Repository:** [https://github.com/impreseo/Delynto-Releases](https://github.com/impreseo/Delynto-Releases)
- **Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)
- **Documentation:** [https://github.com/impreseo/Delynto-Releases/tree/main/documentation](https://github.com/impreseo/Delynto-Releases/tree/main/documentation)
- **Issue Tracker:** [https://github.com/impreseo/Delynto/issues](https://github.com/impreseo/Delynto/issues)

---
*Powered by **IMPRESEO LABS** — Copyright © 2026 IMPRESEO LABS. All rights reserved.*
