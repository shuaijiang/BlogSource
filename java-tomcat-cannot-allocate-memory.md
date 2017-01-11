---
title: 启动tomcat报错  “Cannot allocate memory (errno=12)”解决方法
date: 2017-01-06 16:19:53
tags:  [Java, 计算机]
---

# 问题
启动tomcat statup.sh，直接报错了： VM warning: …… error='Cannot allocate memory' (errno=12)。

就是说内存不够了，查看了下内存还剩余大约1GB，但是对于要启动的程序是够的。

网上查找了一些资料，断定是Java VM的内存分配问题。

JVM初始分配的内存由-Xms指定，默认是物理内存的1/64；
JVM最大分配的内存由-Xmx指定，默认是物理内存的1/4。

默认空余堆内存小于40%时，JVM就会增大堆直到-Xmx的最大限制；
空余堆内存大于70% 时，JVM会减少堆直到-Xms的最小限制。
因此服务器一般设置-Xms、-Xmx相等以避免在每次垃圾回收后调整堆的大小。

# 解决方法
修改tomcat的bin中catalina.sh的配置。修改JAVA_OPTS，调整-Xms 和 -Xmx 到合适的值。

我将之前的 -Xms4096m -Xmx4096m 修改成 -Xms2048m -Xmx2048m

重启tomcat成功。

