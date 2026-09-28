LAB 11 — PHISHING INVESTIGATION
IOC EXTRACTION
==============================

1. EMAIL IOC
-------------
Sender:
security-alert@company-security.example

Recipient:
ayush@company.example

Subject:
URGENT: Account Verification Required


2. URL IOC
----------
URL:
http://192.168.234.130/verify

Protocol:
HTTP

Destination IP:
192.168.234.130

URI Path:
/verify


3. SOURCE IP
------------
Source / Attacker IP:
192.168.234.129

Role:
Kali Linux test machine used to simulate phishing URL access.


4. WEB ACTIVITY
---------------
HTTP Method:
[Enter value observed in Splunk]

HTTP Status:
[Enter value observed in Splunk]

User-Agent:
[Enter value observed in Splunk]

Timestamp:
[Enter timestamp observed in Splunk]


5. PHISHING INDICATORS
----------------------
- Urgent account-verification request
- Threat of account suspension
- Suspicious sender identity
- IP-based URL
- Suspicious /verify path
- Social-engineering language


6. COMPROMISE STATUS
--------------------
Credential submission:
No

Credential theft confirmed:
No

Malware execution confirmed:
No

Account compromise confirmed:
No

Assessment:
Controlled phishing simulation. Suspicious phishing indicators
and HTTP activity were observed, but successful compromise was
not demonstrated.


| Type       | IOC                                       | Description                 |
| ---------- | ----------------------------------------- | --------------------------- |
| Email      | `security-alert@company-security.example` | Simulated suspicious sender |
| URL        | `http://192.168.234.130/verify`           | Simulated phishing URL      |
| IP         | `192.168.234.130`                         | IIS destination             |
| IP         | `192.168.234.129`                         | Kali test/source system     |
| URI        | `/verify`                                 | Account verification path   |
| User-Agent | From Splunk                               | HTTP client information     |
| Timestamp  | From Splunk                               | Time of observed request    |
