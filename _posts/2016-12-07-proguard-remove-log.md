---
layout:     post
title:      "使用Proguard移除代码中的Log代码"

date:       2016-12-06
author:     "tong木头"
header-img: "img/post-bg-alitrip.jpg"
catalog: true
tags:
- Android
---

# 使用Proguard移除代码中的Log代码

修改Proguard的配置文件，添加以下配置：

	-assumenosideeffects class android.util.Log {
	
		public static int v(...);
		
		public static int i(...);
		
		public static int w(...);
		
		public static int d(...);
		
		public static int e(...);
	
	}
	
可以根据需要在发布时候显示的级别来决定移除哪些级别的Log(需要移除的就放到配置中)，同时Proguard的配置中还要注意不要有`dontoptimize`这个配置。