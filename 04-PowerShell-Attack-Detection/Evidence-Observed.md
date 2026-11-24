# Screenshot Evidence Review

The screenshot set contains PowerShell activity, including PowerShell commands, an execution-bypass test, encoded/base-string activity, information gathering, and Windows Security Event ID **4688**.

The visible 4688 screenshot identifies host **DESKTOP-PB7D0G9**.

The screenshots also show a Splunk dashboard named **Windows PowerShell Threat Monitoring Dashboard** and multiple SPL searches used for investigation.

## Evidence Boundary
The screenshots document simulated PowerShell behaviors and detection work. They should not be described as proof that a real malicious payload executed.

## Additional review findings

The panels use different scopes that have not been reconciled. ScriptBlockText is blank and the user is NOT_TRANSLATED. Event Code 1.png is a SecurityCenter Application event, not Sysmon process creation.

**Disposition:** Suspicious-looking test activity observed; no malicious payload established.
