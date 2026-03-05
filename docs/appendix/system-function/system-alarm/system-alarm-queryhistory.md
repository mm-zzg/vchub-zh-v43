# System.Alarm.queryHistory

## 描述

查询当前历史存储的历史报警。

## 语法

**System.Alarm.queryHistory(historyStorage:string): Promise`<any>`**
<br>**System.Alarm.queryHistory(historyStorage:string,params:{**
<br>**startTime?: Date | string,**
<br>**endTime?: Date | string,**
<br>**priority?: AssetAlarmPriority | AssetAlarmPriority[],**
<br>**state?: AssetAlarmState | AssetAlarmState[],**
<br>**path?: string | string[],**
<br>**type?: AssetAlarmType | AssetAlarmType[],**
<br>**asset?: string | string[],**
<br>**expression?: string}): Promise`<any>`**
<br>-参数
<br>historyStorage - 历史存储名称
<br>params  - 查询条件对象，可选参数
<br>{
<br>startTime? - 开始时间，默认为当前时间前8小时
<br>endTime? - 结束时间，默认为当前时间
<br>priority? -  单个或多个等级，可选值为“Low”，“Medium”，“High”，“Critical”
<br>state? - 单个或多个状态，可选值为“Active”，“Unacked”，“Acked”，“Cleared”
<br>path? - 单个或多个报警路径
<br>type? - 单个或多个类型，可选值为"H"，"H2"，"H3"，"H4"，"L"，"L2"，"L3"，"L4"，<br>"RateOfChange"，"Equivalent"，"TrueToFalse"，"FalseToTrue"
<br>asset? - 单个或多个资产
<br>expression? - 表达式，例1：priority == "Low"，例2：path.Contains("Device")，例<br>3：state.HasFlag("Active") && stae.HasFlag("“Unacked")

<br>}
<br>-返回
<br>[
<br>{
<br>path: string //报警路径
<br>name: string //报警名称
<br>type: string //类型
<br>priority: string //等级
<br>eventId: string //状态变更Id
<br>eventTime: string //状态变更时间
<br>state: string //状态
<br>operator: string //确认人
<br>valueType: string //值类型
<br>value: string //报警值
<br>ackTime: string  //确认时间
<br>ackNotes: string //确认信息
<br>ackMode: string //确认模式
<br>nodeName: string //节点名称
<br>storageName: string //历史存储名称
<br>description: string //描述
<br>},
<br>...
<br>]  

## 代码示例 

查询历史存储为"Default"最近8小时的历史报警。

```typescript 
const value = await System.Alarm.queryHistory("Default");
console.log(value);
```   
查询历史存储为"Default"，时间范围为“2025-03-10 00:00:00”至“2025-03-11 00:00:00”，报警等级为“High”，类型为“H”或“H2”，且状态为 "Active,Unacked"的历史报警。

```typescript
const value = await System.Alarm.queryHistory("Default",{startTime:'2025-03-10 00:00:00',endTime:'2025-03-11 00:00:00',priority:"High",type:["H","H2"],expression:'state.HasFlag("Active") && state.HasFlag("Unacked")'});
console.log(value);
``` 

