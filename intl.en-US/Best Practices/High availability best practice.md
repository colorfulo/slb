# High availability best practice {#concept_ppk_txt_vdb .concept}

Server Load Balancer \(SLB\) guarantees availability in terms of system design, product configuration and so on. Besides, you can use SLB together with Alibaba Cloud DNS to achieve cross-region disaster recovery according to business needs.

## High availability of SLB system {#section_nk4_zxt_vdb .section}

Deployed in clusters, Server Load Balancer \(SLB\) can synchronize sessions to protect the ECS instances from single points of failure \(SPOFs\). This improves redundancy and guarantees the service stability. Layer-4 SLB uses the open source software Linux Virtual Server \(LVS\) with Keepalived to achieve load balancing. Layer-7 SLB uses Tengine to achieve load balancing. Tengine, a Web server project based on Nginx, adds advanced features dedicated for high-traffic websites.

Requests from the Internet reach the LVS cluster through ECMP routing. Each LVS in the LVS cluster synchronizes the session to other LVS machines in the cluster through multicast packets, thereby implementing session synchronization among machines in the LVS cluster. At the same time, the LVS cluster performs health check on the Tengine cluster and removes abnormal machines from the Tengine cluster to ensure the availability of Layer-7 Server Load Balancer.

Best practice:

Session synchronization ensures that persistent connections are not affected by server failure in the cluster. But for short connections or when the session synchronization rule is not triggered by the connection \(three-way handshake is not completed\), server failures in the cluster may still affect user requests. To prevent session interruption caused by machine failure in the cluster, you can add a retry mechanism to the service logic to reduce the impact on user access.

## High availability of a single SLB instance {#section_g3m_pvv_wdb .section}

To provide more reliable services, multiple zones for Server Load Balancer are deployed in most regions. If a active zone becomes unavailable, Server Load Balancer rapidly switches to a standby zone to restore its service capabilities within 30 seconds. When the active zone becomes available, Server Load Balancer automatically switches back to the active zone.

**Note:** The active zone and standby zone form zone-level disaster tolerance. An SLB instance switches to the standby zone only when Alibaba Cloud detects that the current zone is unavailable due to power outage or optical cable failure rather than the failure of an instance.

Best practice:

1.  We recommend that you create a Server Load Balancer instance in a region with multiple zones for disaster tolerance.
2.  You can deploy ECS instances in the active zone and standby zone respectively as needed. You can set the zone where most ECS instances are located to the active zone to minimize the access latency.

    However, we do not recommended that you deploy all ECS instances in one zone. You also need to deploy a small number of ECS instances in the standby zone, so that the standby zone still can process requests in extreme conditions \(the active zone is unavailable\).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4169/15382793133122_en-US.png)


## High availability of multiple SLB instances {#section_vvj_kwv_wdb .section}

If your requirements on the availability is extremely high, the availability guaranteeing mechanism of the SLB may cannot meet your demands. For example, when the SLB instance is unavailable due to network attach or configuration error, zone switching is not triggered because no zone-level failure occurs. At this time, you can create multiple SLB instances and schedule requests by using Alibaba Cloud DNS, or achieve cross-region disaster recovery through global Server Load Balancing.

Best practice:

You can deploy SLB instances and backend ECS instances in multiple zones of a region or in multiple regions, and use Alibaba Cloud DNS to schedule the requests.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4169/15382793133121_en-US.png)

## High availability of backend ECS instances {#section_cnp_dzt_vdb .section}

Server Load Balancer checks the service availability of backend ECS instances by performing health checks. The health checks improve the overall availability of front-end services and help reduce the impact of service availability when backend servers are abnormal.

When Server Load Balancer discovers that an instance is unhealthy, it distributes requests to other healthy ECS instances, and only resumes distributing requests to the instance when it has restored to a healthy status. For more information, see [Health check overview](../../../../reseller.en-US/User Guide/Listener/Health check/Health check overview.md#).

Best practice:

In order for the health check function to work, you need to enable and correctly configure the health check. For more information, see [Configure health check](../../../../reseller.en-US/User Guide/Listener/Health check/Health check configurations.md#).

