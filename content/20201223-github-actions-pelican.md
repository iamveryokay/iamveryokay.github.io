Title: Github Actions 部署 Pelican
Date: 2020-12-23
Category: Misc
Modified: 2020-12-23 23:20
Tags: github, Actions

# 坑

## 1

如果不是建立了 `username.github.io` 的仓库，需要在 `gh-pages` 分支下建立网页，此时需要在 `pelicanconf.py` 中把 `SITE_URL` 字段设置成 `https://username.github.io/repo-name`，否则无法设置选中的主题。

## 2

`CRITICAL: argument of type 'NoneType' is not iterable`

要选择 `elegant` `next` 分支，有个bug在里面 ~~**TODO 如何拉取submodule中的别的分支？**~~ -> 已解决，直接 `cd` 到这个目录里面，然后 `git fetch`, `git checkout next`，具体看 `entrypoint.sh` 里面的代码，这个使用的前提是当前的本地只有一个 `remote` 才行。

