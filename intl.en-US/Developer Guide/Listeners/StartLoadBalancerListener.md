# StartLoadBalancerListener {#slb_api_StartLoadBalancerListener .reference}

Start a listener.

Note the following when calling this API:

-   The API can be called only when the instance status is stopped.
-   After this API is called, the status of the listener changes to starting.
-   If the status of the SLB instance to which the listener belongs is locked, this API cannot be called.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform.  Valid value:StartLoadBalancerListener

|
|RegionId|String|Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String|Yes|The ID of the Server Load Balancer instance.|
|Listenerport|Integer|Yes|The front-end port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.Valid value: 1-65535

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=StartLoadBalancerListener
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <StartLoadBalancerListenerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </StartLoadBalancerListenerResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


