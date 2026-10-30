# Delynto — System Requirements

**Powered by IMPRESEO LABS**

---

## 🪟 Windows Desktop Requirements

| Requirement | Minimum Specification | Recommended Specification |
| :--- | :--- | :--- |
| **Operating System** | Windows 10 (64-bit, Version 2004 / Build 19041+) | Windows 11 (64-bit, Version 22H2+) |
| **Architecture** | `x86_64` (AMD64 / Intel 64) | `x86_64` multi-core processor |
| **Memory (RAM)** | 2 GB RAM | 4 GB RAM or higher |
| **Storage** | 50 MB for application; space for files | High-speed NVMe SSD |
| **Network** | 802.11n (Wi-Fi 4) or 100 Mbps Ethernet | 802.11ac / 802.11ax (Wi-Fi 5/6) or Gigabit LAN |
| **Privileges** | Standard user (Administrator not required) | Standard user |

---

## 📱 Android Mobile Requirements

| Requirement | Minimum Specification | Recommended Specification |
| :--- | :--- | :--- |
| **Operating System** | Android 8.0 Oreo (API level 26) | Android 12, 13, 14, or higher |
| **Architecture** | `arm64-v8a` (64-bit ARM) or `x86_64` | 64-bit ARM (`arm64-v8a`) |
| **Memory (RAM)** | 2 GB RAM | 4 GB RAM or higher |
| **Storage** | 60 MB for application; space for files | Internal UFS 2.1+ storage |
| **Network** | 2.4 GHz Wi-Fi / Hotspot support | 5 GHz Wi-Fi (Wi-Fi 5 / Wi-Fi 6) |
| **Permissions** | Storage, Notifications, Nearby Devices | Storage, Notifications, Nearby Devices |

---

## 🌐 Network Requirements

- **Protocol:** UDP (mDNS & RelayMesh discovery) on port `53317`.
- **Transfer Transport:** QUIC / UDP streaming on port `41820` (or dynamically allocated).
- **Topology:** Local subnet reachability, direct Wi-Fi LAN, Ethernet switch, or mobile Wi-Fi hotspot.
- **Internet Access:** **NOT REQUIRED.** Operates 100% offline.
