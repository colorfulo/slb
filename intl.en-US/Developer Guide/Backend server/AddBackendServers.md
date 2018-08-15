# AddBackendServers {#reference_u1m_3pc_ndb .reference}

Add backend servers to a Server Load Balancer \(SLB\) instance.

**Note:** If the ECS instance has already been added, the ECS instances will be ignored.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required| Description|
|:---|:---|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:AddBackendServers

|
|LoadBalancerId|String | Yes|The ID of the Server Load Balancer instance.|
|BackendServers|StringList

|Yes|The list of backend servers to be added.**Note:** Only backend servers in the running status can be added. You can add up to 20 backend servers at a time.

|

|Name |Parameters|Required| Description|
|:----|:---------|:-------|:-----------|
|ServerId|String | Yes|The ID of the ECS instance.|
|Weight|Integer|No |The weight of the backend server. Valid value: \[0,100\]The default value is 100. If the value is 0, no requests will be forwarded to the backend server.

|
|Type |String | Yes|The type of the backend server. Valid value:-   ecs: ECS instance \(Default\)
-   eni: Elastic Network Interface \(ENI\)

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Required|
|:---|:---|:-------|
|RequestId|String|The ID of the request.|
|LoadBalancerId|String|The ID of the SLB instance.|
|BackendServers|List|A list of backend servers.|

|Name |Type|Required|
|:----|:---|:-------|
|ServerId|String|The ID of the ECS instance|
|Weight|Integer|The weight of the backend server.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=AddBackendServers
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&BackendServers=[
    {"ServerId":" vm-233","Weight":"100"},
    {"ServerId":" vm-234","Weight":"100"}]
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <AddBackendServersResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-231</ServerId>
    			<Weight>100</Weight>
                            <Type>eni</Type>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>eni-233</ServerId>
    			<Weight>100</Weight>
                            <Type>eni</Type>
    		</BackendServer>
    	</BackendServers>
    </AddBackendServersResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "LoadBalancerId": "139a00604ad-cn-east-hangzhou-01",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "eni-231",
            "Weight": 100,
            "Type":"eni",
          },
          {
            "ServerId": "eni-233",
            "Weight": 100,
            "Type":"eni"
          }
        ]
      }
    }
    ```


