# 设备

WAGO SCADA 支持多种通讯协议，对于不同的硬件设施，只需为其配置相应的通信驱动程序即可。

要快速连接到您的一台设备，请点击 WAGO SCADA 的“**设备**”菜单，选择要添加的设备类型。

#### 支持的设备类型

- [Modbus TCP](modbus-tcp/index.md)
- [Modbus RTU](modbus-rtu/index.md)
- [OPC UA](opc-ua/index.md)
- [MQTT Native](mqtt-native/index.md)
- [MQTT SparkplugB](mqtt-sparkplugb/index.md)
- [SIEMENS S7](siemens-s7/index.md)
- [WAGO Protocol](wago-protocol/index.md)
- [Camera](camera/index.md)

![alt text](1.png)

#### 如何从我的 PLC 获取数据？

将数据从 PLC 接入 WAGO SCADA 的过程分为两步：

1. 添加设备。

2. 在编辑器的资产窗口中添加I/O变量。请参阅 [创建变量](../assets-and-tags/tag/creating-tags/index.md) 页面。

3. 为变量绑定数据源，在数据源中选择步骤1中添加的设备。请参阅 [I/O变量绑定数据源](../assets-and-tags/tag/creating-tags/io-tag-binding-data-source.md) 页面。

    ![alt text](2.png)






