## 1. 接口描述

本接口(DescribeVpnConn)用于查询VPN通道列表。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

 

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为DescribeVpnConn。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 否 | string | 私有网络ID，可使用vpcId或unVpcId，建议使用unVpcId，例如：vpc-03vihbk9,可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。 | 
| vpnGwId | 否  | String | 系统分配的VPN网关ID，可使用vpnGwId或unVpnGwId，建议unVpnGwId，例如：vpngw-dystbrkv。可通过<a href="/document/api/215/5108" title="DescribeVpnGw">DescribeVpnGw</a>接口查询。 |
| vpnConnId | 否  | String | 系统分配的VPN通道ID，可使用vpnConnId或unVpnConnId，建议使用unVpnConnId，例如：vpnx-ol6bcqp0。 |  
| vpnConnName | 否  | String | vpn通道名称，支持模糊查询。 |  
| offset | 否 | Int | 初始行的偏移量，默认为0。 |
| limit | 否 | Int | 每页行数，默认为20，最大支持50。 |
| orderField | 否 | String | 按某个字段排序，目前仅支持createTime,vpnConnName排序，默认按createTime排序。 |
| orderDirection | 否 | String | 升序（asc）还是降序（desc），默认：desc。 |


## 3. 输出参数

| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| code| Int | 错误码，0：成功，其他值：失败 |
| message |  String | 错误信息 |
| totalCount |   Int | 返回结果中VPN通道总数量总数量|
| data.n | Array  | 返回的数组 |
| data.n.vpcId | String | 系统分配的私有网络ID，例如：gz_vpc_8849。 |
| data.n.unVpcId | String | 系统分配的新的私有网络ID，建议使用新ID，例如：vpc-0ox8fuhw。 |
| data.n.vpnGwId | Int | 系统分配的vpn网关ID，例如：122。 |
| data.n.unVpnGwId | String | 系统分配的新的vpn网关ID，建议使用新ID，例如：vpngw-nhg87nmg。 |
| data.n.vpnGwAddress | String | vpn网关公网IP，例如：112.2.3.10。 |
| data.n.userGwId | String | 系统分配的对端网关ID，例如：122。 |
| data.n.unUserGwId | String | 系统分配的新的对端网关ID，例如：cgw-e098slul。 |
| data.n.userGwAddress | String | 对端网关公网IP，例如：183.12.0.1。 |
| data.n.vpnConnName | String | 通道名称。 |
| data.n.preSharedKey | String | 预共享密钥，例如：d!@#12d。|
| data.n.sourceCidr | Array | 源网段。 |
| data.n.destinationCidr | Array | 目标网段。 |
| data.n.vpcConnStatus | Int | vpn通道状态， 0:创建中，1:创建出错，2:修改中，3:修改出错，4:删除中，5:删除出错，6:运行正常。|
| data.n.netStatus | String | vpn通道网络状态，available:已连通，unavailable:未连通。|
| data.n.IKESet | Array | IKE配置信息数组。 |
| data.n.IPsecSet | Array | IPsec配置信息数组。 |

IKE配置信息数组内容

| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| IKESet.propoEncryAlgorithm |String | IKE配置，身份认证方法，例如：'3des-cbc'，更多详见产品说明文档。 |
| IKESet.propoAuthenAlgorithm | String | IKE配置，认证算法，例如：'md5'，更多详见产品说明文档。 |
| IKESet.exchangeMode |String | IKE配置，协商模式：例如：'aggressive'，更多详见产品说明文档。 |
| IKESet.localIdentity | String | IKE配置，本端标识类型：例如：'address',，更多详见产品说明文档。 |
| IKESet.remoteIdentity | String | IKE配置，对端标识类型：例如：'address'，更多详见产品说明文档。 |
| IKESet.localAddress | String | IKE配置，本端标识，localAddress默认为vpn网关公网IP，更多详见产品说明文档。 |
| IKESet.remoteAddress | String | IKE配置，对端标识，更多详见产品说明文档。 |
| IKESet.localFqdnName | String | IKE配置，本端标识，更多详见产品说明文档。 |
| IKESet.remoteFqdnName | String | IKE配置，对端标识，更多详见产品说明文档。 |
| IKESet.dhGroupName | String | IKE配置，DH group，指定IKE交换密钥时使用的DH组，例如：'group1'，更多详见产品说明文档。 |
| IKESet.ikeSaLifetimeSeconds | Int | IKE配置，IKE SA Lifetime，单位：秒，设置IKE安全提议的SA生存周期，例如：3600，更多详见产品说明文档。 |

