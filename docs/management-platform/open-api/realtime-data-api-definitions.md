# 实时数据接口定义

## GET /api/v1/tagValues

读取实时变量值

协议: Https

请求负载(QueryString):

| 名称 | 类型     | 描述     |
|:------|:----------|:----------|
| path | String[] | 变量列表 |

响应负载(JsonArray):

| 名称    | 类型     | 描述     |
|:---------|:----------|:----------|
| path    | String   | 变量路径 |
| value   | Dynamic  | 变量值   |
| time    | DateTime | 时间戳   |
| quality | String   | 质量     |

## POST /api/v1/tagValues

实时变量写值，支持批量写

协议: Https

请求负载(KeyValue List):

| 名称  | 类型    | 描述   |
|:-------|:---------|:--------|
| key   | String  | 变量名 |
| value | Dynamic | 变量值 |

注意：这边的请求负载是一个如下所示的键值对

![alt text](12.png)

响应负载(JsonObject):

| 名称         | 类型           | 描述   |
|:--------------|:----------------|:----------------|
| totalCount   | Integer        | 变量总数   |
| successCount | Integer        | 写值成功的数量   |
| successCount | Integer        | 写值失败的数量     |
| data         | Key Value List | 一个键值对列表，表示每个变量写值的结果，对于写值失败的变量返回错误消息。键值对的结构如下所示：  <br>![alt text](13.png) |

## GET /api/v1/tagProperties

读取变量属性列表

协议:: Https

请求负载(QueryString):

| 名称 | 类型     | 描述    |
|:------|:----------|:-------------------|
| path | String[] | 属性路径列表, 属性路径由变量路径和属性名称组成.(e.g. Default:tag1#unit) |

响应负载(JsonArray):

| 名称     | 类型    | 描述     |
|:----------|:---------|:----------|
| path     | String  | 变量路径 |
| property | string  | 属性名   |
| value    | Dynamic | 属性值   |

## TagValues /ws/v1/realtimeData

读取实时变量值

协议: WebSocket

请求负载(JsonArray):

| 名称 | 类型     | 描述     |
|:------|:----------|:----------|
| path | String[] | 变量列表 |

响应负载(JsonArray):

| 名称    | 类型     | 描述     |
|:---------|:----------|:----------|
| path    | String   | 变量路径 |
| value   | Dynamic  | 变量值   |
| time    | DateTime | 时间戳   |
| quality | String   | 质量     |

## TagProperties /ws/v1/realtimeData

读取实时变量属性列表

协议: WebSockets

请求负载(JsonArray):

| 名称 | 类型     | 描述   |
|:------|:----------|:---------------|
| path | String[] | 属性路径列表, 属性路径由变量路径和属性名称组成.(e.g. Default:tag1#unit) |

响应负载(JsonArray):

| 名称     | 类型    | 描述     |
|:----------|:---------|:----------|
| path     | String  | 变量路径 |
| property | string  | 属性名   |
| value    | Dynamic | 属性值   |

## Alarms /ws/v1/realtimeData

读取实时报警

协议: WebSockets

请求负载:NA

响应负载(JsonArray):

| 名称         | 类型     | 描述                                       |
|:--------------|:----------|:--------------------------------------------|
| eventId      | String   | 报警事件编号                               |
| path         | String   | 变量路径                                   |
| type         | String   | 报警类型 (Limit, LimitHigh1, LimitHigh2… ) |
| priority     | String   | 报警等级 (Low,Mid,High,Urgent)             |
| status       | Status   | 报警状态( UnAck,Acked, Rtun, Norm)         |
| value        | Dynamic  | 变量值                                     |
| valueType    | String   | 变量值类型                                 |
| description  | String   | 报警描述                                   |
| ackTime      | DateTime | 报警确认时间                               |
| ackNotes     | String   | 报警确认备注                               |
| recoveryTime | DateTime | 报警恢复时间                               |
| operator     | String   | 报警确认人                                 |
| isShelved    | Boolean  | 表示报警是否被搁置                         |
| ackMode      | String   | 报警确认类型 (Auto,Manual,ManualNeedInfo)  |
| activeTime   | DateTime | 报警激活时间                               |

## IncrementAlarms /ws/v1/realtimeData

读取实时增量报警。会话首次返回全量实时报警数据，后续以增量方式推送报警的更新数据。

协议: WebSockets

请求负载:NA

响应负载(JsonArray):

| 名称  | 类型                | 描述   |
|:-------|:---------------------|:------------|
| IsAll | Bool                | 一个标记，表示当前返回的结果是全量还是增量的数据    |
| Data  | Key-value pair list | 一个key-value键值对，key表示事件Id, value表示报警详情(AlarmModel) |

AlarmModel

| 名称         | 类型     | 描述                                       |
|:--------------|:----------|:--------------------------------------------|
| eventId      | String   | 报警事件编号                               |
| path         | String   | 变量路径                                   |
| type         | String   | 报警类型 (Limit, LimitHigh1, LimitHigh2… ) |
| priority     | String   | 报警等级 (Low,Mid,High,Urgent)             |
| status       | Status   | 报警状态( UnAck,Acked, Rtun, Norm)         |
| value        | Dynamic  | 变量值                                     |
| valueType    | String   | 变量值类型                                 |
| description  | String   | 报警描述                                   |
| ackTime      | DateTime | 报警确认时间                               |
| ackNotes     | String   | 报警确认备注                               |
| recoveryTime | DateTime | 报警恢复时间                               |
| operator     | String   | 报警确认人                                 |
| isShelved    | Boolean  | 表示报警是否被搁置                         |
| ackMode      | String   | 报警确认类型 (Auto,Manual,ManualNeedInfo)  |
| activeTime   | DateTime | 报警激活时间                               |

## ShelvedAlarms /ws/v1/realtimeData

读取实时搁置报警

协议: WebSockets

请求负载:NA

响应负载(JsonArray):

| 名称           | 类型   | 描述                           |
|:----------------|:--------|:--------------------------------|
| eventId        | String | 报警事件编号                   |
| path           | String | 变量路径                       |
| expirationTime | String | 过期时间                       |
| priority       | String | 报警等级 (Low,Mid,High,Urgent) |
| operator       | String | 报警确认人                     |

## POST /api/v1/alarms/ack

确认报警

协议:: Https

请求负载(JsonObject):

| 名称     | 类型   | 描述         |
|:----------|:--------|:--------------|
| eventId  | String | 报警事件编号 |
| path     | String | 报警路径     |
| operator | String | 报警确认人   |
| notes    | String | 报警确认备注 |

## POST /api/v1/alarms/batchAck

批量确认报警

协议: Https

请求负载(JsonArray):

| 名称     | 类型   | 描述         |
|:----------|:--------|:--------------|
| eventId  | String | 报警编号     |
| path     | String | 报警路径     |
| operator | String | 报警确认人   |
| notes    | String | 报警确认备注 |

响应负载: NA

