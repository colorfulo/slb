# Heath check FAQ {#concept_zx3_fh5_vdb .concept}

## 1. How does Server Load Balancer \(SLB\) health check work? {#section_m43_1qx_wdb .section}

SLB checks the service availability of the backend servers \(ECS instances\) by performing health checks on the backend servers. When SLB determines that an instance is unhealthy, it stops distributing requests to that instance. Distributions will resume to that instance when it becomes healthy again.

As shown in the following figure, the node servers in the LVS cluster and Tengine cluster perform the data forwarding and health check at the same time. The IP address range used by the health check of SLB is 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \). If the backend ECS instance enables access control such as iptables, you need to allow the access of 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \) on the intranet NIC.

For more information, see [Health check overview](../reseller.en-US/Archives/User Guide (Old Console)/Listener/Health check/Health check overview.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15398329203226_en-US.png)

## 2. What are recommended configurations for health check? {#section_jhf_jqx_wdb .section}

However, to avoid the impact of switching caused by frequent health check failures on the system availability, status is switched \(health check succeeded or failed\) only when the health check continuously succeeds or fails for multiple times in the time window. For more information, see [Health check configurations](../reseller.en-US/Archives/User Guide (Old Console)/Listener/Health check/Health check configurations.md#).

The following are recommended health check configurations for TCP/HTTP/HTTPS listeners.

|Configuration|Recommended value|
|:------------|:----------------|
|**Response timeout**|5 seconds|
|**Health check interval**|2 seconds|
|**Unhealthy threshold**|3|

The following are recommended health check configurations for UDP listeners.

|Configuration|Recommended value|
|:------------|:----------------|
|**Response timeout**|10 seconds|
|**Health check interval**|5 seconds|
|**Unhealthy threshold**|3|
|**Healthy threshold**|3|

**Note:** These configurations are conducive to restoring the service when the health check of a backend server fails. If you have higher requirements, you can specify a lower response timeout value but make sure the processing time in the normal status is less than the specified timeout value.

## 3. Can I disable the health check? {#section_tn3_sqx_wdb .section}

You can only disable health check for HTTP and HTTPS listeners. The health check of UDP and TCP listeners cannot be disabled. For more information, see [Close health check](../reseller.en-US/Archives/User Guide (Old Console)/Listener/Health check/Close health check.md#).

**Note:** When health check is disabled, requests may be distributed to unhealthy ECS instances, which can lead to service interruption. We do not recommend disabling health check.

## 4. How to choose a health check method for TCP listeners? {#section_un3_sqx_wdb .section}

For TCP listeners, both the TCP health check and HTTP health check are supported:

-   Based on network Layer detection, TCP health check uses the traditional three-way handshakes to determine if the backend ECS instance is healthy or not.
-   HTTP health check detects the health status by sending head requests. A Tengine node server sends an HTTP head request and compares the returned code to determine if the backend ECS instance is healthy or not.

The TCP health check minimally impacts performance and consumes less resources on the backend ECS instances. Choose TCP health check if the traffic load on the backend ECS instance is large, and choose HTTP health check if not.

## 5. Is there any impact on health check if the weight for an ECS instance is zero? {#section_wn3_sqx_wdb .section}

In this situation, SLB will no longer forward traffic to this ECS instance and the health check will indicate abnormal for the Layer-4 listeners, while the health check is normal for Layer-7 listeners.

Setting the weight value to zero is equal to manually removing the ECS instance from Server Load Balancer. The weight is set to zero only when restarting, adjusting, or maintaining the ECS instance.

## 6. What method does HTTP listeners use to do health check on backend ECS instances? {#section_xn3_sqx_wdb .section}

HEAD method

If the backend ECS instances disable the HEAD method access, health check on the backend ECS instances will fail. We recommend you access your own IP address using the HEAD method on the ECS instance for testing:

```
echo -e “HEAD /test.html HTTP/1.0\r\n\r\n” | nc -t LAN_IP port
```

## 7. What are the IP address ranges that HTTP listeners use to perform health check on backend ECS instances? {#section_yn3_sqx_wdb .section}

The IP address range used by the health check of SLB is 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \). If the backend ECS instance enables access control such as iptables, you need to allow the access of 100.64.0.0/10 on the intranet NIC.

## 8. Why is the health check frequency displayed on the console different from that recorded in the web logs? {#section_zn3_sqx_wdb .section}

Health check is performed in the cluster to avoid single points of failure. Therefore, the health check frequency recorded in the logs is different from the frequency configured in the console.

## 9. How to troubleshoot the 502 Bad Gateway error? {#section_a43_sqx_wdb .section}

Symptoms:

The 502 Bad Gateway error occurred when accessing the SLB service and the health status of the backend servers is indicated abnormal.  However, the ECS instance can be accessed from the intranet and the port 80 listening is normal although a 404 error is reported in the web logs.

Cause:

The page used for health check does not exist.

Solution:

Modify the health check configurations accordingly.

## 10. Does health check consume system resources? {#section_b43_sqx_wdb .section}

HTTP health checks consume few resources of the backend ECS instances.

## 11. Why do backend servers of the Server Load Balancer frequently receive requests with a UA of KeepAliveClient? {#section_c43_sqx_wdb .section}

Symptoms:

The backend ECS instances frequently receive GET requests from an intranet IP even if there is no user access, and User-Agent is KeepAliveClient.

Cause:

The listener uses TCP protocol but the health check uses HTTP protocol. In this situation, SLB uses the GET method instead of the HEAD method to do the health check.

Solution:

Use the same protocol for the listener and corresponding health check.

## 12. How to handle health check failure caused by a backend database fault? {#section_d43_sqx_wdb .section}

Symptoms:

Two web sites are configured on an ECS instance. The website www.test.com is a static website, and the website app.test.com is a dynamic website. A 502 error occurred when accessing www.test.com due to a backend database fault.

Cause:

Domain name app.test.com is configured for health check. RDS or self-built database failure causes the access error to app.test.com, so the health check fails.

Solution:

Configure the domain name used for health check to www.test.com.

## 13. Why a network connection exception is displayed in the backend service logs but TCP health check is successful? { .section}

Symptoms:

After configuring the backend TCP port in a SLB listener, a network connection exception is frequently shown in the backend service logs. The requests are sent from the SLB instance and the SLB instance also sends RST packets to the backend server at the same time.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15398329213231_en-US.jpg)

