# System.Tag.read


## 描述

获取单个或多个变量的值、路径、质量位、时间。

## 语法
**System.Tag.read(path: string): Promise<{ path: string; value: any; time: string; quality: string; }>System.Tag.read(paths: Array`<string>`): Promise`<Array<{ path: string; value: any; time: string; quality: string; }>>`**

- 参数

    path - 单个或多个变量的路径

- 返回

    单个或多个变量的值、路径、质量位、时间

## 代码示例

获取变量"设备:温度"的值、路径、质量位、时间。

```typescript 
const tag = await System.Tag.read('@设备:温度');
console.log(tag.value);
```   
获取变量"设备:温度"和"设备:功率"的值、路径、质量位、时间。

```typescript 
const tags = await System.Tag.read(['@设备:温度', '@设备:功率']);
console.log(tags);
```   
