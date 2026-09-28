# Lab 10 — Web Attack Detection & Investigation

## 📌 Overview

In this lab, I created a small web security monitoring environment using
Windows IIS, Kali Linux, and Splunk.

The main goal was to simulate common web attacks against an IIS web
application and investigate the activity from the logs collected in Splunk.

The attacks simulated in this lab were:

- SQL Injection
- Path Traversal
- Web/Directory Enumeration

I used Kali Linux as the attacker machine and Windows IIS as the victim
web server. IIS logs were forwarded to Splunk for detection and analysis.

---

## 🏗️ Lab Architecture

Kali Linux
192.168.234.129
       |
       | HTTP Requests
       ↓
Windows IIS Web Server
192.168.234.130
       |
       | IIS Logs
       ↓
Splunk Enterprise
       |
       ↓
Detection → Investigation → IOC → Incident Response

---

## 🎯 Objectives

1. Configure IIS as a web server.
2. Create a controlled vulnerable web application.
3. Generate simulated web attacks from Kali Linux.
4. Collect IIS logs in Splunk.
5. Detect suspicious web requests.
6. Investigate the attacker activity.
7. Extract Indicators of Compromise (IOCs).
8. Create a Splunk dashboard.
9. Map the activity to MITRE ATT&CK.
10. Document the incident like a SOC analyst.

---

## 🛠️ Tools Used

- Kali Linux
- Windows 10
- Microsoft IIS
- Splunk Enterprise
- Splunk Universal Forwarder
- curl
- PowerShell
- Windows Event Logging

---

## 🌐 Lab IP Addresses

Attacker:
192.168.234.129

Victim Web Server:
192.168.234.130

Web Server:
Microsoft IIS 10.0

---

## 🔥 Attacks Simulated

### 1. SQL Injection

A SQL injection-style request was generated using:

id=1%27%20OR%20%271%27=%271

This request was sent to the IIS application to simulate an attacker
attempting to manipulate a web application's database query.

### 2. Path Traversal

A path traversal-style request was generated using:

file=../../../../Windows/win.ini

The request attempts to move outside the intended application directory
and access a Windows system file.

### 3. Web Enumeration

Several common web paths were requested:

/admin
/login
/backup
/robots.txt

This simulates reconnaissance where an attacker searches for
administrative pages, login portals, backup files and other interesting
resources.

---

## 📊 Splunk Detection

The IIS logs were successfully received by Splunk using:

index=main sourcetype="iis"

The logs contained useful fields such as:

- c_ip
- cs_method
- cs_uri_stem
- cs_uri_query
- sc_status
- cs_User_Agent

---

## 🔎 Investigation Findings

The investigation identified:

Attacker IP:
192.168.234.129

Victim:
192.168.234.130

User-Agent:
curl/8.19.0

Suspicious activities included:

- SQL injection-style request
- Path traversal-style request
- Enumeration of /admin
- Enumeration of /login
- Enumeration of /backup
- Request for /robots.txt

The requests occurred within a short time period, which increased the
likelihood that they were part of the same reconnaissance/attack sequence.

---

## 🚨 Conclusion

The lab successfully demonstrated how a SOC analyst can use IIS logs and
Splunk to identify suspicious web activity.

The activity was detected, investigated and correlated using the source IP,
requested URI, query parameters, HTTP status codes and User-Agent.

This lab demonstrates practical skills in:

- Web log analysis
- Splunk SIEM
- Attack detection
- IOC extraction
- Incident investigation
- Incident response
- Security monitoring

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
