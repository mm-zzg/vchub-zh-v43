# image

**描述：修改面图片**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const plane = await scene.findPlane({ name: 'Plane1' });//查找模型
plane.image='a.win10.jpg';//修改图片
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改图片。

![1](../../../../assets/images/3d_lowcode_object_surface_image1.gif)

