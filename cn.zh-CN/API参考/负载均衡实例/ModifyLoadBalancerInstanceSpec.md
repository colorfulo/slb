# ModifyLoadBalancerInstanceSpec {#reference_i4w_xmt_ndb .reference}

修改负载均衡的实例规格。

## 请求参数 {#section_cch_pjg_mdb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。 取值：ModifyLoadBalancerInstanceSpec

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用DescribeRegions接口查询地域ID。

|
|LoadBalancerId|String|是|负载均衡实例ID。|
|LoadBalancerSpec|String|是|负载均衡实例的规格。取值：-   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

每个地域支持的规格不同。关于每种规格的说明，参见[性能保障型实例](../../../../cn.zh-CN/历史文档/用户指南（旧版控制台）/负载均衡实例/性能保障型实例.md#)。

**说明：** 将共享型实例变更为保障型实例，SLB将有小概率可能性出现短暂的业务中断（10秒-30秒），建议您在业务低谷期进行变配，或者使用GSLB将业务调度至其他的SLB实例后，再进行变配操作。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|orderId|String|预付费实例的订单ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=ModifyLoadBalancerInstanceSpec 
&RegionId=us-east-01
&LoadBalancerId=139a00604ad-us-east-01
&LoadBalancerSpec=slb.s2.small 
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ModifyLoadBalancerInstanceSpecResponse>
      <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    </ModifyLoadBalancerInstanceSpecResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    }
    ```


