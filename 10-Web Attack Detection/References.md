# References – Lab 10 Web Attack Detection

## Lab Sources

This lab used the following local components:

- Windows IIS web server
- IIS W3C access logs
- Splunk Enterprise
- Kali Linux
- `curl`
- Windows Event / IIS telemetry

## Investigation References

Useful concepts for this lab:

- IIS access-log analysis
- HTTP request methods and status codes
- Web enumeration
- SQL injection indicators
- Path traversal indicators
- Active scanning
- Exploit attempts against web applications

## Evidence Note

The lab generated controlled requests such as SQL-injection-style and path-traversal-style URLs.

A `200 OK` response only shows that the web server returned a response. It does **not** prove that the simulated attack successfully exploited the application.

## MITRE ATT&CK References

- T1595 – Active Scanning
- T1190 – Exploit Public-Facing Application

These mappings describe the behavior being simulated or investigated; they do not claim that a real compromise occurred.
