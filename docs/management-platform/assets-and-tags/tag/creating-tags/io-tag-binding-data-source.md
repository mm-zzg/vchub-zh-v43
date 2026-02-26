# I/O变量绑定数据源

I/O变量可以绑定数据源，可以直接绑定一个固定的数据源路径，也可以使用参数化的方式绑定一个动态路径。

## 直接绑定

在I/O变量的新增和修改界面，点击数据源的绑定按钮, 弹出数据源绑定弹窗。

![alt text](11.png)

在弹窗中，选择一个设备，配置参数后，点击确认按钮，完成绑定。例如下图所示。

![alt text](12.png)

完成绑定后，在变量的新增和编辑窗口，可以看到具体的数据源路径信息，如下图红框所示：

![alt text](13.png)

**说明**： 
 
1. 绑定到不同的数据源，会显示不同的数据源路径参数。 

2. 数据源文本框中，=左侧表示参数名，=右侧表示参数值。可以修改参数值，不建议修改参数名，修改参数名将导致绑定路径失效。 

3. 请确保数据源输入框中，=左右两侧的内容，与配置页面字段的大小写需一致，否则可能导致数据源绑定失败。建议不要修改=左侧的参数名。

示例如下：  

数据源参数字段：  

![alt text](14.png) 

配置页面字段：  

![alt text](15.png) 

#### 数据源绑定路径参数

| **数据源类型**      | **参数**  |
|:---------------------|:-------------------|
| **OPC UA**          | - DataSourceType <br>- Path <br>- NodeId <br>- DisplayName <br>- DeviceName <br>- GroupName <br>- DataType <br>- IndexOfArrayStr         |
| **Modbus TCP**      | - DataSourceType <br>- DeviceName <br>- FrameName <br>- DataType <br>- Address <br>- Bit (Only Bool tag displays this parameter) |
| **Modbus RTU**      | - DataSourceType <br>- DeviceName <br>- FrameName <br>- DataType <br>- Address <br>- Bit (Only Bool tag displays this parameter) |
| **MQTT Native**     | - DataSourceType <br>- Tag <br>- Address <br>- DataType <br>- DeviceName <br>- GroupName <br>- NodeName  |
| **MQTT SparkplugB** | - DataSourceType <br>- Tag <br>- Address <br>- DataType <br>- DeviceName <br>- GroupName <br>- NodeName  |
| **SIEMENS S7**      | - DataSourceType <br>- DeviceName <br>- Area <br>- DbNumber <br>- DataType <br>- BitOffset <br>- CharLength <br>- AddressOffset          |
| **WAGO Protocol**   | - DataSourceType <br>- Path <br>- Tag <br>- DataType <br>- DeviceName   |

## 参数化绑定

在 **模型** 或者 **实例** 下创建的I/O变量才支持参数化绑定。在数据源文本框后面会显示设置按钮，从设置弹窗中选择需要替换的参数。

![alt text](16.png)

#### 示例：

**工厂有 10个电机，电机下具有相同的变量，唯一的区别是电机连接到不同的数据源。我们希望电机1连接到Device1, 电机2连接到Device2,...电机10连接到Device10。**

**批量创建设备请参考如下章节。**

- [批量操作Modbus TCP设备](../../../devices/modbus-tcp/batch-operation.md)

- [批量操作Modbus RTU设备](../../../devices/modbus-rtu/batch-operation.md)

- [批量操作OPC UA设备](../../../devices/opc-ua/batch-operation.md) 

- [批量操作MQTT Native设备](../../../devices/mqtt-native/batch-operation.md) 

- [批量操作MQTT SparkplugB设备](../../../devices/mqtt-sparkplugb/batch-operation.md)

- [批量操作SIEMENS S7设备](../../../devices/siemens-s7/batch-operation.md) 

- [批量操作WAGO Protocol设备](../../../devices/wago-protocol/batch-operation.md)

- [批量操作Camera设备](../../../devices/camera/batch-operation.md) 
<br>

1. 在“设备”->Modbus TCP列表中批量创建10个modbus tcp设备，名称为Device1~Device10。只有DeviceName和Host不同，其他配置相同。

2. 在“模型”页签下，新建一个模型“Motor”，该模型包含1个自定义参数“No”,表示电机编号。

    ![alt text](17.png)

3. 鼠标右击该模型，创建I/O变量 “功率”。

    ![alt text](18.png)

4. 为变量绑定一个数据源后点击数据源参数的设置按钮，显示变量所属模型“电机”的自定义参数列表。

    ![alt text](19.png)

    可以将参数值替换为模型的自定义属性，模型的自定义属性通过 {} 引用。在创建实例时使用自定义参数值替换路径中的参数。

    ![alt text](20.png)

5. 变量创建完成后。切换到“实例”页签，创建一个名为Motor的文件夹，在文件夹下使用模型“Motor”添加实例。

    ![alt text](21.png)

6. 在添加实例窗口，模型选择 **Motor,** 点击“批量实例”的设置按钮，“数量”设置10，“起始序号”设置为1。

    ![alt text](22.png)

7. 接着我们为每个实例设置自定义参数No。我们将Motor_1绑定到Device1上，所有Motor_1的No值设置为1，依次类推。

    ![alt text](23.png)

8. 设置完成，点击“确认”按钮，会在Motor目录下，生成10个实例。实例下包含相同的变量：功率。

    ![alt text](24.png)

9. 可以通过文本控件，将文本内容绑定到变量的DataSource属性上，查看路径。

    ![alt text](25.gif)

10. 最终实现了变量的批量绑定。**电机1的所有变量绑定到Device1, 电机2的所有变量绑定到Device2,...电机10的所有变量绑定到Device10。**

