# Threat Hunting Findings

## Finding 1 – PowerShell

PowerShell activity was intentionally generated during the exercise and was visible through process-creation telemetry where available.

## Finding 2 – Discovery

Controlled user, system, network, and process discovery commands were executed.

## Finding 3 – Authentication to Execution

The investigation used timestamps to determine whether endpoint execution followed authentication activity.

## Analyst Assessment

The observed pattern is useful for practicing suspicious-activity investigation. Because the activity was intentionally generated in a controlled environment, the findings should not be presented as proof of a real-world intrusion.

## Follow-Up

In a production SOC, I would continue checking:

- parent/child process relationships
- user and source IP
- persistence artifacts
- endpoint file activity
- other hosts using the same account
- additional authentication events
- known IOCs
