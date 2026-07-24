# HTTPS Enumeration (Port 443)

## Objective

Enumerate the HTTPS service, SSL/TLS configuration, certificate details, supported ciphers, and identify potential vulnerabilities.

---

## Step 1 - Identify HTTPS Service

### Command

```bash
nmap -sV -p443 <TARGET_IP>
```

### Why?

Identify the HTTPS service and version.

### Result

- Port 443 is open.
- Apache httpd 2.0.52 (CentOS).

### Evidence

scans/web/05_https_version.txt

Screenshot

screenshots/enumeration/https_version.png

---

## Step 2 - Check SSL Certificate

### Command

```bash
nmap --script ssl-cert -p443 <TARGET_IP>
```

### Why?

Retrieve certificate information.

### Result

- Self-signed certificate
- Expired certificate
- RSA 1024-bit key
- MD5 signature
- Common Name: localhost.localdomain

### Evidence

scans/web/06_ssl_cert.txt

Screenshot

screenshots/enumeration/ssl_certificate.png

---

## Step 3 - Enumerate SSL Ciphers

### Command

```bash
nmap --script ssl-enum-ciphers -p443 <TARGET_IP>
```

### Why?

Identify supported protocols and weak encryption.

### Result

Protocols:

- SSLv3
- TLSv1.0

Weak ciphers detected:

- RC4
- DES
- 3DES
- Export ciphers
- MD5

Least strength: F

### Evidence

scans/web/07_ssl_ciphers.txt

Screenshot

screenshots/enumeration/ssl_ciphers.png

---

## Step 4 - Inspect SSL Handshake

### Command

```bash
openssl s_client -connect <TARGET_IP>:443
```

### Why?

Perform a manual TLS handshake and inspect certificate details.

### Result

Observed:

- Expired certificate
- TLSv1
- SSLv3 compatibility
- Secure Renegotiation not supported
- RSA 1024-bit key

### Evidence

scans/web/08_openssl.txt

Screenshot

screenshots/enumeration/openssl_handshake.png

---

## Step 5 - Check HTTPS Headers

### Command

```bash
curl -k -I https://<TARGET_IP>
```

### Why?

Inspect HTTP response headers over HTTPS.

### Result

TLS negotiation failed because the server only supports obsolete protocols.

### Evidence

scans/web/09_https_headers.txt

Screenshot

screenshots/enumeration/https_headers.png

---

## Step 6 - Search for Public Exploits

### Commands

```bash
searchsploit mod_ssl
```

```bash
searchsploit openssl
```

### Why?

Look for publicly known vulnerabilities affecting the detected software.

### Result

Relevant findings:

- Apache mod_ssl OpenFuck
- Legacy OpenSSL vulnerabilities

### Evidence

scans/web/10_searchsploit_modssl.txt

scans/web/11_searchsploit_openssl.txt

Screenshot

screenshots/vulnerability-research/searchsploit_modssl.png

---

## Enumeration Summary

- HTTPS detected
- Apache 2.0.52
- Expired certificate
- Self-signed certificate
- SSLv3 enabled
- TLSv1 enabled
- Weak ciphers
- Public exploits available for related legacy versions

These findings indicate an outdated SSL/TLS configuration that should be investigated further during the vulnerability research phase.
