# Threat Hunting Hypothesis

## Hypothesis

> If the Windows endpoint was being used by an unauthorized actor, suspicious command execution may appear after authentication, followed by discovery or unusual built-in-tool activity.

## Why This Hypothesis?

The earlier incident phases already produced authentication and process telemetry. Threat hunting is used to look for additional evidence instead of stopping at the first alert.

## Hunt Categories

- PowerShell
- Windows Command Shell
- User discovery
- System discovery
- Network discovery
- Process discovery
- Authentication followed by execution

## Result Interpretation

A hunt can produce:

- supporting evidence
- contradicting evidence
- expected activity
- no useful evidence

“No result” is also a valid hunting result when the query and telemetry are appropriate.
