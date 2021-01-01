+++
categories = "tech"
date = 2020-12-31T16:00:00Z
draft = true
layout = "post"
tags = ["golang"]
title = "golang开发自动刷新_fresh"

+++
`开发golang项目时，频繁的build查看效果实在麻烦，直到我遇到了这个项目，[`[`https://github.com/gravityblast/fresh`](https://github.com/gravityblast/fresh "https://github.com/gravityblast/fresh")`] ,监听文件的改变，自动的build整个项目。`

* 1 安装

      go get github.com/pilu/fresh
* 2 使用方法

      cd /path/to/myapp
      fresh