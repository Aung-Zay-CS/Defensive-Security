#  Risk Management

To study risk management, we need to ensure a proper understanding of the following terms:
- Threat: an intentional or accidental event that can compromise the security of an information system. Examples include hacking, phishing attacks, human error, and natural disasters.
- Vulnerability: a software, hardware, or network weakness that cybercriminals can exploit to gain unauthorised access or compromise a system.
- Asset: a valuable resource or component (tangible or intangible) that an organisation relies upon to achieve its objectives.
- Risk: the probability of a threat source exploiting an existing vulnerability and resulting in adverse business effects.
- Risk Management (RM): the process of identifying, assessing, and mitigating risk to maintain acceptable levels.

##  Threat
A threat is a potential harm or danger to an individual, organisation, or system. Threats can be classified into three main categories: human-made, technical, or natural.

###  Human-made threats
Human-made threats: These threats are caused by human activities or interventions. Examples include:
- Terrorism
- Wars and conflicts
- Riots and civil unrest
- Cyberattacks
- Industrial accidents
- Arson
As can be seen, human-made threats are not limited to cyberattacks; although they do not require technical expertise, arson is a grave threat.
Realising any of these threats can have the power to disrupt the whole business; both a cyberattack and arson can prevent a company from functioning for a while.

###  Technical threats
Technical threats: These threats result from technological failures, malfunctions, or vulnerabilities. Examples include:
- Power outages
- Software and hardware failures
- Data breaches
- Network and system vulnerabilities
- Equipment malfunctions
A power outage can halt an entire company without a backup power source. A failed power supply means the whole server is down unless another backup power supply is on standby.
Any of these technical threats can prevent business processes from moving forward; therefore, considering each of these threats is a must in any risk analysis.

###  Natural threats
Natural threats: These are threats caused by natural events or phenomena. Examples include:
- Earthquakes
- Floods

Natural threats depend on the location of the company or data centre. Studying the natural hazards to which a particular area is exposed is necessary to ensure proper risk analysis.

##  Vulnerability
A vulnerability is a weakness in the system or software that can be exploited by a threat to cause harm.
To elaborate, it is a weakness that can be exploited by malicious individuals, groups, or external factors to gain unauthorised access, cause damage, or compromise the integrity, availability, or confidentiality of a system, data, or network.
Vulnerabilities can arise from software bugs, misconfigurations, or outdated security.

##  Asset
An asset is an economic resource owned or controlled by an individual, company, or government. It typically has the potential to provide some future benefit.
Assets include cash and cash equivalents, accounts receivable, investments, stock, equipment, real estate, and intellectual property.
In the context of information systems, an asset in information systems refers to any valuable resource or component (tangible or intangible) that an organisation relies upon to achieve its objectives. These assets are critical for successfully operating and managing the organisation’s information processes.

Some examples of assets in an information system include:
- Hardware: Servers, workstations, routers, switches, firewalls, and other physical devices used to store, process, and transmit information.
- Software: Operating systems, applications, databases, and other programs that enable the organisation to perform its functions efficiently and effectively.
- Data: Organisational data, which includes sensitive information such as customer records, financial data, intellectual property, and personal data of employees.
- Documentation: Manuals, policy documents.

##  Risk Management
Risk is the probability of a threat source exploiting an existing vulnerability (in an asset) and resulting in adverse business effects. 
Risk management is a process of identifying, assessing, and responding to risks associated with a particular situation or activity.
It involves identifying potential risks, assessing their likelihood and impact, evaluating possible solutions, and implementing the chosen solutions to limit or mitigate risk.
It also involves monitoring and assessing the effectiveness of the solutions put in place.

A Risk Management Policy is a set of procedures and processes designed to minimise the chances of an adverse event or outcome for an organisation.
It helps organisations identify, assess, and manage potential and actual risks related to their operations, financial activities, and compliance with applicable laws and regulations.
The policy provides guidance on identifying and assessing risks, as well as assigning tasks and responsibilities to those involved in managing them.

Information Systems Risk Management is a system of policies, procedures, and practices that seek to protect a company’s computer system from various internal and external threats.
It includes identifying threats, assessing the probability of their occurrence, and evaluating the effectiveness of various measures that can be taken to limit the damage they could cause.
The process also involves determining the resources that should be allocated to respond to potential threats, as well as monitoring and maintaining the integrity of the system.

##  Risk Assessment Methodologies
There are several frameworks for risk assessment. Example methodologies are:

###  NIST SP 800-30
NIST SP 800-30: A risk assessment methodology developed by the National Institute of Standards and Technology (NIST).
It involves identifying and evaluating risks, determining the likelihood and impact of each risk, and developing a risk response plan.

