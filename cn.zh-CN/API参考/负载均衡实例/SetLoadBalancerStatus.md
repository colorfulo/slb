# SetLoadBalancerStatus {#slb_api_SetLoadBalancerStatus .reference}

设置负载均衡实例的状态。

## 调试 {#section_uft_fl5_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerStatus)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_bqw_c1g_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值： SetLoadBalancerStatus

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|LoadBalancerStatus|String|是|负载均衡实例状态。取值：-   active（默认值）

当负载均衡实例的状态为active时，实例中的监听可以根据规则转发接收的流量。

实例创建后的状态默认为active。

-   inactive

当负载均衡实例的状态为inactive时，实例中的监听不会再转发接收的流量。


**说明：** 当一个实例下的所有监听都被删除后，实例状态会被自动改为inactive。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=SetLoadBalancerStatus
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&LoadBalancerStatus=active
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <SetLoadBalancerStatusResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </SetLoadBalancerStatusResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


