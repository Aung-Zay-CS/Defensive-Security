#  Information Security
Information security (infosec) refers to the protection of data resources from unauthorized access, attack, theft, or damage.
Data may be vulnerable because of the way it is stored, transferred, or processed. The systems used to store, transmit, and process data must demonstrate the properties of security.

Secure information has three properties, often referred to as the CIA Triad:
- Confidentiality means that information can only be read by people who have been explicitly authorized to access it.
- Integrity means that the data is stored and transferred as intended, and any modification is unauthorized unless explicitly authorized through proper channels.
- Availability means that information is readily accessible to those authorized to view or modify it.

##  CYBERSECURITY FRAMEWORK
A cybersecurity framework guides the selection and configuration of controls. Frameworks are important because they save an organization from building its security program in a vacuum, or from building the program on a foundation that fails to account for important security concepts.
The use of a framework allows an organization to make an objective statement of its current cybersecurity capabilities, identify a target level of capability, and prioritize investments to achieve that target.
This gives a structure to internal risk management procedures and provides an externally verifiable statement of regulatory compliance.

##  NIST FRAMEWORK
Within the goal of ensuring information security, cybersecurity refers specifically to provisioning secure processing hardware and software.
Information security and cybersecurity tasks can be classified as five functions, following the framework developed by the [National Institute of Standards and Technology](https://nist.gov/cyberframework/online-learning/five-functions).

<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/dbc62b44-bdbd-49ac-9e22-e331e563be5a" width="400px" height=400px"><br> NIST Framework </p>

- Identify: develop security policies and capabilities. Evaluate risks, threats, and vulnerabilities and recommend security controls to mitigate them.
- Protect: procure/develop, install, operate, and decommission IT hardware and software assets with security as an embedded requirement of every stage of this operation's lifecycle.
- Detect: perform ongoing, proactive monitoring to ensure that controls are effective and capable of protecting against new types of threats.
- Respond: identify, analyze, contain, and eradicate threats to systems and data security.
- Recover: implement cybersecurity resilience to restore systems and data if other controls are unable to prevent attacks.

##  ACCESS CONTROL
An access control system ensures that an information system meets the goals of the CIA triad. Access control governs how subjects/principals may interact with objects.
Subjects are people, devices, software processes, or any other system that can request and be granted access to a resource. Objects are the resources.
An object could be a network, server, database, app, or file. Subjects are assigned rights or permissions on resources.

Modern access control is typically implemented as an identity and access management (IAM) system. IAM comprises four main processes:
- Identification: creating an account or ID that uniquely represents the user, device, or process on the network.
- Authentication: proving that a subject is who or what it claims to be when it attempts to access the resource. An authentication factor determines what sort of credential the subject can use. For example, people might be authenticated by providing a password; a computer system could be authenticated using a token such as a digital certificate.
- Authorization: determining what rights subjects should have on each resource, and enforcing those rights. An authorization model determines how these rights are granted. For example, in a discretionary model, the object owner can allocate rights. In a mandatory model, rights are predetermined by system-enforced rules and cannot be changed by any user within the system.
- Accounting: tracking authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted.

<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/1ff7d658-baba-40ee-829a-4bd0216aea4f" width="450px" height=400px"><br> IAM system </p>

The servers and protocols that implement these functions can also be referred to as authentication, authorization, and accounting (AAA).

##  SECURITY CONTROL CATEGORIES
Information and cybersecurity assurance usually takes place within an overall process of business risk management. Implementation of cybersecurity functions is often the responsibility of the IT department.
There are many different ways of thinking about how IT services should be governed to fulfill overall business needs.
Some organizations have developed IT service frameworks to provide best practice guides to implementing IT and cybersecurity. These frameworks can shape company policies and provide checklists of procedures, activities, and technologies that represent best practice.

A security control is designed to give a system or data asset the properties of confidentiality, integrity, availability, and non-repudiation. Controls can be divided into four broad categories based on the way the control is implemented:
- Managerial: the control gives oversight of the information system. Examples could include risk identification or a tool allowing the evaluation and selection of other security controls.
- Operational: the control is implemented primarily by people. For example, security guards and training programs are operational controls.
- Technical: the control is implemented as a system (hardware, software, or firmware). For example, firewalls, antivirus software, and OS access control models are technical controls.
- Physical: controls such as security cameras, alarms, gateways, locks, lighting, and security guards that deter and detect access to premises and hardware are often placed in a separate category from technical controls.

##  SECURITY CONTROL FUNCTIONAL TYPES
As well as a category, a security control can be defined according to the goal or function it performs:

- Preventive: the control acts to eliminate or reduce the likelihood that an attack can succeed. A preventive control operates before an attack can take place. Access control lists (ACL) configured on firewalls and file system objects are preventive-type technical controls. Antimalware software acts as a preventive control by blocking malicious processes from executing.
- Detective: the control may not prevent or deter access, but it will identify and record an attempted or successful intrusion. A detective control operates during an attack. Logs provide one of the best examples of detective-type controls.
- Corrective: the control eliminates or reduces the impact of a security policy violation. A corrective control is used after an attack. A good example is a backup system that restores data that was damaged during an intrusion. Another example is a patch management system that eliminates the vulnerability exploited during the attack.
- Directive: the control enforces a rule of behavior, such as a policy, best practice standard, or standard operating procedure (SOP). For example, an employee's contract will set out disciplinary procedures or causes for dismissal if they do not comply with policies and procedures. Training and awareness programs can also be considered as directive controls.
- Deterrent: the control may not physically or logically prevent access, but it psychologically discourages an attacker from attempting an intrusion. This could include signs and warnings of legal penalties against trespass or intrusion.
- Compensating: the control is a substitute for a principal control, as recommended by a security standard, and affords the same (or better) level of protection but uses a different methodology or technology.

# Conclusion 

In this article, basic cybersecurity fundamental concepts are learned. Do more Practice and Expert it!. <br>
**6/2/2024** <br>
Contributed By - Jord@n
