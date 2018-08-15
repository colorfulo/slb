# DescribeVServerGroupAttribute {#reference_jnq_yvd_ndb .reference}

Query detailed information of a VServer group.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Parameters|Required| Description|
|:---|:---------|:-------|:-----------|
|Action|String| Yes|The action to perform. Valid value:DescribeVServerGroupAttribute

|
|RegionId|String| Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the  DescribeRegions API.

|
|VServerGroupId|String| Yes|The ID of the VServer group.|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Required|
|:---|:---|:-------|
|RequestId|String|The ID of the request.|
|VServerGroupId|String|The ID of the VServer group.|
|VServerGroupName|String|The name of the VServer group.|
|BackendServers|List|A list of backend servers.|

|Name |Type|Required|
|:----|:---|:-------|
|ServerId|String|The ID of the ECS instance.|
|Port|Integer|The port of the backend server.|
|Weight|Integer|The weight of the backend server.|
|Type |String|The type of the backend server. Valid value:-   ecs: ECS instance \(Default\)
-   eni: Elastic Network Interface \(ENI\)

|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DescribeVServerGroupAttributeResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
    	<VServerGroupName>Group1</VServerGroupName>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-232</ServerId>
    			<Port>80</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-233</ServerId>
    			<Port>90</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </DescribeVServerGroupAttributeResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
      "VServerGroupId": "rsp-cige6j5e7p",
      "VServerGroupName": "Group1",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "vm-233",
            "Port": "80",
            "Weight": "100"
          },
          {
            "ServerId": "vm-232",
            "Port": "90",
            "Weight": "100"
          }
        ]
      }
    }
    ```


