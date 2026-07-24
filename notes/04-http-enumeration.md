# HTTP Enumeration

## Objective

Enumerate the web application running on TCP port 80 to identify technologies, hidden resources, default content, and potential vulnerabilities.

---

# 1. Homepage Inspection

## Command

Open the target in a web browser.

```
http://192.168.217.136
```

### Why?

Identify the web application and understand its functionality.

### Observation

- Login page discovered.
- Remote System Administration Login portal.
- Username and Password fields present.

### Evidence

Screenshot

```
screenshots/web-enumeration/01-login-page.png
```

---

# 2. View Page Source

## Command

```
Ctrl + U
```

### Why?

Inspect HTML source for hidden comments, form actions, or sensitive information.

### Observation

- Login form submits data to `index.php`.
- Username parameter: `uname`
- Password parameter: `psw`
- No hidden credentials or comments found.

### Evidence

Screenshot

```
screenshots/web-enumeration/02-source-code.png
```

---

# 3. HTTP Header Enumeration

## Command

```bash
curl -I http://192.168.217.136
```

### Why?

Identify the web server, technologies, and information disclosed through HTTP response headers.

### Findings

- Apache/2.0.52 (CentOS)
- PHP/4.3.9

### Evidence

```
scans/web/01_http_headers.txt
```

---

# 4. Technology Fingerprinting

## Command

```bash
whatweb http://192.168.217.136
```

### Why?

Detect web technologies and frameworks.

### Findings

- Apache 2.0.52
- PHP 4.3.9
- Login form detected

### Evidence

```
scans/web/02_whatweb.txt
```

---

# 5. Directory Enumeration

## Command

```bash
gobuster dir \
-u http://192.168.217.136 \
-w /usr/share/wordlists/dirb/common.txt \
-x php,txt,html
```

### Why?

Discover hidden files and directories.

### Findings

Interesting results:

- `/manual/`
- `index.php`

Apache default documentation was exposed.

### Evidence

```
scans/gobuster/01_gobuster.txt
```

Screenshot

```
screenshots/web-enumeration/06-gobuster.png
```

---

# 6. Apache Manual Review

## Command

Open:

```
http://192.168.217.136/manual/
```

### Why?

Review exposed documentation for software information.

### Findings

Apache HTTP Server Version 2.0 documentation is publicly accessible.

### Evidence

Screenshot

```
screenshots/web-enumeration/03-apache-manual-home.png
```

---

# 7. Nikto Scan

## Command

```bash
nikto -h http://192.168.217.136
```

### Why?

Identify common web server misconfigurations and known issues.

### Findings

- Apache version outdated
- PHP version outdated
- HTTP TRACE enabled
- Missing security headers
- Directory indexing enabled
- Apache default files exposed

### Evidence

```
scans/nikto/01_nikto.txt
```

Screenshot

```
screenshots/web-enumeration/07-nikto.png
```

---

# 8. Vulnerability Research

## Command

```bash
searchsploit Apache 2.0.52
```

```bash
searchsploit PHP 4.3.9
```

### Why?

Identify publicly available exploits for detected software versions.

### Findings

Relevant exploit identified:

- Apache mod_ssl < 2.8.7 OpenSSL
- OpenFuckV2.c (Exploit-DB 47080)

This exploit will be evaluated during the exploitation phase.

### Evidence

```
scans/web/03_searchsploit_apache.txt

scans/web/04_searchsploit_php.txt
```

Screenshot

```
screenshots/web-enumeration/08-searchsploit-apache.png
```

---

# Summary

HTTP enumeration identified an outdated Apache/PHP web server exposing default documentation, directory indexing, HTTP TRACE support, and multiple information disclosure issues. Vulnerability research confirmed publicly available exploits that will be investigated during the exploitation phase.
