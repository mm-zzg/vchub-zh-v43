# createLine

**描述：** 创建线进入场景中

```typescript
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const linePaths = [
    { x: -20, y: -10, z: 0 },
    { x: 60, y: 40, z: 0 },
    { x: 60, y: -10, z: 0 },
    { x: 60, y: -10, z: 20 },
]; //线条顶点坐标
const line =scene.createLine({
    name: 'line', //创建的线条名字
    points:linePaths, //创建顶点坐标
    color: 'rgba(189, 16,224)', //创建的线条颜色
    width:1, //创建线的宽度，默认1
    curve: true, //创建的线条是否为曲线，默认false
    dashed:true //创建的线条是否为虚线，默认false
})
```
**示例：**

在按钮上编写上述代码，点击按钮，可以创建线 进入场景中

![alt text](10.gif)