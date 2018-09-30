# DescribeRules {#reference_nhj_wg2_ndb .reference}

Query forwarding rules associated with a listener.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required| Description|
|:----|:---|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:DescribeRules

|
|RegionId|String | Yes|The region ID of the SLB instance.|
|LoadBalancerId|String | Yes|The ID of the SLB instance.You can obtain the region ID by calling the DescribeRegions API.

|
|ListenerPort|String | Yes|The frontend listening port of the SLB instance.Valid value: 1-65535

|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|Rules|String|A list of rules.|

|Name |Type|Description|
|:----|:---|:----------|
|RuleId|String|The ID of the forwarding rule.|
|RuleName|String|The name of the forwarding rule.|
|Domain|String|The domain name.|
|Url|String|The URL.|
|VServerGroupId|String|The ID of the target VServer group of the forwarding rule.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeRules
&RegionId=cn-hangzhou
&LoadBalancerId=lb-152a602e315
&ListenerPort=80
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DescribeRulesResponse>	
        <RequestId>C9E4B5F7-1AA8-4578-9D59-8525C32BAD41</RequestId>
    	<Rules>
    		<Rule>
    			<Url>/index</Url>
    			<Domain>example.com</Domain>
    			<VServerGroupId>rsp-bp1t8kkfafu8b</VServerGroupId>
    			<RuleId>rule-bp1ixgmll8x92</RuleId>
    			<RuleName>Rule2</RuleName>
    		</Rule>
    		<Rule>
    			<Url>/index</Url>
    			<Domain>test.com</Domain>
    			<VServerGroupId>rsp-bp1t8kkfafu8b</VServerGroupId>
    			<RuleId>rule-bp16ryrpwbg01</RuleId>
    			<RuleName>test2</RuleName>
    		</Rule>
    	</Rules>
    </DescribeRulesResponse>
    ```

-   JSON format

    ```
    {
       "RequestId":"C9E4B5F7-1AA8-4578-9D59-8525C32BAD41",
       "Rules": {
          "Rule ":[
             {
                "Url":"/index",
                "Domain":"example.com",
                "VServerGroupId":"rsp-bp1t8kkfafu8b",
                "RuleId":"rule-bp1ixgmll8x92",
                "RuleName":"test"
             },
             {
                URL: "/Index ",
                "DomainName":"test.com",
                "VServerGroupId":"rsp-bp1t8kkfafu8b",
                "RuleId":"rule-bp16ryrpwbg01",
                "RuleName":"test2"
             }
          ]
       }
    }
    ```


