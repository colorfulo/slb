# Pay-As-You-Go {#concept_dph_vfs_wdb .concept}

SLB is billed based on traffic usage.

## Billing items {#section_e22_ggs_wdb .section}

The cost of an SLB instance is the sum of the following billing items. The billing items vary in the network type and instance type as shown in the following table.

**Note:** “—” means that the corresponding item is not billed and “✔” means that the corresponding item is billed.

|Network type|Instance type|Instance fee|Traffic fee|Capacity fee|
|:-----------|:------------|:-----------|:----------|:-----------|
|Public network|Shared-performance instances|✔|✔|—|
|Guaranteed-performance instances|✔|✔|✔|
|Intranet|Shared-performance instances|-|-|—|
|Guaranteed-performance instances|-|—|✔|

## Instance fee {#section_a1f_lgs_wdb .section}

The instance fee is the public IP reservation fee of Internet SLB instances.

**Note:** Intranet SLB instances are not charged for instance fees.

Instance fees of Internet SLB instances are billed as follows:

-   Instance fee = instance price \(USD/Hour\) x instance reservation time

    The reservation time is the period from the time the instance is created to the time the instance is released.

-   Instance fees are billed on an hourly basis. In a billing cycle, partial hours are billed as full hours.


If the price on the purchase page is different from the price listed in the table, take the price on the purchase page as the standard.

|Region|Instance fee \(USD/hour\)|
|:-----|:------------------------|
|China \(Hangzhou\)/China \(Beijing\)/China \(Shenzhen\)/ China \(Shanghai\)/China \(Zhangjiakou\)|0.003|
|China \(Qingdao\)|0.003|
|China \(Hong Kong\)|0.009|
|US \(Virginia\) /US \(Silicon Valley\)|0.005|
|Singapore|0.006|
|Japan \(Tokyo\)|0.009|
|Germany \(Frankfurt\)|0.006|
|UAE \(Dubai\)|0.009|
|Australia \(Sydney\)|0.006|

## Traffic fee {#section_c1f_lgs_wdb .section}

Traffic fees are charged based on the traffic usage of Internet SLB instances.

**Note:** Intranet instances are free of traffic fee.

Traffic fees of Internet SLB instances are billed as follows:

-   Public traffic fee = public network traffic \(USD/Hour\) x usage time

    Public network traffic is the outbound \(downstream\) traffic. Inbound \(upstream\) traffic is not included in the cost.

-   Instance fees are billed on an hourly basis. In a billing cycle, partial hours are billed as full hours.

    If the price on the purchase page is different from the price listed in the table, take the price on the purchase page as the standard.

    |Region|Traffic fee \(USD/Gbps\)|
    |:-----|:-----------------------|
    |China \(Hangzhou\)/China \(Beijing\)/China \(Shenzhen\)/China \(Shanghai\)/ China \(Zhangjiakou\)|0.125|
    |China \(Qingdao\)|0.113|
    |China \(Hong Kong\)|0.156|
    |US \(Virginia\) /US \(Silicon Valley\)|0.078|
    |Singapore|0.117|
    |Japan \(Tokyo\)|0.120|
    |Germany \(Frankfurt\)|0.070|
    |UAE \(Dubai\)|0.447|
    |Australia \(Sydney\)|0.130|


## 规格费 {#section_r13_y1h_j2b .section}

性能保障型实例规格费按使用量收取，即不论您选择何种规格，实例规格规格费均按照您实际使用的规格收取。如果实例的实际性能指标在两个规格之间，按照较大规格的费用计算（向上取整原则）。

比如，您选择了超强型I \(slb.s3.large\) 规格（最大连接数1,000,000；CPS 500,000；QPS 500,00）。该实例在某小时内各项指标产生的实际峰值如下：

|最大连接数|每秒新建连接数（CPS）|每秒查询数 （QPS）|
|:----|:-----------|:----------|
|90,000|4,000|11,000|

-   从最大连接数维度看，90,000超过slb.s2.small规格中最大连接数50,000的上限，但未达到slb.s2.medium规格中最大连接数100,000的上限，因此从最大连接数维度计算，该小时规格为slb.s2.medium。

-   从每秒新建连接数（CPS）维度看，4,000超过slb.s1.small规格中CPS 3,000的上限，但未到达slb.s2.small规格中CPS 5,000的上限，因此从CPS维度计算，该小时规格为slb.s2.small。

-   从每秒查询数（QPS）维度看，11,000超过slb.s2.medium规格中PS 10,000的上限，但未达到slb.s3.small中QPS 20,000的上限，因此从QPS维度计算，该小时规格为slb.s3.small。

    综合以上三个维度，QPS指标的规格（slb.s3.small）最大，因此将QPS维度的规格作为该小时实例的综合规格，该小时内该实例将按照slb.s3.small规格进行计费。


以后每小时规格费均按照上述方式计算，如下图所示：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13418/15354565863113_zh-CN.png)

因此，按量付费的性能保障型实例具有自动弹性伸缩（或计费）的能力。您在购买时所选的规格，是性能的上限，比如您选择高阶型II \(slb.s3.medium\)，那么意味着，您的实例最大可以达到的规格上限就是高阶型II \(slb.s3.medium\)。

下表中的价格仅供参考，具体价格请以控制台为准。

|地域|规格|最大连接数|每秒新建连接数 \(CPS\)|每秒查询数\(QPS\)|规格费（美元/小时）|
|:-|:-|:----|:--------------|:-----------|:---------|
| 华东1（杭州）

 华北3（张家口）

 华北5（呼和浩特）

 华北1（青岛）

 华北2（北京）

 华东2（上海）

 华南1（深圳\)

 |规格1：简约型I \(slb.s1.small\)|5000|3000|1000|免费|
|规格2：标准型I \(slb.s2.small\)|50,000|5,000|5,000|0.05|
|规格3：标准型II \(slb.s2.medium\)|100,000|10,000|10,000|0.10|
|规格4：高阶型I \(slb.s3.small\)|200,000|20,000|20,000|0.20|
|规格5：高阶型II \(slb.s3.medium\)|500,000|50,000|30,000|0.31|
|规格6：超强型I \(slb.s3.large\)|1,000,000|100,000|50,000|0.51|
| 亚太东南1（新加坡）

 亚太东南3（吉隆坡）

 亚太东南5（雅加达）

 亚太南部1（孟买）

 美国西部1（硅谷）

 美国东部1（弗吉尼亚）

 香港

 |规格1：简约型I \(slb.s1.small\)|5,000|3,000|1,000|免费|
|规格2：标准型I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|规格3：标准型II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|规格4：高阶型I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|规格5：高阶型II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|规格6：超强型I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

