# Lab 03 - Windows Brute Force Attack Detection using Hydra

## Overview

This lab demonstrates how a SOC Analyst detects and investigates a Windows brute-force attack using Splunk Enterprise.

The attack is simulated from Kali Linux using Hydra against a Windows 10 virtual machine.

Authentication events are collected using Splunk Universal Forwarder and investigated within Splunk.

## Lab Environment

Host:
- Windows 11
- Splunk Enterprise

Attacker:
- Kali Linux
- IP: 192.168.234.129

Victim:
- Windows 10
- IP: 192.168.234.128

Installed Tools

- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon
- Hydra
- VMware Workstation

## Skills Learned

- Authentication Monitoring
- Windows Event Analysis
- Splunk SPL
- IOC Extraction
- Dashboard Development
- MITRE ATT&CK Mapping
- Incident Response