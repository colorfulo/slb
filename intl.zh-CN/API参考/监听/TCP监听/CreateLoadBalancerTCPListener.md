# CreateLoadBalancerTCPListener {#slb_api_CreateLoadBalancerTCPListener .reference}

创建TCP监听。

**说明：** 新建的监听的状态为stopped。创建完成后，需调用StartLoadBalancerListener接口启动监听进行流量转发。

## 请求参数 {#section_bqw_c1g_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：CreateLoadBalancerTCPListener

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例ID。|
|ListenerPort|Integer|是|负载均衡实例前端使用的端口，取值：1-65535

|
|BackendServerPort|Integer|是|负载均衡实例后端使用的端口。取值：1-65535

**说明：** 如果不使用服务器组（不指定VServerGroupId参数），则该参数必选。

|
|VServerGroupId|String|否|服务器组ID。|
|MasterSlaveServerGroupId|String|否|主备服务器组ID。**说明：** VServerGroupId和MasterSlaveServerGroupId参数不能同时指定。

|
|Bandwidth|Integer|是|监听的带宽峰值，取值：-   -1：不限制带宽峰值。
-   \[1-5000\]：监听的带宽峰值，所有监听的带宽峰值之和不能超过实例的带宽峰值。

|
|Scheduler|String|否|调度算法。取值：-   wrr（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   wlc：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   rr：按照访问顺序依次将外部请求依序分发到后端服务器。
-   sch：基于源IP地址的一致性hash，相同的源地址会调度到相同的后端服务器。
-   tch：基于四元组的一致性hash（源IP+目的IP+源端口+目的端口），相同的流会调度到相同的后端服务器。

**说明：** 仅有性能保障型实例支持sch和tch一致性hash算法。

|
|PersistenceTimeout|Integer|否|会话保持的超时时间。取值：0-3600（秒）

默认值为0，关闭会话保持。

|
|EstablishedTimeout|Integer|否| 连接超时时间。

 取值：10-900（秒）

 |
|Description|String|否| 设置监听的描述信息。

 |
|AclStatus|String|否| 是否开启访问控制功能。

 取值：on | off（默认值）

 |
|AclType|String|否| 访问控制类型：

 -   white： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

-   black： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当AclStatus参数的值为on时，该参数必选。

 |
|AclId|String|否| 监听绑定的访问策略组ID。

 当AclStatus参数的值为on时，该参数必选。

 |
|HealthCheckType|String|否| 健康检查类型。

 取值：tcp（默认值） | http

 |
|HealthCheckDomain|String|否|用于健康检查的域名，取值：-   $\_ip： 后端服务器的私网IP。当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。
-   domain：域名长度为1-80字符，只能包含字母、数字、点号（.）和连字符（-）。

**说明：** 当健康检查类型为TCP模式时，无需配置该参数。

|
|HealthCheckURI|String|否|用于健康检查的URI。**说明：** 当健康检查类型为TCP模式时，无需配置该参数。

|
|HealthCheckConnectPort|Integer|否| 健康检查使用的端口。取值：

 -   -520：默认使用监听配置的后端端口。
-   1-65535：健康检查的后端服务器的端口。

 |
|HealthyThreshold|Integer|否|健康检查连续成功多少次后，将后端服务器的健康检查状态由fail判定为success。取值：2-10

|
|UnhealthyThreshold|Integer|否|健康检查连续失败多少次后，将后端服务器的健康检查状态由success判定为fail。取值：2-10

|
|HealthCheckConnectTimeout|Integer|否| 接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：1-300（秒）

 **说明：** 如果HealthCheckConnectTimeout的值小于HealthCheckInterval的值，则HealthCheckConnectTimeout无效，超时时间为HealthCheckInterval的值。

 |
|HealthCheckInterval|Integer|否| 健康检查的时间间隔。

 取值：1-50（秒）

 |
|HealthCheckHttpCode|String|否| 健康检查正常的HTTP状态码，多个状态码用逗号分隔。

 取值：http\_2xx（默认值） | http\_3xx | http\_4xx | http\_5xx

 |

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=CreateLoadBalancerTCPListener
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=443
&BackendServerPort=443
&Bandwidth=-1
&VServerGroupId=rsp-cige6j5e7p
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <CreateLoadBalancerTCPListenerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </CreateLoadBalancerTCPListenerResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


