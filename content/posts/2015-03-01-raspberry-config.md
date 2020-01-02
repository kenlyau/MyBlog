---
layout: post
title:  "树莓派配置"
date:   2015-03-01 10:46:25
categories: technique
tags: [raspberry,Linux]
---

### 系统语言配置
- 当apt-get安装软件时，都会报一个相同的错误
{% highlight ruby %}
    perl: warning: Setting locale failed.
    perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_TIME = "zh_CN.UTF-8",
    ...
    ...
    LANG = "en_US.UTF-8"
    perl: warning: Setting locale failed.
    perl: warning: Please check that your locale settings:
{% endhighlight %}
- 真正的原因是perl为系统使用zh_CN.UTF-8，但系统不知道zh_CN.UTF-8是什么东西

#### 解决办法
安装一个中文语言，系统就知道zh_CN.UTF-8了，这个时候用perl就不会报错了
{% highlight ruby %}
    apt-get install language-pack-zh-hans
{% endhighlight %} 

### 更换国内apt源
{% highlight ruby %}
    # 加#注释掉官方地址
    deb http://mirrors.ustc.edu.cn/raspbian/raspbian/   wheezy main contrib non-free rpi
{% endhighlight %}
- 网上说这个事中科大的镜像，中科大是国内的Debian官方认可的源镜像，所以稳定性和速度都有保障！实测效果很好。    

### wifi的设置
- 找到 /etc/wpa_supplicant/wpa_supplicant.conf，
- 最下加入以下代码，然后sudo reboot
{% highlight ruby %}
    network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
    }
{% endhighlight %}


[kenlyau.github.io][link]

[link]:    https://kenlyau.github.io
