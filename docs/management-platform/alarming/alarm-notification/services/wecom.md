# 企业微信

用来配置通过企业微信给特定的群组或者账号发送报警通知。

## 创建企业微信服务

1. 点击“**报警**”->"**报警通知**"->"**通知服务**"，进入通知服务列表页面。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/T-Pm1rnAFS_gmJ-kUiPam2vXM-s66KgNUsgRodtDkSU.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

1. 点击右上角“**新增**”按钮。在新增弹窗中选择企业微信。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/1NODPyuuufPI1junOUg2Lzh-m7UEeq4I_PQlf5iBJTw.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

2. 点击下一步，进入详细配置界面。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/bWC4yg31IM5_xPNWBWPIJ7PAaA42GGml1maH5_be4vc.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

“发送至”默认选择企业微信机器人，如果想发给个人，请勾选企业微信账号，两者允许同时选择。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/FKAoKXYkHEYdoFukfs-Me8zKEqavSoWUnVZI18mlZs8.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

3. 设置完成后，点击'**确认**'按钮，添加该条配置数据。

**属性**

| **名称**       | **描述** |
|----------------|-------------------|
| 名称           | 通知服务名称。 |
| 描述           | 通知服务描述。|
| 发送至         | 设置要发送给哪些人，可以是企业微信机器人，也可以是企业微信账号。选择后，需在页面下方添加对应的信息。  - 实际发送报警通知时，是根据webhook地址进行发送的。每个群机器人会对应一个唯一的webhook地址，一个群机器人可以应用于多个微信群，该机器人应用于哪些群，后续就会对这些群内的用户发送通知。  |
| 企业微信机器人 | 当“发送至”选择了**企业微信机器人**时，显示该配置项**。**用于设置需要接收报警通知的企业微信机器人。别名是机器人的名字。  - 别名：企业微信群的机器人的名字。 - Webhook URL：在企业微信群中配置机器人后，系统自动生成的一条 HTTP 接口地址。  Webhook 地址的形式通常是：*https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=......*  - `qyapi.weixin.qq.com`：企业微信对外开放的 API 域名 - `/cgi-bin/webhook/send`：机器人消息推送的固定路径 - `key=…`：每个机器人独一无二的身份凭证，创建机器人时系统会自动生成 
| 企业微信账号   | 当“发送至”选择了**企业微信账号**时，显示该配置项**。**用于设置需要接收报警通知的企业微信账号。  若想将通知发给个人，需在先在微信管理后台 → “应用管理” 页面创建一个**应用**，通过该应用来进行通知发送。  ![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/DJbHZAvX_AuyDZ0ikoJVcpt6dUJBAC8Vspg6xFRZ15M.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)  | AgentId | 应用的唯一标识。  在企业微信管理后台 → “应用管理” 页面，点击你创建的应用，在应用详情页可见“AgentId”。  ![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/84fkdkk4vJEuWMmPj64JejQKz08lWHp2Pr3u2IUM61c.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)                                                 | |---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| | Secret  | 配合企业ID 与 AgentId，用于调用 API 时的身份验证。  在企业微信管理后台 → “应用管理” 页，点击你创建的应用，在应用详情页可见“Secret”。  ![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/nAEEs899TRlZ4hBIgDESOwoHICDaHcOHfCWdXLGHYTI.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)                   | | 企业ID  | 企业微信组织的唯一标识。  在企业微信管理后台 → “我的企业” 页面内可见。  ![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/DBqttkHdHk9OgTtEb18fqTEj9hW3P-OfYwwhnc5wsXE.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)                                                                              | | 账号    | 设置接收报警通知的企业微信账号。账号需和企业微信管理后台 → “通讯录” 中的**账号**一致。  如果想通过导入的方式添加账号，需在企业微信管理后台，导出账号。  ![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/nkb7ILuRa2ATKqMGhwHZTm215gNiSXLViUUBUW--9VM.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4) | |



#### 如何添加群机器人

**桌面端**

1. 点击一个企业微信群的设置按钮，选择“添加群机器人”。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/NcfLH1vLpOwMypyuJJBHBlGpqwxSkT-ZnZXuAsCaEFQ.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

2. 创建一个机器人

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/z4c8f2QfQ2-X8c_aAFKxmPo1MrDngfblbsP58LR9p3g.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

3. 保存机器人

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/0xxSRo7Tx2-a-H_YSSbq9zWtV5CEFy0m19yhoZA14oU.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

**手机端**

1. 进入一个企业微信群，点击右上角的设置按钮

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/qDS8Mum39ZDOMkzIReo88SYP-Z6VQHy14LYsbMr28j4.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

2. 点击后进入聊天信息页面，在该页面点击群机器人

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/k5ohbOnw3rGnohLwz0eOd4V1zMb_vECarRQMpjVBl0w.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

3. 在群机器人窗口，点击页面右上角的“添加”按钮，按照添加步骤，添加机器人即可。

#### 如何查看群机器人Webhook地址

**桌面端**

在企业微信群内，点击某个群机器人，即可查看该机器人的Webhook地址。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/JNf_yumL1V-7RRC1INUZOs0LSXChAEI6nxP7a8sq534.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

**手机端**

1. 在企业微信群内，点击右上角的设置按钮进入聊天信息页面
2. 在聊天信息页面点击群机器人，进入群机器人列表
3. 在列表中，点击群机器人，即可查看

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/22MuxD3bGULo7CzY02DYvKmFy97ETDBn01qEzvoaSl4.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

**说明：只有自己创建的群机器人，才能查看到Webhook地址。** 

#### 如何创建应用

1. 登录企业微信管理后台(  [https://work.weixin.qq.com/wework_admin/frame#apps](https://work.weixin.qq.com/wework_admin/frame#apps) )，在“应⽤管理“页面点击**创建应用**

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/j2k9puut3Ncf6QDehZghNNjJvN_QdK-CPSVli_ANF6c.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

2. 创建一个应用。

**说明：可见范围一定要设置，选择需要接收报警通知的部门或者成员。**

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/ZMoiojPG_b8LDzN6c3a9bCmSvxjCPE33k8Srs51qVr4.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

3. 应用创建完成后，在该应用页面底部点击”企业可信IP“的配置按钮

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/o0g-fEEaGLgxa_ohKMUk71GzkZrNKWp80jCJQD1eYAM.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

设置可信域名或者设置接受消息服务器URL

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/xuFLZ73ANMhY4qwtRfWiNCw56PtHaQGd02WRellio8g.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

4. 设置可信域名完毕后，配置企业可信IP

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/nODlorhxt4ETKxIQNJ6-JG_tTCi-_QF1sPg1jhfXjXc.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)

5. 完成配置。

## 通知服务应用

在报警的 **通知规则** 中将选择通知服务。

1. 点击“**报警**”->"**报警通知**"->"**通知规则**"，进入通知规则列表页面。
2. 点击列表右上角的“新增“按钮。
3. 在新增弹窗中点击通知的'**+企业微信**'按钮，新增一条Email通知规则，在通知服务选择之前创建好的通知服务。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/Hy6DxVN5/resources/6fqRmeAzxbSo6lnN_kgMBd0LajFYN7iUUhpVvBnEoNc.png?token=W.oBxYsNQNUMamVBc0KRPLwcG7awRNs2Z_ehCyHTf32LquZLJs_Lzv_mFeMgw05e4)