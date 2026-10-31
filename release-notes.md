# Delynto v0.2.0 — Universal Connectivity & MultiLink Experience
### Developed by QUELRAVO • MultiLink
**QUELRAVO — INNOVATION BEYOND LIMITS**  
*One Connection. Multiple Ways to Transfer.*  
*Delynto — Powered by QUELRAVO MultiLink*

We are proud to announce the official release of **Delynto** (`v0.2.0`), introducing **QUELRAVO MultiLink** alongside official company rebranding, cross-platform UI parity, and universal connectivity across **Windows 10/11** and **Android 8.0+**.

---

## 📦 Official Distribution Packages & Checksums

| Package Filename | Platform & Architecture | Format | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| [**`Delynto-0.2.0-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.0/Delynto-0.2.0-Setup.exe) | Windows 10 / 11 (`x86_64`) | NSIS Standalone Installer | 11,632,815 bytes (~11.09 MiB) | `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e` |
| [**`Delynto-0.2.0.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.0/Delynto-0.2.0.apk) | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK | 27,638,658 bytes (~26.36 MiB) | `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974` |
| [**`SHA256SUMS.txt`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.2.0/SHA256SUMS.txt) | All Platforms | Plain Text Manifest | 168 bytes | Manifest containing verified hashes |

### Checksum Verification Commands
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\Delynto-0.2.0-Setup.exe -Algorithm SHA256
  ```
  Expected: `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e`

- **Linux / macOS / Android Termux (Bash):**
  ```bash
  sha256sum Delynto-0.2.0.apk
  # Or verify manifest
  sha256sum -c SHA256SUMS.txt
  ```
  Expected: `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974`

---

## ⚡ What's New in v0.2.0

### 1. Official Company Rebranding — QUELRAVO
- **Identity:** Transitioned corporate attribution to **Developed by QUELRAVO** (`QUELRAVO — INNOVATION BEYOND LIMITS`).
- **Unified Branding:** Updated all user-facing footers, splash screens, About dialogues, Settings views, installers, and technical documentation.
- **Product Nomenclature:** Standardized consumer product as **Delynto**, internal networking engine as **RelayMesh**, and connection technology as **QUELRAVO MultiLink**.

### 2. Dedicated MultiLink UI (6 Connection Methods)
Delynto now includes a dedicated **MultiLink** screen on both Windows desktop and Android mobile, allowing users to select, configure, and inspect 6 universal transfer transports:

1. **Wi-Fi / Hotspot (Recommended & Available):** Direct high-speed local encrypted transfer over standard Wi-Fi LAN or mobile phone hotspot (speeds up to 1.2 Gbps).
2. **USB Cable (Requires Setup):** Physical direct USB connection between Android and Windows PC using high-throughput tethered links (speeds up to 5.0 Gbps).
3. **Bluetooth (Available / Fallback):** Direct peer-to-peer connection via Bluetooth Classic / BLE for lightweight transfers and offline fallback when Wi-Fi is unavailable (speeds up to 2.1 Mbps).
4. **Wi-Fi Direct (Requires Setup):** Direct wireless P2P connection established directly between devices without requiring a router or access point (speeds up to 450 Mbps).
5. **USB Tethering (Requires Setup):** Creates a high-performance virtual Ethernet adapter (`192.168.42.x`, RNDIS/NCM) between Android and Windows with zero configuration (speeds up to 480 Mbps).
6. **Internet Relay (Available):** Optional encrypted remote transfer between devices on separate networks. Zero cloud storage, end-to-end encrypted with ChaCha20-Poly1305.

Each method features real-time status indicators (`Available`, `Checking`, `Connecting`, `Connected`, `Requires setup`, `Not supported`), speed ratings, and interactive setup walkthrough guides.

### 3. Unified Cross-Platform Experience
- **Navigation Parity:** Both desktop and mobile navigation now feature 5 harmonious sections: Nearby Radar, MultiLink, Send/Drop Zone, Active Transfers, and Settings.
- **Honest Statuses:** Full runtime state evaluation with zero artificial or misleading statuses.
- **Pearl × Obsidian Visual Hierarchy:** High-contrast, executive-grade design tailored for low-light and bright working environments.

---

## 🔒 Security & Privacy Architecture
- **Local-First / Zero-Cloud:** All discovery and file transfers occur directly peer-to-peer. Zero cloud storage or account requirement.
- **Ed25519 Cryptographic Identity:** Every device maintains an immutable Ed25519 keypair for identity verification and SAS verification codes.
- **Keypair Integrity:** Core keypair implementation (`crates/relaymesh-identity/src/keypair.rs`) cryptographically verified (`72E7EAA278F922CACF7C1BE8909BF6E339CB08F4A3A3555E7CD548ED730D00C0`).
- **Path Traversal Protection:** All incoming file transfers enforce directory traversal mitigation and Windows reserved filename protections.
