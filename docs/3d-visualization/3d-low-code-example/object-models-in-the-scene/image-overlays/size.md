# size
**描述：修改canvas的size**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const canvas = await scene.findCanvas({ name: 'Canvas' });//查找模型
canvas.size={width:1000,height:1000};//修改canvas的size
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改canvas的size。

![1](../../../../assets/images/3d_lowcode_object_overlays_size1.gif)
