#  Wireshark

##  Packet Filtering

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

###  IP Filters

| Filter | Description |
|---|---|
| ip | Show all IP packets. |
| ip.addr == 10.10.10.111 | Show all packets containing IP address 10.10.10.111. |
| ip.addr == 10.10.10.0/24 | Show all packets containing IP addresses from 10.10.10.0/24 subnet. |
| ip.src == 10.10.10.111 | Show all packets originated from 10.10.10.111 |
| ip.dst == 10.10.10.111 | Show all packets sent to 10.10.10.111 |

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

###  Application Level Protocol Filters

| Filter | Description |
|---|---|
| http | Show all HTTP packets |
| dns | Show all DNS packets |
| http.response.code == 200 | Show all packets with HTTP response code "200" |
| dns.flags.response == 0 | Show all DNS requests |
| http.request.method == "GET" | Show all HTTP GET requests	|
| dns.flags.response == 1 | Show all DNS responses |
| http.request.method == "POST" | Show all HTTP POST requests	|
| dns.qry.type == 1 | Show all DNS "A" records |
