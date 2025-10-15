# Youtube视频发表

1. [下载Youtube视频和音频](https://youtube.iiilab.com/) 。

2. [下载Youtube视频的中英字幕](https://downsub.com/)

3. 合并mp4（视频）和m4a（音频）文件

```shell
ffmpeg -i "test.mp4" -i "test.m4a" -vcodec copy -acodec copy output.mp4
```

4. 合并mp4（视频）和 srt（字幕）文件

```shell
ffmpeg -i "test.mp4" -vf subtitles="test.srt" output_srt.mp4
```
