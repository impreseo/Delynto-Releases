# Delynto — Release Details & Build Metadata

**Product:** Delynto  
**Version:** `v0.2.1` (Production Reliability, Android Blank Screen Repair & UI/UX Parity)  
**Attribution:** Developed by **QUELRAVO** (**QUELRAVO — INNOVATION BEYOND LIMITS**)  
**Release Date:** October 31, 2026  
**Primary Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)  
**Release Repository:** [https://github.com/impreseo/Delynto-Releases](https://github.com/impreseo/Delynto-Releases)  

---

## 📦 Verified Deliverables (v0.2.1)

| Deliverable Artifact | Target OS | Architecture | Package Format | File Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`Delynto-0.2.1-Setup.exe`** | Windows 10/11 | `x86_64` | NSIS Executable | 11,629,962 bytes (~11.09 MiB) | `86d1cf38657f1d57185fbcd5201b4b0841d5cf324b3133b2670bf99624d14830` |
| **`Delynto-0.2.1.apk`** | Android 8.0+ | `arm64-v8a`, `x86_64` | Android APK (Signed v2) | 27,647,094 bytes (~26.37 MiB) | `1191125786fdb68e62542242c58ad8d36b0aa64087a4e8571d663d8a9e2a4ff8` |
| **`SHA256SUMS.txt`** | All | Multi | Plain Text | 174 bytes | Manifest file containing cryptographic hashes |

---

## 🛠️ Build Environment

- **Rust Compiler:** `rustc 1.85.0-nightly` / stable compatible
- **Tauri Toolchain:** Tauri v2.12.4 (`@tauri-apps/cli`)
- **Android Gradle Plugin (AGP):** 8.7.2
- **Android NDK:** 26.3.11579264
- **Android SDK:** API Level 35
- **Node.js Environment:** Node v20.x / Vite 6.4.5 / React 18

---

## 🧪 Verification & Acceptance Results

### 1. Root Cause Resolution (P0 Blank Screen Defect)
- **Theme Definition:** Created native `Theme.Delynto` in `apps/android/app/src/main/res/values/themes.xml` with `#090B10` background and `#131722` surface cards, replacing the bare Android system theme.
- **Compose Theme Wrapper:** Wrapped the entire Android UI tree in `DelyntoTheme` with explicit `MaterialTheme` dark color scheme.
- **Asynchronous JNI Offloading:** Offloaded `NativeBridge.initialize(...)` and native event loop dispatching from `Dispatchers.Main` to `Dispatchers.IO`, preventing UI thread hangs.
- **Engine Initialization Loading Screen:** Added a branded initialization state with Delynto logo, company attribution, and spinner to guarantee zero black frames during cold boot.
- **APK v2 Signature:** Configured `signingConfig = signingConfigs.getByName("debug")` in Gradle `release` buildType so production APKs pass Android package verification. Verified using `apksigner verify --verbose` (Scheme v2: true).

### 2. Desktop UI Parity & Void Elimination
- **Nearby Devices:** Added Quick Share dropzone card and QUELRAVO MultiLink connection guidance below discovered devices, filling desktop viewport at 1080p and 1440p resolutions.
- **MultiLink:** Added Hardware Diagnostics & Architecture Card with interface capabilities, zero-cloud indicators, and real-time adapter metrics.
- **Settings:** Added Downloads Directory Management card to General preferences.

### 3. Keypair Security Integrity
- **File:** `crates/relaymesh-identity/src/keypair.rs`
- **Expected & Verified SHA-256:**  
  `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
- **Integrity Status:** EXACT MATCH — Byte-for-byte preserved.
