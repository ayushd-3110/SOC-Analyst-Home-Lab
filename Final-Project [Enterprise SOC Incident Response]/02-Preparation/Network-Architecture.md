# Network Architecture

```text
                ┌──────────────────────┐
                │   Splunk Enterprise  │
                │        SIEM          │
                │      index=main      │
                └──────────┬───────────┘
                           │
                    Windows Telemetry
                           │
                ┌──────────▼───────────┐
                │    Windows Victim    │
                │ 192.168.234.130      │
                │ DESKTOP-NH5RCBO      │
                │ Sysmon + Windows Logs│
                └──────────▲───────────┘
                           │
                     Lab Traffic
                           │
                ┌──────────┴───────────┐
                │     Kali Linux       │
                │ 192.168.234.129      │
                │ Simulation / Testing │
                └──────────────────────┘
```

This is a private training environment. The systems are used only for controlled SOC exercises.
