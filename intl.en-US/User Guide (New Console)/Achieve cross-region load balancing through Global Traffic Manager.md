# Achieve cross-region load balancing through Global Traffic Manager {#concept_hqf_4k5_vdb .concept}

## Global traffic management {#section_nyz_jlc_wdb .section}

Load balancing is divided into local load balancing and global load balancing according to the geographical structure of its application. Local load balancing balances loads of server groups in the same region. Global load balancing balances server groups that are in different regions and have different network structures.

By using Global Traffic Manager, you can deploy global traffic management above the local traffic balancing to achieve cross-region disaster tolerance, accelerate access from different regions and achieve intelligent resolution.

-   Multi-line intelligent resolution service

    Using DNS intelligent resolution and health check on the running status of the application, global traffic management directs user accesses to the most appropriate IP addresses so that the users can obtain the fastest and smoothest experience.

-   Cross-region disaster tolerance

    Global traffic management supports adding IP addresses of different regions to different address pools and configuring health check. In access policy configurations, set the **address pool A** as the default IP address pool and **address pool B** as the failover IP address pool. Then active-standby IP disaster tolerance of the application service can be achieved.

-   Accelerate accesses from different regions

    By using Global Traffic Manager, you can direct user accesses from different regions to different IP address pools, thus achieving grouped user management and grouped access and helping the application improve user experience.


## Deploy Global Traffic Manager {#section_zkj_hmc_wdb .section}

This tutorial takes aliyuntest.club as an example \(most users of the website are in Singapore and China\) to show how to achieve global load balancing through global traffic management and load balancing.

## Step 1 Purchase and configure ECS instances {#section_kcf_wcv_y2b .section}

Purchase and configure at least two ECS instances in each region where the users of the application of the application service are located.

In this tutorial, two ECS instances are purchased in Beijing, Shenzhen and Shanghai separately, and a simple static web page is built on each ECS instance.

-   Example of ECS instances in the Beijing region
-   Example of ECS instances in the Shenzhen region
-   Example of ECS instances in the Singapore region

## Step 2 Purchase and configure Server Load Balancing instances {#section_u35_ypc_wdb .section}

1.  Refer to [Create an SLB instance](reseller.en-US/User Guide (New Console)/Server Load Balancer instance/Create an SLB instance.md#) to create three Internet Server Load Balancing instances in Beijing, Shenzhen and Singapore separately.
2.  Refer to [Configure an SLB instance](../../../../reseller.en-US/Quick Start (New Console)/Configure an SLB instance.md#) to add listeners and add configured ECS instances to backend server pools.

-   Example of the SLB instance in the Beijing region
-   Example of the SLB instance in the Shenzhen region
-   Example of the SLB instance in the Singapore region

## Step 3 Configure Global Traffic Manager {#section_fkw_drc_wdb .section}

1.  Purchase a Global Traffic Manager instance.
    1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/#/dns/domainList).
    2.  In the left-side navigation pane, click **Global Traffic Manager**.
    3.  On the Global Traffic Manager page, click **Create Instance**.
    4.  Select the version, purchase quantity and service time.
    5.  Click **Buy now**.

        After the instance is successfully purchased, the system automatically allocates a CNAME access domain name.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15689/153829268210621_en-US.png)

2.  Configure the Global Traffic Manager instance.
    1.  On the Global Traffic Manager page, click the ID of the Global Traffic Manager instance or click **Configure** in the **Actions** column.
    2.  In the left-side navigation pane, click **Configurations**.
    3.  In the Global Settings tab, click **Edit** to configure the parameters of the Global Traffic Manager instance.

        Configure the following parameters and use the default values for the remaining options.

        -   Instance Name: Used for identifying the instance used for a certain application and can be customized.
        -   Primary Domain: The primary domain name is used by you to access the application. In this tutorial, enter aliyuntest.club.
        -   Alert Group: When the global traffic management generates abnormal sound, the message sender is notified and the alert contact groups you create in CloudMonitor are automatically obtained.
    4.  Click **Confirm**.
3.  Configure the IP address pool.
    1.  In the IP Address Pool Configurations tab, click **Create Address Pool**.
    2.  On the Create Address Pool page, configure the IP address pool.

        In this tutorial, three IP address pools are to be added and each IP address pool accommodates one of the three SLB addresses in different regions.

        -   Address Pool Name: Custom. For example, China North\_Beijing, China East\_Hanghou, Singapore.
        -   Address: The SLB public IP address to be added to this region.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15689/153829268210664_en-US.png)

    3.  Click **Confirm**.
4.  Configure health check

    In this operation, you need to configure health check for the three address pools separately.

    1.  In the Address Pool tab, click **Edit** next to health check.
    2.  Configure health check parameters.

        **Monitoring Node** shows the locations of monitoring nodes. Select the monitoring node according to the region of the address pool.

5.  Configure the access policy.

    In this tutorial, add different access policies for the three different regions.

    1.  In the Access Policy tab, click **Add Access Policy**.
    2.  On the Add Access Policy tab, configure the access policy.
        -   Configure the corresponding default address pools for different access regions, and set an address pool of another region as the failover address pool.
        -   Select the access region. When users in this region access the application, the address pool configured in the access policy is matched.

            There must be an access policy with **Global** selected. Otherwise some areas cannot access the application.

6.  Configure CNAME access.
    1.  Log on to the Alibaba Cloud DNS console.
    2.  Find the domain name aliyuntest.club and click **Configure** in the **Actions** column.
    3.  On the DNS Settings page, click **Add Record**.
    4.  On the Add Record page, direct the domain name aliyuntest.club accessed by end users to the alias record of the Global Traffic Manager instance in the form of CNAME.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15689/153829268210688_en-US.png)

    5.  Click **Confirm**.

## Step 4 test {#section_sxj_ntc_wdb .section}

Remove the ECS instances of the SLB instance in the Beijing region so as that the SLB service is unavailable.

Visit the website to see if the access is normal.

**Note:** It takes one to two minutes for Global Traffic Manager to make judgement after it monitors that your IP is down. If you set the monitoring frequency to 1 minute, it takes two to three minutes for the link switching caused by exceptions to take effect.

