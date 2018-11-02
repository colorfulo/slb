# DescribeRegions {#slb_api_DescribeRegions .reference}

查询可用地域。

## 调试 {#section_lmd_x55_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeRegions)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

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
|Regions|List|地域列表。|

|名称|类型|描述|
|:-|:-|:-|
|RegionId|String|地域ID。|
|RegionEndpoint|String|Region服务的Endpoint地址。|
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
    <?xml version="1.0" encoding="UTF-8" ?>
    	<RequestId>6C165435-22D9-475F-B722-123B49274B45</RequestId>
    	<Regions>
    		<Region>
    			<RegionId>ap-southeast-1</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>亚太东南 1 (新加坡)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>eu-central-1</RegionId>
    			<RegionEndpoint>slb.eu-central-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>欧洲中部 1 (法兰克福)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-southeast-5</RegionId>
    			<RegionEndpoint>slb.ap-southeast-5.aliyuncs.com</RegionEndpoint>
    			<LocalName>亚太东南 5 (雅加达)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-qingdao</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>华北 1</LocalName>
    		</Region>
    		<Region>
    			<RegionId>us-east-1</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>美国东部 1 (弗吉尼亚)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-south-1</RegionId>
    			<RegionEndpoint>slb.ap-south-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>亚太南部 1 (孟买)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-beijing</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>华北 2</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-shanghai</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>华东 2</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-shenzhen</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>华南 1</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-northeast-1</RegionId>
    			<RegionEndpoint>slb.ap-northeast-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>亚太东北 1 (东京)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-huhehaote</RegionId>
    			<RegionEndpoint>slb.cn-huhehaote.aliyuncs.com</RegionEndpoint>
    			<LocalName>华北 5</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-southeast-2</RegionId>
    			<RegionEndpoint>slb.ap-southeast-2.aliyuncs.com</RegionEndpoint>
    			<LocalName>亚太东南 2 (悉尼)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-hongkong</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>香港</LocalName>
    		</Region>
    		<Region>
    			<RegionId>us-west-1</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>美国西部 1 (硅谷)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>me-east-1</RegionId>
    			<RegionEndpoint>slb.me-east-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>中东东部 1 (迪拜)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-zhangjiakou</RegionId>
    			<RegionEndpoint>slb.cn-zhangjiakou.aliyuncs.com</RegionEndpoint>
    			<LocalName>华北 3</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-hangzhou</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>华东 1</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-southeast-3</RegionId>
    			<RegionEndpoint>slb.ap-southeast-3.aliyuncs.com</RegionEndpoint>
    			<LocalName>亚太东南3 (吉隆坡)</LocalName>
    		</Region>
    	</Regions>
    ```

-   JSON格式

    ```
    {
        "RequestId": "C2641B81-6C58-43E8-91E0-9CCF1AC3A3EA", 
        "Regions": {
            "Region": [
                {
                    "RegionId": "ap-southeast-1", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "亚太东南 1 (新加坡)"
                }, 
                {
                    "RegionId": "eu-central-1", 
                    "RegionEndpoint": "slb.eu-central-1.aliyuncs.com", 
                    "LocalName": "欧洲中部 1 (法兰克福)"
                }, 
                {
                    "RegionId": "ap-southeast-5", 
                    "RegionEndpoint": "slb.ap-southeast-5.aliyuncs.com", 
                    "LocalName": "亚太东南 5 (雅加达)"
                }, 
                {
                    "RegionId": "cn-qingdao", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "华北 1"
                }, 
                {
                    "RegionId": "us-east-1", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "美国东部 1 (弗吉尼亚)"
                }, 
                {
                    "RegionId": "ap-south-1", 
                    "RegionEndpoint": "slb.ap-south-1.aliyuncs.com", 
                    "LocalName": "亚太南部 1 (孟买)"
                }, 
                {
                    "RegionId": "cn-beijing", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "华北 2"
                }, 
                {
                    "RegionId": "cn-shanghai", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "华东 2"
                }, 
                {
                    "RegionId": "cn-shenzhen", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "华南 1"
                }, 
                {
                    "RegionId": "ap-northeast-1", 
                    "RegionEndpoint": "slb.ap-northeast-1.aliyuncs.com", 
                    "LocalName": "亚太东北 1 (东京)"
                }, 
                {
                    "RegionId": "cn-huhehaote", 
                    "RegionEndpoint": "slb.cn-huhehaote.aliyuncs.com", 
                    "LocalName": "华北 5"
                }, 
                {
                    "RegionId": "ap-southeast-2", 
                    "RegionEndpoint": "slb.ap-southeast-2.aliyuncs.com", 
                    "LocalName": "亚太东南 2 (悉尼)"
                }, 
                {
                    "RegionId": "cn-hongkong", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "香港"
                }, 
                {
                    "RegionId": "us-west-1", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "美国西部 1 (硅谷)"
                }, 
                {
                    "RegionId": "me-east-1", 
                    "RegionEndpoint": "slb.me-east-1.aliyuncs.com", 
                    "LocalName": "中东东部 1 (迪拜)"
                }, 
                {
                    "RegionId": "cn-zhangjiakou", 
                    "RegionEndpoint": "slb.cn-zhangjiakou.aliyuncs.com", 
                    "LocalName": "华北 3"
                }, 
                {
                    "RegionId": "cn-hangzhou", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "华东 1"
                }, 
                {
                    "RegionId": "ap-southeast-3", 
                    "RegionEndpoint": "slb.ap-southeast-3.aliyuncs.com", 
                    "LocalName": "亚太东南3 (吉隆坡)"
                }
            ]
        }
    ```


