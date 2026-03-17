# createTube

**描述：** 创建可以贴图的曲线

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const linePaths = [
    { x: -20, y: -10, z: 0 },
    { x: 60, y: 40, z: 0 },
    { x: 60, y: -10, z: 0 },
    { x: 60, y: -10, z: 20 },
]; //线条顶点坐标
const tube =scene.createTube({
    name: 'tube', //创建线条名字
    points:linePaths, //创建线条顶点坐标
    color: 'rgba(189, 16,224)', //创建线条颜色
    width: 3, //创建线条宽度(默认1)
    image: 'a.箭头.png', //创建线条贴图路径
   repeatX: 15, //图片在x方向的重复次数(默认1)
   repeatY: 6 ////图片在y方向的重复次数(默认1)
})
```
**示例：**

在按钮上编写上述代码，点击按钮，可以创建贴图的曲线 进入场景中

![alt text](22.gif)
