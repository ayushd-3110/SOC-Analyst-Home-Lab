Incident Report
Incident ID
SOC-LAB12-INC-001
Incident Title

Suspected Windows Account Compromise – Authentication Anomaly

Category

Account Compromise / Authentication Attack

Severity

Medium

Priority

P2

Status

Closed – Controlled Lab Simulation

Analyst

Ayush Dhumal

Executive Summary

During the investigation, multiple failed authentication attempts were observed against the monitored Windows account. A successful authentication was subsequently generated from the controlled Kali test system. Post-authentication process activity was also generated on the Windows workstation.

Splunk was used to correlate Windows Security events including 4625, 4624, 4672 where applicable, and 4688.

The activity was intentionally generated as part of a controlled SOC laboratory exercise. No real-world account compromise was established.

Affected Asset
Hostname: DESKTOP-NH5RCBO
IP: 192.168.234.130

Use your actual hostname/IP if different.

Source
Kali Linux
192.168.234.129

Use the source IP actually recorded in your Windows events.

Detected Events
4625 — Failed Logon
4624 — Successful Logon
4672 — Special Privileges, if observed
4688 — Process Creation



Investigation

The analyst first identified multiple Event ID 4625 failures.

The source address and account information were then examined.

A subsequent Event ID 4624 showed successful authentication.

Post-authentication Event ID 4688 events were reviewed to determine whether process execution occurred after authentication.

Event ID 4672 was reviewed separately to determine whether privileged activity was associated with the account.

Timeline
Time	Event	Description
Actual time	4625	Failed authentication
Actual time	4625	Failed authentication
Actual time	4625	Failed authentication
Actual time	4624	Successful authentication
Actual time	4672	Privileged activity, if applicable
Actual time	4688	Process creation

Replace Actual time with timestamps from Splunk.

Impact

The simulated activity demonstrates how repeated authentication failures followed by successful authentication and endpoint activity can indicate a potential account compromise.

No actual production system or external account was involved.

Response

For a real SOC incident, recommended actions would include:

Validate the source IP.
Confirm whether the successful login was legitimate.
Review recent account activity.
Review endpoint process activity.
Reset credentials if compromise is confirmed.
Revoke active sessions where appropriate.
Investigate additional hosts.
Preserve relevant evidence.
Escalate according to organizational procedures.

For this lab, no real containment action is required because the activity was intentionally generated.

Final Classification

Controlled Account Compromise Simulation / Suspicious Authentication Activity

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.


## Screenshot-Verified Finding

The failed-logon screenshot shows **4 failed logons** for `ayush` from `192.168.234.129` against `DESKTOP-NH5RCBO`. The supplied 4624 screenshot does not visibly confirm a successful `ayush` logon; its visible rows are `DESKTOP-NH5RCBO$ / SYSTEM`, logon type 5.
