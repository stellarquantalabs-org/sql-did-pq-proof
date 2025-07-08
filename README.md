# sql-did-pq-proof
# (README.md) Post-Quantum Signature Timestamp for SQL Verify
⛓️ **Timestamped on Bitcoin via OpenTimestamps** `✔️`

This repository contains a Bitcoin-anchored timestamp proof for a verifiable credential archive signed using post-quantum cryptography (Dilithium). Anyone can independently verify that this archive existed at the time of timestamping.

Our intent is to publicly prove authorship and cryptographic integrity, anchored in a **trustless, verifiable, and decentralized** way.

## 📂 Included Files

| File                          | Purpose                                                             |
|-------------------------------|---------------------------------------------------------------------|
| `msg.txt`                     | The original signed message (verifiable credential anchor)          |
| `dilithium-public.key`        | Public key used to verify the signature                             |
| `signature.txt`               | Post-quantum signature (Dilithium Level III) of `msg.txt`           |
| `build-hashlog.sha256`        | SHA-256 hash of the file bundle                                     |
| `build-hashlog.sha256.ots`    | Bitcoin-anchored OpenTimestamps proof for the hash                  |
| `ots-timestamp-log.md`        | Raw terminal output of the timestamping process                     |

## ⚙️ Verifying on Ubuntu (Recommended)

For best compatibility and cryptographic security, we recommend verifying the timestamp using Ubuntu (via WSL on Windows or natively on Linux/macOS).

### 1. Install WSL with Ubuntu (Windows only)
```powershell
wsl --install
```
Then open Ubuntu and set your username/password.
### 2. Install Python + OpenTimestamps:
```bash
sudo apt update
sudo apt install python3-pip -y
pip3 install opentimestamps-client
```
### 3. Clone this repo and verify:
```bash
git clone https://github.com/stellarquantalabs-org/sql-did-pq-proof.git
cd sql-did-pq-proof
ots verify build-hashlog.sha256.ots
```
You should see confirmations from OpenTimestamps calendars showing anchoring to Bitcoin.


## ⛓️ Verify the Bitcoin Timestamp (Proof-of-Existence)
To verify the SHA-256 hash of the message archive was anchored into the Bitcoin blockchain:
```bash
# 1. Install OpenTimestamps
pip install opentimestamps-client

# 2. Verify the timestamp
ots verify build-hashlog.sha256.ots
```

# You should see something like:
```bash
Assuming target filename is 'build-hashlog.sha256'
Got 1 attestation(s) from https://finney.calendar.eternitywall.com
Got 1 attestation(s) from https://bob.btc.calendar.opentimestamps.org
Got 1 attestation(s) from https://btc.calendar.catallaxy.com
Got 1 attestation(s) from https://alice.btc.calendar.opentimestamps.org
File anchored in Bitcoin blockchain in block 847003
Timestamp complete
```
✅ This confirms the hash existed publicly at that point in time—immutably recorded on Bitcoin.


## 🔐 Verify the Signature (Optional)
To verify the signature for `msg.txt` using the public key:

- Import the public key from `dilithium-public.key`
- Use your verifier to check that `signature.txt` is valid against `msg.txt`

We’ll provide a WASM verifier soon for browser/offline validation.

## 🛡️ Statement of Integrity

This cryptographic proof was created by Jennifer Aun as part of the SQL Verify decentralized identity project. The goal is to demonstrate authorship, cryptographic authenticity, and timestamped existence of our credential system using post-quantum cryptography and decentralized blockchain anchoring.

This proof is publicly accessible so anyone can verify its authenticity without needing permission from any central authority.

Trust anchored by math— not marketing.

## 🧠 Learn More:

- [OpenTimestamps.org](https://opentimestamps.org)
- [CRYSTALS-Dilithium](https://pq-crystals.org/dilithium/)
- [W3C Verifiable Credentials](https://www.w3.org/TR/vc-data-model/)
