## 1. 接口描述

本接口（ModifyNetworkAcl）用于修改网络ACL名称。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font> 
 

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为ModifyNetworkAcl。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 子网所属的私有网络ID值，可使用vpcId或unVpcId，建议使用unVpcId，例如：vpc-ktom9wg5。可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。 | 
| networkAclId | 是 | String | 系统分配的网络ACL ID，例如：acl-cva92t60。可通过<a href="/doc/api/245/1441" title="DescribeNetworkAcl">DescribeNetworkAcl</a>接口查询。 |
| networkAclName | 是 | String | 网络ACL名称，可任意命名，但不得超过60个字符。 |


## 3. 输出参数
 
| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| code| Int | 错误码，0: 成功，其他值: 失败。 |
| message | String | 错误信息。 |


## 4. 错误码表
  以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的 VPC。VPC 资源不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询VPC。 |
| InvalidNetworkAclID.NotFound | 无效的网络 ACL ID。网络 ACL ID不存在，请再次核实您输入的资源信息是否正确，可通过<a href="/doc/api/245/1441" title="DescribeNetworkAcl">DescribeNetworkAcl</a>接口查询。 |
| InvalidNetworkAclName | 网络 ACL 名称不合法。可任意命名，但不得超过60个字符。 |

## 5. 示例
 
输入
<pre>
  http://vpc.api.qcloud.com/v2/index.php?Action=ModifyNetworkAcl
  &<<a href="/doc/api/229/6976">公共请求参数</a>>
  &vpcId=vpc-ktom9wg5
  &networkAclId=acl-cva92t60
  &networkAclName=barrytt

</pre>

输出
```

{
    "code": 0,
    "message": ""
}

```

