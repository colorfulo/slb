# ECS instance exception troubleshooting {#concept_u5c_f2d_xdb .concept}

After you turn on health check in the load balancing service, when there is a problem with a back-end ECs health check, the request is forwarded to the other health check normal ECS. When the ECS is restored to normal operation, load Balancing automatically restores it to external or internal services.

For the seven-tier load balancing service, when you listen for information about health check exceptions, you can troubleshoot the ECS instance from the following aspects:

-   First, make sure you can access your application service through ECS directly.
-   Make sure that the backend server has enabled the corresponding port which must be consistent with the one you configured in your Server Load Balancer listening configuration.
-   \* Check whether the backend ECS has a firewall or other security protection software. This type of software may easily block the local IP address of the Server Load Balancer system, and thus disable the communication between the Server Load Balancer system and the backend server.
-   \* Check whether the Server Load Balancer health check parameters are correctly set. It is recommended to keep the default values.
-   Static page is recommended for health check. If the page you use for health check isn't the default homepage on backend ECS application server, you have to designate its URL in the health check configuration. It is recommended that simple pages in the form of html are designated for health check. It’s only used to check the return results. Dynamic scripting language like php isn’t recommended.
-   Check whether the backend ECS resources have a high load. A high load will cause slow response in offering services.

In addition, due to the communication between the seven-tier load balancing service and the back-end ECs via the internal network, as a result, ECs is required to listen to the internal network or the full network port. You can check using the following methods:

1.  Checks whether the listen function is normal.

    If SLB frontend port is 80 and ECS backend port is 80, the ECS intranet IP is 10.11.192.1. Run the following command on the server if you can see the monitoring information for 10.1.1.19292.1: 80, or 0.5.0.0: the monitoring information of 80 indicates that the monitoring of this part of the port is normal.

    -   Windows 服务器上运行：`netstat -ano | findstr :80`
    -   Linux 服务器上运行：`netstat -anp | grep :80`
2.  Check whether the server intranet firewall allows port 80. Firewall can be closed temporarily for testing. Enter the following command to close the firewall.
    -   Windows：`firewall.cpl`
    -   Linux：`/etc/init.d/iptables stop`
3.  Check that the back-end port is fine.
    -   For four-tier load balancing, it is normal to use Telnet to test your response. 本例中使用`telnet 10.11.192.1 80`来测试。
    -   For seven-tier load balancing, the HTTP status code needs to be 200 and so on, representing the normal status code, the test methods are as follows:
        -   Windows：直接在ECS上访问ECS的内网IP测试是否正常，本例中为：[http://10.11.192.1](http://10.11.192.1/) 。
        -   Linux：使用`curl -I`命令查看状态是否为 HTTP/1.1 200 OK，本例是：`curl -I 10.11.192.1`。

