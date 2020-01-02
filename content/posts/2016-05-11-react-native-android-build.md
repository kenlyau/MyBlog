---
layout: post
title:  "react-native android build"
date:   2016-05-11 10:38:15
categories: technique
tags: [javascript,react-native,app]
---

### 1. 权限不足
直接 react-native run-android 出现错误，然后换用 sudo react-native run-android 成功，估计是我自己安装的权限问题，按理应该不会出现这种问题。

### 2. gradle-2.4-all.zip 下载超级慢，有时候还直接报错
这个文件我直接下载很快，但是就在cli里面很慢，解决办法就是替换掉下载路径，我直接改到本地路径
{% highlight ruby %}
    ./android/gradle/wrapper/gradle-wrapper.properties
    #distributionUrl=https\://services.gradle.org/distributions/gradle-2.4-all.zip
    distributionUrl=http\://localhost/gradle-2.4-all.zip
{% endhighlight %}

### 3. SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.
这个问题是头天晚上留下的，本来以为ok了，结果还是出问题了，夜太晚，老婆还在催，只有留到今天来处理<br>
网上搜索了，全都指向的是ANDROID_HOME没配置，但是不应该呀，echo $ANDROID_HOME 打印出来是有配置的，继续扩大搜索范围，在stackoverflow上讲  Android Studio 的错误找到了相似的错误，以下直接复制，说的是在android目录下面创建个文件，local.properties，内容就一行 sdk.dir=/Applications/Android Studio.app/sdk
{% highlight ruby %}
 Try adding a new file in the root of your project called "local.properties" (or modify the existing one). It should contain

sdk.dir= 
followed by the path to the sdk location, in my case

sdk.dir=/Applications/Android Studio.app/sdk
I think Android Studio normally creates one automatically but says that it shouldn't be added to VCS. I put it in my .gitignore and cloned the project on my Mac which resulted in this error. Strangely before 0.1.5 it worked just fine without the file.
{% endhighlight %}
### 4. Package com.myproject signatures do not match the previously installed version;
我可以确定这个是最后一个难题了，中间误入歧途，还好这个技能还算有用，这里就记录下,在android目录下面，运行[./gradlew assemble] 这样就可以生成新的apk包，这个包直接安装即可调试。但是还是没有解决[react-native run-android]无法启动模拟器的问题，无奈下换到百度搜索，在百度翻译中出现[包com.myproject签名不匹配，以前安装的版本],瞬间石化，也再次说明了一门外语的重要性。在前天第一次安装环境中我误打误撞是运行成功过的，里面的程序还在，卸载，然后重新运行[react-native run-android]成功运行模拟器。
### 5. 总结下来第一次的成功是侥幸的，也给后来增加的麻烦，经过这一次完整的环境搭建过程，我想RN的android运行环境对我来说已经不算难事的。




[kenlyau.github.io][link]

[link]:    https://kenlyau.github.io
