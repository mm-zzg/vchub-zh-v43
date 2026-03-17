
# System.Library.getSystemImage

## 描述

获取系统图库的图片。

## 语法

System.Library.getSystemImage(path:string): Promise`<string>`

- 参数 

    path - 图片的路径 

- 返回

    base64

## 代码示例

获取系统图库"电力"下的"变压器.svg"。

```typescript 
const base64 = await System.Library.getSystemImage('电力.变压器.svg');
console.log(base64)

```   

