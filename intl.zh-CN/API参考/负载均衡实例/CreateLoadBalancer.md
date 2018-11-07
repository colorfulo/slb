# CreateLoadBalancer {#doc_api_726134 .reference}

创建负载均衡实例。

调用该接口创建实例时，请注意：

-   实例创建后，会产生费用。关于负载均衡的计费说明，参见[计费说明](~~27692~~)。
-   如果不指定实例规格（`LoadBalancerSpec`），则创建性能共享型实例。建议在创建负载均衡实例时，通过规格参数（`LoadBalancerSpec`）指定实例的规格。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLoadBalancer|要执行的操作，取值：

**CreateLoadBalancer**

|
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|Address|String|否|192.168.0.0/24|VPC类型负载均衡实例的IP地址。设置该参数时，必须指定

**VSwitchId**

参数的值。

|
|AddressIPVersion|String|否|ipv4|IP版本。

|
|AddressType|String|否|internet|负载均衡实例的网络类型。取值：

 -   internet：创建公网负载均衡实例后，系统会分配一个公网IP地址，可以转发公网请求。
-   intranet：创建公网负载均衡实例后，系统会分配一个内网IP地址，仅可转发内网请求。

 |
|AutoPay|Boolean|否|true|是否是自动支付预付费公网实例的账单，取值：**true|false（默认）**

 |
|Bandwidth|Integer|否|-1|是否是自动支付预付费公网实例的账单，取值：**true|false（默认）**

 |
|ClientToken|String|否|5A2CFF0E-5718-45B5-9D4D-70B3FF3898|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个ASCII字符。

 |
|Duration|Integer|否|1|预付费公网实例的购买时长，取值：

 -   如果PricingCycle为month，取值为1-9。
-   如果PricingCycle为year，取值为1-3。

 |
|InternetChargeType|String|否|paybytraffic|公网类型实例的付费方式。取值：

 -   paybytraffic：按流量计费（默认值）

 |
|LoadBalancerName|String|否|abc|负载均衡实例的名称。

 长度为2-128个英文或中文字符，必须以大小字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

 不指定该参数时，默认由系统分配一个实例名称。

 |
|LoadBalancerSpec|String|否|slb.s2.small|负载均衡实例的规格。取值：

 -   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

 **注意**： 若不指定规格，则创建性能共享型实例。

 每个地域支持的规格不同。目前支持性能保障型实例的地域有：华北 1（青岛）、华北 2（北京）、华东 1（杭州）、华东 2（上海）、华南 1（深圳）、华北 3（张家口）、华北 5 （呼和浩特）、亚太东南 1（新加坡）和美国东部 1（弗吉尼亚）。关于每种规格的说明，参见[性能保障型实例](~~27657~~)。

 |
|MasterZoneId|String|否|cn-hangzhou-b|负载均衡实例的主可用区ID。

 您可以通过调用[DescribeZone](~~27585~~)接口可查到相应地域下的主备可用区信息。

 |
|PayType|String|否|PrePay|实例的计费类型，取值：

 -   PayOnDemand：按量付费
-   PrePay：预付费

 |
|PricingCycle|String|否|Month|预付费公网实例的计费周期，取值：

`month|year`|
|Ratio|Integer|否|100|Ratio参数

|
|ResourceGroupId|String|否|rg-atstuj3rtoptyui|企业资源组ID。

|
|SlaveZoneId|String|否|cn-hangzhou-d|负载均衡实例的备可用区ID。

 您可以通过调用[DescribeZone](~~27585~~)接口可查到相应地域下的主备可用区信息。

 |
|Tags|String|否|\{"tagKey":"Key1","tagValue":"Value1"\}|负载均衡实例标签。

|
|VSwitchId|String|否|vsw-255ecrwq5|专有网络实例的所属交换机ID。

 创建专有网络类型的负载均衡实例，必须指定该参数。如果指定了该参数，**AddessType**参数的值会默认被设置为**intranet**。

 |
|VpcId|String|否|vpc-25dvzy9f8|负载均衡实例的所属的VPC ID。

|

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01|负载均衡实例的ID。

|
|Address|String|42.250.6.36|分配的负载均衡实例的IP地址。

|
|VpcId|String|vpc-25dvzy9f8|负载均衡实例的所属专有网络的ID。

|
|VSwitchId|String|vsw-255ecrwq5|负载均衡实例的所属交换机的ID。

|
|LoadBalancerName|String|abc|负载均衡实例的名称。

|
|AddressIPVersion|String|ipv4|负载均衡实例的IP地址类型。

|
|NetworkType|String|classic|负载均衡实例网络类型。

|
|OrderId|Long|201429619788910|订单ID。

|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

|
|ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

|

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?RegionId=cn-hangzhou
&Action=CreateLoadBalancer
&Address=192.168.0.0/24
&AddressIPVersion=ipv4
&AddressType=internet
&AutoPay=true
&Bandwidth=-1
&ClientToken=5A2CFF0E-5718-45B5-9D4D-70B3FF3898
&Duration=1
&InternetChargeType=paybytraffic
&LoadBalancerName=abc
&LoadBalancerSpec=slb.s2.small
&MasterZoneId=cn-hangzhou-b
&PayType=PrePay
&PricingCycle=Month
&Ratio=100
&ResourceGroupId=rg-atstuj3rtoptyui
&SlaveZoneId=cn-hangzhou-d
&Tags={"tagKey":"Key1","tagValue":"Value1"}
&VpcId=vpc-25dvzy9f8
&VSwitchId=vsw-255ecrwq5
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateLoadBalancerResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
  <Address>42.250.6.36</Address>
  <NetworkType>classic</NetworkType>
  <MasterZoneId>cn-hangzhou-b</MasterZoneId>
  <SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
  <LoadBalancerName>abc</LoadBalancerName>
</CreateLoadBalancerResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"SlaveZoneId":"cn-hangzhou-d",
	"NetworkType":"classic",
	"LoadBalancerName":"abc",
	"MasterZoneId":"cn-hangzhou-b",
	"Address":"42.250.6.36",
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"LoadBalancerId":"139a00604ad-cn-east-hangzhou-01"
}
```

异常返回示例

`XML` 格式

``` {#xml_return_failed_demo}
<CreateLoadBalancerResponse>
  <Code>InvalidParameter</Code>
  <Message>The specified parameter is not valid.</Message>
  <HostId>slb.aliyuncs.com</HostId>
  <RequestId>0669D684-69D8-408E-A4FA-B9011E0F4E66</RequestId>
</CreateLoadBalancerResponse>

```

`JSON` 格式

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

