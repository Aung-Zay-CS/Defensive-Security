#  Digital Forensics and Incident Response
 DFIR stands for Digital Forensics and Incident Response. This field covers the collection of forensic artifacts from digital devices such as computers, media devices, and smartphones to investigate an incident.
 This field helps Security Professionals identify footprints left by an attacker when a security incident occurs, use them to determine the extent of compromise in an environment, and restore the environment to the state it was before the incident occurred. 

###  The need for DFIR
DFIR helps security professionals in various ways, some of which are summarized below:
- Finding evidence of attacker activity in the network and sifting false alarms from actual incidents.
- Robustly removing the attacker,  so their foothold from the network no longer remains.
- Identifying the extent and timeframe of a breach. This helps in communicating with relevant stakeholders.
- Finding the loopholes that led to the breach. What needs to be changed to avoid the breach in the future?
- Understanding attacker behavior to pre-emptively block further intrusion attempts by the attacker.
- Sharing information about the attacker with the community.

###  Who performs DFIR?
As the name suggests, DFIR requires expertise in both Digital Forensics and Incident Response.
- Digital Forensics: These professionals are experts in identifying forensic artifacts or evidence of human activity in digital devices. 
- Incident Response: Incident responders are experts in cybersecurity and leverage forensic information to identify the activity of interest from a security perspective.

###  Basic concepts of DFIR
***Artifacts***
- Artifacts are pieces of evidence that point to an activity performed on a system. When performing DFIR, artifacts are collected to support a hypothesis or claim about attacker activity. For example, if we are to claim that the attacker used Windows registry keys to maintain persistence on a system, we can use the said registry key to support our claim. In this case, the mentioned registry key will be considered an artifact.

***Evidence Preservation***
- When performing DFIR, we must maintain the integrity of the evidence we are collecting. Therefore, the evidence is first collected and write-protected. Then, a copy of the write-protected evidence is used for analysis. This process ensures that our original evidence is not contaminated and remains safe while analyzing.

***Chain of custody***
- Another critical aspect of maintaining the integrity of evidence is the chain of custody. When the evidence is collected, it must be made sure that it is kept in secure custody. Any person not related to the investigation must not possess the evidence, or it will contaminate the chain of custody of the evidence.

***Order of volatility***
- Digital evidence is often volatile, i.e., it can be lost forever if not captured in time. For example, data in a computer system's memory (RAM) will be lost when the computer is shut down since the RAM keeps data only as long as it remains powered on. Some sources are more volatile as compared to others. For example, a hard drive is persistent storage and maintains the data even if power is lost. Therefore, a hard drive is less volatile than RAM. While performing DFIR, it is vital to understand the order of volatility of the different evidence sources to capture and preserve accordingly. In the example above, we will need to preserve the RAM before preserving the hard drive since we might lose data in the RAM if we don't prioritize it.

***Timeline creation***
- Once we have collected the artifacts and maintained their integrity, we need to present them understandably to fully use the information contained in them. A timeline of events needs to be created for efficient and accurate analysis. This timeline of events puts all the activities in chronological order. This activity is called timeline creation.

###  DFIR Tools
The security industry has built various exciting tools to help with the DFIR process. These tools help save valuable time and enhance the capabilities of security professionals.

***Eric Zimmerman's tools***
- Eric Zimmerman is a security researcher who has written a few tools to help perform forensic analysis on the Windows platform. These tools help the registry, file system, timeline, and many other analyses.

***KAPE***
- Kroll Artifact Parser and Extractor (KAPE) is another beneficial tool by Eric Zimmerman. This tool automates the collection and parsing of forensic artifacts and can help create a timeline of events.

***Autopsy***
- Autopsy is an open-source forensics platform that helps analyze data from digital media like mobile devices, hard drives, and removable drives. Various plugins for autopsy speed up the forensic process and extract and present valuable information from the raw data sources.

***Volatility***
- Volatility is a tool that helps perform memory analysis for memory captures from both Windows and Linux Operating Systems. It is a powerful tool that can help extract valuable information from the memory of a machine under investigation.

***Redline***
- Redline is an incident response tool developed and freely distributed by FireEye. This tool can gather forensic data from a system and help with collected forensic information.

***Velociraptor***
- Velociraptor is an advanced endpoint-monitoring, forensics, and response platform. It is open-source but very powerful.

###  Incident Response Process
- Preparation: Before an incident happens, preparation needs to be done so that everyone is ready in case of an incident. Preparation includes having the required people, processes, and technology to prevent and respond to incidents.
- Identification: An incident is identified through some indicators in the identification phase. These indicators are then analyzed for False Positives, documented, and communicated to the relevant stakeholders.
- Containment: In this phase, the incident is contained, and efforts are made to limit its effects. There can be short-term and long-term fixes for containing the threat based on forensic analysis of the incident that will be a part of this phase.
- Eradication: Next, the threat is eradicated from the network. It has to be ensured that a proper forensic analysis is performed and the threat is effectively contained before eradication. For example, if the entry point of the threat actor into the network is not plugged, the threat will not be effectively eradicated, and the actor can gain a foothold again.
- Recovery: Once the threat is removed from the network, the services that had been disrupted are brought back as they were before the incident happened.
- Lessons Learned: Finally, a review of the incident is performed, the incident is documented, and steps are taken based on the findings from the incident to make sure that the team is better prepared for the next time an incident occurs.

<p align="center"><img src="https://github.com/Aung-Zay-CS/Defensive-Security/assets/154745254/f77226a0-8248-4055-9bf2-d0611ab77422" width="400px" height="400px"><br>Lifecycle</p>

## Conclusion 

In this module, Incident Response handling process and Digital forensics process are learned. Do more Practice and Expert it!. <br>
**6/28/2024** <br>
Contributed By - Jord@n
