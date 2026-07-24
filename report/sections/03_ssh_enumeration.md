# SSH Enumeration

## Objective

Enumerate the SSH service and identify supported algorithms and potential weaknesses.

---

## Commands Used

```bash
nmap -sV -p22 <TARGET_IP>

ssh -vvv root@<TARGET_IP>

nmap --script ssh2-enum-algos -p22 <TARGET_IP>

nmap --script ssh-hostkey -p22 <TARGET_IP>

searchsploit openssh
```

---

## Findings

- OpenSSH 3.9p1 detected.
- Legacy key exchange algorithms supported.
- RSA and DSA host keys identified.
- Multiple outdated encryption algorithms enabled.
- Public exploits available for similar OpenSSH versions.

---

## Risk

The SSH service is outdated and exposes legacy cryptographic algorithms. Although no direct exploit was confirmed during enumeration, the service requires additional assessment.

---

## Evidence

- scans/ssh/01_ssh_version.txt
- scans/ssh/02_ssh_banner.txt
- scans/ssh/03_ssh_algorithms.txt
- scans/ssh/04_ssh_hostkey.txt
- scans/ssh/05_searchsploit.txt

---

## Screenshots

- screenshots/enumeration/ssh_version.png
- screenshots/enumeration/ssh_algorithms.png
- screenshots/enumeration/ssh_hostkeys.png
