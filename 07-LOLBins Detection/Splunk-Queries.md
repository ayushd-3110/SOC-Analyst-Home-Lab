Query 1 — Verify Event 4688

index=main sourcetype="WinEventLog:Security" 
EventCode=4688

Query 2 — Basic Certutil Detection

index=main sourcetype="WinEventLog:Security" EventCode=4688
| search "certutil.exe"
| table _time host EventCode Message
| sort - _time


Query 3 — Extract Investigation Fields

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| search process_path="*certutil.exe"
| table _time host user process_path parent_process command_line
| sort - _time

Query 4 — Multiple LOLBins

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| eval process=lower(process_path)
| search process="*certutil.exe"
    OR process="*mshta.exe"
    OR process="*regsvr32.exe"
    OR process="*rundll32.exe"
    OR process="*bitsadmin.exe"
    OR process="*msiexec.exe"
    OR process="*wmic.exe"
| table _time host process_path Message
| sort - _time


Query 5 — LOLBin Timeline

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| eval process=lower(process_path)
| search process="*certutil.exe"
    OR process="*mshta.exe"
    OR process="*regsvr32.exe"
    OR process="*rundll32.exe"
    OR process="*bitsadmin.exe"
    OR process="*msiexec.exe"
    OR process="*wmic.exe"
| timechart count



5. Correlation Query
Create:

correlation.spl

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| eval process=lower(process_path)
| eval cmd=lower(command_line)
| search process="*certutil.exe"
    OR process="*mshta.exe"
    OR process="*regsvr32.exe"
    OR process="*rundll32.exe"
    OR process="*bitsadmin.exe"
    OR process="*msiexec.exe"
    OR process="*wmic.exe"
| eval suspicious_argument=if(
    match(cmd,"http|https|url|download|execute|javascript|vbscript|encoded"),
    "Yes",
    "No"
)
| eval risk=if(suspicious_argument="Yes","High","Review")
| table _time host user process_path parent_process command_line suspicious_argument risk
| sort - _time