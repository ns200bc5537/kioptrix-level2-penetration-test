# Kioptrix Level 1.1 - Reconnaissance & Enumeration

![Platform](https://img.shields.io/badge/Platform-VulnHub-blue)
![Category](https://img.shields.io/badge/Category-Reconnaissance-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-yellow)

## Overview

This repository documents the **Reconnaissance and Enumeration** phase of a penetration test against the **Kioptrix Level 1.1** vulnerable machine from VulnHub.

The objective was to identify exposed services, enumerate the attack surface, fingerprint technologies, and research potential vulnerabilities **without performing exploitation**.

This project follows a structured penetration testing methodology and serves as the first phase of a multi-stage assessment.

---

## Objectives

- Discover the target host
- Perform TCP port scanning
- Enumerate exposed services
- Identify service versions
- Fingerprint web technologies
- Analyze SSL/TLS configuration
- Enumerate SMB services
- Research known vulnerabilities
- Document findings

---

## Methodology

```text
Information Gathering
        │
        ▼
Host Discovery
        │
        ▼
Port Scanning
        │
        ▼
Service Enumeration
        │
        ▼
Version Detection
        │
        ▼
Web Enumeration
        │
        ▼
SSL Analysis
        │
        ▼
SMB Enumeration
        │
        ▼
Technology Fingerprinting
        │
        ▼
Vulnerability Research
```

---

# Tools Used

| Tool | Purpose |
|------|---------|
| Nmap | Host discovery, port scanning and service detection |
| Nikto | Web server enumeration |
| WhatWeb | Web technology fingerprinting |
| Curl | HTTP header inspection |
| OpenSSL | SSL/TLS analysis |
| Enum4linux | SMB enumeration |
| Searchsploit | Local exploit database |
| Firefox | Manual web enumeration |

---

# Project Structure

```
Kioptrix-Level-1.1-Recon-and-Enumeration/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── notes/
│   ├── Commands.md
│   ├── Enumeration.md
│   ├── Services.md
│   └── Vulnerability-Research.md
│
├── report/
│   ├── Penetration-Test-Report.md
│   └── Findings.md
│
├── scans/
│   ├── nmap.txt
│   ├── nikto.txt
│   ├── enum4linux.txt
│   ├── curl.txt
│   ├── openssl.txt
│   ├── whatweb.txt
│   └── searchsploit.txt
│
├── screenshots/
│
└── assets/
```

---

# Enumeration Highlights

During this phase the following information was identified:

- Open TCP services
- Service versions
- Web server technologies
- SSL/TLS configuration
- HTTP response headers
- SMB accessibility
- Potential attack vectors
- Publicly known vulnerabilities

---

# Skills Demonstrated

- Network Reconnaissance
- TCP Port Scanning
- Service Enumeration
- Web Enumeration
- SSL/TLS Analysis
- Technology Fingerprinting
- SMB Enumeration
- Vulnerability Research
- Attack Surface Analysis
- Professional Documentation

---

# Scope

### Included

- Host Discovery
- Port Scanning
- Service Enumeration
- Version Detection
- Web Enumeration
- SSL Analysis
- SMB Enumeration
- Vulnerability Research

### Not Included

- Initial Access
- Exploitation
- Privilege Escalation
- Post Exploitation
- Persistence

These phases will be documented in a separate repository.

---

# Learning Outcomes

This project provided practical experience with:

- Structured reconnaissance methodology
- Enumeration techniques
- Manual verification of services
- Security tool usage
- Attack surface mapping
- Documentation and reporting

---

# Next Phase

The continuation of this assessment will cover:

- Initial Access
- Exploit Analysis
- Exploit Execution
- Shell Access
- Privilege Escalation
- Root Access
- Post Exploitation
- Lessons Learned

---

# Disclaimer

This project was conducted in a controlled laboratory environment using the **Kioptrix Level 1.1** vulnerable virtual machine for educational purposes only.

No testing was performed against systems without authorization.

---

## Author

**beast**

Cybersecurity Student | Ethical Hacking | Penetration Testing | Red Teaming

---

⭐ If you found this repository useful, consider starring it.
