# title

**描述：修改内嵌页面的** **title**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const webview = await scene.findWebView({ name: 'Webview1' });//查找模型
webview.title='test title';//修改内嵌页面的title
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改内嵌页面的title。

![1](../../../../assets/images/3d_lowcode_object_ePage_title1.gif)

