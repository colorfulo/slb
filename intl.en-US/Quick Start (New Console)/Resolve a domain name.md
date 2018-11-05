# Resolve a domain name {#task_bh5_dll_vdb .task}

You can resolve a domain name to the public address of an SLB instance.

For example, the domain name of your website is www.abc.com and the website is running on an ECS instance with the public IP 1.1.1.1. After creating a Server Load Balancer instance, a public IP 2.2.2.2 is allocated to the instance. You have to add the ECS instance hosting the website to the backend server pool and resolve the domain name www.abc.com to 2.2.2.2. We recommend that you add an A record resolution \(resolve a domain name to an IP address\).

1.  Log on to the Alibaba Cloud DNS console. 
2.   Click **Add Domain Name** to add a domain name. 
3.   On the Basic DNS page, click **Configure** in the **Actions** column of the target domain name, and complete the DNS configuration. 

