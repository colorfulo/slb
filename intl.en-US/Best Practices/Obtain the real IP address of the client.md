# Obtain the real IP address of the client {#concept_xp3_zj5_vdb .concept}

## Introduction to the function of obtaining IP address {#section_sbt_c2w_wdb .section}

Alibaba Cloud Server Load Balancer provides the function of obtaining the real IP address of the client and this function is enabled by default.

-   For the Layer-4 load balancing service \(TCP protocol\), listeners distribute client requests to backend ECS servers without modifying the request headers. Therefore, you can obtain the real IP address from the backend ECS servers without additional configurations.
-   For the Layer-7 load balancing service \(HTTP/HTTPS protocol\), you have to configure the application servers, and then use the X-Forwarded-For header to obtain the real IP addresses of the clients.

    The real client IP is put in the X-Forwareded-For field of the HTTP header in the following format:

    ```
    X-Forwarded-For: the real IP of the user, the proxy server 1-IP, the proxy server 2-IP, ...
    ```

    When this method is used to obtain the real IP of the client, the first IP obtained is the real IP of the client.

    **Note:** For the HTTPS load balancing service, the SSL certificates are configured in front-end listeners, the backend still uses the HTTP protocol. Therefore, the configurations on application servers are the same for HTTP and HTTPS protocols.


## Configure IIS7/IIS8 {#section_jcy_l2w_wdb .section}

1.  [Download](https://img.alicdn.com/tfscom/TB1R64PLVXXXXaaXVXXXXXXXXXX.rar?spm=a2c4g.11186623.2.5.z475ev&file=TB1R64PLVXXXXaaXVXXXXXXXXXX.rar) and extract F5XForwardedFor.
2.  Copy the F5XFFHttpModule.dll and F5XFFHttpModule.ini files from the x86\\Release or x64\\Release directory of your server to a specified directory, such as C:\\F5XForwardedFor\\. Make sure that the IIS process has the write permission to this folder.
3.  Open the **IIS Manager** and double-click the **Modules** function.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4171/15382791543132_en-US.png)

4.  Click **Configure Native Modules**, and then click **Register** in the displayed dialog box.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4171/15382791543133_en-US.png)

5.  Add the downloaded .dll file.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4171/15382791543135_en-US.png)

6.  Add the ISAPI and CGI restrictions for the added files and set the restrictions to Allowed.

    **Note:** Make sure that you have installed the ISAPI and CGI applications.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4171/15382791543136_en-US.png)

7.  Restart the IIS Manager.

## Configure Apache {#section_ebz_smw_wdb .section}

1.  Run the following command to install the mod\_rpaf module.

    ```
     wget https://github.com/gnif/mod_rpaf/archive/v0.6.0.tar.gz
     tar zxvf mod_rpaf-0.6.tar.gz
     cd mod_rpaf-0.6
     /alidata/server/httpd/bin/apxs -i -c -n mod_rpaf-2.0.so mod_rpaf-2.0.c
    ```

2.  Open the /alidata/server/httpd/conf/httpd.conf file and add the following information at the end of the content.

    ```
     LoadModule rpaf_module modules/mod_rpaf-2.0.so
     RPAFenable On
     RPAFsethostname On
     RPAFproxy_ips &lt;IP_address>
     RPAFheader X-Forwarded-For
    ```

    **Note:** To obtain the IP address of the proxy server, add the CIDR block of the proxy server to `RPAFproxy_ips &lt;IP_address>`, such as the IP address range of SLB \(100.64.0.0/10（100.64.0.0/10 是阿里云保留地址，其他用户无法分配到该网段内，不会存在安全风险）\) and the address range of Anti-DDoS Pro. Separate multiple CIDR blocks by commas.

3.  Restart Apache after the adding.

    ```
    /alidata/server/httpd/bin/apachectl restart
    ```


## Configure the Nginx server {#section_r43_fsw_wdb .section}

1.  Run the following command to install http\_realip\_module.

    ```
     wget http://nginx.org/download/nginx-1.0.12.tar.gz
     tar zxvf nginx-1.0.12.tar.gz
     cd nginx-1.0.12
     ./configure --user=www --group=www --prefix=/alidata/server/nginx --with-http_stub_status_module --without-http-cache --with-http_ssl_module --with-http_realip_module
     make
     make install
     kill -USR2 `cat /alidata/server/nginx/logs/nginx.pid`
     kill -QUIT `cat /alidata/server/nginx/logs/ nginx.pid.oldbin`
    ```

2.  Open the nginx.conf file.

    ```
    vi /alidata/server/nginx/conf/nginx.conf
    ```

3.  Add new configuration fields and information behind the following configuration information.

    ```
     fastcgi connect_timeout 300;
     fastcgi send_timeout 300;
     fastcgi read_timeout 300;
     fastcgi buffer_size 64k;
     fastcgi buffers 4 64k;
     fastcgi busy_buffers_size 128k;
     fastcgi temp_file_write_size 128k;
    ```

    The configuration fields and information that need to be added are:

    ```
     set_real_ip_from IP_address
     real_ip_header X-Forwarded-For;
    ```

    **Note:** To obtain the IP address of the proxy server, add the CIDR block of the proxy server to `RPAFproxy_ips &lt;IP_address>`, such as the IP address range of SLB \(100.64.0.0/10（100.64.0.0/10 是阿里云保留地址，其他用户无法分配到该网段内，不会存在安全风险）\) and the address range of Anti-DDoS Pro. Separate multiple CIDR blocks by commas.

4.  Restart Nginx.

    ```
    /alidata/server/nginx/sbin/nginx -s reload
    ```


