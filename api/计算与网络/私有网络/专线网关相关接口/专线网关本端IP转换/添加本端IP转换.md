## 1. 接口描述
本接口(CreateLocalIPTranslationNatRule)用于添加专线网关本端IP转换。
接口请求域名：<font style='color:red'>vpc.api.qcloud.com </font>

1) 私有网络内原 IP 映射为新 IP，并以新 IP 与专线对端进行网络互访，只有 NAT 类型网关才支持。<br/>
2) 原 IP必须在 VPC 网段内，转换后 IP 不能在 VPC 网段内。<br/>
3) 同一个NAT网关下的本端IP转换规则原IP不能重复，转换后IP也不能重复。


## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href='/doc/api/372/4153' title='公共请求参数'>公共请求参数</a>页面。其中，此接口的Action字段为CreateLocalIPTranslationNatRule。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 系统分配的私有网络ID，支持升级前的vpcId，也支持升级后的unVpcId，例如：vpc-ddg454。|
| directConnectGatewayId | 是 | String | 系统分配的专线网关ID，例如：dcg-dgd54g。|
| localIPTranslation.n | 是 | Array | 本端IP转换。|
| localIPTranslation.n.originalIP | 是 | String | 原始IP。|
| localIPTranslation.n.translationIP | 是 | String | 转换后IP。|
| localIPTranslation.n.description | 否 | String | 备注。|


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码，0表示成功，其他值表示失败。详见错误码页面的<a href='/document/api/215/4781' title='公共错误码'>公共错误码</a>。|
| message | String | 模块错误信息描述，与接口相关。|
| data | Array | 返回信息。|
| data.taskId | Int  | 任务ID，操作结果可以用taskId查询，详见<a href="/document/product/215/5094">查询任务执行结果接口</a>。 |
| codeDesc | String | 错误码。|

## 4. 错误码表
  以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的VPC。VPC资源不存在，请再次核实您输入的资源信息是否正确。可调用<a href="/document/product/215/1372" title="查询私有网络列表">查询私有网络列表</a>(DescribeVpcEx)接口查询。|
| InvalidDirectConnectGateway.NotFound | 无效的专线网关。专线网关资源不存在，请再次核实您输入的资源信息是否正确。可调用<a href="/doc/api/245/%e6%9f%a5%e8%af%a2%e4%b8%93%e7%ba%bf%e7%bd%91%e5%85%b3?viewType=preview" title="查询专线网关">查询专线网关</a>(DescribeDirectConnectGateway)接口查询。|
| InvalidOriginalIP.NotInVpcCidr | 无效的原始IP。原始IP不在VPC网段内。|
| InvalidOriginalIP.Duplicate | 无效的原始IP。原始IP重复，原始IP已经在该网关的本端IP专线规则中，原始IP不可重复。|
| InvalidTranslationIP.InVpcCidr | 无效的转换后IP。转换后IP在VPC网段内。|
| InvalidTranslationIP.Duplicate | 无效的转换后IP。 转换后IP重复，转换后IP已经在该网关的本端IP转换规则中，转换后IP不可重复。|
| LocalIPTranslationLimitExceeded | 您添加的本端IP转换规则已达上限。如果需要更多资源，请联系客服申请。更多VPC资源限制信息详见<a href="/doc/product/215/537" title="VPC使用限制">VPC使用限制</a>。|

## 5. 示例
输入
<pre>
http://vpc.api.qcloud.com/v2/index.php?Action=CreateLocalIPTranslationNatRule
&<<a href="/doc/api/229/6976">公共请求参数</a>>
&vpcId=vpc-csnmo39l
&directConnectGatewayId=dcg-mm01ughx
&localIPTranslation.0.originalIP=10.100.10.2
&localIPTranslation.0.translationIP=10.100.10.2
&localIPTranslation.0.description=183.0.0.1
</pre>
输出
```
{
    "code":"0",
    "message":"",
    "data":{
        "taskId":"17934"
    },
    "codeDesc":"Success"
}
```

