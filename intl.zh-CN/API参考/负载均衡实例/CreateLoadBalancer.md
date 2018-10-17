# CreateLoadBalancer {#SLB_api_CreateLoadBalancer .reference}

创建负载均衡实例。

调用该接口创建实例时，请注意：

-   实例创建后，会产生费用。关于负载均衡的计费说明，参见计费说明。
-   如果不指定实例规格（LoadBalancerSpec），则创建性能共享型实例。建议在创建负载均衡实例时，通过规格参数（LoadBalancerSpec）指定实例的规格。

## 请求参数 {#section_cch_pjg_mdb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。 取值：CreateLoadBalancer

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|MasterZoneId|String|否|实例的主可用区ID。您可以通过调用DescribeZone接口可查到相应地域下的主备可用区信息。

|
|SlaveZoneId|String|否|实例的备可用区ID。您可以通过调用DescribeZone接口可查到相应地域下的主备可用区信息。

|
|LoadBalancerSpec|String|否|负载均衡实例的规格。取值：-   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

**说明：** 若不指定规格，则创建性能共享型实例。

每个地域支持的规格不同。目前支持性能保障型实例的地域有：华北 1（青岛）、华北 2（北京）、华东 1（杭州）、华东 2（上海）、华南 1（深圳）、华北 3（张家口）、华北 5 （呼和浩特）、亚太东南 1（新加坡）和美国东部 1（弗吉尼亚）。关于每种规格的说明，参见[性能保障型实例](../../../../intl.zh-CN/历史文档/用户指南（旧版控制台）/负载均衡实例/性能保障型实例.md#)。

|
|LoadBalancerName|String|否|负载均衡实例的名称。长度为 2-128个字符，必须以英文字母开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

|
|AddressType|String|否| 负载均衡实例的网络类型。取值：

 -   internet：创建公网负载均衡实例后，系统会分配一个公网IP地址，可以转发公网请求。
-   intranet：创建私网负载均衡实例后，系统会分配一个内网IP地址，仅可转发内网请求。

 |
|VSwitchId|String|否|负载均衡实例的所属交换机ID。**说明：** 指定该参数后，AddressType的值为会自动设置为intranet。

|
|Address|String|否|VPC类型负载均衡实例的IP地址。设置该参数时，必须指定VSwitchId参数的值。

|
|PayType|String|否|实例的计费类型，取值：-   PayOnDemand：按量付费

|
|InternetChargeType|String|否|公网实例的计费方式。取值：-   paybytraffic：按流量计费（默认值）

|
|ClientToken|String|否|客户端token，用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

|
|ResourceGroupId|String|否|企业资源组ID。|
|AddressIPVersion|String|否|IP版本，可以设置为ipv4或者ipv6。**说明：** 目前，仅有华东1地域的E、F可用区和华北2地域的F、G可用区支持创建ipv6实例且实例类型必须为性能保障型实例。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|LoadBalancerId|String|负载均衡实例的ID。|
|Address|String|分配的负载均衡实例的IP地址。|
|VpcId|String|负载均衡实例的所属VPC ID。|
|VSwitchId|String|负载均衡实例的所属交换机 ID。|
|MasterZoneId|String|负载均衡实例的主可用区。|
|SlaveZoneId|String|负载均衡实例的备可用区。|
|LoadBalancerName|String|负载均衡实例的名称。|
|LoadBalancerSpec|String|负载均衡的实例规格。若没有指定规格，值为空（表示是性能共享型实例）。|
|MasterZoneId|String|实例的主可用区ID。|
|SlaveZoneId|String|实例的备可用区ID。|
|LoadBalancerSpec|String|负载均衡实例的规格。|
|addressIPVersion|String|IP版本。|
|orderId|String|预付费实例的订单ID。|

## 示例 {#section_py2_vly_22b .section}

**请求示例**

``` {#para1}
https://slb.aliyuncs.com/?Action=CreateLoadBalancer
 &RegionId=cn-east-hangzhou-01
 &LoadBalancerName=abc
 &AddressType=internet
 &AddressIPVersion=ipv4
 &InternetChargeType=paybytraffic
 &<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <CreateLoadBalancerResponse>
      <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
      <LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
      <Address>42.250.6.36</Address>
      <NetworkType>classic<NetworkType>
      <MasterZoneId>cn-hangzhou-b<MasterZoneId>
      <SlaveZoneId>cn-hangzhou-d<SlaveZoneId>
      <LoadBalancerName>abc</LoadBalancerName>
    </CreateLoadBalancerResponse>
    ```

-   JSON格式

    ```
    {
     "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
     "LoadBalancerId":"139a00604ad-cn-east-hangzhou-01",
     "Address":"42.250.6.36",
     "NetworkType":"classic",
     "MasterZoneId":"cn-hangzhou-b",
     "SlaveZoneId":"cn-hangzhou-d",
     "LoadBalancerName":"abc"
    }
    ```


