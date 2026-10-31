# Delynto — File Transfer Guide

**Developed by QUELRAVO • MultiLink**

---

## 1. Transfer Mechanics

Delynto transfers files using a segmented streaming protocol over QUIC / TLS 1.3:

1. **Manifest Exchange:**  
   Before any bytes are sent, the sender transmits a `TransferManifest` containing:
   - File name and relative directory structure.
   - Total file size.
   - Chunk count (fixed 4 MiB chunks).
   - Root SHA-256 Merkle tree hash.
2. **Explicit Recipient Consent:**  
   The receiver’s UI displays the incoming transfer prompt. No file data is written to disk until the user accepts.
3. **Concurrent Chunk Pipeline:**  
   Chunks are streamed concurrently. As each chunk arrives, its individual SHA-256 checksum is verified against the manifest before being committed to temporary staging storage.
4. **Final Assembly & Verification:**  
   Once all chunks have arrived, the receiver reconstructs the file, recalculates the full-file SHA-256 digest, and moves the verified file to the final destination directory.

---

## 2. Directory & Batch Transfers

Delynto supports sending multiple files and entire directory hierarchies in a single operation:
- **Directory Traversal Protection:** Relative file paths are sanitized against path traversal attacks (`../` or absolute root paths are strictly rejected).
- **Reserved Name Sanitization:** Windows-reserved filenames (`CON`, `PRN`, `AUX`, `NUL`, `COM1-9`, `LPT1-9`) are sanitized to prevent operating system crashes.
- **Collision Avoidance:** If a file with the same name already exists in the destination folder, Delynto automatically appends a numerical suffix (e.g., `Report (1).pdf`) instead of silently overwriting existing files.

---

## 3. Interrupted Transfer Recovery & Resume

Network interruptions are common over Wi-Fi when moving between access points or closing laptop lids:
- Chunks that were already verified and committed to SQLite/staging are permanently saved.
- When the connection is re-established, the sender and receiver reconcile state via `TransferResumeRequest`.
- The receiver informs the sender which chunk indexes are already verified; only missing chunks are transmitted.
- **Zero Wasted Bandwidth:** A 10 GB transfer interrupted at 95% only transfers the remaining 5% upon resume.
