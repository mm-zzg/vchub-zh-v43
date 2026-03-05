# System.Tag.mock


## 描述

给变量一个模拟值。

## 语法

**System.Tag.mock(path:string, value:any): void**

- 参数

    path - 变量路径

    value - 模拟的值

- 返回

    无

## 代码示例

生成一个 0 到 99 之间的随机整数，并将其赋值给变量“设备:温度”。

```typescript 
const value = parseInt(`${Math.random() * 100}`);
System.Tag.mock('@设备:温度', value);
```   