Cause:

The problem is related to the health check mechanism.

TCP is transparent to the upper-Layer applications and is utilized to reduce the cost of health check and the impact on backend service. TCP health check only performs a simple three-way handshake and then directly sends RST packets to terminate the TCP connection. The data exchange process is as follows:

1.  The SLB instance sends a SYN packet to the backend port.
2.  The backend server replies with a SYN-ACK if the backend port is in normal status.
3.  After successfully receiving the response from the backend port, the SLB instance considers that the port is in normal status and the status of the backend server is normal.
4.  The SLB instance sends a RST packet to the backend port to actively terminate the connection. For now, health check is completed.

After the health check succeeds, the SLB instance directly sends RST packets to terminate the connection and no data is sent afterwards. Therefore, upper-Layer services \(such as Java connection pool\) deem that the connection is abnormal and errors such as `Connection reset by peer` are displayed.

Solution:

-   Use HTTP protocol instead.
-   In the service layer, filter the logs from the SLB IP address range and ignore related error messages.

## 14. Why the health check status is abnormal when the service is actually normal? {#section_ldb_5sx_wdb .section}

Symptoms:

The HTTP health check always fails, but the status code obtained by performing the `curl -I` test is normal as follows:

```
echo -e ‘HEAD /test.html HTTP/1.0\r\n\r\n’ | nc -t 192.168.0.1 80
```

Cause:

