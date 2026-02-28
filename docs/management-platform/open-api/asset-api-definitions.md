# 资产接口定义

## GET /api/v1/assets

读取所有资产树 

协议: Https

请求负载: NA 

响应负载(JsonArray):

| 名称        | 类型   | 描述       |
|:-------------|:--------|:------------|
| id          | String | 资产树编号 |
| name        | String | 资产树名称 |
| description | String | 资产树描述 |

## POST /api/v1/assets

创建资产树

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述       |
|:-------------|:--------|:------------|
| name        | String | 资产树名称 |
| description | String | 资产树描述 |

响应负载: NA

## PUT /api/assets/{id}

更新资产树 

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述       |
|:-------------|:--------|:------------|
| name        | String | 资产树名称 |
| description | String | 资产树描述 |

Response Body: NA

## DELETE /api/v1/assets/{id}

删除资产树

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述       |
|:-------------|:--------|:------------|
| name        | String | 资产树名称 |
| description | String | 资产树描述 |

Response Body: NA

## GET /api/v1/assetModels

读取所有资产模型

协议: Https

请求负载(QueryString):

| 名称       | 类型   | 描述   |
|:------------|:--------|:--------|
| parentPath | String | 父路径 |

响应负载(JsonArray)

| 名称       | 类型   | 描述                         |
|:------------|:--------|:------------------------------|
| treeName   | String | 资产树名称                   |
| parentPath | String | 模型父路径                   |
| name       | String | 模型名称                     |
| type       | String | 资产类型 (Type,Instance,Tag) |
| path       | String | 模型路径                     |

## POST /api/assetModels

创建资产模型

协议: Https

请求负载(QueryString):

| 名称       | 类型   | 描述           |
|:------------|:--------|:----------------|
| parentPath | String | 资产模型父路径 |
| name       | String | 资产模型名称   |

响应负载: NA

## PUT /api/assetModels/{modelPath}

更新资产树模型

协议: Https

请求负载(QueryString):

| 名称       | 类型   | 描述           |
|:------------|:--------|:----------------|
| parentPath | String | 资产模型父路径 |
| name       | String | 资产模型名称   |

响应负载: NA

## DELETE /api/v1/assetModels/{modelPath}

删除资产树模型

协议: Https

请求负载: NA

响应负载: NA

## GET /api/v1/assetModels/{modelPath}/properties

通过资产树模型路径读取模型属性列表，这里的属性是指模型的子元素 

协议: Https

请求负载: NA; 

响应负载(JsonArray):

| 名称        | 类型                 | 描述   |
|:-------------|:----------------------|:---------------------|
| treeName    | String               | 资产树名称|
| parentPath  | String               | 模型父路径 |
| name        | String               | 模型属性名称|
| path        | String               | 模型路径  |
| modelPath   | String               | 模型实例的模型路径，只有当前属性的类型是模型实例的时候不为空                                |
| type        | String               | 资产类型 (Instance,Tag)                                                                    |
| tagType     | String               | 变量类型 (IO,Memory,Expression,System), 只有当前属性的类型是变量时不为空                   |
| valueType   | String               | 变量值类型 (Unknown,Integer,String,Double,Bool,DateTime), 只有当前属性的类型是变量时不为空 |
| description | String               | 模型属性描述|
| properties  | AssetModelProperty[] | 当前模型实例的属性列表  |

## POST /api/v1/assetModels/{modelPath}/properties

创建资产模型属性

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述 |
|:-------------|:--------|:---------|
| name        | String | 资产模型属性名称   |
| type        | String | 资产类型 (Instance,Tag)    |
| modelPath   | String | 模型实例的模型路径，只有当前属性的类型是模型实例的时候不为空     |
| tagType     | String | 变量类型 (IO,Memory,Expression,System), 只有当前属性的类型是变量时不为空                   |
| valueType   | String | 变量值类型 (Unknown,Integer,String,Double,Bool,DateTime), 只有当前属性的类型是变量时不为空 |
| description | String | 模型属性描述 |

响应负载: NA

## POST /api/v1/assetModels/{modelPath}/properties/batch

批量创建资产模型属性

协议: Https

请求负载(JsonArray):

| 名称        | 类型   | 描述  |
|:-------------|:--------|:----------|
| name        | String | 资产模型属性名称    |
| type        | String | 资产类型 (Instance,Tag)     |
| modelPath   | String | 模型实例的模型路径，只有当前属性的类型是模型实例的时候不为空     |
| tagType     | String | 变量类型 (IO,Memory,Expression,System), 只有当前属性的类型是变量时不为空                   |
| valueType   | String | 变量值类型 (Unknown,Integer,String,Double,Bool,DateTime), 只有当前属性的类型是变量时不为空 |
| description | String | 模型属性描述 |

