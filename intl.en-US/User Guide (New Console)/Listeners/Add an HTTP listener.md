# Add an HTTP listener {#concept_dy4_2pn_42b .concept}

It is applicable to applications that need to recognize data contents, such as web applications and small-sized mobile games. You can add an HTTP listener to forward requests from the HTTP protocol.

## Prerequisites {#section_tx3_vqn_42b .section}

[Create an SLB instance](reseller.en-US/User Guide (New Console)/Server Load Balancer instance/Create an SLB instance.md#).

## Step 1 Open the listener configuration wizard {#section_wx3_5qn_42b .section}

To open the listener configuration wizard, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, select **Instances** \> **Server Load Balancer**.
3.  Select a region.
4.  Select one of the following methods to open the listener configuration wizard:
    -   On the Server Load Balancer page, find the target instance and then click **Configure Listener**.
    -   On the Server Load Balancer page, click the ID of the target SLB instance. On the Listeners page, click **Add Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15368365787399_en-US.png)


## Step 2 Configure an HTTP listener {#section_ly4_2pn_42b .section}

To configure a UDP listener, complete these steps:

1.  On the Protocol and Listener page, configure the HTTP listener according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**Select Listener Protocol**|Select the protocol type of the listener.In this tutorial, select **HTTP**.

|
    |**Listening Port**|The listening port used to receive requests and forward the requests to backend servers.The port number is in the range of 1-65535.

**Note:** The listening ports must be unique in a Server Load Balancer instance.

|
    |**Advanced configurations**|
    |**Scheduling Algorithm**|Server Load Balancer supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).    -   **Weighted Round-Robin \(WRR\)** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to the backend servers.
    -   **Weighted Least Connections \(WLC\)**: A server with a higher weight will receive a larger percentage of live connections at any one time. When the weight value is the same, a backend server with a smaller number of connections is more frequently \(and probably\) accessed.
|
    |**Redirection**|Select whether to forward traffic of the HTTP listener to an HTTPS listener.**Note:** If you enables listener forwarding, make sure that you have created an HTTPS listener.

|
    |**Session Persistence**| Select whether to enable session persistence.

 If session persistence is enabled, all session requests from the same client are sent to the same backend server.

 HTTP session persistence is based on cookies. The following two methods are supported:

     -   **Insert cookie**: You only need to specify the cookie timeout period.

