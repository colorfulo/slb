# 孔婷API概览 {#concept_qyw_x1d_cz .concept}

## 实例API {#section_rpm_m2w_pdb .section}

|API|描述|
|:--|:-|
|[CreateLoadBalancer](intl.zh-CN/API参考/负载均衡实例/CreateLoadBalancer.md#)|创建负载均衡实例。|
|[ModifyLoadBalancerInternetSpec](intl.zh-CN/API参考/负载均衡实例/ModifyLoadBalancerInternetSpec.md#)|修改负载均衡实例的计费方式或规格。|
|[DeleteLoadBalancer](intl.zh-CN/API参考/负载均衡实例/DeleteLoadBalancer.md#)|删除负载均衡实例。|
|[SetLoadBalancerStatus](intl.zh-CN/API参考/负载均衡实例/SetLoadBalancerStatus.md#)|设置负载均衡实例的状态。|
|[SetLoadBalancerName](intl.zh-CN/API参考/负载均衡实例/SetLoadBalancerName.md#)|修改负载均衡实例的名称。|
|[DescribeLoadBalancers](intl.zh-CN/API参考/负载均衡实例/DescribeLoadBalancers.md#)|查询已创建的负载均衡实例。|
|[DescribeLoadBalancerAttribute](intl.zh-CN/API参考/负载均衡实例/DescribeLoadBalancerAttribute.md#)|查询指定负载均衡实例的详细信息。|
|[ModifyLoadBalancerInstanceSpec](intl.zh-CN/API参考/负载均衡实例/ModifyLoadBalancerInstanceSpec.md#)|修改负载均衡实例的规格。|
|[DescribeRegions](intl.zh-CN/API参考/负载均衡实例/DescribeRegions.md#)|查询可用地域。|
|[DescribeZones](intl.zh-CN/API参考/负载均衡实例/DescribeZones.md#)|查询指定地域的可用区信息。|

## 监听API {#section_dc5_gfw_pdb .section}

|API|描述|
|:--|:-|
|**TCP监听**|
|[CreateLoadBalancerTCPListener](intl.zh-CN/API参考/TCP监听/CreateLoadBalancerTCPListener.md#)|创建TCP监听。|
|[SetLoadBalancerTCPListenerAttribute](intl.zh-CN/API参考/TCP监听/SetLoadBalancerTCPListenerAttribute.md#)|修改TPC监听的配置。|
|[DescribeLoadBalancerTCPListenerAttribute](intl.zh-CN/API参考/TCP监听/DescribeLoadBalancerTCPListenerAttribute.md#)|查询TCP监听配置。|
|**UDP监听**|
|[CreateLoadBalancerUDPListener](intl.zh-CN/API参考/UDP监听/CreateLoadBalancerUDPListener.md#)|创建UDP监听。|
|[SetLoadBalancerUDPListenerAttribute](intl.zh-CN/API参考/UDP监听/SetLoadBalancerUDPListenerAttribute.md#)|修改UDP监听的配置。|
|[DescribeLoadBalancerUDPListenerAttribute](intl.zh-CN/API参考/UDP监听/DescribeLoadBalancerUDPListenerAttribute.md#)|查询UDP监听配置。|
|**HTTP监听**|
|[CreateLoadBalancerHTTPListener](intl.zh-CN/API参考/HTTP监听/CreateLoadBalancerHTTPListener.md#)|创建HTTP监听。|
|[SetLoadBalancerHTTPListenerAttribute](intl.zh-CN/API参考/HTTP监听/SetLoadBalancerHTTPListenerAttribute.md#)|修改HTTP监听的配置。|
|[DescribeLoadBalancerHTTPListenerAttribute](intl.zh-CN/API参考/HTTP监听/DescribeLoadBalancerHTTPListenerAttribute.md#)|查询HTTP监听配置。|
|**HTTPS监听**|
|[CreateLoadBalancerHTTPSListener](intl.zh-CN/API参考/HTTPS监听/CreateLoadBalancerHTTPSListener.md#)|创建HTTPS监听。|
|[SetLoadBalancerHTTPSListenerAttribute](intl.zh-CN/API参考/HTTPS监听/SetLoadBalancerHTTPSListenerAttribute.md#)|修改HTTPS监听的配置。|
|[DescribeLoadBalancerHTTPSListenerAttribute](intl.zh-CN/API参考/HTTPS监听/DescribeLoadBalancerHTTPSListenerAttribute.md#)|查询HTTPS监听配置。|
|[StartLoadBalancerListener](intl.zh-CN/API参考/监听/StartLoadBalancerListener.md#)|启动监听。|
|[DeleteLoadBalancerListener](intl.zh-CN/API参考/监听/DeleteLoadBalancerListener.md#)|删除监听。|
|[StopLoadBalancerListener](intl.zh-CN/API参考/监听/StopLoadBalancerListener.md#)|停止监听。|
|**访问控制**|
|[SetListenerAccessControlStatus](intl.zh-CN/API参考/访问控制（旧版）/SetListenerAccessControlStatus.md#)|为指定监听开启或关闭访问控制功能。|
|[DescribeListenerAccessControlAttribute](intl.zh-CN/API参考/访问控制（旧版）/DescribeListenerAccessControlAttribute.md#)|查询监听的访问控制配置。|
|[AddListenerWhiteListItem](intl.zh-CN/API参考/访问控制（旧版）/AddListenerWhiteListItem.md#)|添加监听访问控制白名单。|
|[RemoveListenerWhiteListItem](intl.zh-CN/API参考/访问控制（旧版）/RemoveListenerWhiteListItem.md#)|删除监听白名单中的IP地址。|
|**转发策略**|
|[CreateRules](intl.zh-CN/API参考/转发规则/CreateRules.md#)|为指定的HTTP/HTTPS监听添加转发规则。|
|[DeleteRules](intl.zh-CN/API参考/转发规则/DeleteRules.md#)|删除转发规则。|
|[SetRule](intl.zh-CN/API参考/转发规则/SetRule.md#)|更改转发规则的目标服务器组。|
|[DescribeRules](intl.zh-CN/API参考/转发规则/DescribeRules.md#)|查询指定监听已配置的转发规则。|
|[DescribeRuleAttribute](intl.zh-CN/API参考/转发规则/DescribeRuleAttribute.md#)|查询指定转发规则的配置详情。|
|**域名扩展（Beta）**|
|[CreateDomainExtension](intl.zh-CN/API参考/域名扩展（Beta）/CreateDomainExtension.md#)|创建扩展域名。|
|[SetDomainExtensionAttribute](intl.zh-CN/API参考/域名扩展（Beta）/SetDomainExtensionAttribute.md#)|设置已添加的扩展域名。|
|[DescribeDomainExtensions](intl.zh-CN/API参考/域名扩展（Beta）/DescribeDomainExtensions.md#)|查询已添加的扩展域名。|
|[DeleteDomainExtension](intl.zh-CN/API参考/域名扩展（Beta）/DeleteDomainExtension.md#)|删除已添加的扩展域名。|

## 后端服务器API {#section_vpc_kff_cz .section}

|API|描述|
|:--|:-|
|**默认服务器组**|
|[AddBackendServers](intl.zh-CN/API参考/后端服务器/AddBackendServers.md#)|添加默认服务器。|
|[RemoveBackendServers](intl.zh-CN/API参考/后端服务器/RemoveBackendServers.md#)|移除默认服务器。|
|[SetBackendServers](intl.zh-CN/API参考/后端服务器/SetBackendServers.md#)|设置默认服务器权重。|
|[DescribeHealthStatus](intl.zh-CN/API参考/后端服务器/DescribeHealthStatus.md#)|负载均衡实例的默认服务器进行健康检查，返回默认服务器的健康状况。|
|**虚拟服务器组**|
|[CreateVServerGroup](intl.zh-CN/API参考/后端服务器组/CreateVServerGroup.md#)|创建虚拟服务器组，并添加后端服务器。|
|[SetVServerGroupAttribute](intl.zh-CN/API参考/后端服务器组/SetVServerGroupAttribute.md#)|修改虚拟服务器组的配置。|
|[AddVServerGroupBackendServers](intl.zh-CN/API参考/后端服务器组/AddVServerGroupBackendServers.md#)|为指定的后端服务器组添加后端服务器。|
|[RemoveVServerGroupBackendServers](intl.zh-CN/API参考/后端服务器组/RemoveVServerGroupBackendServers.md#)|从指定的后端服务器组中移除后端服务器。|
|[ModifyVServerGroupBackendServers](intl.zh-CN/API参考/后端服务器组/ModifyVServerGroupBackendServers.md#)|替换服务器组中的后端服务器。|
|[DeleteVServerGroup](intl.zh-CN/API参考/后端服务器组/DeleteVServerGroup.md#)|删除服务器组。|
|[DescribeVServerGroups](intl.zh-CN/API参考/后端服务器组/DescribeVServerGroups.md#)|查询已创建的服务器组。|
|[DescribeVServerGroupAttribute](intl.zh-CN/API参考/后端服务器组/DescribeVServerGroupAttribute.md#)|查询服务器组的详细信息。|
|**主备服务器组**|
|[CreateMasterSlaveServerGroup](intl.zh-CN/API参考/主备服务器组/CreateMasterSlaveServerGroup.md#)|创建主备服务器组。|
|[DeleteMasterSlaveServerGroup](intl.zh-CN/API参考/主备服务器组/DeleteMasterSlaveServerGroup.md#)|删除主备服务器组。|
|[DescribeMasterSlaveServerGroupAttribute](intl.zh-CN/API参考/主备服务器组/DescribeMasterSlaveServerGroupAttribute.md#)|查询指定主备服务器组的详细信息。|
|[DescribeMasterSlaveServerGroups](intl.zh-CN/API参考/主备服务器组/DescribeMasterSlaveServerGroups.md#)|查询已创建的主备服务器组。|

## 访问控制API {#section_evr_pcy_5db .section}

|API|描述|
|:--|:-|
|[CreateAccessControlList](intl.zh-CN/API参考/访问控制/CreateAccessControlList.md#)|创建访问控制策略组。|
|[DeleteAccessControlList](intl.zh-CN/API参考/访问控制/DeleteAccessControlList.md#)|删除访问控制策略组。|
|[DescribeAccessControlLists](intl.zh-CN/API参考/访问控制/DescribeAccessControlLists.md#)|查询已创建的访问控制策略组。|
|[DescribeAccessControlListAttribute](intl.zh-CN/API参考/访问控制/DescribeAccessControlListAttribute.md#)|查询访问控制策略组的配置。|
|[SetAccessControlListAttribute](intl.zh-CN/API参考/访问控制/SetAccessControlListAttribute.md#)|修改访问控制策略组的名称。|
|[AddAccessControlListEntry](intl.zh-CN/API参考/访问控制/AddAccessControlListEntry.md#)|在访问控制策略组中添加IP条目。|
|[RemoveAccessControlListEntry](intl.zh-CN/API参考/访问控制/RemoveAccessControlListEntry.md#)|删除访问控制策略组中的IP条目。|

## 标签API {#section_w4z_lff_cz .section}

|API|描述|
|:--|:-|
|[AddTags](intl.zh-CN/API参考/标签/AddTags.md#)|为指定的负载均衡实例添加标签。|
|[DescribeTags](intl.zh-CN/API参考/标签/DescribeTags.md#)|查询已创建的标签。|
|[RemoveTags](intl.zh-CN/API参考/标签/RemoveTags.md#)|解绑负载均衡实例的标签。|

## 服务器证书API {#section_wpm_bvp_y2b .section}

|API|描述|
|---|--|
|[UploadServerCertificate](intl.zh-CN/API参考/服务器证书/UploadServerCertificate.md#)|上传服务器证书。|
|[DeleteServerCertificate](intl.zh-CN/API参考/服务器证书/DeleteServerCertificate.md#)|删除服务器证书。|
|[DescribeServerCertificates](intl.zh-CN/API参考/服务器证书/DescribeServerCertificates.md#)|查询已上传的服务器证书。|
|[SetServerCertificateName](intl.zh-CN/API参考/服务器证书/SetServerCertificateName.md#)|设置服务器证书名称。|
|[UploadCACertificate](intl.zh-CN/API参考/服务器证书/UploadCACertificate.md#)|上传CA证书。|
|[DeleteCACertificate](intl.zh-CN/API参考/服务器证书/DeleteCACertificate.md#)|删除CA证书。|
|[DescribeCACertificates](intl.zh-CN/API参考/服务器证书/DescribeCACertificates.md#)|查询已上传的CA证书。|
|[SetCACertificateName](intl.zh-CN/API参考/服务器证书/SetCACertificateName.md#)|设置CA证书名称。|

## 日志API {#section_f4r_grj_s2b .section}

|API|描述|
|---|--|
|**访问日志**|
|[SetAccessLogsDownloadAttribute](intl.zh-CN/API参考/访问日志/SetAccessLogsDownloadAttribute.md#)|添加访问日志转发规则。|
|[DeleteAccessLogsDownloadAttribute](intl.zh-CN/API参考/访问日志/DeleteAccessLogsDownloadAttribute.md#)|删除访问日志转发规则。|
|[DescribeAccessLogsDownloadAttribute](intl.zh-CN/API参考/访问日志/DescribeAccessLogsDownloadAttribute.md#)|查询访问日志转发规则。|
|**健康检查日志**|
|[SetLogsDownloadAttribute](intl.zh-CN/API参考/健康检查日志/SetLogsDownloadAttribute.md#)|设置日志健康检查功能。|
|[DescribeLogsDownloadAttribute](intl.zh-CN/API参考/健康检查日志/DescribeLogsDownloadAttribute.md#)|查询日志健康检查功能。|
|[DeleteLogsDownloadAttribute](intl.zh-CN/API参考/健康检查日志/DeleteLogsDownloadAttribute.md#)|删除日志健康检查功能。|
|[SetLogsDownloadStatus](intl.zh-CN/API参考/健康检查日志/SetLogsDownloadStatus.md#)|设置日志健康检查状态开关。|
|[DescribeLogsDownloadStatus](intl.zh-CN/API参考/健康检查日志/DescribeLogsDownloadStatus.md#)|查询日志健康检查状态开关。|
|[DescribeRealtimeLogs](intl.zh-CN/API参考/健康检查日志/DescribeRealtimeLogs.md#)|查询健康检查日志。|

## 查询资源约束API {#section_vws_rvp_y2b .section}

|API|描述|
|---|--|
|[DescribeSlbQuotas](intl.zh-CN/API参考/查询配额/DescribeSlbQuotas.md#)|查询负载均衡实例的资源约束。|

