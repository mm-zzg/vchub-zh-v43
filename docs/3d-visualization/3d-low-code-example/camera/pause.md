# pause

**描述：暂停当前的摄像机动画**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
scene.camera.pause();
```
 
**示例：**

在执行摄像机飞行动画期间，点击按钮，暂停当前的动画，恢复自由视角

![pause](../../../assets/images/pause.gif)