# Scenarios {#concept_evl_4p4_tdb .concept}

Server Load Balancer is suitable for applications with high traffic, improving the availability and reliability.

## Load balance your applications {#section_gft_1x4_tdb .section}

Server Load Balancer can automatically distribute incoming traffic across multiple backend servers \(ECS instances\). Additionally, the requests from the same client can be distributed to the same backend server by configuring session persistence.

## **Scale your applications** {#section_l45_dx4_tdb .section}

To meet the demand of your customers, you can increase the number of the backend servers at any time to scale your applications. Integrated with Auto Scaling, your applications can always be extensible if one of your backend server exceeds the preconfigured threshold.

## Protect your applications from single point of failures {#section_gkp_3x4_tdb .section}

You can add multiple backend servers to an SLB instance. If some of the backend servers are unhealthy, Server Load Balancer will stop distributing incoming traffic to them and distribute the traffic to the healthy ones. Once the backend servers become healthy, Server Load Balancer will automatically resume distributing traffic to them.

## Achieve better disaster tolerance in multiple zones {#section_kc4_kx4_tdb .section}

To provide more reliable services, Server Load Balancer is deployed in multiple zones in most regions. If the primary zone becomes unavailable, Server Load Balancer in the standby zone is capable to take over the load balancing service in 30 seconds. Once the primary zone becomes available, Server Load Balancer automatically switches back to the primary zone.

It is recommended that you create a Server Load Balancer instance in a region with multiple zones deployed. Additionally, you also need to consider the deployment of backend servers. It is recommended that you add at least one backend server in each zone to achieve the best efficiency.

As shown in the following figure, ECS instances in different zones are added to an SLB instance. In normal situation, Server Load Balancer will distribute incoming traffic to the ECS instances in the primary zone \(Zone A\). Once the primary zone is unavailable, the incoming traffic will be distributed to the ECS instances in standby zone. This avoids service interruption caused by the failure of a single zone, and also reduces latency between cloud resources.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1535456347947_en-US.png)

However, if you deploy all ECS instances to the primary zone and have no ECS instances deployed in the standby zone. Your service may be interrupted when the primary zone is unavailable, because no ECS instances are available to handle the distributed requests in the standby zone. This deployment takes low latency at the expense of high availability.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1535456347948_en-US.png)

## Achieve better disaster tolerance cross regions {#section_x5d_5x4_tdb .section}

You can create multiple SLB instances in different zones and add ECS instances in the corresponding region as the backend servers. Then, use Alibaba Cloud DNS to resolve a domain to the IP addresses of the created SLB instances. When a region becomes unavailable, DNS will automatically resolve the domain to the standby Server Load Balancer.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1535456347949_en-US.png)

