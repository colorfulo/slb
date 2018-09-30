# CreateDomainExtension {#reference_mpx_bvf_j2b .reference}

Create a domain name extension.

## Request parameters {#section_rm1_bcg_j2b .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action|String|Yes| The action to perform. Valid value:

 CreateDomainExtension

 |
|RegionId|String|Yes|The ID of the region where the Server Load Balancer instance is located.|
|LoadBalancerId|String|Yes|The ID of Server Load Balancer instance.|
|ListenerPort|Integer|Yes| The front-end HTTPS listener port of the Server Load Balancer instance. Valid value:

 1-65535

 |
|Domain|String|Yes|The domain name.|
|ServerCertificateId|String|Yes|The ID of the certificate corresponding to the domain name.|

## Response parameters {#section_xq3_scg_j2b .section}

|Name |Type|Description|
|-----|----|-----------|
|RequestId|String|The ID of the request.|
|ListenerPort|Integer|The front-end port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers.|
|DomainExtensionId|String|The ID of the created domain name extension.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=CreateDomainExtension
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=443
&Domain=*.example2.com
&ServerCertificateId=1231579085529123_164b57543a9_464232488_760347667
&CommonRequestParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <CreateDomainExtensionResponse>
    	<RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
    	<DomainExtensionId>de-bp1k4chwdnhxd</DomainExtensionId>
    	<ListenerPort>443</ListenerPort>
    </CreateDomainExtensionResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "149A2470-F010-4437-BF68-343D5099C19D", 
        "DomainExtensionId": "de-bp1k4chwdnhxd", 
        "ListenerPort": 443
    }
    ```


