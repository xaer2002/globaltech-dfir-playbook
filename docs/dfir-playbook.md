DFIR PLAYBOOK — Targeted Ransomware Attack

Organization: GlobalTech Corp
Author: D’Marqco Rodgers, Duran Anderson
Course: COSC 435 – Computer & Network Security
Project: Final Project – DFIR Playbook (Project 8)
Instructor: Dr. Devharsh Trivedi
Date: dev 1, 2025

1. Purpose & Scope

This Digital Forensics & Incident Response (DFIR) Playbook outlines the procedures for detecting, containing, analyzing, and recovering from a Targeted Ransomware Attack against GlobalTech Corp.

The goal of this document is to:

Protect critical systems

Preserve forensic evidence

Ensure proper chain of custody

Guide containment & eradication

Support safe and verified recovery

Document lessons learned for improvement

This playbook applies to SOC analysts, DFIR responders, IT administrators, and legal/compliance resources during a ransomware incident.

2. Roles and Responsibilities
Incident Commander (IC)

Leads the response effort

Approves containment and communication decisions

Coordinates with executives, legal, and PR

SOC Analyst

Performs triage, alert validation, and initial identification

Collects logs, IOCs, and correlates evidence

Forensic Analyst

Performs memory capture, disk imaging, and artifact analysis

Guarantees chain of custody

IT Operations

Executes containment actions

Restores systems and verifies recovery

Legal & Compliance

Advises on external reporting requirements

Ensures all actions follow legal & regulatory guidelines

3. Incident Response Lifecycle (6 Phases)
PHASE 1 — Preparation

A successful response depends on readiness. Preparation includes:

Sysmon + Windows Event Logging enabled

EDR installed and reporting

Backup system tested regularly

IR team contact list up to date

Forensic toolkits ready:

FTK Imager

WinPMEM

Autopsy

Volatility

Chain-of-custody forms prepared

Isolated analysis workstation available

PHASE 2 — Identification

Goal: Confirm that ransomware activity is occurring.

Common Indicators of Ransomware

Encrypted files with unusual extensions

Ransom notes dropped in directories

Sudden CPU or disk usage spikes

Mass file rename/delete events

EDR alerts for:

Suspicious PowerShell

LSASS access

Shadow copy deletion

Credential dumping

Initial Actions

Validate the alert (SOC analyst).

Collect basic information:

Hostname

User logged in

IP address

Running processes

File changes

Save logs:

Windows Event Logs

Sysmon logs

Firewall logs

EDR alerts

Capture screenshots of visible ransom notes or encrypted files.

Notify Incident Commander.

PHASE 3 — Containment
Immediate Containment (within minutes)

Isolate infected systems (disconnect network cable, disable Wi-Fi, or use EDR isolate mode).

Disable compromised accounts (especially admins).

Block malicious IPs/domains/hashes at firewall/EDR.

Stop the spread by suspending SMB shares temporarily.

Short-Term Containment

Disable RDP and remote admin protocols.

Prevent backups from syncing encrypted files.

Verify lateral movement prevention.

Preserve evidence BEFORE powering off systems:

Memory capture

Process lists

Network connections

PHASE 4 — Eradication

After containment, the goal is to remove the malware and attacker.

Steps

Identify initial infection vector (phishing, RDP brute force, vulnerability exploit, etc.).

Remove malware binaries and persistence mechanisms.

Reset all affected passwords and API keys.

Patch exploited vulnerabilities.

Scan all systems with EDR / AV for confirmation.

Persistence Artifacts to Check

Run keys

Scheduled tasks

Services

DLL hijacking paths

Startup folders

PHASE 5 — Recovery

Restore systems safely and return to normal operations.

Recovery Steps

Restore systems from known-clean backups (offline/immutable preferred).

Rebuild compromised machines if needed.

Re-enable services gradually while monitoring logs.

Validate:

No reinfection

No suspicious outbound traffic

No new admin users

File integrity is restored

Post-Recovery Monitoring

Monitor for at least 14–30 days.

PHASE 6 — Lessons Learned

Held within 7 days of incident closure.

Review Checklist

What caused the incident?

Which controls failed or succeeded?

How fast did each phase occur?

What improvements can reduce future impact?

Update:

Playbook

Training

Detection rules

Network segmentation

Access controls

4. Forensic Procedures
A. Memory Acquisition (RAM)

Memory captures volatile evidence (keys, process injections, network sessions).

Tool: WinPMEM or FTK Imager
Procedure

Document system state & timestamp.

Insert USB with WinPMEM.

Run:

winpmem.exe --format raw --output memory.raw


Calculate and record SHA-256 hash.

Store memory.raw in evidence directory.

B. Disk Imaging

Disk imaging creates a forensically sound copy of the drive.

Tool: FTK Imager
Procedure

Launch FTK Imager as admin.

Create image → E01 format.

Save hash values (MD5 & SHA-256).

Verify image integrity.

Tag evidence with chain-of-custody.

C. Forensic Analysis
Recommended Tools

Autopsy

Volatility

Used for:

Timeline analysis

Deleted files

Registry artifacts

Memory process/dll injection

5. Evidence to Collect
Windows Logs

Event ID 4624/4625 → logon attempts

Event ID 4688 → process creation

Sysmon Event 1 → process creation

Sysmon Event 3 → network connections

Sysmon Event 11 → file create

Sysmon Event 13 → registry modification

Artifacts

Ransom notes

Encryption tool or dropper

Suspicious scheduled tasks

Malware hashes

Exfiltration logs

6. Chain of Custody Requirements

Every evidence item must include:

Field	Requirement
Evidence ID	Unique number
Description	What was collected
Collected By	Name + signature
Date/Time	Exact timestamp
Hash Values	SHA-256
Storage Location	Drive, folder, vault
Transfer Log	Every handoff recorded
7. Indicators of Compromise (IOCs)
File Indicators

Ransom notes (README.txt)

Encrypted extensions like .locked, .encrypted, etc.

Process Indicators

powershell.exe -enc ...

Unknown EXEs in %AppData%

Network Indicators

Outbound traffic to unknown foreign IPs

Repeated failed RDP attempts

8. Communications Plan
Internal

SOC

IT Ops

Executives

Daily or hourly updates

External

(through Legal only)

Law enforcement

Cyber insurance

Regulators

9. Ethical & Legal Considerations

All analysis done in isolated environments

No live malware on production systems

Forensic integrity must be preserved

Evidence secured according to legal standards

10. Conclusion

This DFIR Playbook provides a complete, structured approach for handling a targeted ransomware incident. It ensures rapid identification, proper evidence handling, safe recovery, and institutional learning to reduce repeated risk.