


# Scenario

## Scenario Title

Ransomware-Like Activity on a Windows Endpoint

## Background

The SOC receives an alert indicating unusual process activity on a Windows workstation.

The analyst is asked to determine whether the activity could be associated with ransomware.

---

## Analyst Situation

The workstation:

DESKTOP-NH5RCBO

shows CMD process activity involving a dedicated ransomware simulation directory.

The analyst must investigate:

- Who performed the activity?
- Which process was executed?
- What was the command line?
- What directory was accessed?
- Was the activity authorized?
- Is there evidence of ransomware behavior?

---

## Investigation Approach

The analyst uses Splunk to search Windows Security Event ID 4688.

The analyst then reviews:

1. User
2. Process
3. Parent process
4. Command line
5. Timeline
6. Related authentication events

---

## Final Outcome

The investigation determines that the activity was part of an authorized SOC training exercise.

No actual ransomware infection occurred.

---

## SOC Learning Objective

The scenario demonstrates how a SOC analyst should investigate suspicious process activity while considering both technical evidence and operational context.