# createFire

**描述：** 创建默认火焰特效

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1'”的3D查看器控件
const scene = await view.getScene();
const fire =scene.createFire({
    name: 'fire', //创建火焰的名字
    position: { x: 0, y: 0, z: 0 }, //创建火焰的中心位置
    size:100 //火焰大小(默认5)
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以在指定位置创建火焰特效

![alt text](7.gif)

修改火焰特效和关闭特效：

![alt text](8.png)



