# on

**描述：订阅鼠标或者键盘事件(** 鼠标事件支持: 'click' | 'mousedown' | 'mouseup' | 'mouseout' |'mouseover' 键盘事件支持: 'keydown' | 'keyup'**)**

```typescript
//on按钮中脚本
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();//获取场景
const chariot = await scene.findMesh({ name: 'chariot' });//查找模型
if(!chariot.userData?.off)//判断是否已经订阅过点击事件
{
    const off=chariot.on('click',()=>{console.log(123)});//绑定click事件,返回取消事件的函数
    chariot.userData={off};//在userData保存off函数  
}


//off按钮中脚本
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();//获取场景
const chariot = await scene.findMesh({ name: 'chariot' });//查找模型
if(chariot.userData.off)//判断是否订阅事件
{
    chariot.userData.off();//取消订阅
}
```
 
**示例：**

在按钮上编写上述代码，点击on按钮，订阅click事件，点击off按钮取消订阅。

![1](../../../assets/images/3d_lowcode_SOperation_on1.gif)





