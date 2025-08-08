# moviepy

## 基础介绍

用于视频编辑的 Python 库


## 核心内容
```yaml
moviepy:
    editor:
        AudioFileClip: # 音频文件剪辑
        CompositeVideoClip: # 复合视频剪辑
            write_videofile():
        ImageClip: # 图像剪辑
            set_duration():
        TextClip: # 文字剪辑
            set_duration():
        VideoFileClip: # 视频文件剪辑
            duration:
            fps:
            size:
            subclip(): # 视频截取
            write_videofile(): # 保存文件
                bitrate: # 码率 (单位是kbps)
                codec: # 编解码器
                fps: # 帧率
        concatenate_videoclips():
    video:
        fx:
```