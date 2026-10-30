# Delynto v0.1.0 — Public Beta
### Powered by IMPRESEO LABS
**Tagline:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*

We are proud to announce the first official **Public Beta** release of **Delynto** (`v0.1.0`), a modern, private, zero-cloud device-to-device file transfer client designed for Windows 10/11 and Android.

---

## 🌟 Highlights & Capabilities

- **100% Zero-Cloud Architecture:** Operates completely over local Wi-Fi, Ethernet, or mobile hotspot networks. No accounts, central servers, cloud relays, or telemetry.
- **Wire-Speed QUIC Transport:** Built on the custom Rust **RelayMesh** engine. Segmented 4 MiB chunk streaming over QUIC with TLS 1.3 encryption.
- **Active OS Interface Discovery:** Automatically enumerates operating system network adapters (`GetAdaptersAddresses` on Windows; `getifaddrs` on Android) to discover peers on Wi-Fi, LAN, and offline hotspots without requiring an active internet connection.
- **Mutual Cryptographic Trust:** Self-sovereign Ed25519 node identities. Pairing protected by ephemeral 6-digit PIN codes, QR optical fallback, Short Authentication String (SAS) visual verification, and anti-replay session tracking.
- **Resumable Chunk Pipeline:** Automatically recovers interrupted transfers from the last verified block, avoiding wasted bandwidth.
- **Directory & Batch Jobs:** Seamlessly transmit multi-file collections and nested folders with built-in path traversal (`../`) and Windows reserved name sanitization.
- **Pearl × Obsidian Aesthetic:** Polished light and dark themes with subtle liquid glass depth and custom Windows desktop frameless title bar.

---

## 📦 Release Artifacts & Cryptographic Checksums

| Package | Platform & Architecture | Format | Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- | :--- |
| **`Delynto-0.1.0-Setup.exe`** | Windows 10 / 11 (x86_64) | NSIS Installer | 11,632,472 bytes (~11.09 MiB) | `F8C47D9328FE30A138E9A1CB5CA8614E865B41EEC6648D4D58A14B089D3CE55E` |
| **`Delynto-0.1.0.apk`** | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK | 27,379,041 bytes (~26.11 MiB) | `C0C1C1CFC3F1D96F9399225FEC338FAE3419D5EAC77DDDFB5CF05A75E9DEE3F8` |
| **`SHA256SUMS.txt`** | All Platforms | Text Manifest | 174 bytes | Manifest containing all verified hashes |

---

## 🚀 Installation Quick Guide

### Windows Desktop:
1. Download **`Delynto-0.1.0-Setup.exe`**.
2. Run the installer.
3. *Windows Defender SmartScreen:* Because this beta binary is unsigned, SmartScreen may display an alert. Click **"More info"** > **"Run anyway"**.
4. When prompted by Windows Defender Firewall, allow access on **Private networks** to permit local UDP discovery and QUIC transfer streaming.

### Android Mobile:
1. Download **`Delynto-0.1.0.apk`** to your device.
2. Tap the APK to install. If prompted, enable **"Allow from this source"** in your settings.
3. Open Delynto and grant notification and storage permissions to enable background foreground service transfers.

---

## ⚠️ Known Limitations & Field Verification

- **Public Wi-Fi AP Isolation:** Public networks (hotels, airports, universities) often prohibit client-to-client communication. In these environments, enable an Android **Personal Hotspot** and connect your computer to it, or use the 6-digit code direct connect mode.
- **Physical Device Validation:** All automated socket-level cross-platform loopback tests, Android JNI FFI bindings, and QUIC transfer test suites have achieved a 100% pass rate. Cross-device validation on specific phone hardware models should be evaluated in your target deployment environment.

---

**Full Documentation:** [https://github.com/impreseo/Delynto-Releases/tree/main/documentation](https://github.com/impreseo/Delynto-Releases/tree/main/documentation)  
**Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)  
**Report Issues:** [https://github.com/impreseo/Delynto/issues](https://github.com/impreseo/Delynto/issues)  

*Copyright © 2026 IMPRESEO LABS. All rights reserved.*
