# createDiffusion

**描述：** 创建可以扩散的特效



**示例1：** 创建扩散的球形特效

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1'”的3D查看器控件
const scene = await view.getScene();
scene.createDiffusion({
    name: 'Diffusion', // 创建扩散特效的名称
    type: 'Sphere', // 支持 'Sphere' 和 'Cylinder' 创建球形或者圆柱形扩散
    color: '#ff0000', // 特效颜色 默认蓝色
    radius: 50, // 初始半径大小
    height: 50, // 特效初始高度
    diffuse: 10, // 扩散比例
    position: { x: 0, y: 0, z: 0 }, // 扩散中心位置
    duration: 3000, // 扩散时间
    reversePlay: false // 是否需要反向
})
```
 
在按钮上编写上述代码，点击按钮，可以在指定位置创建扩散的球形特效

![alt text](5.gif)


**示例2：** 创建圆柱形扩散特效

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1'”的3D查看器控件
const scene = await view.getScene();
scene.createDiffusion({
    name: 'Diffusion', // 创建扩散特效的名称
    type: 'Cylinder', // 支持 'Sphere' 和 'Cylinder' 创建球形或者圆柱形扩散
    color: '#ff0000', // 特效颜色 默认蓝色
    radius: 50, // 特效初始半径
    height: 80, // 特效初始高度
    diffuse: 5, // 扩散比例
    position: { x: 0, y: 0, z: 0 }, // 扩散中心位置
    duration: 3000, // 扩散时间
    reversePlay: true // 是否需要反向
})
```
 
在按钮上编写上述代码，点击按钮，可以在指定位置创建扩散的圆柱形特效

![alt text](6.gif)
