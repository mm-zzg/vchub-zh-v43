

# System.Tag.readValue

## 描述

获取单个或多个变量的值。

## 语法
**System.Tag.readValue(path: string): Promise`<any>`**

**System.Tag.readValue(path: Array`<string>`): Promise<{path: string; value: any}>**

- 参数

    path - 单个或多个变量路径

- 返回

    单个变量的值或多个变量的值和路径

## 代码示例 

获取变量"设备:温度"的值。
```typescript 
const tagValue = await System.Tag.readValue('@设备:温度');
console.log(tagValue);
```   
获取变量"设备:温度、设备:功率"的路径及其对应的值。

```typescript 
const tags = await System.Tag.readValue(['@设备:温度','@设备:功率']);
console.log(tags);
```   
