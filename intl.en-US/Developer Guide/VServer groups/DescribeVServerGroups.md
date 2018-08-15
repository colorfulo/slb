# DescribeVServerGroups {#reference_fy2_gvd_ddd .reference}

Query the created VServer groups.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String| Yes|The action to perform. Valid value:DescribeVServerGroups

|
|RegionId|String | Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String| Yes|The ID of the Server Load Balancer instance.|
|**IncludeRule**|Boolean |No|Whether to return the associated forwarding rules. Default value:false

|
|**IncludeListener**|Boolean |No|Whether to return the associated listeners. Default value:false

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|----|----|-----------|
|**RequestId**|String|The ID of the request.|
|**VServerGroups**|List|The list of the VServer groups.|

|Name |Type|Description|
|:----|:---|:----------|
|VServerGroupId|String|The ID of the VServer group.|
|VServerGroupName|String|The name of the VServer group.|
|**AssociatedObjects**|Object|Associated information.|

|Name |Type|Description|
|:----|:---|:----------|
|Rules|List|A list of associated forwarding rules.|
|Listeners|List|A list of associated listeners.|

|Name|Type|Description|
|----|----|-----------|
|RuleId|String|The ID of the forwarding rule.|
|RuleName|String|The name of the forwarding rule.|
|Domain|String|The request domain.|
|Url|String|The request URL.|

|Name |Type|Description|
|-----|----|-----------|
|Protocol|String|The protocol used by the listener.|
|Port|Integer|The listener port.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeVServerGroups
&RegionId=cn-hangzhou
&LoadBalancerId=lb-bp1yii0s312x83r3qpzke
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    	<VServerGroups>
    		<VServerGroup>
    			<VServerGroupId>rsp-bp12bjrnykyp0</VServerGroupId>
    			<VServerGroupName>6</VServerGroupName>
    			<AssociatedObjects>
    				<Listeners></Listeners>
    				<Rules></Rules>
    			</AssociatedObjects>
    		</VServerGroup>
    		<VServerGroup>
    			<VServerGroupId>rsp-bp16rt0dzbm23</VServerGroupId>
    			<VServerGroupName>text2</VServerGroupName>
    			<AssociatedObjects>
    				<Listeners></Listeners>
    				<Rules></Rules>
    			</AssociatedObjects>
    		</VServerGroup>
    	</VServerGroups>
    	<RequestId>E3F94C66-5DDD-4A6B-B37D-FD237FB31FE6</RequestId>
    ```

-   JSON format

    ```
    {
        "VServerGroups": {
            "VServerGroup": [
                {
                    "VServerGroupId": "rsp-bp12bjrnykyp0", 
                    "VServerGroupName": "6", 
                    "AssociatedObjects": {
                        "Listeners": {
                            "Listener": [ ]
                        }, 
                        "Rules": {
                            "Rule": [ ]
                        }
                    }
                }, 
                {
                    "VServerGroupId": "rsp-bp16rt0dzbm23", 
                    "VServerGroupName": "text2", 
                    "AssociatedObjects": {
                        "Listeners": {
                            "Listener": [ ]
                        }, 
                        "Rules": {
                            "Rule": [ ]
                        }
                    }
                }
            ]
        }, 
        "RequestId": "E3F94C66-5DDD-4A6B-B37D-FD237FB31FE6"
    }
    ```


