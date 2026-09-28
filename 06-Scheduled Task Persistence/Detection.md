Detection Objective
Detect creation of new Windows Scheduled Tasks using Security Event ID 4698.

Primary Detection
index=main EventCode=4698
Investigation View
index=main EventCode=4698
| table _time host user EventCode Message
| sort - _time
Detection Logic
IF
Windows Security EventCode = 4698

THEN
Generate Scheduled Task Creation Alert
SOC Classification
Event 4698 does not automatically mean malicious activity.

The analyst must investigate:

Task name

User

Command

Host

Time

Business context