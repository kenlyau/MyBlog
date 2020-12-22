+++
categories = "tech"
date = 2020-12-21T16:00:00Z
layout = "post"
tags = ["Android", "apk"]
title = "apk文件反编译与重新打包签名"

+++
### 1反编译工具 apktool

* 1）工具项目地址：[https://ibotpeaches.github.io/Apktool/](https://ibotpeaches.github.io/Apktool/ "https://ibotpeaches.github.io/Apktool/")
* 2）反编译 \`apktool d xxx.apk -o xxx\`
* 3）重新打包 \`apktool b xxx\`

       会在xxx目录下dist下生成apk文件

### 2 签名

* 1）生成签名证书 \`keytool -genkey -alias android.keystore -keyalg RSA -validity 20000 -keystore android.keystore\`
* 2）apk文件签名 \`jarsigner -verbose -sigalg SHA1withRSA -digestalgSHA1 -keystore android.keystore -signedjar xxx_signed.apk xxx.apk  android.keystore\`