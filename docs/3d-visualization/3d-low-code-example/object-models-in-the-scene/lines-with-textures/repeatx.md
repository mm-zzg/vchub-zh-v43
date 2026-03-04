




# repeatX

**描述：修改贴图线图片在x方向的重复次数**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const tube = await scene.findTube({ name: 'Tube1' });//查找模型
tube.repeatX=5;//修改图片在x方向的重复次数
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改图片在x方向的重复次数。



![1](../../../../assets/images/3d_lowcode_object_linetextures_repeatx1.gif)