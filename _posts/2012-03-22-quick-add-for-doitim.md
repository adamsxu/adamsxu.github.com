---
layout: post
title: "Quick add for Doit.im"
category:
tags: [Alfred, Doit, extension]
---
{% include JB/setup %}

对于新事物或者变化，我们一般会抱着害怕或者抗拒的心理，只有到没有办法的时候才得不去做，由于时间紧张、态度上不是出于本意，效果可想而知。

之前 [@5key](https://twitter.com/#!/@5key)送了我一个[Alfred](www.alfredapp.com/)的PowerPack，让我做一个[Doit.im](http://doit.im/)的Quick Add，随手翻过Alfred extension的文档，粗粗看了一下觉得有点麻烦，就搁置了。

今天下午写代码的时候想到一些任务需要添加，每次去Web上添加，思路被打断，这个体验相当不好，所以想要一个快速添加任务的小工具，一开始打算用Objective-C重新写一个小应用，用Alfred打开XCode的时候，突然想到插件，另外又考虑到丑的应用我肯定不会用下去，但是设计暂时也找不到人，所以决定用Alfred的extension搞定。

看了官方文档以及人家的extension，发现基本上不是用PHP写，就是用Ruby写，都是写了长长一个教程，告诉用户先用git 拿到ruby的代码，然后执行一个命令，编辑一个文件将Token或者用户名密码填在某个位置，然后啪啦啪啦一堆话，彻底崩溃。

看文档里面提到支持AppleScript，找了本AppleScript教程开始，一点点试错，大概花了两个小时的时间将一个只支持标题快速添加完成。[@leeiio](https://twitter.com/#!/@leeiio)的兴趣也起来，他加上了Growl的支持。

地址：https://github.com/adamsxu/Quick-Add-for-Doit.im/downloads
BTW: 需要Alfred PowerPack支持

接下来会加入Smart add以及本地队列支持（防止网络不好的情况，任务添加失败导致丢失）