# System.Function.runScript


## 描述

此方法通过函数名在系统中异步执行用户自定义函数。它提供了一种灵活的方式来调用自定义逻辑，可以选择性地传递参数数组，并返回一个 Promise，该 Promise 会解析为函数的执行结果。 

## 语法

**System.Function.runScript(name: string, args?: Array`<any>`): Promise`<any>`**

- 参数

     名称-自定义函数

     args-函数参数

- 返回值

     函数结果

## 代码示例     

查询男生名单并以表格形式显示。

```typescript 

const maleStudents = await System.Function.runScript('query-students', ['male']);  
const table1 = await System.UI.findControl('Table1'); 
table1.table = System.Datatable.toDatatable(maleStudents); 
table1.applyChanges();

```   
