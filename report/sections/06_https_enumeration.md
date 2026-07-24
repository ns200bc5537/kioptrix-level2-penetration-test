# HTTPS Enumeration

## Objective

Enumerate the HTTPS service and identify SSL/TLS security weaknesses.

---

## Commands Used

```bash
nmap -sV -p443 <TARGET_IP>

nmap --script ssl-cert -p443 <TARGET_IP>

nmap --script ssl-enum-ciphers -p443 <TARGET_IP>

openssl s_client -connect <TARGET_IP>:443

curl -k -I https://<TARGET_IP>

searchsploit mod_ssl

searchsploit openssl
```

---

## Findings

- Apache HTTP Server 2.0.52 detected.
- Self-signed certificate.
- Expired SSL certificate.
- RSA 1024-bit key.
- MD5 certificate signature.
- SSLv3 and TLSv1 supported.
- Multiple weak cipher suites enabled.
- Public exploits available for legacy Apache mod_ssl/OpenSSL versions.

---

## Risk

The HTTPS service is running an outdated SSL/TLS configuration with weak cryptographic settings. These findings increase the attack surface and may allow exploitation of known vulnerabilities.

---

## Evidence

- scans/web/05_https_version.txt
- scans/web/06_ssl_cert.txt
- scans/web/07_ssl_ciphers.txt
- scans/web/08_openssl.txt
- scans/web/09_https_headers.txt
- scans/web/10_searchsploit_modssl.txt
- scans/web/11_searchsploit_openssl.txt

---

## Screenshots

- screenshots/enumeration/https_version.png
- screenshots/enumeration/ssl_certificate.png
- screenshots/enumeration/ssl_ciphers.png
- screenshots/enumeration/openssl_handshake.png
- screenshots/vulnerability-research/searchsploit_modssl.png
