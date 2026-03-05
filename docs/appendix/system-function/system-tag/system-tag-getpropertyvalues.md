# System.Tag.getPropertyValues


## 描述

获取指定的单个或多个节点的路径、属性名称、属性值。

## 语法

**System.Tag.getPropertyValues(path: string): Promise<{ path: string; property: string; value: any }>System.Tag.getPropertyValues(path: Array`<string>`): Promise`<Array<{ path: string; property: string; value: any }>>`**

- 参数

    path - 单个或多个节点属性的路径

- 返回

    单个或多个节点路径、属性名称、属性值

## 代码示例        

获取节点"设备:温度"的路径以及Name属性的值。

```typescript 
const tagProperty = await System.Tag.getPropertyValues('@设备:温度#Name');
console.log(tagProperty);
``` 
获取节点"设备:温度"和"设备:功率"的路径以及Name属性的值。

```typescript 
const tagProperties = await System.Tag.getPropertyValues(['@设备:温度#Name', '@设备:功率#Name']);
console.log(tagProperties);
```   
