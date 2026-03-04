# getChildren

**描述：获取模型的子级**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const box=scene.createBasicMesh({
    type: 'Box',       //模型在模型库的地址
    name: 'Box2',                //创建后的名字
    color: '#6ec800',            //创建的颜色
    position: { x: 0, y:0, z: 0 },     //创建的位置
    rotation: { x: 0, y: 0, z: 0 },     //创建时旋转角度
    size: [30, 30, 30],
});  
const box2=scene.createBasicMesh({
    type: 'Box',       //模型在模型库的地址
    name: 'Box222',                //创建后的名字
    color: '#6ec800',            //创建的颜色
    position: { x: 100, y:100, z: 0 },     //创建的位置
    rotation: { x: 0, y: 0, z: 0 },     //创建时旋转角度
    size: [30, 30, 30],
    parent:box  //设置box2模型的父级为box
});  
console.log(box.getChildren());//控制台输出box的子级数组
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以获取模型的子级模型数组。

![1](../../../../assets/images/3d_lowcode_object_bmodel_getchildren1.gif)
