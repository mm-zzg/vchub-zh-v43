# createModel

**描述：** 创建模型库中的模型进入场景中

```typescript
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
scene.createModel({  
     path:'models.chariot',    //模型在模型库的地址
     name:'叉车',              //创建后的名字
     position: { x: 0, y: 0, z: 0 }  //创建后的模型位置
});   
```
**示例：**

在按钮上编写上述代码，点击按钮，可以模型库中的模型进入场景中


![alt text](11.gif)

![alt text](12.png)
