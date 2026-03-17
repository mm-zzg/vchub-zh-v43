# SQL Server

在此页面上，我们将演示如何将WAGO SCADA连接到SQL Server。

1. 在“**数据库**”->“**数据库连接**”页面，点击“**新增**”按钮。

    ![alt text](6.png)

2. 在弹出的如下窗口中，选择SQL Server，点击“下一步”按钮。

    ![alt text](10.png)

3. 获取SQL Server服务器连接字符串信息, 例如下面两种格式：

    User ID=sa;Password=admin@12345;Server=localhost,1433;Database=scada-history;encrypt=true;TrustServerCertificate=true;

    jdbc:sqlserver://localhost:1433;database=scada-history;user=sa;password=admin@12345;encrypt=true;TrustServerCertificate=true;

    在配置界面输入如下信息（说明：以下数据仅为示例，请根据实际情况填写）。

    ![alt text](11.png)

    - 名称：Demo
    - Host： localhost
    - 端口：1433
    - 数据库名称：scada-history
    - 用户名：sa
    - 密码：admin@12345 
    - 扩展连接参数：encrypt=true;TrustServerCertificate=true;
    - 连接超时(ms)：10000
    - 最大查询点数：5000000
    - 查询超时(s)：30

4. 点击“确认”按钮，弹窗关闭，显示数据库连接列表。在列表中该条数据的连接状态显示为“连接成功”。

    ![alt text](12.png)

