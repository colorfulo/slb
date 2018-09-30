# DescribeLoadBalancers {#slb_api_DescribeLoadBalancers .reference}

查询已创建的负载均衡实例。

## 请求参数 {#section_bqw_c1g_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：DescribeLoadBalancers

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|否|负载均衡实例ID。支持多值查询，最多可输入10个ID，以逗号分隔。

|
|LoadBalancerName|String|否|负载均衡实例名称。支持多值查询，最多可输入10个名称，以逗号分隔。

|
|AddressType|String|否|负载均衡实例的网络类型，取值：intranet | internet 

|
|NetworkType|String|否|私网负载均衡实例的网络类型，取值：-   vpc：专有网络实例
-   classic：经典网络实例

|
|VpcId|String|否|负载均衡实例所属的VPC ID。|
|VswitchId|String|否|负载均衡实例所属的VSwitch ID。|
|Address|String|否|负载均衡实例的服务地址。|
|ServerIntranetAddress|Integer|否|添加的后端服务器（ECS实例）的内网地址。支持多值查询，以逗号分隔。

|
|InternetChargeType|String|否|公网类型实例付费方式。取值：paybybandwidth或paybytraffic|
|ServerId|String|否|添加的后端服务器（ECS实例）的ID。|
|MasterZoneId|String|否|负载均衡实例的主可用区ID。|
|SlaveZoneId|String|否|负载均衡实例的备可用区ID。|
|Tags|String|否|负载均衡实例绑定的标签。最多可指定10个标签。

|

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|TagKey|String|否|标签的key。**说明：** 如果指定了Tags参数，则该参数必选。

|
|TagValue|String|否|对应标签Key的value，不能以aliyun开头。**说明：** 如果指定了Tags参数，则该参数必选。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|LoadBalancers|List|查询到的负载均衡实例列表。|

|名称|类型|描述|
|:-|:-|:-|
|LoadBalancerId|String|负载均衡实例ID。|
|LoadBalancerName|String|负载均衡实例的名称。|
|LoadBalancerStatus|String|负载均衡实例状态：-   inactive: 此状态的实例监听不会再转发流量。
-   active: 实例创建后，默认状态为active。
-   locked: 实例已经被锁定。

|
|Address|String|负载均衡实例的服务地址。|
|RegionId|String|负载均衡实例的地域ID。|
|RegionIdAlias|String|负载均衡实例的名称。|
|AddressType|String|负载均衡实例的网络类型。|
|VSwitchId|String|私网负载均衡实例的交换机ID。|
|VpcId|String|私网负载均衡实例的专有网络ID。|
|NetworkType|String|私网负载均衡实例的网络类型：-   vpc：专有网络实例
-   classic：经典网络实例

|
|CreateTime|String|负载均衡实例的创建时间。|
|MasterZoneId|String|实例的主可用区ID。|
|SlaveZoneId|String|实例的备可用区ID。|
|InternetChargeType|String|公网实例的计费方式。取值：-   paybybandwidth：按带宽计费
-   paybytraffic：按流量计费（默认值）

**说明：** 当PayType参数的值为PrePay时，只支持按带宽计费。

|
|PayType|String|实例的计费类型，取值：-   PayOnDemand：按量付费
-   PrePay：预付费

|
|ResourceGroupId|String|企业资源组ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&RegionId=cn-hangzhou
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeLoadBalancersResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<LoadBalancers>
    		<LoadBalancer>
    			<LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
    			<LoadBalancerName>abc</LoadBalancerName>
    			<Address>100.98.28.56</Address>
    			<AddressType>intranet</AddressType>
    			<RegionId>cn-east-hangzhou-01</RegionId>
    			<VSwitchId>vsw-255ecrwq4</VSwitchId>
    			<VpcId>vpc-25dvzy9f9</VpcId>
    			<NetworkType>vpc</NetworkType>
    			<LoadBalancerStatus>active</LoadBalancerStatus>
    			<MasterZoneId>cn-hangzhou-b</MasterZoneId>
    			<SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
    		</LoadBalancer>
    		<LoadBalancer>
    			<LoadBalancerId>282b00102ac-cn-east-hangzhou-01</LoadBalancerId>
    			<LoadBalancerName>def</LoadBalancerName>
    			<Address>100.98.28.55</Address>
    			<AddressType>intranet</AddressType>
    			<RegionId>cn-east-hangzhou-01</RegionId>
    			<VSwitchId>vsw-255ecrwq5</VSwitchId>
    			<VpcId>vpc-25dvzy9f8</VpcId>
    			<NetworkType>vpc</NetworkType>
    			<LoadBalancerStatus>active</LoadBalancerStatus>
    			<MasterZoneId>cn-hangzhou-b</MasterZoneId>
    			<SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
    		</LoadBalancer>
    	</LoadBalancers>
    </DescribeLoadBalancersResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "LoadBalancers": {
        "LoadBalancer": [
          {
            "LoadBalancerId": "139a00604ad-cn-east-hangzhou-01",
            "LoadBalancerName": "abc",
            "Address": "100.98.28.56",
            "AddressType": "intranet",
            "RegionId": "cn-east-hangzhou-01",
            "VSwitchId": "vsw-255ecrwq4",
            "VpcId": "vpc-25dvzy9f9",
            "NetworkType": "vpc",
            "LoadBalancerStatus ": "active",
            "MasterZoneId": "cn-hangzhou-b",
            "SlaveZoneId": "cn-hangzhou-d"
          },
          {
            "LoadBalancerId": "282b00102ac-cn-east-hangzhou-01",
            "LoadBalancerName": "def",
            "Address": "100.98.28.55",
            "AddressType": "intranet",
            "RegionId": "cn-east-hangzhou-01",
            "VSwitchId": "vsw-255ecrwq5",
            "VpcId": "vpc-25dvzy9f8",
            "NetworkType": "vpc",
            "LoadBalancerStatus ": "active",
            "MasterZoneId": "cn-hangzhou-b",
            "SlaveZoneId": "cn-hangzhou-d"
          }
        ]
      }
    }
    ```


