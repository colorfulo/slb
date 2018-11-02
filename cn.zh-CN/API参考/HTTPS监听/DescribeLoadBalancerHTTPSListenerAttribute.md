# DescribeLoadBalancerHTTPSListenerAttribute {#slb_api_DescribeLoadBalancerHTTPSListenerAttribute .reference}

查询HTTPS监听配置。

## 调试 {#section_lqh_1tz_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPSListenerAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_ow5_23c_ndb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：DescribeLoadBalancerHTTPSListenerAttribute

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|ListenerPort|Integer|是|负载均衡实例前端使用的端口。取值：1-65535

|

## 返回参数 {#section_qw5_23c_ndb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|ListenerPort|Integer|负载均衡实例前端使用的端口。|
|BackendServerPort|Integer|负载均衡实例后端使用的端口。|
|Bandwidth|Integer|监听的带宽峰值。|
|Status|String|当前监听的状态。取值：starting | running | configuring | stopping | stopped

|
|XForwardedFor|String|是否开启通过X-Forwarded-For头字段获取访者真实IP。|
|XForwardedFor\_SLBIP|String|是否通过SLB-IP头字段获取客户端请求的真实IP。|
|XForwardedFor\_SLBID|String|是否通过SLB-ID头字段获取负载均衡实例ID。|
|XForwardedFor\_proto|String|是否通过X-Forwarded-Proto头字段获取负载均衡实例的监听协议。|
|Scheduler|String|调度算法。|
|StickySession|String|是否开启会话保持。|
|StickySessionType|String|cookie的处理方式。|
|CookieTimeout|Integer|Cookie超时时间。|
|Cookie|String|服务器上配置的cookie。|
|AclStatus|String|是否开启访问控制功能。取值：on | off（默认值）

|
|AclType|String|访问控制类型：-   white： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发任何请求。

-   black： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


当AclStatus参数的值为on时，该参数必选。

|
|AclId|String|监听绑定的访问策略组ID。当AclStatus参数的值为on时，该参数必选。

|
|HealthCheck|String|是否开启健康检查。|
|HealthCheckDomain|String|用于健康检查的域名。|
|HealthCheckURI|String|用于健康检查的URI。|
|HealthyThreshold|Integer|健康检查阈值。|
|UnhealthyThreshold|Integer|不健康检查阈值。|
|HealthCheckTimeout|Integer|每次健康检查响应的最大超时间，单位为秒。|
|HealthCheckInterval|Integer|健康检查的时间间隔，单位为秒。|
|HealthCheckHttpCode|String|健康检查正常的HTTP状态码。|
|HealthCheckConnectPort|Integer|健康检查的端口。|
|VServerGroupId|String|绑定的服务器组ID。|
|ServerCertificateId|String|服务器证书ID。|
|CACertificateId|String|CA证书ID。|
|Gzip|String|是否开启Gzip压缩。|
|Rules|List|监听下的转发规则列表，具体请参见[RuleList](#section_yb2_nrf_j2b)。|
|DomainExtensions|String|域名扩展列表，具体请参见[DomainExtensions](#section_gyt_4bn_s2b)。|
|EnableHttp2|String|是否开启HTTP/2特性。取值：on（默认值）|off

|
|TLSCipherPolicy|String| 只有性能保障型实例才可以指定TLSCipherPolicy参数，每种policy定义了一种安全策略，安全策略包含HTTPS可选的TLS协议版本和配套的加密算法套件。

 目前支持以下四种安全策略，详细区别请参见[TLS安全策略差异说明](#section_ppb_3nw_32b)，请根据实际情况选择对应的policy。

 -   tls\_cipher\_policy\_1\_0：
    -   支持TLS版本： TLSv1.0、TLSv1.1和TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。
-   tls\_cipher\_policy\_1\_1：
    -   支持TLS版本： TLSv1.1和TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。
-   tls\_cipher\_policy\_1\_2
    -   支持TLS版本：TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。
-   tls\_cipher\_policy\_1\_2\_strict
    -   支持TLS版本：TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、ECDHE-RSA-AES128-SHA和ECDHE-RSA-AES256-SHA。

 |

## TLS安全策略差异说明 {#section_ppb_3nw_32b .section}

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

|名称|类型|描述|
|--|--|--|
|DomainExtensionId|String|域名扩展ID。|
|Domain|String|域名。|
|ServerCertificateId|String|与域名对应的证书ID。|

## RuleList {#section_yb2_nrf_j2b .section}

|名称|类型|描述|
|--|--|--|
|RuleId|String|转发规则ID。|
|RuleName|String|转发规则名称。|
|Domain|String|域名。|
|Url|String|访问路径。|
|VServerGroupId|String|转发规则的目标服务器组ID。|

## 示例 {#section_sw5_23c_ndb .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerHTTPSListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=443
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
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

-   JSON格式

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


