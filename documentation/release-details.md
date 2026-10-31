# Delynto — Release Details & Build Metadata

**Product:** Delynto  
**Version:** `v0.2.0` (QUELRAVO MultiLink & Complete Product Update)  
**Attribution:** Developed by **QUELRAVO** (**QUELRAVO — INNOVATION BEYOND LIMITS**)  
**Release Date:** October 31, 2026  
**Primary Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)  
**Release Repository:** [https://github.com/impreseo/Delynto-Releases](https://github.com/impreseo/Delynto-Releases)  

---

## 📦 Verified Deliverables

| Deliverable Artifact | Target OS | Architecture | Package Format | File Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`Delynto-0.2.0-Setup.exe`** | Windows 10/11 | `x86_64` | NSIS Executable | 11,632,815 bytes (~11.09 MiB) | `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e` |
| **`Delynto-0.2.0.apk`** | Android 8.0+ | `arm64-v8a`, `x86_64` | Android APK | 27,638,658 bytes (~26.36 MiB) | `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974` |
| **`SHA256SUMS.txt`** | All | Multi | Plain Text | 168 bytes | Manifest file containing cryptographic hashes |

---

## 🛠️ Build Environment

- **Rust Compiler:** `rustc 1.85.0-nightly` / stable compatible
- **Tauri Toolchain:** Tauri v2.12.4 (`@tauri-apps/cli`)
- **Android Gradle Plugin (AGP):** 8.7.2
- **Android NDK:** 26.3.11579264
- **Android SDK:** API Level 35
- **Node.js Environment:** Node v20.x / Vite 6.4.5 / React 18

---

## 🧪 Verification & Test Results

### 1. Rust Core Engine & Protocol
- **Total Workspace Tests:** Automated tests executed via `cargo test --workspace`.
- **Pass Rate:** 100% (All passed; 0 failed; 0 ignored).
- **Tested Modules:**
  - `relaymesh_transport`: MultiLink manager, 6 transport kinds, availability checking, latency/speed scoring.
  - `relaymesh_core`: Engine integration, MultiLink method enumeration and switching.
  - `relaymesh_discovery`: Broadcast, hotspot probing, and reciprocal announcement tests.
  - `pairing_trust`: Handshake, invitation expiry, revocation, short authentication string symmetry.
  - `transfer_e2e`: End-to-end QUIC streaming, chunk verification, zero-byte handling, SHA-256 matching.
  - `cross_platform_android`: JNI FFI, serialization, state machine parity.
  - `traversal_security`: Directory traversal and reserved filename attack mitigation.
  - `corruption_fault_injection`: Corrupted chunk detection and retransmission.
  - `relaymesh_persistence`: Journaling, chunk invalidation, recovery.
  - `relaymesh_protocol`: Manifest validation, candidate exchange, pairing tokens.
  - `relaymesh_storage`: Staging, sanitization, collision avoidance.
  - `relaymesh_ffi`: MultiLink FFI endpoints, lifecycle, panic safety, response serialization.
  - `relaymesh_identity`: SAS symmetry, signature roundtrip.

### 2. Keypair Security Integrity
- **File:** `crates/relaymesh-identity/src/keypair.rs`
- **Expected & Verified SHA-256:**  
  `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
- **Integrity Status:** EXACT MATCH — Byte-for-byte preserved.
