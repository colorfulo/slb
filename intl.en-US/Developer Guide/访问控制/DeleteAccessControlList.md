# DeleteAccessControlList {#reference_n2r_h4v_tdb .reference}

Delete an access control list.

**Note:** An access control list can be deleted only when it is not bound to any listener.

## Request parameters {#section_n4h_pyx_5db .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|To action to perform. Valid value:DeleteAccessControlList

|
|RegionId|String|Yes|The ID of the region of the access control list.|
|AclId|String|Yes|The ID of the access control list.|

## Response parameters {#section_ehc_jzx_5db .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|

## Examples {#section_oxr_pds_cz .section}

**Request example**

```
https://slb.aliyuncs.com/?Action=DeleteAccessControlList
&RegionId=us-west-1
&AclId=acl-rj9xpxzcwxrukois65yw3
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DeleteAccessControlListResponse>
      <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
    </DeleteAccessControlListResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
    }
    ```