响应负载: NA

## PUT /api/v1/assetModels/{modelPath}/properties/{name}

更新资产模型属性

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述             |
|:-------------|:--------|:------------------|
| name        | String | 资产模型属性名称 |
| description | String | 资产模型属性描述 |

响应负载: NA

## DELETE /api/v1/assetModels/{modelPath}/properties/{name}

删除模型属性

协议: Https

请求负载: NA 

响应负载: NA

## GET /api/v1/assetInstances

读取资产实例

协议: Https

请求负载(QueryString):

| 名称       | 类型   | 描述       |
|:------------|:--------|:------------|
| parentPath | String | 实例父路径 |

响应负载:

| 名称       | 类型   | 描述                       |
|:------------|:--------|:----------------------------|
| treeName   | String | 资产树名称                 |
| parentPath | String | 资产实例父路径             |
| name       | String | 资产实例名称               |
| type       | String | 资产类型 (Folder,Instance) |
| modelPath  | String | 模型路径                   |

## POST /api/v1/assetInstances

创建资产实例

协议: Https

请求负载:(JsonObject)

| 名称       | 类型   | 描述             |
|:------------|:--------|:-----------------|
| parentPath | String | 资产实例父路径   |
| name       | String | 资产实例名称     |
| modelPath  | String | 资产实例模型路径 |

## PUT /api/v1/assetInstances/{path}

更新资产实例 

协议: Https

请求负载:(JsonObject)

| 名称       | 类型   | 描述           |
|:------------|:--------|:----------------|
| parentPath | String | 资产实例父路径 |
| name       | String | 资产实例名称   |

响应负载: NA

## DELETE /api/v1/assetInstances/{path}

删除资产实例

协议: Https

请求负载: NA 

响应负载: NA



## GET /api/v1/assetInstances/{path}/properties

读取资产实例属性列表

协议: Https

请求负载: NA 

响应负载:

| 名称        | 类型               | 描述  |
|:-------------|:--------------------|:-----------|
| treeName    | String             | 资产树名称|
| parentPath  | String             | 资产模型实例属性父路径   |
| name        | String             | 资产实例名称|
| path        | String             | 资产实例路径|
| modelPath   | String             | 资产实例的模型路径   |
| type        | String             | 资产类型 (Instance,Tag)    |
| tagType     | String             | 变量类型 (IO,Memory,Expression,System), 只有当前属性的类型是变量时不为空                   |
| valueType   | String             | 变量值类型 (Unknown,Integer,String,Double,Bool,DateTime), 只有当前属性的类型是变量时不为空 |
| description | String             | 变量描述 |
| properties  | AssetModelProperty | 实例子属性列表    |

## GET /api/v1/tags

读取变量列表

协议: Https

请求负载(QueryString):

| 名称       | 类型   | 描述       |
|:------------|:--------|:------------|
| parentPath | String | 变量父路径 |

响应负载(JsonArray):

| 名称        | 类型   | 描述  |
|:-------------|:--------|:----------|
| treeName    | String | 资产树名称 |
| parentPath  | String | 父路径  |
| name        | String | 变量名称 |
| path        | String | 变量路径   |
| modelPath   | String | 模型实例的模型路径，只有当前元素的资产类型是资产模型实例时不为空                            |
| type        | String | 资产类型 (Folder,Instance,Tag)    |
| tagType     | String | 变量类型 (IO,Memory,Expression,System), 只有当前属性的类型是变量时不为空                   |
| valueType   | String | 变量值类型 (Unknown,Integer,String,Double,Bool,DateTime), 只有当前属性的类型是变量时不为空 |
| description | String | 变量描述  |

## POST  /api/v1/tags

创建变量

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述  |
|:-------------|:--------|:-----------|
| parentPath  | String | 变量父路径 |
| name        | String | 变量名称  |
| type        | String | 资产类型 (Folder,Instance,Tag)                                                             |
| tagType     | String | 变量类型 (IO,Memory,Expression,System)                                                     |
| valueType   | String | 变量值类型 (Unknown,Integer,String,Double,Bool,DateTime), 只有当前属性的类型是变量时不为空 |
| description | String | 变量描述  |

## PUT /api/v1/tags/{path}

