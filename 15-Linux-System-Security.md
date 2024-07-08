#  Linux System hardening
Linux systems provide a reliable and robust alternative to closed-source systems, such as MS Windows Server and UNIX.
Of course, we cannot claim that Linux is always the best choice; however, Linux is the best choice for many scenarios. Before using this option, we must focus on securing our Linux systems, also known as Linux hardening.

##  Physical Security
One of the security principles is Defence-in-Depth. Hence, we should always think in terms of layers of security. One of the first layers is physical security.
Let’s say you have taken the necessary measures to prevent intruders from taking the disk drive or the whole computer system.
Moreover, you have ensured that your system passwords are complex and impossible to guess.
If an intruder can access the system physically, it is a non-sophisticated task to use GRUB, a popular Linux bootloader, to reset the root password account.
Hence we have the adage “boot access = root access”.

It is evident that we need to ensure physical security for our computer systems; however, in the unlikely event that physical security is breached, we need to provide additional layers of protection.
Many BIOS and UEFI firmware allows you to add a boot password. This password will prevent unauthorised users from booting the system.
However, this can only be used for personal systems; it won’t make sense to use it on servers as this will require someone to be physically present to supply the boot password.

We can consider adding a GRUB password depending on the Linux system we want to protect. Many tools help achieve that.
One tool is grub2-mkpasswd-pbkdf2, which prompts you to input your password twice and generates a hash for you.
The resulting hash should be added to the appropriate configuration file depending on the Linux distribution (examples: Fedora and Ubuntu).
This configuration would prevent unauthorised users from resetting your root password.
It will require the user to supply a password to access advanced boot configurations via GRUB, including logging in with root access.

###  grub2-mkpasswd-pbkdf2
Password-Based Key Derivation Function 2 (grub2-mkpasswd-pbkdf2) is a command-line tool used in Linux systems, particularly with GRUB 2 (Grand Unified Bootloader version 2), which is the bootloader used by most Linux distributions.

Its primary purpose is to generate hashed passwords using the PBKDF2 (Password-Based Key Derivation Function 2) algorithm.
This tool is typically used to secure GRUB bootloader configurations by encrypting passwords stored in configuration files (like /etc/grub.d/00_header or /boot/grub/grub.cfg). 
Which can help prevent unauthorized access or modification of bootloader settings.

Here’s a brief overview of how grub2-mkpasswd-pbkdf2 works:
- Generate a hashed password: When you run grub2-mkpasswd-pbkdf2, you provide it with a plaintext password. It then uses the PBKDF2 algorithm to generate a hashed representation of this password.
- Store hashed password: The hashed password can be copied and pasted into the GRUB configuration file (like grub.cfg). This hashed password is stored securely and can be used by GRUB during boot to authenticate users who need to access GRUB commands or change boot options.
- Security: Using PBKDF2 ensures that even if an attacker gains access to the configuration file, they won't immediately see the plaintext password. PBKDF2 is designed to be computationally intensive, making brute-force attacks on the hashed password more difficult.
- Usage: After generating the hashed password, you typically need to edit the GRUB configuration file (/boot/grub/grub.cfg) to specify where and how GRUB should use this password for authentication.

```
$ grub2-mkpasswd-pbkdf2
Enter password:
Reenter password:
PBKDF2 hash of your password is grub.pbkdf2.sha512.10000.[hash]
```

##  Firewall
A firewall decides which packets can enter a system and which packets can leave a system. For more information about firewalls, we recommend you check the Firewalls room. Without a firewall, a client can communicate with any server without restrictions; moreover, a client can function as a server and listen for incoming connections from other clients. In other words, if an attacker manages to exploit a vulnerability on a system without a firewall in place, the attacker could use the exploit to listen on a chosen port number on the victim’s machine and connect to it without any restrictions.

A host-based firewall is a piece of software installed on a system we want to protect. Unlike a network-based firewall, the host-based firewall restricts network packets to and from a single host. 

The firewall has two main functions:

What can enter? Allow or deny packets from entering a system.
What can leave? Allow or deny packets from leaving a system.

