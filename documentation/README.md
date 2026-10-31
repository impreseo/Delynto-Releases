# Delynto — Technical & Product Documentation Index

**Product:** Delynto  
**Version:** `v0.2.0` (QUELRAVO MultiLink & Complete Product Update)  
**Attribution:** Developed by **QUELRAVO** (**QUELRAVO — INNOVATION BEYOND LIMITS**)  
**Core Motto:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*  
**Visual Identity:** Pearl × Obsidian × Liquid Glass  

Welcome to the official documentation directory for **Delynto**. This manual provides an exhaustive, engineer-grade guide to understanding, deploying, operating, and auditing Delynto across Windows and Android devices.

---

## 📚 Document Index

| Document | Purpose & Summary |
| :--- | :--- |
| **[Product Overview](product-overview.md)** | Core product philosophy, local-first zero-cloud architecture, and primary capabilities. |
| **[Installation Guide](installation-guide.md)** | Step-by-step instructions for installing on Windows and Android, bypassing SmartScreen, and sideloading. |
| **[Windows Desktop Guide](windows-guide.md)** | Detailed walkthrough of the desktop client, custom title bar, settings, and network configurations. |
| **[Android Mobile Guide](android-guide.md)** | Five-tab mobile interface, background foreground service, battery optimization, and storage access. |
| **[Connection & Pairing Guide](connection-and-pairing.md)** | Automatic local discovery, ephemeral 6-digit PIN codes, QR exchange, and Short Authentication String (SAS). |
| **[File Transfer Guide](file-transfer-guide.md)** | Single file transfers, directory batches, QUIC streaming, chunk verification, and collision resolution. |
| **[Security & Privacy Specification](security-and-privacy.md)** | Cryptographic model, Ed25519 node identities, replay protection, rate limiting, and zero-telemetry guarantee. |
| **[Troubleshooting Guide](troubleshooting.md)** | Diagnostic matrix for AP isolation, firewall blocking, permission denials, and recovery workflows. |
| **[System Requirements](system-requirements.md)** | Hardware, OS version, and network specification compatibility matrices. |
| **[Release Details](release-details.md)** | Compilation toolchains, release artifacts, package sizes, and commit references. |
| **[Checksum Verification](checksums.md)** | Independent cryptographic verification hashes (SHA-256) and instructions. |
| **[Screenshots Gallery](screenshots/README.md)** | Genuine, non-fabricated user interface captures from running applications. |

---

## 🔒 Foundational Principles

1. **Zero Cloud Requirement:** All discovery, negotiation, and data transfers happen directly peer-to-peer over your local Wi-Fi or hotspot. No accounts, servers, or external internet connections are ever required.
2. **Mutual Cryptographic Consent:** Both parties explicitly authorize connections via authenticated Ed25519 handshakes and Short Authentication String (SAS) confirmation.
3. **Restrained, Human-Designed UI:** Built with precision using the Pearl × Obsidian design system, offering seamless contrast in both light and dark environments.
