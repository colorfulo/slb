# Guaranteed-performance instance billing FAQ {#concept_tkd_jh5_vdb .concept}

## 1. When will the guaranteed-performance instance start charging the capacity fees? {#section_zqv_zby_wdb .section}

Alibaba Cloud Server Load Balancer \(SLB\) launched the guaranteed-performance instances in May, 2017, and started the testing at the same time. For now, the guaranteed-performance instance has been tested for 10 months. SLB will charge the capacity fee on guaranteed-performance instances beginning April 1, 2018. For more information, see [How to use guaranteed-performance instances?](../../../../reseller.en-US/Miscellaneous/FAQ/How to use guaranteed-performance SLB instances?.md#).

The fee collection for the guaranteed-performance instances take effect in batches by regions:

-   The first batch:

    Effective time: From April 1 to April 10

    Effective regions: Asia Pacific SE 1 \(Singapore\), Asia Pacific SE 3 \(Kuala Lumpur\), Asia Pacific SE 5 \(Jakarta\), Asia Pacific SOU 1 \(Mumbai\), US West 1 \(Silicon Valley\), US East 1 \(Virginia\), Asia Pacific SOU 1 \(Mumbai\)

-   The second batch:

    Effective time: From April 11 to April 20

    Effective regions: China East 1 \(Hangzhou\), China North 3 \(Zhangjiakou\), China North 5 \(Hohhot\), Hong Kong

-   The third batch:

    Effective time: From April 21 to April 30

    Effective regions: China North 1 \(Qingdao\), China North 2 \(Beijing\), China East 2 \(Shanghai\), China South 1 \(Shenzhen\)


## 2. 已有包年包月保障型实例4月1日开始会收费吗？ {#section_brv_zby_wdb .section}

在到期前**无需**补交性能规格费，但是从4月1日起如果您进行了升级或续费操作，会收取规格费。

## 3. Will intranet SLB instances be charged for capacity fee? {#section_z11_2cy_wdb .section}

-   If the intranet SLB instance is a shared-performance SLB instance, no capacity fees are collected.
-   If the intranet SLB instance is a guaranteed-performance SLB instance, corresponding capacity fees are collected.

    The capacity fees are collected as the same as the Internet guaranteed-performance instances, but intranet guaranteed-performance instances are free from instance fee and traffic fee.


## 3. Will the billing of shared-performance instances be affected after the capacity fees are charged? {#section_drv_zby_wdb .section}

No.

The shared-performance instances will not be charged for the capacity fee.

However, if you change the shared-performance instances to the guaranteed-performance instances, the capacity fees will be collected beginning April 1, 2018.

## 5. Can shared-performance instances be changed to guaranteed-performance instances? {#section_erv_zby_wdb .section}

Yes.

Once an instance is changed to the guaranteed-performance type, it cannot change back and will be charged from April 1st.

## 6. What are the capacities for shared-performance instances? {#section_frv_zby_wdb .section}

Shared-performance instances do not guarantee the performance. No capacities are available.

## 7. How to select a performance capacity? {#section_nmk_fcy_wdb .section}

-   You can select the largest capacity for Pay-As-You-Go instances, because Pay-As-You-Go instance are charged according to the actual usage and are free of charge in idle time.
-   A pre-payment instance \(Year-to-month\) needs to be selected based on your actual volume of business, you can evaluate your business volume in the following ways:
    -   For Layer-4 listeners, the focus of attention is the Max Connection of persistent connection, so Max Connection is used as a key metric. Depending on the business scenario, you need to estimate the Max Connection of a Server Load Balancer instance, and select the appropriate capacity.
    -   For Layer-7 listeners, the focus of attention is the QPS, because QPS determines the throughput of a Layer-7 application system. Similarly, you need to predict QPS based on experience. After the initial selection of a capacity, fine tune the specification during the service pressure test and actual test.

        Therefore, we recommended that you first use a Pay-As-You-Go instance for service test and then by a Subscription instance after determining the capacity. For more information, see [How to select a guaranteed-performance SLB instance](../../../../reseller.en-US/Miscellaneous/FAQ/How to use guaranteed-performance SLB instances?.md#section_ifx_kcn_vdb)


## 8. What is the price of the performance capacity? {#section_irv_zby_wdb .section}

No capacity fee is collected for the Standard I \(slb.s1.small\) capacity. For more information, see [Billing](../../../../reseller.en-US/Miscellaneous/FAQ/How to use guaranteed-performance SLB instances?.md#section_n5z_s1n_vdb).

## 9. Is the traffic fee the same between the shared-performance instances and guaranteed-performance instances? {#section_jrv_zby_wdb .section}

Yes.

## 10. How many guaranteed-performance instances can be created? {#section_krv_zby_wdb .section}

Same as the shared-performance instance, you can purchase up to 60 guaranteed-performance instances. Submit a ticket to apply for more quota.

## 11. Can I adjust the capacity of a guaranteed-performance instance? {#section_lrv_zby_wdb .section}

Yes

-   .
-   A white list is required for the Performance-guaranteed instance of the Year-to-month package. 详情参考[包年包月实例变配](../../../../reseller.en-US/Archives/User Guide (Old Console)/SLB instances/包年包月实例变配.md#)。

**Note:** 

-   Once a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   If you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. If you only change an instance specification, the change takes effect immediately. When you change specifications, it is recommended that you do not change the billing method.
-   Some instances may exist in older clusters due to historical stock. These instances need to be migrated when they are changed to guaranteed-performance instances. Therefore a service interruption of 10-30 seconds may occur. We recommend that you change the instance type when the traffic is low or perform load balancing among instances first through [GSLB](https://promotion.aliyun.com/ntms/act/globalslb.html?spm=5176.71615.741495.1.307291894icRpB&wh_ttid=pc) and then change the instance type.

## 9. Can I still buy shared-performance instances? {#section_orv_zby_wdb .section}

Yes.

However, the shared-performance instances will be phased out in the future. Please pay attention to the official notifications.

