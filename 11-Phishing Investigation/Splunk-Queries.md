Search for /verify
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent
| sort - _time

Search Suspicious Authentication Paths
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent
| sort - _time

Search by Kali Source IP
index=main sourcetype="iis"
| search c_ip="192.168.234.129"
| table _time c_ip cs_method cs_uri_stem cs_uri_query sc_status cs_User_Agent
| sort - _time

Count Phishing Requests
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| stats count

Activity Timeline
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| timechart count

Top Source IPs
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| stats count by c_ip
| sort - count

Suspicious URL Paths
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
    OR cs_uri_stem="/login"
    OR cs_uri_stem="/account"
| stats count by cs_uri_stem
| sort - count

HTTP Response Codes
index=main sourcetype="iis"
| search cs_uri_stem="/verify"
| stats count by sc_status
| sort - count