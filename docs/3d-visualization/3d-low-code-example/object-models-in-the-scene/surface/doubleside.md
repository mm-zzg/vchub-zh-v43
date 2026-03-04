# doubleSide

**描述：修改面是否双面显示**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const plane = await scene.findPlane({ name: 'Plane1' });//查找模型
plane.doubleSide=true;//设置双面显示
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以设置双面显示。

![1](../../../../assets/images/3d_lowcode_object_surface_doubleside1.gif)

