# SetLoadBalancerName {#SetLoadBalancerStatus .reference}

Modify the name of an SLB instance.

## Request parameters {#section_bqw_c1g_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform.  Valid value: SetLoadBalancerName

|
|RegionId|String| No|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of the SLB instance.|
|LoadBalancerName|String | Yes|The name of the SLB instance.The name can contain from 2 to 128 characters including a-z, A-Z, 0-9, periods, underlines, and hyphens, and must start with an English letter.

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetLoadBalancerName
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&LoadBalancerName=abc
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetLoadBalancerNameResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetLoadBalancerNameResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


