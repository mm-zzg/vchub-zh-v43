# WAGO Protocol

WAGO VC Hub中的WAGO Protocol驱动支持与WAGO PLC的基本连接。系统自带一个MQTT Broker，支持用户通过系统提供的账户和密码连接，并通过WAGO Protocol驱动进行数据通信。

支持WAGO Protocol 1.5.0版本。

#### 驱动连接到WAGO Protocol

1. 在”**设备**“->”**WAGO Protocol**“页面，点击“**新增**”按钮。
2. 在新增页面中输入**设备名称**。

![alt text](1.png)

3. 点击**“确认”**按钮。此时该条数据将显示在WAGO Protocol的设备列表页面。请注意状态一栏，仅表示驱动程序的启停状态，并不代表和设备的真正连接状态。

![alt text](2.png)

#### 配置字段

| **名称** | **描述**                                      |
|----------|-----------------------------------------------|
| 设备名称 | 设备名称，在设备列表中唯一。                    |
| 用户名   | 用于与某设备连接的账号，系统自动生成，不可修改。 |
| 密码     | 用于与某设备连接的密码，系统自动生成，支持重置。 |

#### 注意事项

1. 请妥善保管用户名和密码信息，避免泄露给未授权人员，如果发生泄露，请及时重置密码。
2. **全部启用**和**全部禁用**，是对列表中的所有数据进行启用或禁用。

#### 连接到系统MQTT Broker

在使用WAGO Protocol驱动之前，您需要先连接上MQTT Borker。请按照以下步骤进行连接：

1. 获取账户和密码：点击设备的"**查看**"按钮，可以看到系统提供的用户名和密码。
2. 配置Cloud Connectivity

   - 使用网络浏览器打开您WAGO设备的WBM（Web-based Management，基于Web的管理工具）。
   - 输入**Username**和**Password**，以便在PFC上进行身份验证。点击**Submit**。
   - 在**Configuration**下选择**Cloud Connectivity**菜单项，点击**Connection1**。
   - 在右侧的配置中，勾选**Enabled**，启用当前连接**。**
   - 从**Cloud platform**下拉列表中选择**MQTT AnyCloud。**
   - 在**Hostname**字段中输入您的WAGO VC Hub程序发布的IP地址。
   - 在**Port**字段中输入1884。
   - 在**Client ID**中输入设备标识，**需和上述WAGO Protocol设备列表中新增的设备名称保持一致**，用于在 MQTT Server 上标识您的连接。
   - 勾选**Clean session**，启用清除会话。
   - 在**User**中输入连接MQTT Server的用户名，**使用上述WAGO Protocol设备列表中新增的设备信息中的用户名。**
   - 在**Password**输入输入连接MQTT Server的密码，**使用上述WAGO Protocol设备列表中新增的设备信息中的密码。**
   - 在**Data protocol**下拉列表中选择WAGO Protocol 1.5。
   - 点击**Submit**，并重启设备。
   - 稍等片刻后在WBM的**Cloud Connectivity**下检查连接状态，Cloud connection则会显示connected。
**注意**：请不要勾选**Use Compression**，因为这会导致WAGO Protocol驱动无法正常处理数据；另外对于上述列表中其他未提及的字段，虽然勾选这些项目不会影响WAGO VC Hub的功能使用，但WAGO VC Hub尚未实现相应的功能。

3. 连接到 MQTT Server：确认连接成功后，便可以开始使用配置的客户端与WAGO Protocol驱动进行设备数据的传输。

![alt text](3.png)

#### 启用TLS安全连接

WAGO VC Hub程序支持与WAGO PLC设备通过TLS协议建立安全连接。

配置客户端：修改WAGO PLC设备配置页面的连接配置。

   - **Port number**：修改为3883。
   - **TLS**：选择开启。
   - **CA File**：填写路径，/etc/ssl/certs/ server-cert.pem。
   -  获取服务器证书：登录到 PLC 系统并执行命令  openssl s_client -connect **[server IP]** :3883 -showcerts </dev/null 2>/dev/null |openssl x509 -outform PEM > /etc/ssl/certs/server-cert.pem
__*__ __将__ __[server IP]__ __替换成__ __WAGO VC Hub__ __所部署的服务器__ __IP__
![alt text](4.png)



#### 发布和订阅设备数据

