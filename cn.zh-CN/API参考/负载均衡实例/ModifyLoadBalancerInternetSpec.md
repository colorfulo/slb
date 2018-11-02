# ModifyLoadBalancerInternetSpec {#reference_yd1_4lv_tdb .reference}

修改公网负载均衡实例的计费方式，包括：

-   调整按带宽计费实例的带宽峰值，修改完成后，立即生效。
-   从按流量计费转换为按带宽计费。计费类型的变更从第二天凌晨开始生效。
-   从按带宽计费转换为按流量计费。计费类型的变更从第二天凌晨开始生效。

## 调试 {#section_tpn_2j5_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerInternetSpec)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_gy5_3db_5db .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。 取值：ModifyLoadBalancerInternetSpec

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|InternetChargeType|String|否|公网类型实例的付费方式。取值：-   paybybandwidth：按带宽计费
-   paybytraffic：按流量计费

**说明：** 如果不指定该参数，则表示保持原有的计费方式。

|
|Bandwidth|Integer|否|按固定带宽计费方式的公网类型实例的带宽峰值。实例中的监听共享该带宽，详情参见[共享实例带宽](../../../../cn.zh-CN/历史文档/用户指南（旧版控制台）/监听/共享实例带宽.md#)。

取值：1-5000 Mbps（各地域的带宽峰值会有不同）

**说明：** 按流量计费的实例不需要指定该参数（即InternetChargeType为paybytraffic）。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|orderId|String|预付费实例的订单ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

```
https://slb.aliyuncs.com/?Action=ModifyLoadBalancerInternetSpec
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&InternetChargeType=paybybandwidth
&Bandwidth=10
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ModifyLoadBalancerInternetSpecResponse>
      <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </ModifyLoadBalancerInternetSpecResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


