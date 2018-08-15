# DescribeVServerGroupAttribute {#reference_jnq_yvd_ndb .reference}

查询服务器组的详细信息。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeVServerGroupAttribute

|
|RegionId|String|是|负载均衡实例的地域ID。您可以通过调用 DescribeRegions接口获取地域ID。

|
|VServerGroupId|String|是|服务器组ID。|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|VServerGroupId|String|服务器组ID。|
|VServerGroupName|String|服务器组名称。|
|BackendServers|StringJSON格式的List

|后端服务器列表。|

|名称|类型|描述|
|:-|:-|:-|
|ServerId|String|ECS实例ID。|
|Port|Integer|后端服务器使用的端口。|
|Weight|Integer|后端服务器的权重。|
|Type|String|后端服务器类型，取值：-   ecs：ECS实例（默认）
-   eni：弹性网卡实例

|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <DescribeVServerGroupAttributeResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
    	<VServerGroupName>Group1</VServerGroupName>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-232</ServerId>
    			<Port>80</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-233</ServerId>
    			<Port>90</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </DescribeVServerGroupAttributeResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
      "VServerGroupId": "rsp-cige6j5e7p",
      "VServerGroupName": "Group1",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "vm-233",
            "Port": "80",
            "Weight": "100"
          },
          {
            "ServerId": "vm-232",
            "Port": "90",
            "Weight": "100"
          }
        ]
      }
    }
    ```


