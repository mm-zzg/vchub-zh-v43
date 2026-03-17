# System.Security.getRoles


## 描述

获取当前登录用户的所有角色。

## 语法

**System.Security.getRoles(): string** 

- 参数

    无 

- 返回 

    角色，多个角色用逗号隔开

## 代码示例

在文本标签上显示当前登录人的角色。

```typescript 

const roles = System.Security.getRoles();
const label = await System.UI.findControl('文本标签1');
label.text = roles;
label.applyChanges();

```   
