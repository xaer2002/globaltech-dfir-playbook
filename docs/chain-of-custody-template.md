Chain of Custody Template - Digital Forensics

Case Name: GlobalTech Corp – Ransomware Incident
Course: COSC 435 - Computer and Network Security
Student: D'Marco Rodgers, Duran Anderson
Instructor: Dr. Devharsh Trivedi
Date: dec 1, 2025

1. Evidence Observation
field description
Evidence ID	
Evidence types (disk image, memory dump, logs, screenshots, etc.)
Description	
Source system (hostname, IP address, username)
collection date/time	
name of collector	
Collector's signature	
Hash algorithm (SHA-256 required)
hash value	
storage space	
2. Evidence Management Log

Record every time evidence is moved, handled or accessed.

Date/Time Issued by (Name and Signature) Received by (Name and Signature) Purpose of Transfer Storage Location
				
				
				
3. Acquisition details
storage method

Specify the equipment and method used to obtain the evidence. Examples include:

FTK Imager (E01 Disk Image)

WinPMEM (Raw Memory Capture)

Exported Windows Event Log

sysmon log

Autopsy/Instability Analysis Workbench

acquisition notes

Document any notable things observed during the acquisition, such as:

timestamp

system behavior

errors occurred

environmental conditions

4. Verification
field information
Verified by	
Verification date/time	
hash recalculation yes/no
hash matches yes/no
Comments	
5. Final disposition

Describe the final state of the evidence after the investigation is completed. Example:

stored in a secure evidence repository

System returned to owner

destroyed as per policy

extended to legal/compliance

field information
last guardian	
final storage location	
final notes	
authorized by	
authorization date	
6. Signature
explorer

Name:
Signature:
Date:

Supervisor/Incident Commander

Name:
Signature:
Date: