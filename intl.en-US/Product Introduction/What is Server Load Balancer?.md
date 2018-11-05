# What is Server Load Balancer? {#concept_whs_lp4_tdb .concept}

## Overview {#section_dy5_4qx_k2b .section}

Server Load Balancer \(SLB\) is a traffic distribution control service that distributes the incoming traffic among multiple ECS instances according to the configured forwarding rules. SLB expands application service capabilities and enhances application availability.

By setting a virtual service address, SLB virtualizes the added ECS instances into an application service pool with high-performance and high availability, and distributes client requests to ECS instances in the server pool based on forwarding rules.

SLB also checks the health status of the added backend servers, and automatically isolates abnormal ECS instances to eliminate single point of failure \(SPOF\), improving the overall service capability of your application. Additionally, working with Alibaba Anti-DDoS, SLB is able to defend DDoS attacks.

## Server Load Balancer consists of the following components: {#section_ppv_hq4_tdb .section}

SLB consists of the following components:

-   SLB instances

    An SLB instance is a running load balancing service that distributes incoming traffic to backend servers. To use the load balancing service, you must create an SLB instance, and then configure the instance with at least one listener and two backend servers.

-   Listeners

    A listener checks client requests and forwards the requests to the backend servers according to the configured rules. It also performs health check on backend servers.

-   Backend Servers

    Backend servers are the ECS instances added to a SLB instance to process the distributed requests. You can add ECS instances to the default server group, a VServer group, or an active/standby server group to process distributed requests.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4091/1541385352936_en-US.png)


## Benefits {#section_ws5_vq4_tdb .section}

-   High availability

    Server Load Balancer is designed to work in the full-redundancy mode without SPOF. Server Load Balancer supports local and cross-region disaster tolerance. When Server Load Balancer is used together with DNS, the service availability is up to 99.95%.

    You can scale your service based on the application load, without interrupting services continuity.

-   Scalable

    You can increase or decrease the number of backend servers as needed to expand the service capabilities of your applications.

-   Cost effectiveness

    Compared with the traditional hardware load balancing system, Server Load Balancer reduces the cost by 60%.

-   Secure

    Combined with Alibaba Cloud Security, Server Load Balancer can defend against up to 5 Gbps DDoS attacks, such as HTTP flood and SYN flood attacks.


