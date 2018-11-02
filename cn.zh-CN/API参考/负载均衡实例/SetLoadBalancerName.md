# SetLoadBalancerName {#SetLoadBalancerStatus .reference}

修改负载均衡实例的名称。

## 调试 {#section_yrm_xs5_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerName)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_bqw_c1g_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：SetLoadBalancerName

|
|RegionId|String|否|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例ID。|
|LoadBalancerName|String|是|负载均衡实例的名称。长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|参数|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=SetLoadBalancerName
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&LoadBalancerName=abc
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <SetLoadBalancerNameResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetLoadBalancerNameResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


