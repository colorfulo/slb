# RemoveVServerGroupBackendServers {#reference_hg2_4sd_ndb .reference}

Remove backend servers from a VServer group.

**Note:** If the backend server specified in the BackendServers parameter does not exist in the specified VServer group, it is ignored and no error is returned.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Parameters|Required|Description|
|:---|:---------|:-------|:----------|
|Action |String| Yes|The action to perform. Valid value:RemoveVServerGroupBackendServers

|
|RegionId|String| Yes|The ID of the region where the Server Load Balancer instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|VServerGroupId|String| Yes|The ID of the VServer group.|
|Backendservers|StringList

|Yes|The list of backend servers.A VServer group can contain 20 backend servers at most.

|

|Name|Parameters|Required| Description|
|:---|:---------|:-------|:-----------|
|ServerId|String| Yes|The ID of the ECS instance.|
|Port|Integer|Yes|The port used by the backend server.Valid value: 1-65535

|
|Type|String| Yes|The type of the backend server. Valid value:-   ecs: ECS instance \(Default\)
-   eni: Elastic Network Interface \(ENI\)

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Required|
|:---|:---|:-------|
|RequestId|String|The ID of the request.|
|VServerGroupId|String|The ID of the VServer group.|
|Backendservers|List|The list of backend servers.|

## Samples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=RemoveVServerGroupBackendServers
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&VServerGroupName=Group1
&BackendServers=[
    {"ServerId":"vm-233","Port":"80","Weight":"100","Type":"ecs},
    {"ServerId":"vm-232","Port":"90","Weight":"100","Type":"ecs},
]
&common request parameters
```

**返回示例**

-   XML格式

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <RemoveVServerGroupBackendServersResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-231</ServerId>
    			<Port>70</Port>
    			<Weight>100</Weight>
                            <Type>ecs</Type>
    		</BackendServer>
    	</BackendServers>
    </RemoveVServerGroupBackendServersResponse>
    ```

-   JSON format

    ```
    {
      "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
      "VServerGroupId":"rsp-cige6j5e7p",
      "BackendServers":{
      "BackendServer":[
        {"ServerId":"vm-233","Port":"80","Weight":"100","Type":"ecs},
        {"ServerId":"vm-232","Port":"90","Weight":"100","Type":"ecs},
        {"ServerId":"vm-231","Port":"70","Weight":"100","Type":"ecs}
        ]
      }
    }
    ```


