# Features {#concept_sh1_pp4_tdb .concept}

Alibaba Cloud provides Layer-4 and Layer-7 load balancing services, and other functions such as health check, session persistence, domain name based forwarding and so on to ensure high availability of your applications.

|Functions|Layer-4 Server Load Balancer|Layer-7 Server Load Balancer|
|:--------|:---------------------------|:---------------------------|
| Scheduling algorithm

 Server Load Balancer supports round robin, weighted round robin \(WRR\), weighted least connections \(WLC\), and consistent hash.

 |✔|✔|
| Health check

 Server Load Balancer checks the health status of backend servers. If a backend server is declared as unhealthy, Server Load Balancer will stop distributing traffic to it and distribute incoming traffic to other healthy backend servers.

 |✔|✔|
| Session persistence

 Server Load Balancer supports session persistence. In a session, Server Load Balancer can distribute requests from the same client to the same backend server.

 |✔|✔|
| Access control

 Server Load Balancer support adding whitelists and blacklists to control access to your applications.

 |✔|✔|
| High availability

 Server Load Balancer can forward incoming traffic to backend servers in different zones. Additionally, Server Load Balancer is deployed in the active/standby mode in most regions. Server Load Balancer will automatically switch to the standby zone to provide the load balancing service if the primary zone is unavailable.

 |✔|✔|
| Security

 Combined with Alibaba Cloud Security, Server Load Balancer can defend against up to 5 Gbps DDoS attacks.

 |✔|✔|
| Internet and intranet load balancing

 Server Load Balancer provides both Internet and intranet load balancing services. You can create an intranet SLB instance to balance traffic in your VPC network, or create an Internet SLB instance to balance traffic coming from the Internet.

 |✔|✔|
| Monitoring

 With the CloudMonitor service, you can view the number of connections, traffic and more of an SLB instance.

 |✔|✔|
| IPv6 support

 Server Load Balancer supports forwarding requests from IPv6 clients.

 |✔|✔|
| Access logs

 With Log Service, you can analyze access logs of an SLB instance to understand the behavior and geographical distribution of users, troubleshoot problems and more.

 |—|✔|
| Health check logs

 Server Load Balancer stores health check logs of backend servers generated within three days by default. You can store all health check logs in OSS for troubleshooting.

 |✔|✔|
| Domain name/URL based forwarding

 Layer-7 Server Load Balancer supports configuring domain name/URL based forwarding rules to forward requests from different domain names or URLs to different backend servers.

 |—|✔|
| Certificate management

 Server Load Balancer provides centralized certificate management service for applications using HTTPS protocols. You do not need to upload certificates to backend servers. Deciphering is performed on Server Load Balancer to reduce the CPU usage of backend servers.

 |—|✔|
| SNI support

 Server Load Balancer supports configuring multiple certificates in an HTTPS listener to distribute requests with different domain names to different backend servers.

 |—|✔|
| Redirection

 Server Load Balancer supports redirecting HTTP requests to HTTPS requests.

 |—|✔|
| WS/WSS support

 WebSockets is a new HTML protocol. It provides bi-directional communication channels between a client and a server, saving server resources and bandwidth and achieving real-time communication.

 |—|✔|
| HTTP/2 support

 HTTP/2 is the second version of Hypertext Transfer Protocol. It is backward compatible with HTTP1.X and significantly improves performance.

 |—|✔|

