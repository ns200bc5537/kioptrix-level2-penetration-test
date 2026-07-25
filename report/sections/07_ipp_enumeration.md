# IPP Enumeration

## Objective

Enumerate the IPP service and identify potential security weaknesses.

---

## Commands Used

```bash
nmap -sV -p631 <TARGET_IP>

curl -I http://<TARGET_IP>:631

whatweb http://<TARGET_IP>:631

nikto -h http://<TARGET_IP>:631

searchsploit cups
```

---

## Findings

- CUPS 1.1 detected.
- HTTP 403 Forbidden response.
- Version information disclosed.
- Multiple HTTP security headers missing.
- HTTP PUT method enabled.
- Public exploits available for legacy CUPS versions.

---

## Risk

The target is running an outdated CUPS service that discloses version information and lacks several recommended HTTP security headers. Historical vulnerabilities exist for this version and should be investigated during the exploitation phase.

---

## Evidence

- scans/ipp/01_ipp_version.txt
- scans/ipp/02_headers.txt
- scans/ipp/03_whatweb.txt
- scans/ipp/04_nikto.txt
- scans/ipp/05_searchsploit.txt

---

## Screenshots

- screenshots/enumeration/ipp_version.png
- screenshots/enumeration/ipp_headers.png
- screenshots/enumeration/ipp_whatweb.png
- screenshots/enumeration/ipp_browser.png
- screenshots/enumeration/ipp_nikto.png
