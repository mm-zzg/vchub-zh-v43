# System.Utils.importScript


## 描述

导入一份 js 文件。

## 语法

**System.Utils.importScript(scriptFileUrl: string): Promise`<void>`** 

- 参数

    scriptFileUrl - 脚本文件路径

- 返回

    无

## 代码示例

使用 vue+element-ui 创建一个表格。

```typescript 
await System.Utils.importStyle('https://unpkg.com/element-ui/lib/theme-chalk/index.css');
await System.Utils.importScript('https://unpkg.com/vue@2/dist/vue.js');
await System.Utils.importScript('https://unpkg.com/element-ui/lib/index.js');
document.body.innerHTML = `<div id='app'>
    <el-table
      :data="tableData"
      style="width: 500px">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
    </el-table>
</div>`;
 
// @ts-ignore
new Vue({
    el: '#app',
    data: function () {
        return {
            tableData: [{
                date: '2016-05-02',
                name: 'WAGO SCADA',
                address: '上海市普陀区金沙江路 1518'
            }, {
                date: '2016-05-04',
                name: 'WAGO SCADA',
                address: '上海市普陀区金沙江路 1517'
            }, {
                date: '2016-05-01',
                name: 'WAGO SCADA',
                address: '上海市普陀区金沙江路 1519'
            }, {
                date: '2016-05-03',
                name: 'WAGO SCADA',
                address: '上海市普陀区金沙江路 1516'
            }]
        }
    }
});
```  
