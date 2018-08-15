# ModifyVServerGroupBackendServers {#reference_kqp_zsd_ndb .reference}

替换服务器组中的后端服务器。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ModifyVServerGroupBackendServers

|
|RegionId|String|是|负载均衡地域ID。您可以通过调用 DescribeRegions接口获取地域ID。

|
|VServerGroupId|String|是|服务器组ID。|
|OldBackendServers|List|是|要被替换的后端服务器列表。|
|NewBackendServers|List|是|新的后端服务器列表。一个服务器组最多可调用20个后端服务器。

**说明：** 确保OldBackendServers和NewBackendServers服务器组列表中的后端服务器个数相同。

|

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|ServerId|String|是|ECS实例ID。|
|Port|Integer|是| 后端服务器使用的端口。

 取值范围：1-65535

 |
|Weight|Integer|是| 后端服务器的权重，取值：\[0,100\]

 默认值为100。如果值为0，则不会将请求转发给该后端服务器。

 |

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|VServerGroupId|String|服务器组ID。|
|BackendServers|List|后端服务器列表。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&VServerGroupName=Group1
&OldBackendServers=[{"ServerId":"vm-233","Port":"80","Weight":"100"},{"ServerId":"vm-232","Port":"90","Weight":"100"},]
&NewBackendServers=[{"ServerId":"vm-400","Port":"80","Weight":"100"},{"ServerId":"vm-401","Port":"90","Weight":"100"},]
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <ModifyVServerGroupBackendServersResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
    	<BackendServers>
    		<BackendServer>
    			<ServerId>vm-400</ServerId>
    			<Port>80</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    		<BackendServer>
    			<ServerId>vm-401</ServerId>
    			<Port>90</Port>
    			<Weight>100</Weight>
    		</BackendServer>
    	</BackendServers>
    </ModifyVServerGroupBackendServersResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
      "VServerGroupId":"rsp-cige6j5e7p",
      "BackendServers":{
      "BackendServer":[
        {"ServerId":"vm-400","Port":"80","Weight":"100"},
        {"ServerId":"vm-401","Port":"90","Weight":"100"},
        ]
      }
    }
    ```


