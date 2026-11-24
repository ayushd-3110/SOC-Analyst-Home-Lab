# Enterprise SOC Incident Response — Capstone

I used this capstone to practice investigation of authentication and endpoint telemetry in Splunk. The private lab uses Windows host DESKTOP-NH5RCBO (192.168.234.130), test source 192.168.234.129 and index main.

## Findings

The 28 archived captures establish a user network logon, user process activity, creation and verification of a scheduled task, and harmless simulation markers. Mixed searches include background Windows and forwarding activity. A preceding matching failure sequence, lateral movement, credential extraction, encryption and complete containment remain unverified.

## Review the investigation

- [Scenario](01-Scenario/Scenario.md)
- [Preparation](02-Preparation/Preparation.md)
- [Evidence index](Screenshots/README.md)
- [Executive summary](16-Incident-Report/Executive-Summary.md)
- [Final incident report](16-Incident-Report/Final-Incident-Report.md)
- [Threat hunting findings](11-Threat-Hunting/Findings.md)
- [Response and recovery](12-Incident-Response/Recovery.md)

All screenshot files are preserved. Historical search results and proposed validation queries are distinct; no rerun is claimed.
