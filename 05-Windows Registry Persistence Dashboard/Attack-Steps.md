# Attack Steps

## Step 1

Open Command Prompt as Administrator.

---

## Step 2

Create a malicious Run Key.

```
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run

 ^
/v WindowsUpdate ^
/t REG_SZ ^
/d "C:\Windows\System32\cmd.exe" ^
/f
```

Purpose:

Creates a startup registry entry that executes cmd.exe whenever the user logs in.

---

## Step 3

Verify the registry value.

```
reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run
```

---

## Step 4

Observe generated Security Events.

- 4688
- 4663
- 4657

---

## Step 5

Investigate in Splunk.