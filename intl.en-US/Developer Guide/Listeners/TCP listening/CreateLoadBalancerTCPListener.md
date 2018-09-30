# CreateLoadBalancerTCPListener {#slb_api_CreateLoadBalancerTCPListener .reference}

Create a TCP listener.

**Note:** After the listener is created, the listener status is stopped. After the listener is created, call the StartLoadBalancerListener API to start the listener to distribute traffic.

## Request parameters {#section_bqw_c1g_cz .section}

|Name|Type|Required|Description |
|:---|:---|:-------|:-----------|
|Action|String| Yes|The action to perform. Valid value: CreateLoadBalancerTCPListener

|
|RegionId|String| Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String| Yes|The ID of the SLB instance for which the UDP listener is created.|
|ListenerPort|Integer|Yes|The frontend port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers. Valid value:\[1, 65535\]

|
|BackendServerPort|Integer| Yes|The port opened on the backend server to receive requests. Valid value:1-65535

**Note:** If the VServerGroupId parameter is not specified, this parameter is required.

|
|VServerGroupId|String| No|The ID of the VServer group.|
|MasterSlaveServerGroupId|String| No|The ID of the active/standby server group.**Note:** The VServerGroupId parameter and the MasterSlaveServerGroupId parameter cannot be specified at the same time.

|
|Bandwidth|Integer| Yes|The peak bandwidth of the listener. Valid value:-   -1: The peak bandwidth is not limited.
-   \[1-5000\]: The peak bandwidth of the listener. The total peak bandwidth for all listeners cannot exceed the peak bandwidth for the instance.

|
|Scheduler|String| No|The algorithm used to distribute traffic. Valid value:-   wrr \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   wlc: A server with a higher weight will receive a larger percentage of live connections at any one time. If the weights are the same, the system directs network connections to the server with the fewest established connections.
-   rr: Requests are evenly and sequentially distributed to the backend servers.
-   sch: The consistent hash based on the source IP address. The same source IP addresses are scheduled to the same backend server. 
-   tch: The consistent hash based on the quaternion \(source IP + destination IP + source port + destination port\). The same steams are scheduled to the same backend server.

**Note:** Only guaranteed-performance instances support sch and tch consistent hash.

|
|PersistenceTimeout|Integer| No|The timeout value of the session persistence.Valid value: 0-3600 \(seconds\)

The default value is 0. When the default value is used, the session persistence function is disabled.

|
|EstablishedTimeout|Integer| No| The timeout value of the TCP connection in seconds.

 Valid value: 10-900 \(seconds\)

 |
|Description|String| No| Configure the description of the listener.

 |
|AclStatus|String| No| Whether to enable access control.

 Valid value: on | off \(default\)

 |
|AclType|String| No| Select an access control method after enabling the access control function:

 -   white: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   black: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


 This parameter is required when the value of the AclStatus parameter is set to on.

 |
|AclId|String| No| Select an access control list as the whitelist or the blacklist. 

 This parameter is required when the value of the AclStatus parameter is set to on.

 |
|HealthCheckType|String|No| Select a health check method.

 Valid value: tcp \(default\) | http

 |
|HealthCheckDomain|String| No|The domain name used for health check. Valid value:-   $\_ip: The private IP of the backend server. When the $\_ip is specified or the health check domain is not specified, Server Load Balancer uses private IPs of backend servers as the domain names for health check.
-   domain: The domain name can be 1-80 characters in length, and can only contain letters, numbers, periods, or hyphens.

**Note:** This parameter is not required when the TCP health check method is used.

|
|HealthCheckURI|String| No|The URI used for health check.**Note:** This parameter is not required when the TCP health check method is used.

|
|HealthCheckConnectPort|Integer|No| The port used for health check. Valid value:

 -   -520: The backend port that uses the listener configurations by default.
-   1-65535: The port opened on the backend server to do health check.

 |
|HealthyThreshold|Integer| No|The number of consecutive successes of health check performed by the same LVS mode server on the same ECS instance \(from failure to success\).Valid value: 2-10

|
|UnhealthyThreshold|Integer| No|The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance \(from success to failure\).Valid value: 2-10

|
|HealthCheckConnectTimeout|Integer| No| The amount of time to wait for the response from the health check. If an ECS instance sends no response within the specified timeout period, the health check fails.

 Valid value: 1-300 \(seconds\)

 **Note:** If the value of the HealthCheckInterval parameter is greater than the value of the HealthCHeckTimeout parameter, the HealthCHeckTimeout parameter is invalid, and the timeout is set to the value of the HealthCheckInterval parameter.

 |
|HealthCheckInterval|Integer| No| The time interval between two consecutive health checks.

 Valid value: 1-50 \(seconds\)

 |
|HealthCheckHttpCode|String| No| The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by commas.

 Valid value: http\_2xx \(default\) | http\_3xx | http\_4xx | http\_5xx

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String |The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=CreateLoadBalancerTCPListener
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=443
&BackendServerPort=443
&Bandwidth=-1
&VServerGroupId=rsp-cige6j5e7p
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <CreateLoadBalancerTCPListenerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </CreateLoadBalancerTCPListenerResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


