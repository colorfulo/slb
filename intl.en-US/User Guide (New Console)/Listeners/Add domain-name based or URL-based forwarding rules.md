# Add domain-name based or URL-based forwarding rules {#concept_sh5_nj5_vdb .concept}

SLB supports configuring domain-name based or URL based forwarding rules. You can forward requests with different domain names or URLs to different backend servers by adding forwarding rules so as to well allocate server resources.

**Note:** Only HTTP and HTTPS listeners support configuring forwarding rules.

## Introduction to domain-name based or URL-based forwarding rules {#section_hll_n31_wdb .section}

Layer-7 listeners support configuring domain-name based or URL-based forwarding rules to distribute requests with different domain names or URLs to different ECS instances.

URL-based forwarding rules support string matching and adopt sequential matching, such as /admin, /bbs, and /test.

Domain name forwarding rules support exact match and wildcard match:

-   Exact domain name: www.aliyun.com
-   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

    When a request matches multiple forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table.

    |Type| Request URL|Domain name based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
    |:---|:-----------|:--------------------------------|
    |:-------------|:------------|:-------------------|
    |Exact match|www.aliyun.com|✓|×|×|
    |Wildcard match|Market.aliyun.com|×|✓|×|
    |Wildcard match|info.market.aliyun.com|×|×|✓|


You can add different forwarding rules associated with different VServer groups to a Layer-7 listener \(A VServer group consists of multiple ECS instances\). For example, you can forward all read requests to a group of backend servers and forward all write requests to another group of backend servers to optimize resource usage.

After forwarding rules are configured, the sequence of request forwarding is as follows:

-   If the requests match a forwarding rule, the requests are distributed to the VServer group associated with the rule.
-   If not, but the listener is associated with a VServer group, the requests are distributed to the VServer group configured in the listener.
-   If none of the above conditions are met, the requests are forwarded to ECS instances in the default server group.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/15368930062798_en-US.png)

## Add a domain-name based or URL-based forwarding rule {#section_z1n_t1b_wdb .section}

Before adding the forwarding rule, make sure that the following conditions are met:

-   [Add an HTTP listener](reseller.en-US/User Guide (New Console)/Listeners/Add an HTTP listener.md#) or  [Add an HTTPS listener](reseller.en-US/User Guide (New Console)/Listeners/Add an HTTPS listener.md#).
-   [Manage a VServer group](reseller.en-US/User Guide (New Console)/Backend servers/Manage a VServer group.md#).

To add a domain-name based or URL-based forwarding rule, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region and all SLB instance in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target HTTP/HTTPS listener and then click the **Add Forwarding Rules** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15368930067453_en-US.png)

6.  On the Add Forwarding Rules page, click **Add Forwarding Rules**.
7.  On the Add Forwarding Rules page, configure the forwarding rule according to the following information:

    1.  **Domain Name**: Enter the domain name of the request. It can only contain letters, numbers, dashes, or dots.
    2.  **URL**: Enter the path of the request. The URL must start with a slash \(/\), and can only contain letters, numbers, and the following special characters \(-. /%? \#&\).

        **Note:** If you only want to configure a domain name based forwarding rule, leave the URL option empty.

    3.  **VServer Group**: Select the associated VServer group.
    4.  **Description \(optional\)**: Enter the description.
    5.  Click **OK**.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15368930067463_en-US.png)

8.  Click **Add Domain** or **Add Rule** to add another domain name based or URL based forwarding rule.

    You can add up to 20 forwarding rules to an HTTP or HTTPS listener.


## Edit a forwarding rule {#section_gpm_gv4_42b .section}

You can change backend servers associated with the forwarding rule.

To edit a forwarding rule, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region and all SLB instance in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target Layer-7 listener and then click the **Add Forwarding Rules** option.
6.  In the **Forwarding Rules** area, find the target forwarding rule and then click the **Edit** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15368930067464_en-US.png)

7.  Select a new VServer group to be associated with the forwarding rule, and then click **OK**.

## Delete a forwarding rule {#section_wsy_cw4_42b .section}

To delete a forwarding rule, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region and all SLB instance in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target Layer-7 listener, and then click the **Add Forwarding Rules** option.
6.  In the **Forwarding Rules** area, find the target forwarding rule and then click the **Delete** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15368930067465_en-US.png)


