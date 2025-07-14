# 🧠 0Password CTF Challenge — Crack the Vault

Welcome to the **0Password** CTF challenge — a reverse engineering & decryption puzzle for those who enjoy cracking crypto vaults, decoding binaries, and tearing apart Python security mechanisms.

Your objective:  
🔍 **Recover the hidden flag stored in the encrypted `creds.db` database.**

## 📦 Files Provided

You'll receive the following encrypted files:
- `creds.db` — Encrypted SQLite DB storing the flag inside one of the credentials
- `salt.bin` — Random salt (encrypted with device fingerprint)
- `master.hash` — Argon2 hash of the master password (encrypted)
- `device_fingerprint.bin` — 32-byte hardware binding token
- `initialized.lock` — Initialization marker

All files were generated using the password manager [0Password](https://github.com/Z3R0-0x30/0Password-CE), built by **~Prince Patel (0x30)**.

---

## 🛠️ Behind the Scenes

The encryption stack powering this vault includes:

- 🔐 **AES-128 encryption** via `cryptography.Fernet` for credentials  
- 🔐 **Argon2id** hashing for master password  
- 🔐 **Salt encryption** using device-bound fingerprint  
- 🔐 **Master hash encryption** bound to hardware  
- 💾 **SQLite database** (no internet, no cloud — 100% local)

---

## 🎯 Your Goal

> Crack open the database and retrieve the **flag** hidden in the credentials.

**Hints:**
- You don't have the original password.
- You can't decrypt the salt or master hash without reverse engineering the code.
- The flag is inside the `password` field of one record in `creds.db`.
- You can use 0Password.exe with this files to figure out the working, there will be a hidden directory in your system if you have used 0Password, find it and store this 5 files without changing names there so operate it with 0Password.

---

## 💡 Tips

- Analyze how encryption and key derivation works in `0Password`
- You’ll likely need to **replicate or bypass** parts of the encryption chain
- Don’t forget to check the Fernet + Argon2 + fingerprint binding mechanisms

---

## 🧠 Intended For

- CTF Players & Reverse Engineers
- Python Security Enthusiasts
- Cryptography Nerds
- Red Teamers and Cybersecurity Students

---

## ⚠️ Disclaimer

This challenge is for **educational purposes only**. Do not use the techniques learned here for malicious activity.

---

Happy cracking!  
~Prince Patel (0x30) 💻🕶️
