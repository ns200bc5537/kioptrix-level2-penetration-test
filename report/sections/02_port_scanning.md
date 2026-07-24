# Port Scanning

## Objective

Identify open TCP ports and running network services.

---

## Commands Used

```bash
nmap -T4 -p- <TARGET_IP>
```

---

## Findings

| Port | Service | Status |
|------|----------|--------|
|22|SSH|Open|
|80|HTTP|Open|
|111|RPCBind|Open|
|443|HTTPS|Open|
|631|IPP|Open|
|873|Rsync|Open|
|3306|MySQL|Open|

---

## Risk

Multiple exposed services increase the available attack surface and require further enumeration.

---

## Evidence

- scans/nmap/01_tcp_full.nmap

---

## Screenshots

- screenshots/port-scanning/nmap_full_scan.png
