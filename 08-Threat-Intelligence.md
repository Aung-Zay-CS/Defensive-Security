#  Threat Intelligence

Threat Intelligence is the analysis of data and information using tools and techniques to generate meaningful patterns on how to mitigate against potential risks associated with existing or emerging threats targeting organisations, industries, sectors or governments.
Traditionally, defenders use threat intelligence to provide context to the ever-changing threat landscape and quantify findings.
IOCs are quantified by traces left by adversaries such as domains, IPs, files, strings, etc. The blue team can utilize various IOCs to build detections and analyze behavior.
To mitigate against risks, we can start by trying to answer a few simple questions:
- Who's attacking you?
- What's their motivation?
- What are their capabilities?
- What artefacts and indicators of compromise should you look out for?

###  Threat Intelligence Classifications:

Threat Intel is geared towards understanding the relationship between your operational environment and your adversary.
With this in mind, we can break down threat intel into the following classifications: 
- ***Strategic Intel***: High-level intel that looks into the organisation's threat landscape and maps out the risk areas based on trends, patterns and emerging threats that may impact business decisions.
- ***Technical Intel***: Looks into evidence and artefacts of attack used by an adversary. Incident Response teams can use this intel to create a baseline attack surface to analyse and develop defence mechanisms.
- ***Tactical Intel***: Assesses adversaries' tactics, techniques, and procedures (TTPs). This intel can strengthen security controls and address vulnerabilities through real-time investigations.
- ***Operational Intel***: Looks into an adversary's specific motives and intent to perform an attack. Security teams may use this intel to understand the critical assets available in the organisation (people, processes, and technologies) that may be targeted.

###  Threat Intelligence tools

- [***Urlscan.io***](https://urlscan.io/): a free service developed to assist in scanning and analysing websites. It is used to automate the process of browsing and crawling through websites to record activities and interactions.
- [***PhishTool***](https://www.phishtool.com/): PhishTool seeks to elevate the perception of phishing as a severe form of attack and provide a responsive means of email security. 
- ***Abuse.ch***: a research project hosted by the Institue for Cybersecurity and Engineering at the Bern University of Applied Sciences in Switzerland. It was developed to identify and track malware and botnets through several operational platforms developed under the proje
    - [Malware Bazaar](https://bazaar.abuse.ch/):  A resource for sharing malware samples.
    - [Feodo Tracker](https://feodotracker.abuse.ch/):  A resource used to track botnet command and control (C2) infrastructure linked with Emotet, Dridex and TrickBot.
    - [SSL Blacklist](https://sslbl.abuse.ch/):  A resource for collecting and providing a blocklist for malicious SSL certificates and JA3/JA3s fingerprints.
    - [URL Haus](https://urlhaus.abuse.ch/):  A resource for sharing malware distribution sites.
    - [Threat Fox](https://threatfox.abuse.ch/):  A resource for sharing indicators of compromise (IOCs).

###  Cisco Talos Intelligence
IT and Cybersecurity companies collect massive amounts of information that could be used for threat analysis and intelligence. Being one of those companies, Cisco assembled a large team of security practitioners called Cisco Talos to provide actionable intelligence, visibility on indicators, and protection against emerging threats through data collected from their products. The solution is accessible as Talos Intelligence.

[Cisco Talos](https://talosintelligence.com/) encompasses six key teams:
- Threat Intelligence & Interdiction: Quick correlation and tracking of threats provide a means to turn simple IOCs into context-rich intel.
- Detection Research: Vulnerability and malware analysis is performed to create rules and content for threat detection.
- Engineering & Development: Provides the maintenance support for the inspection engines and keeps them up-to-date to identify and triage emerging threats.
- Vulnerability Research & Discovery: Working with service and software vendors to develop repeatable means of identifying and reporting security vulnerabilities.
- Communities: Maintains the image of the team and the open-source solutions.
- Global Outreach: Disseminates intelligence to customers and the security community through publications.
