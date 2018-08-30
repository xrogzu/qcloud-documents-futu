## 1. VPC相关接口

| 接口功能 | Action ID | 功能描述 |
|---------|---------|---------|
| 创建私有网络 | [CreateVpc](/doc/api/245/%E5%88%9B%E5%BB%BA%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C) | 创建私有网络，规划好您的网段。 |
| 删除私有网络 | [DeleteVpc](/doc/api/245/%E5%88%A0%E9%99%A4%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C) | 删除某个私有网络。 |
| 修改私有网络名称 | [ModifyVpcAttribute](/doc/api/245/%E4%BF%AE%E6%94%B9%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%90%8D%E7%A7%B0) | 修改指定vpc的名称。 |
| 查询私有网络列表 | [DescribeVpcEx](/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8) | 批量查询vpc信息，支持分页查询、模糊匹配等。|
| 绑定私有网络内主机与VIP | [AssociateVip](/doc/api/245/%E7%BB%91%E5%AE%9A%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%86%85%E4%B8%BB%E6%9C%BA%E4%B8%8EVIP) | 给vpc内云主机绑定一个VIP。 |

## 2. 子网相关接口
| 接口功能 | Action ID | 功能描述 | 
|---------|---------|---------|
| 创建子网 | [CreateSubnet](/doc/api/245/%E5%88%9B%E5%BB%BA%E5%AD%90%E7%BD%91) |  创建子网，并指定可用区。 |
| 删除子网 | [DeleteSubnet](/doc/api/245/%E5%88%A0%E9%99%A4%E5%AD%90%E7%BD%91) | 删除指定子网。 |
| 修改子网名称 | [ModifySubnetAttribute](/document/api/215/1313) | 修改指定子网名称。 |
| 查询子网列表 | [DescribeSubnetEx](/doc/api/245/%E6%9F%A5%E8%AF%A2%E5%AD%90%E7%BD%91%E5%88%97%E8%A1%A8) | 批量查询子网信息，支持分页查询、模糊匹配等。|
| 查询子网详情 | [DescribeSubnet](/doc/api/245/%E6%9F%A5%E8%AF%A2%E5%AD%90%E7%BD%91%E8%AF%A6%E6%83%85) | 根据用户输入信息，如subnetId、子网名称等，查询对应子网的详细信息。|


## 3. 路由表相关接口
| 接口功能 | Action ID | 功能描述 |
|---------|---------|---------|
| 创建路由表 | [CreateRouteTable](/doc/api/245/%E5%88%9B%E5%BB%BA%E8%B7%AF%E7%94%B1%E8%A1%A8) | 创建一个路由表。 |
| 删除路由表 | [DeleteRouteTable](/doc/api/245/%E5%88%A0%E9%99%A4%E8%B7%AF%E7%94%B1%E8%A1%A8) | 删除指定路由表，删除后该路由表内路由策略都失效。 |
| 修改路由表 | [ModifyRouteTableAttribute](/doc/api/245/%E4%BF%AE%E6%94%B9%E8%B7%AF%E7%94%B1%E8%A1%A8) | 修改指定路由表名称。 |
| 查询路由表 | [DescribeRouteTable](/doc/api/245/%E6%9F%A5%E8%AF%A2%E8%B7%AF%E7%94%B1%E8%A1%A8) | 根据用户输入信息，如routeTableId、路由表名称等，查询对应路由表的详细信息。|
| 修改子网关联的路由表 | [AssociateRouteTable](/document/api/215/1416) | 修改子网关联的路由表。 |
| 添加路由策略 | [CreateRoute](/doc/api/245/5688) | 新增路由策略。 |
| 删除路由策略 | [DeleteRoute](/doc/api/245/5689) | 删除路由策略。 |


## 4. 网络ACL相关接口
| 接口功能 | Action ID | 功能描述 |
|---------|---------|---------|
| 创建VPC网络ACL | [CreateNetworkAcl](/doc/api/245/%E5%88%9B%E5%BB%BAVPC%E7%BD%91%E7%BB%9CACL) | 创建安全防火墙。 |
| 删除网络ACL | [DeleteNetworkAcl](/doc/api/245/%E5%88%A0%E9%99%A4%E7%BD%91%E7%BB%9CACL) | 删除指定安全防火墙。 |
| 修改网络ACL名称 | [ModifyNetworkAcl](/doc/api/245/%E4%BF%AE%E6%94%B9%E7%BD%91%E7%BB%9CACL%E5%90%8D%E7%A7%B0) | 修改安全防火墙名称。 |
| 查询网络ACL列表 | [DescribeNetworkAcl](/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%BD%91%E7%BB%9CACL%E5%88%97%E8%A1%A8) | 查询vpc安全防火墙列表。 |
| 设置网络ACL规则 | [ModifyNetworkAclEntry](/doc/api/245/%E8%AE%BE%E7%BD%AE%E7%BD%91%E7%BB%9CACL%E8%A7%84%E5%88%99) | 设置安全防火墙网络规则。 |
| 网络ACL绑定子网 | [CreateSubnetAclRule](/doc/api/245/%E7%BD%91%E7%BB%9CACL%E7%BB%91%E5%AE%9A%E5%AD%90%E7%BD%91) | 安全防火墙绑定子网。 |
| 网络ACL解绑子网 | [DeteleSubnetAclRule](/doc/api/245/%E7%BD%91%E7%BB%9CACL%E8%A7%A3%E7%BB%91%E5%AD%90%E7%BD%91) | 安全防火墙和子网解绑。 |


