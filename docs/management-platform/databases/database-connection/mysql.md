# MySQL

在此页面上，我们将演示如何将WAGO SCADA连接到 MySQL。

1. 在“**数据库**”->“**数据库连接**”页面，点击“**新增**”按钮。

    ![alt text](6.png)

2. 在弹出的如下窗口中，选择MySQL，点击“下一步”按钮。

    ![alt text](7.png)

3. 获取MySQL服务器连接字符串信息, 例如下面两种格式：

    User ID=SCADAadmin;Password=admin@12345;Host=112.80.63.83,3306;Database=history;Charset=utf8;allowPublicKeyRetrieval=true;

    jdbc:mysql://112.80.63.83:3306/history?user=scadaadmin&password=admin@12345&Charset=utf8&allowPublicKeyRetrieval=true;

    在配置界面输入如下信息（说明：以下数据仅为示例，请根据实际情况填写）。

    ![alt text](8.png)

    - 名称：Demo
    - Host: 112.80.63.83
    - 端口：3306
    - 数据库名称：history
    - 用户名：scadaadmin
    - 密码：admin@12345 
    - 扩展连接参数：Charset=utf8;allowPublicKeyRetrieval=true;
    - 连接超时(ms)：10000
    - 最大查询点数：5000000
    - 查询超时(s)：30

4. 点击“确认”按钮，弹窗关闭，显示数据库连接列表。在列表中该条数据的连接状态显示为“连接成功”。

    ![alt text](9.png)



