

# System.Tag.writeValue


## 描述

对单个或多个变量写值。

## G语法

**System.Tag.writeValue(path: string, newValue: any): Promise`<void>`**

**System.Tag.writeValue(path: string[], newValue: Array`<any>`): Promise`<void>`**

- 参数

    path - 单个或多个变量路径

    newValue - 单个或多个变量的新值

- 返回

    无

## 代码示例 

将 'Device:Start ' 写为 true。

```typescript 

await System.Tag.writeValue('@设备:启动', true);
```
将 'Device:Start ' 和 'Device:MaxPower ' 分别写为 true和500。
```typescript 

await System.Tag.writeValue(['@设备:启动', '@设备:最大功率'], [true, 500]);
```   
