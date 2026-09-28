IOC Extraction

For this lab, extract only indicators actually present in your evidence.

IOC Type	Example / Actual Value
Account	ayush
Source IP	192.168.234.129 if confirmed by event
Destination Host	DESKTOP-NH5RCBO
Destination IP	192.168.234.130
Event ID	4625
Event ID	4624
Event ID	4672 if observed
Event ID	4688
Process	Actual process from 4688
Command Line	Actual command line
Timestamp	Actual event timestamp
IOC Extraction Query
index=main (EventCode=4625 OR EventCode=4624 OR EventCode=4672 OR EventCode=4688)
| table _time host Account_Name Source_Network_Address New_Process_Name Process_Command_Line
| sort _time