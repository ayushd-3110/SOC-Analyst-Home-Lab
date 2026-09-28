
# SOC Incident Report

## 1. Incident Information

**Incident ID:** SOC-LAB11-001  
**Incident Name:** Suspicious Phishing Email  
**Incident Type:** Phishing  
**Severity:** Medium  
**Priority:** P2  
**Status:** Closed  
**Analyst:** Ayush Dhumal  
**Environment:** SOC Home Lab  

---

## 2. What Happened?

A user reported receiving a suspicious email that appeared to come from an IT Security team.

The email asked the user to verify their account within 24 hours using a provided link.

The email contained several suspicious indicators:

- Urgent language
- Account verification request
- Threat of account suspension
- Suspicious sender address
- IP-based URL

The SOC analyst investigated the email and the URL using Kali Linux, IIS logs, and Splunk.

---

## 3. Suspicious Email Details

**From:**
```text
security-alert@company-security.example
````

**To:**

```text
ayush@company.example
```

**Subject:**

```text
URGENT: Account Verification Required
```

**Suspicious URL:**

```text
http://192.168.234.130/verify
```

---

## 4. Investigation

The SOC analyst performed the following steps:

1. Reviewed the suspicious email.
2. Checked the sender and subject.
3. Extracted the URL from the email.
4. Investigated the URL from Kali Linux.
5. Checked IIS web-server logs.
6. Searched the activity in Splunk.
7. Identified the source IP and requested URL.
8. Extracted the available indicators.
9. Checked whether credentials or malware were involved.

---

## 5. Network Information

**Source IP:**

```text
192.168.234.129
```

**Destination IP:**

```text
192.168.234.130
```

**Protocol:**

```text
HTTP
```

**Requested URI:**

```text
/verify
```

**Web Server:**

```text
Microsoft IIS
```

---

## 6. Splunk Investigation

The SOC analyst searched IIS logs in Splunk.

**Index:**

```text
main
```

**Sourcetype:**

```text
iis
```

### Search Used

```spl
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent
| sort - _time
```

The search was used to identify:

* Source IP
* Requested URL
* HTTP method
* HTTP response
* User-Agent
* Time of activity

---

## 7. Indicators Found

| Indicator      | Value                                                                                     |
| -------------- | ----------------------------------------------------------------------------------------- |
| Sender         | [security-alert@company-security.example](mailto:security-alert@company-security.example) |
| URL            | [http://192.168.234.130/verify](http://192.168.234.130/verify)                            |
| Source IP      | 192.168.234.129                                                                           |
| Destination IP | 192.168.234.130                                                                           |
| URI            | /verify                                                                                   |
| Protocol       | HTTP                                                                                      |

---

## 8. Findings

The investigation found multiple phishing indicators.

### Confirmed

* Suspicious email was identified.
* Suspicious sender was identified.
* Suspicious URL was identified.
* HTTP activity was observed.
* IIS logs recorded the web request.
* Splunk was used to investigate the activity.

### Not Confirmed

* No credentials were entered.
* No credential theft was confirmed.
* No malware execution was observed.
* No account compromise was confirmed.
* No server compromise was confirmed.

---

## 9. MITRE ATT&CK

### T1566.002 – Phishing: Spearphishing Link

The simulated email contained a suspicious link.

### T1204 – User Execution

The scenario involved interaction with a suspicious URL.

These mappings represent the techniques simulated in the lab and do not prove successful compromise.

---

## 10. SOC Response

The SOC would take the following actions in a real environment:

1. Quarantine the suspicious email.
2. Search for other users who received the email.
3. Search Splunk for the suspicious sender and URL.
4. Block the malicious URL if confirmed.
5. Check authentication logs.
6. Check endpoint logs for suspicious activity.
7. Reset the user's password if credentials were submitted.
8. Monitor the affected account and endpoint.

---

## 11. Impact

**User Account:** No confirmed compromise

**Credentials:** No credentials submitted

**Malware:** No malware observed

**Server:** No compromise confirmed

**Data Loss:** No data loss identified

**Business Impact:** None – controlled home-lab simulation

---

## 12. Root Cause

The simulated attack used social engineering.

The attacker attempted to make the user believe that an account-security problem existed and that immediate verification was required.

The main techniques used were:

* Urgency
* Fear of account suspension
* Fake security-related communication
* Suspicious verification link

---

## 13. Incident Timeline

| Time | Activity                       |
| ---- | ------------------------------ |
| T+00 | Suspicious email received      |
| T+05 | Email reported to SOC          |
| T+10 | Email investigated             |
| T+15 | Suspicious URL identified      |
| T+20 | URL investigated from Kali     |
| T+25 | IIS logs checked               |
| T+30 | Splunk investigation performed |
| T+35 | IOCs extracted                 |
| T+40 | MITRE mapping completed        |
| T+45 | Impact assessed                |
| T+50 | Incident closed                |

---

## 14. Final SOC Conclusion

The SOC investigation identified a suspicious phishing email containing an account-verification link.

The email contained multiple phishing indicators, and HTTP activity associated with the suspicious URL was observed in the IIS logs and investigated through Splunk.

No evidence of credential theft, malware execution, account compromise, or server compromise was identified.

### Final Classification

**PHISHING SIMULATION – NO CONFIRMED COMPROMISE**

### Final Status

**CLOSED**

---

## 15. Evidence Collected

The following evidence was collected:

* Phishing email screenshot
* Phishing indicator screenshot
* URL investigation screenshot
* Splunk investigation screenshot
* IOC extraction screenshot
* Final investigation screenshot
* Splunk dashboard screenshot
* IIS logs

``

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
