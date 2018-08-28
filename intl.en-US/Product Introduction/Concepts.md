# Concepts {#concept_fz5_np4_tdb .concept}

|Term|Description|
|:---|:----------|
|Server Load Balancer|Alibaba Cloud Server Load Balancer \(SLB\) is a traffic distribution control service that distributes the incoming traffic among multiple Elastic Compute Service \(ECS\) instances according to the configured forwarding rules.|
|Server Load Balancer instance|A Server Load Balancer instance is a running entity of the Server Load Balancer service. To use Server Load Balancer, you must first create a Server Load Balancer instance.|
|Service address|An IP address allocated to an SLB instance. According to the instance type, the IP address is either a public IP or a private IP. You can resolve a domain to a public IP address to provide external services.|
|Listener|A listener defines how incoming requests are distributed. An SLB instance must contain at least one listener.|
|Backend server|The ECS instances that are added to an SLB instance to respond to the distributed requests.|
|Default server group| A group of ECS instances that process the distributed requests.

 If a listener does not configure a VServer group, nor an active/standby server group, the default server group will be used. Incoming traffic will be distributed to the ECS instances in the default server group.

 |
|VServer group| A group of ECS instances that process the distributed requests.

 Different listeners or forwarding rules can configure different VServer groups to distribute different requests to different backend servers.

 |
|Active/standby server group|An active/standby server group contains only two ECS instances. One is the active server and the other one is the standby server. An active/standby server group can only be used in TCP and UDP listeners. When the health check of the active server fails, Server Load Balancer will automatically route traffic to the standby server.|

