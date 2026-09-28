# Screenshot Evidence Review

The screenshots show Windows Security authentication events collected in Splunk.

- Successful logon screenshot: Event ID **4624**, host **DESKTOP-5T5E396** (as displayed in the screenshot).
- Failed logon screenshot: Event ID **4625**, host **DESKTOP-5T5E396**, account **LEO**, logon type **2**, with failure reason **Unknown user name or bad password**.
- The dashboard screenshot shows Windows authentication monitoring.

## Evidence Boundary
The screenshots prove that 4624/4625 telemetry was collected and searchable. They do not by themselves prove that the successful login was malicious.
