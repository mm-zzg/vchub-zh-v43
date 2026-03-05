# System.PTZControl.stop

| **描述**                      |
|-------------------------------|
| 停止云台摄像头的当前移动操作。 |

| **语法**  |
|-------------|
| **System.PTZControl.stop(streamName: string,cameraName: string): Promise<void>**  - 参数        streamName - WebRTC Streamer名称  cameraName - 摄像头名称  - 返回  无 |
||

| **代码示例**                                                                                                                    |
|---------------------------------------------------------------------------------------------------------------------------------|
| 停止WebRTC Streamer Streamer1的摄像头Camera1的移动操作。  ```typescript await System.PTZControl.stop("Streamer1","Camera1"); ``` |

