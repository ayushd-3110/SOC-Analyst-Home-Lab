
---

# 2. `Scenario.md`

```markdown
# Scenario — Phishing Investigation

## Background

An employee reports receiving a suspicious email that appears to originate from the organization's IT Security team.

The email claims that unusual activity has been detected on the employee's account.

The recipient is instructed to verify the account within 24 hours.

The email contains a link:

http://192.168.234.130/verify

The SOC analyst is assigned to determine whether the email contains phishing indicators and whether the suspicious URL generated any activity within the organization's monitored environment.

---

## Simulated Email

From:

security-alert@company-security.example

To:

ayush@company.example

Subject:

URGENT: Account Verification Required

Message:

Hello,

We detected unusual activity on your account.

Please verify your account within 24 hours using the link below:

http://192.168.234.130/verify

Failure to verify your account may result in temporary account suspension.

Regards,

IT Security Team

---

## SOC Analyst Role

The analyst must:

1. Examine the email.
2. Identify suspicious characteristics.
3. Investigate the URL safely.
4. Review IIS web logs.
5. Search for related activity in Splunk.
6. Extract relevant IOCs.
7. Map the activity to MITRE ATT&CK.
8. Document the investigation.
9. Determine whether compromise was demonstrated.

---

## Investigation Questions

The investigation attempts to answer:

- Who sent the email?
- What makes the email suspicious?
- What URL is contained in the email?
- Was the URL accessed?
- What source IP generated the request?
- What HTTP response was returned?
- What URL path was requested?
- Is there evidence of credential theft?
- Is there evidence of malware execution?
- Is there evidence of account compromise?

---

## Scope

This scenario is limited to the private SOC home lab.

No external phishing infrastructure or real user accounts are involved.