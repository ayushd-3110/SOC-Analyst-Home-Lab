# Initial Access Simulation

## Goal

Generate a controlled authentication pattern that can be investigated as an initial-access signal.

## Activity

From Kali, SMB authentication was tested against the Windows lab system.

### Failed Authentication

Run the SMB command and intentionally enter an incorrect password several times:

```bash
smbclient -L //192.168.234.130 -U ayush
```

Generate approximately three failed attempts.

### Successful Authentication

Run the same command again and use the correct lab password:

```bash
smbclient -L //192.168.234.130 -U ayush
```

## Expected Evidence

- Event 4625 – failed logon
- Event 4624 – successful logon

## Important

This is a lab simulation. A successful authentication after failed attempts is an investigation lead, not automatic proof of account compromise.
