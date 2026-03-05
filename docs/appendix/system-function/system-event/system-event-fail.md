
# System.Event.fail


## 描述

给系统事件加个失败的操作事件，可在实时事件控件或历史事件控件中查询。

## 语法

**System.Event.fail(message:string,...args: any): Promise`<void>`**

- 参数

    message - 失败事件的描述 

    args - 失败事件的详情 

- 返回 

    无

Nothing

## 代码示例  

添加一条失败的操作事件。

```typescript 

// 添加失败事件描述
await System.Event.fail('定时关闭灯光失败');

// 添加失败事件描述及详情
await System.Event.fail('定时关闭灯光失败', ['会议室','餐厅','前台','办公区域']);

```  
