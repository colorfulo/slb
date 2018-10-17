# SetLoadBalancerUDPListenerAttribute {#slb_api_SetLoadBalancerUDPListenerAttribute .reference}

Modify the configurations of a UDP listener.

## Request parameters {#section_bqw_c1g_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String| Yes|The action to perform. Valid value:SetLoadBalancerUDPListenerAttribute

|
|RegionId|String|Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String|Yes|The ID of the SLB instance for which the UDP listener is created.|
|ListenerPort|Integer|Yes|The frontend port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.Valid values:1-65535

|
|VServerGroupId|String|No|The ID of the VServer group.|
|MasterSlaveServerGroupId|String|No|The ID of the active/standby server group.**Note:** The VServerGroupId parameter and the MasterSlaveServerGroupId parameter cannot be specified at the same time.

|
|Bandwidth|Integer|Yes|The peak bandwidth of the listener. Valid values:-   -1: The peak bandwidth is not limited.
-   \[1-5000\]: The peak bandwidth of the listener. The total peak bandwidth for all listeners cannot exceed the peak bandwidth for the instance.

|
|Scheduler|String|No|The algorithm used to distribute traffic. Valid values:-   wrr: Backend servers with higher weights receive more requests than those with smaller weights.
-   wlc: A server with a higher weight will receive a larger percentage of live connections at any one time. If the weights are the same, the system directs network connections to the server with the fewest established connections.
-   rr: Requests are evenly and sequentially distributed to the backend servers.
-   sch: The consistent hash based on the source IP address. The same source IP addresses are scheduled to the same backend server. 
-   tch: The consistent hash based on the quaternion \(source IP + destination IP + source port + destination port\). The same streams are scheduled to the same backend server.
-   qch: The consistent hash based on the QUIC Connection ID. The same QUIC Connection IDs are scheduled to the same backend servers.

**Note:** Only guaranteed-performance instances support sch, tch and qch consistent hash.

|
|AclStatus|String|No|Whether to enable access control.|
|AclType|String|No|Select an access control method after enabling the access control function:-   white: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   black: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


This parameter is required when the value of the AclStatus parameter is set to on.

|
|AclId|String|No|Select an access control list as the whitelist or the blacklist.This parameter is required if the value of the AclStatus parameter is on.

|
|HealthCheckConnectPort|Integer|No|The port used for health check. Valid values:1-65535: The port opened on the backend server to do health check.

|
|HealthyThreshold|Integer|No|The number of consecutive successes of health check performed by the same LVS node server on the same ECS instance before the ECS instance is declared as healthy \(from failure to success\).Valid values: 2-10

|
|UnhealthyThreshold|Integer|No|The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance before the ECS instance is declared as unhealthy \(from success to failure\).Valid values: 2-10

|
|HealthCheckConnectTimeout|Integer|No|The amount of time to wait for the response from the health check. If the backend ECS instance does not make correct response in the specified time, the health check fails.Valid values: 1-300 \(seconds\)

**Note:** If the value of the HealthCheckInterval parameter is greater than the value of the HealthCHeckTimeout parameter, the HealthCHeckTimeout parameter is invalid, and the timeout is set to the value of the HealthCheckInterval parameter.

|
|HealthCheckInterval|Integer|No|The time interval between two consecutive health checks.Valid values: 1-50 \(seconds\)

|
|HealthCheckReq|String|No|Request string for UDP health check. Only English letters, digits are allowed. Up to 500 characters can be entered.|
|HealthCheckExp|String|No|Response string for UDP listener check. Only English letters, digits are allowed. Up to 500 characters can be entered.|
|VServerGroup|String|No|Whether to use a VServer group.Valid value: on|off

**Note:** The value of VserverGroup and the value of MasterSlaveServerGroup cannot be on at the same time.

|
|MasterSlaveServerGroup|String|No|Whether to use an active/standby server group.Valid values: on|off

**Note:** The value of VserverGroup and the value of MasterSlaveServerGroup cannot be on at the same time.

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name |Type|Description|
|:----|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetLoadBalancerUDPListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=443
&Bandwidth=-1
&VServerGroupId=rsp-cige6j5e7p
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetLoadBalancerUDPListenerAttributeResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetLoadBalancerUDPListenerAttributeResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


