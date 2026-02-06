# 自定义登录页面

如果用户不希望使用WAGO VC Hub的默认登录页面，可以自行在项目上配置一个登录画面。该登录画面，在用户访问运行画面，需要登录验证时显示。

您可以对每个项目单独设置登录画面。

#### 自定义一个登录画面

1. 在编辑器中组态一个画面，该画面将作为运行时的登录页。例如下图所示：包含用户名，密码输入框，登录按钮。

![alt text](5.png)

2. 为登录按钮设置执行脚本。点击登录按钮时，获取用户名和密码输入框的值，用于登录校验。 

![alt text](6.png)

```typescript
const username = await System.UI.findControl('文本输入框1')
const password = await System.UI.findControl('文本输入框2')
// 执行登录
const loginSuccess = await System.Security.login(username.text, password.text)
// 登录成功，跳转启动画面
if (loginSuccess) System.UI.redirect('#/runtime/yuan/Start', false)
```
 
| **说明：**此处脚本仅是示例，您可以根据您的需求，灵活编辑脚本。 |
|------------------------------------------------------------|

#### 为项目配置登录画面

1. 在编辑器中，点击项目右上角的设置按钮，打开项目管理弹窗。
2. 为项目设置启动画面及登录画面。如果未选择登录画面，则在访问运行页面时将使用WAGO VC Hub自带的登录画面进行登录。
3. 配置完成后，点击确定按钮，保存配置。

![alt text](7.png)

#### 访问项目运行画面

**场景1：当前启用的Identity Provider为Local 类型，项目上配置了登录画面，项目未开启自动登录。**

用户访问该项目的运行画面时，会显示自定义的登录画面，在该画面完成登录后，查看运行画面。

**场景2：当前启用的Identity Provider为Local 类型，项目上配置了登录画面，且项目开启了自动登录。**

用户访问该项目的运行画面时，不会显示自定义的登录画面，直接显示运行画面。

**场景3：当前启用的Identity Provider为OpenID Connect类型，项目上配置了登录画面。**

用户访问该项目的运行画面时，不会显示自定义的登录画面，而是显示Identity Provider对应的第三方系统的登录画面。

**场景4：当前启用的Identity Provider为OpenID Connect类型，项目未配置登录画面。**

用户访问该项目的运行画面时，不会显示自定义的登录画面，而是显示Identity Provider对应的第三方系统的登录画面。

#### 退出运行画面

**场景1：当前启用的Identity Provider为Local 类型，项目上配置了登录画面。**

用户退出，会退至项目上设置的登录画面。

**场景2：当前启用的Identity Provider为Local 类型，项目上未配置登录画面。**

用户退出，会退至WAGO VC Hub自带的登录画面。

**场景3：当前启用的Identity Provider为OpenID Connect类型，项目上未配置登录画面。**

用户退出，会退至Identity Provider对应的第三方系统的登录画面。

**场景4：当前启用的Identity Provider为OpenID Connect类型，项目上配置了登录画面。**

用户退出，会退至Identity Provider对应的第三方系统的登录画面。