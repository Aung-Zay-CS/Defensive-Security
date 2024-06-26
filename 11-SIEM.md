#  SIEM
SIEM stands for Security Information and Event Management system.
It is a tool that collects data from various endpoints/network devices across the network, stores them at a centralized place, and performs correlation on them. 

Some key features provided by SIEM are:
- Real-time log Ingestion
- Alerting against abnormal activities
- 24/7 Monitoring and visibility
- Protection against the latest threats through early detection
- Data Insights and visualization
- Ability to investigate past incidents.

All these logs provide a wealth of information and can help in identifying security issues. Each SIEM solution has its own way of ingesting the logs. Some common methods used by these SIEM solutions are explained below:
- Agent / Forwarder: These SIEM solutions provide a lightweight tool called an agent (forwarder by Splunk) that gets installed in the Endpoint. It is configured to capture all the important logs and send them to the SIEM server.
- Syslog: Syslog is a widely used protocol to collect data from various systems like web servers, databases, etc., are sent real-time data to the centralized destination.
- Manual Upload: Some SIEM solutions, like Splunk, ELK, etc., allow users to ingest offline data for quick analysis. Once the data is ingested, it is normalized and made available for analysis.
- Port-Forwarding: SIEM solutions can also be configured to listen on a certain port, and then the endpoints forward the data to the SIEM instance on the listening port.

###  SIEM Capabilities
SIEM is one major component of a Security Operations Center (SOC) ecosystem, as illustrated below.
SIEM starts by collecting logs and examining if any event/flow has matched the condition set in the rule or crossed a certain threshold

Some of the common capabilities of SIEM are:
- Correlation between events from different log sources.
- Provide visibility on both Host-centric and Network-centric activities.
- Allow analysts to investigate the latest threats and timely responses.
- Hunt for threats that are not detected by the rules in place.

###  Dashboard
Dashboards are the most important components of any SIEM. SIEM presents the data for analysis after being normalized and ingested. Some of the information that can be found in a dashboard are:
- Alert Highlights
- System Notification
- Health Alert
- List of Failed Login Attempts
- Events Ingested Count
- Rules triggered
- Top Domains Visited

##  SIEM Architecture

###  Elastic stack

Elastic stack is the collection of different open source components linked together to help users take the data from any source and in any format and perform a search, analyze and visualize the data in real-time.

***Elasticsearch***

Elasticsearch is a full-text search and analytics engine used to store JSON-formated documents. Elasticsearch is an important component used to store, analyze, perform correlation on the data, etc. Elasticsearch supports RESTFul API to interact with the data.

***Logstash***

Logstash is a data processing engine used to take the data from different sources, apply the filter on it or normalize it, and then send it to the destination which could be Kibana or a listening port. A logstash configuration file is divided into three parts, as shown below.

- The input part is where the user defines the source from which the data is being ingested.

- The filter part is where the user specifies the filter options to normalize the log ingested above. 

- The Output part is where the user wants the filtered data to send. It can be a listening port, Kibana Interface, elasticsearch database, a file, etc

***Beats***

Beats is a host-based agent known as Data-shippers that is used to ship/transfer data from the endpoints to elasticsearch. Each beat is a single-purpose agent that sends specific data to the elasticsearch.

***Kibana***

Kibana is a web-based data visualization that works with elasticsearch to analyze, investigate and visualize the data stream in real-time. It allows the users to create multiple visualizations and dashboards for better visibility.

***How they work together***
- Beats is a set of different data shipping agents used to collect data from multiple agents. Like Winlogbeat is used to collect windows event logs, Packetbeat collects network traffic flows.
- Logstash collects data from beats, ports or files, etc., parses/normalizes it into field value pairs, and stores them into elasticsearch.
- Elasticsearch acts as a database used to search and analyze the data.
- Kibana is responsible for displaying and visualizing the data stored in elasticsearch. The data stored in elasticseach can easily be shaped into different visualizations, time charts, infographics, etc., using Kibana.

###  SPlunk
Splunk is one of the leading SIEM solutions in the market that provides the ability to collect, analyze and correlate the network and machine logs in real-time. 
Splunk has three main components, namely Forwarder, Indexer, and Search Head. These components are explained below:

***Splunk Forwarder***

Splunk Forwarder is a lightweight agent installed on the endpoint intended to be monitored, and its main task is to collect the data and send it to the Splunk instance.
It does not affect the endpoint's performance as it takes very few resources to process. Some of the key data sources are:
- Web server generating web traffic.
- Windows machine generating Windows Event Logs, PowerShell, and Sysmon data.
- Linux host generating host-centric logs.
- Database generating DB connection requests, responses, and errors.

***Splunk Indexer***

Splunk Indexer plays the main role in processing the data it receives from forwarders.
It takes the data, normalizes it into field-value pairs, determines the datatype of the data, and stores them as events. Processed data is easy to search and analyze.

***Search Head***

Splunk Search Head is the place within the Search & Reporting App where users can search the indexed logs as shown below.
When the user searches for a term or uses a Search language known as Splunk Search Processing Language, the request is sent to the indexer and the relevant events are returned in the form of field-value pairs.
