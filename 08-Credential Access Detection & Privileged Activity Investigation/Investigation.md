Investigation Summary

A controlled credential-access simulation was investigated on DESKTOP-NH5RCBO using Splunk and Windows Security logs.

Evidence Found
4624: Successful user logon.
4672: Special privileges assigned, including SeDebugPrivilege.
4648: Explicit credential usage observed.
4688: cmd.exe created with the command:
cmd /c echo mimikatz credential access simulation
Investigation

The SOC analyst correlated the authentication, privilege, and process-creation events and identified the activity as suspicious credential-access behavior.

The ayush account was confirmed as a member of the local Administrators group.

Finding

The Mimikatz activity was simulated using a harmless echo command. No actual Mimikatz execution or credential dumping was confirmed.

Conclusion

Classification: Controlled Credential Access Simulation
Severity: Medium
Status: Closed — Lab Exercise

The investigation demonstrated how Splunk can correlate 4624 + 4648 + 4672 + 4688 to investigate potential credential-access activity.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
