# DescribeRuleAttribute {#reference_fyc_mv2_ndb .reference}

Query the configurations of a forwarding rule.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action |String | Yes|The action to perform. Valid value:DescribeRuleAttribute

|
|RegionId|String | Yes|The ID of the region where the Server Load Balancer instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|RuleId|String | Yes|The ID of the forwarding rule.|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|RuleName|String|The name of the forwarding rule.|
|LoadBalancerId|String|The ID of the Server Load Balancer instance.|
|ListenerPort|Integer|The frontend listener port used by the Server Load Balancer instance.|
|Domain|String|The domain name in the forwarding rule.|
|Url|String|The URL in the forwarding rule.|
|VServerGroupId|String|The ID of the VServer group associated with the forwarding rule.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeRuleAttribute
&RegionId=cn-hangzhou 
&RuleId=rule-3ejhktkaeu
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DescribeRuleAttributeResponse>
    	<RequestId>3E0FA650-1843-466E-8664-3E7D88E0DD5F</RequestId>
    	<Domain>example.com</Domain>
    	<Url>/index</Url>
    	<VServerGroupId>rsp-bp1t8kkfafu8b</VServerGroupId>
    	<LoadBalancerId>lb-bp148m1ohj2juoh9ua7qc</LoadBalancerId>
    	<RuleName>test</RuleName>
    	<ListenerPort>8080</ListenerPort>
    </DescribeRuleAttributeResponse>
    ```

-   JSON format

    ```
    {  
       "RequestId":"3E0FA650-1843-466E-8664-3E7D88E0DD5F",
       "Domain":"example.com",
       "Url":"/index",
       "VServerGroupId":"rsp-bp1t8kkfafu8b",
       "LoadBalancerId":"lb-bp148m1ohj2juoh9ua7qc",
       "RuleName":"test",
       "ListenerPort":8080
    }}
    ```


