# SMB Enumeration

## Why Enumerate SMB?

SMB (Server Message Block) is commonly used for:

- File sharing
- User enumeration
- Anonymous shares
- Remote administration

If SMB is exposed, it can often lead to sensitive information disclosure or even remote code execution.

---

## 1. Detect SMB Service

### Command

```bash
nmap -sV -p139,445 <TARGET_IP>
```

### Result

```
139/tcp closed netbios-ssn
445/tcp closed microsoft-ds
```

### Explanation

- SMB ports are closed.
- No SMB service is available.
- Further SMB enumeration is not possible.

---

## 2. SMB Security Mode

### Command

```bash
nmap --script smb-security-mode -p445 <TARGET_IP>
```

### Result

```
445/tcp closed
```

### Explanation

The SMB security mode cannot be identified because the SMB service is not running.

---

## 3. SMB Protocol Enumeration

### Command

```bash
nmap --script smb-protocols -p445 <TARGET_IP>
```

### Result

```
445/tcp closed
```

### Explanation

No SMB protocol versions are available because the service is closed.

---

## 4. Enumerate SMB Shares

### Command

```bash
smbclient -L //<TARGET_IP>/ -N
```

### Result

```
NT_STATUS_CONNECTION_REFUSED
```

### Explanation

The server refused the connection because SMB is unavailable.

---

## 5. Enumerate Accessible Shares

### Command

```bash
smbclient //<TARGET_IP>/SHARENAME -N
```

### Result

```
NT_STATUS_CONNECTION_REFUSED
```

### Explanation

No shares can be accessed because SMB is not running.

---

## 6. SMB NSE Enumeration

### Command

```bash
nmap --script smb-enum-shares,smb-enum-users,smb-os-discovery -p445 <TARGET_IP>
```

### Result

```
445/tcp closed
```

### Explanation

No SMB information can be collected.

---

## 7. enum4linux

### Command

```bash
enum4linux -a <TARGET_IP>
```

### Result

- Workgroup not found
- NetBIOS did not respond
- Anonymous session failed

### Explanation

Since SMB is unavailable, enum4linux cannot enumerate users or shares.

---

## 8. Searchsploit

### Command

```bash
searchsploit samba
```

### Explanation

Many Samba exploits exist, but none are applicable because no Samba service is running on the target.

---

## Summary

| Finding | Status |
|----------|--------|
| SMB Ports | Closed |
| NetBIOS | Not Available |
| Anonymous Login | Failed |
| Shares | None |
| Users | None |
| Exploitable | No |

---

## Pentester Notes

When SMB ports are closed:

- Do not waste time testing SMB exploits.
- Document the finding.
- Continue with other exposed services.
