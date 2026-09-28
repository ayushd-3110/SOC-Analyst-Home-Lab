# Screenshot Evidence Review

The screenshots provide an important distinction between failed authentication evidence and successful-authentication evidence.

### Failed Logons – Confirmed
The Splunk screenshot shows **4 failed logons** for account **ayush**, source IP **192.168.234.129**, host **DESKTOP-NH5RCBO**.

### Successful Logon Screenshot – Context Matters
The screenshot titled `05-Successful Logon 4624.png` shows Event ID **4624**, but the visible rows are for **DESKTOP-NH5RCBO$ / SYSTEM**, logon type **5**, using **Negotiate**. It does **not** visibly prove a successful `ayush` logon from 192.168.234.129.

### 4672
The privileged-logon screenshot shows **SYSTEM** with multiple privileges. It should not be attributed to `ayush`.

### 4688
The visible process-creation search is dominated by `SplunkForwarder` process activity in the displayed rows. It does not, by itself, prove that `ayush` executed a suspicious process.

## Evidence Boundary
The screenshots strongly support repeated failed authentication against `ayush` from the Kali IP. They do not provide enough visible evidence to claim a successful `ayush` authentication or a confirmed account compromise.
