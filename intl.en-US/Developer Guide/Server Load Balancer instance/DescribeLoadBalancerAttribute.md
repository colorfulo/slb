# DescribeLoadBalancerAttribute {#slb_api_DescribeLoadBalancerAttribute .reference}

Query the detailed information of an SLB instance.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String |Yes|The action to perform. Valid value:DescribeLoadBalancerAttribute

|
|LoadBalancerId|String|Yes|The ID of the SLB instance.|
|RegionId|String|No|The region of the SLB instance. You can obtain the region ID by calling the DescribeRegions API.

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|LoadBalancerId|String|The ID of Server Load Balancer instance.|
|RegionId|String|The ID of the region where the SLB instance is located.|
|RegionIdAlias|String|The alias of the region where the SLB instance is located.|
|LoadBalancerName|String|The name of the SLB instance.|
|LoadBalancerStatus|String|The status of the SLB instance.-   inactive: When the SLB instance in the inactive status, the listeners of the instance do not distribute traffic any more.
-   active: After an instance is created, it is in the active status by default.
-   locked: The SLB instance is locked.

|
|Address|String|The IP address of the SLB instance.|
|AddressType|String|The network type of the SLB instance.|
|NetworkType|String|The network type of the intranet SLB instance.|
|VpcId|String|The ID of the VPC where the intranet SLB instance is created.|
|VSwitchId|String|The ID of the VSwitch to which the intranet SLB instance belongs.|
|Bandwidth|Integer|按带宽计费的公网型实例的带宽峰值。|
|CreateTime |String|The time when the SLB instance is created.|
|ListenerPorts|List|The list of frontend ports configured in the SLB instance.|
|ListenerPortsAndProtocol|List|The list of frontend ports and protocols configured in the SLB instance.|
|BackendServers|List|The list of backend servers added to the SLB instance.|
|MasterZoneId|String|The primary zone ID of the SLB instance.|
|SlaveZoneId|String|The backup zone ID of the SLB instance.|
|LoadBalancerSpec|String|The performance specification of the SLB instance.If this value is empty, the instance is a shared-performance instance.

|
|EndTimeStamp|String|The end time stamp of the SLB instance.|
|InternetChargeType|String|The Internet billing type.|
|PayType|String|The instance payment type.|
|ResourceGroupId|String|The ID of the resource group.|

|Name|Type|Description|
|:---|:---|:----------|
|ListenerPort|Integer|The front-end port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.|
|ListenerProtocol|String|The frontend protocol used by the SLB instance.|
|listenerForward|String|Whether to enable listener forwarding.|
|forwardPort|Integer|The destination listening port. It must be an existing HTTPS listening port.|

|Name |Type|Description|
|:----|:---|:----------|
|ServerId|String|The ID of the backend server \(ECS instance\).|
|Weight|Integer|The weight of the backend server.|
|Type|String|The type of the backend server.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
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

-   JSON format

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
      "Createtime": "2014-01-01 00:00:00 ",
      "ListenerPorts": {
        "Listenerport ":[
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


