Incident Report
Incident Title
Suspicious Scheduled Task Creation

Incident ID
SOC-LAB-006
Detection Source
Splunk
Event
Windows Security Event ID 4698
Affected Asset
Windows Victim VM
Severity
Low / Informational
Description
A Scheduled Task named WindowsUpdateCheck was detected on the Windows endpoint. The task was created intentionally as part of a controlled SOC security lab.

Investigation Findings
The analyst identified:

Scheduled Task creation event

Task name

Creating user

Task command

Affected endpoint

Event timestamp

The configured command was:

cmd.exe /c echo SOC-LAB-6
No malicious payload or external network communication was involved.

MITRE ATT&CK
T1053.005
Scheduled Task/Job: Scheduled Task
Verdict
Benign / Security Testing
Recommended SOC Response
In a real incident:

Validate the task.

Identify the creator.

Determine whether the task is authorized.

Examine the configured executable/script.

Check for related suspicious activity.

Disable/remove malicious tasks.

Isolate the endpoint if compromise is suspected.

Escalate to L2/Incident Response when appropriate.

Final Disposition
Closed — Benign Lab Simulation

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
