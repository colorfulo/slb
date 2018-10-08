# Create an SLB instance {#task_ctx_xsm_vdb .task}

Before creating an SLB instance, make sure that you have properly prepared the environment. For more information, see [Plan and prepare](../../../../intl.en-US/Quick Start (New Console)/Plan and prepare.md#).

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou). 
2.  In the left-side navigation pane, click **Instances** \> **Server Load Balancer**, and click **Create SLB Instance** in the upper-left corner. 
3.   Configure the SLB instance according to the following information. 

    |Configuration|Description|
    |:------------|:----------|
    |**Region**| Select the region where the SLB instance is located.

 **Note:** Make sure that the region of the SLB instance is the same as that of backend ECS instances.

 |
    |**Zone Type**|Display the zone type of the selected region. The zone of a cloud product refers to a set of independent infrastructure and is usually represented by Internet data centers \(IDCs\). Different zones have independent infrastructure \(network, power supply, air-conditioning and so on\). Therefore, an infrastructure fault in one zone will not affect other zones. A zone belongs to a specific region, however, a single region may have one or more zones. SLB has deployed multi-zone in most regions.    -   Single zone: The SLB instance is deployed only in one zone.
    -   Multi-zone: The SLB instance is deployed in two zones. By default, the instance in the primary zone is used to distribute traffic. If the primary zone is faulty, the instance in the backup zone will automatically take over the load balancing service.
|
    |**Primary Zone**|Select the primary zone for the SLB instance. The primary zone carries traffic in normal conditions.|
    |**Backup Zone**|Select the backup zone for the SLB instance. The backup zone only takes over traffic when the primary zone is unavailable.|
    |**Instance Spec**| Select a performance capacity for the instance.

 The performance metrics vary by specification. For more information, see [Guaranteed-performance instances](../../../../intl.en-US/Best Practices/How to use a guaranteed-performance Server Load Balancer instance?.md#).

 |
    |**Instance Type**|Select the instance type based on your business needs. A public or a private IP address is allocated to the SLB instance based on the instance type.  For more information, see [SLB instance and network type](intl.en-US/User Guide/SLB instances/SLB instances overview.md#).    -   Internet: An Internet SLB instance only provides an Internet IP and you can access the SLB service from the Internet.
    -   Intranet: An intranet SLB instance only provides a private IP and you can only access the SLB service from the intranet.
|
    |**Network Type**|If the selected instance type is Intranet, you have to select a network type for the instance.    -   Classic network: The IP of the instance is allocated and managed by Alibaba Cloud in a unified manner.
    -   VPC: The IP of the instance is allocated from the VSwitch CIDR block specified by you.
|
    |**Purchase Quantity**|Select the number of instances to create.|

4.  Click **Buy Now** and complete the payment. 

