
WINDOWS BRUTE FORCE DETECTION & INVESTIGATION LAB
============================================================

PROJECT TYPE:
SOC / Cybersecurity Investigation Project

CASE ID:
BRUTE-001

==============
1. PROJECT OVERVIEW
===============

This project demonstrates how a SOC Analyst can detect and
investigate repeated failed authentication attempts on a
Windows Server.

A controlled brute-force authentication simulation was
performed in a VMware laboratory environment.

Kali Linux was used as the attacker machine and Windows
Server 2025 was used as the target machine.

The main Windows security event investigated was:

Event ID 4625 - An account failed to log on.


===================
2. PROJECT OBJECTIVE
====================

The main objectives of this project were:

1. Create a controlled cybersecurity laboratory.

2. Generate multiple failed authentication attempts.

3. Detect the failed authentication attempts using Windows
   Security Event ID 4625.

4. Identify the source IP address.

5. Identify the targeted account.

6. Identify the authentication type.

7. Understand why the authentication failed.

8. Create an attack timeline.

9. Check whether the attack resulted in a successful login.

10. Create brute-force detection logic.

11. Identify relevant indicators.

12. Map the activity to MITRE ATT&CK.

13. Assess the incident severity.

14. Create a professional SOC incident report.


=====================
3. LAB ENVIRONMENT
======================

Virtualization Platform:
VMware

ATTACKER MACHINE:
Kali Linux

Kali IP Address:
192.168.87.128

TARGET MACHINE:
Windows Server 2025

Windows Server IP Address:
192.168.87.129

TARGET ACCOUNT:
soc-test

Authentication Method:
SMB / Network Authentication


========================
4. ATTACK SIMULATION
=========================

A controlled authentication test was performed from the Kali
Linux virtual machine against my own Windows Server 2025
virtual machine.

Five incorrect password attempts were intentionally generated
against the "soc-test" account.

The purpose was to simulate a small brute-force authentication
attempt and observe how Windows records the activity.

This was performed only inside my own isolated VMware
laboratory environment.


============================
5. WINDOWS EVENT DETECTED
=============================

Primary Event:

Event ID 4625

Meaning:

An account failed to log on.

Important information obtained from the event:

Target Account:
soc-test

Source IP:
192.168.87.128

Logon Type:
3 - Network

Failure Reason:
Unknown user name or bad password

Status:
0xC000006D

Sub Status:
0xC000006A

The Sub Status 0xC000006A indicates that the password was
incorrect.


=============================
6. ATTACK TIMELINE
==============================

Attack Date:
10/07/2026

First Attempt:
18:55:29

Second Attempt:
18:55:31

Third Attempt:
18:55:33

Fourth Attempt:
18:55:35

Fifth Attempt:
18:55:37

Total Attack Duration:
8 seconds

All five attempts:

Source IP:
192.168.87.128

Target Account:
soc-test

Event:
4625

Logon Type:
3 - Network


============================
7. INVESTIGATION FINDINGS
============================

During the investigation, the following was identified:

1. Five failed authentication attempts occurred.

2. All five attempts came from the same source IP:
   192.168.87.128

3. All attempts targeted the same account:
   soc-test

4. All attempts used network authentication:
   Logon Type 3

5. All attempts generated Event ID 4625.

6. The attempts occurred within an 8-second period.

7. The failure reason was invalid credentials.

8. The Sub Status was 0xC000006A, indicating an incorrect
   password.

9. Event ID 4624 was checked to determine whether any of the
   attempts resulted in a successful login.

10. No successful Event ID 4624 authentication was identified
    during the investigated timeframe.


============================
8. SUCCESSFUL LOGIN CHECK
=============================

After finding the five failed authentication events, I
checked Windows Security Event ID 4624.

Event ID 4624 represents a successful logon.

Result:

Failed Authentication Attempts:
5

Successful Authentication Identified:
0

Conclusion:

No evidence was found that the simulated brute-force attempt
successfully authenticated to the Windows Server.


=================================
9. BRUTE-FORCE DETECTION LOGIC
===================================

A potential brute-force alert can be generated when:

- Multiple Event ID 4625 events occur.
- The events come from the same source IP.
- The events target the same account or accounts.
- The events occur within a short period of time.

