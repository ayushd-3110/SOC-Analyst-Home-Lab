# Incident Report

Incident ID : SOC-LAB-02

Date : 02 July 2026

Severity: Medium

Description: An internal workstation initiated multiple TCP connection attempts against another internal host using Nmap.

Affected Asset: Windows 10

Source: 192.168.234.129

Destination :192.168.234.133

Detection Source : Windows Security Event ID 5156

MITRE ATT&CK: T1046

Recommendation: Monitor the host for additional reconnaissance or lateral movement. Verify whether the scanning activity was authorized. Restrict unnecessary network access and implement alerting for repeated connection attempts.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
