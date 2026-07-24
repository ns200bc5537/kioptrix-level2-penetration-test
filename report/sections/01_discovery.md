# Discovery

## Objective

Identify live hosts on the local network.

---

## Commands Used

```bash
arp-scan -l
```

---

## Findings

- Identified active hosts on the local subnet.
- Located the Kioptrix Level 1.1 target.
- Recorded the target IP address for further testing.

---

## Risk

Discovery reveals systems that are reachable on the network and defines the attack surface for the assessment.

---

## Evidence

- scans/discovery/01_arp_scan.txt

---

## Screenshots

- screenshots/discovery/arp_scan.png
