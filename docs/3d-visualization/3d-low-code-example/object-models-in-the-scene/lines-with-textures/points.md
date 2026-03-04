# points

**描述：修改贴图线顶点坐标**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const tube = await scene.findTube({ name: 'Tube1' });//查找模型
tube.points = [{ x: Math.floor(Math.random() * 101), y: Math.floor(Math.random() * 101), z: Math.floor(Math.random() * 101) },
{ x: Math.floor(Math.random() * 101), y: Math.floor(Math.random() * 101), z: Math.floor(Math.random() * 101) },
{ x: Math.floor(Math.random() * 101), y: Math.floor(Math.random() * 101), z: Math.floor(Math.random() * 101) },
{ x: Math.floor(Math.random() * 101), y: Math.floor(Math.random() * 101), z: Math.floor(Math.random() * 101) },
{ x: Math.floor(Math.random() * 101), y: Math.floor(Math.random() * 101), z: Math.floor(Math.random() * 101) }];//修改顶点坐标
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改贴图线顶点坐标。

![1](../../../../assets/images/3d_lowcode_object_linetextures_points1.gif)

