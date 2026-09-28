# Attack Simulation

## Objective

The purpose of this simulation was to generate Windows security telemetry
associated with suspicious credential-access activity.

No real credential dumping was performed.

---

## Step 1 — Verify Current User

The following command was executed:

    whoami

Observed result:

    desktop-nh5rcbo\ayush

This confirmed the account under which the activity was being performed.

---

## Step 2 — Check Group Membership

The following command was executed:

    whoami /groups

The account was identified as a member of:

    BUILTIN\Administrators

The output also showed:

    High Mandatory Level

This confirmed that the test account was operating with administrative
privileges.

---

## Step 3 — Credential Access Simulation

A harmless command was used to simulate Mimikatz-related activity:

    cmd /c echo mimikatz credential access simulation

The command does not perform credential dumping.

Its purpose was to create a process creation event containing a recognizable
credential-access keyword.

---

## Step 4 — Explicit Credential Simulation

An attempt was made using:

    runas /user:.\ayush cmd

The test produced:

    RUNAS ERROR: Unable to acquire user password

The attempt was repeated several times.

This generated useful authentication telemetry and contributed to the
investigation of Event ID 4648.

---

## Step 5 — Windows Security Events

The Windows Security log was reviewed for:

- 4624
- 4648
- 4672
- 4688

---

## Step 6 — Event 4672

Event 4672 showed:

    Special privileges assigned to a new logon.

The event contained privileged tokens such as:

    SeDebugPrivilege
    SeBackupPrivilege
    SeRestorePrivilege
    SeTakeOwnershipPrivilege
    SeImpersonatePrivilege

This was treated as supporting evidence of privileged activity.

---

## Step 7 — Event 4688

Event 4688 confirmed process creation.

The investigation identified:

    New Process Name:
    C:\Windows\System32\cmd.exe

and:

    Process Command Line:
    cmd /c echo mimikatz credential access simulation

---

## Step 8 — Forward Events to Splunk

The Windows Security events were forwarded to Splunk through the
Splunk Universal Forwarder.

Splunk source:

    WinEventLog:Security

Index:

    main

---

## Expected Investigation Timeline

The activity can be viewed as:

    Authentication
          |
          v
    Privileged Logon
          |
          v
    Explicit Credential Activity
          |
          v
    Process Creation
          |
          v
    Credential-Access Indicator
          |
          v
    SOC Investigation