# SetBackendServers {#reference_elf_bmd_ndb .reference}

设置后端服务器权重。

## 调试 {#section_hyf_zyz_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=SetBackendServers)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：SetBackendServers

|
|RegionId|String|是|负载均衡实例的地域ID。|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|BackendServers|StringJSON格式的List

|是|要添加的后端服务器列表。**说明：** 后端服务器（ECS实例）必须是运行中才可以加入负载均衡实例，一次最多可调用20个后端服务器。

|

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|ServerId|string|是|ECS实例ID。|
|Weight|Integer|否|后端服务器的权重，取值：\[0,100\] 默认值为100。如果值为0，则不会将请求转发给该后端服务器。

|
|Type|String|是|后端服务器类型，取值：-   ecs：ECS实例（默认）
-   eni：弹性网卡实例

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|LoadBalancerId|String|负载均衡实例ID。|
|BackendServers|StringJSON格式的List

|后端服务器列表。|

|名称|类型|描述|
|:-|:-|:-|
|ServerId|String|ECS实例ID。|
|Weight|Integer|后端服务器的权重。|
|Type|String|后端服务器类型，取值：-   ecs：ECS实例（默认）
-   eni：弹性网卡实例

|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=SetBackendServers
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&BackendServers=[
    {"ServerId":" vm-233","Weight":"100"},
    {"ServerId":" vm-234","Weight":"100"}]
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <SetBackendServersResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>eni-231</ServerId>
    			<Weight>100</Weight>
                            <Type>eni</Type>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>eni-233</ServerId>
    			<Weight>100</Weight>
                            <Type>eni</Type>
    		</BackendServer>
    	</BackendServers>
    </SetBackendServersResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "LoadBalancerId": "139a00604ad-cn-east-hangzhou-01",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "eni-231",
            "Weight": 100,
            "Type":"eni",
          },
          {
            "ServerId": "eni-233",
            "Weight": 100,
            "Type":"eni"
          }
        ]
      }
    }
    ```


