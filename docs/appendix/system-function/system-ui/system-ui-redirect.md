# System.UI.redirect


## 描述

将页面跳转到新的URL。

## 语法

**System.UI.redirect(url:string, newTab?: boolean)**

- 参数

    url - 需要打开的 url 路径

    newTab - 是否以新 tab 的方式打开，默认 true 可不填

- 返回

    无

## 代码示例

在新的 tab 页面打开百度。

```typescript 

System.UI.redirect('https://www.baidu.com/');
```
在当前 tab 页面打开百度。

```typescript 
System.UI.redirect('https://www.baidu.com/', false);

```   
