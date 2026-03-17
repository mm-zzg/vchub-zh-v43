# Open API

WAGO SCADA Open API（开放API）是指一套允许第三方开发者在其应用程序中访问WAGO SCADA平台功能的Web API接口。WAGO SCADA通过OpenId的方式向第三方提供这些Web API接口。

![alt text](1.png)

WAGO SCADA 开放 API 遵循 RESTful风格，所有 API 路径都基于资源。考虑到 API 版本控制的需求，API 路径以版本号前缀开头。API 路径模板类似于 `api/{VersionNo}/{ResourceName}`。另外WAGO SCADA也提了 基于 WebSocket 协议的API，这些API的路径则以 'ws' 开头。

| Function Method | Http Method | Http Request Body | Http Response Body |
|:---------------------|:-----------------|:-----------------------|:------------------------|
| List                | GET             | N/A                   | Resource*list          |
| Get                 | GET             | N/A                   | Resource               |
| Create              | POST            | Resource              | Resource or Empty      |
| Update              | PUT, PATCH      | Resource              | Resource or Empty      |
| Delete              | DELETE          | N/A                   | N/A                    |

以下是一些API URL定义的示例

| URL           | Http Method| Description       |
|:--------------------|:-----------------|:------------------------|
| api/v1/assets      | GET             | Get all assets         |
| api/v1/assets      | POST            | Create new asset       |
| api/v1/assets/{id} | PUT             | Update the asset by id |
| api/v1/assets/{id} | DELETE          | Delete the asset by id |