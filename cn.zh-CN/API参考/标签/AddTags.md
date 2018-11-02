# AddTags {#reference_gv5_vcf_ndb .reference}

为指定的负载均衡实例添加标签。

调用该接口时，请注意：

-   每个负载均衡实例最多可绑定10个Tag。
-   单次绑定的标签数最多为5对。
-   一个负载均衡实例下的所有Tag和Key不能重复。
-   当添加的标签与原有标签Key相同，但Value不同时，覆盖原有的标签。

## 调试 {#section_oqj_fz1_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=AddTags)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：AddTags

|
|RegionId|String|是|负载均衡地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerID|String|是|负载均衡实例ID。|
|Tags|String|是|要添加的Tag列表。最多可包含5个标签。

|

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|TagKey|String|是|标签的键值。最多支持64个字，不能以aliyun开头，不允许为空。

|
|TagValue|String|否|标签的值。最多支持128个字符， 不能以aliyun开头。

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=AddTags
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&Tags=[
    {"TagKey":"Key1","TagValue":"Value1"}
    {"TagKey":"Key2","TagValue":"Value2"}]
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <AddTagsResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    </AddTagsResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    }
    ```


