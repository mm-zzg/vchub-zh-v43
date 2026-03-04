


# points

**描述：修改线条顶点**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const line = await scene.findLine({ name: 'Line1' });//查找模型
line.points=[{x:200,y:200,z:0},{x:100,y:100,z:0},{x:0,y:200,z:200}]; //修改线的顶点
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改线条顶点。





![1](../../../../assets/images/3d_lowcode_object_line_points1.gif)