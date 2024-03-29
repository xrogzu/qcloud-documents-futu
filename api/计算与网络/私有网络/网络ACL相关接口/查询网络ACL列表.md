## 1. 接口描述

本接口（DescribeNetworkAcl）用于查询网络ACL列表。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>
 

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为DescribeNetworkAcl。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 否 | String | 子网所属的私有网络ID值，可使用vpcId或unVpcId，建议使用unVpcId，例如：vpc-0ox8fuhw。可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。 |
| networkAclId | 否 | String | 系统分配的网络ACL ID，例如：acl-0ox8fuhw。可通过<a href="/doc/api/245/1441" title="DescribeNetworkAcl">DescribeNetworkAcl</a>接口查询。 |
| offset | 否 | Int | 初始行的偏移量，默认为0。 |
| limit | 否 | Int | 每页行数，默认为20，最大支持50。 |
| orderField | 否 | String | 按某个字段排序，目前仅支持createTime,networkAclName排序，默认按createTime排序。 |
| orderDirection | 否 | String | 升序（asc）还是降序（desc），默认：desc。 |


## 3. 输出参数

| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| code| Int | 错误码，0: 成功，其他值: 失败。 |
| message | String | 错误信息。 |
| totalCount |  Int | 返回结果中网络ACL总数量。 |
| data.n | array  | 返回的数组。 |
| data.n.vpcId | String | 系统分配的私有网络ID，例如：gz_vpc_8849。 |
| data.n.unVpcId | String | 系统分配的新的私有网络ID，建议使用新ID，例如：vpc-0ox8fuhw。 |
| data.n.networkAclId | String | 系统分配的网络ACL ID，例如：acl-e9dbyl8s。 |
| data.n.networkAclName | String | 网络名称。 |
| data.n.subnetNum | Int | 绑定子网数量。 |
| data.n.createTime | String | 网络ACL创建时间，例如：2015-11-06 20:55:12。 |
| data.n.networkAclEntrySet | Array | 网络ACL策略信息数组。 |


**networkAclEntrySet 网络ACL策略数组结构：**

| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| networkAclEntrySet.ingress.n | Array | 网络ACL入站规则。 |
| networkAclEntrySet.ingress.n.desc | String | 备注。 |
| networkAclEntrySet.ingress.n.ipProtocol | String | 协议，例如tcp。 |
| networkAclEntrySet.ingress.n.cidrIp | String | 源IP或者源网段，支持IP或者CIDR，例如：10.20.3.0或者10.0.0.2/24。 |
| networkAclEntrySet.ingress.n.portRange | String | 源端口，支持单个接口或者端口段，例如：80或者90-100。 |
| networkAclEntrySet.ingress.n.action | Int | 策略，1:允许，0:拒绝。 |
| networkAclEntrySet.egress.n | Array | 网络ACL出站规则。 |
| networkAclEntrySet.egress.n.desc | String | 备注。 |
| networkAclEntrySet.egress.n.ipProtocol | String | 协议，例如tcp。 |
| networkAclEntrySet.egress.n.cidrIp | String | 源IP或者源网段，支持IP或者CIDR，例如：10.20.3.0或者10.0.0.2/24。 |
| networkAclEntrySet.egress.n.portRange | String | 源端口，支持单个接口或者端口段，例如：80或者90-100。 |
| networkAclEntrySet.egress.n.action | Int | 策略，1:允许，0:拒绝。 |

## 4. 错误码表
  以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的 VPC。VPC 资源不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询VPC 。|
| InvalidNetworkAclID.NotFound | 无效的网络 ACL ID。网络 ACL ID不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/doc/api/245/1441" title="DescribeNetworkAcl">DescribeNetworkAcl</a>接口查询。 |

## 5. 示例
 
输入
<pre>
  http://vpc.api.qcloud.com/v2/index.php?Action=DescribeNetworkAcl
  &<<a href="/doc/api/229/6976">公共请求参数</a>>
  &vpcId=vpc-erxok83l
  &networkAclId=acl-jk7weyp2

</pre>

输出
```

{
    "code": 0,
    "message": "",
    "totalCount": 3,
    "data": [
        {
            "vpcId": "gz_vpc_231",
            "unVpcId": "vpc-erxok83l",
            "networkAclName": "tttssass",
            "networkAclId": "acl-e9dbyl8s",
            "vpcName": "barry-uniqVpci",
            "vpcCidrBlock": "10.20.80.0\/24",
            "subnetNum": 0,
            "createTime": "2015-11-06 20:55:12",
            "networkAclEntrySet": {
                "egress": [
                    {
                        "desc": "",
                        "ipProtocol": "all",
                        "cidrIp": "0.0.0.0\/0",
                        "portRange": "ALL",
                        "action": 1
                    }
                ],
                "ingress": [
                    {
                        "desc": "",
                        "ipProtocol": "all",
                        "cidrIp": "0.0.0.0\/0",
                        "portRange": "ALL",
                        "action": 1
                    }
                ]
            }
        },
        {
            "vpcId": "gz_vpc_265",
            "unVpcId": "vpc-ktom9wg5",
            "networkAclName": "barrytt",
            "networkAclId": "acl-cva92t60",
            "vpcName": "yunapitest",
            "vpcCidrBlock": "10.100.100.0\/24",
            "subnetNum": 0,
            "createTime": "2015-11-04 10:37:07",
            "networkAclEntrySet": {
                "egress": [
                    {
                        "desc": "",
                        "ipProtocol": "all",
                        "cidrIp": "0.0.0.0\/0",
                        "portRange": "ALL",
                        "action": 1
                    }
                ],
                "ingress": [
                    {
                        "desc": "",
                        "ipProtocol": "all",
                        "cidrIp": "0.0.0.0\/0",
                        "portRange": "ALL",
                        "action": 1
                    }
                ]
            }
        },
        {
            "vpcId": "gz_vpc_76",
            "unVpcId": "vpc-03vihbk9",
            "networkAclName": "dddddUniq",
            "networkAclId": "acl-7gvd06dq",
            "vpcName": "pan-vpc2",
            "vpcCidrBlock": "10.100.2.0\/24",
            "subnetNum": 0,
            "createTime": "2015-10-22 18:23:29",
            "networkAclEntrySet": {
                "egress": [
                    {
                        "desc": "",
                        "ipProtocol": "all",
                        "cidrIp": "0.0.0.0\/0",
                        "portRange": "ALL",
                        "action": 1
                    }
                ],
                "ingress": [
                    {
                        "desc": "",
                        "ipProtocol": "all",
                        "cidrIp": "0.0.0.0\/0",
                        "portRange": "ALL",
                        "action": 1
                    }
                ]
            }
        }
    ]
}

```

