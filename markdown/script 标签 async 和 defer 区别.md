---
title: script 标签 async 和 defer 区别
tags: js基础
date: 2019-4-2
categories:  编程
---


![蓝色线代表网络读取，红色线代表执行时间，这俩都是针对脚本的；绿色线代表 HTML 解析](https://www.github.com/aa875982361/plingWeb/raw/master/markdown/1554188678161.png)

^[https://segmentfault.com/q/1010000000640869]这张图告诉我们以下几个要点：
1. defer 和 async  在网络读取的时候都是异步的，
2. 他们的差别在于执行时间，async 是资源下载完成就马上执行， defer 是按照加载顺序执行脚本 相当于是执行时间放在了最后面  
3. 如果没有async 和 defer的话  HTML文件 解析遇到 script 标签会 停止解析 下载资源文件，等到下载完成 执行完毕之后，再继续HTML的解析。
4. 另外 script 的js文件执行 都是在window.onload 事件之前执行^[https://juejin.im/post/5a1229596fb9a0451704cae8]


