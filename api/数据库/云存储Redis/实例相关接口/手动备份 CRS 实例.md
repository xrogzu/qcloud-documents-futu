## 1. 接口描述
本接口(ManualBackupInstance)用于手动备份CRS实例。
接口请求域名：<font style='color:red'>redis.api.qcloud.com </font>

- 请不要频繁的调用该接口，最好每天调用次数不超过24次，否则调用可能会失败。

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href='/document/product/213/6976' title='公共请求参数'>公共请求参数</a>页面。其中，此接口的Action字段为ManualBackupInstance。

| 参数名称 | 是否必选  | 类型 | 描述 |
|:---------|---------|---------|---------|
| redisId | 是 | String | 待操作的实例ID，可通过 [DescribeRedis](/document/product/239/1384) 接口返回值中的 redisId 获取。|
| remark | 否 | String | 备份的备注信息 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码，0表示成功，其他值表示失败。详见错误码页面的<a href='/document/api/239/1757' title='公共错误码'>公共错误码</a>。|
| message | String | 错误信息描述, 成功时，该值为空 |
| codeDesc | String | 业务侧错误码英文描述。成功时返回Success，错误时返回具体业务错误原因。 |
| data | Object | 任务ID |

其中，data 表示任务ID，其参数构成如下：

| 参数名称 | 类型 | 描述 |
|:---------|---------|---------|
| data.requestId | 任务ID | 任务ID，可通过 [DescribeTaskInfo](/document/product/239/1387) 接口查询任务执行状态 |

## 4. 错误码
以下错误码表列出了该接口的业务逻辑错误码。

| 错误代码 | 英文提示 | 错误描述 |
|---------|---------|---------|
|11201|InvalidParameter|业务参数错误|
|10701|InstanceNotExists|没有找到serialId对应的实例|
|10707|InstanceLockedError|实例已被锁住，暂时不能执行该操作|
|10702|InstanceStatusAbnormal|实例状态异常,暂时不能执行该操作（比如：流程中或已隔离或已删除）|

## 5. 示例
<pre>
http://redis.api.qcloud.com/v2/index.php?Action=ManualBackupInstance
&<<a href="/doc/api/229/6976">公共请求参数</a>>
&redisId=crs-izbob1wh
&remark=test_api
</pre>
返回示例如下：
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success"
    "data": {
        "requestId": 375062
    }
}

```