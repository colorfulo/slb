# HTTPS/HTTP监听常见问题 {#concept_ldw_gh5_vdb .concept}

## 1. 为什么请求经过七层负载均衡转发后，后端服务器的响应头中的某些参数会被删除？ {#section_iv5_pyx_wdb .section}

为了实现会话保持，负载均衡会修改后端服务器响应头中的Date、Server、X-Pad和X-Accel-Redirect等参数值。

解决方案：

-   在自定义的报文头部中加入一个前缀，如xl-server或xl-date，以避开负载均衡的处理。
-   将七层HTTP监听改为四层TCP监听。

## 2. 为什么在HTTP请求的头部增加了Transfer-Encoding: chunked字段？ {#section_kv5_pyx_wdb .section}

将域名解析到七层负载均衡的服务地址后，从本地主机访问域名时发现在HTTP请求的头部增加了一个Transfer-Encoding: chunked字段，但是从本地主机直接访问后端服务器时是没有这个字段的。

由于七层负载均衡基于Tengine反向代理实现。Transfer-Encoding字段表示Web服务器如何对响应消息体编码，比如Transfer-Encoding: chunked表示Web服务器对响应消息体做了分块传输。

**说明：** 在四层负载均衡服务中，负载均衡仅转发流量，不存在该字段。

## 3. 为什么HTTP监听访问正常但HTTPS监听打开网址不加载样式？ {#section_lv5_pyx_wdb .section}

现象：

分别创建HTTP和HTTPS监听，两个监听使用同样的后端服务器。以HTTP方式访问监听端口对应的网站时，网站正常显示，但使用HTTPS监听访问时，网站排版显示错乱。

原因：

负载均衡默认是不会屏蔽JS文件加载传输的，可能原因：

-   证书和浏览器安全级别不兼容导致。
-   证书是非正规第三方证书需要联系证书发布者检查证书问题。

解决方案：

1.  打开网站时，按照浏览器提示加载脚本。
2.  在客户端中添加对应证书。

## 4. HTTPS监听使用什么端口？ {#section_ov5_pyx_wdb .section}

HTTPS监听对端口无特殊要求，建议您使用443端口。

## 5. 负载均衡支持哪些类型的证书？ {#section_pv5_pyx_wdb .section}

支持上传PEM格式的服务器证书和CA证书。

服务器证书需要上传证书内容和私钥；CA证书只需要上传证书内容。

## 6. 负载均衡是否支持keytool创建的证书？ {#section_qv5_pyx_wdb .section}

支持。

