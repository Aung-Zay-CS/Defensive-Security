#  The Cyber Kill Chain
The Cyber Kill Chain is a framework developed by Lockheed Martin to identify and prevent cyber intrusions by breaking down the steps an attacker takes to achieve their objective.
It is based on military attack principles and consists of seven stages:

![THE-CYBER-KILL-CHAIN](https://github.com/AungZayMyo/Defensive-Security/assets/154745254/549a59a1-4aa8-4a85-8042-be52de28a5d0)


- Reconnaissance: The attacker gathers information about the target, such as identifying potential vulnerabilities and the best methods of attack.
- Weaponization: The attacker creates a deliverable payload (e.g., malware) to exploit the identified vulnerabilities.
- Delivery: The attacker transmits the payload to the target (e.g., through email, websites, or other vectors).
- Exploitation: The payload is executed on the target system, exploiting the vulnerability.
- Installation: The attacker installs malware or backdoors on the compromised system to maintain access.
- Command and Control (C2): The attacker establishes a command channel to communicate and control the compromised system remotely.
- Actions on Objectives: The attacker takes actions to achieve their goals, such as data theft, system disruption, or further spreading the attack.

##  Example of a Cyber Kill Chain

Scenario: Phishing Attack Leading to Data Exfiltration
- Reconnaissance:
  - The attacker searches social media and corporate websites to gather information about employees and the organization’s structure. They identify potential targets (e.g., employees with access to sensitive data).
- Weaponization:
  - The attacker crafts a convincing phishing email that appears to be from a trusted source, such as a company executive or IT department. They attach a malicious document (e.g., a PDF or Word file) containing a hidden exploit.
- Delivery:
  - The phishing email is sent to the targeted employees.
- Exploitation:
  - An employee opens the malicious attachment, triggering the exploit. The exploit takes advantage of a vulnerability in the document reader software to execute code.
- Installation:
  - The code installs malware on the employee’s computer. The malware might be a keylogger or remote access trojan (RAT) that allows the attacker to control the system.
- Command and Control (C2):
  - The installed malware establishes a connection to the attacker’s C2 server, allowing the attacker to issue commands and exfiltrate data.
- Actions on Objectives:
  - The attacker uses the malware to search for and steal sensitive data, such as intellectual property, customer information, or financial records. They transfer the stolen data back to their own servers.

##  Example Tools 
- Reconnaissance
  - Attacking Tools / Techniques
      - `whois`
      - `censys`
      - `W3af`
      - `maltego`
      - `nmap`
  - Defensive Tools / Techniques
      - `shodan`
      - `snort`
- Weaponization
    - Attacking Tools / Techniques
      - `Metasploit`
      - `SETOOLKIT`
    - Defensive Tools / Techniques
      - `Threat Intelligence Platform`
      - `Security Awareness Training`
- Delivery
    - Attacking Tools / Techniques
      - `Phishing Kits`
      - `Drive-by Download Scripts`
    - Defensive Tools / Techniques
      - `Proofpoint`
      - `Cisco Umbrella`
- Exploitation
    - Attacking Tools / Techniques
      - `Angler`
      - `Neutrino`
    - Defensive Tools / Techniques
      - `Symantec`
      - `McAfee`
      - `Vulnerability Management`
- Installation
    - Attacking Tools / Techniques
      - `Poison Ivy`
      - `DarkComet`
    - Defensive Tools / Techniques
      - `CrowdStrike Falcon`
      - `Application Whitelisting`
- Command and Control (C2)
    - Attacking Tools / Techniques
      - `Cobalt Strike`
      - `DNS Tunneling Tools`
    - Defensive Tools / Techniques
      - `Wireshark`
      - `OpenDNS`
- Actions on Objectives
    - Attacking Tools / Techniques
      - `Exfil`
      - `Mimikatz `
    - Defensive Tools / Techniques
      - `Symantec DLP`
      - `User and Entity Behavior Analytics (UEBA)`
      - `Honeypot`
      - `Audit Log`

# Conclusion 

In this article, The Cyber Kill Chain Framework is described. Do more Practice and Expert it!. <br>
**5/18/2024** <br>
Contributed By - Jord@n
