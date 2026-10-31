# Delynto — Installation Guide

This guide covers step-by-step instructions for deploying Delynto on Windows 10/11 and Android devices.

---

## 🪟 Windows Desktop Installation

### Prerequisites
- Windows 10 (64-bit, Version 2004 or later) or Windows 11.
- Administrator privileges are **not required**; Delynto installs directly into the current user's profile.

### Step-by-Step Installation
1. Download **`Delynto-0.2.0-Setup.exe`** from the [Delynto-Releases](https://github.com/impreseo/Delynto-Releases/releases/latest) repository.
2. Verify the SHA-256 hash using PowerShell:
   ```powershell
   Get-FileHash .\Delynto-0.2.0-Setup.exe -Algorithm SHA256
   ```
   Ensure it matches:
   `a0a2a0427f1f26e1a94ed31ad6be6e74bb846a111dd61df28d704c9d8baedc6e`
3. Double-click `Delynto-0.2.0-Setup.exe`.
4. **SmartScreen Warning Resolution:**  
   Because this initial public beta binary is open-source and unsigned (does not carry an expensive paid EV commercial certificate), Windows Defender SmartScreen may display:
   > *"Windows protected your PC — Microsoft Defender SmartScreen prevented an unrecognized app from starting."*
   - Click **"More info"**.
   - Click **"Run anyway"**.
5. Follow the setup wizard. Delynto installs to:
   ```text
   %LOCALAPPDATA%\Programs\Delynto
   ```
6. **Windows Firewall Prompt:**  
   Upon first launch, Windows Defender Firewall will ask if Delynto can communicate over your network:
   - Check **"Private networks, such as my home or work network"**.
   - Click **"Allow access"**.
   *(Note: This allows local UDP peer discovery on port 53317 and QUIC transfer streaming).*

---

## 📱 Android Installation

### Prerequisites
- Android 8.0 Oreo (API level 26) or newer.
- ARM64 (`arm64-v8a`) or x86_64 device.

### Step-by-Step Installation
1. Download **`Delynto-0.2.0.apk`** to your phone or tablet.
2. Verify the SHA-256 hash in Termux or your terminal:
   ```bash
   sha256sum Delynto-0.2.0.apk
   ```
   Ensure it matches:
   `072feaf1b5c0c53b6def5cc358d1b92419b4dd2f0b0426737e75ccf6eba0a974`
3. Tap the downloaded APK in your Notifications or File Manager app.
4. **Install Unknown Apps Permission:**  
   If Android alerts that installs from this source are not permitted:
   - Tap **"Settings"**.
   - Toggle **"Allow from this source"** to ON.
   - Return to the installer and tap **"Install"**.
5. **App Permissions:**  
   When launching Delynto for the first time:
   - **Notifications:** Grant permission so Delynto can display transfer progress in your status bar.
   - **Storage Access:** Grant permission when saving received files or browsing folders to send.
   - **Nearby Devices (Android 12+):** Allow local Wi-Fi multicast peer discovery.

---

## 🗑️ Uninstallation

### Windows:
- Open **Windows Settings** > **Apps** > **Installed apps**.
- Locate **Delynto** and click **Uninstall**, or launch `Uninstall Delynto.exe` from `%LOCALAPPDATA%\Programs\Delynto`.
- Your downloaded files in `Downloads\Delynto` and local database keys are preserved to prevent data loss.

### Android:
- Long-press the **Delynto** app icon on your home screen or app drawer.
- Tap **App info** > **Uninstall** (or drag to the Trash icon).
