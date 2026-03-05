# System.UI.back


## 描述

使用 System.UI.open() 后可用此函数返回之前页面。

## 语法

**System.UI.back(): void**

- 参数 

    无

- 返回

    无

## 代码示例

在画面A执行脚本 `System.UI.open('B')` 打开画面B。

```typescript 

System.UI.open('B');
```   

在画面 B 执行脚本 `System.UI.back()` 返回画面A。

```typescript 

System.UI.back();
```   
