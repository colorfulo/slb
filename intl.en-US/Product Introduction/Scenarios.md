# Scenarios {#concept_evl_4p4_tdb .concept}

Server Load Balancer is suitable for applications with high traffic, improving the availability and reliability.

## Load balance your applications {#section_gft_1x4_tdb .section}

Server Load Balancer can automatically distribute incoming traffic across multiple backend servers \(ECS instances\). Additionally, the requests from the same client can be distributed to the same backend server by configuring session persistence.

## **Scale your applications** {#section_l45_dx4_tdb .section}

To meet the demand of your customers, you can increase the number of the backend servers at any time to scale your applications. SLB is applicable to various web servers and application servers.

## Protect your applications from single point of failures {#section_gkp_3x4_tdb .section}

You can add multiple ECS instances to a Server Load Balancer instance. When some ECS instances are faulty, Server Load Balancer automatically shields faulty ECS instances and distributes requests to healthy ECS instances, guaranteeing that the application system can still work normally.

## Achieve better disaster tolerance in multiple zones {#section_kc4_kx4_tdb .section}

To provide more stable and reliable services, Server Load Balancer is deployed in multiple zones in most regions to achieve same-region disaster tolerance. If the primary zone becomes unavailable, Server Load Balancer in the standby zone takes over the load balancing service in 30 seconds. Once the primary zone becomes available, Server Load Balancer automatically switches back to the primary zone.

We recommend that you create a Server Load Balancer instance in a region with multiple zones deployed. Additionally, you also need to consider the deployment of backend servers. We recommend that you add at least one backend server in each zone to achieve the highest efficiency.

As shown in the following figure, ECS instances in different zones are added to an SLB instance. In normal situation, Server Load Balancer will distribute incoming traffic to the ECS instances in the primary zone \(Zone A\). Once the primary zone is unavailable, the incoming traffic will be distributed to the ECS instances in standby zone. This avoids service interruption caused by the failure of a single zone, and also reduces latency.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1541401484947_en-US.png)

However, if you deploy all ECS instances in the primary zone and have no ECS instances deployed in the standby zone, your service may be interrupted when the primary zone is unavailable, because no ECS instances are available to handle the distributed requests in the standby zone. This deployment mode achieves low latency at the expense of high availability.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1541401484948_en-US.png)

## Achieve better disaster tolerance across regions {#section_x5d_5x4_tdb .section}

You can deploy Server Load Balancer instances in different regions, and attach ECS instances of different zones in the corresponding regions. The upper layer uses Alibaba Cloud DNS as intelligent DNS, and resolves domain names to service addresses of Server Load Balancer instances in different regions, thus implementing global load balancing. When the system becomes unavailable in a region, you can temporarily stop DNS so that no user access is affected.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1541401484949_en-US.png)