###  Firewall Policy
Before configuring a firewall, you need to decide upon the firewall policy. You might be the decision maker regarding the firewall policy or an enforcer of an existing security policy that covers firewall configuration. It all depends on the system you are protecting.

We will not go into security policies as this is outside the scope of this room. We will mention that the two main approaches are:
- Block everything and allow certain exceptions.
- Allow everything and block certain exceptions.

Each of the above two approaches has its advantages and disadvantages. Blocking everything with a limited set of exceptions would provide tighter and better security; however, it might cause inconvenience to the users depending on the situation.

###  Linux Firewalls
The first Linux firewall was a packet filtering firewall, i.e., a stateless firewall. A stateless firewall can inspect certain fields in the IP and TCP/UDP headers to decide upon a packet but does not maintain information about ongoing TCP connections. As a result, a packet can manipulate a few TCP flags to appear as if it is part of an ongoing connection and evade certain restrictions. Current Linux firewalls are stateful firewalls; they keep track of ongoing connections and restrict packets based on specific fields in the IP and TCP/UDP headers and based on whether the packet is part of an ongoing connection.

The IP header fields that find their way into the firewall rules are:
- Source IP address
- Destination IP address

The TCP/UDP header fields that are of primary concern for firewall rules are:
- Source TCP/UDP port
- Destination TCP/UDP port

It is worth noting that it is impossible to allow and deny packets based on the process but instead on the port number. If you want the web browser to access the web, you must allow the respective ports, such as ports 80 and 443. This limitation differs from MS Windows’ built-in firewall, which can restrict and allow traffic per application.

On a Linux system, a solution such as SELinux or AppArmor can be used for more granular control over processes and their network access. For example, we can allow only the /usr/bin/apache2 binary to use ports 80 and 443 while preventing any other binary from doing so on the underlying system. Both tools enforce access control policies based on the specific process or binary, providing a more comprehensive way to secure a Linux system.

###  Netfilter
At the very core, we have netfilter. The netfilter project provides packet-filtering software for the Linux kernel 2.4.x and later versions. The netfilter hooks require a front-end such as iptables or nftables to manage.

###  iptables
As a front-end, iptables provides the user-space command line tools to configure the packet filtering rule set using the netfilter hooks.

For filtering the traffic, iptables has the following default chains:

- Input: This chain applies to the packets incoming to the firewall.
- Output: This chain applies to the packets outgoing from the firewall.
- Forward This chain applies to the packets routed through the system.

###  nftables
nftables is supported in Kernel 3.13 and later, adding various improvements over iptables, particularly in scalability and performance.
We will create a simple nftables configuration that allows traffic to our local SSH server.
Unlike iptables, nftables start with no tables or chains. We need to add the necessary tables and chains before adding rules. To begin, we will create a table, fwfilter.

###  UFW
After this overview of iptables and nftables, you might have started to develop the impression that configuring firewalls on Linux is a cumbersome, error-prone process. We already mentioned that iptables is like a front-end to netfilter; however, we can simplify things by providing a front-end to the front-end!

Example front-ends to iptables are shown in the figure below and can be divided into:

Command-line Interface (CLI) front-ends, such as firewalld and ufw
Graphical User Interface (GUI) front-ends, such as fwbuilder

##  Remote Access
Providing remote access to a system is a very convenient way to access your system and files when you are not physically present at the target system’s keyboard. However, this also means that you are voluntarily providing a service that attackers will target. Common attacks include:
- Password sniffing
- Password guessing and brute-forcing
- Exploiting the listening service

###  Protecting Against Password Sniffing
Remote access can be achieved through many different protocols and services. Although all modern systems use encrypted protocols, such as the SSH protocol, for remote access, older systems might still use cleartext protocols, such as the Telnet protocol. It is crucial to ensure that you select a protocol that encrypts traffic. The SSH protocol has been around for more than two decades. It has stood the test of time. It has many uses ranging from secure remote access to secure file transfers.

