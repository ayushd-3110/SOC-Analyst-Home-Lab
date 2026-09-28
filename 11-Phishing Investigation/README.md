# Lab 11 — Phishing Investigation

## Overview

This lab demonstrates a Security Operations Center (SOC) investigation of a simulated phishing email.

The objective is to investigate a suspicious email from initial identification through URL analysis, web activity investigation, IOC extraction, MITRE ATT&CK mapping, and incident reporting.

The phishing scenario is completely controlled and performed inside a private SOC home lab. No real phishing campaign, credential harvesting, or external victim targeting is performed.

The simulated email contains an urgent account-verification request and directs the user to a controlled IIS web server.

---

## Lab Scenario

A user receives an email claiming to be from the IT Security team.

The email states that unusual account activity has been detected and asks the user to verify their account within 24 hours.

The message contains a suspicious URL:

http://192.168.234.130/verify

The SOC analyst investigates the email, identifies phishing indicators, investigates the URL from Kali Linux, and searches IIS logs in Splunk for related web activity.

---

## Objectives

- Analyze a suspicious phishing email.
- Identify phishing and social-engineering indicators.
- Investigate a suspicious URL safely.
- Generate controlled HTTP activity from Kali Linux.
- Analyze IIS web logs.
- Detect suspicious URL activity in Splunk.
- Extract relevant IOCs.
- Map the scenario to MITRE ATT&CK.
- Produce a SOC-style incident report.
- Document investigation findings and lessons learned.

---

## Lab Environment

| Component | Configuration |
|---|---|
| Kali Linux | Attacker/Test Machine |
| Kali IP | 192.168.234.129 |
| Windows IIS | Victim/Web Server |
| IIS IP | 192.168.234.130 |
| Web Server | Microsoft IIS 10.0 |
| SIEM | Splunk Enterprise |
| Splunk Index | main |
| Sourcetype | iis |
| Network | VMware private lab network |

---

## Investigation Workflow

Phishing Email
        ↓
Indicator Analysis
        ↓
URL Investigation
        ↓
HTTP Activity
        ↓
IIS Logs
        ↓
Splunk Detection
        ↓
IOC Extraction
        ↓
MITRE ATT&CK Mapping
        ↓
Incident Report

---

## Key Findings

The simulated email contained several suspicious characteristics:

- Suspicious sender identity
- Urgent account-verification request
- Threat of account suspension
- IP-based URL
- `/verify` URL path
- Social-engineering language

Controlled HTTP activity was generated from the Kali test machine toward the IIS server.

The resulting web activity was investigated through Splunk.

No credentials were submitted during the lab.

No successful credential theft or account compromise was demonstrated.

---

## Detection

The main Splunk detection searches IIS events for suspicious authentication-related URL paths.

Example:

```spl
index=main sourcetype="iis"
| search cs_uri_stem="/verify" OR cs_uri_stem="/login" OR cs_uri_stem="/account"
| stats count by c_ip cs_uri_stem sc_status
| sort - count

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
