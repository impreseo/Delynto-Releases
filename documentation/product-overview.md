# Delynto — Product Overview

**Powered by IMPRESEO LABS**  
**Product Principle:** *JUST OPEN. DISCOVER. CONNECT. SHARE.*

---

## What is Delynto?

**Delynto** is a modern, high-performance, zero-cloud device-to-device file transfer system designed for Windows and Android. Built on the custom Rust **RelayMesh** engine, Delynto allows users to move files of any size between computers, phones, and tablets with zero intermediaries, zero third-party cloud uploads, and zero telemetry.

Unlike commercial sharing tools that harvest telemetry, display advertisements, or tunnel your data through remote cloud servers, Delynto establishes direct, authenticated, encrypted peer-to-peer pipelines using local Wi-Fi, Ethernet, or mobile hotspot networks.

---

## Core Capabilities

### 1. Instant Automatic Discovery
When you launch Delynto on two devices connected to the same local area network, they discover each other automatically using UDP multicast/broadcast on port `53317`. No IP entry, port numbers, or technical network setup is needed.

### 2. Multi-Tier Pairing & Trust
- **One-Tap Connect:** Instant connection with verified peers in your trusted journal.
- **Short 6-Digit Codes:** Human-friendly ephemeral pairing codes (e.g., `482-915`) for fast manual discovery across complex Wi-Fi subnets.
- **QR Code Fallback:** Air-gapped, zero-configuration optical pairing via camera scan or token copy.
- **Short Authentication String (SAS):** Visual cryptographic verification code ensures protection against machine-in-the-middle attacks.

### 3. High-Speed QUIC & UDP Streaming
File transfers leverage modern QUIC transport protocols, providing:
- Multi-stream concurrency.
- Head-of-line blocking elimination.
- High-throughput chunk streaming with 4 MiB transfer segments.
- End-to-end SHA-256 chunk hashing and Merkle root verification.
- Interrupted connection auto-recovery and resume without re-transferring received data.

### 4. Zero Cloud & Total Privacy
- **No Accounts:** No signups, email addresses, phone numbers, or passwords.
- **No Cloud Relay:** Payloads never leave your local physical Wi-Fi or hotspot link.
- **No Analytics / Telemetry:** Zero analytics trackers, telemetry pings, crash reporting beacons, or advertisement SDKs.
- **Local SQLite Journal:** All trusted device keys and transfer history are stored strictly in local SQLite databases on your personal machine.

---

## Visual Identity: Pearl × Obsidian × Liquid Glass

Delynto adheres to an intentional, human-crafted design language:
- **Pearl Mode:** Clean, high-legibility light theme featuring soft alabaster backgrounds (`#F8FAFC`) and refined card borders.
- **Obsidian Mode:** True dark theme (`#090B10` background with `#131722` cards) designed for focused work and low-light environments.
- **Liquid Glass Accents:** Subtle, restrained translucent layer blending with high-contrast violet primary accents (`#7661FF`) and cyan status glows (`#00D1FF`).

---

## Platform Support

| Operating System | Minimum Version | Target Architecture | Native Layer |
| :--- | :--- | :--- | :--- |
| **Windows Desktop** | Windows 10 (Build 19041+) / Windows 11 | `x86_64` (64-bit) | Rust Core via Tauri v2 |
| **Android Mobile** | Android 8.0 Oreo (API 26) or higher | `arm64-v8a`, `x86_64` | Rust Core via JNI FFI + Jetpack Compose |

---

## Attribution & Intellectual Property

Delynto is designed, developed, and maintained by **IMPRESEO LABS**.  
All rights reserved © 2026 IMPRESEO LABS.
