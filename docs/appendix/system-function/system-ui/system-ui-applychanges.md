# System.UI.applyChanges


## 描述

批量应用控件属性的修改。

## 语法
**System.UI.applyChanges(controls: Array`<IControl>`, triggerLoadedEvent?: boolean): void**

- 参数

     controls - 需要使修改过属性生效的控件

     triggerLoadedEvent - 是否触发加载事件，可不填默认 false

- 返回

     无

## 代码示例

当锅炉温度过高时，将报警信息显示到 label1 上，将降温信息显示到 label2 上。

```typescript 
const label1 = await System.UI.findControl('Label1');
label1.text = '锅炉温度过高';
label1.backgroundColor = 'red';
label1.fontColor = 'white';

const label2 = await System.UI.findControl('Label2');
label2.text = '降温中...';

System.UI.applyChanges([label1, label2], false);
```   
