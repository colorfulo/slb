# DescribeZones {#slb_api_DescribeZones .reference}

查询指定地域的可用区信息。

## 调试 {#section_zdr_bv5_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeZones)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：DescribeZones

|
|RegionId|String|是|所属地域。|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Zones|List|可用区列表。|

|名称|类型|描述|
|:-|:-|:-|
|ZoneId|String|可用区ID。|
|LocalName|String|可用区名称。|
|SlaveZones|List|主可用区对应的备可用区列表。|

|名称|类型|描述|
|:-|:-|:-|
|ZoneId|String|备可用区ID。|
|LocalName|String|备可用区名称。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeZones
&RegionId=cn-beijing
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    <DescribeZonesResponse>
        <RequestId>A48D35FF-440A-4BC0-A4A2-A9BF69B7E43A</RequestId>
        <Zones>
    	    <Zone>
    		<SlaveZones></SlaveZones>
    		<ZoneId>cn-beijing-b</ZoneId>
    		<LocalName>北京可用区B</LocalName>
    	    </Zone>
        </Zones>
    </DescribeZonesResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "1FF3C0EC-588C-4872-8F86-8D88A652D1E4",
      "Zones": {
        "Zone": [
          {
            "ZoneId": "cn-beijing-b",
            "LocalName": "北京可用区B",
            "SlaveZones": {
              "SlaveZone": []
            }
          }
        ]
      }
    }
    ```


