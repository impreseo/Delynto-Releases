# Delynto — Release Details & Build Metadata

**Product:** Delynto  
**Version:** `v0.1.0` (Public Beta)  
**Attribution:** Powered by **IMPRESEO LABS**  
**Release Date:** October 30, 2026  
**Primary Source Repository:** [https://github.com/impreseo/Delynto](https://github.com/impreseo/Delynto)  
**Release Repository:** [https://github.com/impreseo/Delynto-Releases](https://github.com/impreseo/Delynto-Releases)  

---

## 📦 Verified Deliverables

| Deliverable Artifact | Target OS | Architecture | Package Format | File Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`Delynto-0.1.0-Setup.exe`** | Windows 10/11 | `x86_64` | NSIS Executable | 11,632,472 bytes (~11.09 MiB) | `F8C47D9328FE30A138E9A1CB5CA8614E865B41EEC6648D4D58A14B089D3CE55E` |
| **`Delynto-0.1.0.apk`** | Android 8.0+ | `arm64-v8a`, `x86_64` | Android APK | 27,379,041 bytes (~26.11 MiB) | `C0C1C1CFC3F1D96F9399225FEC338FAE3419D5EAC77DDDFB5CF05A75E9DEE3F8` |
| **`SHA256SUMS.txt`** | All | Multi | Plain Text | 174 bytes | Manifest file containing cryptographic hashes |

---

## 🛠️ Build Environment

- **Rust Compiler:** `rustc 1.85.0-nightly (56fb4db66 2024-12-08)` / stable compatible
- **Tauri Toolchain:** Tauri v2.3+ (`@tauri-apps/cli`)
- **Android Gradle Plugin (AGP):** 8.6.0
- **Android NDK:** 27.2.12479018
- **Android SDK:** API Level 34 (Upside Down Cake)
- **Node.js Environment:** Node v20.x / Vite 6.4.5 / React 18

---

## 🧪 Verification & Test Results

### 1. Rust Core Engine & Protocol
- **Total Workspace Tests:** 52 automated tests executed via `cargo test --workspace`.
- **Pass Rate:** 100% (52 passed; 0 failed; 0 ignored).
- **Tested Modules:**
  - `pairing_trust`: 5/5 passed (handshake, invitation expiry, revocation, short authentication string symmetry).
  - `transfer_e2e`: 8/8 passed (end-to-end QUIC streaming, chunk verification, zero-byte handling, SHA-256 matching).
  - `cross_platform_android`: 8/8 passed (JNI FFI, serialization, state machine parity).
  - `traversal_security`: 2/2 passed (directory traversal and reserved filename attack mitigation).
  - `corruption_fault_injection`: 1/1 passed (corrupted chunk detection and retransmission).

### 2. Keypair Security Integrity
- **File:** `crates/relaymesh-identity/src/keypair.rs`
- **Expected & Verified SHA-256:**  
  `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
- **Integrity Status:** EXACT MATCH — Byte-for-byte preserved.

### 3. Physical Hardware Status
- **Inspection Result:** No physical Android hardware was attached to the build host via ADB during this session.
- **Verification Distinction:** Automated socket-level loopback, FFI integration, and simulated network tests are 100% verified. Physical cross-device deployment remains open for multi-hardware field validation.
