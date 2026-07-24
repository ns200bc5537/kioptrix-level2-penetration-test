# RPC Enumeration

## Objective

Enumerate the RPC service to identify registered programs and determine whether additional network services are exposed.

---

# 1. Service Detection

## Command

```bash
nmap -sV -p111 192.168.217.136
```

### Why?

Identify the service running on TCP port 111.

### Findings

- Port 111 open
- rpcbind version 2 detected

### Evidence

```
scans/rpc/01_rpc_version.txt
```

---

# 2. RPC Program Enumeration

## Command

```bash
rpcinfo -p 192.168.217.136
```

### Why?

List registered RPC programs and identify additional services.

### Findings

- rpcbind (portmapper)
- rpc.statd (status service)

No NFS-related services were identified.

### Evidence

```
scans/rpc/02_rpcinfo.txt
```

---

# 3. Nmap RPC Enumeration

## Command

```bash
nmap --script rpcinfo -p111 192.168.217.136
```

### Why?

Validate the RPC services discovered with rpcinfo.

### Findings

The Nmap NSE script confirmed the exposed RPC programs.

### Evidence

```
scans/rpc/03_rpc_nmap.txt
```

---

# 4. Vulnerability Research

## Command

```bash
searchsploit rpcbind
```

### Why?

Search for publicly available exploits.

### Findings

Only Denial of Service exploits were identified. No suitable remote code execution exploits were found.

---

# Summary

RPC enumeration confirmed the presence of rpcbind and rpc.statd. No NFS services or practical exploitation paths were identified, so the assessment continued with the remaining exposed services.
