# Delynto — Release Details & Build Metadata

**Product:** Delynto  
**Version:** `v0.2.1` (Production Reliability, MultiLink Functionality & UI/UX Parity)  
**Attribution:** Developed by **QUELRAVO** (**QUELRAVO — INNOVATION BEYOND LIMITS**)  
**Release Date:** October 31, 2026  
**Primary Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)  
**Release Repository:** [https://github.com/impreseo/Delynto-Releases](https://github.com/impreseo/Delynto-Releases)  

---

## 📦 Verified Deliverables (v0.2.1)

| Deliverable Artifact | Target OS | Architecture | Package Format | File Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`Delynto-0.2.1-Setup.exe`** | Windows 10/11 | `x86_64` | NSIS Executable | 11,639,483 bytes (~11.10 MiB) | `b9fa11523d9bfbe0200a230c3ccceb5a8a0461029e9b243620593114a8b257ff` |
| **`Delynto-0.2.1.apk`** | Android 8.0+ | `arm64-v8a`, `x86_64` | Android APK (Signed v2) | 27,647,738 bytes (~26.37 MiB) | `689b5fd05953f8c0aa71b786252e16abeb10722e498f775bafa78e6a83832d67` |
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

### 1. QUELRAVO MultiLink Redesign & Defect Rectification
- **Hero Section:** Clean high contrast in both Pearl (light) and Obsidian (dark) modes. Primary heading "QUELRAVO MultiLink", violet subheading "One Connection. Multiple Ways to Transfer.", and description "Connect your devices through the method that works best for you." Secondary corporate attribution pill.
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
- Theme definition (`Theme.Delynto`), `MaterialTheme` Compose wrapper, and background `Dispatchers.IO` JNI offloading guarantee cold-boot rendering with zero blank frames.
- Android APK v2 signature verified using `apksigner verify --verbose` (Scheme v2: true).

### 3. Keypair Security Integrity
- **File:** `crates/relaymesh-identity/src/keypair.rs`
- **Expected & Verified SHA-256:**  
  `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
- **Integrity Status:** EXACT MATCH — Byte-for-byte preserved.
