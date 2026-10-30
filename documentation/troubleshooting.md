# Delynto — Troubleshooting Guide

**Powered by IMPRESEO LABS**

---

## 1. Nearby Devices Not Appearing

### Scenario A: Wi-Fi Access Point (Client) Isolation
- **Symptom:** Both devices are connected to the same Wi-Fi network, but neither appears in the Nearby list.
- **Cause:** Public Wi-Fi networks (hotels, airports, universities, coffee shops) often enable **Client Isolation**, which forbids wireless devices from communicating with one another.
- **Solution:**
  1. Use your Android device to turn on a **Personal Mobile Hotspot**.
  2. Connect your Windows PC to the Android hotspot.
  3. Reopen Delynto — discovery will work immediately.
  4. Alternatively, use the **6-digit Pairing Code** or **QR Code** fallback to establish a direct connection.

### Scenario B: Windows Defender Firewall
- **Symptom:** Windows device can see Android, but Android cannot discover Windows.
- **Cause:** Windows Firewall dropped inbound UDP discovery packets.
- **Solution:**
  1. Open Windows **Settings** > **Network & Internet** > **Properties** of your current Wi-Fi.
  2. Ensure your Network profile type is set to **Private** (not Public).
  3. Open **Windows Security** > **Firewall & network protection** > **Allow an app through firewall**.
  4. Find **Delynto** and ensure both **Private** and **Public** checkboxes are checked.

---

## 2. Pairing & Connection Failures

### Scenario A: "Pairing request timed out or cancelled"
- **Cause:** Pairing invitations are ephemeral and expire after 120 seconds.
- **Solution:** Tap **"Refresh Invitation"** or close and reopen the pairing modal on the inviting device, then re-enter the newly generated 6-digit PIN.

### Scenario B: "Too many incoming pairing attempts. Rate limit exceeded."
- **Cause:** To prevent denial-of-service spam, Delynto allows a maximum of 5 pairing requests within a 60-second window.
- **Solution:** Wait 60 seconds before initiating another pairing request.

---

## 3. Transfer Failures & Performance

### Scenario A: Transfer Speed Dropping or Pausing on Android
- **Cause:** Android battery optimization killed or paused the background process when the screen turned off.
- **Solution:**
  1. Open Android **Settings** > **Apps** > **Delynto**.
  2. Tap **Battery** > Select **"Unrestricted"** (allows background data synchronization).
  3. Ensure the Delynto status bar notification remains visible during transfers.

### Scenario B: "Insufficient disk space"
- **Cause:** The destination drive has less free space than the total size of the incoming transfer.
- **Solution:** Free up space on the destination drive or change the destination directory in **Settings**.
