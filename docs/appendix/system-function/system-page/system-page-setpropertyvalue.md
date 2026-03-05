
# System.Page.setPropertyValue


## 描述

设置当前画面自定义属性或控件属性的值。

## 语法

**System.Page.setPropertyValue(path: string,value: any): void**

- 参数

    path - 画面自定义属性或控件属性的路径
      
    value - 属性新值
   
- 返回

    无

## 代码示例

获取画面自定义属性“编号”的值，给其值每次加 1。

```typescript 
const value = System.Page.getPropertyValue('#custom.编号');
System.Page.setPropertyValue('#custom.编号', value > 100 ? 0 : value + 1);

```   
设置文本输入框 1 的 text 属性为“WAGO VC Hub”。

```typescript 
System.Page.setPropertyValue('文本输入框1#text', 'WAGO VC Hub');


```   

