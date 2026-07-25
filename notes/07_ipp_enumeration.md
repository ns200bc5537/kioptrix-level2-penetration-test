# Port 631 - IPP (CUPS) Enumeration

## Objective

Identify the printing service running on port 631 and determine whether it exposes useful information or known vulnerabilities.

---

## Service Version Detection

### Command

```bash
nmap -sV -p631 <TARGET-IP>
```

### Why?

Detect the service name and version running on port 631.

### Output

```
631/tcp open  ipp  CUPS 1.1
```

### Observation

- Port 631 is open.
- IPP (Internet Printing Protocol) is running.
- Service identified as CUPS 1.1.

---

## HTTP Header Enumeration

### Command

```bash
curl -I http://<TARGET-IP>:631
```

### Why?

Retrieve HTTP response headers without downloading the page.

### Output

```
HTTP/1.1 403 Forbidden
Server: CUPS/1.1
```

### Observation

- Server responds with HTTP 403 Forbidden.
- CUPS version is disclosed in the Server header.
- Remote access is restricted.

---

## Technology Fingerprinting

### Command

```bash
whatweb http://<TARGET-IP>:631
```

### Why?

Identify web technologies running on the service.

### Output

```
CUPS 1.1
403 Forbidden
```

### Observation

- Service confirmed as CUPS 1.1.
- Web interface is not accessible remotely.

---

## Nikto Scan

### Command

```bash
nikto -h http://<TARGET-IP>:631
```

### Why?

Check for common web server misconfigurations.

### Key Findings

- Missing security headers
- HTTP PUT method allowed
- X-Content-Type-Options missing
- Content-Security-Policy missing
- Referrer-Policy missing

### Observation

The service exposes several security misconfigurations. Although the web interface is restricted, these findings could increase the attack surface if authentication or access controls are bypassed.

---

## Browser Enumeration

### URL

```
http://<TARGET-IP>:631
```

### Result

```
403 Forbidden
You don't have permission to access the resource on this server.
```

### Observation

The web interface blocks anonymous remote users.

---

## Vulnerability Research

### Command

```bash
searchsploit cups
```

### Findings

Several historical exploits were found for older CUPS versions, including:

- Buffer Overflow
- Denial of Service
- Information Disclosure
- Remote Code Execution
- Local Privilege Escalation

### Observation

The installed version is old enough to warrant further investigation. However, no exploit was executed during the enumeration phase.

---

## Conclusion

Port 631 is running CUPS 1.1.

The service leaks version information but blocks anonymous access. Multiple historical vulnerabilities exist for this version, making it a potential attack vector during later exploitation.