更新变量

协议: Https

请求负载(JsonObject):

| 名称        | 类型   | 描述       |
|:-------------|:--------|:------------|
| parentPath  | String | 变量父路径 |
| name        | String | 变量名称   |
| description | String | 变量描述   |

## DELETE /api/v1/tags/{path}

删除变量

协议: Https

请求负载: NA 

响应负载: NA

## GET /api/v1/tags/{path}/configuration

读取变量配置

协议: Https

请求负载: NA

响应负载(JsonObject):

| 名称        | 类型                         | 描述           |
|:-------------|:------------------------------|:----------------|
| name        | String                       | 变量名称       |
| tagGroup    | String                       | 变量组         |
| description | String                       | 描述           |
| value       | ValueConfigurationModel      | 值配置         |
| alarm       | AlarmConfigurationModel      | 报警配置       |
| history     | HistoricalConfigurationModel | 历史记录配置   |
| deadband    | DeadbandConfigurationModel   | 采集死区配置   |
| scale       | ScaleConfigurationModel      | 量程转换配置   |
| event       | EventConfigurationModel      | 事件配置       |
| simulate    | SimulationConfigurationModel | 模拟配置       |
| custom      | CustomConfigurationModel     | 自定义属性配置 |

值配置模型定义(ValueConfigurationModel)

