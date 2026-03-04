# openFirstPersonControls

**描述：开启第一人称模式(** 操作方式: 通过键盘的W，A，S，D键， 操作视角的前进,向左,后退,向右移动; 鼠标拖动进行视角转动; 空格键进行跳跃; 查询模型并删。**)**

```typescript
const view = await System.UI.findControl('3D查看器1'); // 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene();
scene.openFirstPersonControls({
    useCollision: true, //是否开启物理碰撞(默认否)
    startCoordinate: { x: 20, y: 100, z: 20 }, //第一人称视角初始位置(默认当前摄像机位置)
    hight: 2.2, //地面高度(默认1.8)
    weight: 4 //重力(默认为1 影响跳跃)
});
```
 
**示例：**

在按钮上编写上述代码，点击按钮，从第一人称视角初始位置开始下落至指定高度。

![1](../../../assets/images/3d_lowcode_SOperation_openfirstpersoncontrols1.gif)