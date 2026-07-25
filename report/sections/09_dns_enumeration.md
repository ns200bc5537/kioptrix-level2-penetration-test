
```markdown
# DNS Enumeration

## Objective

Identify the presence of a DNS service and evaluate it for common information disclosure risks.

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
