Query 1 — Detect Scheduled Tasks

index=main EventCode=4698

Query 2 — Display Investigation Fields

index=main EventCode=4698
| table _time host user EventCode Message
| sort - _time

Query 3 — Count Scheduled Tasks

index=main EventCode=4698
| stats count as "Scheduled Tasks Created"

Dashboard: Single Value

Query 4 — Scheduled Task Timeline

index=main EventCode=4698
| timechart count span=1h

Dashboard: Line Chart

Query 5 — Tasks by Host

index=main EventCode=4698
| stats count by host
| sort - count

Dashboard: Bar Chart


Query 9 — Recent Scheduled Task Creation

index=main EventCode=4698 earliest=-24h
| stats count by host user
| sort - count