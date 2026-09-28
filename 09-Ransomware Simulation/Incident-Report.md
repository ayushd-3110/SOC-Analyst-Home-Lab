# Incident Report

## Incident Title

Ransomware-Like Activity Detected on Windows Endpoint

## Incident Type

Ransomware Simulation

## Severity

Medium

## Status

Closed – Controlled Lab Exercise

---

## Affected Host

DESKTOP-NH5RCBO

## User

ayush

## Detection Source

Splunk

## Primary Event

Windows Security Event ID 4688 – Process Creation

---

## Summary

A controlled ransomware simulation was performed on the Windows endpoint.

Dummy files were created inside:

C:\SOC-Ransomware-Lab

The files were then rapidly modified and renamed with a simulated `.locked` extension.

A simulated ransom note was also created.

---

## Investigation

Splunk was used to review Windows Security Event ID 4688.

The investigation identified:

- CMD execution
- User account involved
- Parent process
- Process command line
- Simulation directory

---

## Impact

No production or personal files were affected.

No actual ransomware was executed.

No real file encryption occurred.

---

## Response

The activity was confirmed as an authorized security lab simulation.

No containment or remediation was required.

---

## Final Classification

False Positive / Authorized Security Testing

The investigation successfully demonstrated the process of detecting and investigating ransomware-like behavior.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
