# RAM authentication {#concept_slb_rjf_cz .concept}

Before calling SLB APIs using a RAM user, the primary account must grant the RAM user the corresponding permission by creating an authentication policy. In the authentication policy, an Alibaba Cloud Resource Name \(ARN\) is used as the unique identifier of the resource to authorize.

## SLB resources {#section_vj2_fyf_cz .section}

The following table lists the SLB resources that can be authorized and the ARN format.

|Resource|ARN format|
|--------|----------|
|LoadBalancer|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:slb:$regionid:$accountid:loadbalancer/\*|
|acs:slb:\*:$accountid:loadbalancer/\*|
|acs:slb:\*:\*:loadbalancer/\*|
|Certificate|acs:slb:$regionid:$accountid:certificate/$servercertificateId|
|acs:slb:$regionid:$accountid:certificate/\*|
|ACL|acs:slb:$regionid:$accountid:acl/\*|
|acs:slb:$regionid:$accountid:acl/$aclid|

`$regionid/accoutid/servercertificateId` is the specific resource ID, and `*` represents all corresponding resources.

## SLB APIs {#section_ytz_qyf_cz .section}

The following table lists the VPC actions that can be authorized and the ARN format.

|API |ARN format|
|----|----------|
|CreateLoadBalancer|acs:slb:$regionid:$accountid:loadbalancer/\*|
|ModifyLoadBalancerInternetSpec|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DeleteLoadBalancer|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerStatus|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerName|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancers|acs:slb:$regionid:$accountid:loadbalancer/\*|
|DescribeLoadBalancerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeRegions|acs:slb:\*:$accountid:\*|
|UploadServerCertificate|acs:slb:%s:%s:certificate/\*|
|DeleteServerCertificate|acs:slb:%s:%s:certificate/%|
|DescribeServerCertificate|acs:slb:%s:%s:certificate/%|
|SetServerCertificateName|acs:slb:%s:%s:certificate/%|
|DescribeServerCertificates|acs:slb:%s:%s:certificate/\*|
|CreateLoadBalancerHTTPListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|CreateLoadBalancerHTTPSListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:slb:%s:%s:certificate/%|
|CreateLoadBalancerTCPListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|CreateLoadBalancerUDPListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|Deleteloadbalancerlistener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|StartLoadBalancerListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|StopLoadBalancerListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerHTTPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerHTTPSListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:slb:%s:%s:certificate/%|
|SetLoadBalancerTCPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerUDPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerHTTPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerHTTPSListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerTCPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerUDPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|AddBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|RemoveBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|SetBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|DescribeHealthStatus|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|CreateVServerGroup|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|SetVServerGroupAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DeleteVServerGroup|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeVServerGroups|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeVServerGroupAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|AddVServerGroupBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|RemoveVServerGroupBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|ModifyVServerGroupBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|CreateAccessControlList|acs:slb:$regionid:$accountid:acl/\*|
|DeleteAccessControlList|acs:slb:$regionid:$accountid:acl/$aclid|
|DescribeAccessControlLists|acs:slb:$regionid:$accountid:acl/$aclid|
|DescribeAccessControlListAttribute|acs:slb:$regionid:$accountid:acl/$aclid|
|SetAccessControlListAttribute|acs:slb:$regionid:$accountid:acl/$aclid|
|AddAccessControlListEntry|acs:slb:$regionid:$accountid:acl/$aclid|
|RemoveAccessControlListEntry|acs:slb:$regionid:$accountid:acl/$aclid|

