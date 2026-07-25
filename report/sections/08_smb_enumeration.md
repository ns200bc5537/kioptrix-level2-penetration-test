# SMB Enumeration

## Objective

Determine whether the target exposes SMB services that could allow user, share, or system enumeration.

---

## Commands Used

```bash
nmap -sV -p139,445 <TARGET_IP>

nmap --script smb-security-mode -p445 <TARGET_IP>

nmap --script smb-protocols -p445 <TARGET_IP>

smbclient -L //<TARGET_IP>/ -N

nmap --script smb-enum-shares,smb-enum-users,smb-os-discovery -p445 <TARGET_IP>

enum4linux -a <TARGET_IP>

searchsploit samba
```

---

## Findings

- TCP ports 139 and 445 are closed.
- SMB service is not running.
- No NetBIOS information available.
- Anonymous SMB session failed.
- No SMB shares or users could be enumerated.
- Samba exploits are not applicable.

---

## Risk

No SMB-related attack surface was identified because the SMB service is unavailable.

---

## Evidence

- scans/smb/01_smb_version.txt
- scans/smb/02_smb_security.txt
- scans/smb/03_smb_protocols.txt
- scans/smb/04_smb_shares.txt
- scans/smb/06_smb_enum.txt
- scans/smb/07_enum4linux.txt
- scans/smb/08_searchsploit.txt

---

## Screenshots

- screenshots/enumeration/smb_version.png
- screenshots/enumeration/smb_shares.png
- screenshots/enumeration/enum4linux.png
- screenshots/vulnerability-research/searchsploit_samba.png
