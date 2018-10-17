# DescribeLoadBalancerHTTPSListenerAttribute {#slb_api_DescribeLoadBalancerHTTPSListenerAttribute .reference}

Query the configurations of an HTTPS listener.

## Request parameters {#section_ow5_23c_ndb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String| Yes|The action to perform. Valid value: DescribeLoadBalancerHTTPSListenerAttribute

|
|RegionId|String|Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String|Yes|The ID of the SLB instance.|
|ListenerPort|Integer|Yes|The frontend port used by the SLB instance.Valid values: 1-65535

|

## Response parameters {#section_qw5_23c_ndb .section}

|Name |Type|Description|
|:----|:---|:----------|
|RequestId|String |The ID of the request.|
|ListenerPort|Integer|The frontend port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.|
|BackendServerPort|Integer|The backend port used by the SLB instance.|
|Bandwidth|Integer|The peak bandwidth of the listener.|
|Status|String|The status of the listener. Valid values:starting | running | configuring | stopping |

|
|XForwardedFor|String|Whether to use the XForwardedFor header to obtain the real IP address of the client.|
|XForwardedFor\_SLBIP|String|Whether to use the XForwardedFor\_SLBIP header to obtain the real IP address of the client request.|
|XForwardedFor\_SLBID|String|Whether to use the XForwardedFor\_SLBID header to obtain the ID of the SLB instance.|
|XForwardedFor\_proto|String|Whether to use the XForwardedFor\_proto header to obtain the protocol used by the listener.|
|Scheduler|String|The algorithm used to distribute traffic.|
|StickySession|String|Whether to enable session persistence.|
|StickySessionType|String|The method used to process the cookie.|
|CookieTimeout|Integer|The timeout of the cookie.|
|Cookie|String|The cookie configured on the backend server.|
|AclStatus|String|Whether to enable the access control.Valid values: on | off \(default\)

|
|AclType|String|Select an access control method after enabling the access control function:-   white: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access Server Load Balancer. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   black: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


This parameter is required when the value of the AclStatus parameter is set to on.

|
|AclId|String|The ID of the access control list bound to the listener.If the value of the AclStatus parameter is on, this parameter is required.

