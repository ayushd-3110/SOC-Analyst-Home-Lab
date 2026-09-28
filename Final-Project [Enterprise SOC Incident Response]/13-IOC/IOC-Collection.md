# IOC Collection

## Host Indicators

- `DESKTOP-NH5RCBO`
- `192.168.234.130`

## Simulation Source

- `192.168.234.129` – Kali lab system

## User

- `ayush`

## Persistence Artifact

- `SOC-Enterprise-Persistence-Test`

## File / Command Indicators

- `SOC Enterprise Incident Simulation`
- `SOC Enterprise Credential Access Simulation`
- `persistence-test.cmd`
- `.locked` test files

## Hashes

No final-project malware hash is claimed from the supplied final-project screenshots. The exact hash visible in Lab 13 belongs to the harmless `malware_simulation.cmd` training artifact and is documented in Lab 13, not treated as a malicious IOC.

## IOC Handling Rule

A lab hostname, IP, filename, or command should be clearly marked as a **lab indicator** so it is not mistaken for a production IOC.