###  Protecting Against Password Guessing
When you set up your Linux system with SSH for remote administration, you also make your Linux box available for all interested parties. Many malicious hackers search the Internet for listening SSH servers and start to guess the login credentials; usually, they try root with the most common passwords. Because your SSH server will be configured to listen for incoming connections 24 hours a day, 365 days a year, evil users have all the time in the world to attempt one password after another.

There are a few guidelines that you can use:

- Disable remote login as root; force login as non-root users.
- Disable password authentication; force public key authentication instead.

It would be best to rely on public key authentication with SSH to help improve the security of the remote login system and make it as fail-proof as possible.
The reasoning behind the above guidelines is that you don’t want the adversary to be able to attack the root account directly. Moreover, even if it is a non-root account, you don’t want the attacker to gain access if there is a weakness in the password.

##  Securing User Account
The root account carries with it tremendous power and hence risk. You are at risk of rendering your system unbootable with a simple mistake. Using a non-root account for everyday work is recommended to avoid sabotaging your system. However, root privileges are still needed for system maintenance, installing/removing software packages, and updating/configuring the system.

###  Use sudo
To avoid logging in as root, the better approach would be to have an account created for administrative purposes added to the sudoers, i.e. group who can use the sudo command. sudo stands for Super User Do and it should precede any command that requires root privileges.

###  Disable root
Once you have created an account for administrative purposes and added it to the sudo/wheel group, you might consider disabling the root account. A straightforward way is to modify the /etc/passwd and change the root shell to /sbin/nologin. In other words, edit /etc/passwd and change the line root:x:0:0:root:/root:/bin/bash to root:x:0:0:root:/root:/sbin/nologin.

###  Enforce a Strong Password Policy
The libpwquality library provides many options for password constraints. The configuration file can be found at:
- `/etc/security/pwquality.conf` on RedHat and Fedora
- `/etc/pam.d/common-password` on Debian and Ubuntu. You can install it using apt-get install libpam-pwquality

Here are a few example options:
- `difok` allows you to specify the number of characters in the new password that were not present in the old password.
- `minlen` sets the minimum allowed length for new passwords.
- `minclass` specifies the minimum number of required classes of characters; a class can be uppercase, lowercase, and digits, among others.
- `badwords` provides a space-separated list of words that must not be contained in the chosen password.
- `retry=N` prompts the user N times before returning an error.

###  Disable Unused Accounts
As part of system maintenance, it is vital to disable user accounts that no longer need access to the system in question. For instance, these users might have moved to another department or quit the company.

You can disable a user account in the same way we would disable the root account. An easy way would be to edit the /etc/passwd file and set the shell of the user account we want to disable to /sbin/nologin.

Let’s say that we want to disable the account of the user Michael with username michael.
- `Enabled account: michael:x:1000:1000:Michael:/home/michael:/usr/bin/fish`
- `Disabled account: michael:x:1000:1000:Michael:/home/michael:/sbin/nologin`

We should do the same for local services. In other words, we should set the shell to sbin/nologin for all the local service accounts such as www-data, mongo, and nginx, to name a few. The reason is that these services need accounts to run on the system but would never need to log in and access a shell. Any of these services could perhaps have an RCE (Remote Code Execution) vulnerability, and by setting the shell to nologin, we can at least prevent interactive logins for the account of the affected service.

##  Software and Services
Every piece of software you install on your system also increases the number of potential vulnerabilities. In other words, installing additional software packages and new services increases the vulnerabilities an attacker can exploit to gain access to your system and, eventually, to other systems on your network. You can follow some guidelines to help you reduce the attack surface.

###  Disable Unnecessary Services
One of the easiest ways to improve your security posture is by removing or disabling unneeded services and packages. In simple terms, we need to minimise the number of installed system packages as every package carries some risk, and we cannot know when a related vulnerability will be discovered. The best policy is to avoid installing unneeded packages.

For example, if you don’t need a web server, you should ensure you don’t install one. If you needed to run a web server at one point but no longer need it now, you should remove it or at least disable it. Otherwise, you will be exposing yourself to unnecessary risk.

