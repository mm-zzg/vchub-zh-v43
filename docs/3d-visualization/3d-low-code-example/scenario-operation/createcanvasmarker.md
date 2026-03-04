# createCanvasMarker

**描述：** 通过传入的canvas,创建始终面向镜头的图片标注

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1'”的3D查看器控件
const scene = await view.getScene();
const canvas=document.createElement('canvas'); //创建一个画布
const ctx=canvas.getContext('2d'); //2d渲染画布
// 设置画布背景
ctx.canvas.width = 300;
ctx.canvas.height = 100;
ctx.fillStyle = '#808000';
ctx.fillRect(0, 0, 300, 100);
// 绘制一个棕色矩形，左上角坐标为(0, 0)，宽度为300，高度为100
// 设置画布文字
ctx.font = '20px boldsans-serif';
ctx.fillStyle = '#ff0000';
ctx.fillText('这是一个canvas', 0, 20);//起点坐标0，20
scene.createCanvasMarker({
    canvas:canvas, //选择画布
    name: 'canvas', //创建图片标注的名字
    position:{x: 0, y: 10, z: 0},  //创建图片标注的位置
    size:{width:300,height:100},  //创建图片标注长宽
    //parent:ThreeDlElement|null//创建物体的父级(默认直接添加进场景)
})

```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以在指定位置创建图片标注

![alt text](4.gif)

