# Screenshot Evidence Review

The screenshots show Windows Scheduled Task persistence activity and a Splunk **Event ID 4698** record. The visible event shows:

- Host: **DESKTOP-PB7D0G9**
- Account: **ayush**
- Event ID: **4698**
- Task name: **WindowsUpdateCheck**

The screenshot set also includes Task Scheduler trigger/action views, task verification, Event Viewer 4698, a Splunk investigation query, and a Windows Scheduled Task Detection dashboard.

## Evidence Boundary
The task name resembles a system task, but the evidence should be described as a lab-created scheduled task. Do not call it a real attacker persistence mechanism without additional evidence.
