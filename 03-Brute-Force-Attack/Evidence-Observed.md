# Screenshot Evidence Review

The failed-logon screenshot shows repeated **Event ID 4625** events on **DESKTOP-PB7D0G9**. The visible event details include:

- Logon type: **2**
- Failure reason: **Unknown user name or bad password**
- Status: **0xC000006D**
- Sub-status: **0xC000006A**

The screenshot set also contains an Event ID 4624 screenshot and a dashboard for Windows Authentication Brute Force Detection.

## Evidence Boundary
The screenshots support repeated authentication-failure investigation. A successful 4624 event must still be correlated with the same account, source, and time before concluding that a brute-force attempt succeeded.
