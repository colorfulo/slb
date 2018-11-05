# Terms {#concept_fz5_np4_tdb .concept}

|Term|Description|
|:---|:----------|
|Server Load Balancer|Alibaba Cloud Server Load Balancer \(SLB\) is a traffic distribution control service that distributes the incoming traffic among multiple Elastic Compute Service \(ECS\) instances according to the configured forwarding rules.|
|Server Load Balancer instance|A Server Load Balancer instance is a running entity of the Server Load Balancer service. To use Server Load Balancer, you must first create a Server Load Balancer instance.|
|Endpoint|An IP address allocated to an SLB instance. According to the instance type, the IP address is either a public IP or a private IP. You can resolve a domain name to a public IP address to provide external services.|
|Listener|A listener defines how incoming requests are distributed. An SLB instance must contain at least one listener.|
|Backend servers|The ECS instances that are added to an SLB instance to process distributed requests.|
|Default server group| A group of ECS instances that process the distributed requests.

 If a listener does not configure a VServer group or an active/standby server group, the default server group is used. Incoming traffic is distributed to ECS instances in the default server group.

 |
|VServer group| A group of ECS instances that process the distributed requests.

 Different listeners can be associated with different VServer groups to distribute different requests to different backend servers.

 |
|Active/standby server group|An active/standby server group contains only two ECS instances. One is the active server and the other one is the standby server. When the health check of the active server fails, Server Load Balancer will automatically route traffic to the standby server.|

