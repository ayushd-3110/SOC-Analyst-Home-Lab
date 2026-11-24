# Investigation — Registry Persistence Investigation

## Question

What does the archived telemetry establish about activity on DESKTOP-PB7D0G9, and what remains uncertain?

## Observations

I verified the controlled Run-key entry Lab5Persistence and reviewed the archived dashboard, which displays six registry-related records.

## Analysis

The dashboard's object name, value name and user columns are blank; broad object-access and process creation records do not independently prove changes to the particular value. Execution at the next logon has not been demonstrated.

## Conclusion and follow-up

Controlled registry artifact observed; attacker persistence not established. Document the actual registry value and distinguish creation, execution and cleanup evidence.

[Evidence observations](Evidence-Observed.md) · [Incident report](Incident-Report.md)
