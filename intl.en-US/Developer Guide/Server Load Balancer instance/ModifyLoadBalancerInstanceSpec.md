# ModifyLoadBalancerInstanceSpec {#reference_i4w_xmt_ndb .reference}

Modify the specification of a guaranteed-performance SLB instance.

## Request parameters {#section_cch_pjg_mdb .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform.  Valid value: ModifyLoadBalancerInstanceSpec

|
|RegionId|String | Yes|The region of the SLB instance.You can query the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of the SLB instance.|
|LoadBalancerSpec|String | Yes|The specification of the SLB instance. Valid value:-   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

The available specifications vary by region. For more information, see [Guaranteed-performance instances](../../../../reseller.en-US/User Guide/SLB instances/Guaranteed-performance instances.md#).

**Note:** When you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. We recommend that you perform this operation when the traffic is low or use GSLB to schedule the service to other SLB instances first.

|

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|orderId|String|预付费实例的订单ID。|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=ModifyLoadBalancerInstanceSpec 
&RegionId=us-east-01
&LoadBalancerId=139a00604ad-us-east-01
&LoadBalancerSpec=slb.s2.small 
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <ModifyLoadBalancerInstanceSpecResponse>
      <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    </ModifyLoadBalancerInstanceSpecResponse>
    ```

-   JSON format

    ```
    {
      "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    }
    ```


