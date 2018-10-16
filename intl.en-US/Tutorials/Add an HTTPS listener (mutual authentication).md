# Add an HTTPS listener \(mutual authentication\) {#concept_mkk_3j5_vdb .concept}

To add an HTTPS listener with mutual authentication, you have to upload a server certificate and a CA certificate to SLB when configuring the listener.

A self-signed CA certificate is used to sign the client certificate in this tutorial. To add an HTTPS listener with mutual authentication, complete these steps:

1.  [Prepare a server certificate](#section_klf_y5z_vdb)
2.  [Generate a CA certificate using Open SSL](#section_cqz_pvz_vdb)
3.  [Generate a client certificate](#section_jbr_hyz_vdb)
4.  [Upload the server certificate and the CA certificate](#section_mdg_411_wdb)
5.  [Install the client certificate](#section_cts_cd1_wdb)
6.  [Configure an HTTPS listener \(mutual authentication\)](#section_p5w_zd1_wdb)
7.  [Test the SLB service](#section_q3q_r21_wdb)

## Step 1 Prepare a server certificate {#section_klf_y5z_vdb .section}

A server certificate is used by the client browser to check whether the certificate sent by the server is signed and issued by a trusted center. You can purchase a server certificate from Alibaba Cloud Security [Certificate Service](https://www.aliyun.com/product/cas?spm=a2c4g.11186623.2.11.nw2Pcs), or from other service providers.

## Step 2 Generate a CA certificate by using Open SSL {#section_cqz_pvz_vdb .section}

1.  Run the following commands to create a ca folder under the /root directory and then create four sub folders under the ca folder.

    ```
    $ Sudo mkdir ca
     $ cd ca
     $ sudo mkdir newcerts private conf server
    ```

    where:

    -   newcerts is used to store the digit certificate signed by a CA certificate.
    -   private is used to hold the private key of the CA.
    -   conf is used to store the configuration files used for simplifying parameters.
    -   server is used to store the server certificate.
2.  Create an openssl.conf file that contains the following information in the conf directory.

    ```
    [ ca ]
     default_ca = foo
     [ foo ] 
     dir = /root/ca
     database = /root/ca/index.txt
     new_certs_dir = /root/ca/newcerts
     certificate = /root/ca/private/ca.crt
     serial = /root/ca/serial
     private_key = /root/ca/private/ca.key
     RANDFILE = /root/ca/private/.rand
     default_days = 365
     default_crl_days= 30
     default_md = md5
     unique_subject = no
     policy = policy_any
     [ policy_any ]
     countryName = match
     stateOrProvinceName = match
     organizationName = match
     organizationalUnitName = match
     localityName = optional
     commonName = supplied
     Emailaddress = optional
    ```

3.  Run the following command to generate a private key.

    ```
    $ CD/root/CA
     $ sudo openssl genrsa -out private/ca.key
    ```

    The following figure is an example of the key generation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/15396848592750_en-US.png)

4.  Run the following command and input the required information according to the prompts. Press Enter to generate the csr file used to generate the certificate.

    ```
    $ Sudo OpenSSL req-New-key private/CA. Key-out private/CA. CSR
    ```

    **Note:** Common Name is the domain name of the SLB instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/15396848592753_en-US.png)

5.  Run the following command to generate the crt file.

    ```
    $ sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  Run the following command to set the start sequence number for the private key, which can be any four characters.

    ```
    $ sudo echo FACE > serial
    ```

7.  Run the following command to create a CA key library.

    ```
    $ sudo touch index.txt
    ```

8.  Run the following command to create a certificate revocation list for removing the client certificate.

    ```
    $ sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"
    ```

    The response is as follows:

    ```
    Using configuration from /root/ca/conf/openssl.conf
    ```


## Step 3 Generate a client certificate {#section_jbr_hyz_vdb .section}

1.  Run the following command to generate a users directory under the ca directory to store the client certificate.

    ```
    $ Sudo mkdir users
    ```

2.  Run the following command to create a key for the client.

    ```
    $ Sudo OpenSSL FIG/root/CA/users/client. Key 1024
    ```

    **Note:** Enter a pass phrase when creating the key. It is the password to protect the private key from unauthorized access. Enter the same password twice.

3.  Run the following command to create a csr file for requesting certificate sign.

    ```
    $ sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    As prompted, input the pass phrase used in the previous step and provide required information.

    **Note:** A challenge password is the client certificate password \(Separate it from the password of `client.key`. In this tutorial, the password is test\). It can be same as that of the root certificate or server certificate.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/15396848592757_en-US.png)

4.  Run the following command to sign the client key by using the CA key in step 2.

    ```
    $ sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    Enter y twice when prompted to confirm the operation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/15396848592758_en-US.png)

5.  Run the following command to convert the certificate to the PKCS12 file that can be recognized by most browsers.

    ```
    $ sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    Follow the prompts to enter the pass phrase of client. key.

    Then enter the password used for exporting the client certificate. This password is used to protect the client certificate, which is required when installing the client certificate.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/15396848592759_en-US.png)

6.  Run the following command to view the generated client certificate.

    ```
    cd users
     ls
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/15396848592760_en-US.png)


## Step 4 Upload the server certificate and the CA certificate {#section_mdg_411_wdb .section}

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  On the Server Load Balancer page, click **Create SLB Instance**.
3.  Configure the instance and then click **Buy Now**.

    In this tutorial, the instance type is **Internet** and the region is **China \(Hangzhou\)**. For more information, see [Create an SLB instance](intl.en-US/Archives/User Guide (Old Console)/SLB instances/Create an SLB instance.md#).

4.  Go back to the Server Load Balancer page, hover the mouse to the instance name area, click the displayed pencil icon and modify the name of the SLB instance.
5.  In the left-side navigation pane, click the Certificates tab.
6.  Click **Create Certificate**.
7.  On the Create Certificate page, complete the following configurations and click **OK**.
    -   **Regions**: In this tutorial, select **China \(Hangzhou\)**.

        **Note:** The region of the certificate must be the same as that of the Server Load Balancer instance.

    -   **Certificate Type**: Select **Server Certificate**.
    -   **Certificate Content and Private Key**: Copy the content and private key of the server certificate.

        **Note:** Before copying the content, click **Import Sample** to view the valid certificate format and private key format. For more information, see [Certificate formats](intl.en-US/Archives/User Guide (Old Console)/Certificate management/Certificate requirements.md#).

8.  In the left-side navigation pane, click **Certificates**, and then click **Create Certificate** to upload a CA certificate.
9.  On the Create Certificate page, complete the following configurations and click **OK**.
    -   **Regions**: In this tutorial, select **China \(Hangzhou\)**.

        **Note:** The region of the certificate must be the same as that of the Server Load Balancer instance.

    -   **Certificate Type**: Select **CA Certificate**.
    -   **Certificate Content**: Copy the content of the CA certificate.

        **Note:** Before copying the content, click **Import Sample** to view the valid certificate format and private key format. For more information, see [Certificate formats](intl.en-US/Archives/User Guide (Old Console)/Certificate management/Certificate requirements.md#).


## Step 5 Install client certificates {#section_cts_cd1_wdb .section}

Install the generated client certificates. The Windows operating system and IE web browser are used as examples in this tutorial.

1.  Open the Git Bash command line window, run the following command to export the client certificate generated in step 3.

    ```
    scp root@IPaddress:/root/ca/users/client.p12 . /
    ```

    **Note:** IPaddress is the IP of the server where the client certificate is generated.

2.  Import the certificate to the IE web browser:
    1.  Open the IE web browser, click **Settings** \> **Internet Options**.
    2.  Click the **Content** tab, and then click **Certificates** to import the downloaded client certificate. When importing the certificate, enter the password of the PKCS12 file.

## Step 6 Configure an HTTPS listener \(mutual authentication\) {#section_p5w_zd1_wdb .section}

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the **China \(Hangzhou\)** region, click the ID of the created SLB instance or click **Configure Listener**.
3.  Select the Listeners tab and click **Add Listener**.
4.  Under the Protocol and Listener tab, configure the listener.

    -   **Select Listener Protocol**: HTTPS
    -   **Listening Port**: 443
    -   **Scheduling Algorithm**: Round Robin \(RR\)
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/153968486010035_en-US.png)

5.  Click **Next**. Under the SSL Certificates tab, configure the SSL certificate and enable mutual authentication.

    -   **Server Certificate**: Select the uploaded server certificate.
    -   **CA Certificate**: Select the uploaded client certificate.
    ![](images/13813_en-US_source.png)

6.  Click **Next**. On the displayed page, click Default Server Group and then click **Add**. Add ECS instances and set the backend port to 80.
7.  Click **Next** and enable health check.
8.  Click **Next** to view the listener configurations.
9.  Click **Submit**.
10. Click **OK**.

## Step 7 Test the SLB service {#section_q3q_r21_wdb .section}

1.  Go back to the Server Load Balancer page to view the health check status. When the status is **Normal**, the backend servers can receive requests forwarded by SLB listeners.
2.  Enter the public IP address of the Server Load Balancer instance in the web browser, and select Trust when prompted whether to trust the client certificate.
3.  Refresh web page, and then you can find that the requests are evenly distributed to the backend servers.

    ![](images/13780_en-US_source.png)

    ![](images/13781_en-US_source.png)


