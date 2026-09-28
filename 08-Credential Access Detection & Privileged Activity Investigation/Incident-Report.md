## Incident Report – Credential Access / Mimikatz Simulation

## Incident Information

| Field | Details |
|---|---|
| Incident ID | SOC-LAB8-001 |
| Incident Type | Credential Access Simulation |
| Detection Source | Splunk |
| Affected Host | DESKTOP-NH5RCBO |
| User | ayush |
| Severity | Medium |
| Status | Closed – Lab Simulation |
| Detection Method | Windows Security Event Logs |
| Primary Event | 4688 – Process Creation |
| Supporting Events | 4624, 4648, 4672 |
| MITRE ATT&CK | T1003 – OS Credential Dumping |
| Environment | Windows SOC Home Lab |

---

# 1. Executive Summary

A suspicious credential-access activity was detected on the Windows endpoint `DESKTOP-NH5RCBO`.

The activity was intentionally simulated as part of a SOC detection lab to demonstrate how an analyst could identify Mimikatz-related behavior using Windows Security logs and Splunk.

The primary detection was based on Event ID 4688, which recorded the creation of a `cmd.exe` process containing the command:

cmd /c echo mimikatz credential access simulation

The investigation also identified successful logon activity (4624), special privileges assigned to a logon session (4672), and explicit credential usage (4648).

The activity was associated with the local administrative account `ayush`.

No actual Mimikatz executable was run and no credentials were dumped.

---

# 2. Incident Description

The objective of this simulation was to reproduce telemetry that a SOC analyst might encounter during a credential-access investigation.

A harmless command was executed instead of the real Mimikatz tool:

cmd /c echo mimikatz credential access simulation

This generated Event ID 4688 and allowed the investigation to focus on:

- Process creation
- Command-line analysis
- User identification
- Privilege analysis
- Authentication correlation
- Credential-access indicators

---

# 3. Detection

The activity was detected in Splunk using Windows Security Event Logs.

Primary event:

Event ID 4688 – Process Creation

Observed command:

cmd /c echo mimikatz credential access simulation

Observed user:

ayush

Observed process:

C:\Windows\System32\cmd.exe

Observed parent process:

C:\Windows\System32\cmd.exe

---

# 4. Supporting Evidence

## Event ID 4624

A successful logon was observed for the endpoint.

The event showed:

Account: ayush

Logon Type: 2

This confirms an interactive user session.

---

## Event ID 4672

Event ID 4672 showed:

Special privileges assigned to a new logon.

The event associated with the user contained multiple privileges, including:

- SeSecurityPrivilege
- SeTakeOwnershipPrivilege
- SeLoadDriverPrivilege
- SeBackupPrivilege
- SeRestorePrivilege
- SeImpersonatePrivilege

The account was also confirmed to be a member of the local Administrators group.

---

## Event ID 4648

Event ID 4648 was observed with the message:

A logon was attempted using explicit credentials.

The account whose credentials were used was:

ayush

Target:

localhost

This event was treated as supporting evidence and not proof of credential theft.

---

# 5. Attack / Activity Timeline

| Stage | Event | Description |
|---|---|---|
| 1 | 4624 | User successfully authenticated |
| 2 | 4672 | Special privileges assigned |
| 3 | 4648 | Explicit credentials used |
| 4 | 4688 | cmd.exe process created |
| 5 | 4688 | Mimikatz-related simulation command detected |
| 6 | Splunk | SOC analyst investigated and correlated events |

---

# 6. Impact Assessment

### Actual impact

No actual credential theft occurred.

No actual Mimikatz credential dump was performed.

No credentials were intentionally exposed.

### Potential impact in a real environment

If the observed behavior represented real Mimikatz execution, an attacker could potentially attempt to obtain:

- Windows authentication material
- Password hashes
- Kerberos tickets
- Cached credentials
- Other sensitive authentication information

Because the account was an administrator, successful credential-access activity could potentially have significant impact.

---

# 7. Indicators of Compromise / Detection Indicators

The following indicators were identified during the simulation:

### Host

DESKTOP-NH5RCBO

