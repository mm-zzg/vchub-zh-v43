# 常见OPC UA Server测试报告

我们使用以下常见的OPC UA Server，测试其和WAGO VC Hub中的OPC UA驱动之间的通信。

## OPC UA Server

1. Prosys： v5.5.0-341
2. Softing： v1.46.0.7428
3. Matrikon： v1.9.0.8629

## 测试结果

#### 1.支持通过安全连接方式进行连接

|          | 用户名密码 | 安全连接 |
|----------|:------------|:----------|
| Prosys   | Y          | Y        |
| Softing  | Y          | Y        |
| Matrikon | Y          | Y        |

#### 2.WAGO  VC Hub支持OPC UA Server的以下数据类型

|                 | Prosys | Softing | Matrikon |
|-----------------|:--------|:---------|:----------|
| Byte            | 读/写  | 读/写   | 读/写    |
| SByte           | 读/写  | 读/写   | 读/写    |
| Int16           | 读/写  | 读/写   | 读/写    |
| Int32           | 读/写  | 读/写   | 读/写    |
| Int64           | 读/写  | 读/写   | 读/写    |
| UInt16          | 读/写  | 读/写   | 读/写    |
| UInt32          | 读/写  | 读/写   | 读/写    |
| UInt64          | 读/写  | 读/写   | 读/写    |
| Float           | 读/写  | 读/写   | 读/写    |
| Double          | 读/写  | 读/写   | 读/写    |
| String          | 读/写  | 读/写   | 读/写    |
| Boolean         | 读/写  | 读/写   | 读/写    |
| DateTime        | 读/写  | 读/写   | 读/写    |
| Guid            | 读     | 读      | 读       |
| ByteString      | 读     | 读      | 读       |
| XmlElement      | 读     | 读      | 读       |
| NodeId          | 读     | 读      | 读       |
| ExpandedNodeId  | 读     | 读      | 读       |
| StatusCode      | 读     | 读      | 读       |
| QualifiedName   | 读     | 读      | 读       |
| LocalizedText   | 读     | 读      | 读       |
| ExtensionObject | 读     | 读      | 读       |
| DataValue       | 读     | 读      | 读       |
| Variant         | 读     | 读      | 读       |
| Number          | 读/写  | 读/写   | 读/写    |
| Integer         | 读/写  | 读/写   | 读/写    |
| UInteger        | 读/写  | 读/写   | 读/写    |
| Enumeration     | 读/写  | 读/写   | 读/写    |
| 一维数组        | 读/写  | 读/写   | 读/写    |

