Dashboard Queries
Panel 1 — Total Phishing Requests
index=main sourcetype="iis"
| search cs_uri_stem="/verify" OR cs_uri_stem="/login" OR cs_uri_stem="/account"
| stats count

Visualization:

Single Value

Panel 2 — Phishing Activity Timeline
index=main sourcetype="iis"
| search cs_uri_stem="/verify" OR cs_uri_stem="/login" OR cs_uri_stem="/account"
| timechart count

Visualization:

Line Chart

Panel 3 — Top Source IPs
index=main sourcetype="iis"
| search cs_uri_stem="/verify" OR cs_uri_stem="/login" OR cs_uri_stem="/account"
| stats count by c_ip
| sort - count

Visualization:

Bar Chart

Panel 4 — Suspicious URL Paths
index=main sourcetype="iis"
| search cs_uri_stem="/verify" OR cs_uri_stem="/login" OR cs_uri_stem="/account"
| stats count by cs_uri_stem
| sort - count

Visualization:

Bar Chart

Panel 5 — HTTP Response Codes
index=main sourcetype="iis"
| search cs_uri_stem="/verify" OR cs_uri_stem="/login" OR cs_uri_stem="/account"
| stats count by sc_status
| sort - count

Visualization:

Pie Chart / Bar Chart


---

