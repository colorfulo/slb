# DescribeDomainExtensions {#reference_ds1_mfq_n2b .reference}

Query added domain name extensions.

## Request parameters {#section_rm1_bcg_j2b .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action|String|Yes| The action to perform. Valid value:

 DescribeDomainExtensions

 |
|RegionId|String|Yes|The ID of the region where the Server Load Balancer instance is located.|
|LoadBalancerId|String|Yes|The ID of Server Load Balancer instance.|
|ListenerPort|Integer|Yes| The front-end HTTPS listener port of the Server Load Balancer instance. Valid value:

 1-65535

 |
|DomainExtensionId|String|No|The ID of the domain name extension.|

## Response parameters {#section_xq3_scg_j2b .section}

|Name |Type|Required|
|:----|:---|:-------|
|RequestId|String|The ID of the request.|
|ListenerPort|Integer|The front-end port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.|
|LoadBalancerId|String|The ID of the instance.|
|DomainExtensionList|List|A list of domain name extensions.|

|Name |Type|Description|
|:----|:---|:----------|
|DomainExtensionId|String|The ID of the domain name extension.|
|Domain|Integer|The domain name.|
|ServerCertificateId|String|The ID of the certificate used by the domain name.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeDomainExtensions
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=443
&CommonRequestParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <SetDomainExtensionAttributeResponseResponse>
    	<RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
    	<DomainExtensionId>de-bp1k4chwdnhxd</DomainExtensionId>
    	<ListenerPort>443</ListenerPort>
    </SetDomainExtensionAttributeResponseResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "CCC710F8-285C-415F-9211-9BD6BF7BB997", 
        "DomainExtensions": {
            "DomainExtension": [
                {
                    "ServerCertificateId": "1231579085529123_164b57543a9_464232488_760347667", 
                    "Domain": "*.example2.com", 
                    "DomainExtensionId": "de-bp1k4chwdnhxd"
                }
            ]
        }
    }
    ```


