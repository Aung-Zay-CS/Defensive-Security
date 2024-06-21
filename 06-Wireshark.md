#  Traffic Monitoring
Network traffic monitoring involves the process of capturing and analyzing data packets flowing through a computer network.
Effective network traffic monitoring requires balancing between capturing sufficient data for analysis and managing the overhead of monitoring tools on network performance. It plays a critical role in maintaining network security, optimizing performance, and ensuring the reliability of network operations in organizations of all sizes.

#  Wireshark
Wireshark is a powerful network protocol analyzer that allows you to capture and analyze network traffic in real-time. 
Wireshark can capture live packet data from a network interface or read packets from a previously saved capture file. 
It supports a wide range of network protocols and can capture packets on Ethernet, Wi-Fi, Bluetooth, USB, and other network interfaces.

##  Packet Filtering
Once captured, Wireshark provides detailed packet inspection capabilities. It allows you to view packet headers and payloads, dissect protocols, and analyze packet timing and sequence. Wireshark offers powerful filtering and search functionalities. You can apply display filters to focus on specific packets (e.g., by protocol, IP address, port number) and use search tools to find packets containing specific data or patterns.


###  Comparison Operators

| English | C-Like |	Description |	Example |
|---|---|---|---|
| eq	| ==	| Equal	| ip.src == 10.10.10.100 |
| ne	| !=	| Not equal	| ip.src != 10.10.10.100 |
| gt	| >	 | Greater than	ip.ttl > 250 |
| lt	| <	 | Less Than | ip.ttl < 10 |
| ge	| >= | Greater than or equal to | ip.ttl >= 0xFA |
| le	| <= | Less than or equal to | ip.ttl <= 0xA |

###  Logical Expressions

| English | C-Like |	Description |	Example |
|---|---|---|---|
| and |	&& | Logical AND | (ip.src == 10.10.10.100) AND (ip.src == 10.10.10.111) |
| or	| II | Logical OR	| (ip.src == 10.10.10.100) OR (ip.src == 10.10.10.111) |
| not	| !	| Logical NOT	| !(ip.src == 10.10.10.222) |

##  Protocol Filters
Wireshark supports 3000 protocols and allows packet-level investigation by filtering the protocol fields.
This task shows the creation and usage of filters against different protocol fields. 

###  ICMP/IP Filters

| Filter | Description |
|---|---|
| ip | Show all IP packets. |
| ip.addr == 10.10.10.111 | Show all packets containing IP address 10.10.10.111. |
| ip.addr == 10.10.10.0/24 | Show all packets containing IP addresses from 10.10.10.0/24 subnet. |
| ip.src == 10.10.10.111 | Show all packets originated from 10.10.10.111 |
| ip.dst == 10.10.10.111 | Show all packets sent to 10.10.10.111 |
| icmp | global search |
| data.len > 64 and icmp | Packet length |


###  ARP Filters

| Filter | Description |
|---|---|
| arp | Global search |
| arp.opcode == 1 | Opcode 1: ARP requests. |
| arp.opcode == 2 | Opcode 2: ARP responses. |
| arp.dst.hw_mac==00:00:00:00:00:00 | Hunt: Arp scanning |
| arp.duplicate-address-detected or arp.duplicate-address-frame | Hunt: Possible ARP poisoning detection |
| ((arp) && (arp.opcode == 1)) && (arp.src.hw_mac == target-mac-address) | Hunt: Possible ARP flooding from detection |


###  TCP and UDP Filters

| Filter | Description |
|---|---|
| tcp.port == 80 | Show all TCP packets with port 80 |
| udp.port == 53 | Show all UDP packets with port 53 |
| tcp.srcport == 1234 | Show all TCP packets originating from port 1234	|
| udp.srcport == 1234 | Show all UDP packets originating from port 1234 |
| tcp.dstport == 80 | Show all TCP packets sent to port 80 |
| udp.dstport == 5353 | Show all UDP packets sent to port 5353 |
| udp.dstport in {55 .. 70} | port range filter |
| tcp.flags == 2 | Only TCP SYN flag. |
| tcp.flags == 16 | Only ACK flag. |
| tcp.flags == 18 | Only SYN, ACK flags. |
| tcp.flags == 4 | Only RST flag. |
| tcp.flags == 20 | Only RST, ACK flags. |
| tcp.flags == 1 | Only FIN flags. |

TCP Connect Scans
- ` tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024 `

