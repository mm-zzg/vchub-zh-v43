# MQTT Native

WAGO VC Hub中的MQTT Native驱动程序基于MQTT协议设计和开发，支持满足MQTT协议的报文信息传输。同时系统自带一个MQTT Broker，支持用户通过系统提供的账户和密码连接，并通过MQTT Native驱动进行数据通信。

#### 驱动连接到MQTT Broker

1. 在”**设备**“->”**MQTT Native**“页面，点击“**新增组**”按钮。

**组**：组是用于组织设备的一种方式，通过将设备组织成组，可以更方便地进行管理和操作。

2. 在新增页面中输入**组名**。

![alt text](1.png)

3. 点击**“确认”**按钮。此时该条数据将显示在MQTT Native的设备列表页面。

![alt text](2.png)

4. 在操作一栏中点击“**添加节点**”，输入节点名称，为当前组添加一个新的节点。

**节点**：节点代表具体设备的实体，具有唯一标识符，用于区分各个设备。

![alt text](3.png)

   1. 点击**“确认”**按钮。此时该条数据将显示在当前组的节点列表页面。 
![alt text](4.png)

5. 在启用状态一栏点击启用按钮，启用该节点。

![alt text](5.png)

**配置字段**

| **名称** | **描述**                                      |
|----------|-----------------------------------------------|
| 组名称   | 驱动的组名称，在驱动列表中唯一。                |
| 节点名称 | 组的某个节点名称，在组中唯一。                  |
| 用户名   | 用于与某节点连接的账号，系统自动生成，不可修改。 |
| 密码     | 用于与某节点连接的密码，系统自动生成，支持重置。 |

###### 注意事项

1. 节点列表中，**启用状态**表示设备是否已被启用，未启用的设备不会进行连接，启用的设备会尝试进行连接。
2. **全部启用**和**全部禁用**，是对列表中的所有数据进行启用或禁用。
3. 请妥善保管用户名和密码信息，避免泄露给未授权人员，如果发生泄露，请及时重置密码。

#### 连接MQTT Broker

在使用 MQTT Native 驱动程序之前，您需要先连接到系统的 MQTT Broker。请按照以下步骤进行连接：

1. 获取账户和密码：点击节点的**“查看”**按钮，可以看到系统提供的用户名和密码。
2. 配置客户端：在您的应用程序或设备中，配置 MQTT 客户端以连接到系统的 MQTT Broker：

   - Broker 地址：填写系统 MQTT Broker 的地址。
   - Broker 端口：填写系统 MQTT Broker 的端口号。默认为 1884。
   - 客户端 ID：填写一个唯一的客户端标识符，用于在 MQTT Broker 上标识您的连接。
   - 用户名和密码：使用您获取到的账户和密码。
3. 连接到 MQTT Broker：使用 MQTT 客户端，在应用程序或设备中连接到系统的 MQTT Broker。确认连接成功后，便可以开始使用配置的客户端与MQTT Native驱动程序进行设备数据的传输。

#### 发布和订阅设备数据

MQTT Native驱动基于MQTT协议设计和开发，接入驱动的MQTT客户端发送的报文Topic需要遵循如下结构：

**主题：Topic**

**wsV1.0/group_name/message_type/node_name/[device_name]**

| **元素**     | **描述**                                                                                                                                                                                                                          |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ws1.0        | 根元素，为固定内容。                                                                                                                                                                                                                |
| group_name   | 此元素是对客户端的逻辑分组标识，对应系统中的**组名称** ，它可以按照逻辑或者实际使用要求进行分组，比如区分A/B 车间、a/b 产线等。此元素可以是任意合法的字符串，但不能包含特殊字符，比如*/+# 等，并且内容尽可能短。                           |
| message_type | 此元素说明该如何处理payload 信息。  系统 定义如下message_type ：  1. **NBIRTH** –  设备测点信息，可初始化某Node 下所有设备信息和测点信息 2. **NDATA** –  测点数据，发送某设备下测点数据 3. **NCMD** –  测点命令，回写某设备下测点数据  |
| node_name    | 此元素是客户端唯一标志，对应系统中的**节点名称** 。此元素可以是任意合法的字符串，但不能包含特殊字符，比如 */+# 等，并且尽可能短。                                                                                                       |
| device_name  | **[可选]** 此元素是设备的唯一标识，它可以是任意关联到节点的物理或逻辑设备。此元素是可选的，客户端可通过此元素将消息发送给指定设备。不同节点下的device_name 可以重复，且可以是任意合法字符，但不能包含特殊字符，比如*/+# 等，并且尽可能短。 |

**message_type详细解释**

1. **NBIRTH** –  传输设备配置信息

