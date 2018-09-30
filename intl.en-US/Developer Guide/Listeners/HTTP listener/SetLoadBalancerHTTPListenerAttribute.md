# SetLoadBalancerHTTPListenerAttribute {#slb_api_SetLoadBalancerHTTPListenerAttribute .reference}

Modify the configurations of an HTTP listener.

## Request parameters {#section_bqw_c1g_cz .section}

|Name |Type|Required| Description|
|:----|:---|:-------|:-----------|
|Action |String | Yes|The action to perform.  Valid value: SetLoadBalancerHTTPListenerAttribute

|
|RegionId|String | Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of the SLB instance.|
|ListenerPort|Integer|Yes|The frontend port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.\[1, 65535\]

|
|VServerGroup|String| No|Whether to use the VServer group. Valid value:on | off \(default\)

|
|VServerGroupId|String| No|The ID of the VServer group.This parameter must be specified if the value of the VServerGroup parameter is on.

|
|Bandwidth|Integer|Yes|The peak bandwidth of the listener. Valid value:-   -1: The peak bandwidth is not limited.
-   \[1-5000\]: The peak bandwidth of the listener. The sum of the peak bandwidths of all listeners under an instance cannot exceed the bandwidth of that instance.

|
|AclStatus|String| No|Whether to enable access control.Valid value: on | off \(default\)

|
|AclType|String| No|Select an access control method after enabling the access control function:-   white: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks.  After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   black: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


This parameter is required when the value of the AclStatus parameter is set to on.

|
|AclId|String| No|Select an access control list as the whitelist or the blacklist. This parameter is required when the value of the AclStatus parameter is set to on.

|
|XForwardedFor|String| No|Whether to use the XForwardedFor header to obtain the real IP address of the client. Valid value: on \(default\) | off

|
|XForwardedFor\_SLBIP|String| No|Whether to use the XForwardedFor\_SLBIP header to obtain the real IP address of the client request. Valid value:on  | off \(default\)

|
|XForwardedFor\_SLBID|String| No|Whether to use the XForwardedFor header to obtain the ID of the SLB instance. Valid value:on | off \(default\)

|
|XForwardedFor\_proto|String| No|Whether to use the XForwardedFor\_proto header to obtain the protocol used by the listener. Valid value:on | off \(default\)

|
|Scheduler|String| No|The algorithm used to distribute traffic. Valid value:-   wrr \(Default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   wlc: A server with a higher weight will receive a larger percentage of live connections at any one time. When the weight value is the same, a backend server with a smaller number of connections is more frequently \(and probably\) accessed.
-   rr: Requests are evenly and sequentially distributed to the backend servers.

|
|StickySession|String | Yes|Whether to enable session persistence. Valid value:on | off

|
|StickySessionType|String| No|The method used to handle the cookie. Valid values:-   insert: Insert the cookie.

Server Load Balancer adds a session cookie to the first response from the backend server and identifies the server which has sent the response. The next request will contain the cookie and the listener will distribute the request to the same backend server.

-   server: You can set the cookie name in the response.

Server Load Balancer will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access the Server Load Balancer, the listener will distribute the request to the previously recorded backend server.

**Note:** When the value of the StickySession parameter is set to on, this parameter is required.


|
|CookieTimeout|Integer|No |The cookie timeout in seconds. Valid value: \[1,86400\]

**Note:** This parameter is required when the value of the StickySession parameter is on, and the value of the StickySessionType parameter is insert.

|
|Cookie|String| No|The cookie configured on the backend server.The cookie must be 1-200 characters in length and can only contain ASCII characters and numbers. It cannot contain commas, semicolons or spaces, nor can it begin with $.

This parameter is required when the value of the StickySession parameter is on and the value of the StickySessionType parameter is server.

|
|HealthCheck|String | Yes|Whether to enable health check. Valid value:on | off

|
|HealthCheckDomain|String| No|The domain name used for health check. Valid value:-   $\_ip: The private IP of the backend server. When an IP is specified or the health check domain is not specified, Server Load Balancer uses private IPs of backend servers as the domain names for health check.
-   domain: The domain name can be 1-80 characters in length, and can only contain letters, numbers, periods, or hyphens \(-\).

|
|HealthCheckURI|String| No|The URI used for health check.|
|HealthCheckConnectPort|Integer|No |The port used for health check. Valid value:-   1-65535: The port opened on the backend server to do health check.

|
|HealthyThreshold|Integer|No |The number of consecutive successes of health check performed by the same LVS mode server on the same ECS instance \(from failure to success\).Valid value: 2-10

|
|UnhealthyThreshold|Integer|No |The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance \(from success to failure\).Valid value: 2-10

|
|HealthCheckTimeout|Integer|No |The amount of time in seconds to wait for the response from a health check. If an ECS instance sends no response within the specified timeout period, the health check fails.Valid value: 1-300 \(seconds\)

**Note:** If the value of the HealthCheckInterval parameter is greater than the value of the HealthCHeckTimeout parameter, the HealthCHeckTimeout parameter is invalid, and the timeout is set to the value of the HealthCheckInterval parameter.

|
|HealthCheckInterval|Integer|No |The time interval between two consecutive health checks.Valid value: 1-50 \(seconds\)

|
|HealthCheckHttpCode|String| No|The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by commas.Valid value: http\_2xx \(default\) | http\_3xx | http\_4xx | http\_5xx

|
|Gzip|String| No| Whether to enable the Gzip compression.

 Valid value: on \(default\) | off

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetLoadBalancerHTTPListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&Bandwidth=-1
&HealthCheck=on
&HealthCheckDomain=$_ip
&HealthCheckURI=/test/index.html
&HealthCheckConnectPort=8080
&HealthyThreshold=4
&UnhealthyThreshold=4
&HealthCheckTimeout=3
&HealthCheckInterval=5
&VServerGroupId=rsp-cige6j5e7p
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetLoadBalancerHTTPListenerAttributeResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetLoadBalancerHTTPListenerAttributeResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


