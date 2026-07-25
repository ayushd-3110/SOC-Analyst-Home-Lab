# Lab 02 – Internal Port Scan Detection using Splunk

## Objective

Simulate an internal reconnaissance attack using Kali Linux against a Windows workstation and investigate the activity using Splunk Enterprise.

## Skills Learned

- Network Reconnaissance Detection
- Windows Firewall Log Analysis
- Splunk Searching
- IOC Identification
- MITRE ATT&CK Mapping
- Dashboard Development
- Incident Investigation

---

## Lab Architecture

Attacker

Kali Linux

IP:
192.168.234.129

↓

Victim

Windows 10

IP:
192.168.234.133

↓

Logs

Windows Security Logs

↓

Universal Forwarder

↓

Splunk Enterprise

Host

192.168.6.1

---

## Attack

Tool Used

Nmap

Command

nmap -sn 192.168.234.133 
sudo nmap -sV  192.168.234.133
nmap -A 192.168.234.133

---

## Detection

Windows Security Event ID

5156

5158

---

## MITRE ATT&CK

T1046

Network Service Discovery
