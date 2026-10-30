# Delynto — Cryptographic Checksum Verification

**Powered by IMPRESEO LABS**

To ensure your downloaded Delynto application packages have not been tampered with or corrupted in transit, verify their cryptographic SHA-256 hashes against the official records published below.

---

## 🔒 Official SHA-256 Checksums

| Package Filename | Target OS & Architecture | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- |
| **`Delynto-0.1.0-Setup.exe`** | Windows 10 / 11 (64-bit) | 11,632,472 bytes | `F8C47D9328FE30A138E9A1CB5CA8614E865B41EEC6648D4D58A14B089D3CE55E` |
| **`Delynto-0.1.0.apk`** | Android 8.0+ (ARM64 / x86_64) | 27,379,041 bytes | `C0C1C1CFC3F1D96F9399225FEC338FAE3419D5EAC77DDDFB5CF05A75E9DEE3F8` |

---

## How to Verify

### 1. Windows (PowerShell)
Open PowerShell in the directory where your download is saved:

```powershell
Get-FileHash .\Delynto-0.1.0-Setup.exe -Algorithm SHA256
```

Compare the resulting `Hash` string with:
`F8C47D9328FE30A138E9A1CB5CA8614E865B41EEC6648D4D58A14B089D3CE55E`

### 2. Linux / macOS / Android Termux (Bash)
```bash
sha256sum Delynto-0.1.0.apk
```

Compare the output with:
`c0c1c1cfc3f1d96f9399225fec338fae3419d5eac77dddfb5cf05a75e9dee3f8`

Or verify the manifest automatically if you downloaded `SHA256SUMS.txt`:
```bash
sha256sum -c SHA256SUMS.txt
```

---

## Keypair Architecture Fingerprint
The internal cryptography foundation of RelayMesh identity utilizes an immutable Ed25519 implementation.
- File: `crates/relaymesh-identity/src/keypair.rs`
- SHA-256: `72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`
