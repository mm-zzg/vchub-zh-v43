# System.Datatable.toDatatable


## 描述

将从第三方API或者数据库获取的数据转换为数据表对象。

## 语法

**System.Datatable.toDatatable(data: Array`<any>`, headers?: Array`<string>`): Datatable**

- 参数

    data - 数据

    headers - 列名称集合，data 为二维数组时需要指定列名称

- 返回

    数据表对象

## 代码示例      

场景1：将对象数组生成为表格可以使用的数据源。

```typescript 
const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable([
    { studentId: 3, firstName: 'Charlie', lastName: 'Williams', gender: 'M', birthDate: '2000-05-30' },
    { studentId: 11, firstName: 'Kelly', lastName: 'Hernandez', gender: 'F', birthDate: '2000-01-25' },
    { studentId: 15, firstName: 'Mia', lastName: 'Gonzalez', gender: 'F', birthDate: '2001-04-06' }
]);
table1.applyChanges();
```   
场景2：将二维数组生成为表格可以使用的数据源。
```typescript 
const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable([
    [3, 'Charlie', 'Williams', 'M', '2000-05-30'],
    [11, 'Kelly', 'Hernandez', 'F', '2000-01-25'],
    [15, 'Mia', 'Gonzalez', 'F', '2001-04-06']
], ['studentId', 'firstName', 'lastName', 'gender', 'birthDate']);
table1.applyChanges();
```   
