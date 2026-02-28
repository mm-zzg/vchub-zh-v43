# 历史数据接口定义

## GET /api/v1/historicalData/tagValuess

读取变量历史记录

协议: Https

请求负载(QueryString):

| 名称            | 类型     | 描述   |
|:-----------------|:----------|:-----------------------|
| startTime       | DateTime | 开始时间 |
| endTime         | DateTime | 结束时间 |
| queryMode       | String   | 查询模式(None,Raw,FixedPoints,Periodic)   |
| points          | Integer  | 查询点数  |
| interval        | Integer  | 采样周期(单位：秒)   |
| period          | Integer  | 采样周期 |
| periodMode      | Integer  | 采样周期模式(None,Second,Minute,Hour,Day)   |
| aggregationType | String   | 采样类型 (Raw, Avg, Max, Min, First,Last,Count,CountOn,CountOff,DurationOn,DurationOff) |
| path            | String[] | 变量列表  |

响应负载(Json Array)

| 名称    | 类型     | 描述     |
|:---------|:----------|:----------|
| path    | String   | 变量路径 |
| value   | Dynamic  | 变量值   |
| time    | DateTime | 时间戳   |
| quality | String   | 质量     |

## GET /v1/historicalData/alarms

读取历史报警

协议: Https

请求负载(QueryString):

| 名称         | 类型     | 描述   |
|:--------------|:----------|:-------------|
| providerName | String   | 历史库名称    |
| startTime    | DateTime | 开始时间     |
| endTime      | DateTime | 结束时间      |
| path         | String[] | 变量列表   |
| priority     | String[] | 优先级列表(Low,Medium,High,Critical) |
| state        | String[] | 报警状态列表(Active,Unacked,Acked,Cleared) |
| type         | String[] | 报警类型列表(H ,H2 , H3,H4,L,L2,L3,L4,RateOfChange,Equivalent,TrueToFalse,FalseToTrue)                           |
| asset        | String[] | 资产列表   |
| expression   | String   | 表达式，例1：priority == "Low"，例2：path.Contains("Device")，例3：state.HasFlag("Active") && stae.HasFlag("“Unacked") |

响应负载(JsonArray):

| 名称        | 类型     | 描述  |
|:-------------|:----------|:-------------|
| eventId     | String   | 历史记录编号    |
| path        | String   | 报警路径  |
| name        | String   | 报警名称         |
| type        | String   | 报警类型 (H ,H2 , H3,H4,L,L2,L3,L4,RateOfChange,Equivalent,TrueToFalse,FalseToTrue ) |
| priority    | String   | 报警等级 (Low,Medium,High,Critical )   |
| eventTime   | DateTime | 历史记录时间      |
| status      | Status   | 报警状态(Active,Unacked;Active,Acked;Cleared,Unacked;Cleared,Acked)                  |
| value       | Dynamic  | 变量值  |
| valueType   | String   | 变量值类型    |
| description | String   | 报警描述      |
| ackTime     | DateTime | 报警确认时间   |
| ackNotes    | String   | 报警确认备注    |
| operator    | String   | 报警确认人     |
| ackMode     | String   | 报警确认类型 (Auto,Manual,ManualNeedInfo)   |

## POST /v1/historicalData/alarms

读取历史报警

协议: Https

请求负载(JsonObject):

字段说明与** GET /v1/historicalData/alarms** 相同，仅为 POST 形式

响应负载(JsonArray):

字段说明与 **GET /v1/historicalData/alarms** 的响应结构一致

## GET /v1/historicalData/pagedAlarms

分页读取历史报警

协议: Https

请求负载(QueryString):

| 名称         | 类型     | 描述|
|:--------------|:----------|:--------------|
| pageIndex    | Integer  | 当前页码（从 1 开始）  |
| pageSize     | Integer  | 每页返回的数据条数  |
| providerName | String   | 历史库名称   |
| startTime    | DateTime | 开始时间   |
| endTime      | DateTime | 结束时间   |
| path         | String[] | 变量列表   |
| priority     | String[] | 优先级列表(Low,Medium,High,Critical)    |
| state        | String[] | 报警状态列表(Active,Unacked,Acked,Cleared)         |
| type         | String[] | 报警类型列表(H ,H2 , H3,H4,L,L2,L3,L4,RateOfChange,Equivalent,TrueToFalse,FalseToTrue)                           |
| asset        | String[] | 资产列表   |
| expression   | String   | 表达式，例1：priority == "Low"，例2：path.Contains("Device")，例3：state.HasFlag("Active") && stae.HasFlag("“Unacked") |

响应负载(JsonObjec):

| 名称       | 类型                     | 描述     |
|:------------|:--------------------------|:----------------|
| TotalCount | Integer                  | 历史报警的总条数    |
| TotalPage  | Integer                  | 历史报警的总页数    |
| Data       | AssetAlarmHistoryModel[] | 报警数据列表，字段结构与 **GET /v1/historicalData/alarms** 的响应负载一致 |

## POST /v1/historicalData/pagedAlarms

分页读取历史报警

协议: Https

请求负载(JsonObject):

字段说明与 **GET /v1/historicalData/pagedAlarms** 相同，仅为 POST 形式

响应负载(JsonObjec):

字段说明与 **GET /v1/historicalData/pagedAlarms** 的响应结构一致