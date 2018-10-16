# Cannot access Server Load Balancer {#concept_wzy_kyc_xdb .concept}

When the client cannot access Server Load Balancer, the possible causes and resolutions are as follows:

1.  If you haven't added any listener after creating a SLB instance, you can't ping the endpoint of the SLB instance at this moment.

    解决方案：配置监听，详情查看[配置监听](../../../../reseller.en-US/Archives/User Guide (Old Console)/Listener/Listeners overview.md#)。

2.  Four-tier Load Balancing back-end Linux The ECS kernel is configured incorrectly.

    An ECS instance of a Linux system added by a four-tier Load Balancing back-end must be turned off for its rrochelle filter feature in the Linux kernel. Otherwise, you may not be able to access the load balancing service addresses from the client by using telnet, but the health check is normal.

    Linux's rp\_filter feature is used to implement reverse filtering \(I .e., urpf \). It verifies the flow of reverse packets to avoid IP fake attacks. However, this feature may conflict with the policy route for load balancing the underlying LVS, cause an exception in the access.

    Solution: ensure that the system configuration file for the back-end ECs instance has a value of 0 for the following three parameters. 编辑`/etc/sysctl.conf`后，执行`sysctl -p`使配置生效。

    ```
     net.ipv4.conf.default.rp_filter = 0
     net.ipv4.conf.all.rp_filter = 0
     net.ipv4.conf.eth0.rp_filter = 0
    ```

3.  4-tier Load Balancing back windows The ECS parameter is configured incorrectly.

    For four-tier load balancing service, load Balancing back-end ECs instances are currently not supported, and services are provided directly to clients at the same time, as a back-end server for your load balancing.

    This may probably result in the situation that relevant access requests are forwarded to the same ECS, which may cause a data access loop and access failure of the Server Load Balancer service by the corresponding ECS.

    Solutions:

    1.  Install Windows Loop Network Card: Right-click**Computer** \> **Attribute** . On the Control Panel home page, click**Device Manager** \> **Add hardware** \> **Install the hardware that I manually select from the list** \> **Show all devices** , Select the device shown in the following figure for installation.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4298/15396829873341_en-US.png)

    2.  Enable weak host Model, perform the following command to view idx for all network interfaces.

        ```
        netsh interface ipv4 show interface
        ```

    3.  将所有网络接口分别设置`weakhostsend=enabled`, `weakhostsend=enabled`。 比如设置Idx为12的网卡：

        ```
        netsh interface ipv4 set interface 12 weakhostsend=enabled
        netsh interface ipv4 set interface 12 weakhostreceive=enabled
        ```

4.  Abnormal local network of the client or abnormal intermediate link of ISP.

    For the Server Load Balancer service for the public network, abnormality in client network or abnormality in ISP's network between the client and Server Load Balancer may also lead to the access failure of Server Load Balancer from the client.

    Methods of troubleshooting: from different regions and different network environments, do an access test on the Load Balancing appropriate service port. If there is an exception only when it is accessed by the local network, it is determined that the problem is caused by a network exception, at this point, you can continue to do further troubleshooting and analysis through ongoing Ping tests or MTR routing traces.

5.  Client IP address is intercepted by Alibaba Cloud Security.

    For the Server Load Balancer service for the public network, if the client network is a shared network \(all LAN servers share the Internet using a limited number of public IPs\). Meanwhile, certain servers within the local network launch malicious attacks such as continuous scanning against IP addresses of relevant Alibaba Cloud services due to some factors such as being infected by viruses.

    Solution: To solve this problem, you can see the following steps and add the public IPs of the local network into the access whitelist of Server Load Balancer:

    1.  在客户端网络环境下访问http://ip.taobao.com，获取客户端网络环境对应的公网IP。
    2.  Add the obtained IP address into the whitelist. This operation permits all accesses from the corresponding IP address to the Server Load Balancer.

        **Note:** This operation may pose a security risk, ensure that the IP in the whiteable list does not maliciously attack the load balancing.

    If the problem isn't solved, you can provide the following information when submitting a ticket so that we can help you solve the problem more efficiently:

    -   - ID of SLB instance or IP address of Server Load Balancer.
    -   - The public IP corresponding to the public network client acquired by visiting ip.taobao.com.
    -   - Screenshots of long-time ping and MTR route tracking tests of Server Load Balancer IP implemented on public network client.

