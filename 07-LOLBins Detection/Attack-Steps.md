# Attack Steps — LOLBins Detection

## Step 1 — Prepare the Windows Victim

Verify that Windows Security Event ID 4688 is enabled and that
process command-line logging is enabled.

Verify:

Event Viewer
→ Windows Logs
→ Security

Confirm that new process creation events are being generated.

---

## Step 2 — Open Command Prompt

Open Command Prompt on the Windows victim machine.

The activity is performed in a controlled SOC lab environment.

---

## Step 3 — Execute the LOLBin

Run:

certutil -dump C:\Windows\System32\notepad.exe

This uses the legitimate Windows certutil.exe utility.

The command is intentionally used to generate process-execution
telemetry for detection testing.

---

## Step 4 — Observe the Command Result

The command may return:

CRYPT_E_NO_MATCH

This is expected because notepad.exe is not a certificate/container
that certutil can process with the -dump operation.

The failure of the command does not matter for this lab.

The important point is that certutil.exe was executed and Windows
generated process-creation telemetry.

---

## Step 5 — Verify Event ID 4688

Open:

Event Viewer
→ Windows Logs
→ Security

Locate the new Event ID:

4688 — A new process has been created.

Verify the following fields:

- Account Name
- New Process Name
- Creator Process Name
- Process Command Line
- New Process ID

Expected evidence:

New Process Name:
C:\Windows\System32\certutil.exe

Creator Process Name:
C:\Windows\System32\cmd.exe

Process Command Line:
certutil -dump C:\Windows\System32\notepad.exe

---

## Step 6 — Verify Splunk Ingestion

Wait for the Universal Forwarder to send the event to Splunk.

Search:

index=main sourcetype="WinEventLog:Security" EventCode=4688
| search "certutil.exe"

Confirm that the Certutil process-creation event appears.

---

## Step 7 — Investigate the Event

Analyze:

- Who executed the process?
- Which host executed it?
- What process launched it?
- What command line was used?
- Was the activity expected?
- Are there related suspicious events?

---

## Step 8 — Classify the Activity

For this lab, the activity is classified as:

Benign / Controlled Security Testing

In a real SOC environment, the analyst would investigate the
context before deciding whether the activity is malicious.