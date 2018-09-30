# DescribeLoadBalancerHTTPListenerAttribute {#slb_api_DescribeLoadBalancerHTTPListenerAttribute .reference}

Query the configurations of an HTTP listener.

## Request parameters {#section_ow5_23c_ndb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action |String |Yes|The action to perform.  Valid value: DescribeLoadBalancerHTTPListenerAttribute

|
|RegionId|String | Yes|The region of Server Load Balancer instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of Server Load Balancer instance.|
|ListenerPort|Integer|Yes|The frontend port used by the Server Load Balancer instance.Valid value: 1-65535

|

## Response parameters {#section_qw5_23c_ndb .section}

|Name |Type|Description|
|:----|:---|:----------|
|RequestId|String|The ID of the request.|
|ListenerPort|Integer|The frontend port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.|
|BackendServerPort|Integer|The port opened on the backend server to receive requests.|
|Bandwidth|Integer|The peak bandwidth of the listener.|
|Status|String|The status of the listener. Valid value:starting | running | configuring | stopping |

|
|XForwardedFor|String|Whether to use the XForwardedFor header to obtain the real IP address of the client.|
|XForwardedFor\_SLBIP|String|Whether to use the XForwardedFor\_SLBIP header to obtain the real IP address of the client request.|
|XForwardedFor\_SLBID|String|Whether to use the XForwardedFor\_SLBID header to obtain the ID of the SLB instance.|
|XForwardedFor\_proto|String|Whether to use the XForwardedFor\_proto header to obtain the protocol used by the listener.|
|Scheduler|String|The algorithm used to distribute traffic. |
|StickySession|String|Whether to enable session persistence.|
|StickySessionType|String|The method used to process the cookie.|
|CookieTimeout|Integer|The timeout of the cookie.|
|cookie|String|The cookie configured on the backend server.|
|AclStatus|String|Whether to enable the access control.Valid value: on | off \(default\)

|
|AclType|String|Select an access control method after enabling the access control function:-   white: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks.  After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   black: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


This parameter is required when the value of the AclStatus parameter is set to on.

|
|AclId|String|The ID of the access control list bound to the listener.This parameter is required when the value of the AclStatus parameter is set to on.

|
|HealthCheck|String|Whether to enable health check.|
|HealthCheckDomain|String|The domain name used for health check.|
|HealthCheckURI|String|The URI used for health check.|
|HealthyThreshold|Integer|The number of consecutive successes of health check performed by the same LVS mode server on the same ECS instance \(from failure to success\).|
|UnhealthyThreshold|Integer|The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance \(from success to failure\).|
|HealthCheckTimeout|Integer|The maximum amount of time in seconds to wait for the response from a health check. |
|HealthCheckInterval|Integer|The time interval between two consecutive health checks.|
|HealthCheckHttpCode|String|The HTTP status code indicating that the health check is normal.|
|HealthCheckConnectPort|Integer|The port used for health check.|
|Gzip|String|Whether to enable Gzip compression.|
|**EnableHttp2**|String|Whether to enable the HTTP/2 feature.Valid value: on \(default\)| off

|
|Rules|List|A list of forwarding rules. For more information, see [RuleList](#section_xpt_mtf_j2b).|

## RuleList {#section_xpt_mtf_j2b .section}

|Name|Type|Description|
|----|----|-----------|
|RuleId|String|The ID of the forwarding rule.|
|RuleName|String|The name of the forwarding rule.|
|Domain|String|The domain name.|
|Url|String|The URL.|
|VServerGroupId|String|The ID of the target VServer group of the forwarding rule.|

## Examples {#section_sw5_23c_ndb .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerHTTPListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DescribeLoadBalancerHTTPListenerAttributeResponse>  
        <RequestId>8D8A6319-F05A-4577-B50D-388B4B30E103</RequestId>
        <HealthCheckHttpCode>http_2xx,http_3xx</HealthCheckHttpCode>
        <CookieTimeout>1000</CookieTimeout>
        <HealthCheckTimeout>5</HealthCheckTimeout>
        <XForwardedFor_SLBID>off</XForwardedFor_SLBID>
        <Gzip>on</Gzip>
        <Scheduler>wrr</Scheduler>
        <HealthyThreshold>3</HealthyThreshold>
        <StickySession>on</StickySession>
        <UnhealthyThreshold>3</UnhealthyThreshold>
        <XForwardedFor_SLBIP>off</XForwardedFor_SLBIP>
        <XForwardedFor_proto>off</XForwardedFor_proto>
        <Bandwidth>-1</Bandwidth>
        <HealthCheckURI>/</HealthCheckURI>
        <VServerGroupId>rsp-bp1kfa2u3y5yw</VServerGroupId>
        <HealthCheck>on</HealthCheck>
        <ListenerPort>8080</ListenerPort>
        <Status>running</Status> 
        <XForwardedFor>on</XForwardedFor>
        <HealthCheckInterval>2</HealthCheckInterval>
        <StickySessionType>insert</StickySessionType>
    </DescribeLoadBalancerHTTPListenerAttributeResponse>
    ```

-   JSON format

    ```
    {
       "RequestId":"8D8A6319-F05A-4577-B50D-388B4B30E103",
       "HealthCheckHttpCode":"http_2xx,http_3xx",
       "CookieTimeout":1000,
       "HealthCheckTimeout":5,
       "XForwardedFor_SLBID":"off",
       "Gzip":"on",
       "Scheduler":"wrr",
       "Maid": 3,
       "StickySession":"on",
       "UnhealthyThreshold":3,
       "XForwardedFor_SLBIP":"off",
       "XForwardedFor_proto":"off",
       "Bandwidth":-1,
       "HealthCheckURI":"/",
       "VServerGroupId":"rsp-bp1kfa2u3y5yw",
       "HealthCheck":"on",
       "ListenerPort":8080,
       "Status":"running",
       "XForwardedFor":"on",
       "HealthCheckInterval":2,
       "StickySessionType":"insert"
    }
    ```


