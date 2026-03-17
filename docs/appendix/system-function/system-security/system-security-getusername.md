

# System.Security.getUsername


## 描述

获取当前登录用户的用户名。

## 语法
**System.Security.getUsername(): string**

- 参数

    无

- 返回

    用户名

## 代码示例

在文本标签上显示当前登录人的用户名。

```typescript 

const user = System.Security.getUsername();
const label = await System.UI.findControl('文本标签1');
label.text = user;
label.applyChanges();

```   
