# Anti-DDoS Basic {#concept_qtj_cqn_vdb .concept}

You can view Alibaba Cloud Security thresholds of an Internet SLB instance on the SLB console.

## Introduction to Anti-DDoS Basic {#section_cnq_p3c_wdb .section}

Alibaba Cloud provides up to 5 Gbps basic anti-DDoS protection for SLB. As shown in the following figure, all traffic from the Internet must first go through Alibaba Cloud Security before arriving at SLB. Anti-DDoS Basic cleans and filters common DDoS attacks and protects your services against attacks such as SYN flood, UDP flood, ACK flood, ICMP flood, and DNS Query flood.

![](../DNSLB11827830/images/2870_en-US.jpeg)

Anti-DDoS Basic sets the cleaning threshold and blackholing threshold according to the bandwidth of the Internet SLB instance. When the inbound traffic reaches the threshold, the cleaning or blackholing is triggered:

-   Cleaning: When the attack traffic from the Internet exceeds the cleaning threshold or matches certain attack traffic model, Alibaba Cloud Security starts cleaning the attack traffic. The cleaning operation includes packet filtration, traffic speed limitation, packet speed limitation and so on.
-   Blackholing: When the attack traffic from the Internet exceeds the blackholing threshold, blackholing is triggered and all inbound traffic is dropped.

## View thresholds {#section_f35_ljc_wdb .section}

You can view the thresholds of an instance on the SLB console. If you cannot view the thresholds using a RAM account, ask your system administrator to grant the permission for you. For more information, see [Allow read-only access to Anti-DDoS Basic](#section_c4n_wjc_wdb).

To view thresholds, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region.
3.  Hover the mouse pointer to the DDoS icon next to the target instance to view the following thresholds. You can click the link to go to the DDoS console to view more information.
    -   Traffic Scrubbing Threshold \(bits/s\): When the inbound traffic exceeds the BPS cleaning threshold, cleaning is triggered.
    -   Traffic Scrubbing Threshold \(packets/s\): When the inbound packets exceed the PPS cleaning threshold, cleaning is triggered.
    -   Blackholing Threshold: When the inbound traffic exceeds the blackholing threshold, blackholing is triggered.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15694/15382927037339_en-US.png)


## Allow read-only access to Anti-DDoS Basic {#section_c4n_wjc_wdb .section}

To allow read-only access to Anti-DDoS Basic, complete these steps:

**Note:** You have to use the primary account to complete the authorization.

1.  Use the primary account to log on to the RAM console.
2.  In the left-side navigation pane, click **Users**, find the target RAM account and click **Manage**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/15382927032872_en-US.png)

3.  Click **User Authorization Policies**, and then click **Edit Authorization Policy**.
4.  In the displayed dialog box, search **AliyunYundunDDosReadOnlyAccess**, and then add it to the Selected Authorization Policy Names list. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/15382927032873_en-US.png)


