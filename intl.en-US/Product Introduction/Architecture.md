# Architecture {#concept_ivd_np4_tdb .concept}

Server Load Balancer is deployed in clusters. The cluster deployment model eliminates Single Point of Failures of backend servers, improves redundancy and increases service stability.

Alibaba Cloud provides Layer-4 \(TCP protocol and UDP protocol\) and Layer-7 \(HTTP protocol and HTTPS protocol\) load balancing services.

-   Layer 4 uses the open source software Linux Virtual Server \(LVS\) with Keepalived to achieve load balancing, and also makes some customization to it according to the cloud computing requirements.
-   Layer-7 SLB uses Tengine to achieve load balancing. Tengine is a Web server project launched by Taobao. Based on Nginx, it adds a wide range of advanced features dedicated for high-traffic websites.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4092/1538278647938_en-US.png)


As shown in the following figure, Layer-4 Server Load Balancer in each region is actually run in a cluster of multiple LVS machines. The cluster deployment model strengthens the availability, stability, and scalability of the load balancing services in abnormal circumstances.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4092/1538278648939_en-US.png)

Additionally, the LVS machine in the LVS cluster uses multicast packets to synchronize sessions to other LVS machines. As shown in the following figure, the session A established on LVS1 is synchronized to other LVS machines after three packets are transferred. In normal situations, the session request is sent to LVS1 as the solid line shows. If LVS1 is abnormal or being maintained, the session request will be sent to other normally working machines as the dotted line shows. Therefore, SLB clusters support hot upgrade, and machine failure or system maintenance will not affect your business.

**Note:** If a connection is not established \(three-way handshake is not completed\), or a connection has been established but the session synchronization is not triggered, the hot upgrade does not guarantee that the connection is not interrupted and the client needs to re-initiate the connection.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4092/1538278648941_en-US.png)

