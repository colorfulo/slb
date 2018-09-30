# SetDomainExtensionAttribute {#reference_mpx_bvf_j2b .reference}

Modify the certificate of a domain name extension.

## Request parameters {#section_rm1_bcg_j2b .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action|String|Yes| The action to perform. Valid value:

 SetDomainExtensionAttribute

 |
|RegionId|String|Yes|The ID of the region where the Server Load Balancer instance is located.|
|DomainExtensionId|Integer|Yes|The ID of the domain name extension to be modified.|
|ServerCertificateId|String|Yes|The ID of the new certificate.|

## Response parameters {#section_xq3_scg_j2b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetDomainExtensionAttribute
&RegionId=cn-hangzhou
&Domain=*.example2.com
&ServerCertificateId=1231579085529123_164b57543a9_464232488
&CommonRequestParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <SetDomainExtensionAttributeResponse>
    	<RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
    </SetDomainExtensionAttributeResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "149A2470-F010-4437-BF68-343D5099C19D"
    }
    ```


