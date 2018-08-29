# DescribeRegions {#slb_api_DescribeRegions .reference}

查询可用地域。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作。取值：DescribeRegions

|
|AcceptLanguage|String|否|支持的语言。包括以下取值：-   中文：zh-CN
-   英文：en-US
-   日文：ja

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|RegionEndpoint|String|Region服务的Endpoint地址。|
|Regions|List|地域列表。|

|名称|类型|描述|
|:-|:-|:-|
|RegionId|String|地域ID。|
|LocalName|String|地域名称。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeRegions
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeRegionsResponse>
    	<RequestId>1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6</RequestId>
    	<Regions>
    		<Region>
    			<RegionId>cn-east-hangzhou-01</RegionId>
    			<LocalName>杭州</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-beijing</RegionId>
    			<LocalName>北京</LocalName>
    		</Region>
    	</Regions>
    </DescribeRegionsResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6",
      "Regions": {
        "Region": [
          {
            "RegionId": "cn-qingdao,
            "LocalName": "青岛"
          },
          {
            "RegionId": "cn-beijing",
            "LocalName": "北京"
          }
        ]
      }
    }
    ```


