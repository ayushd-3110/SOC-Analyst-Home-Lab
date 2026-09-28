# Indicators of Compromise

## Network IOC

Source IP:

192.168.234.129

Target IP:

192.168.234.130

---

## User-Agent

curl/8.19.0

---

## Suspicious URLs / Paths

/Lab10/default.asp

/Lab10/admin

/Lab10/login

/Lab10/backup

/Lab10/robots.txt

---

## Suspicious Parameters

id=1%27%20OR%20%271%27=%271

file=../../../../Windows/win.ini

---

## Attack Indicators

SQL Injection-style input:

%27 OR %27

Path Traversal:

../

Sensitive file reference:

win.ini

Web enumeration:

admin
login
backup
robots.txt