# createWebView

**描述：** 根据传入的src链接生成默认样式的内嵌页面

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const webView =scene.createWebView({
    name: "webView",//内嵌页面的名字
    title: 'bing',//内嵌页面的标题
    src: 'https://cn.bing.com/?FORM=Z9FD1',//内嵌页面的地址
    size: {
     width: 1000,
     height: 800
    }, //内嵌页面的宽高
    fixed:true, //是否始终面向镜头
    position:{x:0,y:0,z:0}
    //parent:ThreeDlElement|null//创建的父级，默认直接添加进场景
})
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以在指定位置创建内嵌页面

![alt text](23.gif)


