# Tutorial overview {#concept_ybd_pfl_vdb .concept}

This section provides a complete tutorial on using Server Load Balancer \(SLB\). An Internet SLB instance is created to distribute incoming requests to two backend servers.

**Note:** Before creating an SLB instance, you must plan your SLB service, such as the instance type, instance region, and more. For more information, see [Plan and prepare](reseller.en-US/Quick Start (New Console)/Plan and prepare.md#).

The tutorial includes the following tasks:

1.  [Create an ECS instance](reseller.en-US/Quick Start (New Console)/Create an ECS instance.md#)

    Server Load Balancer is a complementary service for ECS multi-machine solutions, and must be used in conjunction with ECS instances. In this tutorial, two ECS instances are created to process the distributed traffic.

2.  [Deploy applications](reseller.en-US/Quick Start (New Console)/Install static web pages.md#)

    Deploy applications on ECS instances. In this tutorial, a static web page is created by using Apache to test the load balancing service.

3.  [Create an SLB instance](reseller.en-US/Quick Start (New Console)/Create an SLB instance.md#)

    Create an SLB instance. An SLB instance is a running entity of Server Load Balancer.

4.  [Configure listeners and add backend servers](reseller.en-US/Quick Start (New Console)/Configure an SLB instance.md#)

    After creating an SLB instance, you have to add at least one listener, and add ECS instances as backend servers.

5.  [Resolve a domain name](reseller.en-US/Quick Start (New Console)/Resolve a domain name.md#)\(optional\)

    Use Alibaba Cloud DNS to resolve a domain name to the IP address of the SLB instance to provide external services.

6.  [Delete an SLB instance](reseller.en-US/Quick Start (New Console)/Delete an SLB instance.md#)

    If you no longer need the SLB instance, release it to avoid additional charges.


