# UploadCACertificate {#reference_lpx_l1f_ndb .reference}

Upload a CA certificate.

You can only upload one certificate each time. After a certificate is successfully uploaded, the certificate ID, name, and fingerprint are returned.

## Request parameters {#section_bqw_c1g_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform. Valid value:UploadCACertificate

|
|RegionId|String | Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|CACertificate|String | Yes|The content of the public key to upload.|
|CACertificateName|String| No|The name of the CA certificate.|
|ResourceGroupId|String| No|The ID of the enterprise resource group.|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|CACertificateId|String|The ID of the CA certificate.|
|CACertificateName|String|The name of the CA certificate.|
|Fingerprint|String|The fingerprint of the CA certificate.|
|CreateTime |String|The time when the CA certificate was uploaded.|
|Fingerprint|Long|The timestamp at which the CA certificate was uploaded.|
|ExpireTime|String|The time of expiration.|
|ExpireTimeStamp|Long|The timestamp of expiration.|
|CommonName|String|Corresponds to the common name field of the certificate.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=UploadCACertificate
&Action=UploadCACertificate
&RegionId=cn-east-hangzhou-01
&CACertificate=test
&CACertificateName=mycacert01
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <UploadCACertificateResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<CACertificateId>idkp-234-cn-test-02</CACertificateId>
    	<CACertificateName>mycacert01</CACertificateName>
    	<Fingerprint>02:DF:AB:ED</Fingerprint>
    </UploadCACertificateResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710", 
        "CACertificateId": "idkp-123-cn-test-01", 
        "CACertificateName": "mycert01", 
        "Fingerprint": "01:DF:AB:CD", 
        "ExpireTime": "2017-06-23T11:33:08Z", 
        "ExpireTimeStamp": 1498217588000, 
        "CommonName": "symantec basic dv ssl ca - g1"
    }
    ```


