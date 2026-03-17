# reset

**描述：重置摄像头设置, 停止摄像头动画, 回到初始位置**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
await scene.camera.reset();//相机位置回到初始位置
```
 
**示例：**

在按钮上编写上述代码，点击按钮，摄像头回到初始位置。

![reset](../../../assets/images/reset.gif)

