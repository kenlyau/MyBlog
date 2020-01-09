---
layout: post
title:  nginx-proxy-domain-issue
image: "/image/pawel_czerwinski_1.jpg"
date:   2018-06-10 22:06:25
categories: technique
tags: [nginx, liunx]
---

长期以来用阿里云的服务器，配置nginx来反向代理家里的树莓派（电信封了80端口，访问不方便，代理后网址美观多了），经常会发现网站打不开，重启nginx后恢复正常。一直没有深入分析问题，
刚好今天有时间可以好好看看到底是怎么回事。

- 1，直接打开nginx配好的网站无法打开502错误
- 2，直接打开树莓派的网站可以打开
- 3，在阿里云curl树莓派网站可以打开

从表现来看，猜测应该是nginx解析反向代理的域名的缓存引起的，电信的是动态IP，一段时候会变。百度一下，果然有。
http://www.hostloc.com/thread-443474-1-1.html，和我想的一直，nginx的dns缓存问题。也给了解决方案，那就直接用了。

```
server {
       listen      8080;
       server_name localhost;
       resolver 114.114.114.114 223.5.5.5 valid=3600s;
       resolver_timeout 3s;
       set $qq "**";
       location / {
          proxy_pass http://$qq;
       }
   }
 
 参数说明：

# resolver 可以在http全局设定，也可在server里面设定
# resolver 后面指定DNS服务器，可以指定多个，空格隔开
# valid设置DNS缓存失效时间，自己根据情况判断，建议600以上
# resolver_timeout 指定解析域名时，DNS服务器的超时时间，建议3秒左右

#注意：当resolver 后面跟多个DNS服务器时，一定要保证这些DNS服务器都是有效的，因为这种是负载均衡模式的，当DNS记录失效了(超过valid时间)，首先由第一个DNS服务器(114.114.114.114)去解析，下一次继续失效时由第二个DNS服务器(223.5.5.5)去解析，亲自测试的，如有任何一个DNS服务器是坏的，那么这一次的解析会一直持续到resolver_timeout ，然后解析失败，且日志报错解析不了域名，通过页面抛出502错误。
```

最后一条注意项，我没有注意，还是直接用的域名，但是nginx重启成功，先观察下。

### 2018.9.20 更新
后来发现还是不行，这很奇怪，索性更换阿里的tengine，问题解决
