







# fontSize

**描述：修改文本标注大小**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const label = await scene.findTextLabel({ name: 'Label1' });//查找模型
label.fontSize=100;//修改文本标注大小
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改文本标注大小。



![1](../../../../assets/images/3d_lowcode_object_textAnnotation_fontsize1.gif)