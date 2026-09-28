## Correlation Query
index=main sourcetype="iis"
| eval attack_type=case(
    match(cs_uri_query,"(?i)(%27|'|%22).*(OR|AND).*="),"SQL Injection",
    match(cs_uri_query,"(?i)(\.\./|%2e%2e|win\.ini)"),"Path Traversal",
    match(cs_uri_stem,"(?i)(admin|login|backup|robots\.txt)"),"Web Enumeration",
    true(),"Other"
)
| where attack_type!="Other"
| stats count values(attack_type) as attack_types values(cs_uri_stem) as targeted_paths values(cs_uri_query) as queries values(sc_status) as status by c_ip
| where count >= 3


Correlation Explanation
Instead of looking at one request independently, this query groups suspicious activity by source IP.

This helps identify a pattern such as:

One IP
   ↓
Enumeration
   ↓
SQL Injection attempt
   ↓
Path Traversal attempt
In this lab, the source:

192.168.234.129
performed multiple suspicious requests against:

192.168.234.130
This makes the activity more suspicious than a single isolated request

## Investigation Query
index=main sourcetype="iis" c_ip="192.168.234.129"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent
| sort _time
Investigation Result

The investigation identified:

Source IP

192.168.234.129

Target

192.168.234.130

User-Agent

curl/8.19.0
