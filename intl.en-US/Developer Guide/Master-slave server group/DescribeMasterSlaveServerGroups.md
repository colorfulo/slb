# DescribeMasterSlaveServerGroups {#reference_jn1_kzd_ndb .reference}

Query created active/standby server groups.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Parameters|Required|Description|
|:---|:---------|:-------|:----------|
|Action|String| Yes|The action to perform. Valid value:DescribeMasterSlaveServerGroups

|
|RegionId|String| Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String|Yes|The ID of the Server Load Balancer instance.|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Required|
|:---|:---|:-------|
|RequestId|String|The ID of the request.|
|MasterSlaveServerGroupId|String|The ID of the active/standby server group.|
|MasterSlaveServerGroupName|String|The name of the active/standby server group.|
|MasterSlaveBackendServers|List|A list of active/standby server groups.|

|Name|Type|Required|
|:---|:---|:-------|
|ServerId|String|The ID of the ECS instance.|
|Port|String|The port used by the backend server.Valid value: 1-65535

|
|Weight|String| The weight of the backend server. Valid value: \[0,100\]

 The default value is 100. If the value is 0, no requests will be forwarded to the backend server.

 |
|ServerType|String|The role of the backend server. Valid value:Master \(default\) | Slave

|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeMasterSlaveServerGroups
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DescribeMasterSlaveServerGroupsResponse>
        <RequestId>2631BB5E-B576-4925-BDED-07A66D23E5DE</RequestId>
        <MasterSlaveServerGroups>
    	<MasterSlaveServerGroup>
    		<MasterSlaveServerGroupId>rsp-bp1ro3mwp2x2m</MasterSlaveServerGroupId>
    		<MasterSlaveServerGroupName>test</MasterSlaveServerGroupName>
    	</MasterSlaveServerGroup>
        </MasterSlaveServerGroups>
    </DescribeMasterSlaveServerGroupsResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "2631BB5E-B576-4925-BDED-07A66D23E5DE",
      "MasterSlaveServerGroups": {
        "MasterSlaveServerGroup": [
          {
            "MasterSlaveServerGroupId": "rsp-bp1ro3mwp2x2m",
            "MasterSlaveServerGroupName": "test"
          }
        ]
      }
    }
    ```


