# rotateAround

**描述：摄像机环绕动画**

```typescript
cconst view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const mesh = await scene.findMesh({ name: 'chariot' });
scene.camera.rotateAround({
    obj: mesh, //摄像机环绕的对象
    yRotateAngle: 360, //摄像机环绕角度
    duration: 3000 //摄像机环绕持续时间ms
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以开启摄像机环绕动画。

![rotate](../../../assets/images/rotate.gif)

