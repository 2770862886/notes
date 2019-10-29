% Audio/Video

# 播放nv12
``` shell
ffplay -f rawvideo -video_size 1568x528 -pix_fmt nv12 640x480-30frames.nv12
```

# 播放
``` shell
ffplay -window_title "caterpillar404" output11.mp4
```

# 转码
``` shell
ffmpeg -i output11.mp4 -f rawvideo -pix_fmt nv12 output11.nv12
```

# 查看
``` shell
ffprobe output99.mp4
```
