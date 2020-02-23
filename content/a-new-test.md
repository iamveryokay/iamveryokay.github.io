Title: Pelican使用指南
Date: 2019-02-07
Category: Misc
Modified: 2019-02-07 20:37
Tags： Pelican

<s>这个是测试</s>

# 安装pelican
* `pip install pelican markdown`，注意markdown一定要装，不然用markdown报的错误是没有找到文件之类的。

# 生成pelican
* `pelican -s pelicanconf.py -o output content`，简写的话`pelican content`

# 预览pelican
* `python -m http.server port` 或者 `python -m pelican.server port`，然后在浏览器输入`localhost:8000`就可以看到，我的chrome好像有缓存，所以预览的时候还是原来的页面，重开了隐身模式才搞定。

# 从github第一次clone pelican
注意主题elegant是一个submodule([ref](https://git-scm.com/book/en/v2/Git-Tools-Submodules))，需要执行以下步骤：

* `git submodule init`
* `git submodule update`
这样以后主题就会下载下来，然后再`pelican content`、`nginx -s reload`就可以更新网页了。
* 以后可以用`git pull`来更新代码，然后`pelican content`、`nginx -s reload`

#  推送到 github

```
pelican content -o output -s pelicanconf.py
ghp-import output -b gh-pages
git push git@github.com:elemoine/elemoine.github.io.git gh-pages:master
```


