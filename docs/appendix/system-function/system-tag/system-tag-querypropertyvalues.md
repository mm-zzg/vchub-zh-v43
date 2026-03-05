
# System.Tag.queryPropertyValues


## 描述

获取指定父级路径下直接（非递归）子节点的路径、属性名称和属性值。

## 语法

**System.Tag.queryPropertyValues(tagParentPath:string,property:string): Promise`<Array<{ path: string; property: string; value: any }>>`**

- 参数

    tagParentPath - 父级路径

    property  - 属性名称

- 返回

    直接子节点的路径、属性名称、属性值

## 代码示例

获取路径"设备:设备1"下所有直接子节点的路径，以及子节点的 Name 属性的值。

```typescript 
const tagProperties = await System.Tag.queryPropertyValues('@设备:设备1','Name');
console.log(tagProperties);
```   
