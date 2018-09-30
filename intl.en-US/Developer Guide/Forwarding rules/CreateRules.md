# CreateRules {#reference_dzs_pd2_ndb .reference}

Add forwarding rules to an HTTP/HTTPS listener.

## Request parameters {#section_v5w_nds_cz .section}

|Name |Type|Required| Description|
|:----|:---|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:CreateRules

|
|RegionId|String | Yes|The ID of the region where the SLB instance is located.You can obtain the region ID by calling the DescribeRegions API.

|
|LoadBalancerId|String | Yes|The ID of the SLB instance.|
|ListenerPort|String | Yes|The frontend listening port of the SLB instance.Valid value: 1-65535

|
|RuleList|List|Yes|The forwarding rules to add.**Note:** You can add up to 10 forwarding rules in one request.

|

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|RuleName|String | Yes|The name of the forwarding rule.It can contain 1 to 80 characters and can only contain letters, numbers, dashes, slashes, dots, and sublines.

**Note:** The names of different rules in a listener must be unique.

|
|Domain|String| No|The domain name in the request.It can only contain letters, numbers, dashes, or dots.

|
|Url|String| No|The URL.It can contain 1 to 80 characters, and can contain only letters, numbers, dashes, slashes, dots, percent signs, question marks, number signs, or ampersands.

**Note:** You must specify a domain name or a URL, or both of them. The combination of the domain name and the URL must be unique in a listener.

|
|VServerGroupId|String | Yes|The ID of the VServer group associated with the forwarding rule.|

## Response parameters {#section_ssd_pds_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|Rules|List|A list of forwarding rules.|

|Name |Type|Description|
|:----|:---|:----------|
|RuleId|String|The ID of the forwarding rule.|
|RuleName|String|The name of the forwarding rule.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

``` {#public}
https://slb.aliyuncs.com/?Action=CreateRules
&RegionId=cn-hangzhou
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&Rules=[
    {"RuleName":"Rule1","Domain":"abcdefg.com","Url":"/image","VServerGroupId":"Group1"},
    {"RuleName":"Rule2","Domain":"abcdefg.com","Url":"/cache","VServerGroupId":"Group2"},
  ]
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <CreateRulesResponse>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    	<Rules>
    		<Rule>
    			<RuleId>rule-3ejhktkaeu</RuleId>
    			<RuleName>Rule1</RuleName>
    		</Rule>
    		<Rule>
    			<RuleId>rule-tybqi6qkp8</RuleId>
    			<RuleName>Rule2</RuleName>
    		</Rule>
    	</Rules>
    </CreateRulesResponse>
    ```

-   JSON format

    ```
    {
      "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
      "Rules": {
        "Rule ":[
          {
            "RuleId": "rule-3ejhktkaeu",
            "RuleName": "Rule1"
          },
          {
            "RuleId": "rule-tybqi6qkp8",
            "RuleName": "Rule2"
          }
        ]
      }
    }
    ```


