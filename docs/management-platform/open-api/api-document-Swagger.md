# API 文档(Swagger)

在浏览器中输入 WAGO SCADA 主机地址并加上后缀 “swagger”（例如：https://example.com/swagger, http://localhost:8066/swagger），将会导航到 Open API 文档页面。该页面列出了所有WAGO SCADA的Open API 定义。

![alt text](2.png)

我们可以通过 Swagger 调用和测试这些Open API

1. 点击“授权”按钮以输入访问令牌。有关访问令牌的信息，请参考 [Open Id Connect](open-id-connect.md) 部分。请注意，输入访问令牌时，访问令牌应格式化为“Bearer {access_token}”。

    ![alt text](3.png)

    ![alt text](4.png)

2. 点击箭头展开API详情

    ![alt text](5.png)

    ![alt text](6.png)

3. 点击 “Try it out”, 然后点击 “Execute” 调用API

    ![alt text](7.png)

    ![alt text](8.png)

4. 服务端返回API的结果

    ![alt text](9.png)

## 如何指定返回的语言？

在调用 API 时，请在 HTTP 请求头（Headers）中添加如下字段：`Accept-Language: zh-CN` 或 `Accept-Language: en-US`

当您调用 API 时，系统将按以下优先级顺序决定响应语言：

1. **Accept-Language header**：若传入 `zh-CN` 或 `en-US`，系统将严格按此返回对应语言内容。

2. **用户会话 Cookie**：若未设置 Accept-Language ，系统将读取当前用户会话 Cookie 中的语言标识（如 `lang=en-US`）作为响应语言。

3. **默认语言**：若以上两者均为空或无效，系统将默认使用英文（`en-US`）作为响应语言。

**支持的语言：**

- `zh-CN`：简体中文
- `en-US`：美式英语

**示例**：应用同时面向中国和美国用户。假设您需要获取某个用户的详细信息，为了避免因语言差异造成的沟通障碍，当 API 调用失败时，系统会根据用户的语言偏好返回相应的错误信息。

**中国用户访问：**

```json
GET api/v1/user/999
Accept-Language: zh-CN
```
 
**返回:** 

```json
{
  "message": "用户不存在"
}
```
 
**美国用户访问：**

```json
GET api/v1/user/999
Accept-Language: en-US
```
 
**返回：**

```json
{
  "message": "User does not exist"
}
```
 
