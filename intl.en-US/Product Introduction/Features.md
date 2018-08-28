# Features {#concept_sh1_pp4_tdb .concept}

Alibaba Cloud provides Layer-4 and Layer-7 load balancing services, and other functions such as health check, session persistence, domain forwarding and so on to ensure high availability of your applications.

|Feature|Layer-4 SLB|Layer-7 SLB|
|:------|:----------|:----------|
| Scheduling algorithm

 Server Load Balancer supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).

 |✔|✔|
| Health check

 Server Load Balancer checks the health status of backend servers. If a backend server is declared unhealthy, Server Load Balancer will distribute incoming traffic to other healthy backend servers and stop distributing traffic to it until it returned to the healthy status.

 |✔|✔|
| Session persistence

 Server Load Balancer supports session persistence. In a session, Server Load Balancer can distribute requests from the same client to a same backend server.

 |✔|✔|
| Access control

 Server Load Balancer support adding whitelists and blacklists to control the access to your applications.

 |✔|✔|
| High availability 

 Server Load Balancer can forward incoming traffic to backend servers in different zones. Additionally, Server Load Balancer is deployed in the active/standby mode in most regions. Server Load Balancer will automatically switches to the standby zone to provide the load balancing service if the primary zone is unavailable.

 |✔|✔|
| Security

 Combined with Alibaba Cloud Security, Server Load Balancer can defend against up to 5 Gbps DDoS attacks.

 |✔|✔|
| Internet and internal load balancing

 Server Load Balancer provides both Internet-facing and internal load balancing services. You can create a private SLB instance to balance traffic going through in your VPC network, or create an Internet SLB instance to balance traffic coming from the Internet.

 |✔|✔|
| Monitoring

 With the CloudMonitor service, you can view the number of connections, and other traffic information of SLB listeners.

 |✔|✔|
| IPv6 support

 Server Load Balancer support forwarding requests from IPv6 clients.

 |✔|✔|
| Access logs

 With Log Service, you can analyze access logs of an SLB instance to understand the behavior and geographical distribution of client users, troubleshoot problems and so on.

 |—|✔|
| Health check logs

 Server Load Balancer stores health check logs of backend servers in three days by default. You can store all health check logs in OSS for troubleshooting.

 |✔|✔|
| Domain/URL forwarding

 Layer-7 Server Load Balancer supports configuring domain/URL forwarding rules to forward requests from different domains or URLs to different backend servers.

 |—|✔|
| Certificate management

 Server Load Balancer provides a centralized certificate management service for applications using HTTPS protocols. You do not need to upload certificates to backend servers. Deciphering is performed on Server Load Balancer to reduce the CPU usage of backend servers.

 |—|✔|
| SNI support

 Server Load Balancer supports configuring multiple certificates in an HTTPS listener to distribute requests from different domains to different backend servers.

 |—|✔|
| Redirection

 Server Load Balancer supports redirecting HTTP requests to HTTPS requests.

 |—|✔|
| WS/WSS support

 WebSockets is a new HTML protocol. It provides bi-directional communication channels between a client and a server, saving server resources and bandwidth and achieving real-time communication.

 |—|✔|
| HTTP/2 support

 HTTP/2 is the second version of Hypertext Transfer Protocol. It is backward compatible with HTTP1.X and significantly improves performance by allowing multiple requests to be sent to on the same connection.

 |—|✔|

