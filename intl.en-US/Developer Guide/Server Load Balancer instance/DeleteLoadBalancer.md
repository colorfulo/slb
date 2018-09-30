# DeleteLoadBalancer {#reference_kwc_kng_mdb .reference}

Delete an SLB instance.

**Note:** The configurations such as listeners or tags are also deleted after the instance is deleted.

## Request parameters {#section_bqw_c1g_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform.  Valid value:  DeleteLoadBalancer

|
|RegionId|String | Yes|The region of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String |Yes|The ID of the SLB instance.|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteLoadBalancer
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&RegionId=ap-southeast-1
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <DeleteLoadBalancerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </DeleteLoadBalancerResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


