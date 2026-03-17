# name

**描述：获取模型的name**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const box=scene.createBasicMesh({
    type: 'Box',       //模型在模型库的地址
    name: 'Box2',                //创建后的名字
    color: '#6ec800',            //创建的颜色
    position: { x: 0, y:0, z: 0 },     //创建的位置
    rotation: { x: 0, y: 0, z: 0 },     //创建时旋转角度
    size: [30, 30, 30]
});   //创建的基础模型的初始长宽高，Box默认值[5,5,5]，Sphere默认值[3.5,15,15]，Cylinder默认值[2,2,15,20]，

console.log(box.name);//控制台输出box的name
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以在控制台输出模型name。

![1](../../../../assets/images/3d_lowcode_object_bmodel_name1.gif)

