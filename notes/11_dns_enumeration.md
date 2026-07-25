# DNS Enumeration

## Objective

Determine whether a DNS service is available and assess it for common misconfigurations such as zone transfers or recursive queries.

---

## Why DNS Enumeration?

DNS servers may expose:

- Internal hostnames
- Zone transfers (AXFR)
- Recursive resolution
- Domain information
- Network mapping opportunities

If DNS is not running, no further DNS testing is required.

---

## Commands Used

```bash
nmap -sV -p53 <TARGET_IP>

nmap -sU -p53 <TARGET_IP>

nmap --script dns-recursion -p53 <TARGET_IP>

dig @<TARGET_IP>

dig @<TARGET_IP> axfr

host -l localhost <TARGET_IP>

nslookup <TARGET_IP>

