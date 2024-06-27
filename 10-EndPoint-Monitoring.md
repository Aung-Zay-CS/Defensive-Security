#
##
###  Sysmon
Sysmon, a tool used to monitor and log events on Windows, is commonly used by enterprises as part of their monitoring and logging solutions.
Part of the Windows Sysinternals package, Sysmon is similar to Windows Event Logs with further detail and granular control.

From the Microsoft Docs, "System Monitor (Sysmon) is a Windows system service and device driver that, once installed on a system, remains resident across system reboots to monitor and log system activity to the Windows event log.
It provides detailed information about process creations, network connections, and changes to file creation time.
By collecting the events it generates using Windows Event Collection or SIEM agents and subsequently analyzing them, you can identify malicious or anomalous activity and understand how intruders and malware operate on your network."

Sysmon gathers detailed and high-quality logs as well as event tracing that assists in identifying anomalies in your environment.
Sysmon is most commonly used in conjunction with security information and event management (SIEM) system or other log parsing solutions that aggregate, filter, and visualize events.
When installed on an endpoint, Sysmon will start early in the Windows boot process. In an ideal scenario, the events would be forwarded to a SIEM for further analysis.

###  Sysmon Event IDs

- Event ID 1 - Process Creation
```
<RuleGroup name="" groupRelation="or">
	<ProcessCreate onmatch="exclude">
	 	<CommandLine condition="is">C:\Windows\system32\svchost.exe -k appmodel -p -s camsvc</CommandLine>
	</ProcessCreate>
</RuleGroup>
```

- Event ID 3: Network Connection
```
<RuleGroup name="" groupRelation="or">
	<NetworkConnect onmatch="include">
	 	<Image condition="image">nmap.exe</Image>
	 	<DestinationPort name="Alert,Metasploit" condition="is">4444</DestinationPort>
	</NetworkConnect>
</RuleGroup>
```

- Event ID 7: Image Loaded
```
<RuleGroup name="" groupRelation="or">
	<ImageLoad onmatch="include">
	 	<ImageLoaded condition="contains">\Temp\</ImageLoaded>
	</ImageLoad>
</RuleGroup>
```

- Event ID 8: CreateRemoteThread
```
<RuleGroup name="" groupRelation="or">
	<CreateRemoteThread onmatch="include">
	 	<StartAddress name="Alert,Cobalt Strike" condition="end with">0B80</StartAddress>
	 	<SourceImage condition="contains">\</SourceImage>
	</CreateRemoteThread>
</RuleGroup>
```

- Event ID 11: File Created
```
<RuleGroup name="" groupRelation="or">
	<FileCreate onmatch="include">
	 	<TargetFilename name="Alert,Ransomware" condition="contains">HELP_TO_SAVE_FILES</TargetFilename>
	</FileCreate>
</RuleGroup>
```

- Event ID 12 / 13 / 14: Registry Event
```
<RuleGroup name="" groupRelation="or">
	<RegistryEvent onmatch="include">
	 	<TargetObject name="T1484" condition="contains">Windows\System\Scripts</TargetObject>
	</RegistryEvent>
</RuleGroup
```

- Event ID 15: FileCreateStreamHash
```
<RuleGroup name="" groupRelation="or">
	<FileCreateStreamHash onmatch="include">
	 	<TargetFilename condition="end with">.hta</TargetFilename>
	</FileCreateStreamHash>
</RuleGroup> 
```

- Event ID 22: DNS Event
```
<RuleGroup name="" groupRelation="or">
	<DnsQuery onmatch="exclude">
	 	<QueryName condition="end with">.microsoft.com</QueryName>
	</DnsQuery>
</RuleGroup>
```

###  Installing Sysmon
The installation for Sysmon is fairly straightforward and only requires downloading the binary from the Microsoft website. You can also download all of the Sysinternals tools with a PowerShell command.

PowerShell command: `Download-SysInternalsTools C:\Sysinternals`

To start Sysmon you will want to open a new PowerShell or Command Prompt as an Administrator.
- Command Used: `Sysmon.exe -accepteula -i ..\Configuration\swift.xml`


##  Osquery
Osquery is an open-source agent created by Facebook in 2014. It converts the operating system into a relational database. It allows us to ask questions from the tables using SQL queries, like returning the list of running processes, a user account created on the host, and the process of communicating with certain suspicious domains. It is widely used by Security Analysts, Incident Responders, Threat Hunters, etc. Osquery can be installed on multiple platforms: Windows, Linux, macOS, and FreeBSD.

| Commands | Description |
|---|---|
| .tables | list all the available tables |
| .tables user | list all the tables with the term |
| .schema tablen_name | list a table's schema |
| select | to query select |
| = | equal |
| <> | not equal |
| >, >= | greater than, greater than, or equal to |
| <, <= | less than or less than or equal to |
| BETWEEN | between a range |
| LIKE | pattern wildcard searches |
| % | wildcard, multiple characters |
| _ | wildcard, one character |

###  Example Queries

Exploring Users information
- `select p.pid, p.name, p.path, u.username from processes p JOIN users u on u.uid=p.uid LIMIT 10;`
- `select uid, username, description from users;`
- `SELECT * FROM users WHERE username='James';`

Exploring services information
- `select count(name) from services where status=’RUNNING’;`
- `select name, status from services;`
- `select count(name) from services;`

Exploring Installed Programs
- `SELECT * FROM programs LIMIT 1;`
- `SELECT name from programs;`
- `SELECT name, version, install_location, install_date from programs limit 1;`
- `SELECT count(*) from programs;`
- `select uid, pid, name, path from processes;`
- `select name,install_location from programs where name LIKE ‘%wireshark%’;`

## Conclusion 

In this module, Endpoint monitoring solutions are complex to understand and such solutions are integrated with SIEM or 24/7 monitoring. Do more Practice and Expert it!. <br>
**6/27/2024** <br>
Contributed By - Jord@n
