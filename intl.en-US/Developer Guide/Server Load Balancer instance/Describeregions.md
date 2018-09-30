# Describeregions {#slb_api_DescribeRegions .reference}

Query regions.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description |
|----|----|--------|------------|
|Action|String| Yes|The action to perform. Valid value: DescribeRegions

|
|AcceptLanguage|String| No|Supported languages. Valid values:-   Chinese: zh-CN
-   English: en-US
-   Japanese: ja

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String |The ID of the request.|
|RegionEndpoint|String |The endpoint address of the region.|
|Regions|List|A list of regions.|

|Name|Type|Description|
|:---|:---|:----------|
|RegionId|String |The ID of the region.|
|LocalName|String |The name of the region.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeRegions
&CommonParameters
```

**Response example**

-   XML format

    ```
    &lt;? xml version="1.0" encoding="UTF-8" ? >
    	<RequestId>6C165435-22D9-475F-B722-123B49274B45</RequestId>
    	<Regions>
    		<Region>
    			<RegionId>ap-southeast-1</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>Singapore</LocalName>
    		</Region>
    		<Region>
    			<RegionId>eu-central-1</RegionId>
    			<RegionEndpoint>slb.eu-central-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>Germany (Frankfurt)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-southeast-5</RegionId>
    			<RegionEndpoint>slb.ap-southeast-5.aliyuncs.com</RegionEndpoint>
    			<LocalName>Indonesia (jakarta)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-qingdao</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Qingdao)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>us-east-1</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>US (Virginia)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-south-1</RegionId>
    			<RegionEndpoint>slb.ap-south-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>India (Mumbai)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-beijing</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Beijing)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-shanghai</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Beijing)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-shenzhen</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Shenzhen)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-northeast-1</RegionId>
    			<RegionEndpoint>slb.ap-northeast-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>Japan (Tokyo)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-huhehaote</RegionId>
    			<RegionEndpoint>slb.cn-huhehaote.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Hohhot)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-southeast-2</RegionId>
    			<RegionEndpoint>slb.ap-southeast-2.aliyuncs.com</RegionEndpoint>
    			<LocalName>Australia (Sydney)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-hongkong</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Hong Kong)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>us-west-1</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>US (Silicon Valley)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>me-east-1</RegionId>
    			<RegionEndpoint>slb.me-east-1.aliyuncs.com</RegionEndpoint>
    			<LocalName>UAE (Dubai)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-zhangjiakou</RegionId>
    			<RegionEndpoint>slb.cn-zhangjiakou.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Zhangjiakou)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>cn-hangzhou</RegionId>
    			<RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
    			<LocalName>China (Hangzhou)</LocalName>
    		</Region>
    		<Region>
    			<RegionId>ap-southeast-3</RegionId>
    			<RegionEndpoint>slb.ap-southeast-3.aliyuncs.com</RegionEndpoint>
    			<LocalName>Malasia (Kuala Lumpur)</LocalName>
    		</Region>
    	</Regions>
    ```

-   JSON format

    ```
    {
        "RequestId": "C2641B81-6C58-43E8-91E0-9CCF1AC3A3EA", 
        "Regions": {
            "Region": [
                {
                    "RegionId": "ap-southeast-1", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "Singapore"
                }, 
                {
                    "RegionId": "eu-central-1", 
                    "RegionEndpoint": "slb.eu-central-1.aliyuncs.com", 
                    "LocalName": "Germany (Frankfurt)"
                }, 
                {
                    "Regionid": ap-southeast-5 ", 
                    "RegionEndpoint": "slb.ap-southeast-5.aliyuncs.com", 
                    "LocalName": "Indonesia (Jakarta)"
                }, 
                {
                    "RegionId": "cn-qingdao", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "China (Qingdao)"
                }, 
                {
                    "RegionId":"us-east-1" 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "US (Virginia)"
                }, 
                {
                    "RegionId": "ap-southeast-1", 
                    "RegionEndpoint": "slb.ap-south-1.aliyuncs.com", 
                    "LocalName": "India (Mumbai)"
                }, 
                {
                    "RegionId": "cn-beijing" 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "China (Beijing)"
                }, 
                {
                    "RegionId": "cn-shanghai", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "China (Shanghai)"
                }, 
                {
                    "RegionId": "cn-shenzhen", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "China (Shenzhen)"
                }, 
                {
                    "RegionId": "ap-northeast-1", 
                    "RegionEndpoint": "slb.ap-northeast-1.aliyuncs.com", 
                    "LocalName": "Japan (Tokyo)"
                }, 
                {
                    "RegionId": "cn-huhehaote", 
                    "RegionEndpoint": "slb.cn-huhehaote.aliyuncs.com", 
                    "LocalName": "China (Hohhot)"
                }, 
                {
                    "RegionId": "ap-southeast-2", 
                    "RegionEndpoint": "slb.ap-southeast-2.aliyuncs.com", 
                    "LocalName": "Australia (Sydney)"
                }, 
                {
                    "RegionId": "cn-hongkong", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "China (Hong Kong)"
                }, 
                {
                    "RegionId": "us-west-1", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "US (Silicon Valley)"
                }, 
                {
                    "RegionId": "me-east-1", 
                    "Regionendpoint": slb.me-east-1.aliyuncs.com ", 
                    "LocalName": "UAE (Dubai)"
                }, 
                {
                    "RegionId": "cn-zhangjiakou", 
                    "RegionEndpoint": "slb.cn-zhangjiakou.aliyuncs.com", 
                    "LocalName": "China (Zhangjiakou)"
                }, 
                {
                    "RegionId": "cn-hangzhou", 
                    "RegionEndpoint": "slb.aliyuncs.com", 
                    "LocalName": "China (Hangzhou)"
                }, 
                {
                    "RegionId": "ap-southeast-3", 
                    "RegionEndpoint": "slb.ap-southeast-3.aliyuncs.com", 
                    "LocalName": "Malaysia (Kuala Lumpur)"
                }
            ]
        }
    ```


