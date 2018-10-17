# Create certificate {#concept_ekm_gj1_dfb .concept}

To configure an HTTPS listener, you can directly use a certificate in SSL Certificate Service or upload the required third-party server certificate and CA certificate to the SLB. Then you no longer need to configure certificates on the backend servers.

SLB supports certificates from the following two resources:

-   Certificates issued or hosted by Alibaba Cloud SSL Certificate Service: You can select the certificate from Alibaba Cloud SSL Certificate Service. You will receive alerts when the certificate is about to expire, and can renew the certificate easily.

    Currently client CA certificates are not supported.

-   Third-party certificates: To upload a third-party certificate, you must have the public key/private key files of the certificate.

    HTTPS server certificates and client CA certificates are supported.


Note the following before creating a certificate:

-   If you want to use a certificate in multiple regions, you must select multiple regions when creating the certificate.
-   You can create up to 100 certificates per account.

## Select Certificate From SSL Certificate Service {#section_i3q_gm1_dfb .section}

Alibaba Cloud SSL Certificate Service issues digital certificates of different brands to provide HTTPS services for websites, so that the websites are trustworthy and are prevented from hijacking, tampering and interception. It also uniformly manages the life cycles of certificates to simplify certificate deployment. For more information, see [SSL certificate service](https://www.aliyun.com/product/cas?spm=5176.8142029.security.5.3dbd6d3ezWmWrn).

To use certificates in SSL Certificate Service, you must log on to the [SSL Certificate console](https://yundun.console.aliyun.com/?spm=5176.2020520001.106.d20cas.3c474bd31n23aP&p=cas#/cas/home) to buy a certificate or upload a third-party certificate to the SSL Certificate Service.

To select a certificate from SSL Certificate Service, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  In the left-side navigation pane, click **Certificates**.
3.  Click **Create Certificate**. On the Create Certificate page, select **Select Certificate From SSL Certificate Service** .

    ![](images/11881_en-US.png)

4.  Click **Next**. On the Select Certificate From SSL Certificate Service page, select the region to deploy the certificate and then select the SSL certificate to use from the certificate list.

    A certificate cannot be used across regions. If a certificate is to be used in multiple regions, select all these regions.

5.  Click **OK**.

## Upload a third-party certificate {#section_q2y_kj1_dfb .section}

Before uploading a third-party certificate, make sure the following conditions are met:

-   You have purchased a server certificate.
-   You have generated a CA certificate and a client certificate. For more information, see [Generate a CA certificate](intl.en-US/User Guide/Certificate management/Generate a CA certificate.md#).

To upload a third-party certificate to the SLB instance, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  In the left-side navigation pane, click **Certificates**.
3.  Click **Create Certificate**.
4.  On the Create Certificate page, click **Upload Third-party Certificate**.

    ![](images/11880_en-US.png)

5.  Click **Next**. On the Upload Third-Party Certificate page, upload the certificate content.

    |Configuration|Description |
    |:------------|:-----------|
    |**Certificate name**| Enter a certificate name.

 The name must be 1-80 characters long, and can only contain letters, numbers and the following special characters:

 \_/. -

 |
    |**Regions**| Select one or more regions where the certificate is uploaded.

 A certificate cannot be used across regions. If a certificate is to be used in multiple regions, select all these regions.

 |
    |**Certificate Type**|Select the type of the certificate to be uploaded:    -   **Server Certificate**: For HTTPS one-way authentication, only the server certificate and the private key are required.
    -   **CA Certificate**: For HTTPS mutual authentication, both the server certificate and the CA certificate are required.
|
    |**Certificate Content**| Paste the certificate content in the editor.

 Click **View Sample Certificate** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

 |
    |**Private Key**|Paste the private key of the server certificate in the editor.Click **View Sample Certificate** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

**Note:** A private key is only required when uploading a server certificate.

|

6.  Click **OK**.

