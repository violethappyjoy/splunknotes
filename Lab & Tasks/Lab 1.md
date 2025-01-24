## What is Splunk?
Splunk is a software platform used for searching, analyzing, and visualizing machine-generated data from various sources like applications, servers, networks, and devices in real-time. It is widely used for log management, monitoring, security, and business intelligence.
#### Common Use Cases
- IT Operations: Monitoring infrastructure and troubleshooting issues.
- Security: Detecting and responding to threats through Security Information and Event Management (SIEM).
- DevOps: Observability into CI/CD pipelines and application performance.
- Business Insights: Analyzing customer behavior or operational data.
## [[Task 1]] - Install Splunk and configure distributed arch.
Step 1: Install Splunk on instance 1 and configure SH(Search Head), LM(License Master) DS(Deployment Server) and DMC(Distributed management Console)
Step 2: Install Splunk on instance 2, 3 and 4. Disable UI
- Types of distributed deployment: [Link](https://docs.splunk.com/Documentation/Splunk/8.2.4/Deploy/Deploymentcharacteristics)
- Best practices to install Splunk: [Link](https://docs.splunk.com/Documentation/Splunk/8.2.5/Installation/Whatsinthismanual)
- Default Splunk ports: [Link](https://docs.splunk.com/Documentation/Splunk/8.2.5/InheritedDeployment/Ports)
- How Licensing Works: [Link](https://docs.splunk.com/Documentation/Splunk/8.2.5/Admin/HowSplunklicensingworks)
- DS and DC: [Link](https://docs.splunk.com/Documentation/Splunk/8.2.5/Updating/Aboutdeploymentserver)

## [[Task 2]]
Step 1: Create Index
		1. IDX1
			1. crest_window: Retention 1 month
			2. crest_prod: retention 3 months
		2. IDX2
			1. crest_hr: retention 3 months
			2. crest_dev: retention 2 months
Step 2: Setup distributed search on SH and add both the indexer.(Hint add-peer)
Step 3: Enable listening on indexer on ingestion port (hint: inputs.conf)

- [Bucket life cycle](https://conf.splunk.com/files/2017/slides/splunk-data-life-cycle-determining-when-and-where-to-roll-data.pdf)
- [Stores indexes](https://docs.splunk.com/Documentation/Splunk/8.2.5/Indexer/HowSplunkstoresindexes)
- [How indexing works](https://community.splunk.com/t5/Getting-Data-In/Diagrams-of-how-indexing-works-in-the-Splunk-platform-the-Masa/m-p/590774)
## [[Task 3]]
Lab Goal: Create a Splunk Distributed architecture that is Non-Clustered.
Naming conventions and role of each machine: (To be followed strictly)

|               |                                                                                  |
| ------------- | -------------------------------------------------------------------------------- |
| **Name**      | **Role**                                                                         |
| Splunk_Core_1 | - Search Head<br>- License Master<br>- Deployment Server<br>- Monitoring Console |
| Splunk_Core_2 | Indexer                                                                          |
| Splunk_Core_3 | Universal Forwarder                                                              |

**Task description** 
1. Install Splunk on all the instances 
2. Use the latest Splunk version 
3. What is the general practice around suggesting what version of Splunk to be used? If a customer asked you, what version would you suggest?
4. Can I have different versions of Splunk installed on different instances (Forwarder, Indexer, SH?) Does it work? What is the impact if you run different versions? Understand Splunk compatibility matrix.
1. Splunk_Core_1 should act as SH, LM, DS, DMC
2. Splunk_Core_21, Splunk_Core_22 and Splunk_Core_23 should be idx
3. Machine 5 should act as UF
**Technical Specifications:**
1. Management Port : 8089
2. Ingestion Port : 9997
======================================================================
Step 1 : Install Splunk on instance 5 (UF)
Step 2 :  configure UF to send data to idx1, idx2 and idx3 (hint : outputs.conf )
Step 3 : Enable data stream via forwarder using app. Pushing the app via DS
1. Input via FS [hint monitor] - /var/log/messages
index : crest_dev
source type : linux_messages
1. Add monitor via CLI (Structured) [Attached csv file]
index : crest_prod
 Step 4 : Look at all the source types in crest_dev & crest_prod.
Step 5 : Look at the host which is using dhcp and create a count of unique ip addresses as below. Expected output as below.(hint: field extraction via regex)
- [Different ways of ingesting data to Splunk](https://docs.splunk.com/Documentation/Splunk/latest/Data/Configureyourinputs)
- [Forwarding Best Practices 1](https://docs.splunk.com/Documentation/Splunk/8.2.4/DistSearch/Forwardsearchheaddata)
- [Forwarding Best Practices 2](https://docs.splunk.com/Documentation/Splunk/8.2.4/Indexer/Forwardmanagerdata)
- [Troubleshooting Inputs](https://docs.splunk.com/Documentation/Splunk/8.2.4/Data/Troubleshoottheinputprocess)
- [Search Best Practices 1](https://www.splunk.com/en_us/blog/customers/splunk-clara-fication-search-best-practices.html)
- [Search Best Practices 2](https://docs.splunk.com/Documentation/Splunk/latest/SearchTutorial/Startsearching)



