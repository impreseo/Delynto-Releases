# Delynto — Cryptographic Checksum Verification

**Developed by QUELRAVO • MultiLink**  
**QUELRAVO — INNOVATION BEYOND LIMITS**

To ensure your downloaded Delynto application packages have not been tampered with or corrupted in transit, verify their cryptographic SHA-256 hashes against the official records published below.

---

## 🔒 Official SHA-256 Checksums (v0.2.0)

| Package Filename | Target OS & Architecture | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- |
| **`Delynto-0.2.0-Setup.exe`** | Windows 10 / 11 (64-bit) | 11,632,815 bytes (~11.09 MiB) | `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e` |
| **`Delynto-0.2.0.apk`** | Android 8.0+ (ARM64 / x86_64) | 27,638,658 bytes (~26.36 MiB) | `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974` |

---

## How to Verify

### 1. Windows (PowerShell)
Open PowerShell in the directory where your download is saved:

```powershell
Get-FileHash .\Delynto-0.2.0-Setup.exe -Algorithm SHA256
```

Compare the resulting `Hash` string with:
`a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e`

### 2. Linux / macOS / Android Termux (Bash)
```bash
sha256sum Delynto-0.2.0.apk
```

Compare the output with:
`072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974`

Or verify the manifest automatically if you downloaded `SHA256SUMS.txt`:
```bash
sha256sum -c SHA256SUMS.txt
```

---

## Keypair Architecture Fingerprint
The internal cryptography foundation of RelayMesh identity utilizes an immutable Ed25519 implementation.
- File: `crates/relaymesh-identity/src/keypair.rs`
- SHA-256: `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
