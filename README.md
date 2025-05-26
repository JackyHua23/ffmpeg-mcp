# FFmpeg-MCP

基于FFmpeg命令行的MCP服务器，通过对话实现本地视频搜索、剪辑、拼接、播放等功能。

## 功能特性

### 视频管理
- **`find_video_path`** - 视频文件搜索
  - 在指定目录递归搜索视频文件
  - 支持完整文件名或无后缀名搜索
  - 返回完整文件路径

- **`get_video_info`** - 获取视频信息
  - 返回视频时长、帧率、编码格式、分辨率等详细信息

### 视频编辑
- **`clip_video`** - 视频剪辑
  - 支持指定开始时间、结束时间或持续时间
  - 返回剪辑后的文件路径

- **`concat_videos`** - 视频拼接
  - 支持多个视频文件合并
  - 自动检测视频参数一致性，启用快速模式

- **`scale_video`** - 视频缩放
  - 自定义输出分辨率
  - 支持保持宽高比（使用-2参数）

- **`overlay_video`** - 视频叠加
  - 实现画中画效果
  - 支持9种相对位置和自定义偏移

### 媒体提取
- **`extract_frames_from_video`** - 提取视频帧
  - 支持PNG、JPG、WEBP格式
  - 可设置提取频率和最大帧数

- **`extract_audio_from_video`** - 提取音频
  - 从视频中分离音轨
  - 支持多种音频格式输出

### 播放功能
- **`play_video`** - 视频播放
  - 支持mov/mp4/avi/mkv/3gp等格式
  - 可调节播放速度和循环次数

## 安装配置

### 1. 下载项目
```bash
git clone https://github.com/video-creator/ffmpeg-mcp.git
cd ffmpeg-mcp
uv sync
```

### 2. 配置MCP客户端
```json
{
  "mcpServers": {
    "ffmpeg-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/ffmpeg-mcp",
        "run",
        "ffmpeg-mcp"
      ],
      "transportType": "stdio"
    }
  }
}
```

> 注意：请将 `/path/to/ffmpeg-mcp` 替换为实际的项目路径

## 系统要求

- **操作系统**: macOS (ARM64 / x86_64)
- **依赖**: FFmpeg