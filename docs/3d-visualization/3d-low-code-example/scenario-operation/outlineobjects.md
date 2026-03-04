# outlineObjects

**描述：设置需要勾边的模型**

```typescript
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const forklift = await scene.findMesh({ name: 'Forklift' });
const roboticArm02 = await scene.findMesh({ name: 'RoboticArm_02' });
scene.outlineObjects = [roboticArm02];
```
 
**示例：**

在按钮上编写上述代码，点击按钮，对传入的模型进行勾边。

![1](../../../assets/images/3d_lowcode_SOperation_outlineobjects1.gif)