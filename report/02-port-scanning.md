# Phase 2 – Port Scanning

## Objective

Identify exposed TCP services.

## Method

A full TCP scan was performed using Nmap.

## Command

```bash
sudo nmap -T4 -p- 192.168.217.136 -oA scans/nmap/01_tcp_full
```

## Results

Seven TCP ports were identified.

| Port | Service |
|------|---------|
|22|SSH|
|80|HTTP|
|111|RPCBind|
|443|HTTPS|
|631|IPP|
|873|rsync|
|3306|MySQL|

## Evidence

Figure 2 – Full TCP Port Scan

## Conclusion

The discovered services will be enumerated individually in the next phase.
