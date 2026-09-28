
# Indicators of Compromise (IOC)

## Overview

The following indicators were identified during the controlled ransomware simulation.

These indicators are lab-specific and should not be treated as real malicious IOCs.

---

## Host

DESKTOP-NH5RCBO

---

## User

ayush

---

## Process

C:\Windows\System32\cmd.exe

---

## Simulation Directory

C:\SOC-Ransomware-Lab

---

## Simulated File Extension

.locked

---

## Simulated Ransom Note

README_RANSOM_NOTE.txt

---

## Keyword Indicators

SOC-Ransomware-Lab

SIMULATED_RANSOMWARE_ACTIVITY

RANSOMWARE

---

## IOC Classification

| Indicator | Type | Purpose |
|---|---|---|
| DESKTOP-NH5RCBO | Host | Victim endpoint |
| ayush | User | Account associated with activity |
| cmd.exe | Process | Process observed during simulation |
| C:\SOC-Ransomware-Lab | Directory | Simulation location |
| .locked | Extension | Simulated suspicious extension |
| README_RANSOM_NOTE.txt | File | Simulated ransom note |

---

## Important Note

These indicators were intentionally created as part of the lab and are not evidence of a real compromise.