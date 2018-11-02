# DeleteDomainExtension {#reference_i1l_3nq_n2b .reference}

删除扩展域名。

## 调试 {#section_pb3_31b_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DeleteDomainExtension)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_rm1_bcg_j2b .section}

|名称|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作，取值：

 DeleteDomainExtension

 |
|RegionId|String|是|负载均衡示例的地域ID。|
|DomainExtensionId|Integer|是|要删除的扩展域名ID。|

## 返回参数 {#section_xq3_scg_j2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteDomainExtension
&RegionId=cn-hangzhou
&DomainExtensionId=de-bp1k4chwdnhxd
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    <DeleteDomainExtensionResponse>
    	<RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
    </DeleteDomainExtensionResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId": "149A2470-F010-4437-BF68-343D5099C19D"
    }
    ```


