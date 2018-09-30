# DescribeAccessLogsDownloadAttribute {#reference_k2w_gjl_l2b .reference}

Query access log forwarding rules.

## Request parameters {#section_md3_jjl_l2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String | Yes|The action to perform. Valid value: DescribeAccessLogsDownloadAttribute.|
|RegionId|String | Yes|The region of the SLB instance.|
|LogType|String| No|The valid value is layer4 or layer7 and the default value is layer7.|
|PageNumber|int|No|The default value is 1.|
|PageSize |int|No|The default value is 20, the start value is 1 and the maximum value is 50.|

## Request example {#section_jpk_bll_l2b .section}

```

https://slb.aliyuncs.com/?Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&LogType=layer7
```

## Response example {#section_mvj_dll_l2b .section}

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    	<Count>1</Count>
    	<LogsDownloadAttributes>
    		<LogsDownloadAttribute>
    			<LoadBalancerId>lb-bp1sof7s257tuo1ofrzzc</LoadBalancerId>
    			<LogProject>test-log-project</LogProject>
    			<LogStore>test-log-store</LogStore>
    			<LogType>layer7</LogType>
    			<RegionId>cn-hangzhou</RegionId>
    			<RoleArn>acs:ram::1655928604919847:role/aliyunlogwriteonlyrole</RoleArn>
    		</LogsDownloadAttribute>
    	</LogsDownloadAttributes>
    	<PageNumber>1</PageNumber>
    	<PageSize>20</PageSize>
    	<RequestId>FC1F244F-A20E-43F3-9BA1-C21149157243</RequestId>
    	<TotalCount>1</TotalCount>
    ```

-   JSON format

    ```
    
    {
    "count": 1,
    "LogsDownloadAttributes": {
    "LogsDownloadAttribute": [
    {
    "LoadBalancerId": "lb-bp1sof7s257tuo1ofrzzc",
    "LogProject": "test-log-project",
    "logstores":["test-logstore"],
    "LogType": "layer7",
    "RegionId": "cn-hangzhou",
    "RoleArn": "acs:ram::1655928604919847:role/aliyunlogwriteonlyrole"
    }
    ]
    },
    "PageNumber": 1,
    "PageSize": 20,
    "RequestId": "FC1F244F-A20E-43F3-9BA1-C21149157243",
    "TotalCount": 1
    }
    ```


