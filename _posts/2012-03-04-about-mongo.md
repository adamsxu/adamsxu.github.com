---
layout: post
title: "About Mongo"
category: 
tags: [database, mongodb]
---
{% include JB/setup %}

1. 尽量使用新版本，目前性能比较2.0.3 > 1.8.4 > 1.8.1
2. 在EC2上使用Mongo，建议使用Raid10 
 
	步骤：
		
		2.1 yes | sudo mdadm --create -l10 -n4 /dev/md0  /dev/sdh1 /dev/sdh2 /dev/sdh3 /dev/sdh4
		2.2 echo DEVICE /dev/sdh1 /dev/sdh2 /dev/sdh3 /dev/sdh4 | sudo tee /etc/mdadm.conf 
		2.3 sudo su
		2.4 mdadm -Ds >> /etc/mdadm.conf
		2.5 sudo mkfs.ext4 /dev/md0
		2.6 sudo sed -i '$ a\/dev/md0 /data ext4 defaults,auto,noatime,noexec,nodiratime 0 0' /etc/fstab
		2.7 sudo mkdir /data
		2.8 sudo mount /dev/md0
		
	如果使用Amazon Linux，他的/etc/rc.sysinit是有问题的，不会自动加载，需要将/etc/rc.sysinit中的
		
		[ -r /proc/mdstat -a -r /dev/md/md-device-map ] && /sbin/mdadm -IRs		
		修改成		
		[ -r /proc/mdstat ] && /sbin/mdadm --assemble --scan
		
	
3. 索引使用要谨慎，越少越好，这个需要在Schema设计的时候需要注意
