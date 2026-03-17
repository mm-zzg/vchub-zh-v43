# getWorldPosition

**描述：获取模型的世界坐标**

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
});  
console.log(box.getWorldPosition());//控制台输出模型世界坐标
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以获取模型的世界坐标。

![1](../../../../assets/images/3d_lowcode_object_bmodel_getworldposition1.gif)
