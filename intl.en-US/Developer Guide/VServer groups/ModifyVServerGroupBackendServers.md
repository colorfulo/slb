# ModifyVServerGroupBackendServers {#reference_kqp_zsd_ndb .reference}

Replace backend servers in a VServer group.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Parameters|Required|Description|
|:---|:---------|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:ModifyVServerGroupBackendServers

|
|RegionId|String| Yes|The ID of the region where the Server Load Balancer instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|VServerGroupId|String| Yes|The ID of the VServer group.|
|OldBackendServers|StringList

|Yes|The list of backend servers to be removed.|
|NewBackendServers|StringList

|Yes|The list of backend servers to be added.A VServer group can contain 20 backend servers at most.

**Note:** Make sure the number of backend servers in OldBackendServers is the same as that of backend servers in NewBackendServers.

|

|Name|Parameters|Required|Description|
|:---|:---------|:-------|:----------|
|ServerId|String| Yes|The ID of the ECS instance to add.|
|Port|Integer|Yes| The port used by the backend server.

 Valid value: 1-65535

 |
|Weight|Integer|Yes| The weight of the backend server. Valid value: \[0,100\]

 The default value is 100. If the value is 0, no requests will be forwarded to this backend server.

 |

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Required|
|:---|:---|:-------|
|RequestId|String|The ID of the request.|
|VServerGroupId|String|The ID of VServer group.|
|BackendServers|StringA list of backend servers.

|The list of backend servers.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&VServerGroupName=Group1
&OldBackendServers=[{"ServerId":"vm-233","Port":"80","Weight":"100"},{"ServerId":"vm-232","Port":"90","Weight":"100"},]
&NewBackendServers=[{"ServerId":"vm-400","Port":"80","Weight":"100"},{"ServerId":"vm-401","Port":"90","Weight":"100"},]
&CommonParameters
```

**Response example**

-   XM format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <ModifyVServerGroupBackendServersResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-400</ServerId>
    			<Port>80</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-401</ServerId>
    			<Port>90</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </ModifyVServerGroupBackendServersResponse>
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
        ]
      }
    }
    ```


