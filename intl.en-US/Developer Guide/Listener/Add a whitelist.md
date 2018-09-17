# Add a whitelist {#doc_api_555060 .reference}

Configure a whitelist for a listener.

Configure a whitelist for a listener. This API supports incremental updates.

## Request parameters {#parameters .section}

|Name|Type|Required|Example value|Description|
|----|----|--------|-------------|-----------|
|Action|String |Yes|AddListenerWhiteListItem|The action to perform. Valid value:

AddListenerWhiteListItem|
|ListenerPort|Integer|Yes|80|The front-end port of the listener that is used to receive incoming traffic and distribute the traffic to the backend servers. Valid value: \[1, 65535\]

|
|LoadBalancerId|String|Required|139a00604ad-cn-east-hangzhou-01|The ID of the Server Load Balancer instance.

|
|RegionId|String|Required|cn-hangzhou|Select the region where the instance is located.

|
|SourceItems|String |Yes|1.1.1.1,1.1.1.0/21| |
|Tags|String|No|tag1|The tag of the listener.

|

## Response parameter {#resultMapping .section}

|Name|Type|Example value|Required|
|----|----|-------------|--------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. 

|

## Examples {#demo .section}

Request example

``` {#request_demo}

https://slb.aliyuncs.com/
&Action=AddListenerWhiteListItem
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&ListenerPort=80
&SourceItems=1.1.1.1,1.1.1.0/21
&Public request parameters

```

Success response example

`XML` format

``` {#xml_return_success_demo}
<AddListenerWhiteListItemResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</AddListenerWhiteListItemResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

Error response example

`JSON` format

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"cdn.aliyuncs.com",
	"Code": "InvalidParameter"
}
```

## Error codes { .section}

[View error codes.](https://error-center.aliyun.com/status/product/Slb)

