# RemoveBackendServers {#reference_amf_hjd_ndb .reference}

Remove one or more ECS instances from the default backend server group.

**Note:** No error will be returned if an ECS instance to be removed does not exist in the default backend server group.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Parameters|Required| Description|
|:----|:---------|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:RemoveBackendServers

|
|RegionId|String | Yes|The region ID of Server Load Balancer instance.|
|LoadBalancerId|String | Yes|The ID of the Server Load Balancer instance.|
|BackendServers| List

 |Yes|A list of backend servers to remove.**Note:** Up to 20 backend servers can be removed at a time.

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|LoadBalancerId|String|The ID of the SLB instance.|
|BackendServers|List|The list of backend servers.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=RemoveBackendServers
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&BackendServers=["i-bp143t8c5uralrxxxx","i-bp12zdi79965uxxxx"]
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <RemoveBackendServersResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-231</ServerId>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-232</ServerId>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </RemoveBackendServersResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "LoadBalancerId": "139a00604ad-cn-east-hangzhou-01",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "vm-233",
            "Weight": 100
          },
          {
            "ServerId": "vm-234",
            "Weight": 100
          }
        ]
      }
    }
    ```


