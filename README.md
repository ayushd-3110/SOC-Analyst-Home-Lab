# SOC Analyst Home Lab | Ayush Dhumal

A hands-on SOC analyst portfolio focused on Windows and IIS telemetry, Splunk search and dashboards, alert triage, threat hunting, evidence interpretation and incident reporting. All activities were performed in a controlled training environment.

## Portfolio

| Lab | Investigation |
|---|---|
| 01 | [Windows Authentication Monitoring](01-Windows-Event-Logs/README.md) |
| 02 | [Network Connection and Port-Scan Investigation](02-Lab-Port-Scanning/README.md) |
| 03 | [Brute-Force Authentication Investigation](03-Brute-Force-Attack/README.md) |
| 04 | [PowerShell Activity Investigation](04-PowerShell-Attack-Detection/README.md) |
| 05 | [Registry Persistence Investigation](05-Windows%20Registry%20Persistence%20Dashboard/README.md) |
| 06 | [Scheduled Task Investigation](06-Scheduled%20Task%20Persistence/README.md) |
| 07 | [LOLBins Process Investigation](07-LOLBins%20Detection/README.md) |
| 08 | [Credential-Access Indicator and Privileged Logon Investigation](08-Credential%20Access%20Detection%20%26%20Privileged%20Activity%20Investigation/README.md) |
| 09 | [Ransomware-Style File Activity Investigation](09-Ransomware%20Simulation/README.md) |
| 10 | [IIS Web Security Investigation](10-Web%20Attack%20Detection/README.md) |
| 11 | [Phishing Link Triage](11-Phishing%20Investigation/README.md) |
| 12 | [Suspected Account Compromise Investigation](12-Account%20Compromise%20Investigation/README.md) |
| 13 | [Harmless Malware-Artifact Investigation](13-Malware%20Investigation/README.md) |
| 14 | [Endpoint Threat Hunting](14-Threat%20Hunting/README.md) |
| Capstone | [Enterprise SOC Incident Response](Final-Project%20%5BEnterprise%20SOC%20Incident%20Response%5D/README.md) |

## Environment

- Splunk Enterprise and Windows Security logs
- Sysmon and Windows endpoint telemetry where available
- IIS web logs for web- and email-link investigations
- Windows and Kali virtual machines in a controlled network

The lab environment changed across exercises; each lab documents its own observed host and date. The final project uses Windows host DESKTOP-NH5RCBO, index main and private lab addresses.

## Evidence and scope

Each lab includes a screenshot-grounded evidence summary and an incident report. The archive contains 148 original PNG screenshots and two PDF dashboard exports. An observed event is not automatically a malicious event; a keyword match, successful logon or HTTP response does not establish compromise. Simulated behavior and unverified hypotheses are labeled accordingly.

Archived dashboard results are kept as captured. Reviewed searches and proposed improvements have not been executed in a live Splunk instance as part of the documentation revision.

## Skills demonstrated

Authentication triage, Windows event review, process analysis, network and web log interpretation, false-positive assessment, threat hunting, incident timelines, evidence handling and SOC reporting.

See [Skills Demonstrated](Skills-Demonstrated.md) for the skills overview.
