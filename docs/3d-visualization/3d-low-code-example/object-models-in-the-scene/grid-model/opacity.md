







# opacity

**描述：改变模型透明度**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const box=await scene.findMesh({name:'Box2'});//查找模型
box.opacity=0.25;//修改模型透明度(0-1)
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改模型透明度。



![1](../../../../assets/images/3d_lowcode_object_gmodel_opacity1.gif)