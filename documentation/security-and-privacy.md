# Delynto — Security & Privacy Specification

**Developed by QUELRAVO • MultiLink**

---

## 1. Cryptographic Identity Model

Every Delynto node generates a unique, self-sovereign cryptographic identity upon its first run:
- **Algorithm:** Ed25519 (Edwards-curve Digital Signature Algorithm).
- **Key Generation:** High-entropy OS cryptographically secure pseudorandom number generator (CSPRNG via `ring` / `ed25519-dalek`).
- **Identity Fingerprint:** 16-character hexadecimal string formatted with hyphens (e.g. `6E38-D91F-AFEB-4012`) derived from the SHA-256 hash of the node's public key.
- **Keypair Integrity:** Core key generation and signing routines in `relaymesh-identity` are rigorously tested and verified byte-for-byte.

---

## 2. Pairing & Connection Security

- **Session UUIDs:** Every pairing invitation contains a cryptographically random UUID v4 that expires after 120 seconds.
- **Mutual Signature Verification:** Both initiator and responder cryptographically sign the session challenge. A session UUID alone cannot authorize a connection.
- **Short Authentication String (SAS):** Generates a visual 6-digit confirmation number using HMAC/HKDF over the lexicographically sorted node public keys and the session UUID. Eliminates machine-in-the-middle attacks.
- **Replay Protection:** The engine maintains an in-memory set of observed pairing session IDs (`seen_pairing_sessions`). Replayed requests are dropped immediately.
- **Rate Limiting:** Both initiator and responder throttle pairing attempts to a maximum of 5 requests per 60 seconds to prevent denial-of-service spam.

---

## 3. Data-in-Transit Encryption

- **Transport Security:** Control channels and data transfers utilize QUIC with TLS 1.3 encryption.
- **Forward Secrecy:** Session keys are ephemeral and negotiated per connection using Diffie-Hellman key exchange.
- **End-to-End Integrity:** Each 4 MiB transfer chunk is verified with SHA-256 before disk writing. The entire file is verified against its root Merkle digest before moving from staging to the user's Downloads folder.

---

## 4. Local-First & Zero Telemetry Guarantee

- **Zero Cloud Reliance:** All peer discovery, control negotiations, and payload bytes are exchanged directly over the local network.
- **No External Servers:** Delynto functions completely on isolated offline routers or mobile hotspots without an internet connection.
- **No Analytics / Telemetry:** There are no analytics beacons, tracking identifiers, usage metrics, or advertisement SDKs in the codebase.
- **Local Persistence:** Trust journals and transfer records reside exclusively in a local SQLite database (`journal.db`).
