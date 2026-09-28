
---

# 8. `IOC.md`

```markdown
# IOC Extraction

## Purpose

Threat hunting can identify potential Indicators of Compromise (IOCs).

In this controlled laboratory, most indicators are simulation-related rather than confirmed malicious IOCs.

---

## Potential Indicators

| Indicator | Example |
|---|---|
| Host | DESKTOP-NH5RCBO |
| User | ayush |
| IP Address | 192.168.234.130 |
| Process | powershell.exe |
| Parent Process | cmd.exe |
| Commands | whoami, systeminfo, ipconfig, tasklist |
| HTTP Destination | 192.168.234.130 |

---

## Important Note

These indicators should not automatically be classified as malicious.

For example:

```text
powershell.exe
ipconfig
systeminfo
tasklist