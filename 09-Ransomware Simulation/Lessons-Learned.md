# Lessons Learned

## 1. Process Telemetry Is Important

Event ID 4688 helped identify the process responsible for the simulated activity.

---

## 2. Command-Line Visibility Is Valuable

The process command line provided useful context about what the user or process executed.

---

## 3. Ransomware Detection Requires Multiple Signals

A single process-creation event is not enough to confirm ransomware.

A stronger SOC detection should correlate:

- Process creation
- File modification
- File renaming
- Unusual extensions
- Ransom-note creation
- EDR alerts

---

## 4. Context Matters

The activity was suspicious from a behavioral perspective, but investigation showed that it was an authorized lab simulation.

SOC analysts must verify context before declaring an incident.

---

## 5. Isolation Is Important

The simulation was performed inside a dedicated directory.

This prevented accidental modification of Windows or personal files.

---

## 6. Splunk Correlation Improves Detection

Correlating multiple security events provides more context than investigating a single event.

---

## Key Takeaway

Ransomware detection should focus on behavior rather than relying on a single indicator.