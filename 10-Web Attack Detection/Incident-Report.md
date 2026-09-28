# Incident Report

## Incident Name

Lab 10 — Web Attack Detection

## Incident Type

Web Application Attack

## Severity

Medium

## Status

Closed — Controlled Lab Simulation

## Attacker

192.168.234.129

## Target

192.168.234.130

## Web Server

Microsoft IIS 10.0

## SIEM

Splunk Enterprise

---

## Executive Summary

A controlled web security exercise was performed against a Windows IIS
server.

The simulated attacker generated multiple suspicious HTTP requests from
Kali Linux.

The activity included SQL injection-style input, path traversal and
web endpoint enumeration.

The IIS logs were successfully collected in Splunk and analyzed using
custom detection and investigation queries.

---

## Timeline

The activity occurred on:

31 August 2026

The IIS logs recorded requests from the Kali system during the lab exercise.

---

## Evidence

The investigation identified:

Source IP:
192.168.234.129

Target IP:
192.168.234.130

User-Agent:
curl/8.19.0

Suspicious paths:

/Lab10/admin
/Lab10/login
/Lab10/backup
/Lab10/robots.txt

Suspicious parameters:

id=1%27%20OR%20%271%27=%271

file=../../../../Windows/win.ini

---

## Detection

Splunk was used to identify suspicious request patterns and correlate
multiple requests from the same source.

---

## Impact

No real production system was involved.

This was a controlled cybersecurity lab.

The available evidence demonstrates suspicious attack attempts but does not
establish successful compromise of the Windows host or database.

---

## Response

The activity was investigated using IIS logs and Splunk.

The source IP, requested paths, parameters, HTTP status codes and User-Agent
were identified.

Recommended remediation includes input validation, secure coding practices,
request filtering and continued SIEM monitoring.

---

## Final Assessment

The lab successfully demonstrated a SOC workflow for detecting and
investigating suspicious web activity:

Detection
→ Investigation
→ Correlation
→ IOC Extraction
→ Incident Response
→ Reporting

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