但在上传证书前，您需要将证书转换为PEM格式，详情参见[转换证书格式](../../../../intl.zh-CN/用户指南（旧版，即将下线）/证书管理/转换证书格式.md#)。

## 7. 可以使用PKCS\#12（PFX）格式的证书么？ {#section_rv5_pyx_wdb .section}

可以。

但在上传证书前，您需要将证书转换为PEM格式，详情参见[转换证书格式](../../../../intl.zh-CN/用户指南（旧版，即将下线）/证书管理/转换证书格式.md#)。

## 8. 一个账号可以上传多少个证书？ {#section_sv5_pyx_wdb .section}

每个账号最多可上传100个证书，包含CA证书和服务器证书。

## 9. 添加证书时，为什么会出现KeyEncryption的错误？ {#section_tv5_pyx_wdb .section}

该错误由于私钥内容有误导致。关于私钥格式说明，参见[证书要求](../../../../intl.zh-CN/用户指南（旧版，即将下线）/证书管理/证书要求.md#)。

## 10. 一个HTTPS监听可绑定多少证书？ {#section_uv5_pyx_wdb .section}

性能共享型负载均衡实例若使用HTTPS单向认证，则一个监听只能绑定一个服务器证书；若使用HTTPS双向认证，则一个监听需要绑定一个服务器证书和一个CA证书。

性能保障型负载均衡HTTPS监听支持挂载多个证书，将来自不同访问域名的请求转发至不同的后端服务器组，详细操作请参见[配置教程](../../../../intl.zh-CN/教程/单SLB实例配置多域名HTTPS网站.md#)。

## 11. 负载均衡HTTPS支持哪些SSL协议版本？ {#section_vv5_pyx_wdb .section}

TLSv1、TLSv1.1以及TLSv1.2。

## 12. 为什么HTTPS协议实际产生的流量会比账单流量多一些？ {#section_wv5_pyx_wdb .section}

HTTPS协议会使用一些流量用于协议握手，因此其实际产生的流量会多于帐单流量。

## 13. HTTPS session ticket的保持时间是多久？ {#section_xv5_pyx_wdb .section}

HTTPS session ticket保持时间为300秒。

## 14. 可以上传包含DH PARAMETERS字段的证书么？ {#section_yv5_pyx_wdb .section}

HTTPS监听使用的ECDHE算法簇支持前向保密技术，不支持将DHE算法簇所需要的安全增强参数文件上传，即不支持将PEM证书文件中含BEGIN DH PARAMETERS字段的证书上传。

## 15. HTTPS监听是否支持SNI？ {#section_zv5_pyx_wdb .section}

SNI（Server Name Indication）是为了解决一个服务器使用多个域名和证书的SSL/TLS扩展，负载均衡HTTPS监听支持SNI功能，具体请参见[配置教程](../../../../intl.zh-CN/用户指南（旧版，即将下线）/监听/七层监听/扩展域名/配置教程.md#)。

## 16. HTTP/HTTPS监听访问后端服务器的HTTP协议版本是什么？ {#section_aw5_pyx_wdb .section}

HTTP/1.0。

## 17. 后端服务器能否获取客户端访问HTTP/HTTPS监听的协议版本？ {#section_bw5_pyx_wdb .section}

可以。

## 18. 一个请求通过负载均衡到达后端服务器，如果客户端在未收到后端服务器的回复前主动断开和负载均衡的连接，负载均衡会同时断开和后端服务器的连接么？ {#section_cw5_pyx_wdb .section}

负载均衡在读写过程中不会断开与后端服务器的连接。

## 19. HTTP/HTTPS监听是否支持WebSocket/SSL WebSocket? {#section_dw5_pyx_wdb .section}

全部地域都已支持WSS/WS协议，详情参见[WS/WSS协议支持常见问题](intl.zh-CN/常见问题/WS/WSS协议支持常见问题.md#)。

## 20. HTTP/HTTPS连接的超时时间是如何规定的？ {#section_d44_xyx_wdb .section}

-   HTTP长连接的请求数量限定是最多连续发送100个请求，超过限定将关闭这条连接。
-   HTTP长连接两个HTTP/HTTPS请求之间的超时时间为15秒（存在误差1-2秒），超过后会关闭TCP连接，如果用户有长连接使用需求请尽量保持在13秒之内发送一个心跳请求。
-   负载均衡与后端一台ECS实例TCP三次握手完成过程的超时时间为5秒，超时后选择下一台ECS实例；查询访问日志的upstream响应时间可以定位。
-   负载均衡等待一台ECS实例回复请求的响应时间是60秒，超过后一般会返回504响应码或408响应码给客户端；查询访问日志的upstream响应时间可以定位。
-   HTTPS session重用超时间为300秒，超过后同一客户端需要重新进行完整的SSL握手过程。

## 21. 负载均衡是否支持配置域名和URL转发策略？ {#section_fw5_pyx_wdb .section}

支持，详情参见[配置域名URL转发策略](../../../../intl.zh-CN/用户指南（旧版，即将下线）/监听/七层监听/添加域名和路径转发.md#)。

## 22. 每个监听可以添加多少条域名和URL转发规则？ {#section_gw5_pyx_wdb .section}

每个监听最多可添加20条转发规则。

