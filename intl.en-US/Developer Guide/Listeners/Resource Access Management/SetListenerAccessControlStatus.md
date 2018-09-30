# SetListenerAccessControlStatus {#slb_api_SetListenerAccessControlStatus .reference}

Enable or disable the access control function of a listener.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required| Description|
|:----|:---|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:SetListenerAccessControlStatus

|
|RegionId|String | Yes|The region of SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of SLB instance.|
|ListenerPort|Integer|Yes|The frontend port used by the SLB instance.Valid value: 1-65535

|
|AccessControlStatus|String | Yes|Whether to enable access control. Valid value:-   open\_white\_list: Enable access control.
-   close: Disable access control.

**Note:** When the access control is enabled, you must configure a whitelist of IP addresses. Otherwise, no access is allowed.

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetListenerAccessControlStatus
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&AccessControlStatus=open_white_list
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetListenerAccessControlStatusResponse>
          <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetListenerAccessControlStatusResponse>
    ```

-   JSON format

    ```
    {
      "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


