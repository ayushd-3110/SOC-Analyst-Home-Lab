# Screenshot Evidence Review

The Nmap screenshots show scanning against **192.168.234.133**. The open-port scan shows the host was up and **445/tcp (microsoft-ds)** was open, while most other TCP ports were filtered/no-response.

The screenshots also show open-port, aggressive, version-detection, ping, and full-TCP scan activity.

## Splunk Evidence
Screenshots named `splunk 5158.png` and `splunk 5156.png` show Windows firewall network events associated with the investigation.

## Evidence Boundary
The screenshots establish scanning activity and network telemetry. They do not prove successful exploitation of the Windows host.