SLB adds a cookie to the first response from the backend server \(insert SERVERID in the HTTP/HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.

    -   **Rewrite cookie**: You can set the cookie to insert to the HTTP/HTTPS response according to your needs. You must maintain the timeout period and lifecycle of the cookie on the backend server.

SLB will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the recorded backend server. For more information, see [Session persistence](../../../../reseller.en-US/Best Practices/Configure cookie in the backend server.md#).

 |
    |**Enable Access Control**|Select whether to enable the access control function.|
    |**Access Control Method**| Select an access control method after enabling the access control function:

     -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks.  After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.

 |
    |**Access Control List**|Select an access control list as the whitelist or the blacklist.**Note:** An IPv6 instance can only bind IPv6 access control lists and an IPv4 instance can only bind IPv4 access control lists. For more information, see [Configure an access control list](reseller.en-US/User Guide/Access control/Configure an access control list.md#).

|
    |**Enable Peak Bandwidth Limit**| Select whether to configure the listening bandwidth.

 If the SLB instance is billed by bandwidth, you can set different peak bandwidths for different listeners to limit the traffic passing through the listeners. The sum of the peak bandwidths of all listeners under an instance cannot exceed the bandwidth of that instance.

 By default, all listeners share the bandwidth of the SLB instance.

 **Note:** Instances billed by traffic have no peak bandwidth limit by default.

 |
    |**Idle Timeout**|Specify the idle connection timeout in seconds. Valid value: 1-60If no request is received during the specified timeout period, Server Load Balancer will close the connection and restart the connection when the next request comes.

This function is available in all regions.

|
    |**Request Timeout**|Specify the request timeout in seconds. Valid value: 1-180If no response is received from the backend server during the specified timeout period, Server Load Balancer will stop waiting and send an HTTP 504 error code to the client.

This function is available in all regions.

|
    |**Enable Gzip Compression**|Choose whether to enable Gzip compression to compress files of specific formats.Now Gzip supports the following file types: text/xml, text/plain, text/css, application/javascript, application/x-javascript application/rss+xml, application/atom+xml and application/xml.

|
    |**Add HTTP Header Fields**|Select the custom HTTP headers that you want to add:    -   Use the `X-Forwarded-For` field to retrieve the client source IP address.
    -   Use the `X-Forwarded-Proto` field to retrieve the listener protocol used by the SLB instance.
    -   Use the `SLB-IP` field to retrieve the public IP address of the SLB instance.
    -   Use the `SLB-ID` field to retrieve the ID of the SLB instance.
|
    |**Get Client Source IP Address**|HTTP listener uses X-Forwarded-For to obtain the real IP of the client.|
    |**Automatically Enable Listener After Creation**|Choose whether to enable listener after the listener is configured. The listener is enabled by default.|

2.  Click **Next**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15654/15368365797434_en-US.png)


## Step 3 Add backend servers {#section_ylm_3qn_42b .section}

Add backend servers to process requests. You can use the default server group configured for the instance, or configure a VServer group or an active/standby server group for the listener. For more information, see [Backend server overview](reseller.en-US/User Guide (New Console)/Backend servers/Backend server overview.md#). 

In this tutorial, the default server group is used:

1.  Select **Default Server Group** and then click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/153683657910030_en-US.png)

2.  Select the ECS instances to add and then click **Add to Selected Server List**. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15368365797499_en-US.png)

3.  Configure the ports and weights of the added backend servers.
    -   Port

        The port opened on the backend server \(ECS instance\) to receive requests. The port number is in the range of 1-65535. Ports of backend servers can be the same in an SLB instance.

    -   Weight

        The weight of the backend server \(ECS instance\). An ECS instance with a higher weight will receive a larger number of connection requests.

        **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15368365797504_en-US.png)

4.  Click **Next**.

## Step 4 Configure health check {#section_ay4_jqn_42b .section}

Server Load Balancer checks the service availability of the backend servers \(ECS instances\) by performing health checks. The health check function improves the overall availability of your services and avoids the impact of backend server failures. Click **Modify** to change health check configurations. For more information, see [Configure health check](reseller.en-US/User Guide (New Console)/Health check/Configure health check.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/153683657910032_en-US.png)

## Step 5 Submit the configurations {#section_ey5_lqn_42b .section}

To confirm the listener configurations, complete these steps:

1.  On the Submit page, check listener configurations. You can click **Modify** the change the configurations.
2.  Click **Submit**.
3.  On the Submit page, click **OK** after the configurations are successful.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/153683657910033_en-US.png)


After the configurations are successful, you can view the created listener on the Listeners page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/153683657910034_en-US.png)

## Related operations {#section_pz4_2pn_42b .section}

-   [Configure health check](reseller.en-US/User Guide (New Console)/Health check/Configure health check.md#)
-   [Manage a default server group](reseller.en-US/User Guide (New Console)/Backend servers/Manage a default server group.md#)
-   [Manage a VServer group](reseller.en-US/User Guide (New Console)/Backend servers/Manage a VServer group.md#)
-   [Manage an active/standby server group](reseller.en-US/User Guide (New Console)/Backend servers/Manage an active/standby server group.md#)
-   [Configure access control](reseller.en-US/User Guide (New Console)/Access control/Configure access control.md#)
-   [Add domain-name based or URL-based forwarding rules](reseller.en-US/User Guide (New Console)/Listeners/Add domain-name based or URL-based forwarding rules.md#)
-   [Manage a domain name extension](reseller.en-US/User Guide (New Console)/Listeners/Domain name extension (Beta)/Manage a domain name extension.md#)

