# DescribeTags {#reference_hfl_3df_ndb .reference}

查询已创建的标签。

调用该接口时，请注意：

-   支持根据实例ID、标签键值、标签值等条件查询。
-   指定的查询条件为and关系，只有满足所有指定条件的便签才会被返回。
-   如果指定了标签的key而没有指定标签的值，则返回所有符合指定Key的标签。
-   不允许只指定TagKey而不指定TagValue。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeTags

|
|RegionId|String|是|负载均衡地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerID|String|否|负载均衡实例ID。|
|Tags|String|否|要查询的标签列表。|
|PageSize|Integer|否|分页查询时设置的每页行数。取值范围：\[1, 50\]默认值为10。

|
|PageNumber|Integer|否|列表页码，默认值1。|
|DistinctKey|String|否|是否为DistinctKey。|

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|TagKey|String|是|标签的键值。最多支持64个字，不能以aliyun开头，不允许为空。

|
|TagValue|String|否|标签的值。最多支持128个字符， 不能以aliyun开头。

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|TagSets|List|Tag列表。|
|PageSize|Integer|分页包含的条目。|
|PageNumber|Integer|当前页码。|
|TotalCount|Integer|查询到的标签个数。|

|名称|类型|描述|
|:-|:-|:-|
|TagKey|String|标签的键值。|
|TagValue|String|标签的值。|
|InstanceCount|Integer|该标签绑定的实例总数。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeTags
&RegionId=cn-hangzhou
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeTagsResponse>
      <RequestId>87696689-7951-4206-B30F-79D35A95C904</RequestId> 
      <TotalCount>3</TotalCount>
      <PageNumber>1</PageNumber>
      <PageSize>50</PageSize>
       <TagSets>
          <TagSet>
                <InstanceCount>1</InstanceCount>
                <TagKey>Protocol</TagKey>
                <TagValue>HTTPS</TagValue>
             </TagSet>
             <TagSet>
                <InstanceCount>1</InstanceCount>
                <TagKey>network</TagKey>
                <TagValue>classic</TagValue>
             </TagSet>
             <TagSet>
                <InstanceCount>1</InstanceCount>
                <TagKey>acs_cluster</TagKey>
                <TagValue>cb2f4d713ba634931bf5851f08c073256</TagValue>
             </TagSet>
       </TagSets>
    </DescribeTagsResponse>
    ```

-   JSON格式

    ```
    {
       "PageNumber":1,
       "TotalCount":3,
       "PageSize":50,
       "RequestId":"87696689-7951-4206-B30F-79D35A95C904",
       "TagSets":{
          "TagSet":[
             {
                "InstanceCount":1,
                "TagValue":"HTTPS",
                "TagKey":"Protocol"
             },
             {
                "InstanceCount":1,
                "TagValue":"classic",
                "TagKey":"network"
             },
             {
                "InstanceCount":1,
                "TagValue":"cb2f4d713ba634931bf5851f08c073256",
                "TagKey":"acs_cluster"
             }
          ]
       }
    }  
    ```


