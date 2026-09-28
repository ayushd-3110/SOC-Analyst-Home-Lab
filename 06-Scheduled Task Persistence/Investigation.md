Investigation
Step 1 — Validate the Alert

The SOC analyst identified a Windows Security Event ID 4698, indicating that a Scheduled Task was created.

EventCode = 4698

The event was confirmed as present in Splunk.

Step 2 — Identify the Host

Determine which Windows endpoint generated the event.

Host = Windows Victim
Step 3 — Identify the Task

The task identified during the investigation was:

WindowsUpdateCheck
Step 4 — Identify the User

Review Event ID 4698's Message field to determine the account responsible for creating the task.

Record the actual username from your event.

User = <username from event>
Step 5 — Analyze the Command

The controlled task executed:

cmd.exe /c echo SOC-LAB-6

This command does not perform malicious activity.

Step 6 — Determine Intent

The task was intentionally created as part of the SOC lab.

Therefore:

Intent = Security Testing
Step 7 — Determine Severity

Because the activity is controlled and harmless:

Severity = Informational / Low

In a real environment, the severity could become Medium or High if the task executed a suspicious executable, script, or payload.

Investigation Conclusion

The Scheduled Task creation event was successfully detected and investigated. The task was determined to be a controlled lab simulation rather than malicious persistence.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
