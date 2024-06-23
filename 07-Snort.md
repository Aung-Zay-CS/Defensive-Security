#  Snort
SNORT is an open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS). It was developed and still maintained by Martin Roesch, open-source contributors, and the Cisco Talos team. 

Capabilities of Snort;
- Live traffic analysis
- Attack and probe detection
- Packet logging
- Protocol analysis
- Real-time alerting
- Modules & plugins
- Pre-processors
- Cross-platform support! (Linux & Windows)

Snort has three main use models;

- Sniffer Mode - Read IP packets and prompt them in the console application.
- Packet Logger Mode - Log all IP packets (inbound and outbound) that visit the network.
- NIDS (Network Intrusion Detection System)  and NIPS (Network Intrusion Prevention System) Modes - Log/drop the packets that are deemed as malicious according to the user-defined rules.

###  Intrusion Detection System (IDS)

IDS is a passive monitoring solution for detecting possible malicious activities/patterns, abnormal incidents, and policy violations.
It is responsible for generating alerts for each suspicious event. 

There are two main types of IDS systems;
- Network Intrusion Detection System (NIDS) - NIDS monitors the traffic flow from various areas of the network.
The aim is to investigate the traffic on the entire subnet. If a signature is identified, an alert is created.
- Host-based Intrusion Detection System (HIDS) - HIDS monitors the traffic flow from a single endpoint device.
The aim is to investigate the traffic on a particular device. If a signature is identified, an alert is created.

Intrusion Prevention System (IPS)
IPS is an active protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations.
It is responsible for stopping/preventing/terminating the suspicious event as soon as the detection is performed.

There are four main types of IPS systems;

- Network Intrusion Prevention System (NIPS) - NIPS monitors the traffic flow from various areas of the network.
The aim is to protect the traffic on the entire subnet. If a signature is identified, the connection is terminated.
- Behaviour-based Intrusion Prevention System (Network Behaviour Analysis - NBA) - Behaviour-based systems monitor the traffic flow from various areas of the network.
The aim is to protect the traffic on the entire subnet. If a signature is identified, the connection is terminated.

Network Behaviour Analysis System works similar to NIPS.
The difference between NIPS and Behaviour-based is; behaviour based systems require a training period (also known as "baselining") to learn the normal traffic and differentiate the malicious traffic and threats.
This model provides more efficient results against new threats.
The system is trained to know the "normal" to detect "abnormal". The training period is crucial to avoid any false positives. In case of any security breach during the training period, the results will be highly problematic.
Another critical point is to ensure that the system is well trained to recognise benign activities. 

- Wireless Intrusion Prevention System (WIPS) - WIPS monitors the traffic flow from of wireless network. The aim is to protect the wireless traffic and stop possible attacks launched from there.
If a signature is identified, the connection is terminated.
- Host-based Intrusion Prevention System (HIPS) - HIPS actively protects the traffic flow from a single endpoint device. The aim is to investigate the traffic on a particular device.
If a signature is identified, the connection is terminated.

HIPS working mechanism is similar to HIDS. The difference between them is that while HIDS creates alerts for threats, HIPS stops the threats by terminating the connection.

###  Detection/Prevention Techniques

There are three main detection and prevention techniques used in IDS and IPS solutions;
| Technique | Approach |
|---|---|
| Signature-Based | This technique relies on rules that identify the specific patterns of the known malicious behaviour. This model helps detect known threats. |
| Behaviour-Based | This technique identifies new threats with new patterns that pass through signatures. The model compares the known/normal with unknown/abnormal behaviours. |
| Policy-Based | This technique compares detected activities with system configuration and security policies. This model helps detect policy violations. |


##  Snort Usecases
| Parameter | Description |
|---|---|
| -V | provides information about your instance version. |
| -v | Verbose. Display the TCP/IP output in the console. |
| -T | testing configuration. |
| -c | identifying the configuration file. |
| -d | Display the packet data (payload). |
| -e | Display the link-layer (TCP/IP/UDP/ICMP) headers. |
| -X | Display the full packet details in HEX. |
| -i | This parameter helps to define a specific network interface to listen/sniff. |
| -l | Logger mode, target log and alert output directory. |
| -K | ASCII	Log packets in ASCII format. |
| -r | Reading option, read the dumped logs in Snort. |
| -n | Specify the number of packets that will process/read. |
| -N | Disable logging. |
| -D | Background mode. |
| -A | Alert modes(console/cmg/Full/fast/none) |
| -r / --pcap-single= |	Read a single pcap |
| --pcap-list="" | Read pcaps provided in command |
| --pcap-show	| Show pcap name on console during processing. |

The following command will show you the instance version.
- `snort -V`

Here "-T" is used for , and "-c" is .
- `sudo snort -c /etc/snort/snort.conf -T`

to sniff on the interface named "eth0"
- `sudo snort -v -i eth0`

