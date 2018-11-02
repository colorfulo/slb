# AddListenerWhiteListItem {#slb_AddListenerWhiteListItem .reference}

添加监听访问控制白名单。

## 调试 {#section_gyd_wwz_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=AddListenerWhiteListItem)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：AddListenerWhiteListItem

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|ListenerPort|Integer|是|负载均衡实例前端使用的端口。取值：1-65535

|
|SourceItems|String|是|访问控制白名单，只转发来自名单中的IP地址的请求。支持输入IP地址或IP地址段（CIDR block形式），多个IP地址或地址段用逗号分隔。

不允许输入0.0.0.0或0.0.0.0/0，若要关闭访问控制，请调用SetListenerAccessControlStatus接口将AccessControlStatus的值设置为close，关闭访问控制。

**说明：** 监听的AccessControlStatus为open\_white\_list时有效。

|

## 返回参数 {#section_ssd_pds_cz .section}

|参数|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=AddListenerWhiteListItem
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&SourceItems=10.10.10.10,10.20.10.3/24
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <AddListenerWhiteListItemResponse>
          <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </AddListenerWhiteListItemResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


