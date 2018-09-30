# SetCACertificateName {#reference_kwt_lcf_ndb .reference}

Configure a name for a CA certificate.

## Request parameters {#section_bqw_c1g_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:SetCACertificateName

|
|CACertificateId|String|Yes|The ID of the CA certificate.|
|RegionId|String|Yes|The ID of the region where the CA certificate is located.You can obtain the region ID by calling the DescribeRegions API.

|
|CACertificateName|String|Yes|The name of the CA certificate.The name must start with English letters, and can contain 1-80 characters including English letters, numbers, underscores \(\_\), periods \(.\), and hyphens \(-\).

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetCACertificateName
&CACertificateId=139a00604ad-cn-east-hangzhou-01
&CACertificateName=mycacert02
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetCACertificateNameResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
    </SetCACertificateNameResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
    }
    ```


