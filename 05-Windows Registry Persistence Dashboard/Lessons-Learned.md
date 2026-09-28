# Lessons Learned

- Registry Run Keys are a common persistence technique.
- Windows Security Logs can detect registry persistence without Sysmon.
- Correlating Event IDs 4688, 4663, and 4657 provides high-confidence detection.
- Splunk dashboards improve visibility into registry modifications.
- Registry auditing should be enabled on critical systems.