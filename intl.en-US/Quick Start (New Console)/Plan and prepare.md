# Plan and prepare {#concept_ug3_rfl_vdb .concept}

Before using Server Load Balancer, you must determine the instance region, listener protocol, and network types to use according to your business.

## Plan the region of the Server Load Balancer instance {#section_nby_m4l_vdb .section}

Note the following when selecting the region where the SLB instance is created:

-   To reduce latency and increase the download speed, it is recommended that you choose a region that is physically closest to the region where your customers are located.
-   To provide more stable and reliable load balancing services, multiple zones for Server Load Balancer are deployed in most regions for better disaster tolerance. It is recommended that you select the region where primary and backup zones are available.
-   Server Load Balancer does not support cross-region deployment. Ensure that the region is the same for the Server Load Balancer and the backend ECS instances.

## Choose a network type \(Internet or intranet\) {#section_o3k_44l_vdb .section}

Server Load Balancer provides Internet and Intranet load balancing services:

-   If you want to user Server Load Balancer to distribute requests from the Internet, create an Internet SLB instance.

    An Internet SLB instance is provided with a public IP to receive requests from the Internet.

-   If you want to use Server Load Balancer to distribute requests from the intranet, create an intranet SLB instance.

    An intranet Server Load Balancer instance only has a private IP and is accessible only from a classic network or VPC.


## Select an instance specification {#section_v4f_bzg_y2b .section}

Server Load Balancer launched guaranteed-performance instances on April 1, 2018. With guaranteed-performance instances, you can exclusively use your instance resources to guarantee service availability. Alibaba Cloud Server Load Balancer provides 6 specifications for you to use.

-   For a Pay-As-You-Go instance, you can select the largest specification \(slb.s3.large\). This guarantees the business flexibility \(flexibility\) and will not cause extra costs. But if you think your business is unlikely to reach Super I \(slb.s3.large\), you can also set a reasonable limit of flexibility, such as slb.s3.medium.
-   对于预付费实例，您需要评估您的实际业务量，然后选择一个较合适的规格，对于业务量评估来说，主要参考下面几个原则：
    -   如果是四层监听，关注的重点是长连接的并发连接数，那么最大（并发）连接数应当作为一个关键指标来参考。 根据不同的业务场景，您需要预估一个负载均衡实例需要承载的最大并发连接数，并选择相应的规格。
    -   如果是七层监听，关注的重点是QPS的性能，QPS决定了一个七层应用系统的吞吐量。 同样，您也需要根据经验对QPS进行预估。 在初步选定一个规格后，在业务压测和实测过程中对规格进行微调。
    -   结合与性能保障型实例一起推出的其它关键监控指标，查看实际业务流量的走势、峰值情况，对性能规格进行更加精确的选取。

## Select a listener protocol {#section_bhq_r4l_vdb .section}

Server Load Balancer supports Layer-4 \(TCP and UDP\) and Layer-7 \(HTTP and HTTPS\) load balancing.

-   A Layer-4 listener distributes connection requests directly to backend servers without modifying HTTP headers. After a request arrives at a Layer-4 listener, Server Load Balancer uses the backend port configured in the listener to create a TCP connection with backend ECS instances.
-   A Layer-7 listener is an implementation of reverse proxy. After a request arrives at a Layer-7 listener, Server Load Balancer uses a TCP connection to transmit the data packets to backend ECS instances instead of transmitting the data packets directly.

    The Layer-7 listener has one more procedure than the Layer-4 listener when forwarding incoming requests. Due to this additional procedure, the performance of the Layer-7 listener is less efficient to that of the Layer-4 listener. In addition, scenarios such as insufficient client ports and excessive connections to backend servers also affect the performance of the Layer-7 listeners. If you have high performance requirements, it is recommended that you use Layer-4 listeners.

    For more information, see [Protocols](../../../../intl.en-US/User Guide (New Console)/Listeners/Listener overview.md#table_spy_pp5_vdb).


## Prepare backend servers {#section_f5v_54l_vdb .section}

Before using the load balancing service, you must create an ECS instance and deploy applications on it, then add the ECS instance to an SLB instance to handle the forwarded client request.

Note the following when creating and configuring ECS instances:

-   ECS regions and zones

    Make sure the region is the same for the ECS instances and Server Load Balancer instance. Additionally, it is recommended that you deploy the ECS instances in different zones to improve availability.

-   Application configuration

    No additional configuration is not required after applications are deployed on the ECS instances. However, if you want to use a Layer-4 listener, and the ECS instances use the Linux operating system, make sure the values of the following parameters in the net.ipv4.conf file are set to zero:

    ```
    
    net.ipv4.conf.default.rp_filter = 0
    net.ipv4.conf.all.rp_filter = 0
    net.ipv4.conf.eth0.rp_filter = 0
    ```


