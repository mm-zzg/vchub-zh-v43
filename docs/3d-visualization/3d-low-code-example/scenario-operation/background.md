# background

**描述：** 设置3D场景背景色

```typescript
const view = await System.UI.findControl('3D查看器1');  // 获取画面中名为“3D查看器1'”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
view.backgroundColor= '#6ec800';  // 修改背景色为绿色
view.applyChanges(); // 应用
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改场景的背景色。

![alt text](1.gif)
