# SetServerCertificateName {#reference_o2z_yz2_ndb .reference}

Configure a name for a server certificate.

## Request parameters {#section_bqw_c1g_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:SetServerCertificateName

|
|ServerCertificateId|String|Yes|The ID of the server certificate.|
|RegionId|String|Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|ServerCertificateName|String|Yes|The name of the server certificate.The name must start with English letters, and can contain 1-80 characters including English letters, numbers, underscores \(\_\), periods \(.\), and hyphens \(-\).

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetServerCertificateName
&RegionId=cn-hangzhou
&ServerCertificateId=139a00604ad-cn-east-hangzhou-01
&ServerCertificateName=abc
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetServerCertificateNameResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
    </SetServerCertificateNameResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
    }
    ```


