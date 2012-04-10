---
layout: post
title: "Android Develop Tips"
category: 
tags: [Android, Tips]
---
{% include JB/setup %}

1. Emulated memory size.
	
	在~/.android/avd/下面找到对应.avd和.ini文件。
	加入 `hw.ramSize = 1024MB`
2. Enable Snapshots.
	
	创建虚拟机的时候，记得勾选 Snapshot Enabaled
	启动的时候，在Launch Options上勾选上Launch from snapshot 和 Save to snapshot
	如果想保持虚拟机的环境不变，则在保存过一次之后，以后启动的时候，将 Save to snapshot勾选去掉。
3. IDEA 在MacOS 不读取.bash_profile里面的信息。只能在/etc/launchd.conf 中设置。 

	setenv ANDROID_HOME /android/home

且需要重启机器。如果不想重启机器的话，则使用命令行

	launchctl setenv ANDROID_HOME /android/home

重启IDEA即可。