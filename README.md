# SOC Analyst Home Lab

A hands-on cybersecurity portfolio demonstrating practical Security
Operations Center (SOC) skills through 14 security investigation labs
and an enterprise incident response capstone.

## Project Overview

I developed this home lab to strengthen my practical skills in security
monitoring, log analysis, alert triage, threat hunting, incident
investigation, and incident response.

The project uses a controlled virtual environment to investigate
security-related events through Splunk and Windows endpoint telemetry.

Each investigation includes supporting evidence, analytical findings,
detection searches, and documentation of observed limitations.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Splunk Enterprise | SIEM, log analysis and dashboards |
| Splunk Universal Forwarder | Log collection |
| Windows Event Viewer | Windows security event analysis |
| Sysmon | Endpoint telemetry |
| Windows | Monitored endpoint |
| Kali Linux | Controlled lab environment |
| VMware Workstation | Virtualization |
| Microsoft IIS | Web server log investigation |
| SPL | Security event searching and analysis |
| MITRE ATT&CK | Threat behavior mapping |

## Lab Portfolio

| No. | Lab | Skills Demonstrated |
|---|---|---|
| 01 | Windows Event Logs | Authentication monitoring |
| 02 | Port Scanning Detection | Network traffic investigation |
| 03 | Brute-Force Detection | Authentication anomaly analysis |
| 04 | PowerShell Activity Detection | Process and script analysis |
| 05 | Registry Persistence | Registry event investigation |
| 06 | Scheduled Task Persistence | Scheduled task monitoring |
| 07 | LOLBins Detection | Legitimate binary usage analysis |
| 08 | Credential Access Investigation | Privileged activity analysis |
| 09 | Ransomware Simulation | File activity investigation |
| 10 | Web Attack Detection | IIS log analysis |
| 11 | Phishing Investigation | Suspicious email and URL triage |
| 12 | Account Compromise Investigation | Authentication investigation |
| 13 | Malware Investigation | Process and file artifact analysis |
| 14 | Threat Hunting | Proactive security investigation |
| 15 | Enterprise SOC Incident Response | End-to-end incident investigation |

## SOC Investigation Workflow

1. Identify suspicious security events.
2. Review and validate available telemetry.
3. Investigate affected hosts and accounts.
4. Analyze process and authentication activity.
5. Collect and document relevant evidence.
6. Assess potential false positives.
7. Map relevant behavior to MITRE ATT&CK.
8. Determine an evidence-based analyst verdict.
9. Document response recommendations.
10. Prepare an incident report.

## Enterprise SOC Incident Response Capstone

The final project integrates skills developed throughout the individual
labs into a structured incident investigation.

Key investigation areas include:

- Authentication anomalies
- Endpoint process activity
- PowerShell monitoring
- Discovery-related activity
- Persistence investigation
- Credential-access indicators
- Network authentication
- Threat hunting
- Incident response and recovery assessment
- Executive reporting

The investigation distinguishes confirmed observations from simulated
behavior and unverified hypotheses.

## Evidence and Documentation

The repository contains:

- 14 individual SOC investigation labs
- 1 enterprise incident response capstone
- 148 original screenshots
- 14 individual lab dashboards
- 2 PDF dashboard exports
- Evidence-based incident reports
- SPL investigation searches
- MITRE ATT&CK mappings
- Lessons learned and investigation limitations

## Skills Demonstrated

### Security Monitoring

- SIEM monitoring and log analysis
- Windows Security event investigation
- Authentication anomaly identification
- Endpoint activity monitoring

### Detection Engineering

- Splunk SPL searches
- Dashboard development
- Security event classification
- False-positive assessment

### Threat Investigation

- Evidence collection
- IOC analysis
- Process investigation
- Authentication and timeline analysis
- Threat hunting

### Incident Response

- Alert triage
- Incident severity assessment
- Containment and recovery considerations
- Technical incident documentation
- Executive reporting

## Evidence Integrity

All original screenshots and dashboard exports have been preserved.

The documentation distinguishes observed events, controlled simulations,
and unverified findings. Archived dashboard results are historical
evidence, and proposed detection improvements require live validation.

## Disclaimer

This project was developed for educational purposes within an authorized,
controlled home-lab environment.

No real-world compromise, credential theft, or destructive malware
execution is claimed.

## Author

**Ayush Dhumal**

Aspiring SOC Analyst | Cybersecurity Enthusiast

GitHub: https://github.com/ayushd-3110
