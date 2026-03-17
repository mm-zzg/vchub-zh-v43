
# System.Security.login


## 描述

使用该函数可直接登录系统，以避免使用系统自带的登录页面。

## 语法
**System.Security.login(username: string, password: string): Promise`<boolean>`**

- 参数

     username 用户名

     password 密码

- 返回

    是否登录成功

## 代码示例

页面上方有一个切换用户的按钮，点击按钮打开“LoginPopup”弹框，用户输入用户名和密码登录成功后系统自动跳转到项目首页。

切换用户按钮脚本

![alt text](a_sf_ss-login1.png)

```typescript 
const result = await System.UI.openPopup('LoginPopup');
if (result === 'GoHomePage') {
    System.UI.goHome();
}


```   
LoginPopup 弹框页面登录按钮脚本

![alt text](a_sf_ss-login2.png)

```typescript 
const usernameInput = await System.UI.findControl('UsernameInput');
const passwordInput = await System.UI.findControl('PasswordInput');
const succeeded = await System.Security.login(usernameInput.text, passwordInput.text);
if (succeeded) {
    System.UI.close('GoHomePage');
}

```   


