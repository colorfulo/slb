# DescribeHealthStatus {#reference_as4_5md_ndb .reference}

查询后端服务器的健康状态。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeHealthStatus

|
|RegionId|String|是|负载均衡实例的地域ID。|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|ListenerPort|Integer|否|负载均衡实例前端使用的端口。取值：1-65535

**说明：** 不设置该参数表示获取所有端口的健康检查状态。

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|BackendServers|List|后端服务器列表。|

|名称|类型|描述|
|:-|:-|:-|
|ServerId|String|ECS实例ID。|
|ServerHealthStatus|String|后端服务器的健康状况：-   normal：后端服务器健康。
-   abnormal：后端服务器不健康。
-   unavailable：未完成健康检查。

|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeHealthStatus
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeHealthStatusResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-233</ServerId>
    			<ServerHealthStatus>normal</ServerHealthStatus>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-234</ServerId>
    			<ServerHealthStatus>abnormal</ServerHealthStatus>
    		</BackendServer>
    	</BackendServers>
    </DescribeHealthStatusResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "LoadBalancerId": "139a00604ad-cn-east-hangzhou-01",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "vm-233",
            "ServerHealthStatus": "normal"
          },
          {
            "ServerId": "vm-234",
            "ServerHealthStatus": "abnormal"
          }
        ]
      }
    }
    ```


