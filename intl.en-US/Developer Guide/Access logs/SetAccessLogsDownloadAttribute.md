# SetAccessLogsDownloadAttribute {#reference_ohp_g32_l2b .reference}

Configure an access log forwarding rule.

## Request parameters {#section_zhn_51f_l2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String | Yes|The action to perform. Valid value: SetAccessLogsDownloadAttribute|
|RegionId|String | Yes|The region of the SLB instance or LogStore.|
|LogsDownloadAttributes|String | Yes|A list of access log forwarding rules. For more information, see [Table 1](#table_mj3_kbf_l2b).|

|Name|Type|Required|Description|
|----|----|--------|-----------|
|LogProject|String |Yes|The LogProject of your SLS.|
|LogStore|String | Yes|The LogStore of your SLS.|
|LoadBalancerId|String | Yes|The ID of the SLB instance that requires forwarding access logs.|
|LogType|String| No|The valid value is layer4 or layer7 and the default value is layer7.|
|RoleName|String| No|The access RoleName of your SLS. The default value is aliyunlogwriteonlyrole.|

## Response parameters {#section_yg3_hbf_l2b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|

## Request example {#section_wsl_ncf_l2b .section}

```

https://slb.aliyuncs.com?Action= SetAccessLogsDownloadAttribute
&RegionId=cn-hangzhou
& LogsDownloadAttributes =[

]
&CommonParameters
```

## Response example {#section_x4s_qcf_l2b .section}

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    ```

-   JSON format

    ```
    "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
    ```


