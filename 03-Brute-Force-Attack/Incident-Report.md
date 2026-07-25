# Incident Report

## Incident Information

Incident ID:    SOC-LAB-03

Incident Name:  Windows Brute Force Attack Detection

Date:   25/07/2026

Analyst:    Ayush

Severity:   High

Status: Closed

---

# Executive Summary

A Windows brute-force authentication attack was simulated using Hydra from a Kali Linux attacker machine against a Windows 10 victim machine.

Splunk Enterprise detected multiple failed authentication attempts through Windows Security Logs.

The authentication activity was investigated and correlated to identify the attack pattern.

---

# Environment

SIEM:   Splunk Enterprise

Attacker

Kali Linux

IP: 192.168.234.129

Victim

Windows 10

IP: 192.168.234.128

---

# Attack Summary

Attack Type

Windows Brute Force

Tool Used

Hydra

Target Service

Remote Desktop Protocol (RDP)

Target Account

ayush

---

# Evidence

Windows Event ID 4625

Failed Logons

Windows Event ID 4624

Successful Logons

Splunk Authentication Dashboard

Authentication Timeline

Raw Authentication Logs

---

# Timeline

| Time | Event |
|------|-------|
| 02:00 | Hydra attack started |
| 02:01 | Failed authentication events generated |
| 02:03 | Splunk alert triggered |
| 02:05 | SOC investigation initiated |
| 02:10 | Incident confirmed |

---

# Indicators of Compromise

| IOC | Value |
|------|-------|
| Source IP | 192.168.234.129 |
| Destination IP | 192.168.234.128 |
| Username | ayush |
| Tool | Hydra |
| Protocol | RDP |

---

# MITRE ATT&CK Mapping

| Tactic | Technique |
|---------|-----------|
| Credential Access | T1110 - Brute Force |
| Initial Access | T1078 - Valid Accounts (If Successful) |

---

# Risk Assessment

Likelihood: High

Impact: High

Business Risk:  Credential compromise may allow attackers to gain unauthorized access to sensitive business resources.

---

# Recommendations

Implement Multi-Factor Authentication.

Enable Account Lockout Policy.

Review failed authentication events regularly.

Deploy authentication alerts in Splunk.

Monitor RDP activity continuously.

Restrict RDP access using firewall rules.

Use strong password policies.

---

# Lessons Learned

Authentication logs provide valuable evidence for detecting brute-force attacks.

Splunk enables rapid investigation through centralized log collection.

Correlation between failed and successful logins improves attack detection.

Continuous monitoring reduces incident response time.

---

# Conclusion

The authentication activity matched the characteristics of a Windows brute-force attack.

The SOC investigation successfully identified the attack pattern, extracted relevant indicators, mapped the activity to MITRE ATT&CK, and documented the incident for future reference.