# skybox

**描述：** 传入用户创建的天空盒库名称或者系统默认天空盒库名称,如果同时设定背景色和背景图片和天空盒以天空盒为主(天空盒图片必须是正方形)

```typescript
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
view.skyBox='sunset';//传入天空盒的名字
view.applyChanges();//应用更改(Tips:背景相关的设置设置了之后需要调用一下需要调用applyChanges()方法)
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改场景的天空盒。

![1](../../../assets/images/3d_lowcode_SOperation_skybox1.gif)
