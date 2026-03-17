# backgroundImg

**描述：** 设置背景图片

```typescript
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3DView控件
view.backgroundImage='a.win10.jpg'; // 设置背景图片为图库a的win10.jpg图片
view.applyChanges(); // 应用     Tips:背景相关的设置设置了之后需要调用一下需要调用applyChanges()方法
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改场景的背景图片。

![alt text](2.gif)
