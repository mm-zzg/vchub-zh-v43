# findWebView

**描述：** 查询场景中符合条件的第一个内嵌页面

查询内嵌页面：

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const mash = await scene.findWebView({
    //id:"3b013f32-d6b0-484e-835c-e63e75d30ecb", //要查询模型的唯一uuid
    name: 'webView', //模糊查询名字包含webView的内嵌页面
    //userData  用户自定义的数据内容
})
console.log(mash) //输出所有查询到的结果
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以查询场景中名字包含 webView 的第一个内嵌页面

![1](../../../assets/images/3d_lowcode_SOperation_findwebview1.gif)

查询到的模型可以使用其所有方法和属性：

![alt text](3d_lowcode_SOperation_findwebview2.png)




