# System.UI.close


## 描述

关闭当前打开的画面。

## 语法

**System.UI.close(data?: any): void**

- 参数

    data - 关闭弹框页面时可用，作为 System.UI.openPopup 函数的返回值

- 返回

    无

## 代码示例

关闭当前画面

```typescript 
System.UI.close();

```
关闭当前弹框画面

```typescript 
System.UI.close('Successfully added');
```
