# CreateAccessControlList {#reference_n2r_h4v_tdb .reference}

Create an access control list.

You can create multiple access control lists. Each list contains multiple IP addresses or CIDR blocks. Limits on access control lists are as follows:

|Resource|Default limit|
|:-------|:------------|
|The maximum number of access control lists per region.|50|
|The maximum number of IP addresses added each time.|50|
|The maximum number of entries per access control list.|300|
|The maximum number of access control lists per listener.|50|

## Request parameters {#section_n4h_pyx_5db .section}

|Name|Type |Required| Description|
|:---|:----|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:CreateAccessControlList

|
|RegionId|String | Yes|The ID of the region of the access control list.|
|AclName|String | Yes|The name of the access control list.|

## Response parameters {#section_ehc_jzx_5db .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|AclId|String|The ID of the access control list.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

```
https://slb.aliyuncs.com/?Action=CreateAccessControlList
&RegionId=us-west-1
&AclName=group1
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <CreateAccessControlListResponse>
      <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
      <AclId>acl-rj9xpxzcwxrukois65yw3</AclId>
    </CreateAccessControlListResponse>
    ```

-   JSON format

    ```
    {
        "AclId": "acl-rj9xpxzcwxrukois65yw3",
        "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
    }
    ```


