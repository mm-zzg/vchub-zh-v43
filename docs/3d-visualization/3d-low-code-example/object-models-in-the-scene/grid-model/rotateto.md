



# rotateTo

**描述：模型旋转动画**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const mesh = await scene.findMesh({ name: 'Forklift' });
const meshRotation = mesh.rotation;
mesh.rotateTo({
    rotation: { x: meshRotation.x, y: meshRotation.y - 90, z: meshRotation.z } //模型需要旋转到的角度
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以播放模型旋转动画。





![1](../../../../assets/images/3d_lowcode_object_gmodel_rotateto1.gif)