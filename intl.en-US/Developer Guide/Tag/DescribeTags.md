# DescribeTags {#reference_hfl_3df_ndb .reference}

Query the created tags.

Note the following when calling this API:

-   You can query the tags by instance ID, tag key, and tag value.
-   The specified conditions are of “and” relation, and only tag sets meeting all specified conditions are returned.
-   If you only specify a tag key without a value, all tags associated with the key are queried.
-   You cannot specify only a TagKey without a TagValue.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform. Valid value:DescribeTags

|
|RegionId|String | Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerID|String| No|The ID of the SLB instance.|
|Tags|String| No|The list of tags to query.|
|PageSize |Integer|No |The number of rows per page. Valid value: \[1, 50\]The default value is 10.

|
|PageNumber|Integer|No |The number of pages to return. The default value is 1.|
|DistinctKey|String| No|Whether it is DistinctKey.|

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|TagKey|String | Yes|The key of the tag.It can contain up to 64 characters, and cannot start with aliyun or be empty.

|
|TagValue|String| No|The value of the tag.It can contain up to 128 characters, and cannot start with aliyun.

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|TagSets|List|The list of tags.|
|PageSize |Integer  |The number of rows per page.|
|PageNumber|Integer|The current page number.|
|TotalCount |Integer|The total number of queried tags.|

|Name |Type|Description|
|:----|:---|:----------|
|TagKey|String|The key of the tag.|
|TagValue|String|The value of the tag.|
|InstanceCount|Integer|The total number of instances bound to the tag.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeTags
&RegionId=cn-hangzhou
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
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

-   JSON format

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


