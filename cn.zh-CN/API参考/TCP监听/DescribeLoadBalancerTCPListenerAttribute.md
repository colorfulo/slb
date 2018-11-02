# DescribeLoadBalancerTCPListenerAttribute {#slb_api_DescribeLoadBalancerTCPListenerAttribute .reference}

查询TCP监听配置。

## 调试 {#section_tnj_sx1_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerTCPListenerAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数。取值：DescribeLoadBalancerTCPListenerAttribute

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|ListenerPort|Integer|是|负载均衡实例前端使用的端口。取值：1-65535

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|ListenerPort|Integer|负载均衡实例前端使用的端口。|
|BackendServerPort|Integer|负载均衡实例后端使用的端口。|
|Bandwidth|Integer|监听的带宽峰值。|
|Status|String|当前监听的状态，取值：starting | running | configuring | stopping | stopped

|
|Scheduler|String|调度算法。-   wrr（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   wlc：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   rr：按照访问顺序依次将外部请求依序分发到后端服务器。

|
|VServerGroupId|String|绑定的服务器组ID。|
|MaterSlaveServerGroupId|String|绑定的主备服务器组ID。|
|PersistenceTimeout|String|是否开启了会话保持，值为0表示没有开启。|
|EstablishedTimeout|String|连接超时时间。|
|HealthCheckType|String|TCP协议监听的健康检查方式。|
|HealthCheck|String|是否开启健康检查。|
|AclStatus|String|是否开启访问控制功能。取值：on | off（默认值）

|
|AclType|String| 访问控制类型：

 -   white： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

-   black： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当AclStatus参数的值为on时，该参数必选。

 |
|AclId|String|监听绑定的访问策略组ID。当AclStatus参数的值为on时，该参数必选。

|
|HealthyThreshold|Integer|健康检查阈值。|
|UnhealthyThreshold|Integer|不健康检查阈值。|
|HealthCheckConnectTimeout|Integer|超时时间。|
|HealthCheckConnectTimeout|Integer|每次健康检查响应的最大超时间，单位为秒。|
|HealthCheckInterval|Integer|健康检查的时间间隔，单位为秒。|
|HealthCheckDomain|String|用于健康检查的域名。|
|HealthCheckURI|String|用于健康检查的URI。|
|HealthCheckHttpCode|String|健康检查正常的HTTP状态码。|
|SynProxy|String|是否开启SynProxy，SynProxy是负载均衡的攻击防护功能。建议一般情况下不要调整这个参数，由负载均衡控制。

取值：

-   enable：开启
-   disable：关闭

|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerTCPListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
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

-   JSON格式

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


