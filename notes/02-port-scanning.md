# Phase 2 – Port Scanning

## Objective

Identify all open TCP ports exposed by the target.

## Command

```bash
sudo nmap -T4 -p- 192.168.217.136 -oA scans/nmap/01_tcp_full
```

## Why this command?

- `-T4` speeds up scanning in a lab environment.
- `-p-` scans all TCP ports.
- `-oA` saves the output in three formats.

## Findings

Open Ports

- 22 SSH
- 80 HTTP
- 111 RPCBind
- 443 HTTPS
- 631 IPP
- 873 rsync
- 3306 MySQL

## Next Step

Perform service enumeration on all discovered ports.
