# HTTP Enumeration

## Objective

Enumerate the web server, identify technologies, directories, and publicly known vulnerabilities.

---

## Commands Used

```bash
curl -I http://<TARGET_IP>

whatweb http://<TARGET_IP>

gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirb/common.txt -x php,txt,html

nikto -h http://<TARGET_IP>

searchsploit apache

searchsploit php
```

---

## Findings

- Apache 2.0.52
- PHP 4.3.9
- /manual directory discovered
- Directory indexing enabled
- Missing security headers
- HTTP TRACE enabled
- Multiple outdated software versions detected
- Public exploits available

---

## Risk

The web server runs legacy software with multiple security weaknesses that may lead to further exploitation.

---

## Evidence

- scans/web/01_http_headers.txt
- scans/web/02_whatweb.txt
- scans/gobuster/01_gobuster.txt
- scans/nikto/01_nikto.txt
- scans/web/03_searchsploit_apache.txt
- scans/web/04_searchsploit_php.txt

---

## Screenshots

- screenshots/web-enumeration/homepage.png
- screenshots/web-enumeration/manual_page.png
- screenshots/vulnerability-research/nikto.png
