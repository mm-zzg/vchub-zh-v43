# canvas

**描述：修改canvas**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
const canvas = await scene.findCanvas({ name: 'Canvas' });//查找模型
const canvas2=document.createElement('canvas'); //创建一个画布
const ctx=canvas2.getContext('2d'); //2d渲染画布
// 设置画布背景
ctx.canvas.width = 300;
ctx.canvas.height = 100;
ctx.fillStyle = '#6ec800';
ctx.fillRect(0, 0, 300, 100);
// 绘制一个棕色矩形，左上角坐标为(0, 0)，宽度为300，高度为100
// 设置画布文字
ctx.font = '20px bold sans-serif';
ctx.fillStyle = '#ff0000';
ctx.fillText('这是一个canvas', 0, 20);//起点坐标0，20
canvas.canvas=canvas2;//修改canvas属性
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改canvas。


![1](../../../../assets/images/3d_lowcode_object_overlays_canvas1.gif)