| 名称                 | 类型    | 描述   |
|:----------------------|:---------|:-------------------------|
| valueType            | String  | 数据类型(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | 初始值     |
| engineeringLowLimit  | Double  | 工程下限    |
| engineeringHighLimit | Double  | 工程上限    |
| unit                 | String  | 单位      |
| writable             | Boolean | 可写   |
| dataSource           | String  | 数据源     |
| dataSourcePath       | String  | 原变量路径   |
| readExpression       | String  | 表达式(读值)  |
| writeExpression      | String  | 表达式(写值)  |

报警配置模型定义(AlarmConfigurationModel)

| 名称              | 类型                                | 描述           |
|:-------------------|:-------------------------------------|:----------------|
| limitAlarm        | LimitAlarmConfigurationModel        | 限值报警配置   |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | 变化率报警配置 |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | 等值报警配置   |
| booleanAlarm      | BooleanAlarmConfigurationModel      | 开关报警配置   |

限值报警配置模型定义(LimitAlarmConfigurationModel)

| 名称               | 类型              | 描述         |
|:--------------------|:-------------------|:--------------|
| activeDelayEnabled | Boolean           | 启用激活延迟 |
| activeDelay        | Integer           | 激活延时     |
| resumeDelayEnabled | Boolean           | 启用恢复延时 |
| resumeDelay        | Integer           | 恢复延时     |
| inclusive          | String            | 区间包含模式 |
| limitAlarms        | LimitAlarmModel[] | 限值报警列表 |

限值报警模型定义(LimitAlarmModel)

| 名称             | 类型    | 描述   |
|:------------------|:---------|:---------------------------|
| enabled          | Boolean | 启用     |
| type             | String  | 类型(H ,H2 , H3,H4,L,L2,L3,L4)     |
| name             | String  | 名称     |
| priority         | String  | 级别(Low,Medium,High,Critical)   |
| limit            | Double  | 限值  |
| deadband         | Double  | 死区值   |
| deadbandMode     | String  | 死区模式   |
| ackMode          | String  | 确认模式(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | 通知规则  |
| description      | String  | 描述  |

变化率报警配置模型定义(RateOfChangeAlarmConfigurationModel)

| 名称               | 类型                     | 描述           |
|:--------------------|:--------------------------|:----------------|
| activeDelayEnabled | Boolean                  | 启用激活延迟   |
| activeDelay        | Integer                  | 激活延时       |
| resumeDelayEnabled | Boolean                  | 启用恢复延时   |
| resumeDelay        | Integer                  | 恢复延时       |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | 变化率报警列表 |

变化率报警模型定义(RateOfChangeAlarmModel)

| 名称             | 类型    | 描述   |
|:------------------|:---------|:-------------------|
| enabled          | Boolean | 启用    |
| name             | String  | 名称      |
| priority         | String  | 级别(Low,Medium,High,Critical)      |
| changeRate       | Double  | 变化率(%)     |
| cycle            | Double  | 周期    |
| cycleUnit        | String  | 周期单位(Msec,Sec,Min,Hour,Day,Week,Month,Year)                             |
| ackMode          | String  | 确认模式(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | 通知规则    |
| description      | String  | 描述     |

等值报警配置模型定义(EquivalentAlarmConfigurationModel)

| 名称               | 类型                   | 描述         |
|:--------------------|:------------------------|:--------------|
| activeDelayEnabled | Boolean                | 启用激活延迟 |
| activeDelay        | Integer                | 激活延时     |
| resumeDelayEnabled | Boolean                | 启用恢复延时 |
| resumeDelay        | Integer                | 恢复延时     |
| equivalentAlarms   | EquivalentAlarmModel[] | 等值报警列表 |

等值报警模型定义(EquivalentAlarmModel)

| 名称             | 类型    | 描述     |
|:------------------|:---------|:---------------|
| enabled          | Boolean | 启用      |
| name             | String  | 名称   |
| priority         | String  | 级别(Low,Medium,High,Critical)  |
| Value            | Dynamic | 值      |
| ackMode          | String  | 确认模式(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | 通知规则  |
| description      | String  | 描述      |

开关报警配置模型定义(BooleanAlarmConfigurationModel)

| 名称               | 类型                | 描述         |
|:--------------------|:---------------------|:--------------|
| activeDelayEnabled | Boolean             | 启用激活延迟 |
| activeDelay        | Integer             | 激活延时     |
| resumeDelayEnabled | Boolean             | 启用恢复延时 |
| resumeDelay        | Integer             | 恢复延时     |
| booleanAlarms      | BooleanAlarmModel[] | 开关报警列表 |

开关报警模型定义(BooleanAlarmModel)

| 名称             | 类型    | 描述    |
|:------------------|:---------|:-------------|
| enabled          | Boolean | 启用    |
| type             | String  | 类型        |
| name             | String  | 名称    |
| priority         | String  | 级别(Low,Medium,High,Critical)  |
| ackMode          | String  | 确认模式(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | 通知规则  |
| description      | String  | 描述    |

历史记录配置模型定义(HistoricalConfigurationModel)

| 名称                 | 类型    | 描述   |
|:----------------------|:---------|:--------|
| mode                 | String  | 模式(On Change,Periodic)   |
| storagePeriod        | Integer | 存储周期  |
| storagePeriodUnit    | String  | 储存周期单位(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
| compressionMode      | String  | 压缩模式(Off,Delta Compression,Slope Compression)   |
| compressionType      | String  | 压缩类型(Absolute,Percent)  |
| value                | Double  | 值   |
| timeoutFallback      | Boolean | 超时补值  |
| fallbackInterval     | Integer | 补值间隔        |
| fallbackIntervalUnit | String  | 补值间隔单位(Msec,Sec,Min,Hour,Day,Week,Month,Year) |

采集死区配置模型定义(DeadbandConfigurationModel)

| 名称          | 类型    | 描述                   |
|:---------------|:---------|:------------------------|
| mode          | String  | 模式(Absolute,Percent) |
| deadbandValue | Integer | 死区值                 |

量程转换配置模型定义(ScaleConfigurationModel)

| 名称     | 类型   | 描述                        |
|:----------|:--------|:-----------------------------|
| mode     | String | 模式(Linear,Square,Reverse) |
| rawMin   | Double | 最小原始值                  |
| rawMax   | Double | 最大原始值                  |
| valueMin | Double | 最小值                      |
| valueMax | Double | 最大值                      |

事件配置模型定义(EventConfigurationModel)

| 名称                | 类型    | 描述       |
|:---------------------|:---------|:------------|
| setValueEnabled     | Boolean | 变量写值   |
| setValue            | String  | 值         |
| valueChangedEnabled | Double  | 布尔值跳变 |

模拟配置模型定义(SimulationConfigurationModel)

| 名称            | 类型    | 描述  |
|:-----------------|:---------|:-------------------------|
| type            | String  | 类型(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | 初始值       |
| simulationValue | String  | 模拟值     |
| value           | Dynamic | 值     |
| minValue        | Double  | 最小值      |
| maxValue        | Double  | 最大值      |
| decimals        | Integer | 小数位      |
| changeFrequency | Integer | 变化频率        |
| changeAmplitude | Double  | 变化幅度    |

自定义属性配置模型定义(CustomConfigurationModel)

| 名称    | 类型          | 描述           |
|:---------|:---------------|:----------------|
| customs | CustomModel[] | 自定义属性列表 |

自定义属性模型定义(CustomModel)

| 名称  | 类型    | 描述 |
|:-------|:---------|:------|
| name  | String  | 名称 |
| value | Dynamic | 值   |