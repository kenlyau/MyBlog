---
layout: post
title:  "nginx vhost proxy config"
date:   2016-11-16 22:06:25
categories: technique
tags: [nginx,linux,server]
---


{% highlight ruby %}
    server {
		server_name abc.com;
		location / {
			proxy_redirect off;
			proxy_set_header Host $host;
			proxy_set_header X-Real-IP $remote_addr;
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
			proxy_pass http://xxx.com;
		}
		access_log /root/tmp/logs/abc.com.log;
	}
{% endhighlight %}


[jekyll]:    http://jekyllrb.com
