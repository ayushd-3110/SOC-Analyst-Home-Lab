# Investigation – Lab 12 Account Compromise

## Investigation Goal

The goal of this investigation was to determine whether unusual authentication activity was followed by suspicious endpoint activity.

## Evidence Reviewed

The investigation focused on:

- Event ID 4625 – failed logon
- Event ID 4624 – successful logon
- Event ID 4672 – special privileges
- Event ID 4688 – process creation

## Investigation Steps

### 1. Review Failed Logons

I searched for repeated Event ID 4625 records and checked:

- account name
- source address
- logon type
- authentication package
- event time

### 2. Review Successful Logons

I then checked Event ID 4624 to see whether a successful authentication occurred after the failed attempts.

### 3. Review Process Activity

Event ID 4688 was reviewed for process creation after authentication.

### 4. Review Privileged Activity Carefully

Event ID 4672 was checked separately.

A 4672 event is not automatically evidence that the simulated user `ayush` received special privileges. The account and event context must be checked before making that conclusion.

## Key Correlation

The useful timeline pattern for this lab was:

**Failed authentication → successful authentication → endpoint activity**

This is an investigation lead. It is not, by itself, proof that the account was compromised.

## Analyst Conclusion

The activity was generated in a controlled lab using the user's own Windows and Kali systems. The exercise demonstrates how a SOC analyst can move from an authentication alert to endpoint investigation.

No real-world account compromise was established.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
