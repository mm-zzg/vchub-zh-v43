

# System.UI.openPopup


## 描述

打开一个弹窗画面。

## Grammar
  
**System.UI.openPopup(page: string, options: {**
      
**pageProperties?: any;**
       
**position?: { type: 'center' | 'follow' | 'custom'; left?: number; top?: number; },**
       
**titleBar?: {**
              
**title?: string;**
              
**backgroundColor?: string;** 
              
**height?: number;**
             
**position?: 'left' | 'center' | 'right';**
              
**font?: 'Microsoft YaHei' | 'SimSun' | 'SimHei' | 'Arial' | 'Calibri' | 'Source Han Sans SC' | 'Georgia' | 'Tahoma' | 'Times New Roman' | 'Trebuchet MS' | 'Verdana' | 'Digital Numbers';**
              
**fontSize?: number;**
              
**fontColor?: string;**
             
**bold?: boolean;**
              
**italic?: number;**
              
**}**

**}): Promise`<any>`**

- 参数

    page - 需要打开的弹窗名称

    options - {

    pageProperties - 画面属性

    position - {

    type - 弹窗属性 center 屏幕中央、follow 跟随鼠标、custom 用户自定义，

    letft - 仅 type 为 custom 时需要填写，不填默认 0，

    top - 仅 type 为 custom 时需要填写，不填默认 0

    }

    titleBar - {

    title - 标题，

    backgroundColor - 标题栏背景色，

    height - 标题栏高度,

    position - 标题位置：左、中、右，

    font - 标题字体，

    fontSize - 标题字体大小，

    fontColor - 标题字体颜色，

    bold - 标题是否加粗，

    italic - 标题是否斜体

    }

}

- 返回

    等待弹框关闭时获取返回值

## 代码示例

**场景1：打开弹框，不等待弹框关闭**

在画面居中的位置打开名称为“详情”的弹窗，修改弹框标题为“A0003详情”，并设置弹框页面属性 id 为“A0003”。

```typescript 
System.UI.openPopup('详情', {
    pageProperties:{
      custom: {
          id: "A0003"
      }
    },
    position:{
        type: "center"
    },
    titleBar:{
        title: "A0003详情"
    }
});
```
**场景2：打开弹框，等待弹框关闭**

在画面左边距 200 上边距 200 的位置打开名称为“添加维保记录”的弹窗，修改弹框标题为“维保详情”，并设置弹框页面属性 user 为“User005”、logDate 为当前日期，待弹框关闭后跳转到“维保记录列表”页面。
 
```typescript
const addResult  = await System.UI.openPopup('添加维保记录', {
    pageProperties:{
      custom: {
          user: "User005",
          logDate: new Date().toLocaleDateString()
      }
    },
    position:{
        type: "custom",
        left: 200,
        top: 200,
    },
    titleBar:{
        title: "维保详情"
    }
});

if(addResult === 'done'){
    System.UI.open('维保记录列表');
}
```
在“添加维保记录”的弹窗页面，保存数据后将页面关闭并发送通知给 openPopup 函数。
```typescript
//TODO (用户自行保存维保记录到数据库)

System.UI.close('done');
```
