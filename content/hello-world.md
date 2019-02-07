Title: 在Nginx上配置Pelican
Date: 2019-01-06
Category: Misc
Tags: Centos, Pelican, Nginx

# 安装Pelican
## 安装scl
* `yum install centos-release-scl`
* `sudo yum install rh-python36`
* `scl enable rh-python36 bash` 如果要退出，可以按`exit`

## 创建虚拟环境（可选）
* `python -m venv my_web_venv` 创建虚拟环境
* `source my_web_venv/bin/activate`

## 正式安装Pelican
* `pip install pelican`
* `pip install markdown` 如果想用 `markdown`的话
* `pelican quick-start` 快速创建 [ref](http://docs.getpelican.com/en/stable/)
* 开始你的写作

# 安装Nginx
Nginx不在官方的Centos仓库中，需要额外添加EPEL仓库。
## 添加EPEL

[ref](https://www.tecmint.com/how-to-enable-epel-repository-for-rhel-centos-6-5/)

* `wget http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm`
* `rpm -ivh epel-release-latest-7.noarch.rpm`
* `yum repolist disabled` 显示没有激活的源
* `yum repolist enabled` 显示激活的源
* `yum repolist all`
## 使用Nginx下载EPEL
* `yum --enablerepo=epel info nginx` 显示nginx信息
* `yum --enablerepo=epel install nginx`

## 配置Nginx

* 到`/etc/nginx/nginx.conf`配置，`user nginx`改成`nginx root`（我是root，不知道会不会有风险...）
* 修改`server`模块里面修改`server_name your_domain`
* 修改`root /usr/share/nginx/html` -> `root your_pelican_dir/output`
* `service nginx restart`，以后可以热启动`nginx -s reload`


