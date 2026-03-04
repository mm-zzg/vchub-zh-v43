# createRain

**描述：** 创建默认下雨特效

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const rain =scene.createRain({
    name: 'rain', //创建雨的名字
    position: { x: 0, y: 0, z: 0 }, //创建下雨的中心位置
    range:{ depth: 1000, width: 500, height: 500 }, //雨点下落的范围 默认(1000,500,500)     depth值为y轴向上depth/2范围和y轴向下depth/2的范围
    speed: 1, //下落速度(默认0.5)
    count: 2500 //雨点数量(默认2000)
});
```
**示例：**

在按钮上编写上述代码，点击按钮，可以在指定位置创建下雨特效

![alt text](15.gif)

修改下雨特效和关闭特效：

![alt text](16.png)


