# Create an IPv6 instance {#task_uz2_kjz_c2b .task}

Server Load Balancer supports creating IPv6 instances. After an IPv6 instance is created, the system allocates a public IPv6 address to the instance to forward requests from IPv6 clients.

IPv6 is the abbreviation of Internet Protocol Version 6. IPv6 is the next-generation IP protocol designed by IETF \(Internet Engineering Task Force\) to replace the current version of IP protocol \(IPv4\). By extending the length of IPv4 address from 32 bits to 128 bits, it expands the address space by 79,228,162,514,264,337,593,543,950,336 times. After IPv6 is used, each sand on the world can be allocated with an IP address.

**Note:** 

-   Currently, only Zone E and Zone F in the China \(Hangzhou\) region support creating IPv6 instances and the instances must be guaranteed-performance instances.
-   The Internet IPv6 network environment is still in the early stages of construction, and some links may cannot be accessed. If such problem occurs, submit a ticket. Besides, SLA is not provided in the pre-release stage.
-   Because IPv6 has a longer IP head than IPv4, when you use a UDP listener on an IPv6 SLB instance, you must ensure that the MTU of the NIC communicating with the SLB on the backend server \(ECS instance\) is not greater than 1480 \(some applications require synchronizing its configuration files based on this MTU value\), otherwise the packets may be discarded because they are too large.

    If you use a TCP/HTTP/HTTPS listener, no additional configurations are required because the TCP protocol supports MSS auto-negotiation.


SLB IPv6 has the following features:

-   Smooth migration, which is not sensed by the service

    You can directly bind ECS instances using IPv4 addresses to an IPv6 SLB instance and smoothly migrate the service to IPv6 without transforming the original system.

    Adding the IPv6 entry has no impact on the original IPv4 service. If the traffic volume increases, you only need to increase the backend ECS instances.

-   IPv6 access control ensures more security and reliable service deployment

    Alibaba Cloud SLB supports IPv6 access control. You can configure the access control list according to your business needs.

    -   A blacklist can effectively block the access of malicious addresses to the SLB service.
    -   If a whitelist is configured, only addresses in the whitelist can access the SLB service.

1.   Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb). 
2.  Select **Instances** \> **Server Load Balancer**. 
3.  On the Server Load Balancer page, click **Create SLB Instance** in the upper-left corner. 
4.   Configure the SLB instance. For the IP version, select **IPv6**. Other configurations are the same as configurations of common instances. See [SLB configurations](reseller.en-US/User Guide/SLB instances/Create an SLB instance.md#table_ivr_hjn_vdb).

    **Note:** Currently, only Zone E and Zone F in the China \(Hangzhou\) region support creating IPv6 instances and the instances must be guaranteed-performance instances.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15645/15368333527308_en-US.png)

5.   Go back to the Server Load Balancer page to view the created IPv6 instance. 

Once the IPv6 instance is created, the system allocates an IPv6 address to it.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15645/15368333527309_en-US.png)

