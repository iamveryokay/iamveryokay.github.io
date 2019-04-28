Title: 使用colab下载YouTube视频
Date: 2019-04-28
Category: Misc
Modified: 2019-04-28 23:04
Tags: Colab, Youtube-dl

# 动机
谷歌推出了类似jupyter notebook的云端python笔记表，同时还可以通过在命令行前面加上感叹号的形式访问远程的Ubuntu容器。这让我萌生了以彼之矛，破彼之盾的想法，用谷歌自家提供的平台下载自家的视频，岂不快哉？

# 下载流程
* 配置pip，配置好以后就可以在容器中使用youtube_dl下载视频了
```
!pip install youtube_dl
```

* 下载视频
```
!youtube-dl  -o "./%(title)s.%(ext)s" https://www.youtube.com/watch?v=FVFPRstvlvk
```

* 查看下载的视频
```
!ls
```

* 把视频从容器中下载到本地目录，复制刚刚查看的内容到下面的函数里
```python
from google.colab import files
files.download('AVENGERS 4 ENDGAME  - 8 Minute Trailers (4K ULTRA HD) NEW 2019.webm') 
```

* enjoy！

# 其他
* 查看可以下载的视频类型组合
```
!youtube-dl -F https://www.youtube.com/watch?v=dbyOUJn4WG8
```

* 下载想要的视频，如果是video only的话，记得把音频也选上
```
!youtube-dl -f 135+250 -o "./%(title)s.%(ext)s" https://www.youtube.com/watch?v=dbyOUJn4WG8
```

* enjoy again !

# 在mac上使用youtube_dl下载视频
* `brew install youtube_dl`
* `youtube_dl --proxy 127.0.0.1:1080 https://www.youtube.com/watch?v=FVFPRstvlvk`