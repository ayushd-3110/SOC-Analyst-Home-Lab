Step 1 — Generate Failed Logins

From Kali:

smbclient -L //192.168.234.130 -U ayush

Enter an intentionally incorrect password.

Repeat approximately 3 times.

Expected Windows event:

Event ID: 4625
Description: An account failed to log on
Step 2 — Generate Successful Authentication

Run:

smbclient -L //192.168.234.130 -U ayush

Enter the correct password.

Expected event:

Event ID: 4624
Successful logon
Step 3 — Generate Harmless Process Activity

On the Windows VM:

whoami
hostname

Then:

cmd /c echo Account Compromise Simulation

Expected event:

Event ID: 4688
Process Creation
Step 4 — Check Privileged Activity

Search:

index=main EventCode=4672

If 4672 exists, determine which account generated it.

Do not automatically associate a SYSTEM 4672 event with ayush.