Dashboard — 5 Main Queries

Dashboard name:

Lab 12 - Account Compromise Investigation Dashboard

Panel 1 — Total Authentication Events

Visualization: Single Value

index=main (EventCode=4625 OR EventCode=4624)
| stats count as "Total Authentication Events"
Panel 2 — Failed vs Successful Authentication

Visualization: Column Chart

index=main (EventCode=4625 OR EventCode=4624)
| eval Authentication_Type=case(
    EventCode=4625,"Failed Login",
    EventCode=4624,"Successful Login"
)
| stats count by Authentication_Type
Panel 3 — Authentication Timeline

Visualization: Line Chart

index=main (EventCode=4625 OR EventCode=4624)
| eval Authentication_Type=case(
    EventCode=4625,"Failed Login",
    EventCode=4624,"Successful Login"
)
| timechart span=1m count by Authentication_Type
Panel 4 — Top Source IPs

Visualization: Bar Chart

index=main (EventCode=4625 OR EventCode=4624)
| stats count by Source_Network_Address
| sort - count
| head 10
Panel 5 — Post-Authentication Process Activity

Visualization: Table

index=main EventCode=4688
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time