# setOutlineOption
**描述：设置勾边参数**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const forklift = await scene.findMesh({ name: 'Forklift' });
const roboticArm01 = await scene.findMesh({ name: 'RoboticArm_01' });

scene.setOutlineOption({
    color: '#6ec800',
    edgeStrength: 7, // 勾边粗细
    edgeGlow: 1, // 勾边光晕
    pulsePeriod: 5, // 呼吸效果
    selectObjects: [forklift, roboticArm01] // 需要勾边的模型
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，修改勾边的参数，对模型进行勾边。

![1](../../../assets/images/3d_lowcode_SOperation_setoutlineoption1.gif)


