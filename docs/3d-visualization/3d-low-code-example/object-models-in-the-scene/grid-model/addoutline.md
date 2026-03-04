# addOutline

**描述：单独为模型设置勾边**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const mesh = await scene.findMesh({ name: 'Forklift' });
mesh.addOutline({
    color: 'red',
    edgeStrength: 3, // 勾边粗细
    edgeGlow: 1, // 勾边光晕
    pulsePeriod: 5, // 呼吸效果
})
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以设置模型勾边及勾边参数。










![1](../../../../assets/images/3d_lowcode_object_gmodel_addoutline1.gif)