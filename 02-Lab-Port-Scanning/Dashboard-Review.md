# Archived dashboard review

I reviewed the recorded scan and Windows network telemetry. The investigation shows 8,072 Event 5156 records, including browser, DNS and Splunk forwarding activity.

The dashboard reflects total permitted connections, not 8,072 scan attempts. The Windows endpoint is the leading source in the dashboard. Event 5158 indicates a local port bind and cannot establish scanning independently.

The dashboard image remains unchanged. Any proposed improvement needs validation in Splunk before it is presented as an updated result.
