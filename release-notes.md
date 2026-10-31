# Delynto v0.2.1 — Production Reliability & UI/UX Parity Update
### Developed by QUELRAVO • MultiLink
**QUELRAVO — INNOVATION BEYOND LIMITS**  
*One Connection. Multiple Ways to Transfer.*  
*Delynto — Powered by QUELRAVO MultiLink*

We are pleased to announce the release of **Delynto** (`v0.2.1`), a critical production reliability and cross-platform UX update. This release resolves the P0 mobile blank-screen defect, enhances desktop viewport layout to eliminate empty void, adds APK v2 signature verification, and brings full Android–Desktop design parity.

---

## 📦 Official Distribution Packages & Checksums (v0.2.1)

| Package Filename | Platform & Architecture | Format | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| [**`Delynto-0.2.1-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.1/Delynto-0.2.1-Setup.exe) | Windows 10 / 11 (`x86_64`) | NSIS Standalone Installer | 11,629,962 bytes (~11.09 MiB) | `86d1cf38657f1d57185fbcd5201b4b0841d5cf324b3133b2670bf99624d14830` |
| [**`Delynto-0.2.1.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.1/Delynto-0.2.1.apk) | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK (Signed v2) | 27,647,094 bytes (~26.37 MiB) | `1191125786fdb68e62542242c58ad8d36b0aa64087a4e8571d663d8a9e2a4ff8` |
| [**`SHA256SUMS.txt`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.1/SHA256SUMS.txt) | All Platforms | Plain Text Manifest | 174 bytes | Manifest containing verified hashes |

### Checksum Verification Commands
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\Delynto-0.2.1-Setup.exe -Algorithm SHA256
  ```
  Expected: `86d1cf38657f1d57185fbcd5201b4b0841d5cf324b3133b2670bf99624d14830`

- **Linux / macOS / Android Termux (Bash):**
  ```bash
  sha256sum Delynto-0.2.1.apk
  # Or verify manifest
  sha256sum -c SHA256SUMS.txt
  ```
  Expected: `1191125786fdb68e62542242c58ad8d36b0aa64087a4e8571d663d8a9e2a4ff8`

---

## ⚡ What's New & Fixed in v0.2.1

### 1. Critical Mobile Blank Screen Defect Resolution (P0 Defect)
- **Root Cause 1 (Missing Theme Definition):** Android previously inherited `Theme.Material.NoActionBar` with a default black background. Added native `Theme.Delynto` in `themes.xml` (`#090B10` background, `#131722` card surface) and applied it to `AndroidManifest.xml`.
- **Root Cause 2 (Missing Compose Theme):** In `MainActivity.kt`, wrapped the app in `DelyntoTheme` using `darkColorScheme`, ensuring all text, containers, and icons resolve proper contrast.
- **Root Cause 3 (Synchronous JNI UI Thread Blocking):** Moved `NativeBridge.initialize(...)` and native event loop dispatching off `Dispatchers.Main` onto `Dispatchers.IO` coroutine context to prevent UI thread freezes during startup.
- **Root Cause 4 (Uninitialized Screen State):** Added `isEngineInitializing` state with an executive branded loading screen (Delynto logo, company attribution, and spinner) during native engine boot.

### 2. Android APK v2 Cryptographic Signature Fix
- In `apps/android/app/build.gradle.kts`, the `release` build type was missing `signingConfig = signingConfigs.getByName("debug")`.
- Production APK is now cryptographically signed and passes `apksigner verify --verbose` with Scheme v2 active, allowing immediate installation on physical devices without package parse errors.

### 3. Desktop UI/UX Parity & Screen Void Elimination
- **Nearby Devices View:** Added an integrated Quick Share dropzone and QUELRAVO MultiLink guidance tips below discovered device cards to seamlessly occupy high-resolution desktop viewports.
- **MultiLink View:** Added Hardware Diagnostics & Adapter Architecture card providing real-time hardware capabilities, zero-cloud indicators, and adapter telemetry.
- **Settings View:** Added a dedicated Default Downloads Directory configuration card to General preferences with direct folder opening.

### 4. Preserved Cryptographic Invariants
- `crates/relaymesh-identity/src/keypair.rs` untouched and verified:  
  SHA-256: `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`.

---

# Historical Releases

## Delynto v0.2.0 — Universal Connectivity & MultiLink Experience
*Initial MultiLink release introducing 6 connection transports and QUELRAVO rebranding.*
- Windows: `Delynto-0.2.0-Setup.exe` (SHA-256: `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e`)
- Android: `Delynto-0.2.0.apk` (SHA-256: `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974`)
