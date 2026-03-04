








# wireframe

**描述：模型是否开启线框模式**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const mesh = await scene.findMesh({ name: 'Forklift' }); //查找模型
mesh.wireframe = true; //模型是否开启线框模式
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以设置模型线框模式。




![1](../../../../assets/images/3d_lowcode_object_gmodel_wireframe1.gif)