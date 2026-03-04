# createSmoke

**描述：** 创建默认烟雾特效

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const smoke =scene.createSmoke({
    name: 'smoke', //创建烟雾的名字
    position: { x: 0, y: 0, z: 0 }, //创建烟雾的中心位置
    size:5 //烟雾大小(默认1)
});
```
**示例：**

在按钮上编写上述代码，点击按钮，可以在指定位置创建烟雾特效

![alt text](17.gif)

关闭特效：

![alt text](18.png)


