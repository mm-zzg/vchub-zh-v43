# System.Page.getPropertyValue

## 描述

获取当前画面自定义属性或控件属性的值。

## 语法  

**System.Page.getPropertyValue(path: string): any**

- 参数 

    path - 画面自定义属性或控件属性的路径 

- 返回 

    属性值


## 代码示例

获取画面自定义属性“编号”的值。

```typescript 

const value = System.Page.getPropertyValue('#custom.编号');
console.log(value);

```   
获取文本输入框1的text属性值。

```typescript 
const value = System.Page.getPropertyValue('文本输入框1#text');
console.log(value);

```   

