# Deleteloadbalancerlistener {#slb_api_DeleteLoadBalancerListener .reference}

Delete a listener.

**Note:** Only the listener in the stopped or running status can be deleted.

## Request parameters {#section_a1k_l1c_ndb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform.  Valid value:Deleteloadbalancerlistener

|
|LoadBalancerId|String|Yes|The ID of the Server Load Balancer instance.You can obtain the region ID by calling the DescribeRegions API.

|
|Listenerport|Integer|Yes| The front-end port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.

 Valid value: 1-65535

 |

## Response parameters {#section_c1k_l1c_ndb .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_e1k_l1c_ndb .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteLoadBalancerListener
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DeleteLoadBalancerListenerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </DeleteLoadBalancerListenerResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


