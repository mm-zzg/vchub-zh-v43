






# movePaths

**描述：模型根据路径位移动画**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const mesh = await scene.findMesh({ name: 'Forklift' });
const meshWorldPosition = mesh.getWorldPosition();
const paths = [
    { x: meshWorldPosition.x, y: meshWorldPosition.y, z: meshWorldPosition.z + 10 },
    { x: meshWorldPosition.x - 30, y: meshWorldPosition.y, z: meshWorldPosition.z + 10 },
    { x: meshWorldPosition.x - 30, y: meshWorldPosition.y, z: meshWorldPosition.z },
    { x: meshWorldPosition.x-10, y: meshWorldPosition.y, z: meshWorldPosition.z },
]
mesh.movePaths({
    worldPaths: paths, // 位移动画路径
    faceForward: true, // 模型始终面向位移方向
    duration: 3000
})
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以播放模型位移动画。



![1](../../../../assets/images/3d_lowcode_object_gmodel_movepaths1.gif)