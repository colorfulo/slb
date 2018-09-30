# DeleteServerCertificate {#reference_i2g_sx2_ndb .reference}

Delete a server certificate.

**Note:** You cannot delete a CA certificate that is in use.

## Request parameters {#section_bqw_c1g_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:DeleteServerCertificate

|
|RegionId|String|No|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|ServerCertificateId|String|Yes|The ID of the server certificate.|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteServerCertificate
&RegionId=cn-hangzhou
&ServerCertificateId=idkp-123-cn-test-01
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DeleteServerCertificateResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </DeleteServerCertificateResponse>
    ```

-   JSON format

    ```
    {
         "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
     }
    ```


