# System.PTZControl.move

| **描述**                  |
|---------------------------|
| 控制云台摄像头的移动操作。 |

| **语法**   |
|--------------|
| **System.PTZControl.move(streamName: string,**  **cameraName: string,**  **operation: "Home" | "MoveUp" | "MoveDown" | "MoveLeft" | "MoveRight" | "ZoomIn" | "ZoomOut"**  **): Promise<void>**  - 参数        streamName - WebRTC Streamer名称  cameraName - 摄像头名称        operation - 云台操作指令，可选值：                           "Home" - 复位，                           "MoveUp" - 向上移动，                           “MoveDown” - 向下移动，                           “MoveLeft” - 向左移动，                           "MoveRight" - 向右移动，                           "ZoomIn" - 放大，                           “ZoomOut” - 缩小    - 返回  无 |
| |

| **代码示例** |
|----------------------------------------------------------------------------------------------------------------------------------------|
| 控制WebRTC Streamer Streamer1的摄像头Camera1向上移动。  ```typescript await System.PTZControl.move("Streamer1","Camera1","MoveUp"); ``` |

