# Registry artifact and detection context

The screenshot verifies the controlled Run-key value `Lab5Persistence` pointing to `C:\Temp\lab5.bat`. The entry is a lab artifact, not a confirmed malicious IOC. Related event types include 4657 (registry value change), 4663 (object access) and 4688 (process creation); each must be interpreted in its own context. Execution and cleanup are not independently established.
