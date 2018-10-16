# Add an HTTPS listener {#concept_dy4_2pn_42b .concept}

It is applicable to applications requiring encrypted transmission. You can add an HTTPS listener to forward requests from the HTTPS protocol.

## Prerequisites {#section_tx3_vqn_42b .section}

[Create an SLB instance](intl.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#).

## Step 1 Open the listener configuration wizard {#section_wx3_5qn_42b .section}

To open the listener configuration wizard, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, select **Instances** \> **Server Load Balancer**.
3.  Select a region.
4.  Select one of the following methods to open the listener configuration wizard:
    -   On the Server Load Balancer page, find the target instance and then click **Configure Listener**.
    -   On the Server Load Balancer page, click the ID of the target SLB instance. On the Listeners page, click **Add Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15396723467399_en-US.png)


## Step 2 Configure a UDP listener {#section_ly4_2pn_42b .section}

To configure a TCP listener, complete these steps:

1.  On the Protocol and Listenerpage, configure the HTTPS listener according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**Select Listener Protocol**|Select the protocol type of the listener.In this tutorial, select **HTTPS**.

|
    |**Listening Port**|The listening port used to receive requests and forward the requests to backend servers.The port number is in the range of 1-65535.

**Note:** The listening ports must be unique in a Server Load Balancer instance.

|
    |**Advanced configurations**|
    |**Scheduling Algorithm**|Server Load Balancer supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).    -   **Weighted Round-Robin \(WRR\)** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to the backend servers.
    -   **Weighted Least Connections \(WLC\)**: A server with a higher weight will receive a larger percentage of live connections at any one time. When the weight value is the same, a backend server with a smaller number of connections is more frequently \(and probably\) accessed.
|
    |**Enable Session Persistence**| Select whether to enable session persistence.

 If session persistence is enabled, all session requests from the same client are sent to the same backend server.

 HTTP session persistence is based on cookies. The following two methods are supported:

     -   **Insert cookie**: You only need to specify the cookie timeout period.

