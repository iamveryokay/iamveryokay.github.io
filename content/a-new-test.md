Title: Pelican使用指南
Date: 2019-02-07
Category: Misc
Modified: 2019-02-07 20:37
Tags： Pelican

<s>这个是测试</s>

# 安装pelican
* `pip install pelican markdown`，注意markdown一定要装，不然用markdown报的错误是没有找到文件之类的。

# 生成pelican
* `pelican -s pelicanconf.py -o output content`，简写的话`pelican output`

# 预览pelican
* `python -m http.server`，然后在浏览器输入`localhost:8000`就可以看到，我的chrome好像有缓存，所以预览的时候还是原来的页面，重开了隐身模式才搞定。


