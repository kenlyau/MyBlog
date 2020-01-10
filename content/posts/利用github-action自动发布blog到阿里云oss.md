+++
categories = "tech"
date = 2020-01-10T15:00:00Z
layout = "post"
tags = ["aliyun", "github"]
title = "利用github-action自动发布blog到阿里云oss"

+++
* 1 创建action所需yml脚本文件，创建文件：.github/workflows/main.yml
* 2 编写脚本

  \`\`\`

      name: action name #脚本名称
      
      on: [push] #在push后执行脚本
      
      jobs:
        build:
          runs-on: ubuntu-latest #运行系统环境
          steps: #执行命令步骤
          - uses: actions/checkout@v1 #拉去最新代码
          

  \`\`\`