Laboratory detection threshold:

5 or more failed authentication attempts
from the same source IP
within 1 minute.


In this project:

Failed Attempts:
5

Source IP:
192.168.87.128

Target Account:
soc-test

Time Window:
8 seconds

Detection Condition:
MET


======================================
10. IOC / INVESTIGATION INDICATORS
======================================

Source IP:
192.168.87.128

Target IP:
192.168.87.129

Target Account:
soc-test

Event ID:
4625

Logon Type:
3

Status:
0xC000006D

Sub Status:
0xC000006A


IMPORTANT:

The IP address 192.168.87.128 belongs to the Kali Linux
virtual machine used for this controlled laboratory attack.

It should NOT be considered a malicious IP outside this
laboratory.


==============================
11. MITRE ATT&CK MAPPING
=============================

TACTIC:
Credential Access

TECHNIQUE:
T1110 - Brute Force

DESCRIPTION:

The activity involved repeated authentication attempts
against the same account using incorrect passwords.

The behavior is consistent with the Brute Force technique.


=======================
12. INCIDENT SEVERITY
========================

SEVERITY:
Medium

REASON:

Multiple rapid authentication failures were detected from
the same source against the same account.

However:

- No successful authentication was identified.
- No evidence of account compromise was found.
- The activity was intentionally generated in a controlled
  laboratory environment.

Therefore, the incident is classified as:

Attempted Brute Force / Unsuccessful Authentication


===================
13. SOC RESPONSE
===================

In a real production environment, a SOC Analyst could:

1. Investigate the source IP.

2. Identify whether the source is legitimate.

3. Investigate the targeted account.

4. Check for successful Event ID 4624 logons.

5. Check whether other accounts were targeted.

6. Check for account lockouts.

7. Review additional authentication activity.

8. Reset credentials if compromise is suspected.

9. Block or contain the source when appropriate.

10. Escalate the incident if successful authentication or
    additional suspicious activity is discovered.


=========================
14. FINAL CONCLUSION
==========================

This project successfully demonstrated a complete SOC
investigation workflow for a Windows brute-force
authentication attempt.

Five failed network authentication attempts were generated
from Kali Linux against the Windows Server 2025 machine.

The attempts targeted the "soc-test" account and generated
Windows Security Event ID 4625.

All five attempts originated from 192.168.87.128 and occurred
within an 8-second period.

The authentication failures had:

Status:
0xC000006D

Sub Status:
0xC000006A

The investigation also checked for Event ID 4624
successful authentication events.

No successful authentication was identified.

Therefore, the final conclusion is:

THE CONTROLLED BRUTE-FORCE ATTEMPT WAS DETECTED BUT
WAS UNSUCCESSFUL.

No evidence of successful account compromise was identified
during this investigation.


==========================
15. SKILLS DEMONSTRATED
===========================

Windows Event Viewer
Windows Security Logs
Event ID 4625 Analysis
Event ID 4624 Analysis
Authentication Log Analysis
SMB / Network Authentication
Brute-Force Detection
IOC Identification
Timeline Analysis
MITRE ATT&CK Mapping
SOC Investigation
Incident Severity Assessment
Incident Reporting
VMware Laboratory Setup
Kali Linux
Windows Server 2025


=========================
16. PROJECT STRUCTURE
==========================

01-Case-Intake
    Case-Intake.txt

02-Lab-Setup
    Lab-Environment.txt

03-Attack-Evidence
    Attack-Activity.txt

04-Windows-Logs
    Event-4625-Evidence.txt

05-Analysis
    Incident-Assessment.txt

06-Detection
    Detection-Logic.txt

07-Timeline
    Attack-Timeline.txt

08-IOCs
    IOC-List.txt

09-Incident-Report
    Final-Incident-Report.txt

10-Screenshots
    Investigation screenshots


===================
17. DISCLAIMER
====================

This project was performed entirely in a controlled VMware
laboratory environment using my own virtual machines.

The authentication attempts were intentionally generated
for cybersecurity learning, Windows event analysis, and
SOC investigation practice.

No unauthorized systems were targeted.


============================================================
END OF PROJECT README
============================================================
