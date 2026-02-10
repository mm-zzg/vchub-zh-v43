# WebRtc Streamer安全设置

采用默认安装方式安装的WebRtc Streamer采用的是Http的方式，当我们需要使用SSL时，就需要进行额外的操作。

WebRtc Streamer支持用 **Https** 的方式部署。

## 获取Https证书

我们可以使用官方机构颁发的证书，也可以自己生成开发证书。

#### 如何生成开发证书？

1. 可以使用OpenSSL生成

2. 也可以借助第三方网站生成

在 **Windows** 中可以使用以下步骤通过OpenSSL生成证书（在 **Linux** 中，将 “copy” 替换为 “cp” ，将 “type” 替换为 “cat”即可）：

```bash
  openssl genrsa -des3 -out server.key 2048
  openssl req -new -key server.key -out server.csr
  copy server.key server.key.orig
  openssl rsa -in server.key.orig -out server.key
  openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt
  copy server.crt server.pem
  type server.key >> server.pem
```
 
创建的 server.pem 文件必须包含一个 'CERTIFICATE' 部分以及一个 “RSA PRIVATE KEY”部分。它应该看起来像这样：

```plain
-----BEGIN CERTIFICATE-----
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
-----END CERTIFICATE-----
-----BEGIN RSA PRIVATE KEY-----
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
-----END RSA PRIVATE KEY-----
```
 
## 部署WebRtc Streamer为Https

将上一步生成的server.pem 文件放置在webrtc streamer程序的根目录。

运行以下命令，启动Https的WebRtc Streamer 服务。

1. **Windows**

    ```powershell
    # 7443s 就是https的端口7443
    webrtc-streamer.exe -H 7443s -c server.pem
    ```
 
2. **Linux**

    ```powershell
    # 7443s 就是https的端口7443
    webrtc-streamer -H 7443s -c server.pem
    ```
 
3. 启动完毕后可以看到日志。

    ```prolog
    nullLogger level:4
    HTTP Listen at 7443s
    ```
 
## 常见问题

如果 OpenSSL 配置设置不正确，服务器将不会开启。在 'civetweb.conf' 中配置错误日志文件以获取更多信息：

```Plain Text
  error_log_file error.log
```
 
检查 error.log 的内容：

```Plain Text
load_dll: cannot load libeay32.*/libcrypto.*/ssleay32.*/libssl.*
```
 
此错误消息表示 SSL 库尚未安装（正确）。 对于 Windows，您可以使用预构建的二进制文件。链接位于 OpenSSL 项目主页 （ [http://www.openssl.org/related/binaries.html](http://www.openssl.org/related/binaries.html)）。 选择 C:\Program Files\OpenSSL-Win64 文件夹(默认位置)作为安装目录。

```Plain Text
set_ssl_option: cannot open server.pem: error:PEM routines:*:PEM_read_bio:no start line
set_ssl_option: cannot open server.pem: error:PEM routines:*:PEM_read_bio:bad end line
```
 
这些错误消息指示 ssl_certificate 文件的格式不符合 SSL 库的期望。PEM 文件必须包含两者： “CERTIFICATE”和“RSA PRIVATE KEY”部分。它应该是严格的 ASCII 文件。 上述说明可用于创建有效的 ssl_certificate 文件。