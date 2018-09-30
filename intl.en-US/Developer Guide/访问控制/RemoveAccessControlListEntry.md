# RemoveAccessControlListEntry {#reference_n2r_h4v_tdb .reference}

Delete IP entries in an access control list.

## Request parameters {#section_n4h_pyx_5db .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The action to perform. Valid value:RemoveAccessControlListEntry

|
|RegionId|String|Yes|The ID of the region of the access control list.|
|AclId|String|Yes|The ID of the access control list.|
|AclEntrys|List|No| The IP entries to be deleted. The IP entry can either be an IP address or a CIDR block. Separate multiple IP addresses or CIDR blocks by commas. For example:

 \[\{“entry”:”10.0.0.1”,”comment”:”Entry 1”\},\{“entry”:”192.168.0.0/16”,”comment”:”Entry 2”\}\]

 **Note:** If the access control list is associated with a listener, deleting all IP entries in the access control list is not allowed.

 |

## Response parameters {#section_ehc_jzx_5db .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

```
https://slb.aliyuncs.com/?Action=RemoveAccessControlListEntry
&RegionId=us-west-1
&AclId=acl-rj9xpxzcwxrukois65yw3
&AclEntrys=[{"entry":"10.0.0.1","comment":"Entry 1"}]
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <RemoveAccessControlListEntryResponse>
      <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
    </RemoveAccessControlListEntryResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
    }
    ```