Topic ：wsV1.0/group_name/**NBIRTH**/node_name

 当成功接入 VC Hub 后，客户端可以通过此 Topic 将当前 node_name 下的所有设备配置信息和测点配置信息推送给系统。

2. **NDATA** –  传输测点数据

Topic ：wsV1.0/group_name/**NDATA**/node_name/[device_name]

 当成功推送测点配置信息后，客户端可以通过此 Topic 将测点数据推送给系统。

3. **NCMD** –  回传测点数据

Topic ：wsV1.0/group_name/**NCMD**/node_name/device_name

 当客户端需要并且允许某些测点可以接收来自系统下发的值时，客户端可通过订阅此 Topic 来接收数据。

**payload结构**

1. Topic ：wsV1.0/group_name/NBIRTH/node_name

payload结构

| **属性**       | **类型** | **描述**      |
|----------------|----------|---------------|
| DeviceName     | String   | 设备名称      |
| Tags           | 集合     | 测点信息      |
| Name           | String   | 测点名称      |
| Description    | String   | 测点描述      |
| Address        | ulong    | 测点地址/别名 |
| **  **DataType | integer  | 测点数据类型  |

**Name** 可以是测点的名称，也可以是测点的路径。当需要对测点进行分组归类的时候，可以按照以下格式，如：**”Name”:”first/second/testTag”** ，即可将testTag测点归属于second目录，同时second归属于first目录。

**DataType**集合如下

| 值 | **类型** | **说明**       |
|----|----------|----------------|
| 0  | Unknown  | 未知的数据类型 |
| 1  | Int8     | 8位有符号整数  |
| 2  | Int16    | 16位有符号整数 |
| 3  | Int32    | 32位有符号整数 |
| 4  | Int64    | 64位有符号整数 |
| 5  | UInt8    | 8位无符号整数  |
| 6  | UInt16   | 16位无符号整数 |
| 7  | UInt32   | 32位无符号整数 |
| 8  | UInt64   | 64位无符号整数 |
| 9  | Float    | 单精度浮点数   |
| 10 | Double   | 双精度浮点数   |
| 11 | Boolean  | 布尔值         |
| 12 | String   | 字符串         |
| 13 | DateTime | 日期           |

报文示例：

```json
[
    {
        "DeviceName": "Device1",
        "Tags": [
            {
                "Name": "Temp",
                "Description": "Temperature",
                "Address": 1,
                "Value": 35,
                "DataType": 1
            },
            {
                "Name": "Voltage",
                "Description": "Voltage",
                "Address": 2,
                "Value": 10,
                "DataType": 1
            }
        ]
    },
    {
        "DeviceName": "Device2",
        "Tags": [
            {
                "Name": "Temp",
                "Description": "Temperature",
                "Address": 1,
                "Value": 35,
                "DataType": 1
            },
            {
                "Name": "FolderA/Items/TagA",
                "Description": "TagA",
                "Address": 2,
                "Value": 35,
                "DataType": 1
            }
        ]
    }
]

```
 


2. Topic ：wsV1.0/group_name/NDATA/node_name/[device_name]

payload结构

| **属性**  | **类型** | **描述**         |
|-----------|----------|------------------|
| Name      | string   | 测点的名称/ 路径 |
| Value     | string   | 测点值           |
| Timestamp | int      | 测点时间戳       |

报文示例：



```json
{
    "Tags": [
        {
            "Name": "Temp",
            "Value": 45,
            "Timestamp": 1687858118
        },
        {
            "Name": "Voltage",
            "Value": 10,
            "Timestamp": 1687858118
        }
    ]
}
```
 


 考虑到节约带宽和提高传输性能，所有测点的时间戳可以单独用一个属性表示，优先使用测点的 Timestamp ，若测点不存在 Timestamp ，则使用顶层对象的 Timestamp， 以下是一个例子：

```json
{
	"Timestamp": 1687858118,
	"Tags": [{
			"Name": "Temp",
			"Value": 45
		},
		{
			"Name": "Voltage",
			"Value": 10
		}
	]
}
```
 




3. Topic ：wsV1.0/group_name/NCMD/node_name/device_name

payload结构：

| **属性** | **类型** | **描述**         |
|----------|----------|------------------|
| Name     | string   | 测点的名称/ 路径 |
| Value    | string   | 测点值           |

报文示例：

```json
{"Name":"Voltage","Value":120}
```
 


#### 与变量绑定

将变量与客户端测点进行绑定。

1. 创建一个I/O变量。

![alt text](6.png)

2. 在变量的编辑界面，点击数据源的**设置**按钮。

![alt text](7.png)

3. 选择需要绑定的组、节点、设备和目录，并勾选数据类型匹配的测点。

![alt text](8.png)

4. 点击“**确认**”按钮，完成配置。