UDP Scans
- `icmp.type==3 and icmp.code==3`

###  NetBIOS Filters
| Filter | Description |
|---|---|
| nbns | Global search.	|
| nbns.name contains "keyword" | "name, Time to live (TTL) and IP address details" |


###  Application Level Protocol Filters

| Filter | Description |
|---|---|
| dns | Show all DNS packets |
| dns.flags.response == 0 | Show all DNS requests |
| dns.flags.response == 1 | Show all DNS responses |
| dns.qry.type == 1 | Show all DNS "A" records |
| dns contains "dnscat" | Known patterns like dnscat and dns2tcp |
| dns.qry.name.len > 15 and !mdns | Anomalous and non-regular names in DNS addresses. |
| dhcp or bootp | Filtering the proper DHCP packet |
| dhcp.option.dhcp == 3 | "DHCP Request" packets  |
| dhcp.option.dhcp == 5 | "DHCP ACK" packets |
| dhcp.option.dhcp == 6 | "DHCP NAK" packets represent denied requests |
| dhcp.option.hostname contains "keyword" | "DHCP Request" options for grabbing information |
| dhcp.option.domain_name contains "keyword" | "DHCP Request" options for grabbing information|
| kerberos.CNameString contains "keyword" | User account search |
| kerberos.CNameString and !(kerberos.CNameString contains "$" ) | User account search |
| kerberos | Global search.	|
| kerberos.pvno == 5 | Protocol version. |
| kerberos.realm contains ".org" | Domain name for the generated ticket. |
| kerberos.SNameString == "krbtg" | Service and domain name for the generated ticket. |

##  Cleartext Protocol Analysis
Investigating cleartext protocol traces sounds easy, but when the time comes to investigate a big network trace for incident analysis and response, the game changes. Proper analysis is more than following the stream and reading the cleartext data. For a security analyst, it is important to create statistics and key results from the investigation process.


###  FTP Analysis
File Transfer Protocol (FTP) is designed to transfer files with ease, so it focuses on simplicity rather than security.
As a result of this, using this protocol in unsecured environments could create security issues like:

- MITM attacks
- Credential stealing and unauthorised access
- Phishing
- Malware planting
- Data exfiltration

| Filter | Description |
|---|---|
| ftp | show all ftp traffic |
| ftp.response.code == 211 | 211/212/213 |
| ftp.response.code == 227 | 220/227/228/229 |
| ftp.response.code == 230 | 230/231/331/430/530/ |
| ftp.request.command == "USER" | |
| ftp.request.command == "PASS" | "FTP" commands |
| ftp.request.arg == "password" | |

Bruteforce signal: List failed login attempts.
- `ftp.response.code == 530`
Bruteforce signal: List target username.
- `(ftp.response.code == 530) and (ftp.response.arg contains "username")`
Password spray signal: List targets for a static password.
- `(ftp.request.command == "PASS" ) and (ftp.request.arg == "password")`


###  HTTP Analysis 
Hypertext Transfer Protocol (HTTP) is a cleartext-based, request-response and client-server protocol. It is the standard type of network activity to request/serve web pages, and by default, it is not blocked by any network perimeter. As a result of being unencrypted and the backbone of web traffic, HTTP is one of the must-to-know protocols in traffic analysis. Following attacks could be detected with the help of HTTP analysis:

- Phishing pages
- Web attacks
- Data exfiltration
- Command and control traffic (C2)

| Filter | Description |
|---|---|
| http | Show all HTTP packets |
| http.request.method == "POST" | Show all HTTP POST requests	|
| http.request.method == "GET" | Show all HTTP GET requests	|
| http.response.code == 200 | Show all packets with HTTP response code "200" |
| http.request | Listing all request |
| http.response.code == 200 | 2xx/3xx/4xx/5xx |
| http.user_agent | global search for user agent |
| http.user_agent contains "nmap" | User agent: Browser and operating system identification |
| http.server contains "apache" | Server: Server service name. |
| http.host contains "keyword" | Hostname of the server |
| http.request.uri contains "admin" | Points the requested resource from the server. |
| http.request.full_uri contains "admin | Full *URI: Complete URI information. |
| http.connection == "Keep-Alive" | Connection status. |

# Conclusion 

In this module, Traffic Monitoring and investigating with wireshark pratical are leared. Do more Practice and Expert it!. <br>
**6/19/2024** <br>
Contributed By - Jord@n
