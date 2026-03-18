# YouTube Download Skill

这是一个用于 OpenClaw 个人助手的 YouTube 视频下载技能（Skill）。

## 功能特性

使用 yt-dlp 下载 YouTube 视频和音频：

- 🎬 下载 YouTube 视频（支持多种质量选择）
- 🎵 仅提取音频（支持 MP3、M4A、FLAC 等格式）
- 📋 下载完整播放列表
- 📝 下载字幕（自动生成或手动添加）
- 🎛️ 自定义输出文件名和格式

## 安装

### 前置要求

确保已安装 yt-dlp：

```bash
pip install yt-dlp
```

或更新到最新版本：

```bash
pip install -U yt-dlp
```

## 使用方法

### 下载最佳质量视频

```bash
yt-dlp "https://www.youtube.com/watch?v=VIDEO_ID"
```

### 仅下载音频（MP3 格式）

```bash
yt-dlp -x --audio-format mp3 "https://www.youtube.com/watch?v=VIDEO_ID"
```

### 查看可用格式

```bash
yt-dlp -F "https://www.youtube.com/watch?v=VIDEO_ID"
```

### 下载指定格式

```bash
yt-dlp -f 137+140 "https://www.youtube.com/watch?v=VIDEO_ID"
```

### 下载播放列表

```bash
yt-dlp -o "%(playlist_index)s - %(title)s.%(ext)s" "https://www.youtube.com/playlist?list=PLAYLIST_ID"
```

### 自定义输出文件名

```bash
yt-dlp -o "%(title)s - %(uploader)s.%(ext)s" "https://www.youtube.com/watch?v=VIDEO_ID"
```

## 常用选项

- `-x, --extract-audio`: 仅提取音频
- `--audio-format mp3`: 指定音频格式（mp3, m4a, wav, flac 等）
- `-F, --list-formats`: 列出所有可用格式
- `-f, --format`: 指定格式代码
- `-o, --output`: 自定义输出文件名模板
- `--playlist-start N`: 从播放列表第 N 个开始
- `--playlist-end N`: 到播放列表第 N 个结束
- `--write-sub`: 下载字幕
- `--write-auto-sub`: 下载自动生成的字幕
- `--sub-lang en,zh`: 指定字幕语言

## 输出文件名模板变量

- `%(title)s`: 视频标题
- `%(uploader)s`: 上传者名称
- `%(upload_date)s`: 上传日期（YYYYMMDD）
- `%(playlist_index)s`: 播放列表中的序号
- `%(id)s`: 视频 ID
- `%(ext)s`: 文件扩展名

## 更多示例

### 下载视频并保存到指定目录

```bash
yt-dlp -o "/path/to/downloads/%(title)s.%(ext)s" "URL"
```

### 下载 1080p 视频 + 最佳音频

```bash
yt-dlp -f "bestvideo[height<=1080]+bestaudio/best[height<=1080]" "URL"
```

### 下载整个频道的所有视频

```bash
yt-dlp "https://www.youtube.com/c/CHANNEL_NAME/videos"
```

## 如何在 OpenClaw 中使用

1. 将此仓库克隆或下载到你的 OpenClaw 工作区的 `skills/` 目录下
2. 在 OpenClaw 中，当你提到 "下载 YouTube 视频"、"提取音频"、"下载播放列表" 等时，该 Skill 会自动触发
3. OpenClaw 会使用 `SKILL.md` 中的指导来帮助你完成任务

## 目录结构

```
youtube-download-skill/
├── SKILL.md          # Skill 的主要说明文件
└── README.md         # 本文件
```

## 许可证

MIT License
