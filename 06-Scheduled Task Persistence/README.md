Title: Scheduled Task Persistence Detection & Investigation

Overview
This lab simulates a common Windows persistence technique where an attacker creates a Scheduled Task to execute a command automatically. Windows Security Event ID 4698 is collected by Splunk and investigated to determine whether the activity is legitimate or suspicious.

The lab follows a realistic SOC workflow:
Suspicious Activity
       ↓
Windows Event 4698
       ↓
Splunk Detection
       ↓
Alert Triage
       ↓
Investigation
       ↓
MITRE ATT&CK Mapping
       ↓
IOC Collection
       ↓
Incident Classification
       ↓
Response


Tools
Windows VM

Splunk Enterprise

Splunk Universal Forwarder

Windows Event Viewer

VMware

Detection Source
Windows Security Event ID: 4698

MITRE ATT&CK
T1053.005
Scheduled Task/Job: Scheduled Task


Lab Result
A controlled Scheduled Task was created on the Windows endpoint and successfully detected in Splunk using Event ID 4698.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
