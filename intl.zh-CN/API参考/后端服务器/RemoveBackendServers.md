# RemoveBackendServers {#reference_amf_hjd_ndb .reference}

移除后端服务器。

**说明：** 如果要移除的后端服务器不在指定的负载均衡实例的服务器列表中，会直接忽略，不会报错。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：RemoveBackendServers

|
|RegionId|String|是|负载均衡实例的地域。|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|BackendServers|List|是|要移除的后端服务器ID。**说明：** 一次最多可以移除20个后端服务器。

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|string|请求ID。|
|LoadBalancerId|String|负载均衡实例ID。|
|BackendServers|List|后端服务器列表。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=RemoveBackendServers
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&BackendServers=["i-bp143t8c5uralrxxxx","i-bp12zdi79965uxxxx"]
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <RemoveBackendServersResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-231</ServerId>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-232</ServerId>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </RemoveBackendServersResponse>
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
            "Weight": 100
          },
          {
            "ServerId": "vm-234",
            "Weight": 100
          }
        ]
      }
    }
    ```


