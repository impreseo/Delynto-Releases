# Delynto — Cryptographic Checksum Verification

**Powered by IMPRESEO LABS**

To ensure your downloaded Delynto application packages have not been tampered with or corrupted in transit, verify their cryptographic SHA-256 hashes against the official records published below.

---

## 🔒 Official SHA-256 Checksums

| Package Filename | Target OS & Architecture | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- |
| **`Delynto-0.1.0-Setup.exe`** | Windows 10 / 11 (64-bit) | 11,632,757 bytes | `317f9e2409cfcba3ca687e914d2d0dc5f983839ae99cd743ff92720db7fa07d0` |
| **`Delynto-0.1.0.apk`** | Android 8.0+ (ARM64 / x86_64) | 27,415,905 bytes | `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b` |

---

## How to Verify

### 1. Windows (PowerShell)
Open PowerShell in the directory where your download is saved:

```powershell
Get-FileHash .\Delynto-0.1.0-Setup.exe -Algorithm SHA256
```

Compare the resulting `Hash` string with:
`317f9e2409cfcba3ca687e914d2d0dc5f983839ae99cd743ff92720db7fa07d0`

### 2. Linux / macOS / Android Termux (Bash)
```bash
sha256sum Delynto-0.1.0.apk
```

Compare the output with:
`ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b`

Or verify the manifest automatically if you downloaded `SHA256SUMS.txt`:
```bash
sha256sum -c SHA256SUMS.txt
```

---

## Keypair Architecture Fingerprint
The internal cryptography foundation of RelayMesh identity utilizes an immutable Ed25519 implementation.
- File: `crates/relaymesh-identity/src/keypair.rs`
- SHA-256: `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
