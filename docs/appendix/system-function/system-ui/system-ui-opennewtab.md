

# System.UI.openNewTab


## 描述

在新的浏览器tab打开画面。

## 语法

**System.UI.openNewTab(page: string, pageProperties?: any): void**

- 参数

     page - 需要打开的画面名称。

     pageProperties - 画面属性

- 返回

     无

## 代码示例

在新的浏览器 tab 打开画面 A。

```typescript 
System.UI.openNewTab('A');
```
在新的浏览器 tab 打开画面 A，并将 A 的画面属性 id 设置为"A0003"。

```typescript 

System.UI.openNewTab('A', {
    custom: {
        id: "A0003"
    }
});
```   
