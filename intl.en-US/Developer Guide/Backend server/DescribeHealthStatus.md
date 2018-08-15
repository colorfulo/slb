# DescribeHealthStatus {#reference_as4_5md_ndb .reference}

Query the health status of the backend servers.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Parameters|Required|Description|
|:----|:---------|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:DescribeHealthStatus

|
|RegionId|String| Yes|The region ID of the SLB instance.|
|LoadBalancerId|String | Yes|The ID of the SLB instance.|
|ListenerPort|Integer|No |The front-end port of the listener. Valid value:Valid value: 1-65535

**Note:** If no port is specified, the health check status of all ports is returned.

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|BackendServers|List|A list of backend servers.|

|Name |Type|Description|
|:----|:---|:----------|
|ServerId|String|The ID of the ECS instance|
|ServerHealthStatus|String|The health check status of the backend server:-   normal: The backend server is healthy.
-   abnormal: The backend server is unhealthy.
-   unavailable: The health check is not completed yet.

|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeHealthStatus
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DescribeHealthStatusResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-233</ServerId>
    			<ServerHealthStatus>normal</ServerHealthStatus>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-234</ServerId>
    			<ServerHealthStatus>abnormal</ServerHealthStatus>
    		</BackendServer>
    	</BackendServers>
    </DescribeHealthStatusResponse>
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
            "ServerHealthStatus": "normal"
          },
          {
            "ServerId": "vm-234",
            "ServerHealthStatus": "abnormal"
          }
        ]
      }
    }
    ```


