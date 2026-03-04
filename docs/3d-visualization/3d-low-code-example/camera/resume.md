# resume

**描述：继续执行之前暂停的摄像机动画**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
scene.camera.resume();
```
 
**示例：**

在暂停摄像机飞行动画之后，点击按钮，继续执行之前未完成的摄像机飞行动画

![resume](../../../assets/images/resume.gif)
