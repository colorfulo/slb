# Health Check causes large amounts of log processing {#concept_hpj_h2d_xdb .concept}

The log management of Server Load Balancer can automatically save health check logs within three days. If there are too many health check logs that may affect your maintenance, you can configure to reduce health check logs or prevent the logs from being generated in certain scenarios by using the following options.

**Note:** \>Note: By reducing health check logs, you may be unable to identify problems occurred during the running of Server Load Balancer instance in a timely manner. So configure it as needed.

-   [Get access log](#section_ubj_tgd_xdb)
-   [Adjust health check frequency](#section_a5r_bhd_xdb)
-   [Turn off health check under 7-tier Load Balancing](#section_dj2_rjd_xdb)
-   [Switching 7-tier load balancing to 4-tier Load Balancing](#section_ahx_1ld_xdb)
-   [Disable application logs on the health check page](#section_snb_nnd_xdb)

## Get access log {#section_ubj_tgd_xdb .section}

HTTP health uses the head Request Method by default \(the get method is later opened \), therefore, the actual log of access can be obtained by filtering out the request from head.

## Adjust health check frequency {#section_a5r_bhd_xdb .section}

You can increase the interval between two health checks to reduce the health check counts and logs generated.

Potential risks

After you increase the interval, if the backend ECS instance fails, the time needed for Server Load Balancer to detect the faulty ECS instance is increased accordingly.

Operation Steps

1.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/)。
2.  在实例管理页面中找到相应的负载均衡实例，单击**管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253386_en-US.png)

3.  单击监听进入监听管理页面，找到对应监听，单击**配置**。
4.  在配置监听对话框中单击**下一步**，进入健康检查配置。
5.  调整**健康检查间隔**，范围为1～50秒，间隔越大，健康检查的频率就越低，后端服务器产生的日志也会相应减少。 Please modify according to your actual situation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253390_en-US.png)

6.  单击**确认**完成修改。

## Turn off health check under 7-tier Load Balancing {#section_dj2_rjd_xdb .section}

In layer-7 \(HTTP/HTTPS\) Server Load Balancer, the health check can be implemented by HTTP Head requests. Application logs of the backend ECS instance record the health check request information, leading to a large amount of log data.

Potential risks

After you turn off health check in HTTP/https mode, load balancing no longer checks back-end servers, once a back-end server fails, it is not possible to automatically switch access traffic to other normal back-end servers.

Operation steps

1.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/)。
2.  在实例管理页面中找到对应的负载均衡实例，单击**管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253386_en-US.png)

3.  单击**监听**进入监听管理页面，找到对应监听，单击**配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253388_en-US.png)

4.  在配置监听对话框中单击**下一步**，进入健康检查配置。
5.  关闭**是否开启健康检查**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432263397_en-US.png)

6.  单击**确认**完成修改。

## Switching 7-tier Load Balancing 4-tier Load Balancing {#section_ahx_1ld_xdb .section}

Health checks in the 4-tier TCP mode use only the three-way handshake Implementation of TCP, the Application log is not generated. If your business can switch to 4-tier TCP mode, this method can reduce the application log generation.

Potential risks

After you change the HTTP/HTTPS mode into the TCP mode, Server Load Balancer checks only the status of the listener port, instead of the HTTP status. In this way, Server Load Balancer cannot detect the exceptions occurred to HTTP applications in real time.

Operation steps

1.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/)。
2.  在实例管理页面中找到对应的负载均衡实例，单击**管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253386_en-US.png)

3.  单击**监听**进入监听管理页面，找到对应监听，单击**配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253388_en-US.png)

4.  在配置监听对话框中单击**下一步**，进入健康检查配置。
5.  将**健康检查模式**修改为**TCP**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432263404_en-US.png)

6.  单击**确认**完成修改。

## Disable application logs on the health check page {#section_snb_nnd_xdb .section}

In addition to the business site, configure the Health Check site independently, and close the application log of the Health Check page, you can reduce the number of health check logs. For example, the business site is ABC. 123.com，则使用test. 123.com作为健康检查站点，并关闭test. 123.com站点的日志记录。

Potential risks

If the health check site is running normally, but the service site encounters an exception, the health check cannot detect the exceptions of the service site.

Operation steps

1.  Create a new health check site and health check page on the back-end server and turn off logging. 本操作以ngix为例进行说明。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432263405_en-US.png)

2.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/?spm=a2c63.o282931.a3.9.60c23195z3tLiU)。
3.  在实例管理页面中找到对应的负载均衡实例，单击**管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253386_en-US.png)

4.  单击**监听**进入监听管理页面，找到对应监听，单击**配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432253388_en-US.png)

5.  在配置监听对话框中单击**下一步**，进入健康检查配置。
6.  在**域名**中输入健康检查站点的域名，在**检查路径**中输入健康检查页面的的相对路径。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4302/15393432263414_en-US.png)

7.  单击**确认**完成修改。

