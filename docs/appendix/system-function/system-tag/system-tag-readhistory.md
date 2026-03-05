# System.Tag.readHistory


## Description

获取当前变量的历史记录，包括变量的路径、值、质量位、时间、聚合模式。

## 语法

```typescript
enum AggregationMode { "Raw", "Avg", "Max", "Min", "First", "Last", "Count", "Range", "CountOn", "CountOff", "DurationOn", "DurationOff" }

enum PeriodMode { "Second", "Minute", "Hour", "Day" }

interface ExtraOption { 
  timeout?: number; 
  noInterpolation?: boolean;
  ignoreBadQuality?: boolean; 
  includeBoundingValues?: boolean 
}

interface TagHistoryData {
  path: string;
  value: any;
  quality: string;
  time: string;
  aggregationMode: AggregationMode;
}

System.Tag.readHistory(
  start: Date | string,
  end: Date | string,
  tag: string | Array<string>,
  queryMode: "Raw",
  extraOption?: ExtraOption
): Promise<Array<TagHistoryData>>;

System.Tag.readHistory(
  start: Date | string,
  end: Date | string,
  tag: string | Array<string>,
  queryMode: "FixedPoints",
  aggregationMode: AggregationMode | Array<AggregationMode>,
  points: number,
  extraOption?: ExtraOption
): Promise<Array<TagHistoryData>>;

System.Tag.readHistory(
  startDate: string | Date,
  endDate: string | Date,
  tag: string | Array<string>,
  queryMode: "Periodic",
  aggregationMode: AggregationMode | Array<AggregationMode>,
  period: number,
  periodMode: PeriodMode,
  extraOption?: ExtraOption
): Promise<Array<TagHistoryData>>;

```
Parameter






|  Name         | Type        | Description    |
|:---------------|:-----------------|:----------------|
| start         | Date or string         | 开始时间   |
| end            | Date or string       | 结束时间         |
| tag            | string or `Array<string>`   | 查询的标签或者标签列表 |
| queryMode      | QueryMode           |查询类型   |
| aggregationMode  | AggregationMode or `Array<AggregationMode`> |单个或多个变量聚合模式。
当查询方式为"FixedPoints"、"Periodic"时需指定 |
| points      | number | 点数，当查询方式为"FixedPoints"时需指定 query modes  |
| period        | number          | 周期，当查询方式为"Periodic"时需指定  |
| periodMode    | PeriodMode      | 周期单位，当查询方式为"Periodic"时需指定|
| extraOption.timeout | number    | 查询超时时间，单位为秒|
| extraOption.noInterpolation   | boolean | 是否不启用插值|
| extraOption.ignoreBadQuality  | boolean | 查询原始数据是否忽略坏质量位的数据|
| extraOption.includeBoundingValues | boolean    | 是否在插值时包含临界值。当查询一段时间数据，首尾无数据时，会查询首部前 1 天最后一笔数据，和尾部后一天第一笔数据作为首尾的插值 |


## 代码示例

获取变量"设备:温度"在2024-08-14 00:00:00~2024-08-15 00:00:00之间原始值的历史记录。

```typescript 
const value = await System.Tag.readHistory('2024-08-14 00:00:00', '2024-08-15 00:00:00', '@设备:温度','Raw'，{
  timeout: 30
});
console.log(value);
```
获取变量"设备:温度"在2024-08-14 00:00:00~2024-08-15 00:00:00之间,查询方式为"FixedPoints"，聚合模式为"Avg"，点数为30的历史记录。

```typescript 
const value = await System.Tag.readHistory('2024-08-14 00:00:00', '2024-08-15 00:00:00', '@设备:温度','FixedPoints','Avg',30, {
  timeout: 60,
  noInterpolation: true,
  ignoreBadQuality: true,
  includeBoundingValues: false
});
console.log(value);
```   
获取变量"设备:温度"在2024-08-14 00:00:00~2024-08-15 00:00:00之间,查询方式为"Periodic"，聚合模式为"Max"，周期为1，周期单位为"Minute"的历史记录。

```typescript 
const value = await System.Tag.readHistory('2024-08-14 00:00:00', '2024-08-15 00:00:00', '@设备:温度','Periodic','Max',1,'Minute', {
  timeout: 60,
  noInterpolation: true,
  ignoreBadQuality: true,
  includeBoundingValues: false
});
console.log(value);
```   



