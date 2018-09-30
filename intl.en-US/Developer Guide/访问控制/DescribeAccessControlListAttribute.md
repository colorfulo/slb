# DescribeAccessControlListAttribute {#reference_n2r_h4v_tdb .reference}

Query the configurations of an access control list.

## Request parameters {#section_n4h_pyx_5db .section}

|Name|Type |Required| Description|
|:---|:----|:-------|:-----------|
|Action |String | Yes|The action to perform. Valid value:DescribeAccessControlListAttribute

|
|RegionId|String | Yes|The ID of the region of the access control list.|
|Aclid|String | Yes|The ID of the access control list.|
|AclEntryComment|String| No|The description of the route entry in the access control list.|

## Response parameters {#section_ehc_jzx_5db .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|AclId|String|The ID of the access control list.|
|AclName|String|The name of the access control list.|
|AclEntrys|List|The IP entries in the access control list.|
|RelatedListeners|List|The listeners associated with the access control list.|

|Name |Type|Description|
|:----|:---|:----------|
|AclEntryIP|String|The IP of the entry in the access control list.|
|AclEntryComment|String|The comment of the entry in the access control list.|

|Name |Type|Description|
|:----|:---|:----------|
|LoadBalancerId|String|The ID of the Server Load Balancer instance.|
|ListenerPort|Integer|The frontend port of the listener.|
|Protocol|Integer|The protocol used by the listener.|
|AclType|String|The access control type:-   black: blacklist
-   white: whitelist

|

## Examples {#section_oxr_pds_cz .section}

**Request example**

```
https://slb.aliyuncs.com/?Action=DescribeAccessControlListAttribute
&RegionId=us-west-1
&AclId=acl-0xiowxdr4drxtm2w8hupo
&CommonParameters
```

**Response examples**

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <DescribeAccessControlListAttributeResponse>
    <AclName>group1</AclName>
    <RequestId>6669026E-067E-47B6-8106-EA810382A3BB</RequestId>
    <AclEntrys>
      <AclEntry>
        <AclEntryComment>1,10.10.0.0/24</AclEntryComment>
        <AclEntryIP>10.10.0.0/24</AclEntryIP>
      </AclEntry>
    </AclEntrys>
    <AclId>acl-0xiowxdr4drxtm2w8hupo</AclId>
    <RelatedListeners>
      <RelatedListener>
        <AclType>white</AclType>
        <LoadBalancerId>lb-0xiw3x1ljvd2a5golok5v</LoadBalancerId>
        <Protocol>https</Protocol>
        <ListenerPort>443</ListenerPort>
      </RelatedListener>
    </RelatedListeners>
    </DescribeAccessControlListAttributeResponse>
    ```

-   JSON format

    ```
    {
      "AclName": "group1",
      "RequestId": "6669026E-067E-47B6-8106-EA810382A3BB"
      "AclEntrys": {
          "AclEntry": [
              {
                  "AclEntryComment": "1,10.10.0.0/24",
                  "AclEntryIP": "10.10.0.0/24"
              }
          ]
        },
          "AclId": "acl-0xiowxdr4drxtm2w8hupo",
          "RelatedListeners": {
          "RelatedListener": [
              {
                  "AclType": "white",
                  "LoadBalancerId": "lb-0xiw3x1ljvd2a5golok5v",
                  "Protocol": "https",
                  "ListenerPort": 443
              }
          ]
      }
    }
    ```


