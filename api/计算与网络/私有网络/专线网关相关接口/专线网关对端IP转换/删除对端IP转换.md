## 1. 接口描述
本接口(DeletePeerIPTranslationNatRule)用于删除专线网关对端IP转换。
接口请求域名：<font style='color:red'>vpc.api.qcloud.com </font>



## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href='/doc/api/372/4153' title='公共请求参数'>公共请求参数</a>页面。其中，此接口的Action字段为DeletePeerIPTranslationNatRule。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 私有网络ID或者统一ID，建议使用统一ID。|
| directConnectGatewayId | 是 | String | 专线网关ID。|
| peerIPTranslation.n | 是 | Array | 对端IP转换规则数组。 |
| peerIPTranslation.n.originalIP | 是 | String | 原始IP。 |
| peerIPTranslation.n.translationIP | 是 | String | 转换后IP。 |


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码。0表示成功，其他值表示失败。详见错误码页面的<a href='/document/api/215/4781' title='公共错误码'>公共错误码</a>。|
| message | String | 模块错误信息描述，与接口相关。|
| codeDesc | String | 错误码。 |
| data | Array | 返回信息。 |

## 4. 错误码表
  以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的VPC，VPC资源不存在。请再次核实您输入的资源信息是否正确。可调用<a href="/doc/api/245/%e5%88%9b%e5%bb%ba%e7%a7%81%e6%9c%89%e7%bd%91%e7%bb%9c" title="查询私有网络列表">查询私有网络列表</a>(DescribeVpcEx)接口查询。|
| InvalidDirectConnectGateway.NotFound | 无效的专线网关，专线网关资源不存在。请再次核实您输入的资源信息是否正确。可调用<a href="/doc/api/245/%e6%9f%a5%e8%af%a2%e4%b8%93%e7%ba%bf%e7%bd%91%e5%85%b3" title="查询专线网关">查询专线网关</a>(DescribeDirectConnectGateway)接口查询。|
| InvalidPeerIPTranslation.NotFound | 无效的对端IP转换规则，对端IP转换规则不存在。请再次核实您输入的资源信息是否正确。可调用<a href="/doc/api/245/%e6%9f%a5%e8%af%a2%e4%b8%93%e7%ba%bf%e7%bd%91%e5%85%b3%e5%af%b9%e7%ab%afIP%e8%bd%ac%e6%8d%a2" title="查询专线网关对端IP转换">查询专线网关对端IP转换</a>(DescribePeerIPTranslationNatRule)接口查询。|

## 5. 示例
输入
<pre>
http://vpc.api.qcloud.com/v2/index.php?Action=DeletePeerIPTranslationNatRule
&<<a href="/doc/api/229/6976">公共请求参数</a>>
&vpcId=vpc-csnmo39l
&directConnectGatewayId=dcg-mm01ughx
&peerIPTranslation.0.originalIP=10.100.10.3
&peerIPTranslation.0.translationIP=183.0.0.1
&peerIPTranslation.0.description=183.0.0.1
</pre>
输出
```
{
    "code":"0",
    "message":"",
    "codeDesc":"Success",
    "data":[
        
    ]
}
```

