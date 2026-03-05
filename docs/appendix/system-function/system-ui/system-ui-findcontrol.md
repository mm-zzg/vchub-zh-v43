# System.UI.findControl


## 描述

查找画面中的控件实例。

## 语法

**System.UI.findControl(name: string): any**

- 参数

    name - 要查询控件的名称，可直接通过控件名称推断控件类型

- 返回

    控件实例

## 代码示例

当锅炉温度过高时，将报警信息更新到 label1 上。

```typescript 

const label1 = await System.UI.findControl('Label1');
label1.text = '锅炉温度过高';
label1.backgroundColor = 'red';
label1.fontColor = 'white';
label1.applyChanges();
```   
