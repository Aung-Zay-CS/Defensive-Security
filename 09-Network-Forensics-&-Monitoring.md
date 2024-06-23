#  Network Monitoring

Network monitoring is a set of management actions to watch/continuously overview and optionally save the network traffic for further investigation. This action aims to detect and reduce network problems, improve performance, and in some cases, increase overall productivity. It is a main part of the daily IT/SOC operations and differs from Network Security Monitoring (NSM) in its purpose. Network monitoring is highly focused on IT assets like uptime (availability), device health and connection quality (performance), and network traffic balance and management (configuration). Monitoring and visualising the network traffic, troubleshooting, and root cause analysis are also part of the Network Monitoring process. This model is helpful for network administrators and usually doesn't cover identifying non-asset in-depth vulnerabilities and significant security concerns like internal threats and zero-day vulnerabilities. Usually, Network Monitoring is not within the SOC scope. It is linked to the enterprise IT/Network management team.


###  Zeek
Zeek (formerly Bro) is an open-source and commercial passive Network Monitoring tool (traffic analysis framework) developed by Lawrence Berkeley Labs. Today, Zeek is supported by several developers, and Corelight provides an Enterprise-ready fork of Zeek. Therefore this tool is called both open source and commercial.

Zeek Signatures

Zeek supports signatures to have rules and event correlations to find noteworthy activities on the network. Zeek signatures use low-level pattern matching and cover conditions similar to Snort rules. Unlike Snort rules, Zeek rules are not the primary event detection point. Zeek has a scripting language and can chain multiple events to find an event of interest. We focus on the signatures in this task, and then we will focus on Zeek scripting in the following tasks.


#  Network Forensics
Network Forensics is a specific subdomain of the Forensics domain, and it focuses on network traffic investigation.
Network Forensics discipline covers the work done to access information transmitted by listening and investigating live and recorded traffic, gathering evidence/artefacts and understanding potential problems. 
Briefly, it is the action of recording packets of network traffic and creating investigatable sources and establishing a root–cause analysis of an event.
The ultimate goal is to provide sufficient information to detect malicious activities, security breaches, policy/regulation compliance, system health and user behaviour.
The investigation process identifies communicated hosts in terms of time, frequency, protocol, application and data.

###  The investigation tries to answer the 5W;
- Who (Source IP and port)
- What (Data/payload)
- Where (Destination IP and port)
- When (Time and data)
- Why (How/What happened)

###  Network Forensics Use Cases

The most common network forensics use cases are explained below;
- Network discovery: Discovering the network to overview connected devices, rogue hosts and network load.
- Packets reassembling: Reassembling the packets to investigate the traffic flow. This use case is helpful in unencrypted traffic flows.
- Data leakage detection: Reviewing packet transfer rates for each host and destination address helps detect possible data leakage.
- Anomaly and malicious activity detection: Reviewing overall network load by focusing on used ports, source and destination addresses, and data helps detect possible malicious activities along with vulnerabilities.
- Policy/Regulation compliance control: Reviewing overall network behaviour helps detect policy/regulation compliance.


###  Challenges of Network Forensics
General challenges of the network forensics are explained below;

- Deciding what to do: One of the most difficult challenges of network forensics is "Deciding what to do". There are several purposes of carving networks; SOC, IH/IR and Threat Hunting. Observing, trapping, catching, or stopping an anomalous activity is also possible.
- Sufficient data/evidence collection on the network: One of the advantages of network forensics is "Ease of collecting evidence". However, the breadth of this concept poses a challenge. There are multiple points to consider in data/evidence collection.
- Short data capture: One of the challenges in data/evidence collection. Capturing all network activity is not applicable and operable. So, it is hard always to have the packet captures that covers pre, during and post-event. 
- Encrypted traffic: Encrypted data is another challenge of network forensics. In most cases, discovering the contents of the encrypted data is not possible. However, the encrypted data still can provide valuable information for the hypothesis like source and destination address and used services.
- GDPR and Privacy concerns in traffic recording: Capturing the traffic is the same as "recording everything on the wire"; therefore, this act should comply with GDPR and business-specific regulations (e.g. HIPAA, PCI DSS and FISMA ).
- Time zone issues: Using a common time zone is important for big-scale event investigation. Especially when working with multiple resources over different time zones, usage of different time zones create difficulties in event correlation.
- Lack of logs: Network forensics is not limited to investigating the network traffic data. Network devices and event logs are crucial in event correlation and investigation hypotheses. This fact is known by the attackers/threats as well; therefore these logs are often erased by them, in order to make the investigation more difficult.


###  Sources of Network Forensics Evidence

Capturing proper network traffic requires knowledge and tools. Usually, there is a single chance of gathering the live traffic as evidence. There are multiple evidence resources to gather network forensics data.
- TAPS
- InLine Devices
- SPAN Ports
- Hubs
- Switches
- Routers
- DHCP Servers
- Name Servers
- Authentication Servers
- Firewalls
- Web Proxies
- Central Log Servers
- Logs (IDS/IPS, Application, OS, Device)

## Conclusion 

In this module, Network monitoring and forensics basic tools and concepts are learned. Do more Practice and Expert it!. <br>
**6/23/2024** <br>
Contributed By - Jord@n
