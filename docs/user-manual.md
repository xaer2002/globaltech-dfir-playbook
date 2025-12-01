User Manual - Ransomware DFIR Response Guide

Document: User Manual
Project: COSC 435 – DFIR Playbook
Student: D'Marco Rodgers, Duran Anderson
Instructor: Dr. Devharsh Trivedi
Date: dec 1, 2025

1. Objective

This user manual provides a clear, step-by-step guide for responders dealing with the ransomware incident at GlobalTech Corp.
It serves as a simplified, quick-action reference based on the full DFIR playbook.

2. When to use this manual

Use this manual if any of the following occurs:

Ransom notes appear on the system

Files have been renamed or encrypted

Users report sudden access or file-availability issues

EDR alerts identify suspicious behavior

Network activity becomes unusually high or irregular

3. Immediate action (first 5 minutes)
1. Isolate the infected system immediately

Disconnect the Ethernet Cable

Disable Wi-Fi

Use the "Isolate Host" feature of the EDR platform, if available

2. Notify key response personnel

Contact the following teams immediately:

Security Operations Center (SOC)

incident commander

IT operations

3. Tasks to avoid

Do not shut down the system

Do not delete ransom notes or suspicious files

Do not run antivirus scan

Do not open unknown executables or attachments

These actions can destroy forensic evidence.

4. Evidence Collection Procedures
1. Capture Screenshot

Document:

ransom note message

encrypted or renamed files

suspicious processes

2. Collect System and Security Logs

Export the following:

windows event log

sysmon log

EDR alerts and detection

3. Acquire memory

Use WinPMEM to get volatile memory:

winpmem.exe --format raw --output memory.raw

4. Disc Imaging (if directed by DFIR Lead)

E01 Use FTK Imager to create a forensic disk image.

5. Full chain of custody documentation

Record:

name of collector

date and time