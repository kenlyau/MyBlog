---
layout: post
title:  "upgrade Jekyll v3"
date:   2017-06-15 13:47:09 +0800
categories: technique
tags: [jekyll]
---

升级jekyll到3.3版本，从2.x版本到3.x版本据说是提高了生成静态页面的速度，无奈我的文章太少无法享受到。

3.x引入了bundle这个ruby的东西
> gem install bundle

> gem update jekyll

新的分页插件已重默认中移除，需要重新安装一下
> gem install jekyll-paginate

但是我是没有成功的，原因是在模板中无法使用 " paginator.posts" 这个日志数组，官方说的是这个只能在index.html 这种模板中才能用，然后我还是没有成功。

这里我找了一个替代插件，"jekyll-paginate-v2"
> gem install jekyll-paginate-v2

### 修复jekyll-paginate-v2引发的github pages无法生成首页的问题

重新看了下官方文档，将根目录下的index.md 修改为 index.html

[https://github.com/sverrirs/jekyll-paginate-v2]
