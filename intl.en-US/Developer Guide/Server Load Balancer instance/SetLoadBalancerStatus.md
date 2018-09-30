# SetLoadBalancerStatus {#slb_api_SetLoadBalancerStatus .reference}

Set the status of an SLB instance.

## Request parameters {#section_bqw_c1g_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value: SetLoadBalancerStatus

|
|RegionId|String|Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String|Yes|The ID of the Server Load Balancer instance.|
|LoadBalancerStatus|String|Yes|The status of the SLB instance. Valid value:-   active \(default\)

You can set the status to active when you want an active SLB instance to restart distributing traffic.

By default, the SLB instance status is active.

-   inactive

If you set the status of an SLB instance to inactive, the listeners in the instance cannot distribute traffic any more.


**Note:** The instance status changes to inactive if all the listeners of the instance are deleted.

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=SetLoadBalancerStatus
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&LoadBalancerStatus=active
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <SetLoadBalancerStatusResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetLoadBalancerStatusResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


