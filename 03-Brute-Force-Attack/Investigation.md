# Investigation

## Incident Summary

During routine security monitoring, Splunk Enterprise generated alerts indicating multiple failed authentication attempts against a Windows workstation.

The authentication failures occurred within a short period, indicating possible password guessing activity.

---

## Alert Details

Alert Name: Windows Brute Force Detection

Severity: High

Detection Time: 2.00 

---

## Investigation Timeline

| Time | Activity |
|------|----------|
| 02:00 | Hydra attack initiated |
| 02:01 | Multiple Event ID 4625 generated |
| 02:03 | Authentication investigation started |
| 02:05 | Authentication logs analyzed |
| 02:08 | IOC extraction completed |
| 02:10 | Incident report created |

---

## Evidence Collected

Windows Security Event Logs

Failed Logons (4625)

Successful Logons (4624)

Authentication Messages

Splunk Dashboard

Timeline Analysis

---

## Questions Investigated

### Which account was targeted?

Target User: ayush

---

### How many failed logins occurred?

54

---

### Was there a successful login?

Yes 

Event ID:

4624

---

### Was the account locked?

No

Event ID:

4740

---

### What attack technique was observed?

Credential Brute Force

MITRE ATT&CK

T1110

---

## Indicators of Compromise

Source IP:  192.168.234.129

Destination IP: 192.168.234.128

Target Account: ayush

Attack Tool:    Hydra

Protocol:   RDP

---

## Analysis

The authentication logs revealed repeated failed login attempts against the same user account.

The repeated failures suggest password guessing activity consistent with brute-force attacks.

If a successful login follows these failures, immediate containment actions should be initiated.

---

## Recommendations

Reset the affected password.

Enable Multi-Factor Authentication (MFA).

Review Account Lockout Policy.

Monitor future authentication attempts.

Review firewall logs.

Investigate the attacking system.

Monitor additional endpoints for similar activity.

---

## Investigation Result

Status: Confirmed Brute Force Attempt

Severity:   High