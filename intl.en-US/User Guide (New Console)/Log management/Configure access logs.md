# Configure access logs {#concept_bl3_24n_vdb .concept}

Integrated with Alibaba Cloud Log Service, you can understand the behavior and geographical distribution of client users, troubleshoot problems by analyzing the access logs of a Server Load Balancer instance.

## What are access logs? {#section_h3l_1ls_vdb .section}

The access log collects detailed information of all requests sent to a Server Load Balancer instance, including the request time, client IP address, latency, request URL, server response, and so on. As the entry of Internet access, Server Load Balancer receives massive client requests. You can use access logs to analyze user behavior and geographical distribution, troubleshoot issues.

After you enable the SLB access logs, you can store the access logs in the Logstore of SLS to collect and analyze the access logs. You can also disable access logs at any time.

There is no extra fee for Server Load Balancer access logs. You only need to pay for the Log Service.

**Note:** 

-   Only Layer-7 Server Load Balancer supports configuring access logs and this function is available in all regions now.
-   Make sure that the HTTP header value does not contain `||`, otherwise, the exported logs may be misplaced.

## Benefits {#section_jzd_pls_vdb .section}

The following are benefits of Server Load Balancer access logs:

-   Easy to use

    Free developers and maintenance staff from tedious and time-consuming log processing so that they can concentrate on business development and technical research.

-   Cost-effective

    Access logs are typically very large. Processing access logs takes a lot of time and consumes a lot of resources. With Log Service, the access log processing is faster and cost-effective than self-build open-source solutions. Log Service can analyze one hundred million logs in one second.

-   Real-time

    Scenarios such as DevOps, monitoring, and alerting require real-time log data. Traditional data storage and analysis tools cannot meet this requirement. For example, it takes long time to ETL data to Hive where a lot of work is spent on data integration. Powered by its powerful computing capability, Log Service can process and analyze access logs in seconds.

-   Flexible

    You can enable or disable Server Load Balancer access logs according to the instance capacity. Additionally, you can set the storage period \(1 to 365 days\) as needed and the Logstore's capacity is scalable to meet increasing business service demands.


## Configure access logs {#section_ntc_tls_vdb .section}

Before configuring access logs, make sure:

1.  A Layer-7 listener is added.
2.  Log Service is activated.

To configure access logs, complete these steps.

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, click **Logs** \> **Access Logs**.
3.  Select a region.
4.  Click **Authorize**, and then click **Confirm Authorization Policy** to authorize Server Load Balancer to write logs to Log Service.

    If you are using a RAM account, the primary account is required to perform authorization. For more information, see [Authorize a RAM user to use access logging](intl.en-US/User Guide/Log management/Authorize a RAM user to configure access logs.md#).

    **Note:** This operation is required only at the first time.

5.  On the Access Logs page, find the target Server Load Balancer instance and click **Configure Logging**.
6.  Select the LogProject and LogStore of Log Service and then click **OK**.

    If there is no available LogStore, click **Log Service console** to create log projects.

    **Note:** Make sure that the name of the LogProject is globally unique and the region of the LogProject is the same as that of the Server Load Balancer instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15368937867478_en-US.png)


## Search and analyze access logs {#section_od1_l4s_vdb .section}

After configuring Server Load Balancer access logs, you can search and view logs using the following indexing fields.

|Field|Field description|
|:----|:----------------|
|body\_bytes\_sent|The size of HTTP body \(in byte\) sent to the client.|
|Client\_ip|The client IP.|
|host |The host header in the request.|
|http\_user\_agent|The received http\_user\_agent header in the request.|
|request\_length |The length of the request including startline, HTTP header and HTTP body.|
|request\_method |The request method.|
|request\_time|The interval between the time the Server Load Balancer receives the first request and the time the Server Load Balancer returns a response.|
|Request\_uri|The URL of the received request.|
|Slbid|The ID of the Server Load Balancer instance.|
|status|The response status code sent by the SLB.|
|Upstream\_addr|The IP address and port number of the backend server.|
|upstream\_response\_time |The interval between the time Server Load Balancer sends a request to the backend server and the time Server Load Balancer sends a response to the client.|
|Upstream\_status|The response status code of the backend server received by SLB.|

## Search access logs {#section_hd5_r4s_vdb .section}

To search access logs, complete these steps:

1.  Go to the log search page. You can navigate to the search page from the Server Load Balancer console or the Log Service Console:
    -   From the Server Load Balancer console:

        On the Access Logs page, click **View Logs**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15368937877479_en-US.png)

    -   From the Log Service console:

        On the Logstores page, click **Search** of the target Logstore.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15368937872492_en-US.png)

2.  Click the corresponding index field to view detailed information.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15368937872493_en-US.png)

3.  Enter an SQL statement to query.

    For example, enter the following SQL statement to query Top 20 clients.

    ```
    * | select ip_to_province(client_ip) as client_ip_province, count(*) as pv group by
          client_ip_province order by pv desc limit 50
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15368937872494_en-US.png)


## Analyze access logs {#section_cvs_xps_vdb .section}

You can analyze access logs through the dashboard, which provides various graphic information.

To analyze access logs, complete these steps:

1.  On the Log Service console, click the project name of the target project.
2.  In the left-side navigation pane, click **Search/Analytics - Query** \> **Dashboard**, and then click **View**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15368937872495_en-US.png)


## Disable access logging {#section_vgd_kqs_vdb .section}

To disable access logging, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, click **Logs** \> **Access Logs**.
3.  Select a region.
4.  On the Access Logs page, find the target instance and click **Delete** to disable access logging.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15368937877480_en-US.png)

5.  Click **OK** in the displayed dialog box.

