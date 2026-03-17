# sSystem.Alarm.query

## 描述
 查询实时报警。

## 语法

**System.Alarm.query(): Promise`<any>`**  
**System.Alarm.query(params?:{**  
**priority?: AlarmPriority | AlarmPriority[],**  
**state?: AlarmState | AlarmState[],**  
**path?: string | string[],**  
**type?:AlarmType | AlarmType[],**  
**asset?: string | string[],**  
**group?: string | string[],**  
**expression?: string}): Promise`<any>`**  
-参数        
params - 查询条件对象，可选参数        
{             
priority? -  单个或多个等级，可选值为“Low”，“Medium”，“High”，“Critical”             state? - 单个或多个状态，可选值为“Active”，“Unacked”，“Acked”，“Cleared”             path? - 单个或多个报警路径             
type? - 单个或多个类型，可选值为
"H"，"H2"，"H3"，"H4"，"L"，"L2"，"L3"，"L4"，"RateOfChange"，"Equivalent"，"TrueToFalse"，"FalseToTrue"             
group? - 单个或多个报警组             
asset? - 单个或多个资产             
expression? - 表达式，例1：priority == "Low"，例2：path.Contains("Device")，例3：state.HasFlag("Active") && stae.HasFlag("“Unacked")        
}  
-返回  
[           
{  path: string //报警路径              
name: string //报警名称              
type: string //类型             
priority: string //等级             
eventTime: string //状态变更时间              
state: string //状态              
operator: string //确认人              
valueType: string //值类型              
value: string //报警值  
ackTime: string  //确认时间  
ackNotes: string //确认信息              
recoveryTime:string //恢复时间  
description: string //描述  
ackMode: string //确认模式              
ruleName: string //通知规则  
groupNames: string //报警组              
activeTime: string //激活时间      
},            
...        
] 

## 代码示例

查询所有的实时报警。 

```typescript 
const value = await System.Alarm.query(); console.log(value); 
```   
查询报警等级为 High，类型为 H 或 H2，报警组为Default，且状态为 "Active,Unacked" 的实时报警。 
```typescript 
const value = await System.Alarm.query({priority:"High",type:["H","H2"],group:'Default',expression:               
'state.HasFlag("Active") && state.HasFlag("Unacked")'}); 
console.log(value); 
```

