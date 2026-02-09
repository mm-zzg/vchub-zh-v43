# 批量操作Camera设备

在工业现场，往往需要批量创建设备。WAGO SCADA通过**导出和导入**功能来实现这一功能。

**说明：**要想实现快速创建设备，建议先在列表中手动新增一条设备信息，之后将该设备进行导出，根据导出的字段信息添加新的设备。

#### 批量新增

###### 1.导出设备

点击列表右上角的“导出”按钮，可以将列表中的所有设备信息进行导出。

点击导出按钮后，会询问“是否要为导出文件设置密码？”

如果选择“是”，则需要设置密码后点击“确认”按钮进行导出；如果选择“否”，点击“确认”按钮直接导出。

导出文件为zip文件。

双击zip文件下的Camera.xlsx文件，查看导出的设备详情。

导出文件示例：

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/NAkyxAKN/resources/YT8xiC08JKy6Iz_lfJC-QHAe7yrbDCxM-UGnpTtwQVQ.png?token=W.keG7N7jy6g3YZwoGtHEZcq4ugpZG-o5aTahmM0vewLiff6iCX-gPuFVZVmCyu8g)

- 红框中内容为字段信息。
- 如果是WebRTCStreamer，则“IsWebRTCStreamer”字段为True。
- Camera信息紧跟在对应的WebRTCStreamer下面。例如上图的WebRTCStreamer“FactoryA下，存在1个Camera，Camera1。

###### 2.在Excel中新增设备

选中WebRTCStreamer和Camera，拉动鼠标，完成快速复制。WebRTCStreamer名称会递增。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/NAkyxAKN/resources/w1IwzO1tJ-_-QQGibfwz3e0tWq03Rb7QUpG1Ax-nG2s.gif?token=W.keG7N7jy6g3YZwoGtHEZcq4ugpZG-o5aTahmM0vewLiff6iCX-gPuFVZVmCyu8g)

如果某一列想保持不变，例如所有WebRTCStreamer下都使用同样的Camera名称，可以先复制一个WebRTCStreamer，手动将Camera名称改为一致。之后再全选进行拖动复制。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/NAkyxAKN/resources/tCic8LmFbam8-M_6u2Wxbm6RHGeFsKv4ZkkkF6EioLQ.gif?token=W.keG7N7jy6g3YZwoGtHEZcq4ugpZG-o5aTahmM0vewLiff6iCX-gPuFVZVmCyu8g)

###### 3.导入设备

点击列表右上角的“导入”按钮，可以将导出的内容进行导入。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/NAkyxAKN/resources/tXWFQTk149gDbXFAaka5lbaJbicS_m40f2hnpxAT70s.png?token=W.keG7N7jy6g3YZwoGtHEZcq4ugpZG-o5aTahmM0vewLiff6iCX-gPuFVZVmCyu8g)

上传要导入的文件后，如果该文件导出时设置了密码，在导入时需要输入密码后才可以成功导入。如果导出时未设置密码，则上传完文件后，直接点击“确认”按钮进行导入。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/NAkyxAKN/resources/nXn0SBDoQFJQmJScw5jd1n3DlvgAEBg8upkQXgrsQRc.png?token=W.keG7N7jy6g3YZwoGtHEZcq4ugpZG-o5aTahmM0vewLiff6iCX-gPuFVZVmCyu8g)

#### 批量修改

可以通过导出的excel，对设备信息进行批量修改。修改后将excel导入，导入时，将按照名称进行数据更新。

- Excel中的WebRTC Streamer名称和Camera列表中的名称一致，则使用excel中的该条配置进行数据更新。
- Excel中的WebRTC Streamer名称和其下的Camera，与Camera列表中的一致，则使用excel中的该条配置进行数据更新。
- Excel中的WebRTC Streamer名称或者Camera名称在Camera列表中不存在，则在列表中新增该WebRTC Streamer和Camera。
- Camera列表中的WebRTC Streame，不存在于导入文件中，则导入后，列表中的该数据不受影响。

#### 批量删除

勾选需要删除的设备后，点击列表上方的删除按钮进行批量删除。

![img](https://docs.wagoscada.cn/wiki/api/wiki/editor/QHXVK91b/NAkyxAKN/resources/u5iUSLBD-2PMZ32Pf_ocFM6evx7YGXE8c-6nVdMk8Wk.png?token=W.keG7N7jy6g3YZwoGtHEZcq4ugpZG-o5aTahmM0vewLiff6iCX-gPuFVZVmCyu8g)

**说明：**

1. 只能对当前页的数据进行删除，不支持跨页删除
2. 删除WebRTC Streamer时，会连同其下的Camera一起删除