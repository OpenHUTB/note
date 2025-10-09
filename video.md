# 视频

## 合并mp4（视频）和m4a（音频）文件

```shell
ffmpeg -i "test.mp4" -i "test.m4a" -vcodec copy -acodec copy output.mp4
```

应用于 [油管下载的视频](https://youtube.iiilab.com/) 。