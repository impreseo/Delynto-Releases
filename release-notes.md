# Delynto v0.2.1 — MultiLink Functionality Repair & Production UI/UX Parity
### Developed by QUELRAVO • MultiLink
**QUELRAVO — INNOVATION BEYOND LIMITS**  
*One Connection. Multiple Ways to Transfer.*  
*Delynto — Powered by QUELRAVO MultiLink*

We are pleased to announce the release of **Delynto** (`v0.2.1`), delivering a complete overhaul of the **QUELRAVO MultiLink** interface, repairing method presentation, eliminating confusing technical noise, restoring light and dark theme contrast, removing unverified theoretical speed claims, and establishing unified visual parity across Windows desktop and Android mobile.

---

## 📦 Official Distribution Packages & Checksums (v0.2.1)

| Package Filename | Platform & Architecture | Format | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| [**`Delynto-0.2.1-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.1/Delynto-0.2.1-Setup.exe) | Windows 10 / 11 (`x86_64`) | NSIS Standalone Installer | 11,639,483 bytes (~11.10 MiB) | `b9fa11523d9bfbe0200a230c3ccceb5a8a0461029e9b243620593114a8b257ff` |
| [**`Delynto-0.2.1.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.1/Delynto-0.2.1.apk) | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK (Signed v2) | 27,647,738 bytes (~26.37 MiB) | `689b5fd05953f8c0aa71b786252e16abeb10722e498f775bafa78e6a83832d67` |
| [**`SHA256SUMS.txt`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.1/SHA256SUMS.txt) | All Platforms | Plain Text Manifest | 174 bytes | Manifest containing verified hashes |

### Checksum Verification Commands
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\Delynto-0.2.1-Setup.exe -Algorithm SHA256
  ```
  Expected: `b9fa11523d9bfbe0200a230c3ccceb5a8a0461029e9b243620593114a8b257ff`

- **Linux / macOS / Android Termux (Bash):**
  ```bash
  sha256sum Delynto-0.2.1.apk
  # Or verify manifest
  sha256sum -c SHA256SUMS.txt
  ```
  Expected: `689b5fd05953f8c0aa71b786252e16abeb10722e498f775bafa78e6a83832d67`

---

## ⚡ What's New & Fixed in v0.2.1

### 1. QUELRAVO MultiLink Redesign & UI/UX Defect Rectification
- **Hero Section Overhaul:** Fixed contrast issues across both themes. Heading "QUELRAVO MultiLink", subheading "One Connection. Multiple Ways to Transfer.", and description "Connect your devices through the method that works best for you." Secondary corporate attribution pill.
- **Unified 6-Card System:** Every card shares an identical component layout, background, border, corner radius (18px), and padding. Removed all repetitive question mark help circles in favor of a single clear action button per card.
- **Truthful Availability & Implementation Statuses:**
  - Wi-Fi / Hotspot: Available (Recommended for local wireless).
  - USB Tethering: Available / Requires Setup (Recommended for direct physical cable transfer).
  - USB Cable: Experimental / Direct Cable (Tethering recommended for immediate transfer).
  - Bluetooth: Requires Setup (Offline fallback for light documents & photos).
  - Wi-Fi Direct: Requires Setup (Direct wireless peer-to-peer; mobile hotspot recommended).
  - Internet Relay: In Standby (Zero-cloud remote standby; public infrastructure in standby).
- **Speed Claim Rectification:** Removed unverified theoretical speed numbers (e.g. 1.2 Gbps, 5.0 Gbps). Replaced with honest qualitative throughput tiers (`Local Wireless · High-Speed`, `Direct Hardware · Maximum Cable Speed`, etc.). Real speeds are measured and displayed dynamically during live transfers.
- **Focused Bottom Section:** Replaced raw diagnostic terminology with an active connection status card and setup guidance box. Advanced adapter metrics remain accessible in Settings.

### 2. Mobile Blank Screen Defect (P0) & APK Signing
- Fixed application startup failure on Android devices. Created native `Theme.Delynto` (`#090B10` background, `#131722` surface) in `themes.xml` and applied it in `AndroidManifest.xml`. Wrapped the entire Compose tree in `DelyntoTheme` with explicit `MaterialTheme` dark tokens. Offloaded JNI initialization and event polling to background `Dispatchers.IO` coroutine context. Added an initial branded loading screen to ensure zero black frames during cold boot.
- Android APK v2 signature verified using `apksigner verify --verbose` (Scheme v2: true).

### 3. Preserved Cryptographic Invariants
- `crates/relaymesh-identity/src/keypair.rs` untouched and verified:  
  SHA-256: `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`.

---

# Historical Releases

## Delynto v0.2.0 — Universal Connectivity & MultiLink Experience
*Initial MultiLink release introducing 6 connection transports and QUELRAVO rebranding.*
- Windows: `Delynto-0.2.0-Setup.exe` (SHA-256: `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e`)
- Android: `Delynto-0.2.0.apk` (SHA-256: `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974`)
