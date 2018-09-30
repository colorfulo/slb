# DeleteRules {#reference_xgj_xf2_ndb .reference}

Delete forwarding rules.

## Request parameters {#section_v5w_nds_cz .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:DeleteRules

|
|RegionId|String|Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|RuleIds|List|Yes|The forwarding rules to delete.|

## Response parameters {#section_ssd_pds_cz .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteRules
&RegionId=cn-hangzhou 
&RuleIds=[rule-tybqi6qkp8,rule-3ejhktkaeu]
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DeleteRulesResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    </DeleteRulesResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
    }
    ```


