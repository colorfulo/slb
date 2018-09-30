# Query Quota-DescribeSlbQuotas {#reference_t5v_dbl_s2b .reference}

Query the resource limits of Server Load Balancer.

## Request parameters {#section_z4m_1dl_s2b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String| Yes|The action to perform. Valid value:DescribeSlbQuotas

|
|RegionId|String| Yes|The region that requires querying the resource limits of Server Load Balancer. This action applies to all SLB instances in this region.|

## Response parameters {#section_th5_kdl_s2b .section}

|Name|Type|Description|
|----|----|-----------|
|Quotas|List|For more information, see [Quotas](#section_vyl_k2l_s2b).If no value is returned, there is no special quota configuration. Query the default value in [Limits](https://help.aliyun.com/document_detail/32459.html?spm=a2c4g.11186623.6.543.7OYrpf).

|
|Name|String|The name of the resource limit.|
|Max|Integer|The maximum value of the resource limit item.|
|Comment|String |The description of the resource limit item.|

## Quotas {#section_vyl_k2l_s2b .section}

|Resource limit name|Resource limit name|Description|Limit scope|Default value|
|-------------------|-------------------|-----------|-----------|-------------|
|Max number of Server certificates per region|server-cers-per-region|`Max number of Server certificates per region`|A single user in a region|100|
|Max number of Client CA certificates per region|client-ca-cers-per-region|`Max number of Client CA certificates per region`|A single user in a region|100|
|Max number of SLB instances that a single backend server can be attached to|slbs-per-backendserver|`Max number of SLB instances that a single backend server can be attached to`|A single SLB instance in a region|50|
|Max number of backend servers can be attached to a single SLB instance|backendservers-per-slb|`Max number of backend servers can be attached to a single SLB instance`|A single SLB instance in a region|200|
|Max number of listeners per SLB instance|listeners-per-slb|`Max number of listeners per SLB instance`|A single SLB instance in a region|50|
|Max number of URL-based forwarding rule per listener|rules-per-listener|`Max number of URL-based forwarding rule per listener`|A single SLB instance in a region|400|
|Max number of domain extensions per listener|domain-extensions-per-listener|`Max number of domain extensions per listener`|A single instance + listener|3|
|Max number of access control lists per region|acls-per-region|`Max number of access control lists per region`|A region account|50|
|Max number of listeners that an single access control list can be attached to|listeners-per-acl|`Max number of listeners that an single access control list can be attached to`|A single listener|50|
|Max number of entries per access control list|entries-per-acl|`Max number of entries per access control list`|A single access control list|300|
|Max number of SLB instances per account|slbs-per-user|`Max number of SLB instances per account`|global|60|

## Examples {#section_qjx_rsp_42b .section}

**Request example**

```

https://slb.aliyuncs.com?Action=DescribeSlbQuotas
&RegionId=cn-hangzhou
&CommonParameters
```

```

https://slb.aliyuncs.com?Action=DescribeSlbQuotas
&RegionId=cn-hangzhou
&<CommonParameters>
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    	<RequestId>980F7B6D-EF5F-40AF-BA92-A743149AA79D</RequestId>
    	<Quotas>
    		<Quota>
    			<Comment>Max number of Server certificates per region</Comment>
    			<Max>100</Max>
    			<QuotaName>server-cers-per-region</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of Client CA certificates per region</Comment>
    			<Max>100</Max>
    			<QuotaName>client-ca-cers-per-region</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of SLB instances that a single backend server can be attached to</Comment>
    			<Max>50</Max>
    			<QuotaName>slbs-per-backendserver</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of backend servers can be attached to a single SLB instance</Comment>
    			<Max>200</Max>
    			<QuotaName>backendservers-per-slb</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of listeners per SLB instance</Comment>
    			<Max>50</Max>
    			<QuotaName>listeners-per-slb</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of forwarding rule per listener</Comment>
    			<Max>20</Max>
    			<QuotaName>rules-per-listener</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of extension domains per listener</Comment>
    			<Max>3</Max>
    			<QuotaName>domain-extensions-per-listener</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of access control lists per region</Comment>
    			<Max>50</Max>
    			<QuotaName>acls-per-region</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of listeners that an single access control list can be attached to</Comment>
    			<Max>50</Max>
    			<QuotaName>listeners-per-acl</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of entries per access control list</Comment>
    			<Max>300</Max>
    			<QuotaName>entries-per-acl</QuotaName>
    		</Quota>
    	</Quotas>
    ```

-   JSON format

    ```
    {
        "RequestId": "980F7B6D-EF5F-40AF-BA92-A743149AA79D", 
        "Quotas ":{
            "Quota": [
                {
                    "Comment": "Max number of server certificates per region ", 
                    "Max": 100, 
                    "QuotaName": "server-cers-per-region"
                }, 
                {
                    "Comment": "Max number of Client CA certificates per region", 
                    "Max": 100, 
                    "QuotaName": "client-ca-cers-per-region"
                }, 
                {
                    "Comment": "Max number of SLB instances that a single backend server can be attached to", 
                    "Max": 50, 
                    "QuotaName": "slbs-per-backendserver"
                }, 
                {
                    "Comment:" Max number of backend servers can be attached to a single SLB instance ", 
                    "Max": 200, 
                    "QuotaName": "backendservers-per-slb"
                }, 
                {
                    "Comment": "Max number of listeners per SLB instance", 
                    "Max": 50, 
                    "QuotaName": "listeners-per-slb"
                }, 
                {
                    "Comment": "Max number of forwarding rule per listener", 
                    "Max": 20, 
                    "QuotaName": "rules-per-listener"
                }, 
                {
                    "Comment": "Max number of extension domains per listener", 
                    "Max": 3, 
                    "QuotaName": "domain-extensions-per-listener"
                }, 
                {
                    "Comment": "Max number of access control lists per region", 
                    "Max": 50, 
                    "QuotaName": "acls-per-region"
                }, 
                {
                    "Comment": "Max number of listeners that an single access control list can be attached to", 
                    "Max": 50, 
                    "QuotaName": "listeners-per-acl"
                }, 
                {
                    "Comment": "Max number of entries per access control list", 
                    "Max": 300, 
                    "QuotaName": "entries-per-acl"
                }
            ]
        }
    }
    ```


