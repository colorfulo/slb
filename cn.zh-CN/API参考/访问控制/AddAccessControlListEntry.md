# AddAccessControlListEntry {#reference_n2r_h4v_tdb .reference}

在访问控制策略组中添加IP条目。

每个策略组可包含多个IP地址条目或IP地址段条目，访问控制策略组的条目限制如下：

|资源|默认限制|
|:-|:---|
|单账号每次可添加的IP地址条目个数|50|
|每个访问控制策略组可包含的条目个数|300|

## 请求参数 {#section_n4h_pyx_5db .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：AddAccessControlListEntry

|
|RegionId|String|是|访问控制策略组的地域ID。|
|AclId|String|是|访问控制策略组ID。|
|AclEntrys|String|否| 访问控制策略组中要添加的IP条目，可以指定IP地址或IP地址段（CIDR block），多个IP地址/地址段之间用逗号隔开。比如：

 \[\{“entry”:”10.0.0.1/24”,”comment”:”条目1”\},\{“entry”:”192.168.0.0/16”,”comment”:”条目2”\}\]

 **说明：** 每次最多可添加50个条目。

 |

## 返回参数 {#section_ehc_jzx_5db .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

```
https://slb.aliyuncs.com/?Action=AddAccessControlListEntry
&RegionId=us-west-1
&AclId=acl-rj9xpxzcwxrukois65yw3
&AclEntrys=[{"entry":"10.0.0.1/24","comment":"条目1"},{"entry":"192.168.0.0/16","comment":"条目2"}]
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <AddAccessControlListEntryResponse>
      <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
    </AddAccessControlListEntryResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
    }
    ```


