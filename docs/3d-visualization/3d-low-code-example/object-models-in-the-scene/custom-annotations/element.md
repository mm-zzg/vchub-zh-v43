# element

**描述：修改自定义标注的element**

```typescript
const view = await System.UI.findControl('3D查看器1');// 获取画面中名为“3D查看器1”的3D查看器控件
const scene = await view.getScene(); // 获取3D查看器控件中的场景
let div = document.createElement('div');//创建HTML元素的容器
// 标题
let head = document.createElement('p');//创建一个段落显示标题
head.style.textAlign = 'center'; //文本居中对齐
head.style.padding = '5px'; //文本间距
head.innerHTML = 'NewHtmlMarker'; //文本内容
div.appendChild(head); //将标题添加进容器

const html = await scene.findHtml({ name: 'HTML1' });//查找模型
html.element=div;//修改div
```
 
**示例：**

在按钮上编写上述代码，点击按钮，可以修改自定义标注的element。

![1](../../../../assets/images/3d_lowcode_object_cAnnotations_element1.gif)



