# DescribeLoadBalancers {#slb_api_DescribeLoadBalancers .reference}

Query created SLB instances.

## Request parameters {#section_bqw_c1g_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform.  Valid value: DescribeLoadBalancers

|
|RegionId|String | Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String| No|The ID of the SLB instance.Multi-valued query is supported. You can input up to 10 IDs and separate them by commas.

|
|LoadBalancerName|String| No|The name of the SLB instance.Multi-valued query is supported. You can input up to 10 IDs and separate them by commas.

|
|AddressType|String| No|The network type of the SLB instance. Valid value:intranet | internet 

|
|NetworkType|String| No|The network type of the intranet SLB instance. Valid value:-   vpc: An SLB instance of the VPC network.
-   classic: An SLB instance of the classic network.

|
|VpcId|String| No|The ID of the VPC where the intranet SLB instance is created.|
|VSwitchId|String| No|The ID of the VSwitch to which the intranet SLB instance belongs.|
|Address|String| No|The IP address of the SLB instance.|
|ServerIntranetAddress|Integer|No |The intranet address of the added backend server \(ECS instance\).Multi-valued query is supported. You can separate values by commas.

|
|InternetChargeType|String| No|The payment method of the Internet SLB instance. Valid value: paybybandwidth or paybytraffic|
|ServerId|String| No|The ID of the added backend server \(ECS instance\).|
|MasterZoneId|String| No|The ID of the primary zone of the SLB instance.|
|SlaveZoneId|String| No|The ID of the backup zone of the SLB instance.|
|Tags|String| No|The tags bound to the SLB instance.You can specify up to 10 tags.

|

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|TagKey|String| No|The key of the tag.**Note:** This parameter is required if the Tags parameter is specified.

|
|TagValue|String| No|The value of the tag key. It cannot begin with aliyun.**Note:** This parameter is required if the Tags parameter is specified.

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|LoadBalancers|List|The list of queried SLB instances.|

|Name |Type|Description|
|:----|:---|:----------|
|LoadBalancerId|String|The ID of the SLB instance.|
|LoadBalancerName|String|The name of the SLB instance.|
|LoadBalancerStatus|String|The status of the SLB instance.-   inactive: When the SLB instance in the inactive status, the listeners of the instance do not distribute traffic any more.
-   active: After an instance is created, it is in the active status by default.
-   locked: The SLB instance is locked.

|
|Address|String|The IP address of the SLB instance.|
|RegionId|String|The ID of the region where the SLB instance is located.|
|RegionIdAlias|String|The name of the SLB instance.|
|AddressType|String|The network type of the SLB instance.|
|VSwitchId|String|The ID of the VSwitch where the SLB instance is created.|
|VpcId|String|The ID of the VPC where the SLB instance is created.|
|NetworkType|String|The network type of the intranet SLB instance.-   vpc: The SLB instance of the VPC network
-   classic: The SLB instance of the classic network

|
|CreateTime |String|The time when the SLB instance was created.|
|MasterZoneId|String|The ID of the primary zone.|
|SlaveZoneId|String|The ID of the backup zone.|
|InternetChargeType|String|The billing method used for the Internet SLB instance. Valid value:-   paybybandwidth: Pay by bandwidth
-   paybytraffic: Pay by traffic \(default\)

**Note:** 当PayType参数的值为PrePay时，只支持按带宽计费。

|
|PayType|String|The billing method of the SLB instance. Valid value:-   PayOnDemand: Pay-As-You-Go
-   PrePay: Subscription

|
|ResourceGroupId|String|The ID of the enterprise resource group.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&RegionId=cn-hangzhou
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
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

-   JSON format

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


