
---

# 6. `Detection.md`

```markdown
# Detection — Phishing Investigation

## Detection Objective

Detect suspicious web requests associated with the simulated phishing URL.

The detection focuses on authentication-related paths commonly associated with account verification.

---

## Basic Detection

```spl
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent


Expanded Detection
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent
| sort - _time


Source IP Detection
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
| stats count by c_ip
| sort - count
Suspicious URL Detection
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| stats count by cs_uri_stem
| sort - count
Response Code Analysis
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
| stats count by sc_status
| sort - count