dumping packet data mode 
- `sudo snort -d`

Snort instance in full packet dump mode
- `sudo snort -X`

Start the Snort instance in dump and link-layer header grabbing mode
- `sudo snort -de`

Snort instance in packet logger mode
- `sudo snort -dev -l /home/user/Desktop`
- `sudo snort -dev -K ASCII -l /home/user/Desktop`

Snort instance in packet reader mode 
- `sudo snort -r snort.log.1638459842 -ntc 10`

Snort instance in packet reader mode with Berkeley Packet Filters
- `sudo snort -r logname.log -X`
- `sudo snort -r logname.log icmp`
- `sudo snort -r logname.log tcp`
- `sudo snort -r logname.log 'udp and port 53'`

Investigating single PCAP
- `snort -r icmp-test.pcap`
- `sudo snort -c /etc/snort/snort.conf -q -r icmp-test.pcap -A console -n 10`

Investigate multiple pcaps
- `sudo snort -c /etc/snort/snort.conf -q --pcap-list="icmp-test.pcap http2.pcap" -A console -n 10`
- `sudo snort -c /etc/snort/snort.conf -q --pcap-list="icmp-test.pcap http2.pcap" -A console --pcap-show`
- ``

###  ﻿Snort in IDS/IPS Mode
Capabilities of Snort are not limited to sniffing and logging the traffic. IDS/IPS mode helps you manage the traffic according to user-defined rules. (N)IDS/IPS mode depends on the rules and configuration.

Snort ICMP Rule Example:
- `alert icmp any any <> any any  (msg: "ICMP Packet Found"; sid: 100001; rev:1;)`

This rule is located in "/etc/snort/rules/local.rules".

Snort instance and disable logging
- `sudo snort -c /etc/snort/snort.conf -N`

Snort instance in background mode 
- `sudo snort -c /etc/snort/snort.conf -D`

Snort instance in console alert mode (console)
- `sudo snort -c /etc/snort/snort.conf -A console`
- `sudo snort -c /etc/snort/rules/local.rules -A console`

Snort instance in cmg alert mode
- `sudo snort -c /etc/snort/snort.conf -A cmg`

Snort instance in fast alert mode
- `sudo snort -c /etc/snort/snort.conf -A fast`

Snort instance in full alert mode
- `sudo snort -c /etc/snort/snort.conf -A full`

Snort instance in none alert mode
- `sudo snort -c /etc/snort/snort.conf -A none`

##  Snort Detection Rules

Detecting TCP port 80 for both inbound and outbound HTTP traffic
```
alert tcp any 80 <> any any (msg:"TCP port 80 inbound traffic detected";sid:1000000000001; rev :1)
alert tcp any any <> any 80 (msg:"TCP port 80 outbound traffic detected";sid:1000000000002; rev :1)
alert tcp any 80,443 -> any any (msg: "HTTPX Packet Found"; sid:1000002; rev:1;)
```

Detecting TCP port 21 for both inbound and outbound FTP traffic
```
alert tcp any 21 <> any any (msg:"Outbound ftp traffic detected";sid:1000000000003; rev :1)
alert tcp any any <> any 21 (msg:"Inbound ftp traffic detected";sid:1000000000004; rev :1)
alert tcp any any <> any 21 (msg:"Failed ftp login attempt";content:"530";sid:1000000000005; rev :1)
alert tcp any any <> any 21 (msg:"Successful ftp login";content:"230";sid:1000000000006; rev :1)
alert tcp any any <> any 21 (msg:"Invalid Password";content:"331";sid:1000000000007; rev :1)
alert tcp any any <> any 21 (msg:"Invalid Admin Password";content:"331";content:"Administrator";sid:1000000000008; rev :1)
```

Detecting PNG file and GIF file in traffic
- `alert tcp any any -> any any (msg:"PNG File Detected"; content:"|89 50 4E 47 0D 0A 1A 0A|"; depth:8;sid:10000000009)`
- `alert tcp any any -> any any (msg:"GIF File Detected"; content:"GIF89a"; depth:6;sid:10000000010)`

Detecting Torrent file in traffic
- `alert tcp any any -> any any (msg:"Torrent File Detected"; content:".torrent"; nocase;sid:10000000011)`

Detecting ICMP packet in traffic
- `alert icmp any any -> any any (msg: "ICMP Packet Found"; sid:1000001; rev:1;)`

Detecting payload size in traffic
- `alert tcp any any -> any any (msg: "Packet payload size between 770 and 855 bytes detected"; dsize: 770<>855; sid: 1000001;)`

Detecting and Droping ssh connection in taffic
- `drop tcp any 22 <> any any (msg:"SSH Connection attempted"; sid:100001; rev:1;)`

## Conclusion 

In this module, Intrusion Detection/Prevention System investigating with snort pratical are leared. Do more Practice and Expert it!. <br>
**6/22/2024** <br>
Contributed By - Jord@n
