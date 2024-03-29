## 1. 接口描述
 
本接口(DescribeRedis)用于查询CRS实例列表。
接口请求域名：<font style='color:red'>redis.api.qcloud.com </font>

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href='/doc/api/372/4153' title='公共请求参数'>公共请求参数</a>页面。其中，此接口的Action字段为DescribeRedis。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| limit | 是 | Int | 分页大小|
| offset | 是 | Int | 当前页码|
| redisId | 否 | String | 实例Id|
| redisName | 否 | String | 实例名称|
| orderBy | 否 | String | 枚举范围redisId,projectId,createtime|
| orderType | 否 | Int | 1倒序，0顺序，默认倒序|
| vpcIds.n  | 否 | Int | 历史原因，仍保留该参数，推荐使用下面参数unVpcIds。 私有网络ID数组，数组下标从0开始，如果不传则默认选择基础网络。|
| unVpcIds.n  | 否 | String | 私有网络ID数组，数组下标从0开始，如果不传则默认选择基础网络。请使用[私有网络列表](/doc/api/245/1372) 查询返回的unVpcId为准，如：vpc-kd7d06of|
| subnetIds.n | 否 | Int | 历史原因，仍保留该参数，推荐使用下面参数unSubnetIds。私有网络下的子网ID数组，数组下标从0开始|
| unSubnetIds.n | 否 | String | 子网ID数组，数组下标从0开始。 vpc子网下，取值以查询[查询子网列表](/document/product/215/1371) 返回的unSubnetId为准，如：subnet-3lzrkspo|
| projectIds.n | 否 | String | 项目ID 组成的数组，数组下标从0开始|

## 3. 输出参数
| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码, 0表示成功，其他值表示失败。详见错误码页面的<a href='/document/api/239/1757' title='公共错误码'>公共错误码</a>。|
| message | String | 模块错误信息描述，与接口相关。|
| codeDesc | String | 业务侧错误码英文描述。成功时返回Success，错误时返回具体业务错误原因。 |
| totalCount | Int | 实例数 |
| data | Array |  |
| data.redisSet | Array | | 
| data.redisSet.redisName | String | 实例名称 | 
| data.redisSet.redisId | String | 实例唯一串号| 
| data.redisSet.appid | Int | appid | 
| data.redisSet.projectId | Int | 项目id | 
| data.redisSet.regionId | Int | 地域id 1--广州 4--上海  7--上海金融 8--北京  11--深圳金融  | 
| data.redisSet.zoneId | Int | 区域id | 
| data.redisSet.vpcId | Int | vpc网络id，不推荐使用 |
| data.redisSet.unVpcId | String | vpc网络id，推荐使用 |  
| data.redisSet.subnetId | Int | vpc网络下子网id，不推荐使用 |
| data.redisSet.unSubnetId | String | vpc网络下子网id，推荐使用 | 
| data.redisSet.status | Int | 实例当前状态，0：待初始化；1：实例在流程中；2：实例运行中；-2：实例已隔离 | 
| data.redisSet.statusDesc | String | 实例状态描述 | 
| data.redisSet.wanIp | String | 实例vip | 
| data.redisSet.port | Int | 实例端口号 | 
| data.redisSet.createtime | String | 实例创建时间 | 
| data.redisSet.size | Int | 实例容量大小，单位：MB| 
| data.redisSet.sizeUsed | Int | 实例当前已使用容量，单位：MB | 
| data.redisSet.typeId | Int | 实例类型，1：集群版；2：主从版| 
| data.redisSet.typeIddesc | String | 实例类型描述 |
 | data.redisSet.deadlineTime | String | 实例到期时间 |


## 4. 错误码
以下错误码表列出了该接口的业务逻辑错误码。

| 错误代码 | 英文提示 | 错误描述 |
|---------|---------|---------|
|11201|InvalidParameter|业务参数错误|

## 5. 示例
<pre>
http://redis.api.qcloud.com/v2/index.php?Action=DescribeRedis
&<<a href="/doc/api/229/6976">公共请求参数</a>>
&limit=10
&offset=0
</pre>
返回示例如下：
```
{
    "code": 0,
	"message": ""，
	"codeDesc": "Success",
    "totalCount": 1,
    "data": {
        "redisSet": [
            {
                "redisName":"att_test",
                "redisId":"crs-ooakfyj3",
                "appid":"1251966477",
                "projectId":"0",
                "regionId":"1",
                "zoneId":"100002",
                "vpcId": 4864,
 				"unVpcId": "vpc-j5yvvkul",
                "subnetId": 14158,
				"unSubnetId": "subnet-py2q60ty",
                "status":"2",
                "statusDesc":"实例运行中",
                "wanIp":"10.66.170.224",
                "port":"6379",
                "createtime":"2016-05-04 16:59:53",
                "size":"2048",
                "sizeUsed":"0",
                "typeId":"1",
                "typeIddesc":"集群版",
				"autoRenewFlag": 1,
                "deadlineTime":"2016-08-14 16:59:53"
            }
        ]
    }
}
```