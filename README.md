# SOC Analyst Home Lab

## About This Repository

This repository contains my hands-on **SOC Analyst home lab** built to practice how a security analyst investigates alerts, searches logs in Splunk, validates suspicious activity, collects evidence, and writes incident reports.

The project is intentionally built as a **safe learning environment** using my own virtual machines. Attack behaviors are simulated or harmless wherever possible.

## What I Practiced

The lab portfolio covers:

1. Windows Event Log Collection
2. Port Scanning Detection
3. Brute-Force Detection
4. PowerShell Attack Detection
5. Windows Registry Persistence
6. Scheduled Task Persistence
7. LOLBins Detection
8. Credential Access / Mimikatz Detection
9. Ransomware Simulation
10. Web Attack Detection
11. Phishing Investigation
12. Account Compromise Investigation
13. Malware Investigation
14. Threat Hunting
15. Final Enterprise SOC Incident Response Project

## Main Tools

- Splunk Enterprise
- Windows 10/Windows workstation VM
- Kali Linux
- Sysmon
- Splunk Universal Forwarder
- Windows Event Logs
- Nmap
- SMB / `smbclient`
- Command Prompt and PowerShell

## Lab Environment

| Component | Role |
|---|---|
| Kali Linux | Attack / simulation machine |
| Windows VM | Victim / investigation endpoint |
| Splunk Enterprise | SIEM and log analysis |
| Sysmon | Endpoint process and activity telemetry |
| Universal Forwarder | Sends Windows logs to Splunk |

The final-project environment used the following lab addresses:

- Kali: `192.168.234.129`
- Windows victim: `192.168.234.130`
- Windows host: `DESKTOP-NH5RCBO`
- Windows user: `ayush`
- Splunk index: `main`

> IP addresses above describe the documented lab environment. They are not production systems.

## How I Documented Each Lab

Each lab focuses on a simple SOC workflow:

**Scenario → Preparation → Simulation → Detection → Investigation → IOC → MITRE ATT&CK → Incident Report → Lessons Learned**

Where screenshots are available, they are used as evidence of what was actually observed.

## Important Evidence Rule

This repository distinguishes between:

- **Observed:** directly seen in Splunk, Windows, Kali, or a screenshot.
- **Simulated:** intentionally generated for the lab.
- **Attempted:** an attack was tested, but successful exploitation was not proven.
- **Not observed:** the expected event was not available in the collected telemetry.

I do not treat a successful login, HTTP 200 response, process event, or keyword match by itself as proof of compromise.

## Safety

No real malware, credential theft, destructive ransomware, or unauthorized target was used.

The ransomware and malware labs use harmless files and commands. Credential-access activity is simulated without extracting real credentials.

## Portfolio Goal

The purpose of this repository is to demonstrate practical SOC skills such as:

- SIEM log analysis
- Windows event investigation
- Authentication analysis
- Process investigation
- PowerShell analysis
- Detection engineering
- Threat hunting
- IOC collection
- MITRE ATT&CK mapping
- Incident response documentation
- Clear analyst reporting


## Screenshot-Grounded Documentation

The lab documentation has been reviewed against the screenshots stored in each lab. Screenshot-derived facts are recorded in each lab's `Evidence-Observed.md`. Screenshot folders themselves were **not modified**.

Where a screenshot does not prove a claimed action, the documentation now says so explicitly instead of filling the gap with assumptions.