## 5. 对端网关相关接口
| 接口功能 | Action ID |  功能描述 |
|---------|---------|---------|
| 创建对端网关 | [AddUserGw](/doc/api/245/5116) | 创建要连接的对端网关。 |
| 删除对端网关 | [DeleteUserGw](/doc/api/245/5117) | 删除指定对端网关。 |
| 修改对端网关名称 | [ModifyUserGw](/doc/api/245/5118) | 修改对端网关名称。 |
| 查询对端网关列表 | [DescribeUserGw](/doc/api/245/5119) | 根据用户信息，如对端网关ID，名称，查询对应对端网关的信息。|



## 6. 对等连接
| 接口功能 | Action ID |  功能描述 |
|---------|---------|---------|
| 创建同地域对等连接 | [CreateVpcPeeringConnection](/doc/api/245/2107) | 创建同地域对等连接。 |
| 删除同地域对等连接 | [DeleteVpcPeeringConnection](/doc/api/245/2104) | 删除同地域对等连接。 |
| 修改同地域对等连接属性 | [ModifyVpcPeeringConnection](/doc/api/245/2103) | 修改同地域对等连接属性。 |
| 接受同地域对等连接 | [AcceptVpcPeeringConnection](/doc/api/245/2106) | 接受同地域对等连接。 |
| 驳回同地域对等连接 | [RejectVpcPeeringConnection](/doc/api/245/2105) | 驳回同地域对等连接。 |
| 启用同地域过期对等连接 | [EnableVpcPeeringConnection](/doc/api/245/2102) | 启用同地域过期对等连接。 |
| 创建跨地域对等连接 | [CreateVpcPeeringConnectionEx](/doc/api/245/4803) | 创建跨地域对等连接。 |
| 删除跨地域对等连接 | [DeleteVpcPeeringConnectionEx](/doc/api/245/4804) | 删除跨地域对等连接。 |
| 修改跨地域对等连接属性 | [ModifyVpcPeeringConnectionEx](/doc/api/245/4805) | 修改跨地域对等连接属性。 |
| 接受跨地域对等连接 | [AcceptVpcPeeringConnectionEx](/doc/api/245/4806) | 接受跨地域对等连接。 |
| 驳回跨地域对等连接 | [RejectVpcPeeringConnectionEx](/doc/api/245/4807) | 驳回跨地域对等连接。 |
| 启用跨地域过期对等连接 | [EnableVpcPeeringConnectionEx](/doc/api/245/4808) | 启用跨地域过期对等连接。 |
| 查询对等连接 | [DescribeVpcPeeringConnections](/doc/api/245/2101) | 查询对等连接。 |

