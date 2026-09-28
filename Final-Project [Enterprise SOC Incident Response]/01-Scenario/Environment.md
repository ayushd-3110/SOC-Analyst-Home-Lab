# Environment

| System | Address / Value | Role |
|---|---|---|
| Kali Linux | `192.168.234.129` | Simulation / attack system |
| Windows | `192.168.234.130` | Victim / monitored endpoint |
| Windows hostname | `DESKTOP-NH5RCBO` | Endpoint under investigation |
| Windows user | `ayush` | Lab account |
| Splunk | Enterprise | SIEM |
| Index | `main` | Windows event storage |
| Sysmon | Windows endpoint | Endpoint telemetry |

## Main Windows Events

- 4624 – Successful Logon
- 4625 – Failed Logon
- 4672 – Special Privileges Assigned
- 4688 – Process Creation
- 4698 – Scheduled Task Created

## Important Note

Not every event is proof of malicious activity. The analyst must look at the event fields, timing, account, source, process, and surrounding activity.
