# Phase 3.1 - SSH Enumeration

## Objective

Identify the SSH service, determine its version, and collect information useful for vulnerability research.

**Target:** 192.168.217.136  
**Port:** 22/TCP

---

# 1. Service Version Detection

## Command

```bash
nmap -sV -p22 192.168.217.136
```

### Why?

Detect the SSH software and version running on the target.

### Output

```text
22/tcp open ssh OpenSSH 3.9p1 (protocol 1.99)
```

### Analysis

- Port **22** is open.
- The target is running **OpenSSH 3.9p1**.
- Protocol **1.99** indicates SSHv2 compatibility.
- The detected version will be researched later for known vulnerabilities.

**Evidence**

- `scans/ssh/01_ssh_version.txt`
- `screenshots/enumeration/01-ssh-version.png`

---

# 2. SSH Banner

## Command

```bash
ssh -v 192.168.217.136
```

### Why?

Collect the SSH banner and observe the server's response.

### Key Output

```text
Remote software version OpenSSH_3.9p1

Unable to negotiate...

Their offer:
diffie-hellman-group-exchange-sha1
```

### Analysis

- The banner confirms **OpenSSH 3.9p1**.
- The server supports legacy key exchange algorithms.
- Modern SSH clients reject these algorithms by default.

**Evidence**

- `scans/ssh/02_ssh_banner.txt`
- `screenshots/enumeration/02-ssh-banner.png`

---

# 3. Supported Algorithms

## Command

```bash
nmap --script ssh2-enum-algos -p22 192.168.217.136
```

### Why?

Identify supported cryptographic algorithms.

### Key Output

```text
KEX:
diffie-hellman-group1-sha1

Host Keys:
ssh-rsa
ssh-dss
```

### Analysis

- Legacy SHA-1 based algorithms are enabled.
- `ssh-dss` is deprecated on modern systems.
- Older cryptography may increase security risk.

**Evidence**

- `scans/ssh/03_ssh_algorithms.txt`
- `screenshots/enumeration/03-ssh-algorithms.png`

---

# 4. Host Keys

## Command

```bash
nmap --script ssh-hostkey -p22 192.168.217.136
```

### Why?

Retrieve SSH host key fingerprints.

### Key Output

```text
RSA1
RSA
DSA
```

### Analysis

- SSH host keys were successfully identified.
- These fingerprints help verify server identity.

**Evidence**

- `scans/ssh/04_ssh_hostkey.txt`
- `screenshots/enumeration/04-ssh-hostkey.png`

---

# 5. Exploit Research

## Command

```bash
searchsploit openssh
```

### Why?

Search for publicly known exploits related to OpenSSH.

### Result

Multiple exploits were found, including:

- Username Enumeration
- Buffer Overflow
- Denial of Service
- Command Execution

### Analysis

Finding an exploit in Searchsploit **does not** confirm the target is vulnerable. The exploit must match the detected version and be validated during the **Vulnerability Research** phase.

**Evidence**

- `scans/ssh/05_searchsploit.txt`
- `screenshots/enumeration/05-searchsploit-ssh.png`

---

# SSH Enumeration Summary

| Item | Result |
|------|--------|
| Port | 22/TCP |
| Service | SSH |
| Version | OpenSSH 3.9p1 |
| Protocol | 1.99 |
| Host Keys | RSA, RSA1, DSA |
| Key Exchange | Legacy SHA-1 algorithms |
| Next Phase | Vulnerability Research |

## Conclusion

SSH enumeration successfully identified the service version, supported algorithms, and host keys. These findings provide the information required to perform targeted vulnerability research before considering any exploitation.
