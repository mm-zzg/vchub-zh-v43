
# moveTo

**描述：模型位移动画**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const mesh = await scene.findMesh({ name: 'Forklift' });
const meshWorldPosition = mesh.getWorldPosition();
box.moveTo({
    worldPosition:{ x: meshWorldPosition.x, y: meshWorldPosition.y, z: meshWorldPosition.z +10}, //模型需要移动到的世界坐标
    duration:500, //动画持续时间ms(默认1000)
    repeated:1,//动画重复次数(默认0)
    reversePlay:true, //动画是否反向播放是否重复播放(默认false)
    delay:1000  //动画延时多久播放ms(默认0)
})
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以播放模型位移动画。






![1](../../../../assets/images/3d_lowcode_object_gmodel_moveto1.gif)