# DeleteRules {#reference_xgj_xf2_ndb .reference}

删除转发规则。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DeleteRules

|
|RegionId|String|是|负载均衡实例的地域ID。您可以通过调用 DescribeRegions接口获取地域ID。

|
|RuleIds|List|是|要删除的转发规则列表。|

## 返回参数 {#section_ssd_pds_cz .section}

|参数|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteRules
&RegionId=cn-hangzhou 
&RuleIds=[rule-tybqi6qkp8,rule-3ejhktkaeu]
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <DeleteRulesResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    </DeleteRulesResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
    }
    ```


