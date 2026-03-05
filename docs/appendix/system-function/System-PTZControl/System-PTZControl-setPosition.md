# System.PTZControl.setPosition

| **描述**                  |
|---------------------------|
| 设置云台摄像头的绝对位置。 |

| **语法**  |
|--------|
| **System.PTZControl.setPosition(streamName: string,cameraName: string,x: number,y: number,z: number): Promise<void>**  - 参数        streamName - WebRTC Streamer名称  cameraName - 摄像头名称        x - 摄像头的水平坐标，范围[-1,1]        y - 摄像头的垂直坐标，范围[-1,1]        z - 摄像头的变焦值，范围[0,1]  - 返回  无 |
| |

| **代码示例**  |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 将WebRTC Streamer Streamer1的摄像头Camera1设置为水平坐标-1、垂直坐标-1和变焦值1。  ```typescript await System.PTZControl.setPosition("Streamer1","Camera1",-1,-1,1); ``` |

