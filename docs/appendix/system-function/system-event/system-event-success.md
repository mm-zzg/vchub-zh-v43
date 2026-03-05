# System.Event.success


## 描述

给系统事件加个成功的操作事件，可在实时事件控件或历史事件控件中查询。

## 语法

**System.Event.success(message:string,...args: any): Promise`<void>`**

- 参数 

    message - 成功事件的描述 

    args - 成功的事件的详情 

- 返回

    无

## 代码示例

添加一条成功的操作事件。

```typescript 
// 添加成功事件描述
await System.Event.success('定时关闭灯光成功');

// 添加成功事件描述及详情
await System.Event.success('定时关闭灯光成功', ['会议室','餐厅','前台','办公区域']);



```   
