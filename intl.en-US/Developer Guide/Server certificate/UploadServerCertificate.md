# UploadServerCertificate {#reference_qbv_nw2_ndb .reference}

Upload a server certificate.

Only one server certificate and the corresponding private key can be uploaded at a time. This API is transactional, that is, the server certificate and the private key are uploaded either successfully or not. After the certificate and private key are successfully uploaded, the fingerprints of all server certificates under your account are returned.

## Request parameters {#section_bqw_c1g_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform. Valid value:UploadServerCertificate

|
|RegionId|String | Yes|The region of the server certificate.You can obtain the region ID by calling the DescribeRegions API.

|
|ServerCertificate|String| No|The public key certificate to upload.|
|ServerCertificateName|String| No|The name of the server certificate to upload.|
|PrivateKey|String| No|The private key to upload.|
|AliCloudCertificateId|String| No|The ID of the Alibaba Cloud certificate.|
|AliCloudCertificateName|String| No|The name of the Alibaba Cloud certificate.|
|ResourceGroupId|String| No|The ID of the enterprise resource group.|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|ServerCertificateId|String|The ID of the server certificate.|
|ServerCertificateName|String|The name of the server certificate.|
|Fingerprint|String|The fingerprint of the server certificate.|
|ExpireTime|String|The time of expiration.|
|ExpireTimeStamp|Long|The timestamp of expiration.|
|CommonName|String|The domain name that corresponds to the common name field of the certificate.|
|SubjectAlternativeNames|List|A list of subject alternative names. For more information, see [SubjectAlternativeNames](#section_lxl_5lf_j2b).|

## SubjectAlternativeNames {#section_lxl_5lf_j2b .section}

|Name |Type|Description|
|-----|----|-----------|
|SubjectAlternativeName|String|The alternative domain name.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=UploadServerCertificate
&Action=UploadServerCertificate
&RegionId=cn-hangzhou-01
&ServerCertificate=test
&ServerCertificateName=mycert01
&PrivateKey=wmsad! q23
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <UploadServerCertificateResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<ServerCertificateId>idkp-123-cn-test-01</ServerCertificateId>
    	<ServerCertificateName>mycert01</ServerCertificateName>
    	<Fingerprint>01:DF:AB:CD</Fingerprint>
    </UploadServerCertificateResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710", 
        "ServerCertificateId": "idkp-123-cn-test-01", 
        "ServerCertificateName": "mycert01", 
        "Fingerprint": "01:DF:AB:CD", 
        "ExpireTime": "2017-06-23T11:33:08Z", 
        "ExpireTimeStamp": 1498217588000, 
        "CommonName": "www.rzemp.com", 
        "SubjectAlternativeNames": {
            "SubjectAlternativeName": [
                "www.rzemp.com", 
                "rzemp.com"
            ]
        }
    }
    ```


