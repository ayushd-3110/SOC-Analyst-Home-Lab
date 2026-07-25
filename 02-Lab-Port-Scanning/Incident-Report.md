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