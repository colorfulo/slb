# DescribeLoadBalancerAttribute {#slb_api_DescribeLoadBalancerAttribute .reference}

查询指定负载均衡实例的详细信息。

## 调试 {#section_ocd_f55_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeLoadBalancerAttribute

|
|LoadBalancerId|String|是|负载均衡实例ID。|
|RegionId|String|是|负载均衡实例的地域。 您可以通过调用 DescribeRegions接口获取地域ID。

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|LoadBalancerId|String|负载均衡实例的ID。|
|RegionId|String|负载均衡实例的地域ID。|
|RegionIdAlias|String|负载均衡实例所属的地域别名。|
|LoadBalancerName|String|负载均衡实例的名称。|
|LoadBalancerStatus|String|负载均衡实例状态：-   inactive: 此状态的实例监听不会再转发流量。
-   active: 实例创建后，默认状态为active。
-   locked: 实例已经被锁定。

|
|Address|String|负载均衡实例的服务地址。|
|AddressType|String|负载均衡实例的网络类型。|
|NetworkType|String|私网负载均衡实例的网络类型。|
|VpcId|String|私网负载均衡实例的专有网络ID。|
|VswitchId|String|私网负载均衡实例的交换机ID。|
|Bandwidth|Integer|按带宽计费的公网型实例的带宽峰值。|
|CreateTime|String|负载均衡实例的创建时间。|
|ListenerPorts|List|负载均衡实例前端使用的端口列表。|
|ListenerPortsAndProtocol|List|负载均衡实例前端使用的端口和协议列表。|
|BackendServers|List|负载均衡实例的后端服务器列表。|
|MasterZoneId|String|负载均衡实例的主可用区ID。|
|SlaveZoneId|String|负载均衡实例的备可用区ID。|
|LoadBalancerSpec|String|负载均衡实例的的性能规格。如果取值为空，则代表是性能共享型实例。

|
|EndTimeStamp|String|负载均衡实例结束时间戳。|
|InternetChargeType|String|网络计费类型。|
|PayType|String|实例付费类型。|
|ResourceGroupId|String|资源组ID。|

|名称|类型|描述|
|:-|:-|:-|
|ListenerPort|Integer|负载均衡实例前端使用的端口。|
|ListenerProtocol|String|负载均衡实例前端使用的协议。|
|listenerForward|String|是否启用监听转发。|
|forwardPort|Integer|转发到的目的监听端口，必须是已经存在的HTTPS监听端口。|

|名称|类型|描述|
|:-|:-|:-|
|ServerId|String|后端服务器名（ECS实例）ID。|
|Weight|Integer|后端服务器的权重。|
|type|String|后端服务器类型。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeLoadBalancerAttributeResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
    	<RegionId>cn-east-hangzhou-01</RegionId>
    	<LoadBalancerName>abc</LoadBalancerName>
    	<LoadBalancerStatus>active</LoadBalancerStatus>
    	<Address>42.250.6.36</Address>
    	<AddressType>internet</AddressType>
    	<InternetChargeType>paybybandwidth</InternetChargeType>
    	<Bandwidth>5</Bandwidth>
    	<CreateTime>2014-01-01 00:00:00</CreateTime>
    	<ListenerPorts>
    		<ListenerPort>80</ListenerPort>
    		<ListenerPort>443</ListenerPort>
    	</ListenerPorts>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-233</ServerId>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-234</ServerId>
    			<Weight>90</Weight>
    		</BackendServer>
    	</BackendServers>
    	<MasterZoneId>cn-hangzhou-b</MasterZoneId>
    	<SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
    </DescribeLoadBalancerAttributeResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "LoadBalancerId": "139a00604ad-cn-east-hangzhou-01",
      "RegionId": "cn-east-hangzhou-01",
      "LoadBalancerName": "abc",
      "LoadBalancerStatus ": "active",
      "Address": "42.250.6.36",
      "AddressType": "internet",
      "InternetChargeType": "paybybandwidth",
      "Bandwidth": "5",
      "CreateTime": "2014-01-01 00:00:00",
      "ListenerPorts": {
        "ListenerPort": [
          80,
          443
        ]
      },
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "vm-233",
            "Weight": 100
          },
          {
            "ServerId": "vm-234",
            "Weight": 90
          }
        ]
      },
      "MasterZoneId": "cn-hangzhou-b",
      "SlaveZoneId": "cn-hangzhou-d"
    }  
    ```


