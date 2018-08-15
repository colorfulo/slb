# SetVServerGroupAttribute {#reference_fw5_prd_ndb .reference}

Modify the configurations of a VServer group.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Parameters|Required|Description|
|:---|:---------|:-------|:----------|
|Action|String| Yes|The action to perform. Valid value:SetVServerGroupAttribute

|
|RegionId|String | Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|VServerGroupId|String | Yes|The ID of the VServer group.|
|VServerGroupName|String| No|The name of the VServer group.|
|BackendServers|StringList

|No |The list of the backend servers.A VServer group can contain 20 backend servers at most.

|

|Name|Parameters|Required|Description|
|:---|:---------|:-------|:----------|
|ServerId|String | Yes|The ID of the ECS instance to add.|
|Port|Integer|Yes|The port used by the backend server.Valid value: 1-65535

|
|Weight|Integer|Yes| The weight of the backend server. Valid value: \[0,100\]

 The default value is 100. If the value is 0, no requests will be forwarded to the backend server.

 |
|Type|String| Yes|The type of the backend server.-   ecs: ECS instance \(Default\)
-   eni: Elastic Network Interface \(ENI\)

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|VServerGroupId|String|The ID of the VServer group.|
|VServerGroupName|String|The name of the VServer group.|
|BackendServers|List|The list of backend servers.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetVServerGroupAttribute
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&VServerGroupName=Group1
&BackendServers=[
    {"ServerId":"vm-233","Port":"80","Weight":"100"},
    {"ServerId":"vm-232","Port":"90","Weight":"100"},
    {"ServerId":"vm-232","Port":"90","Weight":"100"},
]
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <SetVServerGroupAttributeResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-233</ServerId>
    			<Port>80</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-232</ServerId>
    			<Port>90</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-231</ServerId>
    			<Port>70</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </SetVServerGroupAttributeResponse>
    ```

-   JSON format

    ```
    {
      "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
      "VServerGroupId":"rsp-cige6j5e7p",
      "BackendServers":{
      "BackendServer":[
        {"ServerId":"vm-233","Port":"80","Weight":"100"},
        {"ServerId":"vm-232","Port":"90","Weight":"100"},
        {"ServerId":"vm-232","Port":"90","Weight":"100"},
        ]
      }
    }
    ```


