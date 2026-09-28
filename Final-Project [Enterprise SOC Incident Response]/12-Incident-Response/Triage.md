# Triage

## Triage Goal

Quickly determine:

1. What happened?
2. Which host is involved?
3. Which account is involved?
4. When did it happen?
5. What evidence is available?
6. Is immediate containment required?

## Initial Evidence

- Failed authentication
- Successful authentication
- Process creation
- PowerShell activity
- Discovery activity

## Triage Decision

In a production environment, the authentication-to-execution sequence would justify deeper investigation.

In this lab, the analyst knows the activity was intentionally generated.

## Evidence Preservation

Record:

- timestamps
- host
- user
- source IP
- process path
- command line
- relevant event IDs
- screenshots
- Splunk queries

## Analyst Rule

Do not add an IOC or finding just because a query was expected to return something. Record what the telemetry actually shows.
