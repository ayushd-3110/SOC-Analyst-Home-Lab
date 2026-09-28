# Lessons Learned

1. LOLBins are legitimate Windows utilities that can be abused by
   attackers.

2. Event ID 4688 is an important source of process execution telemetry.

3. Command-line logging provides valuable investigation context.

4. The executable name alone is not enough to classify an event as
   malicious.

5. Parent-child process relationships help analysts understand
   execution chains.

6. User and host information are important during alert triage.

7. Splunk can be used to detect and investigate LOLBin execution.

8. Multiple LOLBins can be monitored through a common detection rule.

9. Correlation and contextual analysis can reduce false positives.

10. IOC collection must be based on observed evidence.

11. MITRE ATT&CK mapping should describe the observed behavior rather
    than simply labeling a binary as malicious.

12. A SOC analyst should determine intent before escalating an alert.