参考**WAGO Messaging Protocol**协议,官方文档 [https://www.wago.com.cn/cn/d/15719](https://www.wago.com.cn/cn/d/15719)。

#### 与变量绑定

将变量与客户端测点进行绑定。

1. 创建一个I/O变量。

![alt text](5.png)

2. 在变量的编辑界面，点击数据源的**设置**按钮。

![alt text](6.png)

3. 选择需要绑定的测点。

![alt text](7.png)

4. 点击“**确认**”按钮，完成配置。

#### WAGO Protocal PLC程序Command请求及响应处理

配置PLC Command:

```typescript
//配置Command0接收三个string参数,回复三个string参数		
aCommandDescriptions[0].bCommandId := 0; // The command Id must be unique
aCommandDescriptions[0].bNumberOfRequestParameters := 3;
aCommandDescriptions[0].bNumberOfResponseParameters := 3;
aCommandDescriptions[0].sName := 'WriteValue';

//配置Command0接收的参数名和类型
aCommandDescriptions[0].aRequestParameters[0].sParameterName := 'Name'; //第一个参数为变量名
aCommandDescriptions[0].aRequestParameters[0].eParameterType := WagoAppCloud.eCommandParameterType.CPT_STRING;
aCommandDescriptions[0].aRequestParameters[1].sParameterName := 'Value'; //第二个参数为变量值
aCommandDescriptions[0].aRequestParameters[1].eParameterType := WagoAppCloud.eCommandParameterType.CPT_STRING;
aCommandDescriptions[0].aRequestParameters[2].sParameterName := 'RequestId'; //第三个参数为请求ID
aCommandDescriptions[0].aRequestParameters[2].eParameterType := WagoAppCloud.eCommandParameterType.CPT_STRING;

//配置Command0回复的参数名和类型
aCommandDescriptions[0].aResponseParameters[0].sParameterName := 'Name'; //第一个参数为变量名
aCommandDescriptions[0].aResponseParameters[0].eParameterType := WagoAppCloud.eCommandParameterType.CPT_STRING;
aCommandDescriptions[0].aResponseParameters[1].sParameterName := 'Success'; //第二个参数为是否成功
aCommandDescriptions[0].aResponseParameters[1].eParameterType := WagoAppCloud.eCommandParameterType.CPT_STRING;
aCommandDescriptions[0].aResponseParameters[2].sParameterName := 'RequestId'; //第三个参数为请求ID
aCommandDescriptions[0].aResponseParameters[2].eParameterType := WagoAppCloud.eCommandParameterType.CPT_STRING;
```
 
响应处理：

```typescript
IF xCommandReceived THEN //收到Command之后xCommandReceived为True
	dwReceivedCmdId := IncomingCommand.dwCommandId; //获取CommandId
	CASE dwReceivedCmdId OF //判断CommandId
		0:
			response.dwCommandId:= dwReceivedCmdId; //reponseId与ReceivedId保持一致
			response.bNumberOfResponseParameters := 3; //设置回复参数为3
			response.dwInvokeId := IncomingCommand.dwInvokeId; //设置回复调用Id  
//设置三个回复参数类型	              
response.aResponseParameters[0].eParameterType:=aCommandDescriptions[0].aResponseParameters[0].eParameterType; 
response.aResponseParameters[1].eParameterType:=aCommandDescriptions[0].aResponseParameters[1].eParameterType;			
response.aResponseParameters[2].eParameterType:=aCommandDescriptions[0].aResponseParameters[2].eParameterType;	
//设置三个回复参数名字			
response.aResponseParameters[0].sParameterName:=aCommandDescriptions[0].aResponseParameters[0].sParameterName;		
response.aResponseParameters[1].sParameterName:=aCommandDescriptions[0].aResponseParameters[1].sParameterName;			
response.aResponseParameters[2].sParameterName:=aCommandDescriptions[0].aResponseParameters[2].sParameterName;
//设置三个回复参数默认值	
response.aResponseParameters[0].sParameterValue := IncomingCommand.aRequestParameters[0].sParameterValue;//请求和回复变量名保持一致
response.aResponseParameters[1].sParameterValue :=BOOL_TO_STRING(FALSE);//默认Command执行失败	
response.aResponseParameters[2].sParameterValue:=IncomingCommand.aRequestParameters[2].sParameterValue;//请求和回复请求ID保持一致
			FOR index:=0 TO 9 BY 1 DO //循环判断写值变量名与PLC变量名是否一致
				IF(Publish.aTagConfiguration0[index].sTag=Name) THEN //一致则写值
Publish.xVariable[index]:=STRING_TO_BOOL(IncomingCommand.aRequestParameters[1].sParameterValue);
				   response.aResponseParameters[1].sParameterValue :=BOOL_TO_STRING(TRUE);//写值成功
				   EXIT;//退出循环
				END_IF
			END_FOR
			xResponseTrigger := TRUE;//回复
	END_CASE
END_IF
```
 