## 7. 专线网关相关接口
| 接口功能 | Action ID |  功能描述 |
|---------|---------|---------|
| 创建专线网关 | [CreateDirectConnectGateway](/doc/api/245/4824) | 创建专线网关。 |
| 修改专线网关属性 | [ModifyDirectConnectGateway](/doc/api/245/4826) | 修改专线网关属性。|
| 删除专线网关 | [DeleteDirectConnectGateway](/doc/api/245/4825) | 删除专线网关。 |
| 查询专线网关 | [DescribeDirectConnectGateway](/doc/api/245/4827) | 查询专线网关。 |
| 添加专线网关本端IP转换 | [CreateLocalIPTranslationNatRule](/doc/api/245/5185) | 添加专线网关本端IP转换。 |
| 删除专线网关本端IP转换 | [DeleteLocalIPTranslationNatRule](/doc/api/245/5186) | 删除专线网关本端IP转换。 |
| 修改专线网关本端IP转换 | [ModifyLocalIPTranslationNatRule](/doc/api/245/5187) | 修改专线网关本端IP转换。 |
| 查询专线网关本端IP转换 | [DescribeLocalIPTranslationNatRule](/doc/api/245/5188) | 查询专线网关本端IP转换。 |
| 添加专线网关本端源IP端口转换 | [CreateLocalSourceIPPortTranslationNatRule](/document/api/215/5190) | 添加专线网关本端源IP端口转换。 |
| 删除专线网关本端源IP端口转换 | [DeleteLocalSourceIPPortTranslationNatRule](/document/api/215/5191) | 删除专线网关本端源IP端口转换。 |
| 修改专线网关本端源IP端口转换 | [ModifyLocalSourceIPPortTranslationNatRule](/document/api/215/5192) | 修改专线网关本端源IP端口转换。 |
| 查询专线网关本端源IP端口转换 | [DescribeLocalSourceIPPortTranslationNatRule](/document/api/215/5193) | 查询专线网关本端源IP端口转换。 |
| 添加专线网关本端目的IP端口转换 | [CreateLocalDestinationIPPortTranslationNatRule](/document/api/215/5195) | 添加专线网关本端目的IP端口转换。 |
| 删除专线网关本端目的IP端口转换 | [DeleteLocalDestinationIPPortTranslationNatRule](/document/product/215/5196) | 删除专线网关本端目的IP端口转换。 |
| 修改专线网关本端目的IP端口转换 | [ModifyLocalDestinationIPPortTranslationNatRule](/document/api/215/5197) | 修改专线网关本端目的IP端口转换。 |
| 查询专线网关本端目的IP端口转换 | [DescribeLocalDestinationIPPortTranslationNatRule](/document/api/215/5198) | 查询专线网关本端目的IP端口转换。 |
| 添加专线网关对端IP转换 | [CreatePeerIPTranslationNatRule](/document/api/215/5201) | 添加专线网关对端IP转换。 |
| 删除专线网关对端IP转换 | [DeletePeerIPTranslationNatRule](/document/api/215/5202) | 删除专线网关对端IP转换。 |
| 修改专线网关对端IP转换 | [ModifyPeerIPTranslationNatRule](/document/api/215/5203) | 修改专线网关对端IP转换。 |
| 查询专线网关对端IP转换 | [DescribePeerIPTranslationNatRule](/document/api/215/5204) | 查询专线网关对端IP转换。 |
| 添加本端IP转换 acl策略 | [CreateLocalIPTranslationAclRule](/doc/api/245/5205) | 添加本端IP转换 acl策略。 |
| 删除本端IP转换 acl策略 | [DeleteLocalIPTranslationAclRule](/doc/api/245/5206) | 删除本端IP转换 acl策略。 |
| 修改本端IP转换 acl策略 | [ModifyLocalIPTranslationAclRule](/doc/api/245/5207) | 修改本端IP转换 acl策略。 |
| 查询本端IP转换 acl策略 | [DescribeLocalIPTranslationAclRule](/doc/api/245/5208) | 查询本端IP转换 acl策略。 |
| 添加本端IP端口转换 acl策略 | [CreateLocalSourceIPPortTranslationAclRule](/doc/api/245/5211) | 添加本端IP端口转换 acl策略。 |
| 删除本端IP端口转换 acl策略 | [DeleteLocalSourceIPPortTranslationAclRule](/doc/api/245/5212) | 删除本端IP端口转换 acl策略。 |
| 修改本端IP端口转换 acl策略 | [ModifyLocalSourceIPPortTranslationAclRule](/doc/api/245/5213) | 修改本端IP端口转换 acl策略。 |
| 查询本端IP端口转换 acl策略 | [DescribeLocalSourceIPPortTranslationAclRule](/doc/api/245/5214) | 查询本端IP端口转换 acl策略。 |

## 8. NAT网关相关接口
| 接口功能 | Action ID |  功能描述 |
|---------|---------|---------|
| 创建NAT网关 | [CreateNatGateway](/doc/api/245/4094) |  创建NAT网关。 |
| 查询NAT网关创建状态 | [QueryNatGatewayProductionStatus](/doc/api/245/4089) |  查询NAT网关创建状态。 |
| 删除NAT网关 | [DeleteNatGateway](/doc/api/245/4087) | 删除NAT网关。 |
| 修改NAT网关 | [ModifyNatGateway](/doc/api/245/4086) | 修改NAT网关。 |
| 查询NAT网关 | [DescribeNatGateway](/doc/api/245/4088) | 查询NAT网关。 |
| NAT网关绑定EIP | [EipBindNatGateway](/doc/api/245/4093) | NAT网关绑定EIP。 |
| NAT网关解绑EIP | [EipUnBindNatGateway](/doc/api/245/4092) | NAT网关解绑EIP。 |
| 升级NAT网关规格 | [UpgradeNatGateway](/doc/api/245/4090) | 升级NAT网关规格。 |

## 9. 弹性网卡相关接口
| 接口功能 | Action ID |  功能描述 |
|---------|---------|---------|
| 创建弹性网卡 | [CreateNetworkInterface](/doc/api/245/4811) |  创建弹性网卡。 |
| 删除弹性网卡 | [DeleteNetworkInterface](/doc/api/245/4813) |  删除弹性网卡。 |
| 查询弹性网卡信息 | [DescribeNetworkInterfaces](/doc/api/245/4814) | 查询弹性网卡信息。 |
| 弹性网卡申请内网Ip | [AssignPrivateIpAddresses](/doc/api/245/4817) | 弹性网卡申请内网Ip。 |
| 弹性网卡退还内网Ip | [UnassignPrivateIpAddresses](/doc/api/245/4819) | 弹性网卡退还内网Ip。 |
| 弹性网卡绑定云主机 | [AttachNetworkInterface](/doc/api/245/4820) | 弹性网卡绑定云主机。 |
| 弹性网卡解绑云主机 | [DetachNetworkInterface](/document/product/215/4822) | 弹性网卡解绑云主机。 |
| 弹性网卡迁移 | [MigrateNetworkInterface](/doc/api/245/5384) | 弹性网卡迁移。 |
| 内网IP迁移 | [MigratePrivateIpAddress](/doc/api/245/5385) | 内网IP迁移。 |



