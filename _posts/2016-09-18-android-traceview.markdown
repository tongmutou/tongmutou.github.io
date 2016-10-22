---
layout:     post
title:      "Android性能调试工具Traceview使用"
subtitle:   "介绍一下Traceview的使用方法"
date:       2016-09-16
author:     "没什么了不起"
header-img: "img/post-bg-alitrip.jpg"
catalog: true
tags:
- Android Traceview
---

# Android性能调试工具Traceview使用

使用TraceView主要有两种方式：

最简单的方式就是直接打开DDMS，选择一个进程，然后按上面的“Start Method Profiling”按钮，等红色小点变成黑色以后就表示TraceView已经开始工作了。然后我就可以滑动一下列表（现在手机上的操作肯定会很卡，因为Android系统在检测Dalvik虚拟机中每个Java方法的调用，这是我猜测的）。操作最好不要超过5s，因为最好是进行小范围的性能测试。然后再按一下刚才按的按钮，等一会就会出现上面这幅图，然后就可以开始分析了。

第2种方式就是使用android.os.Debug.startMethodTracing();和android.os.Debug.stopMethodTracing();方法，当运行了这段代码的时候，就会有一个trace文件在/sdcard目录中生成，也可以调用startMethodTracing(String traceName) 设置trace文件的文件名，最后你可以使用adb pull /sdcard/test.trace /tmp 命令将trace文件复制到你的电脑中，然后用DDMS工具打开就会出现第一幅图了
