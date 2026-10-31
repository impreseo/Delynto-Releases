# Delynto v0.1.2 — Hotspot Connectivity & UX Update
### Powered by IMPRESEO LABS
**Tagline:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*

We are pleased to announce the official release of **Delynto** (`v0.1.2`), our major **Hotspot Connectivity & UX Update** for **Windows 10/11** and **Android 8.0+**.

This release brings zero-config **Hotspot-First Connectivity**—allowing instant, reliable discovery and high-speed local file transfer when an Android phone hosts a mobile hotspot and a Windows PC connects to it (or vice versa), without requiring an external internet connection or router. It also delivers a complete user interface decluttering, removing low-level diagnostic noise in favor of clean, responsive device cards and streamlined pairing workflows.

---

## 📦 Official Distribution Packages & Checksums

| Package Filename | Platform & Architecture | Format | Exact File Size | Cryptographic SHA-256 Hash |
| :--- | :--- | :--- | :--- | :--- |
| [**`Delynto-0.1.2-Setup.exe`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.2/Delynto-0.1.2-Setup.exe) | Windows 10 / 11 (`x86_64`) | NSIS Standalone Installer | 11,634,858 bytes (~11.10 MiB) | `efb3ff7a6ed1466faa97d77752a45855fd2147b99748aed7acf4a09110aa152f` |
| [**`Delynto-0.1.2.apk`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.2/Delynto-0.1.2.apk) | Android 8.0+ (`arm64-v8a`, `x86_64`) | Android APK | 27,415,905 bytes (~26.14 MiB) | `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b` |
| [**`SHA256SUMS.txt`**](https://github.com/impreseo/Delynto-Releases/releases/download/v0.1.2/SHA256SUMS.txt) | All Platforms | Plain Text Manifest | 174 bytes | Manifest containing all verified hashes |

### Checksum Verification Commands
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\Delynto-0.1.2-Setup.exe -Algorithm SHA256
  ```
  Expected: `efb3ff7a6ed1466faa97d77752a45855fd2147b99748aed7acf4a09110aa152f`

- **Linux / macOS / Android Termux (Bash):**
  ```bash
  sha256sum Delynto-0.1.2.apk
  # Or verify manifest
  sha256sum -c SHA256SUMS.txt
  ```
  Expected: `ae4e3a9029ef7a82bfa0e2336864492e1e68e5b44187aee1b819903854c1780b`

---

## ⚡ What's New in v0.1.2

### 1. Hotspot-First Zero-Configuration Connectivity
- **The Challenge:** When an Android phone enables a mobile hotspot and a Windows PC joins as a Wi-Fi client (or vice versa), Android tethering firewalls (`iptables` / driver powersave) frequently drop broadcast packets (`255.255.255.255`, `192.168.43.255`) and multicast groups (`239.255.0.1`), rendering devices invisible to each other.
- **The Solution:**
  - **Gateway Candidate Probing:** Delynto automatically computes the subnet default gateway `((ip & netmask) | 1)` on port `53317`. A Windows PC connected to an Android hotspot (`192.168.43.x`) immediately sends direct unicast discovery probes to `192.168.43.1:53317`.
  - **Tethering DHCP Client Sweeping:** When the host device possesses a `.1` address on standard mobile hotspot subnets (`192.168.43.0/24`, `192.168.49.0/24`, or `192.168.50.0/24`), it sweeps candidate client IPs (`.2` through `.25`) over UDP.
  - **Reciprocal Unicast Announcements:** Upon receiving a valid discovery packet from any new or updated peer, the discovery receiver immediately replies with an explicit reciprocal unicast announcement directly to the sender's source IP and port. Even if the network enforces client isolation, discovery is established bidirectionally in milliseconds.

### 2. Complete Devices Screen Overhaul & UI Decluttering
- **Noise Elimination:** Removed diagnostic clutter from primary views:
  - Eliminated RelayMesh port badges, STUN candidate count badges, LAN host badges, route probing buttons, and raw cryptographic fingerprints.
- **Clean Device Cards:** Each discovered peer displays:
  - Platform device icon (Windows laptop / Android smartphone).
  - Clean device name.
  - Platform identity.
  - Live status indicator ("Online").
  - Prominent action button: **Send Files** (for trusted/paired devices) or **Connect** (for new nearby devices).
- **Secondary Modals:** Direct IP input and QR pairing are moved into clean, dedicated modals that keep the main interface uncluttered.
- **Hotspot-First Guidance:** The empty state now provides friendly, actionable guidance:
  > *"Connect both devices to the same Wi-Fi network. Using your phone's hotspot? Turn it on and connect your PC to it."*

### 3. Cross-Platform Consistency
- Standardized UI scope to strictly supported platforms: **Windows** and **Android**. Removed mock/unsupported Mac and Linux references from platform filters, activity logs, and device selection dialogs.
- Harmonized Pearl × Obsidian theme switching, navigation headers, and status rails across desktop and mobile.

---

## 📱 Mobile Hotspot Usage Guide

### Scenario: Sharing Between Phone and PC Without a Router
1. On your **Android device**, turn on **Personal Hotspot / Mobile Hotspot**.
2. On your **Windows PC**, connect to the hotspot's Wi-Fi network.
3. Open **Delynto** on both devices.
4. Within seconds, your devices will appear in the **Nearby Devices** list.
5. Click **Connect** to pair, then select files to transfer at direct local Wi-Fi speeds.

---

## 🔒 Security & Privacy Architecture
- **Local-First / Zero-Cloud:** All discovery and file transfers occur entirely across the local network link. No telemetry, user accounts, or external servers are utilized.
- **Ed25519 Cryptographic Identity:** Every device maintains an immutable Ed25519 keypair for identity verification and SAS verification codes.
- **Path Sanitization:** All incoming transfers strictly enforce directory traversal and Windows reserved filename protections.
