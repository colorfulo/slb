# Manage a VServer group {#concept_ewt_whp_42b .concept}

A virtual server group \(VServer group\) is a group of ECS instances. If you associate a VServer group with a listener, the listener distributes requests to the associated VServer group instead of other backend servers.

If you add default backend servers, VServer groups and forwarding rules to the same Layer-7 listener, the sequence of request forwarding is as follows:

-   If the requests match a forwarding rule, the requests are distributed to the VServer group associated with the rule.
-   If not, the requests are distributed to the VServer group associated with the listener.
-   If no VServer group is configured on the listener, the requests are forwarded to ECS instances in the default server group.

## Create a VServer group {#section_jqy_c3p_42b .section}

Before creating a VServer group, make sure the following conditions are met:

-   You have [created an SLB instance](intl.en-US/User Guide/SLB instances/Create an SLB instance.md#).
-   You have created ECS instances and deploy applications to process distributed requests. 

Note the following when creating a VServer group:

-   The ECS instances added to the VServer group and the SLB instance must be located in the same region.
-   One ECS instance can be added to multiple VServer groups.
-   One VServer group can be associated with multiple listeners.
-   A VServer group consists of ECS instances and application ports.

To add ECS instances, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the VServer Groups tab.
5.  On the VServer Group page, click **Create VServer Group**.
6.  On the Create VServer Group page, complete these steps:
    1.  In the **VServer Group Name** text box, enter the name of the VServer group.
    2.  Click **Add** to select the server to add in the Available Servers list.
    3.  Click **Add to Selected Server List** and click **OK**.
    4.  Under the **Servers Added** tab, complete the following configuration and click **OK**.

        -   **Port**: The backend port opened on the ECS instance to receive requests.

            The backend ports in a Server Load Balancer instance can be the same.

        -   **Weight**: An ECS instance with a higher weight receivers more requests.

            **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15368930827368_en-US.png)

        You can modify the ports and weights of added servers in batches.

        -   Click ![](images/11116_en-US.png): Duplicate to below. If you modify the port or weight of the current server, the ports or weights of all servers blow are also changed.
        -   Click ![](images/11119_en-US.png): Duplicate to above. If you modify the port or weight of the current server, the ports or weights of all servers above are also changed.
        -   Click ![](images/11120_en-US.png): Duplicate to all. If you modify the port or weight of the current server, the ports or weights of all servers in the VServer group are also changed.
        -   Click ![](images/11121_en-US.png): Clear all. If you clear the port or weight of the current server, the ports or weights of all servers in the VServer group are also cleared.
        ![](images/11115_en-US.png)


## Edit a VServer group {#section_iwj_tjp_42b .section}

To modify the ECS instance configuration in a VServer group, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the VServer Groups tab.
5.  Find the target VServer group, and then click the **Edit** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15368930827473_en-US.png)

6.  Modify the port and weight of the ECS instance or click **Delete** to remove the ECS instance from the VServer group, and then click **OK**.

## Delete a VServer group {#section_upw_1np_42b .section}

To delete a VServer group, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the VServer Groups tab.
5.  Find the target VServer group, and then click the **Delete** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15368930827474_en-US.png)

6.  In the displayed dialog box, click **OK**.

