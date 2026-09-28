# Lessons Learned

## Technical Lessons

- Threat hunting is proactive rather than purely alert-driven.
- Windows Event ID 4688 is useful for process investigation.
- Command-line information provides valuable context.
- Parent-child process relationships help reconstruct execution chains.
- PowerShell activity should be investigated in context.
- Discovery commands can be legitimate or suspicious depending on context.
- Authentication and process events can be correlated to build timelines.
- Splunk can be used to search historical endpoint telemetry.

---

## SOC Investigation Lessons

A SOC analyst should avoid assuming that a single command proves compromise.

For example:

```text
powershell.exe
systeminfo
ipconfig
tasklist


an all be legitimate.

Effective threat hunting requires correlation between:

User
+
Time
+
Process
+
Parent Process
+
Command Line
+
Authentication
+
Network Activity