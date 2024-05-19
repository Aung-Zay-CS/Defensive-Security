#  Windows Firewall
Windows Defender Firewall is a built-in feature of Microsoft Windows operating systems.
It acts as a barrier between your computer and the internet, monitoring and controlling incoming and outgoing network traffic based on an organization's predefined rules.
Its primary function is to protect your computer from unauthorized access or malicious activity by filtering network traffic.
It can block certain applications from accessing the internet, prevent unauthorized access to your computer from external sources,
and help keep your system secure from various network-based threats such as hackers, viruses, and malware.
Windows Defender Firewall is designed to be user-friendly, with basic settings suitable for most users and
advanced settings available for more experienced users or IT administrators who need finer control over network traffic.

##  Inbound rules & Outbound rules
Outbound rules and inbound rules are two fundamental components of Windows Defender Firewall (or any firewall, for that matter) that govern how network traffic is controlled.

Inbound Rules: These rules control the incoming network traffic to your computer. They specify what kind of connections or traffic are allowed to reach your computer from the network or the internet.
For example, you might have an inbound rule that allows incoming traffic on port 80 (HTTP) to reach your web server. Inbound rules are crucial for managing what services and applications can accept incoming connections.

Outbound Rules: On the other hand, outbound rules govern the outgoing network traffic from your computer. They specify what kind of connections or traffic are allowed to leave your computer and reach the network or the internet.
For example, you might have an outbound rule that allows your web browser to connect to external web servers on port 443 (HTTPS). Outbound rules help control which applications are allowed to communicate with the outside world.

Both inbound and outbound rules are essential for maintaining security and controlling network traffic on your computer.
By configuring these rules, you can ensure that only authorized traffic is allowed in and out of your system, thereby reducing the risk of unauthorized access, malware infections, and other security threats.


##  Profiles
Profiles: Windows Defender Firewall supports multiple network profiles, including Domain, Private, and Public.
Each profile has its own set of firewall settings, allowing you to customize rules based on the network location your device is connected to.
For example, you might have more relaxed rules for your home network (Private profile) compared to a public Wi-Fi network (Public profile).

###  Lab one steps
Blocking ICMP Protocol

- first call run box and type `firewall.cpl` to navigate to firewall menu & click on advanced setting.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/54359c21-0667-4f4c-92e6-08e089a4af6f" width="450px" height="300px"><br>Figure (1) </p>

- right click on Inbound rule and click new rule to add rule.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/a9e8b2b7-49c5-4e37-903d-08a249c68e94" width="450px" height="300px"><br>Figure (2) </p>

- select custom to add custom rules.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/d0aa5e03-57eb-4694-85d5-82fc97136555" width="450px" height="300px"><br>Figure (3) </p>

- to apply all programs and choose all programs.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/f138acf0-82dc-4fd4-addd-ea35b2d83153" width="450px" height="300px"><br>Figure (4) </p>

- choose ICMPv4 protocol and apply settings as shown in figure.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/4b394e36-d4c4-496a-a351-6273b7901e8b" width="450px" height="300px"><br>Figure (5) </p>

- we will block every incoming ip addresses & outcoming addresses. 
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/8e5bd30f-9e90-406f-afb0-676ae8f26fa5" width="450px" height="300px"><br>Figure (6) </p>

- action is to block the connection & select block connection option.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/73b46264-7f11-47cd-bdcb-b5fb3068bf66" width="450px" height="300px"><br>Figure (7) </p>

- We will apply this rule to all network profile.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/5ac7366a-7f4c-4691-b298-b6082c1a0499" width="450px" height="300px"><br>Figure (8) </p>

- We can name this rule.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/253589ee-66cd-4b49-a1f4-7fdeb04716b1" width="450px" height="300px"><br>Figure (9) </p>

- right click on recent rule name and enable rule. 
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/f5164906-c05f-4035-86a0-b7fc18ff4d38" width="450px" height="300px"><br>Figure (10) </p>

- ping from another machine and you will don't get reply.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/d1a1590f-bbe5-41ed-ae00-be241190d196" width="450px" height="300px"><br>Figure (11) </p>

###  Lab two 
Blocking firefox from internet.

- first call run box and type `firewall.cpl` & click on advanced settings and click on outbound rule.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/d5ef80a3-ff1c-4ce8-a4b3-1a688f83ccdc" width="450px" height="300px"><br>Figure (12) </p>

- choose on this program path and navigate the location of the firefox.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/3b8916c8-fc66-41bd-938a-1923805a0539" width="450px" height="300px"><br>Figure (13) </p>

- choose block the connection to block.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/9b03e3a3-2a82-4372-ba6f-16fab9b03b67" width="450px" height="300px"><br>Figure (14) </p>

- apply this rule to all profiles.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/9a3e15d7-e972-41d6-b28e-9b3b66e939ee" width="450px" height="300px"><br>Figure (15) </p>

- name this rule.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/c0a6f8ab-0891-4e62-bacf-916f7972da81" width="450px" height="300px"><br>Figure (16) </p>

- firefox cann't connect to internet.
<p align="center"><img src="https://github.com/AungZayMyo/Defensive-Security/assets/154745254/313a2071-63ec-436b-a84f-de69ece14daa" width="450px" height="300px"><br>Figure (17) </p>

## Conclusion 

In this tutorial, Windows Defender firewall features and labs are demostrated. Do more Practice and Expert it!. <br>
**5/19/2024** <br>
Contributed By - Jord@n
