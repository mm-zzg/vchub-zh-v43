
# System.UI.open


## 描述

用替换窗口的方式打开新的画面。

## 语法

**System.UI.open(page: string, pageProperties?: any): void**

- 参数

     page - 需要打开的画面名称

     pageProperties - 画面属性

- 返回

     无

## 代码示例

打开画面A。

```typescript 
System.UI.open('A');
```

打开画面 A，并将 A 的画面属性 id 设置为"A0003"。

```typescript 
System.UI.open('A', {
    custom: {
        id: "A0003"
    }
});
```  
