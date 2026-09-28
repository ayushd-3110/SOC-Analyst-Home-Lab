
Scenario
The SOC receives an alert indicating that a new Scheduled Task has been created on a Windows endpoint.

The task is named:

WindowsUpdateCheck


The SOC analyst must determine whether this is:

-Legitimate administrative activity
-A software-created task
-Malicious persistence
-A controlled security-lab simulation

Analyst Objectives
-The analyst must identify:
-Affected host
-Task name
-Task creation time
-Creating user
-Task command
-Event ID
-Whether the activity is suspicious
-Appropriate response

Initial Alert

-Alert: Scheduled Task Created
-Host: Windows Victim
-Event ID: 4698
-Severity: Medium