If the returned status code is different from the normal status code configured on the console, the backend ECS instance is declared as unhealthy. For example, if the configured normal status code is http\_2xx, all other status codes returned not matching this status code will be considered as health check failure.

No error occurred when a curl test is performed on the Tengine/Nginx cluster, but a 404 error occurred in the test.html test file because the default site is used in the echo test.

Resolution:

-   Modify the main configuration file and annotate the default site.
-   Add the domain name used for health check in the health check configurations.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15398329213234_en-US.jpg)

## 15. How to troubleshoot health check exceptions? {#section_fjj_ttx_wdb .section}

Follow these steps to troubleshoot health check exceptions:

1.  Check if the backend ECS instance can provide services normally. If HTTP health check is configured, make sure that the returned status code is the same with the normal status code configured on the console.
2.  Because the health check is performed on backend ECS instances through the intranet, log on to the backend ECS instance and check if the application port is listening on an intranet IP. If not, change the listening port to an intranet IP.
3.  Make sure the next hop for 10.0.0.0/8, 100.64.0.0/10, and 11.0.0.0/8 on the ECS instance is set to the intranet gateway. If the ECS instance only has an intranet IP, guarantee the default route \(0.0.0.0/0\) points to the intranet gateway.

    Configure the route as follows:

    -   Windows: Log on to the ECS instance. Download [Windows route adding tool](http://ecsimagetools.oss-cn-hangzhou.aliyuncs.com/windows_add_routes.bat) and double click it to add route configurations.
    -   Linux: Log on to the ECS instance, download the [Linux route adding tool](http://ecsimagetools.oss-cn-hangzhou.aliyuncs.com/linux_add_routes.sh) and run the `bash linux_add_routes.sh` command.
    -   FreeBSD: Log on to the ECS instance, download the [FreeBSD route adding tool](http://ecsimagetools.oss-cn-hangzhou.aliyuncs.com/freebsd_add_routes.sh) and run the `bash freebsd_add_routes.sh` command.

        After you run the route adding tool, the intranet route is displayed as normal, as shown in the figure below.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15398329213241_en-US.png)

4.  Ensure the backend port you configured in the listener is opened on the backend server.
5.  Check if the weight value of the backend ECS instance is zero. If so, the health check status is abnormal.
6.  Check if there is a firewall or other security software in the backend ECS instance. This kind of software could mask the local IP address of the SLB system so as that the system cannot communication with the backend ECS instance. We recommend closing the firewall or uninstalling the security software to perform a test.
7.  Check whether the response time of the backend ECS instance exceeds the response timeout of health check.

    Run the following command to view the response time of the Layer-4 health check.

    ```
    time telnet <SLB IP address> <SLB Port>
    ```

    Run the following command to view the response time of the Layer-7 health check.

    ```
    time echo -e ‘HEAD <Check path of health check> HTTP/1.0\r\n\r\n’|nc -t <Port>
    ```

    **Note:** Run this command on another ECS instance in the same account and region. For example, the check path of health check is /, the intranet IP of the ECS instance is 192.168.0.1, and the port number is 80, use the following command:  `time echo -e ‘HEAD / HTTP/1.0\r\n\r\n’ | nc -t 192.168.0.1 80.`

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15398329213246_en-US.png)

    When the value of the real parameter in the result exceeds the response timeout, the backend ECS instance is declared as unhealthy.

    Solution:

    -   Optimize the application or program to reduce the response time.
    -   Increase the response timeout value set in the listener check.
8.  For the Layer-7 health check, run `echo -e “HEAD /test.html HTTP/1.0\r\n\r\n” |nc -t LAN_IP 80` to check if the returned value is 2XX or 3XX.

    **Note:** /test.html is the check path of health check. Change it as needed.

9.  Check if the traffic load on the backend ECS instance is too heavy, which leads to over long response timeout.
10. We recommend using HTML static file to perform health check. The file is used only for checking the returned result. We do not recommend using dynamic scripting languages such as PHP.

