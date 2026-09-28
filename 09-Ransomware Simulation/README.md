# LAB 9 – Ransomware Simulation & Detection

## Overview

This lab demonstrates how a SOC analyst can investigate ransomware-like behavior using Windows Security logs and Splunk.

The simulation was performed in a controlled Windows environment using only dummy files.

No real ransomware was executed and no personal or system files were encrypted.

---

## Real-World Scenario

A user reports that multiple files on a workstation have suddenly been modified and renamed.

The SOC analyst receives suspicious process telemetry and investigates whether the behavior could indicate ransomware.

The analyst must identify:

- The affected host
- The user
- The process
- The parent process
- The command line
- The timeline
- Potential indicators
- Whether the activity is malicious or authorized

---

## Lab Environment

```text
Windows Victim VM
       |
       | Windows Security Logs
       ↓
Splunk Universal Forwarder
       |
       ↓
Splunk Enterprise
       |
       ↓
SOC Detection & Investigation

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
