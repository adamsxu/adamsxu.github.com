---
layout: post
title: "Android Test Project"
category: 
tags: [Android, Test]
---
{% include JB/setup %}

在IDEA里面用跑Android的测试代码的时候，会提示

	JUnit version 3.8 or later expected:

那是因为android.jar里面带了一个JUnit造成的，只要将Junit 3.8以上的版本放在android.jar的上面优先加载即可
