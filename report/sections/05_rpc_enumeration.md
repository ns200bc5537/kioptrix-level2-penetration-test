# RPC Enumeration

## Objective

Enumerate RPC services exposed by the target.

---

## Commands Used

```bash
nmap -sV -p111 <TARGET_IP>

rpcinfo -p <TARGET_IP>

nmap --script rpcinfo -p111 <TARGET_IP>

searchsploit rpcbind
```

---

## Findings

- rpcbind Version 2 detected.
- Portmapper service available.
- RPC status service exposed.
- Only Denial-of-Service exploits publicly available.

---

## Risk

RPC services expose additional information about the system and may increase the attack surface.

---

## Evidence

- scans/rpc/01_rpc_version.txt
- scans/rpc/02_rpcinfo.txt
- scans/rpc/03_rpc_nmap.txt

---

## Screenshots

- screenshots/enumeration/rpcinfo.png

