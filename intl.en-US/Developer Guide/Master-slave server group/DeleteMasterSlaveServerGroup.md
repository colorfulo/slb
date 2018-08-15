# DeleteMasterSlaveServerGroup {#reference_fvz_rxd_ndb .reference}

Delete a specified master-slave server group.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:DeleteMasterSlaveServerGroup

|
|RegionId|String|Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|MasterSlaveServerGroupId|String|Yes|The ID of the master-slave server group to be deleted.**Note:** A master-slave server group in use cannot be deleted.

|

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Response parameters {#section_ssd_pds_cz .section}

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=CreateMasterSlaveServerGroup
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&MasterSlaveServerGroupName=Group1
&MasterSlaveBackendServers=[
    {"ServerId":"vm-233","Port":"80","Weight":"100","ServerType":"Master"},
    {"ServerId":"vm-232","Port":"90","Weight":"100","ServerType":"Slave"},
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DeleteMasterSlaveServerGroupResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    </DeleteMasterSlaveServerGroupResponse>
    ```

-   JSON format

    ```screen
    {
      "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
    }
    ```


