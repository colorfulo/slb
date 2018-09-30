# DescribeZones {#slb_api_DescribeZones .reference}

Query available active/standby zones in the specified region.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform.  Valid value:DescribeZones

|
|RegionId|String|Yes|The ID of the region to query.|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|Zones|List|The list of available zones.|

|Name|Type|Description|
|:---|:---|:----------|
|ZoneId|String|The ID of the active zone.|
|LocalName|String|The name of the active zone.|
|SlaveZones|List|The list of standby zones.|

|Name|Type|Description|
|:---|:---|:----------|
|ZoneId|String|The ID of the standby zone.|
|LocalName|String|The name of the standby zone.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeZones
&RegionId=cn-beijing
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <DescribeZonesResponse>
        <RequestId>A48D35FF-440A-4BC0-A4A2-A9BF69B7E43A</RequestId>
        <Zones>
    	    <Zone>
    		<SlaveZones></SlaveZones>
    		<ZoneId>cn-beijing-b</ZoneId>
    		<LocalName>Beijing ZoneB</LocalName>
    	    </Zone>
        </Zones>
    </DescribeZonesResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "1FF3C0EC-588C-4872-8F86-8D88A652D1E4",
      "Zones": {
        "Zone": [
          {
            "ZoneId": "cn-beijing-b",
            "LocalName": "Beijing ZoneB",
            "SlaveZones": {
              "SlaveZone": []
            }
          }
        ]
      }
    }
    ```


