# createHtmlMarker

**描述：** 根据html创建标注

```typescript
const view = await System.UI.findControl('3D查看器1')// 获取画面中名为“3D查看器1'”的3D查看器控件
const scene = await view.getScene();
let div =document.createElement('div');//创建HTML元素的容器
// 标题
let head =document.createElement('p');//创建一个段落显示标题
head.style.textAlign= 'center'; //文本居中对齐
head.style.padding = '5px'; //文本间距
head.innerHTML = 'HtmlMarker'; //文本内容
div.appendChild(head);//将标题添加进容器
const htmlMarker =scene.createHtmlMarker({
    element: div, //选择html标注
    name: "html", //创建的html标注名字
    fixed:true, //false:标注始终面向镜头  true:固定视角朝向z轴
    position:{x:0,y:10,z:0}, //创建的位置
    //parent:ThreeDlElement|null//创建的父级，默认直接添加进场景
}); 

```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以在指定位置创建 html标注

![alt text](9.gif)