###  Block Unneeded Network Ports
After you remove any packages that are not required and disable preinstalled services that might not be removed, it is critical to set your firewall rules accordingly. If you don’t have a web server, there is no reason to allow packets to TCP ports 80 and 443. The reasoning behind this is that if the attacker manages to start a disabled service, the firewall will block its traffic, and the attacker won’t be able to access its TCP port(s).

###  Avoid Legacy Protocols
At one point in the past, Telnet was the primary protocol to remote access a system; the TFTP protocol was commonly used to transfer files. Such protocols should no longer be allowed as secure alternatives have been released.

Instead of Telnet, the SSH protocol is now widely available. For example, the Secure File Transfer Protocol (SFTP) protocol provides a great alternative to the TFTP protocol. The critical point is that a secure alternative is selected and used.

###  Remove Identification Strings
Whenever you connect to a remote server, it usually replies with its version number. This information would reveal various information to the attacker, such as the name of the server/program, the version number, and the host operating system.

##  Update and Upgrade Policies
It is vital that you keep your system updated with the latest security patches and bug fixes.

You can update a Debian-based distribution, such as Ubuntu, with the following two commands:
- apt update to download package information from the configured sources
- apt upgrade to install available upgrades for all packages from the configured sources

You can update a RedHat or Fedora system using the following:
- dnf update on newer releases (Red Hat Enterprise Linux 8 and later)
- yum update on older releases (Red Hat Enterprise Linux 7 and earlier)

Since we are talking about production systems, we need to select distributions that will continue to receive updates smoothly for many years.

###  Ubuntu LTS Releases
For example, Ubuntu releases a Long Term Support (LTS) version every two years. LTS releases have an even version number (indicating the year) with 04 (for April), such as 18.04, 20.04, and 22.04. An LTS version will grant you five years of security updates for the base OS without a subscription and another five years if you pay for Extended Security Maintenance (ESM).

###  RedHat Releases
RedHat Enterprise Linux 8 and 9 offer 12 years of support in three phases:
- Full Support for five years
- Maintenance Support for five years
- Extended Life Phase for two years

For example, Red Hat Enterprise Linux 9 was released on May 18, 2022. It can benefit from updates as follows:
- Full support till May 31, 2027
- Maintenance support till May 31, 2032

For more details, check Red Hat Enterprise Linux Life Cycle.

###  Kernel Updates
Updating the system should not be limited to the installed software; it should consider updating the kernel. For instance, in 2016, a security vulnerability that affects the Linux kernel was discovered. It allows an attacker to gain root access to a system by exploiting a race condition in the copy-on-write (COW) mechanism, giving it the name “Dirty COW.” The vulnerability is present in all Linux kernel versions from 2.6.22 onwards. It has been patched in most major Linux distributions, but it is still a threat to systems that have not been updated. Because Dirty COW is a severe vulnerability that can allow attackers to gain root access to Linux systems, it is crucial to keep your system, including its kernel, up-to-date with the latest security patches to reduce the risk of exploitation.

###  Automatic Updates
Now that you have a Linux system with security updates throughout its life, we must ensure that the updates are properly installed, and security fixes are applied.
Stay updated with security news in case of a vulnerability that affects your systems is disclosed.
Depending on the Linux distribution that you are using, consider configuring automatic updates. Automating updates on Linux distributions that prioritize stability over cutting-edge technology would be safe.

##  Audit and Log Configuration
Most log files on Linux systems are stored in the /var/log directory. Here are a few of the logs that can be referenced when looking into threats:

- `/var/log/messages` - a general log for Linux systems
- `/var/log/auth.log` - a log file that lists all authentication attempts (Debian-based systems)
- `/var/log/secure` - a log file that lists all authentication attempts (Red Hat and Fedora-based systems)
- `/var/log/utmp` - an access log that contains information regarding users that are currently logged into the system
- `/var/log/wtmp` - an access log that contains information for all users that have logged in and out of the system
- `/var/log/kern.log` - a log file containing messages from the kernel
- `/var/log/boot.log` - a log file that contains start-up messages and boot information

## Conclusion 

In this module, Linux system hardening techniques are learned. Do more Practice and Expert it!. <br>
**7/8/2024** <br>
Contributed By - Jord@n
