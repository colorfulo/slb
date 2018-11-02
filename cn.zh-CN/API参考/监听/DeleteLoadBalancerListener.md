# DeleteLoadBalancerListener {#slb_api_DeleteLoadBalancerListener .reference}

删除监听。

**说明：** 只有当监听的状态为stopped或者running时，才可以删除。

## 调试 {#section_ln4_2wz_qfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancerListener)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_a1k_l1c_ndb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：DeleteLoadBalancerListener

|
|LoadBalancerId|String|是|负载均衡实例的ID。您可以通过调用 DescribeRegions接口获取地域ID。

|
|ListenerPort|Integer|是| 负载均衡实例前端使用的端口。

 取值：1-65535

 |

## 返回参数 {#section_c1k_l1c_ndb .section}

|名称|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_e1k_l1c_ndb .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DeleteLoadBalancerListener
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DeleteLoadBalancerListenerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </DeleteLoadBalancerListenerResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


