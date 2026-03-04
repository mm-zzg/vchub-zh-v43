# lookAt

**描述：摄像机聚焦于场景内的物体**

#### 使用方式1:

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const mesh = await scene.findMesh({ name: 'Forklift' });
await scene.camera.lookAt({
    object: mesh,
    distance: 1, // 摄像机距离模型的距离
    duration: 500 // 动画持续时间
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，使摄像机从场景中任意位置聚焦到模型。

![lookat](../../../assets/images/lookat.gif)

#### 使用方式2:

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const mesh = await scene.findMesh({ name: 'Forklift' });
await scene.camera.lookAt({
    object: mesh,
    viewOffset: { x: 0, y: 30, z: 0 }, // 动画结束后摄像机位置
    duration: 500 // 动画持续时间
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，使摄像机聚焦到模型并停留在固定位置。


![lookat1](../../../assets/images/lookat1.gif)