IPsec配置信息数组内容

| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| IPsecSet.encryptAlgorithm | String | IPsec配置，加密算法，例如：'3des-cbc'，更多详见产品说明文档。 |
| IPsecSet.integrityAlgorith | String | IPsec配置，认证算法：例如：'md5'，更多详见产品说明文档。 |
| IPsecSet.encapMode | String | IPsec配置，报文封装模式：例如：'tunnel'，更多详见产品说明文档。 |
| IPsecSet.securityProto | String | IPsec配置，安全协议：例如：'ESP'，更多详见产品说明文档。 |
| IPsecSet.ipsecSaLifetimeSeconds |  Int | IPsec配置，IPsec SA lifetime(s)：单位秒，例如：360，更多详见产品说明文档。 |
| IPsecSet.ipsecSaLifetimeTraffic |  Int | IPsec配置，IPsec SA lifetime(KB)：单位KB，例如：3600，更多详见产品说明文档。 |
| IPsecSet.pfsDhGroup |  String | IPsec配置，PFS：例如：'dh-group1'更多详见产品说明文档。 |


## 4. 错误码表
 以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。

| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的 VPC。VPC 资源不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询VPC。 |
| InvalidVpnGw.NotFound | 无效的 VPN 网关。VPN 网关资源不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/5108" title="DescribeVpnGw">DescribeVpnGw</a>接口查询vpn网关。 |
| InvalidVpnGw.NotFound | 无效的 VPN 通道。VPN 通道资源不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/document/product/215/5113" title="DescribeVpnConn">DescribeVpnConn</a>接口查询vpn通道。 |


## 5. 示例
 
输入
<pre>
  http://vpc.api.qcloud.com/v2/index.php?Action=DescribeVpnConn
  &<<a href="/doc/api/229/6976">公共请求参数</a>>
  &vpcId=vpc-erxok83l

</pre>

