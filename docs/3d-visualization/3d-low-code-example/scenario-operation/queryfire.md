# queryFire

**描述：** 查询场景中符合条件的全部火特效

查询火：

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
const mash = await scene.queryFire('fire') //查询名字包含fire的特效
console.log(mash) //输出所有查询到的结果
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以查询场景中名字包含 fire 的火特效

![1](../../../assets/images/3d_lowcode_SOperation_queryfire1.gif)

查询到的模型可以使用其所有方法和属性：

![alt text](3d_lowcode_SOperation_queryfire2.png)




