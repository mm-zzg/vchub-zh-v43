# 设置服务运行用户

通过为 "WAGO VC Hub" 服务指定特定的用户身份，可以限制该服务的权限，只授予其运行所需的**最小权限**。这有助于防止服务被滥用或被利用进行恶意操作。

将不同服务运行在不同用户下，可以将这些服务**相互隔离**，从而防止一个服务的漏洞或问题影响其他服务。也可以更容易地**跟踪和审计 "**WAGO VC Hub" 服务的活动。

WAGO VC Hub 服务在Windows中默认登录身份为**本地系统账户**，在Linux中默认以**root**用户运行。

#### Windows服务的“登录身份”

在Windows中，你可以通过几种不同的方法设置Windows服务的“登录身份”（Log On As）。以下是使用服务控制台（Services Console）、命令行工具（sc）来设置Windows服务登录身份的步骤。

更改服务登录身份需要管理员权限。

#### 方法 1: 使用服务控制台（Services Console）

1. **打开服务控制台**:

   - 按 `Win + R` 打开运行窗口。
   - 输入 `services.msc` 并按回车。
2. **找到并右键点击目标服务 WAGO VC Hub**:

   - 在服务列表中找到你要修改的服务 WAGO VC Hub。
   - 右键点击该服务，并选择 `属性`。
3. **设置登录信息**:

   - 在属性窗口中，切换到 `登录` 选项卡。
   - 选择 `此账户`，然后输入账户名和密码。
   - 点击 `确定` 保存设置。

![alt text](30.png)



#### 方法 2: 使用命令行工具（sc）

你可以使用 `sc config` 命令来配置服务的登录信息。

```bash
sc config "WAGO_SCADA" obj= "Domain\Username" password= "Password"
```
 
- **Domain\Username**: 账户名，可以是 `.\Username`（表示本地账户）或者 `Domain\Username`（表示域账户）。如果服务需要访问网络资源或其他计算机上的资源，使用域账户可能会更合适。
- **Password**: 账户的密码。

#### Linux服务的启动和运行用户

WAGO VC Hub仅支持使用‘systemd’设置服务，大多数Linux发行版都使用'systemd'，你可以通过编辑服务单元文件来设置服务的启动和运行用户。

1. **编辑服务单元文件**: 

通常，服务单元文件位于 `/etc/systemd/system/` 或 `/lib/systemd/system/` 目录下。

```bash
sudo nano /etc/systemd/system/wagoscada.service
```
 
2. **在服务单元文件中指定用户**: 

添加或修改 `[Service]` 部分中的 `User` 和 `Group` 选项来指定运行服务的用户和组。

```plain
[Unit]
Description=WagoScada-Daemon
After=network.target

[Service]
WorkingDirectory=/usr/local/bin/wagoscada-4.0.3-linux-x64
ExecStart=/usr/local/bin/wagoscada-4.0.3-linux-x64/start.sh
Restart=always
RestartSec=10
SyslogIdentifier=wagoscada-log
User=myuser
Group=mygroup

[Install]
WantedBy=multi-user.target graphical.target
```
 
3. **重新加载systemd配置并启动服务**: 

在编辑完单元文件后，重新加载`systemd`配置并启动服务。

```bash
sudo systemctl daemon-reload
sudo systemctl start wagoscada
```
 
#### 注意事项

   - 使用正确的账户和密码，以确保服务能够正常启动和运行。
   - 避免使用弱密码。
   - 确保账户具有最低权限原则，仅授予服务运行所需的权限，WAGO VC Hub服务需要**服务安装目录**，以及**服务数据目录**的读写权限。
   - 默认服务安装目录：
Windows：`"C:\Program Files\WAGO SCADA" `

Linux：`"/usr/local/bin/wagoscada"`

   - 默认数据目录：
Windows：`"C:\ProgramData\WAGOSCADA"`

Linux：`"/usr/share/WAGOSCADA"`

