Step 1 — Open PowerShell as Administrator
Open PowerShell on the Windows Victim VM.

Purpose: Scheduled Tasks can be created through Windows command-line utilities.

Step 2 — Create the Scheduled Task
Run:

schtasks /create /tn "WindowsUpdateCheck" /tr "cmd.exe /c echo SOC-LAB-6" /sc minute /mo 5
Explanation
Parameter	Meaning
/create	Creates a new task
/tn	Specifies task name
/tr	Specifies command to execute
/sc	Defines schedule
/mo 5	Every 5 minutes
The command is intentionally harmless and only executes:

echo SOC-LAB-6
Step 3 — Verify the Task
schtasks /query /tn "WindowsUpdateCheck" /v /fo list
Purpose: Confirm that the task exists and inspect its configuration.

Step 4 — Verify Event 4698
Open:

Event Viewer
→ Windows Logs
→ Security
Search for:

4698
Purpose: Confirm that Windows generated the Scheduled Task creation event.

Step 5 — Verify in Splunk
Run:

index=main EventCode=4698
Purpose: Confirm that the Universal Forwarder successfully sent the event to Splunk.

Step 6 — Cleanup
After investigation:

schtasks /delete /tn "WindowsUpdateCheck" /f
Purpose: Remove the simulated persistence mechanism.
