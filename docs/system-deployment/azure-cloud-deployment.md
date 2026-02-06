# Azure 云部署

#### 简介

该文档主要介绍，如何基于Azure Virutal Machine部署WAGAO VC Hub服务，以及如何通过Azure提供的配套服务以及WAGO VC Hub自有的能力，提升WAGO VC Hub服务的可用性、容灾、备份能力。

我们将从单台虚拟机的部署开始，针对不同业务场景，循序渐进地描述如何部署一套可信赖使用的VC Hub系统。

#### 环境要求

###### 硬件（虚拟机配置）

[系统要求](../overview/system-requirements.md) 

#### 部署方式

###### 单虚拟机部署

######## 概要

订阅一台符合硬件配置的Azure Virtual Machine以及Azure Database服务，即可在后续完成云端部署工作。

目前，WAGO VC Hub支持的Azure Database服务类型有：Azure Database for MySQL,Azure Database for PostgreSQL，Azure SQL(SQL Server)。

该方法仅适用于的业务场景，是在对系统稳定性、容灾能力要求相对不高的情况下使用，优势是配置简单。

###### 部署架构

下图为WAGO VC Hub基于Azure的单机部署架构，将WAGO VC Hub可直接通过安装包一键式安装到Azure VM上。

我们推荐用户直接订阅Azure Database服务来存储VC Hub的历史数据（VC Hub服务同样支持本地数据库连接，但需要用户自己保证数据库可用性与备份等稳定性功能），在成功订阅了Azure Database后，通过WAGO VC Hub的数据库连接功能与之建立联系。

云端的WAGO VC Hub节点，支持通过MQTT协议与设备站点进行数据通讯，如图中**Station2**，建立MQTT通讯的前提，需要用户开启Azure Virtual Machine的**1883**端口，云端VC Hub将通过**1883**端口与设备站点进行通讯，该端口目前暂不支持自定义。

用户可以通过WAGO VC Hub内置的[组网](../management-platform/networking.md)功能，使云端的WAGO VC Hub节点与其它WAGO VC Hub节点建立通讯，如图中的**Station2**，**Station2**可以部署在云端或本地，用户需要开启Azure Virtual Machine的**8060**端口，该端口可在VC Hub网站中自定义修改。

![alt text](10.png)

###### Service Level Agreements分析

