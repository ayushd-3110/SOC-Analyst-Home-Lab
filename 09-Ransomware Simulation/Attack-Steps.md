# Attack Simulation

## Overview

This lab demonstrates ransomware-like behavior in a controlled Windows environment.

No real ransomware was used and no personal or system files were encrypted. The simulation was performed only inside:

C:\SOC-Ransomware-Lab

The purpose was to generate suspicious process activity that a SOC analyst could investigate using Windows Security logs and Splunk.

---

## Step 1 – Create the Lab Directory

The first step was to create an isolated directory:

C:\SOC-Ransomware-Lab

This directory was used to ensure that the simulation did not affect normal Windows files.

---

## Step 2 – Create Dummy Files

The following CMD command was used:

for /L %i in (1,1,20) do echo SOC Ransomware Test File %i > file%i.txt

This created 20 harmless test files:

file1.txt
file2.txt
...
file20.txt

### SOC Relevance

This represents files that could potentially be targeted during a ransomware attack.

---

## Step 3 – Simulate Mass File Modification

The following command was executed:

for /L %i in (1,1,20) do echo SIMULATED_RANSOMWARE_ACTIVITY >> file%i.txt

The command rapidly modified the test files.

The `>>` operator appends data to an existing file instead of overwriting it.

### SOC Relevance

Rapid modification of many files can be an indicator of ransomware-like activity.

---

## Step 4 – Simulate File Renaming

The files were renamed using:

for /L %i in (1,1,20) do ren file%i.txt file%i.locked

Example:

file1.txt → file1.locked

file2.txt → file2.locked

### SOC Relevance

Unexpected mass file renaming or unusual file extensions can indicate ransomware activity.

---

## Step 5 – Create a Simulated Ransom Note

A harmless simulation note was created:

echo THIS IS A SOC LAB RANSOMWARE SIMULATION > README_RANSOM_NOTE.txt

Additional text was added explaining that no real files were encrypted.

### SOC Relevance

The appearance of a ransom note together with mass file activity can increase the confidence of a ransomware investigation.

---

## Step 6 – Generate Windows Process Telemetry

Windows Security auditing generated Event ID 4688.

The event contained information such as:

- User account
- New process
- Parent process
- Process command line
- Host

Example observed process:

C:\Windows\System32\cmd.exe

Example command observed in Splunk:

cmd /c dir C:\SOC-Ransomware-Lab

---

## Result

The simulation generated ransomware-like activity in an isolated directory and produced Windows process telemetry that could be investigated using Splunk.

No real ransomware or real data encryption was performed.