###  Facilitated Risk Analysis Process (FRAP)
Facilitated Risk Analysis Process (FRAP): A risk assessment methodology that involves a group of stakeholders working together to identify and evaluate risks.
It is designed to be a more collaborative and inclusive approach to risk analysis.

###  Operationally Critical Threat, Asset, and Vulnerability Evaluation (OCTAVE)
Operationally Critical Threat, Asset, and Vulnerability Evaluation (OCTAVE): A risk assessment methodology that focuses on identifying and prioritising assets based on their criticality to the organisation’s mission and assessing the threats and vulnerabilities that could impact those assets.

###  Failure Modes and Effect Analysis (FMEA)
Failure Modes and Effect Analysis (FMEA): A risk assessment methodology commonly used in engineering and manufacturing.
It involves identifying potential failure modes for a system or process and then analysing the possible effects of those failures and the likelihood of their occurrence.

##  Risk Analysis
We have two approaches when it comes to risk analysis:

- Qualitative Risk Analysis, where we assign ratings to risks. The ratings can be a qualitative adjective, such as high, medium, and low. Alternatively, it can be something symbolic, such as red, yellow, and green.
- Quantitative Risk Analysis, where we assign monetary values and use that as a basis for decision-making.

###  Qualitative Risk Analysis
As the name suggests, qualitative risk analysis uses qualitative adjectives to describe:
- Probability of a risk-taking place, i.e., probability of a threat exploiting a vulnerability
- Impact of the risk, if realised, which can range between trivial to extreme

###  Quantitative Risk Analysis
Single Loss Expectancy
Using quantitative analysis, we need to assign monetary values and numeric percentages. Let’s start with the following equation:

`SLE = AssetValue × EF`

Where:

Single Loss Expectancy (SLE) is the loss incurred due to the realisation of a threat represented as a monetary value.
Asset Value is the monetary valuation of an asset
Exposure Factor (EF) is the percentage of loss a realised threat can cause to an asset.
SLE Numeric Example
Consider the following numeric example for a work laptop considering the threat of a ransomware virus.

Asset Value = $10,000; the laptop is worth $1000, and the data are worth $9000.
EF = 90%; a ransomware infection would cause all the data to be unusable.
Consequently,

`SLE = AssetValue × EF = $10, 000 × 90% = $9, 000.`

In other words, a ransomware infection for such a work laptop would cause the company to lose $9000, assuming there is no backup copy.

Annualised Loss Expectancy
However, this information is insufficient for us to decide on countermeasures. We need to find the expected loss per year.

`ALE = SLE × ARO`

Where:

Annualised Loss Expectancy (ALE) is the loss the company expects to lose per year due to the threat.
Annualised Rate of Occurrence (ARO) is the expected number of times this threat is realised yearly, i.e., frequency per year.
Why do we need to calculate ALE? ALE helps us decide whether paying for a particular control or safeguard is justified, as we will see in Task 7.

ALE Numeric Example
Let’s revisit our example and calculate the ALE.

We have already calculated the SLE as $9000; we need to figure out how often we expect this incident to happen yearly.
Based on experience, a work computer is infected with ransomware once every two years. Hence, the annualised rate of occurrence is 0.5.

Consequently,

`ALE = SLE × ARO = $9000 × 0.5 = $4, 500.`

In simple terms, we expect the ransomware threat to cost us $4500 per laptop per year unless we take proper measures.

##  Risk Respond
Risk management’s third component focuses on how organisations respond to the risks identified through risk assessment. What are the possible responses to risks?
- Avoid Risk
- Transfer Risk (or Share Risk)
- Mitigate Risk (or Reduce Risk)
- Accept Risk

The response you choose against the risk takes into account the severity of the threat, the probability of occurrence, and the costs of the possible countermeasures. Let’s cover each in more detail.
- Avoid Risk: If a company decides to eliminate the activity that leads to the risk, that would be risk avoidance. A bank might decide that all employees’ computers cannot access the Internet to protect its systems against all online threats. An organisation might instruct its employees to work exclusively using the workstations on its premises to prevent data from being stolen.
- Transfer Risk: A company might consider the risk too high to handle, so it decides to purchase insurance. That would be risk transference or risk sharing. A publishing house might buy insurance against fire, for instance.
- Mitigate Risk: A company might invest in countermeasures to reduce risk to an acceptable level; this would be risk mitigation. To protect against computer viruses, a company might install antivirus on all its computers instead of blocking access to the Internet and glueing the USB ports.
- Accept Risk: Sometimes, the countermeasure cost exceeds the loss incurred if the risk is realised.

