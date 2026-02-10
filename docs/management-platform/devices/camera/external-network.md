# 外网播放Camera

如果想通过外网访问camera控件的视频，可以通过部署Coturn穿透服务实现外网访问。Coturn 是一个免费的开源 TURN 和 STUN 服务器实现。TURN 服务器是一款用于 VoIP 媒体流量 NAT 穿透的服务器和网关。

- ***只有Camera组件有外网访问的需求时才需要部署Coturn穿透服务。***
- ***部署Coturn服务的所在服务器一定要可以访问外网，且外网也可以访问该服务器，具有固定的外网Ip或域名。***
- ***且要放开3478、3479、5349TCP和UDP以及49152-65535UDP端口的防火墙。***

## 下载Coturn

官网地址： [GitHub - coturn/coturn: coturn TURN server project](https://github.com/coturn/coturn)   

## 部署Coturn

#### Linux 

```bash
# 安装coturn
apt install coturn
# 启动turn server
# turnserver --log-file=stdout -v --min-port={UDP开始端口} --max-port={DUP结束端口} -a -r {外网Ip或域名} -u {账号}:{密码}
例如：turnserver --log-file=stdout -v --min-port=49152 --max-port=65535 -a -r 122.254.123.122 -u admin:mm123456789
```
 
以上方式启动会有个问题，当服务器重启或者意外断开后，服务会关闭，不会自动重启，所以我们需要将服务更改为systemd 服务单元，这样可以更方便地管理启动、重启及日志。

```bash
# 安装coturn
apt install coturn

# 进入服务单元文件夹
cd /etc/systemd/system

# 在 /etc/systemd/system 目录下创建 coturnservice.service 文件，并在文件填写以下内容：

[Unit]
Description=Coturn TURN Server
After=network.target

[Service]
Type=simple
# ExecStart=turnserver --min-port={UDP开始端口} --max-port={DUP结束端口} -a -r {外网Ip或域名} -u {账号}:{密码}
ExecStart=turnserver --min-port=49152 --max-port=65535 -a -r 122.254.123.122 -u admin:mm123456789
Restart=on-failure

[Install]
WantedBy=multi-user.target  

# 保存后，启用并启动服务：
sudo systemctl daemon-reload
sudo systemctl enable coturnservice
sudo systemctl start coturnservice
```
 
通过这种方式，turnserver 将作为服务在后台运行，并会在系统重启后自动运行。

#### Windows

Coturn 服务器目前没有官方的 Windows 版本，因为它的设计和开发主要面向 Linux/Unix 系统。如果想在Windows环境中部署Coturn，主要有以下2种方式：

1. **使用 Windows Subsystem for Linux (WSL)**

      - 在 Windows 10 或 Windows 11 上启用 WSL，并安装一个 Linux 发行版（例如 Ubuntu）。详情请参照微软官方文档： [安装 WSL](https://learn.microsoft.com/zh-cn/windows/wsl/install)。

      - 后续步骤请参照上文 **Linux**。

2. **使用 Docker for Windows**

      - 部署步骤请参照下文 **Docker**。

#### Docker

以下步骤都基于Docker已经安装。如果未安装Docker，请参考官方文档： [Install | Docker Docs](https://docs.docker.com/engine/install/) 

**方式1：** 使用镜像

```bash
# 注意 该方式在服务器性能不佳时可能无法启动容器，因为会映射大量UDP端口，可能会在处理端口映射时出现卡死，或者部署失败的问题
# -a -r {你的机器外网Ip或域名} -u {账号}:{密码}
docker run -d -p 3478:3478 -p 3478:3478/udp -p 5349:5349 -p 5349:5349/udp -p 49152-65535:49152-65535/udp coturn/coturn --log-file=stdout -v -a -r 122.254.123.122 -u admin:mm123456789
```
 
**方式2**：直接使用主机网络（**推荐**)

```bash
# 这种方式会直接使用主机的网络，宿主机端口3478、3479、5349的TCP和DUP端口请保持未使用状态
# --min-port={UDP开始端口} --max-port={DUP结束端口} -a -r {你的机器外网Ip或域名} -u {账号}:{密码}
docker run -d --network=host coturn/coturn --log-file=stdout -v --min-port=49152 --max-port=65535 -a -r 122.254.123.122 -u admin:mm123456789
```
 
说明： [Docker在较大的端口范围内表现不佳⁠](https://github.com/instrumentisto/coturn-docker-image/issues/3)。

## 如何使用

当Coturn服务器部署完毕后，我们可以在WebRtc Streamer中使用该服务器配置。

在WebRtc Streamer启动时附加参数，例如：

```bash
# 在原启动命令后附加参数 -s "{外网Ip或域名}:3478" -t "{账号}:{密码}@{外网IP或域名}:3478" -R {UDP开始端口}:{UDP结束端口}
# 3478：Coturn部署时的默认端口
# 外网IP或域名：Coturn所在服务器的外网Ip或者访问域名
# 账号：Coturn部署时 -u 命令设置的账号
# 密码：Coturn部署时 -u 命令设置的密码
# -R {UDP开始端口}:{UDP结束端口}：Coturn启动时设置的UDP端口范围，例如Docker启动时设置的-p 49152-65535:49152-65535/udp，或二进制安装启动设置的--min-port=49152 --max-port=65535，请保持WebRtc Streamer的UDP端口范围和Conturn的DUP端口范围保持一致
```
 
#### Docker

```bash
# docker run -d --network=host -it mpromonet/webrtc-streamer -o -s "{外网IP或域名}:3478" -t "{账号}:{密码}@{外网IP或域名}:3478" -R {UDP开始端口}:{UDP结束端口}
docker run -d --network=host -it mpromonet/webrtc-streamer -o -s "122.254.123.122" -t "admin:mm123456789@122.254.123.122:3478" -R 49152:65535
```
 
#### Linux

```bash
# ./webrtc-streamer -H 0.0.0.0:8000 -o -s "{外网IP或域名}:3478" -t "{账号}:{密码}@{外网IP或域名}:3478" -R {UDP开始端口}:{UDP结束端口}
 ./webrtc-streamer -H 0.0.0.0:8000 -o -s "122.254.123.122:3478" -t "turn:mm123456789@122.254.123.122:3478" -R 49152:65535
```
 
#### Windows

```bash
# webrtc-streamer.exe -H 0.0.0.0:8000 -o -s "{外网IP或域名}:3478" -t "{账号}:{密码}@{外网IP或域名}:3478" -R {UDP开始端口}:{UDP结束端口}
webrtc-streamer.exe -H 0.0.0.0:8000 -o -s "122.254.123.122:3478" -t "turn:mm123456789@122.254.123.122:3478" -R 49152:65535
```
 


