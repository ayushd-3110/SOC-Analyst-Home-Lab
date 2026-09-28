# Scenario — LOLBins Detection

## Background

The SOC monitoring system generates an alert for suspicious process
execution on a Windows endpoint.

The alert involves a legitimate Windows utility, certutil.exe.

Attackers may abuse legitimate Windows utilities, commonly referred
to as Living-off-the-Land Binaries (LOLBins), to perform suspicious
activities while blending into normal system activity.

The SOC analyst must determine whether the execution is legitimate,
suspicious, or potentially malicious.

---

## Lab Environment

The investigation is performed using:

- Windows Victim Machine
- Splunk Enterprise
- Splunk Universal Forwarder
- Windows Security Event Logs
- Event ID 4688

---

## Simulated Activity

The controlled lab executes:

certutil -dump C:\Windows\System32\notepad.exe

This generates a Windows Security Event ID 4688 containing:

- User
- Host
- New Process Name
- Parent Process
- Process Command Line

---

## SOC Analyst Task

The analyst must:

1. Detect the certutil.exe execution.
2. Identify the affected host.
3. Identify the user who executed the process.
4. Identify the parent process.
5. Analyze the command line.
6. Determine whether the activity is expected.
7. Search for related suspicious activity.
8. Extract relevant investigation artifacts.
9. Map the behavior to MITRE ATT&CK.
10. Document the investigation in an incident report.

---

## Investigation Finding

The observed activity was intentionally generated as part of a
controlled security lab.

The activity was therefore classified as:

Benign / Controlled Lab Activity

No containment or remediation was required.

---

## Real-World SOC Relevance

In a production SOC, the same detection could indicate:

- Abuse of a legitimate Windows utility
- Execution of suspicious commands
- Possible defense evasion
- Possible malware activity
- Possible attacker activity

The analyst should investigate the complete process chain,
command line, user, host, and surrounding telemetry before
determining the severity of the alert.