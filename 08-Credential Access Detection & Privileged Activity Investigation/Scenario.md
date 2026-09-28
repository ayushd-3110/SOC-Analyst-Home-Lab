# Lab 8 — Credential Access / Mimikatz Detection

## Scenario
A user workstation has been compromised, and the SOC team receives an alert indicating suspicious activity involving credential-access behavior.

The analyst notices that the activity occurred under an administrative account. Windows Security logs show a successful logon, a privileged logon, and suspicious process creation.

The analyst needs to determine:

Who performed the activity?

Which workstation was involved?

Was the account privileged?

What process was executed?

What command line was used?

Is the activity consistent with Mimikatz or another credential-access technique?

Is there evidence of credential theft?

Does the activity require incident response?

For this lab, actual credential dumping is not performed. Instead, we use a controlled simulation to generate realistic Windows process telemetry and investigate it in Splunk.

## SOC analyst mindset
The investigation is:

Alert
  ↓
Identify user
  ↓
Identify host
  ↓
Check authentication
  ↓
Check privileged activity
  ↓
Examine process creation
  ↓
Look for Mimikatz/credential-access indicators
  ↓
Determine severity
  ↓
Respond