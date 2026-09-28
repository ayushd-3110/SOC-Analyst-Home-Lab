
---

# 5. `Attack-Simulation.md`

```markdown
# Attack Simulation — Phishing Investigation

## Purpose

This document describes the controlled phishing simulation used to generate investigation telemetry.

The simulation does not attempt to steal credentials or compromise a real account.

---

## Step 1 — Create Phishing Email

Create:

```text
C:\SOC-Phishing-Lab\Lab11-Phishing-Email.txt
From: IT Security <security-alert@company-security.example>
To: ayush@company.example
Subject: URGENT: Account Verification Required

Hello,

We detected unusual activity on your account.

Please verify your account within 24 hours using the link below:

http://192.168.234.130/verify

Failure to verify your account may result in temporary account suspension.

Regards,
IT Security Team

Step 2 — Identify Indicators

The email contains:

Urgency
Account verification request
Account suspension warning
Suspicious sender
IP-based URL
/verify path
Step 3 — Simulate URL Access

From Kali:

curl -I "http://192.168.234.130/verify"

Additional controlled requests:

curl -I "http://192.168.234.130/login"
curl -I "http://192.168.234.130/account"
Step 4 — Generate Detailed HTTP Evidence
curl -v "http://192.168.234.130/verify"

This can display:

Connection information
Destination
HTTP method
HTTP response
Server information
Expected Result

The IIS server receives HTTP requests from the Kali machine.

The requests should be recorded in IIS logs if IIS logging is enabled correctly.

Important Limitation

A successful HTTP request does not prove:

Credential theft
Account compromise
Malware execution
Successful exploitation

The lab demonstrates phishing-related activity and investigation telemetry.




---