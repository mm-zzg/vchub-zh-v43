# flyPath

**描述：摄像机环绕动画**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
await scene.camera.flyPath ({
    paths: [{x:110,y:150,z:-50},{x:92,y:120,z:-36},{x:23,y:25,z:11},{x:-30,y:10,z:27}], //摄像机飞行路径
    duration: 1800, //摄像机环绕持续时间ms
    target: [0,0,-27]//摄像机飞行时朝向的坐标(默认朝向为当前朝向)
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以开启摄像机飞行动画

![flypath](../../../assets/images/flypath.gif)

