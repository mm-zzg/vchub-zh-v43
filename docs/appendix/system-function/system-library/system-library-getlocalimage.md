# System.Library.getLocalImage


## 描述
获取本地图库的图片。

## 语法
**System.Library.getLocalImage(path:string): Promise`<string>`**

- 参数

    path - 图片的路径

- 返回

    base64

## 代码示例

获取本地图库“风景”下的“太阳.svg”。

```typescript 

const base64 = await System.Library.getLocalImage('风景.太阳.svg');
console.log(base64)
```   
