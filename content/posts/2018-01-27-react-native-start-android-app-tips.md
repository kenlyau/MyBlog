---
layout: post
title:  react-native-start-android-app-tips
date:   2018-01-27 17:06:25
categories: technique
tags: [react-native, react]
---


#### 设置hot reloading （热更新）
系统菜单设置 enable hot reloading

#### 不知道怎么调出系统菜单，这个怎么办，使用下面的adb命令
adb shell input keyevent KEYCODE_MENU

### 小米系统怎么了，小米拦截了这条命令，没反应，但是可以摇一摇手机调用调试菜单。然后我的手机尾插坏了，不稳定，没法摇动。
有人开发了 Frappe 这个程序，可以在电脑上通过adb调试指令，和摇一摇。

### 小米系统怎么了，还是没反应
系统->开发选项->miui优化 关闭

### 小米系统怎么了，马蛋。有反应了，但是反应没对
重装系统，换flyme。