截至2024-04-01，Azure官方提供了在单实例虚拟机场景中可供参考的Uptime Calculation如下：

 [Service Level Agreement for Microsoft Online Services (WW)](https://wwlpdocumentsearch.blob.core.windows.net/prodv2/OnlineSvcsConsolidatedSLA(WW)(English)(April2024)(CR).docx)

| Azure Virtual Machine | Standard SSD | Standard HDD | Database |
|-----------------------|--------------|--------------|----------|
| 99.9%                 | 99.5%        | 95%          | 99.9%    |

###### 双虚拟机主备部署

为应对单台虚拟机服务可用性不能适应稳定性要求较高场景的情况下，可以利用两台Azure Virtual Machine实现WAGO VC Hub服务的主备部署（两台Azure VM推荐订阅在不同的Availability Zones中，可用性将提高到99.99%）。

利用WAGO VC Hub服务提供的[冗余](../management-platform/redundancy/index.md)配置，将两个VC Hub服务建立连接，形成主备，在主虚拟机宕机的情况下，备虚拟机会立刻接管数据监控服务，在用户角度做到无感切换。

同时，两个WAGO VC Hub节点连接到同一个Azure Database上，Device需要通过MQTT协议同时与两个VC Hub节点进行数据交互。

而本地WAGO VC Hub节点则只需配置与云端主VC Hub节点的组网连接即可,在主节点宕机后，本地VC Hub与云端的连接将自动切换到备用VM上。

![alt text](11.png)



##### Service Level Agreements分析

根据单台Azure VM提供的可用性描述，在双虚拟机部署配置主备理想状态下的Uptime Calculation如下：

| 同一 Azure 区域中跨两个或更多可用性区域 | 同一可用性集或同一专用主机组中 |
|-----------------------------------------|--------------------------------|
| 99.99%                                  | 99.95%                         |

#### 端口配置

用户需要手动开启Azure Virtual Machine的端口，赋予WAGO VC Hub通讯权限。

| 端口号 | 功能       | 描述                                                                          |
|--------|------------|-------------------------------------------------------------------------------|
| 8066   | HTTP服务   | 提供了WAGO VC Hub HTTP服务，用户可在安装过程自定义修改，也支持在管理平台中修改  |
| 8043   | HTTPS服务  | 提供了WAGO VC Hub HTTPS服务，用户可在安装过程自定义修改，也支持在管理平台中修改 |
| 8060   | 组网与冗余 | 在组网和冗余功能通讯时使用，默认为8060，用户可在管理平台中修改                  |
| 1883   | MQTT通讯   | 云端VC Hub系统与设备建立MQTT通讯时使用，暂不支持自定义                         |

#### 数据备份及还原

##### 概要

我们推荐用户定期对WAGO VC Hub中的重要数据进行备份，用户可以采用手动或自动的方式进行。

##### 如何操作

##### 历史数据库

在云部署方案中，我们推荐使用Azure Database来存储VC Hub历史数据(包含采集历史数据和报警历史数据)，Azure Database同样提供了数据备份功能，用户可以参照Azure提供的技术文档 [更改 Azure SQL 数据库的自动备份设置](https://learn.microsoft.com/en-us/azure/azure-sql/database/automated-backups-change-settings?view=azuresql-db&preserve-view=true&tabs=azure-portal)，配置定期备份VC Hub历史数据库。

在需要还原历史数据时，Azure Database也提供了自动恢复功能， [从 Azure SQL 数据库中的备份还原数据库](https://learn.microsoft.com/en-us/azure/azure-sql/database/recovery-using-backups?view=azuresql-db&tabs=azure-portal)。

###### 应用程序数据目录

除历史数据外，WAGO VC Hub的所有数据都以文件的形式存储在一个固定的文件夹中，作为应用程序数据目录，其中包含工程、证书、网络、日志等数据。

用户可定期手动复制应用程序数据目录到其它存储设备中进行备份。

在需要还原时，用户可将WAGO VC Hub服务手动停止后，将Azure VM中的应用程序数据目录替换为备份的应用程序数据目录，再重新启动WAGO VC Hub服务即可。

Azure提供了 [Azure Backup](https://azure.microsoft.com/en-us/products/backup)服务，该服务可配置定期进行自动备份，并提供了云存储空间。

Azure Backup也提供了还原功能，具体可参考 [将文件还原到 Azure 中的虚拟机](https://learn.microsoft.com/en-us/azure/backup/tutorial-restore-files)（注意：在进行还原前，仍需手动停止WAGO VC Hub服务）

应用程序数据目录的具体位置，可在安装过程配置，如下图所示。

![alt text](12.png)

#### 数据监控

###### 概要

在生产环境中，当Azure VM整体宕机时，系统管理员通常都会收到异常报告信息，但在部分情景下，是服务器中的某个服务出现异常中断，例如VC Hub服务异常、数据库服务异常。此时，可引入Azure Monitor对服务器中VC Hub服务以及数据库服务进行性能监控。

系统管理员可以通过监测面板观测服务器状态，及时接收异常报警状态，处理故障，也可配置Azure Backup，监测备份故障与异常。

在部署了WAGO VC Hub服务的Azure VM中，启用Azure Monitor代理，即可在Azure Monitor中心实时接收数据。

![alt text](13.png)

###### Azure Monitor地址

 [Azure Monitor](https://azure.microsoft.com/en-us/products/monitor)

#### 扩展

本手册主要描述了如何使用Azure提供的云服务部署WAGO VC Hub，同样，我们也支持其它云服务供应商类似的托管的虚拟机服务、数据库服务、备份服务、监控服务，如AWS、阿里云、腾讯云等。