SLB adds a cookie to the first response from the backend server \(insert SERVERID in the HTTP/HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.

    -   **Rewrite cookie**: You can set the cookie to insert to the HTTP/HTTPS response according to your needs. You must maintain the timeout period and lifecycle of the cookie on the backend server.

SLB will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the recorded backend server. For more information, see [Session persistence](../../../../intl.en-US/Miscellaneous/Best practices/Configure cookie in the backend server.md#).

 |
    |**Enable HTTP2.0**|Select whether to enable HTTP 2.0.|
    |**Enable Access Control**|Select whether to enable the access control function.|
    |**Access Control Method**| Select an access control method after enabling the access control function:

     -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks.  After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If blacklist access is on, but no IP is added to the access policy group, the load balancing listen forwards all requests.

 |
    |**Access Control List**|Select an access control list as the whitelist or the blacklist.**Note:** An IPv6 instance can only bind IPv6 access control lists and an IPv4 instance can only bind IPv4 access control lists. For more information, see [Configure an access control list](intl.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).

|
    |**Enable Peak Bandwidth Limit**| Select whether to configure the listening bandwidth.

 If the SLB instance is billed by bandwidth, you can set different peak bandwidths for different listeners to limit the traffic passing through the listeners. The sum of the peak bandwidths of all listeners under an instance cannot exceed the bandwidth of that instance.

 By default, all listeners share the bandwidth of the SLB instance.

 **Note:** Instances billed by traffic have no bandwidth peak limit by default.

 |
    |**Idle Timeout**|Specify the idle connection timeout in seconds. Valid value: 1-60If no request is received during the specified timeout period, Server Load Balancer will close the connection and restart the connection when the next request comes.

This function is available in all regions.

|
    |**Request Timeout**|Specify the request timeout in seconds. Valid value: 1-180If no response is received from the backend server during the specified timeout period, Server Load Balancer will stop waiting and send an HTTP 504 error code to the client.

This function is available in all regions.

|
    |**TLS Security Policy**| Only guaranteed-performance instances support selecting the TLS security policy to use.

 The TLS security policy contains available TLS protocol versions and supporting encryption algorithm suites. For more information, see [Support TLS security policy](intl.en-US/User Guide/Listeners/Support TLS security policy.md#).

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

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153967234611858_en-US.png)

2.  Click **Next**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153967234610035_en-US.png)


## Step 3 Configure the SSL certificate {#section_m52_pxn_42b .section}

To add an HTTPS listener, you must upload a server certificate or CA certificate, as shown in the following table.

|Certificate|Description|Required for one-way authentication|Required for mutual authentication|
|:----------|:----------|:----------------------------------|:---------------------------------|
|Server certificate|Used to identify a server.The client uses it to check whether the certificate sent by the server is issued by a trusted center.

|YesThe server certificate must be uploaded to the certificate management system of the Server Load Balancer.

|YesUpload the server certificate to SLB.

|
|Client certificate|Used to identify a client.The client user can prove its true identity when communicating with the server. You can sign a client certificate with a self-signed CA certificate.

|No|YesInstall the client certificate on the client.

|
|CA certificate|The server uses the CA certificate to authenticate the signature on the client certificate, as part of the authorization before launching a secure connection. If the authentication fails, the connection will be rejected.|No|YesThe server certificate must be uploaded to the certificate management system of the Server Load Balancer.

|

Note the following before uploading certificates:

-   The uploaded certificate must be in the PEM format. For more information, see [Certificate requirements](intl.en-US/User Guide/Certificate management/Certificate requirements.md#). 
-   After the certificate is uploaded to SLB, SLB can manage the certificate and you do not need to bind the certificate on backend ECS instances.
-   It usually takes one to three minutes to activate the HTTPS listener because the uploading, loading, and validation of certificates take some time. Normally it takes effect in one minute and it will definitely take effect in three minutes.
-   The ECDHE algorithm cluster used by HTTPS listeners supports forward secrecy, but does not support uploading security enhancement parameter files required by the DHE algorithm cluster, such as strings containing the `BEGIN DH PARAMETERS` field in the PEM certificate file. For more information, see [Certificate formats](intl.en-US/Archives/User Guide (Old Console)/Certificate management/Certificate requirements.md#).
-   Currently, Server Load Balancer HTTPS listeners do not support SNI \(Server Name Indication\). You can use TCP listeners instead, and then configure SNI on the backend ECS instances.
-   The session ticket retention time of HTTPS listeners is 300 seconds.
-   The actual amount of traffic is larger than the billed traffic amount because some traffic is used for the protocol handshaking.
-   In the case of a large number of new connections, HTTPS listeners consume more traffic.

To configure the SSL certificate, complete these steps:

1.  Select the server certificate that has been uploaded, or click **Create Server Certificate** to upload a server certificate.

    For more information, see [Upload a certificate](intl.en-US/User Guide/Certificate management/Upload a certificate.md#). 

2.  If you want to enable HTTPS mutual authentication, click **Modify** and enable mutual authentication.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/15396723469566_en-US.png)

3.  Select an uploaded CA certificate, or click **Create CA Certificate** to upload a CA certificate.

    You can use a self-signed CA certificate. For more information, see [Generate a CA certificate](intl.en-US/User Guide/Certificate management/Generate a CA certificate.md#).


## Step 4 Add backend servers {#section_vqk_zmn_42b .section}

Add backend servers to process requests. You can use the default server group configured for the instance, or configure a VServer group or an active/standby server group for the listener. For more information, see [Backend server overview](intl.en-US/User Guide/Backend servers/Backend server overview.md#). 

In this tutorial, the default server group is used:

1.  Select **Default Server Group** and then click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153967234610036_en-US.png)

2.  Select the ECS instances to add and then click **Add to Selected Server List**. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15396723467499_en-US.png)

3.  Configure the ports and weights of the added backend servers.
    -   Port

        The port opened on the backend server \(ECS instance\) to receive requests. The port number is in the range of 1-65535. Ports of backend servers can be the same in an SLB instance.

    -   Weight

        The weight of the backend server \(ECS instance\). An ECS instance with a higher weight will receive a larger number of connection requests.

        **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15396723477504_en-US.png)

4.  Click **Next**.

## Step 5 Configure health check {#section_oj3_mnn_42b .section}

Server Load Balancer checks the service availability of the backend servers \(ECS instances\) by performing health checks. The health check function improves the overall availability of your services and avoids the impact of backend server failures. Click **Modify** to change health check configurations. For more information, see [Configure health check](intl.en-US/User Guide/Health check/Configure health check.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153967234710037_en-US.png)

## Step 6 Submit the configurations {#section_hwm_qnn_42b .section}

To confirm the listener configurations, complete these steps:

1.  On the Submit page, check listener configurations. You can click **Modify** the change the configurations. Click **Submit**.
2.  On the Submit page, click **OK** after the configurations are successful.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153967234710038_en-US.png)


After the configurations are successful, you can view the created listener on the listeners page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153967234710039_en-US.png)

## Related operations {#section_pz4_2pn_42b .section}

-   [Configure health check](intl.en-US/User Guide/Health check/Configure health check.md#)
-   [Manage a default server group](intl.en-US/User Guide/Backend servers/Manage a default server group.md#)
-   [Manage a VServer group](intl.en-US/User Guide/Backend servers/Manage a VServer group.md#)
-   [Manage an active/standby server group](intl.en-US/User Guide/Backend servers/Manage an active__standby server group.md#)
-   [Generate a CA certificate](intl.en-US/User Guide/Certificate management/Generate a CA certificate.md#)
-   [Upload a certificate](intl.en-US/User Guide/Certificate management/Upload a certificate.md#)
-   [Configure access control](intl.en-US/User Guide/Access control/Configure access control.md#)
-   [Add domain-name based or URL-based forwarding rules](intl.en-US/Tutorials/Traffic forwarding based on domain name or URL.md#)
-   [Manage a domain name extension](intl.en-US/User Guide/Listeners/Manage a domain name extension.md#)