|
|HealthCheck|String|Whether to enable health check.|
|HealthCheckDomain|String|The domain name used for health check.|
|HealthCheckURI|String|The URL used for health check.|
|HealthyThreshold|Integer|The number of consecutive successes of health check performed by the same LVS node server on the same ECS instance before the ECS instance is declared as healthy \(from failure to success\).|
|UnhealthyThreshold|Integer|The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance before the ECS instance is declared as unhealthy \(from success to failure\).|
|HealthCheckTimeout|Integer|The maximum amount of time in seconds to wait for the response from a health check. |
|HealthCheckInterval|Integer|The time interval between two consecutive health checks.|
|HealthCheckHttpCode|String|The HTTP status code indicating that the health check is normal.|
|HealthCheckConnectPort|Integer|The port used for health check.|
|VServerGroupId|String|The ID of the VServer group.|
|ServerCertificateId|String|The ID of the server certificate.|
|CACertificateId|String|The ID of the CA certificate.|
|Gzip|String|Whether to enable Gzip compression.|
|Rules|List|A list of forwarding rules. For more information, see [RuleList](#section_yb2_nrf_j2b).|
|DomainExtensionList|String|A list of domain name extensions. For more information, see [DomainExtensions](#section_gyt_4bn_s2b).|
|EnableHttp2|String|Whether to enable the HTTP/2 feature.Valid values: on \(default\) | off

|
|TLSCipherPolicy|String| You can only specify the TLSCipherPolicy parameter for guaranteed-performance instances. Each security policy includes the TLS protocol versions that can be selected by HTTPS and the supporting cipher suites.

 The following four security policies are supported currently. For more information, see [Differences along TLS security policies](#section_ppb_3nw_32b). Select the policy according to actual situation.

 -   tls\_cipher\_policy\_1\_0:
    -   Supported TLS versions: TLSv1.0, TLSv1.1, and TLSv1.2.
    -   Supported encryption algorithm suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA and DES-CBC3-SHA.
-   tls\_cipher\_policy\_1\_1:
    -   Supported TLS versions: TLSv1.1 and TLSv1.2.
    -   Supported encryption algorithm suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA and DES-CBC3-SHA.
-   tls\_cipher\_policy\_1\_2
    -   Supported TLS version: TLSv1.2.
    -   Supported encryption algorithm suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA and DES-CBC3-SHA.
-   tls\_cipher\_policy\_1\_2\_strict
    -   Supported TLS version: TLSv1.2.
    -   Supported encryption algorithm suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-RSA-AES128-SHA and ECDHE-RSA-AES256-SHA.

 |

## Differences along TLS security policies {#section_ppb_3nw_32b .section}

|policy|tls\_cipher\_policy\_1\_0|tls\_cipher\_policy\_1\_1|tls\_cipher\_policy\_1\_2|tls\_cipher\_policy\_1\_2\_strict|
|------|-------------------------|-------------------------|-------------------------|---------------------------------|
|TLS| |1.2/1.1/1.0|1.2/1.1|1.2|1.2|
|CIPHER|ECDHE-RSA-AES128-GCM-SHA256|✔|✔|✔|✔|
|ECDHE-RSA-AES256-GCM-SHA384|✔|✔|✔|✔|
|ECDHE-RSA-AES128-SHA256|✔|✔|✔|✔|
|ECDHE-RSA-AES256-SHA384|✔|✔|✔|✔|
|AES128-GCM-SHA256|✔|✔|✔| |
|AES256-GCM-SHA384|✔|✔|✔| |
|AES128-SHA256|✔|✔|✔| |
|AES256-SHA256|✔|✔|✔| |
|ECDHE-RSA-AES128-SHA|✔|✔|✔|✔|
|ECDHE-RSA-AES256-SHA|✔|✔|✔|✔|
|AES128-SHA|✔|✔|✔| |
|AES256-SHA|✔|✔|✔| |
|DES-CBC3-SHA|✔|✔|✔| |

## DomainExtensions {#section_gyt_4bn_s2b .section}

|Name|Type|Description|
|----|----|-----------|
|DomainExtensionId|String|The ID of the domain name extension.|
|Domain|String|The domain name.|
|ServerCertificateId|String|The ID of the certificate corresponding to the domain name.|

## RuleList {#section_yb2_nrf_j2b .section}

|Name|Type|Description|
|----|----|-----------|
|RuleId|String|The ID of the forwarding rule.|
|RuleName|String|The name of the forwarding rule.|
|Domain|String|The domain name.|
|Url|String|The request URL.|
|VServerGroupId|String|The ID of the target VServer group of the forwarding rule.|

## Examples {#section_sw5_23c_ndb .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerHTTPSListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
& Listenerport = 443
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DescribeLoadBalancerHTTPSListenerAttributeResponse>  
        <RequestId>11F52428-64ED-40F7-98C2-DBB6D0BB0AD7</RequestId>
        <HealthCheckHttpCode>http_2xx,http_3xx</HealthCheckHttpCode>
        <HealthCheckTimeout>5</HealthCheckTimeout>
        <ServerCertificateId>1231579085529123_15dbf6ff26f_1991415478_2054196746</ServerCertificateId>
        <XForwardedFor_SLBID>off</XForwardedFor_SLBID>
        <Gzip>on</Gzip>
        <HealthyThreshold>3</HealthyThreshold>
        <Scheduler>wrr</Scheduler>
        <StickySession>off</StickySession>
        <UnhealthyThreshold>3</UnhealthyThreshold>
        <XForwardedFor_SLBIP>off</XForwardedFor_SLBIP>
        <XForwardedFor_proto>off</XForwardedFor_proto>
        <Bandwidth>-1</Bandwidth> 
        <HealthCheckURI>/</HealthCheckURI>
        <VServerGroupId>rsp-0xiju72xwnr93</VServerGroupId>
        <HealthCheck>on</HealthCheck>
        <ListenerPort>443</ListenerPort>
        <Status>running</Status>
        <XForwardedFor>on</XForwardedFor>
        <HealthCheckDomain></HealthCheckDomain>
        <HealthCheckInterval>2</HealthCheckInterval>
        <BackendServerPort>443</BackendServerPort>
    </DescribeLoadBalancerHTTPSListenerAttributeResponse>
    ```

-   JSON format

    ```
    {
      "RequestId":"11F52428-64ED-40F7-98C2-DBB6D0BB0AD7",
       "HealthCheckHttpCode":"http_2xx,http_3xx",
       "HealthCheckTimeout":5,
       "ServerCertificateId":"1231579085529123_15dbf6ff26f_1991415478_2054196746",
       "XForwardedFor_SLBID":"off",
       "Gzip":"on",
       "HealthyThreshold":3,
       "Scheduler":"wrr",
       "StickySession":"off",
       "UnhealthyThreshold":3,
       "XForwardedFor_SLBIP":"off",
       "XForwardedFor_proto":"off",
       "Bandwidth":-1,
       "HealthCheckURI":"/",
       "VServerGroupId":"rsp-0xiju72xwnr93",
       "HealthCheck":"on",
       "ListenerPort":443,
       "Status":"running",
       "XForwardedFor":"on",
       "HealthCheckDomain":"",
       "HealthCheckInterval":2,
       "BackendServerPort":443
    }
    ```