输出
```

{
    "code": 0,
    "message": "",
    "totalCount": 3,
    "data": [
        {
            "vpcId": "gz_vpc_76",
            "unVpcId": "vpc-03vihbk9",
            "vpcName": "pan-vpc2",
            "vpcCidrBlock": "10.100.2.0\/24",
            "vpnGwId": 547,
            "unVpnGwId": "vpngw-kfldykuz",
            "vpnGwName": "test-76",
            "vpnGwAddress": "183.60.249.32",
            "vpnConnId": 399,
            "unVpnConnId": "vpnx-ol6bcqp0",
            "vpnConnName": "399_vpnconn",
            "userGwId": 315,
            "unUserGwId": "cgw-e098slul",
            "userGwName": "9101",
            "userGwAddress": "183.60.249.39",
            "vpcConnStatus": 6,
            "preSharedKey": "tencent",
            "remoteSlaIp": "169.254.112.2",
            "sourceCidr": [
                "10.100.2.0\/24"
            ],
            "destinationCidr": [
                "10.100.25.0\/24"
            ],
            "vpnProto": "ip-sec",
            "createTime": "2015-11-06 11:20:39",
            "IKEArr": {
                "propoAuthenAlgorithm": "sha",
                "propoEncryAlgorithm": "des-cbc",
                "exchangeMode": "main",
                "localIdentity": "address",
                "remoteIdentity": "address",
                "localAddress": "183.60.249.32",
                "remoteAddress": "183.60.249.39",
                "localFqdnName": null,
                "remoteFqdnName": null,
                "dhGroupName": "group1",
                "ikeSaLifetimeSeconds": "86400"
            },
            "IPSECArr": {
                "encryptAlgorithm": "aes-cbc-128",
                "integrityAlgorith": "sha1",
                "encapMode": "tunnel",
                "securityProto": "ESP",
                "pfsDhGroup": "null",
                "ipsecSaLifetimeSeconds": "3600",
                "ipsecSaLifetimeTraffic": "1843200"
            }
        },
        {
            "vpcId": "gz_vpc_80",
            "unVpcId": "vpc-fyvpmam9",
            "vpcName": "pan-vpc6",
            "vpcCidrBlock": "10.100.6.0\/24",
            "vpnGwId": 453,
            "unVpnGwId": "vpngw-ncr48l69",
            "vpnGwName": "huasan-8080",
            "vpnGwAddress": "183.60.249.42",
            "vpnConnId": 301,
            "unVpnConnId": "vpnx-85ao9zdy",
            "vpnConnName": "301_vpnconn",
            "userGwId": 245,
            "unUserGwId": "cgw-7ihaps8r",
            "userGwName": "183.60.249.44",
            "userGwAddress": "183.60.249.44",
            "vpcConnStatus": 6,
            "preSharedKey": "tencent",
            "remoteSlaIp": "169.254.112.4",
            "sourceCidr": [
                "10.100.6.0\/24"
            ],
            "destinationCidr": [
                "10.100.2.0\/24"
            ],
            "vpnProto": "ip-sec",
            "createTime": "2015-08-08 16:23:04",
            "IKEArr": {
                "propoAuthenAlgorithm": "sha",
                "propoEncryAlgorithm": "des-cbc",
                "exchangeMode": "main",
                "localIdentity": "address",
                "remoteIdentity": "address",
                "localAddress": "183.60.249.42",
                "remoteAddress": "183.60.249.44",
                "localFqdnName": null,
                "remoteFqdnName": null,
                "dhGroupName": "group1",
                "ikeSaLifetimeSeconds": "86400"
            },
            "IPSECArr": {
                "encryptAlgorithm": "aes-cbc-128",
                "integrityAlgorith": "sha1",
                "encapMode": "tunnel",
                "securityProto": "ESP",
                "pfsDhGroup": "null",
                "ipsecSaLifetimeSeconds": "3600",
                "ipsecSaLifetimeTraffic": "1843200"
            }
        },
        {
            "vpcId": "gz_vpc_80",
            "unVpcId": "vpc-fyvpmam9",
            "vpcName": "pan-vpc6",
            "vpcCidrBlock": "10.100.6.0\/24",
            "vpnGwId": 453,
            "unVpnGwId": "vpngw-ncr48l69",
            "vpnGwName": "huasan-8080",
            "vpnGwAddress": "183.60.249.42",
            "vpnConnId": 292,
            "unVpnConnId": "vpnx-p0j71qf6",
            "vpnConnName": "292_testtest",
            "userGwId": 232,
            "unUserGwId": "cgw-esg61xg5",
            "userGwName": "183.60.249.24",
            "userGwAddress": "183.60.249.24",
            "vpcConnStatus": 6,
            "preSharedKey": "tencent",
            "remoteSlaIp": "169.254.112.3",
            "sourceCidr": [
                "10.100.6.0\/24"
            ],
            "destinationCidr": [
                "10.100.12.0\/24"
            ],
            "vpnProto": "ip-sec",
            "createTime": "2015-08-06 20:29:25",
            "IKESet": {
                "propoAuthenAlgorithm": "md5",
                "propoEncryAlgorithm": "3des-cbc",
                "exchangeMode": "main",
                "localIdentity": "address",
                "remoteIdentity": "fqdn",
                "localAddress": "183.60.249.42",
                "remoteAddress": null,
                "localFqdnName": null,
                "remoteFqdnName": "vpn86",
                "dhGroupName": "group2",
                "ikeSaLifetimeSeconds": "11180"
            },
            "IPsecSet": {
                "encryptAlgorithm": "aes-cbc-192",
                "integrityAlgorith": "md5",
                "encapMode": "tunnel",
                "securityProto": "ESP",
                "pfsDhGroup": "dh-group1",
                "ipsecSaLifetimeSeconds": "500",
                "ipsecSaLifetimeTraffic": "80000"
            }
        }
    ]
}

```

