# How to use a guaranteed-performance Server Load Balancer instance? {#concept_umd_czv_tdb .concept}

Alibaba Cloud plans to charge capacity fee on guaranteed-performance Server Load Balancer instances from April 1, 2018, and continue to sell shared-performance Server Load Balancer instances.

The charging of capacity fee will take effect in batches as follows:

-   The first batch:

    Time: take effect successively from April 1st to April 10th

    Regions: Singapore, Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), India \(Mumbai\), US \(Silicon Valley\), US \(Virginia\)

-   The second batch:

    Time: take effect successively from April 11th to April 20th

    Regions: China \(Hangzhou\), China \(Zhangjiakou\), China \(Hothot\), China \(Hong Kong\)

-   The third batch:

    Time: take effect successively from April 21th to April 30th

    Regions: China \(Qingdao\), China \(Beijing\), China \(Shanghai\), China \(Shenzhen\)


[1. What are guaranteed-performance instances?](#section_lht_gym_vdb)

[2. How are guaranteed-performance instances billed?](#section_eth_yzm_vdb)

[3. What is the price of each capacity?](#section_n5z_s1n_vdb)

[4. How to select a guaranteed-performance instance?](#section_ifx_kcn_vdb)

[5. Can I modify the capacity after the instance is created?](#section_dmb_q2n_vdb)

[6. When will be the guaranteed-performance instances charged?](#section_gvt_kfn_vdb)

[7. After Alibaba Cloud starts to charge capacity fee on guaranteed-performance instances, will extra fees be charged on shared-performance instances?](#section_hxl_pfn_vdb)

[8. Why sometimes guaranteed-performance instances cannot reach the performance limit as defined in the capacity?](#section_ehc_vfn_vdb)

[9. Can I still buy shared-performance instances?](#section_flq_wfn_vdb)

[10. Will intranet SLB instances be charged for capacity fee?](#section_nfy_xfn_vdb)

## 1. What are guaranteed-performance instances? {#section_lht_gym_vdb .section}

A guaranteed-performance instance provides guaranteed performance metrics \(performance SLA\) and is opposite to a shared-performance instance.  For a shared-performance instance, the performance metrics are not guaranteed and the resources are shared by all instances.

All instances are shared-performance instances before Alibaba launches guaranteed-performance instances. You can view the instance type on the console. 

Hover your mouse pointer to the green icon of the target instance to view the performance metrics, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623277_en-US.png)

The following are three key performance metrics for guaranteed-performance instances:

-   Max Connection

    The maximum number of connections to a SLB instance.  When the maximum number of connections reaches the limits of the capacity, the new connection will be dropped.

-   Connection Per Second \(CPS\)

    The rate at which a new connection is established per second.  When the CPS reaches the limits of the capacity, the new connection will be dropped.

-   Query Per Second \(QPS\)

    The number of HTTP/HTTPS requests that can be processed per second. This metrics is only available for Layer-7 Server Load Balancer. When the QPS reaches the limits of the capacity, the new connection will be dropped.


Alibaba Cloud Server Load Balancer provides the following capacities for guaranteed-performance instances:

|Capacity|Capacity|Max Connection|Connection Per Second \(CPS\)|Query Per Second \(QPS\)|
|:-------|:-------|:-------------|:----------------------------|:-----------------------|
|Capacity 1| Small I \(slb.s1.small\)|5,000|3,000|1,000|
|Capacity 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|
|Capacity 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|
|Capacity 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|
|Capacity 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|
|Capacity 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|

If you want to use a larger capacity, contact your customer manager.

## 2. How are guaranteed-performance instances billed? {#section_eth_yzm_vdb .section}

Guaranteed-performance instances are billed as follows:

Total fee \(per instance\) = instance fee + traffic fee + capacity fee

**Note:** The corresponding capacity fee is billed for each guaranteed-performance instance no matter the network type of the instance, and is billed based on the actual usage depending on the capacity selected. If the actual performance metrics of an instance occurs between two capacities, the capacity fee is charged at the higher capacity fee. 

Load Balancing is divided into two types of charging modes, pre-payment and on-demand payment. In different billing modes, the specification charge rules for the performance guarantee instance are different:

-   Pre-payment mode

    The performance guarantee instance specification fee is charged according to the pre-payment mode, that is, during the payment cycle of the instance, the instance specification fee is charged at a fixed price. Suppose you choose high-end I. \(SLB. s3.small\) specification, and choose to purchase for 3 months, the specification fee = SLB. s3.small specification monthly price X March.

-   Pay-As-You-Go mode

    The performance guarantee instance specification fee is charged by usage, no matter what kind of specification you choose, the instance specification fee will be charged according to the specifications you actually use.

    For example, if you purchase the  Super I \(slb.s3.large\) capacity, and the actual usage of your instance in an hour is as follow:

    |Max Connection|CPS|QPS|
    |:-------------|:--|:--|
    |90000|4000|11000|

    -   From the perspective of Max Connection, the actual metrics 90,000 occurs between the limit 50,000 defined in the Standard I \(slb.s2.small\) capacity and the limit 100,000 defined in the Standard II \(slb.s2.medium\) capacity. Therefore, the capacity of the Max Connection metrics in this hour is Standard II \(slb.s2.medium\).
    -   From the perspective of CPS, the actual metrics 4,000 occurs between the limit 3,000 defined in the Small I \(slb.s1.small\) capacity and the limit 5,000 defined in the Standard I \(slb.s2.small\) capacity. Therefore, the capacity of the CPS metrics in this hour is Standard I \(slb.s2.small\).
    -   From the perspective of QPS, the actual metrics 11,000 occurs between the limit 10,000 defined in the Standard II \(slb.s2.medium\) capacity and the limit 20,000 defined in the Higher I \(slb.s3.small\) capacity.  Therefore, the capacity of the QPS metrics in this hour is Higher I \(slb.s3.small\).

        Comparing these three metrics, the capacity of the QPS metrics is highest, therefore, the capacity fee of the instance in this hour is charged at the price of the Higher I \(slb.s3.small\) capacity.

    The following figure is an example showing how the capacity fee is billed for an SLB instance in the first three hours:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623280_en-US.png)

    The billing of the guaranteed-performance instances is flexible.  The performance capacity selected when purchasing an SLB instance limits the performance. For example, if slb.s3.medium is selected, the new connections are dropped when the HTTP requests in one second reach 30,000.


## 3. What is the price of each capacity? {#section_n5z_s1n_vdb .section}

The following table lists the capacity price of each capacity. Besides the capacity fee, the instance fee and traffic/bandwidth fee are also charged. For more information, see [Billing](../../../../reseller.en-US/Pricing/Pay-As-You-Go.md#).

|Region|Capacity|Capacity|Max Connection|CPS|QPS|Package year package month \(RMB/month\)|USD/Hour|
|:-----|:-------|:-------|:-------------|:--|:--|:---------------------------------------|:-------|
| China \(Beijing\)

 China \(Zhangjiakou\)

 China \(Huhehaote\)

 China \(Qingdao\)

 China \(Beijing\)

 China \(Shanghai\)

 China \(Shenzhen\)

 |Capacity 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge|Free of charge|
|Capacity 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|190.00|0.32|
|Capacity 3 |Standard II \(slb.s2.medium\)|100,000|10,000|10,000|380.00|0.63|
|Capacity 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|760.00|1.27|
|Capacity 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|1,143.00|1.91|
|Capacity 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|1,908.00|3.18|
| Singapore

 Malaysia \(Kuala Lumpur\)

 Indonesia \(Jakarta\)

 India \(Mumbai\)

 US \(Silicon Valley\)

 US \(Virginia\)

 Hong Kong

 |Capacity 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge|Free of charge|
|Capacity 2| Standard I \(slb.s2.small\)|50,000|5,000|5,000|228.00|0.38|
|Capacity 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|456.00|0.76|
|Capacity 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|912.00|1.52|
|Capacity 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|1,372.00|2.29|
|Capacity 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|2,290.00|3.82|

Capacity fees of guaranteed-performance instances in the international regions can enjoy an 83% discount.

## 4. How to select a capacity? {#section_ifx_kcn_vdb .section}

-   Because the capacity fee is billed based on the actual usage, we recommend that you select the largest capacity \(slb.s3.large\). This guarantees the business flexibility \(flexibility\) and will not cause extra costs. If your traffic does not reach the largest capacity, you can select a more reasonable capacity, such as slb.s3.medium.
-   If you are buying a pre-payment instance, the situation is slightly more complicated. Because the specification fee is charged constantly at a fixed rate, and you don't want to buy a specification that exceeds your actual business volume, and therefore to pay an unnecessary cost, so you need to assess your actual business volume, and a reasonable consideration of some redundancy, and then select a more appropriate specification for the volume of business assessment, the main reference is to the following principles:
    -   If it is a four-tier listen, the focus is on the number of concurrent connections with long connections, then the largest \(concurrent\) the number of connections should be referred to as a key indicator. Depending on the business scenario, you need to estimate the maximum number of concurrent connections that a load balancing instance needs to host, and select the appropriate specifications.
    -   If it is a seven-tier Monitor, the focus is on QPS performance, QPS determines the throughput of a seven-tier application system. Similarly, you need to predict QPS based on experience. After the initial selection of a specification, fine tune the specification during the business pressure measurement and measurement process.
    -   Combined with other key monitoring indicators launched in conjunction with the Performance Assurance instance, view the trend and peak of actual business traffic, and select performance specifications more precisely. For more details, refer to monitoring data.

        Example of concurrent connections monitoring

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623281_en-US.png)

        New Connection monitoring example

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623282_en-US.png)

        QPS monitoring example

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623283_en-US.png)


## 5. Can I modify the capacity after the instance is created? {#section_dmb_q2n_vdb .section}

Yes. You can change the capacity at any time and the change takes effect immediately. 

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623284_en-US.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623287_en-US.png)

The specifications of the cost-per-volume performance-guaranteed instance can be either elevated or lowered, A white list is required for the Performance-guaranteed instance of the Year-to-month package. For details, please refer to the package years and months instance variation.

Therefore, we recommend that you first use a paid instance to test your business, confirm the specifications and then purchase the required specifications of the package year package month instance.

**Note:** 

-   After you change a shared-performance instance to a guaranteed-performance instance, you cannot change it back.
-   When changing Performance Assurance instance specifications, if you change the way you charge at the same time \(on a flow meter or on a bandwidth basis \), the specification change needs to be zero to the next day to take effect. If you only change an instance specification, the change takes effect immediately. When you change specifications, we that you do not change the billing method.
-   Some instances may exist in older clusters due to historical stock. If you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. Therefore, we recommend that changing the capacity in period of low traffic volume or performing load balancing among instances through [GSLB](https://promotion.aliyun.com/ntms/act/globalslb.html?spm=5176.71615.741495.1.307291894icRpB&wh_ttid=pc) first.
-   The IP of the SLB instance will not be changed after you changing the instance type or the capacity.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623288_en-US.png)

## 6. When will be the guaranteed-performance instances charged? {#section_gvt_kfn_vdb .section}

Alibaba Cloud launched the guaranteed-performance instances in May 2017, and will charge the capacity fee on guaranteed-performance instances beginning April 1, 2018.

The charging of capacity fee will take effect in batches as follows:

-   The first batch:

    Time: take effect successively from April 1st to April 10th

    Regions: Singapore, Malaysia \(Kuala Lumpur\), Indonesia \(jakarta\), India \(Mumbai\), US \(Silicon Valley\), US \(Virginia\)

-   The second batch:

    Time: take effect successively from April 11th to April 20th

    Regions: China \(Hangzhou\), China \(Zhangjiakou\), China \(Hothot\), China \(Hong Kong\)

-   The third batch:

    Time: take effect successively from April 21th to April 30th

    Regions: China \(Qingdao\), China \(Beijing\), China \(Shanghai\), China \(Shenzhen\)


## 7. After Alibaba Cloud starts to charge capacity fee on guaranteed-performance instances, will extra fees be charged on shared-performance instances? {#section_hxl_pfn_vdb .section}

No.

The billing of the original shared-performance instances is the same if you do not change it to a performance-guaranteed instance.  However, if you change the shared-performance instance to the guaranteed-performance one, the capacity fee will be charged from the April 1st, 2018.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15379525623289_en-US.png)

## 8. Why sometimes guaranteed-performance instances cannot reach the performance limit as defined in the capacity? {#section_ehc_vfn_vdb .section}

It applies the cask theory.

Guaranteed-performance instances do not guarantee that the three metrics can reach the capacity limits at the same time.  The limitation is triggered as long as a metric first reaches the limitation defined in the capacity. For example, you have purchased a guaranteed-performance instance of the Higher I \(slb.s3.small\) capacity. 

When the QPS of the instance reaches 20,000 but the number of maximum connections does not reach 200,000, the new connections are still dropped because the QPS has reached the limitation.

## 9. Can I still buy shared-performance instances? {#section_flq_wfn_vdb .section}

Yes.

However, shared-performance instances will be phased out in the future. Please pay attention to the official announcement.

## 10. Will intranet SLB instances be charged for capacity fee? {#section_nfy_xfn_vdb .section}

If the intranet SLB instance is a shared-performance instance, no capacity fee is charged. If the intranet SLB instance is a guaranteed-performance instance, corresponding capacity fee is charged, and no other fees are charged.

