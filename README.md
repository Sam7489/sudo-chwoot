# 🚨 CVE-2025-32463 - Sudo EoP Exploit (PoC)

This repository contains a **Proof of Concept (PoC)** exploit script targeting the vulnerability **CVE-2025-32463**, affecting `sudo` versions **1.9.14 to 1.9.17**.

> 🔥 Exploit by [Rich Mirch](https://github.com/richmirch)  
> 🐚 Repo maintained and shared for educational and research purposes by [@Sam7489](https://github.com/Sam7489)

## 📌 About the Vulnerability

**CVE-2025-32463** is a **local privilege escalation vulnerability** discovered in `sudo`, where the misuse of the `-R` option (used to set a custom root directory) combined with a crafted `nsswitch.conf` file allows arbitrary shared object injection and execution with **root privileges**.

- ✅ Affects: `sudo` versions **1.9.14 → 1.9.17**
- ❌ Fixed in: `sudo` **1.9.18 and above**
- ⚠️ Impact: Local users can escalate privileges and spawn a **root shell**.

## 🔍 Exploit Behavior

This PoC:
- Creates a malicious **NSS shared library** that grants root access.
- Constructs a fake `nsswitch.conf` file to load the custom NSS module.
- Uses `sudo -R` to execute within a fake root directory that contains the crafted config and library.
- Spawns a **root shell** if successful.

---

## 🧪 Usage

> ⚠️ Use in **lab environments** only. Do not run this on production systems.

```bash
chmod +x sudo-chwoot.sh
./sudo-chwoot.sh
