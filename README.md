# Defensive-Security
Basic Defensive Security Concepts for Defensive Security. Before you dividing to the cyber security you must familiarity with security principles.

##  Terms

- Vulnerability: Vulnerable means susceptible to attack or damage. In information security, a vulnerability is a weakness.
- Threat: A threat is a potential danger associated with this weakness or vulnerability.
- Risk: The risk is concerned with the likelihood of a threat actor exploiting a vulnerability and the consequent impact on the business.

##  Security Principles

###  CIA Traid
When you want to judge the security of a system, you need to think in terms of the security triad: confidentiality, integrity, and availability (CIA).

- Confidentiality ensures that only the intended persons or recipients can access the data.
- Integrity aims to ensure that the data cannot be altered; moreover, we can detect any alteration if it occurs.
- Availability aims to ensure that the system or service is available when needed.

Going one more step beyond the CIA security triad, we can think of
- Authenticity: Authentic means not fraudulent or counterfeit. Authenticity is about ensuring that the document/file/data is from the claimed source.
- Nonrepudiation: Repudiate means refusing to recognize the validity of something. Nonrepudiation ensures that the original source cannot deny that they are the source of a particular document/file/data.

###  DAD
The security of a system is attacked through one of several means. It can be via the disclosure of secret data, alteration of data, or destruction of data.
- Disclosure is the opposite of confidentiality. In other words, disclosure of confidential data would be an attack on confidentiality.
- Alteration is the opposite of Integrity. For example, the integrity of a cheque is indispensable.
- Destruction/Denial is the opposite of Availability.

The opposite of the CIA Triad would be the DAD Triad: Disclosure, Alteration, and Destruction.
- Disclosure: As in most modern countries, healthcare providers must maintain medical records’ confidentiality. As a result, if an attacker succeeds in stealing some of these medical records and dumping them online to be viewed publicly, the health care provider will incur a loss due to this data disclosure attack.
- Alteration: Consider the gravity of the situation if the attacker manages to modify patient medical records. This alteration attack might lead to the wrong treatment being administered, and consequently, this alteration attack could be life-threatening.
- Destruction/Denial: Consider the case where a medical facility has gone completely paperless. If an attacker manages to make the database systems unavailable, the facility will not be able to function properly. They can go back to paper temporarily; however, the patient records won’t be available. This denial attack would stall the whole facility.

###  Defence-in-Depth
Defence-in-Depth refers to creating a security system of multiple levels; hence it is also called Multi-Level Security. Defense in depth is a strategy that leverages multiple security measures to protect an organization's assets.
The thinking is that if one line of defense is compromised, additional layers exist as a backup to ensure that threats are stopped along the way.

<p align="center"><img src="https://github.com/Aung-Zay-CS/Defensive-Security/assets/154745254/91ec6912-250b-4e4b-b532-351742b5f499" width="400px"></p>

###  Zero Trust
This principle treats trust as a vulnerability, and consequently, it caters to insider-related threats. After considering trust as a vulnerability, zero trust tries to eliminate it. It is teaching indirectly, “never trust, always verify.” In other words, every entity is considered adversarial until proven otherwise. Zero trust does not grant trust to a device based on its location or ownership. This approach contrasts with older models that would trust internal networks or enterprise-owned devices. Authentication and authorization are required before accessing any resource. As a result, if any breach occurs, the damage would be more contained if a zero trust architecture had been implemented.
