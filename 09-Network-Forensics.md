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
