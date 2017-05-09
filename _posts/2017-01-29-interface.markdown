---
layout: post
title:  "开发们一直说的接口到底是什么？"
date:  2017-01-29 12:20:38 +0800
category: The internet product
---
<p>做app产品的同学应该对接口这个词不陌生，催上线的时候经常听到开发”这个接口还有点问题“，”后台没把接口给我别找我“，”还有个接口需要测试一下“等等这些话，那接口到底是什么呢？</p>
<p>这篇文章主要面向对象是产品或设计的小伙伴，因此我尽量不涉及深层次的实现，如有任何疑惑请联系我的邮箱：libertyindeath@mail.com</p>
<p>在具体到接口是什么之前，我想先讲一下他们是怎么进行通信的，假设您公司的后台是使用php的，其与app即客户端之间的通信很类似现在很流行的B/S架构</p>
<p>B/S架构即为Browser/Server（浏览器服务器）架构,其由C/S架构演变而来。我们平时可以通过浏览器直观的看到其通信。</p>
<p>现在打开你电脑的浏览器（推荐chrome或火狐），按F12（mac用户command+option+i）进入开发者模式，大概是这个样子：</p>
![image](https://libertyindeath.github.io/2017-01-29-pic1.png)
<p>点击network并刷新页面，点击出现的interface.html，这时你会看到此次刷新浏览器进行的操作，即向服务器端请求了这个页面的数据，request url就是浏览器发送的请求链接，然后点击response，这个时候出现了这个页面的源代码，这就是服务器端给你返回的数据。</p>
![image](https://libertyindeath.github.io/2017-01-29-pic2.png)
![image](https://libertyindeath.github.io/2017-01-29-pic3.png)
<p>现在通过浏览器与服务器通信的过程知道了客户端如何获取数据的，下面我们来讲php与app之间通信的具体实现</p>
<p>通信过程中app端与浏览器一样对服务器进行地址请求，但不同的是用户在使用的过程中是看不到其请求的地址的，这些地址被封装在app里面。另一个不同之处是，我们之前看到服务器给浏览器返回的是html格式的页面源码，但app端请求到的数据格式是json或者xml格式的，这两个格式的文件如下图，这里只需知道长什么样子即可，想要深入了解的同学请自行Google</p>
![image](https://libertyindeath.github.io/2017-01-29-pic4.png)
![image](https://libertyindeath.github.io/2017-01-29-pic5.png)
<p>下面我用一张图来直观的表达这个通信过程：</p>
![image](https://libertyindeath.github.io/2017-01-29-pic6.png)
<p>app接口可以做的事：</p>
|获取数据|从数据库中或缓存中获取数据，然后通过接口数据返回给客户端|
|提交数据|通过接口提交数据给服务器，然后服务器入库处理或其他处理|
<p>
