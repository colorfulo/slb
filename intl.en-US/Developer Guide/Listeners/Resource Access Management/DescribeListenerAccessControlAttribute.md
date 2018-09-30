# DescribeListenerAccessControlAttribute {#slb_api_DescribeListenerAccessControlAttribute .reference}

Query the access control configurations of a listener.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required| Description|
|:----|:---|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:DescribeListenerAccessControlAttribute

|
|LoadBalancerId|String | Yes|The ID of SLB instance.|
|ListenerPort|Integer|Yes|The frontend port used by the SLB instance.Valid value: 1-65535

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|AccessControlStatus|String|Whether to enable the access control. Valid value:-   open\_white\_list: Enable the the access control.
-   close: Disable the access control.

|
|SourceItems|String|The access control list.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeListenerAccessControlAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DescribeListenerAccessControlAttributeResponse>
    	<RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    	<AccessControlStatus>open_white_list</AccessControlStatus>
    	<SourceItems>1.1.1.1,1.1.1.0/21</SourceItems>
    </DescribeListenerAccessControlAttributeResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
      "AccessControlStatus": "open_white_list",
      "SourceItems": "1.1.1.1,1.1.1.0/21"
    }
    ```


