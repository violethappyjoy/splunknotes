ref.: [refLink](https://docs.splunk.com/Documentation/Splunk/8.2.5/InheritedDeployment/Ports
Components and their relationship with the network

| Component                  | Purpose                                        | Communicates on | Listens on                   |
| -------------------------- | ---------------------------------------------- | --------------- | ---------------------------- |
| All components*            | Management / REST API                          | N/A             | TCP/8089                     |
| Search head / Indexer      | Splunk Web access                              | Any             | TCP/8000                     |
| Search head                | App Key Value Store                            | Any             | TCP/8065, TCP/8191           |
| Indexer                    | Receiving data from forwarders                 | N/A             | TCP/9997                     |
| Search head cluster member | Cluster replication                            | N/A             | TCP/8081, TCP/9887, TCP/8181 |
| Indexer cluster peer node  | Cluster replication                            | N/A             | TCP/8080, TCP/9887           |
| Heavy Forwarder or Indexer | Receiving data over HTTP Event Collector (HEC) | N/A             | TCP/8088                     |
![[Pasted image 20250115211706.png]]