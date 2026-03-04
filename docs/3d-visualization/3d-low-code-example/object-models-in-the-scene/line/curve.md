# curve

**描述：修改线条是否曲线展示**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const line = await scene.findLine({ name: 'Line1' });//查找模型
line.curve=false; //是否曲线展示
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改线条是否曲线展示。
![1](../../../../assets/images/3d_lowcode_object_line_curve1.gif)