### User

ayush

### Process

C:\Windows\System32\cmd.exe

### Suspicious Command

cmd /c echo mimikatz credential access simulation

### Detection Keywords

- mimikatz
- credential
- sekurlsa
- logonpasswords
- lsass
- privilege

These should be treated as **detection indicators**, not confirmed IOCs, because the lab used a harmless simulation.

---

# 8. MITRE ATT&CK Mapping

## T1003 – OS Credential Dumping

The simulation represents the behavior associated with credential-access techniques such as OS credential dumping.

### T1003.001 – LSASS Memory

Mimikatz is commonly associated with credential-access attempts involving LSASS memory.

However, this lab did not perform actual LSASS memory dumping.

Therefore:

Technique demonstrated:

Credential-access detection concept

Actual credential dumping:

Not performed

---

# 9. Investigation Performed

The SOC analyst:

1. Identified Event ID 4688.
2. Extracted the process name.
3. Extracted the parent process.
4. Extracted the command line.
5. Identified the associated user.
6. Investigated Event ID 4624.
7. Investigated Event ID 4672.
8. Investigated Event ID 4648.
9. Confirmed administrative privileges.
10. Correlated the events in Splunk.
11. Determined that the activity was a controlled simulation.

---

# 10. Response Actions

Because this was a controlled home-lab simulation, no real containment was required.

In a production SOC environment, recommended actions would include:

### Immediate Actions

- Validate the alert.
- Identify the affected host.
- Identify the user.
- Review process creation events.
- Investigate LSASS access.
- Check for additional credential-access activity.

### Containment

If actual credential dumping were confirmed:

- Isolate the endpoint.
- Disable or restrict the compromised account.
- Reset affected credentials.
- Revoke active sessions/tokens where appropriate.
- Block malicious tools or binaries.

### Eradication

- Remove unauthorized tools.
- Identify persistence mechanisms.
- Review endpoint security telemetry.
- Check for additional compromised systems.

### Recovery

- Restore the endpoint to a trusted state.
- Reset credentials.
- Monitor the account and endpoint.
- Continue enhanced monitoring for additional suspicious activity.

---

# 11. Root Cause

For this lab, the root cause was intentional user-generated simulation activity.

The command was deliberately created to generate Windows Security telemetry containing a Mimikatz-related keyword.

This was not an actual compromise.

---

# 12. Lessons From the Incident

The investigation demonstrated several important SOC concepts:

1. Event ID 4688 is valuable for process-level investigation.
2. Command-line logging can provide important context.
3. Event ID 4672 can help identify privileged sessions.
4. Event ID 4624 provides authentication context.
5. Event ID 4648 can identify explicit credential usage.
6. A single event should not automatically be treated as malicious.
7. Event correlation provides stronger detection confidence.
8. Administrative accounts require additional scrutiny.
9. Detection keywords should be combined with process and user context.
10. Analysts must distinguish between suspicious behavior and confirmed compromise.

---

# 13. Final Analyst Conclusion

The alert was successfully detected and investigated.

The evidence confirms that a Mimikatz-related credential-access **simulation** occurred on `DESKTOP-NH5RCBO`.

The strongest detection evidence was Event ID 4688 containing:

cmd /c echo mimikatz credential access simulation

Supporting authentication and privilege events were also identified.

However, the investigation did not find evidence of actual Mimikatz execution or credential dumping.

Final classification:

**Benign / Authorized Security Lab Simulation**

Incident status:

**Closed**

---

# 14. Evidence Collected

The following evidence was collected during the lab:

- Windows Event Viewer screenshot – Event ID 4672
- Windows Event Viewer screenshot – Event ID 4624
- Windows Event Viewer screenshot – Event ID 4648
- Windows Event Viewer screenshot – Event ID 4688
- Splunk Event ID 4688 investigation
- Splunk credential-access keyword search
- Splunk event-correlation query
- Splunk dashboard screenshots
- `whoami` output
- `whoami /groups` output

---

# 15. Final Status

**CLOSED – LAB SIMULATION**

No production system was compromised and no real credentials were dumped.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
