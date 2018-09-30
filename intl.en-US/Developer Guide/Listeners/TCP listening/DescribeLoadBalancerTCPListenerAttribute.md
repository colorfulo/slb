# DescribeLoadBalancerTCPListenerAttribute {#slb_api_DescribeLoadBalancerTCPListenerAttribute .reference}

Query the configurations of a TCP listener.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform.  Valid value:DescribeLoadBalancerTCPListenerAttribute

|
|RegionId|String | Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of the SLB instance.|
|ListenerPort|Integer|Yes|The frontend port used by the SLB instance.Valid value: 1-65535

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|ListenerPort|Integer|The frontend port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.|
|BackendServerPort|Integer|The port opened on the backend server to receive requests.|
|Bandwidth|Integer|The peak bandwidth of the listener.|
|Status|String|The status of the listener. Valid value:Starting | running | configuring | stopping | stopped

|
|Scheduler|String|The scheduling algorithm.-   wrr \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   wlc: A server with a higher weight will receive a larger percentage of live connections at any one time. When the weight value is the same, a backend server with a smaller number of connections is more frequently \(and probably\) accessed.
-   rr: Requests are evenly and sequentially distributed to the backend servers.

|
|VServerGroupId|String|The ID of the VServer group.|
|MaterSlaveServerGroupId|String|The ID of the active/standby server group.|
|PersistenceTimeout|String|Whether the session persistence is enabled. The session persistence is not enabled when the value is 0.|
|EstablishedTimeout|String|The connection timeout.|
|HealthCheckType|String|The health check method used by the TCP listener.|
|HealthCheck|String|Whether to enable health check.|
|AclStatus|String|Whether to enable the access control.Valid value: on | off \(default\)

|
|AclType|String| Select an access control method after enabling the access control function:

 -   white: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks.  After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   black: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


 This parameter is required when the value of the AclStatus parameter is set to on.

 |
|AclId|String|The ID of the access control list bound to the listener.This parameter is required when the value of the AclStatus parameter is set to on.

|
|HealthyThreshold|Integer|The number of consecutive successes of health check performed by the same LVS mode server on the same ECS instance \(from failure to success\).|
|UnhealthyThreshold|Integer|The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance \(from success to failure\).|
|HealthCheckConnectTimeout|Integer|The timeout value.|
|HealthCheckConnectTimeout|Integer|The maximum amount of time in seconds to wait for the response from a health check. |
|HealthCheckInterval|Integer|The time interval in seconds of health check.|
|HealthCheckDomain|String|The domain name used for health check.|
|HealthCheckURI|String|The URI used for the health check.|
|HealthCheckHttpCode|String|The HTTP status code indicating that the health check is normal.|
|SynProxy|String|Whether to enable SynProxy. SynProxy protects SLB from attacks.We recommend that you do not adjust this parameter and use the value set by SLB.

Valid value:

-   enable: Enable
-   disable: Disable

|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerTCPListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DescribeLoadBalancerTCPListenerAttributeResponse>
        <RequestId>73B5E961-8E7B-4CF9-9DA9-1BDC25CC7A47</RequestId>
        <HealthCheckHttpCode></HealthCheckHttpCode>
        <PersistenceTimeout>0</PersistenceTimeout>
        <HealthCheckType>tcp</HealthCheckType>
        <HealthyThreshold>3</HealthyThreshold>
        <Scheduler>wrr</Scheduler>
        <UnhealthyThreshold>3</UnhealthyThreshold>
        <Bandwidth>-1</Bandwidth>
        <HealthCheckURI></HealthCheckURI>
        <HealthCheck>on</HealthCheck>
        <HealthCheckConnectTimeout>5</HealthCheckConnectTimeout>
        <ListenerPort>80</ListenerPort>
        <Status>running</Status>
        <EstablishedTimeout>900</EstablishedTimeout>
        <HealthCheckDomain></HealthCheckDomain>
        <HealthCheckInterval>2</HealthCheckInterval>
        <BackendServerPort>80</BackendServerPort>
    </DescribeLoadBalancerTCPListenerAttributeResponse>
    ```

-   JSON format

    ```
    {
       "RequestId":"73B5E961-8E7B-4CF9-9DA9-1BDC25CC7A47",
       "HealthCheckHttpCode":"",
       "PersistenceTimeout":0,
       "HealthCheckType":"tcp",
       "HealthyThreshold":3,
       "Scheduler":"wrr",
       "UnhealthyThreshold":3,
       "Bandwidth":-1,
       "HealthCheckURI":"",
       "HealthCheck":"on",
       "HealthCheckConnectTimeout":5,
       "ListenerPort":80,
       "Status":"running",
       "EstablishedTimeout":900,
       "HealthCheckDomain":"",
       "HealthCheckInterval":2,
       "BackendServerPort":80
    }
    ```


