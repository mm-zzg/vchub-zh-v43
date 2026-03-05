

# System.Db.runSqlQuery


## 描述

执行SQL查询，实现对数据库的操作。在执行SQL查询以操作数据库之前，请先参考“[​创建SQL Query​](../../../2d-visualization/sql-query/create-sql-query.md)”章节，完成 SqlQuery 的创建。

## 语法

**System.Db.runSqlQuery(projectName: string, queryName: string, parameters?: Array<{ name: string, value: any}>): Promise`<any>`**

**System.Db.runSqlQuery(queryName: string, parameters?: Array<{ name: string, value: any}>): Promise`<any>`**

- 参数 

    projectName - 项目名称，具体使用场景请参考下方代码示例

    queryName - 查询名称       

    parameters - 查询参数列表 

- 返回 
    
    查询结果

## 代码示例     

**Query:** 查询数据库中性别为男的学生并更新 Table 控件。

```typescript 

// 场景1：执行当前项目中的sql query
const maleStudents = await System.Db.runSqlQuery('query-students', [{
    name: 'gender',
    value: 'male'
}]);

const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable(maleStudents);
table1.applyChanges();

// 场景2：执行其他项目中的sql query需指定项目名称
// 场景3：在服务脚本模块执行sql query需指定项目名称
const maleStudents = await System.Db.runSqlQuery('another-project-name', 'query-students', [{
    name: 'gender',
    value: 'male'
}]);

const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable(maleStudents);
table1.applyChanges();
```   
**Scalar Query:** 统计12岁的学生数量并更新Label控件。

```typescript 
// Scenario 1: Execute the SQL query in the current project
const count = await System.Db.runSqlQuery('number-of-students-by-age', [{
    name: 'age',
    value: 12
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = `${count} students`;
label1.applyChanges();


// 场景1：执行当前项目中的sql query
const count = await System.Db.runSqlQuery('number-of-students-by-age', [{
    name: 'age',
    value: 12
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = `${count} students`;
label1.applyChanges();

// 场景2：执行其他项目中的sql query需指定项目名称
// 场景3：在服务脚本模块执行sql query需指定项目名称
const count = await System.Db.runSqlQuery('another-project-name', 'number-of-students-by-age', [{
    name: 'age',
    value: 12
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = `${count} students`;
label1.applyChanges();

```   

**Update Query:** 更新 Thomas 的邮箱为`thomas@example.com`并更新 Label 控件。

```typescript 
// 场景1：执行当前项目中的sql query
const updatedRowCount = await System.Db.runSqlQuery('update-student-email', [{
    name: 'name',
    value: 'Thomas'
}, {
    name: 'email',
    value: 'thomas@example.com'
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = updatedRowCount == 1 ? 'update success' : 'update failed';
label1.applyChanges();

// 场景2：执行其他项目中的sql query需指定项目名称
// 场景3：在服务脚本模块执行sql query需指定项目名称
const updatedRowCount = await System.Db.runSqlQuery('another-project-name', 'update-student-email', [{
    name: 'name',
    value: 'Thomas'
}, {
    name: 'email',
    value: 'thomas@example.com'
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = updatedRowCount == 1 ? 'update success' : 'update failed';
label1.applyChanges();
```   
