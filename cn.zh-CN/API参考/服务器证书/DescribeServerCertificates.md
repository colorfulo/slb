# DescribeServerCertificates {#reference_llz_dy2_ndb .reference}

查询已上传的服务器证书。

**说明：** 为了保证证书安全，只返回证书的指纹和名称，不返回证书和私钥的内容。

## 请求参数 {#section_bqw_c1g_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeServerCertificates

|
|RegionId|String|否|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|ServerCertificateId|String|否|服务器证书ID。|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|ServerCertificates|List|服务器证书列表。|

|名称|类型|描述|
|:-|:-|:-|
|ServerCertificateId|String|服务器证书ID。|
|ServerCertificateName|String|服务器证书名称。|
|Fingerprint|String|服务器证书的指纹。|
|CreateTime|String|服务器证书上传的时间。|
|CreateTimeStamp|Long|服务器证书上传的时间戳。|
|IsAliCloudCertificate|Integer|是否是阿里云证书。0代表不是阿里云证书。|
|AliCloudCertificateName|String|阿里云证书名称。|
|AliCloudCertificateId|String|阿里云证书ID。|
|ExpireTime|String|过期时间。|
|ExpireTimeStamp|Long|过期时间戳。|
|CommonName|String|域名，对应证书的CommonName字段。|
|SubjectAlternativeNames|List|数组格式，返回证书的备用域名列表，对应证书的Subject Alternative Name字段，详情请参见[SubjectAlternativeNames](#section_ojl_gpf_j2b)。|
|ResourceGroupId|String|实例的企业资源组ID|
|RegionId|String|负载均衡实例的地域。|

## SubjectAlternativeNames {#section_ojl_gpf_j2b .section}

|名称|类型|描述|
|--|--|--|
|SubjectAlternativeName|String|备用域名。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeServerCertificates
&Action=DescribeServerCertificate 
&RegionId=cn-east-hangzhou-01
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeServerCertificatesResponse>
       <RequestId>9F8232CD-29B5-4A21-86C5-4154D5F6A578</RequestId>
       <ServerCertificates>
          <ServerCertificate>
                <AliCloudCertificateId />
                <AliCloudCertificateName />
                <CreateTime>2018-03-14T09:15:21Z</CreateTime>
                <CreateTimeStamp>1521018921000</CreateTimeStamp>
                <Fingerprint>cd:90:1b:7b:49:4d:1d:90:f6:01:de:9a:81:7d:31:a7:38:1d:84:8d</Fingerprint>
                <IsAliCloudCertificate>0</IsAliCloudCertificate>
                <RegionId>cn-hangzhou</RegionId>
                <RegionIdAlias>cn-hangzhou</RegionIdAlias>
                <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
                <ServerCertificateId>1231579085529123_16223cae1ec_2024493633_797495279</ServerCertificateId>
                <ServerCertificateName>www.aliyuntest.club</ServerCertificateName>
          </ServerCertificate>			
          <ServerCertificate>	
                <AliCloudCertificateId>0</AliCloudCertificateId>
                <AliCloudCertificateName />
                <CreateTime>2016-12-13T09:57:49Z</CreateTime>
                <CreateTimeStamp>1481623069000</CreateTimeStamp>
                <Fingerprint>cd:90:1b:7b:49:4d:1d:90:f6:01:de:9a:81:7d:31:a7:38:1d:84:8d</Fingerprint>
                <IsAliCloudCertificate>0</IsAliCloudCertificate>
                <RegionId>cn-hangzhou</RegionId>
                <RegionIdAlias>cn-hangzhou</RegionIdAlias>
                <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
                <ServerCertificateId>1231579085529123_158f79de306</ServerCertificateId>
                <ServerCertificateName>test_certificate</ServerCertificateName>
          </ServerCertificate>
       </ServerCertificates>
    </DescribeServerCertificatesResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710", 
        "ServerCertificates": {
            "ServerCertificate": [
                {
                    "ServerCertificateId": "139a00604ad-cn-east-hangzhou-01", 
                    "ServerCertificateName": "abe", 
                    "Fingerprint ": "A:B:E", 
                    "ExpireTime": "2017-06-23T11:33:08Z", 
                    "ExpireTimeStamp": 1498217588000, 
                    "CommonName": "www.rzemp.com", 
                    "SubjectAlternativeNames": {
                        "SubjectAlternativeName": [
                            "www.rzemp.com", 
                            "rzemp.com"
                        ]
                    }
                }, 
                {
                    "ServerCertificateId": "282b00102ac-cn-east-hangzhou-02", 
                    "ServerCertificateName": "abf", 
                    "Fingerprint ": "A:B:F", 
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
            ]
        }
    }
    
    ```


