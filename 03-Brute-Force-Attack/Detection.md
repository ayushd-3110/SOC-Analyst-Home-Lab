# Detection

## Detection Overview

This lab focuses on detecting a Windows Remote Desktop Protocol (RDP) brute-force attack using Splunk Enterprise. The attack was simulated from a Kali Linux attacker machine using Hydra against a Windows 10 victim machine.

The Windows Security Event Logs generated during the attack were collected by Splunk Universal Forwarder and analyzed in Splunk Enterprise.

---

## Detection Strategy

The SOC continuously monitors Windows Security Logs for abnormal authentication behavior.

Indicators of brute-force attacks include:

- Multiple failed logon attempts within a short time
- A successful login after several failures
- Authentication attempts targeting the same account
- Authentication attempts from unusual source systems
- High authentication frequency

---

## Windows Event IDs

| Event ID | Description |
|----------|-------------|
| 4625 | Failed Logon |
| 4624 | Successful Logon |
| 4648 | Logon using Explicit Credentials |
| 4776 | NTLM Authentication |
| 4740 | Account Lockout (if configured) |

---

## Detection Workflow

Hydra Attack
↓

Windows Security Logs Generated

↓

Universal Forwarder Collects Logs

↓

Splunk Enterprise Indexes Events

↓

SOC Analyst Investigates

↓

Incident Confirmed

---

## Detection Logic

A brute-force attack is suspected when:

- One user account receives numerous Event ID 4625 events.
- The failures occur within a short time interval.
- Event ID 4624 follows multiple Event ID 4625 events.
- Authentication attempts originate from the same source.

---

## Detection Severity

High

Reason:

Credential attacks may lead to unauthorized access and compromise of business systems.

---

## Detection Outcome

The authentication logs indicated multiple failed login attempts against the Windows workstation.

The event pattern matched a brute-force authentication attack.

The archived events show repeated authentication failures requiring investigation; successful compromise remains unverified.
## Validate a threshold-based detection

Use the [capstone authentication validation searches](../Final-Project%20%5BEnterprise%20SOC%20Incident%20Response%5D/10-Splunk/Authentication-Validation.md). The dashboard totals are useful for scoping. The detection checks an ordered sequence for the same host, target identity and source IP.
