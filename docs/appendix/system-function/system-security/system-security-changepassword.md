# System.Security.changePassword


## 描述
修改当前登录用户的密码。

## 语法
**System.Security.changePassword(oldPassword:string,newPassword:string): Promise`<boolean>`**

- 参数

    oldPassword  旧密码 

    newPassword  新密码

- 返回

    是否修改成功

## 代码示例

将当前登录用户的密码由 abc123 改为 abc456。

```typescript 
const result = await System.Security.changePassword('abc123','abc456');
console.log(result);

```   
