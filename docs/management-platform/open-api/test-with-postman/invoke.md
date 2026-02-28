# 调用HTTPS接口

Open API通过HTTPS协议提供Web API，默认的HTTPS端口设置为8043。

1. 在Postman中创建针对Open API的HTTP请求之前，请先浏览Swagger文档页面上的API定义。关于如何打开，Swagger页面可以参考 [API 文档(Swagger)](../api-document(Swagger).md)。关于API的定义也可以参考 [资产接口定义](../asset-api-definitions.md)，[历史数据接口定义](../historical-data-api-definitions.md)，[实时数据接口定义](../realtime-data-api-definitions.md)。

    ![alt text](7.png)

2. 在postman中新建请求，并根据API列表中的API定义输入地址和方法

    ![alt text](8.png)

3. 打开“Authorization”选项卡，从“Auth Type”下拉列表中选择“Bearer Token”，然后在“Token”文本框中输入访问令牌。

    ![alt text](9.png)

4. 点击“Send”按钮，API将返回带有成功状态码的响应。

    ![alt text](10.png)



