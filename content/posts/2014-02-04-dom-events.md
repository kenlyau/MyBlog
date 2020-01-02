---
layout: post
title:  "dom事件流"
date:   2014-02-04 1:06:25
categories: technique
tags: [javascript,dom]
---

### 标准事件流
* 标准浏览器支持：事件捕获-事件目标-事件冒泡
* IE旧浏览器（ie8-）：事件目标-事件冒泡

### DOM 0级事件
{% highlight ruby %}
element.onclick = function() {
	//something
};
{% endhighlight %}


### DOM 2级事件
{% highlight ruby %}
//w3c
element.addEventListener("click", function(event) {
	//something
},false//取消捕获保持和ie一致);
//ie8-
element.attachEvent("click", function(event) {
	//something
});
{% endhighlight %}

###事件系统
* ie与Opera
{% highlight ruby %}
绑定事件：element.attachEvent("on"+type, callback);
卸载事件：element.detachEvent("on"+type, callback);
创建事件：document.createEventObject();//事件主体document
派发事件：element.fireEvent(type, event);
{% endhighlight %}

* w3c
{% highlight ruby %}
绑定事件：element.addEventListenser(type, callback, [boolean]);
卸载事件：element.removeEventListenser(type, callback, [boolean]);
创建事件：element.createEvent(types);
初始化事件：event.initEvent();
派发事件：element.dispatchEvent(event);
{% endhighlight %}

###事件对象
* bubbles-Boolean-事件是否冒泡
* stopPropagation()-function-取消事件捕获或冒泡，如果bubbles为true，可以使用(ie下：cancelBubble=true)
* cancelable-Boolean-是否可以取消事件默认行为
* currentTarget-element-事件处理程序当前处理事件的那个元素
* defaultPrevented-Boolean-是否已经调用preventDefault()
* preventDefault()-function-取消事件默认行为，如果cancelable是true，可以使用（ie下：returnValue=false）
* target-element-事件目标(ie下：srcElement)
* type-string-事件类型

[kelyau.github.io][link]

[link]:    https://kelyau.github.io
