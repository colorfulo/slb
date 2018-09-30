# DeleteAccessLogsDownloadAttribute {#reference_gkx_ydf_l2b .reference}

Delete an access log forwarding rule.

## Request parameters {#section_nnh_12f_l2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String |Yes|The action to perform. Valid value: DeleteAccessLogsDownloadAttribute|
|RegionId|String | Yes|The region of the SLB instance.|
|LogsDownloadAttributes|String | Yes|A list of access log forwarding rules. For more information, see|

|Name|Type|Required|Description|
|----|----|--------|-----------|
|LoadBalancerId|String | Yes|The ID of the SLB instance that requires forwarding access logs.|

## Response parameters {#section_vbn_43k_l2b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|

## Request example {#section_vbd_bjk_l2b .section}

```

https://slb.aliyuncs.com?Action=DeleteAccessLogsDownloadAttribute
&RegionId=cn-hangzhou
& LogsDownloadAttributes =[
{ "LoadBalancerId":"lb-uf68ps3rekbljmdb0cxp7" }]
```

## Response example {#section_ilj_2jk_l2b .section}

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    ```

-   JSON format

    ```
    
    {
    "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
    }
    ```


