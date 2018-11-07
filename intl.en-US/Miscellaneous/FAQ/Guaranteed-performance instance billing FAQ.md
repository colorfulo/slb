# Guaranteed-performance instance billing FAQ {#concept_tkd_jh5_vdb .concept}

## 1. When will the guaranteed-performance instance start charging the capacity fees? {#section_zqv_zby_wdb .section}

Alibaba Cloud Server Load Balancer \(SLB\) launched the guaranteed-performance instances in May, 2017, and started the testing at the same time. For now, the guaranteed-performance instance has been tested for 10 months. SLB will charge the capacity fee on guaranteed-performance instances from April 1, 2018. For more information, see [How to use guaranteed-performance instances?](../../../../intl.en-US/Miscellaneous/FAQ/How to use guaranteed-performance SLB instances?.md#).

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


## 2. Will intranet SLB instances be charged for capacity fee? {#section_z11_2cy_wdb .section}

-   If the intranet SLB instance is a shared-performance SLB instance, no capacity fees are collected.
-   If the intranet SLB instance is a guaranteed-performance SLB instance, corresponding capacity fees are collected.

    The capacity fees are collected as the same as the Internet guaranteed-performance instances, but intranet guaranteed-performance instances are free from instance fee and traffic fee.


## 3. Will the billing of shared-performance instances be affected after the capacity fees are charged? {#section_drv_zby_wdb .section}

No.

The shared-performance instances will not be charged for the capacity fee.

However, if you change the shared-performance instances to the guaranteed-performance instances, the capacity fees will be collected from April 1, 2018.

## 4. Can shared-performance instances be changed to guaranteed-performance instances? {#section_erv_zby_wdb .section}

Yes.

Once an instance is changed to the guaranteed-performance type, it cannot change back and will be charged from April 1st.

## 5. Can I change a shared-performance instance to a guaranteed-performance instance? {#section_dck_fhm_sfb .section}

Yes.

Guaranteed-performance instances are charged and cannot be changed back to shared-performance instances.

## 5. What are the capacities for shared-performance instances? {#section_frv_zby_wdb .section}

Shared-performance instances do not guarantee the performance. No capacities are available.

## 6. How to select a performance capacity? {#section_nmk_fcy_wdb .section}

You can select the largest capacity for Pay-As-You-Go instances, because Pay-As-You-Go instance are charged according to the actual usage and are free of charge in idle time.

## 7. What is the price of the performance capacity? {#section_irv_zby_wdb .section}

Six capacities are provided for guaranteed-performance instances. No capacity fee is collected for the Standard I \(slb.s1.small\) capacity. For more information, see [Billing](../../../../intl.en-US/Miscellaneous/FAQ/How to use guaranteed-performance SLB instances?.md#section_n5z_s1n_vdb).

## 8. Are the traffic fee and instance fee of guaranteed-performance instances the same as those of shared-performance instances? {#section_jrv_zby_wdb .section}

Yes.

## 9. How many guaranteed-performance instances can be created? {#section_krv_zby_wdb .section}

Same as shared-performance instances, you can purchase up to 60 guaranteed-performance instances. Open a ticket to apply for more quota.

## 10. Can I adjust the capacity of a guaranteed-performance instance? {#section_lrv_zby_wdb .section}

Yes

You can upgrade or downgrade a Pay-As-You-Go guaranteed-performance instance. For more information, see [后付费实例变配](../../../../intl.en-US/Archives/User Guide (Old Console)/SLB instances/Change the configuration.md#).

**Note:** 

-   Once a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   Some instances may exist in older clusters due to historical stock. These instances need to be migrated when they are changed to guaranteed-performance instances. Therefore a service interruption of 10-30 seconds may occur. We recommend that you change the instance type when the traffic is low or perform load balancing among instances first through [GSLB](https://promotion.aliyun.com/ntms/act/globalslb.html?spm=5176.71615.741495.1.307291894icRpB&wh_ttid=pc) and then change the instance type.

## 11. Can I still buy shared-performance instances? {#section_orv_zby_wdb .section}

Yes.

However, the shared-performance instances will be phased out in the future. Please pay attention to the official notifications.

