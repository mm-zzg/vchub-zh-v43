# position

**描述：设置摄像机的位置**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
scene.camera.position={x:30,y:17,z:-10};//设置摄像机位置为30，17，-10
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以设置摄像机的位置

![position](../../../assets/images/position.gif)

