---
layout:     post
title:      "LayoutTransition--Android布局变化时的动画实现"

date:       2017-07-07
author:     "tong木头"
header-img: "img/post-bg-alitrip.jpg"
catalog: true
tags:
- Android
---

# 介绍

在开发中经常会动态的改变`ViewGroup`中子`View`的状态，比如改变子`View`的可见性。默认是没有动画效果的，看起来会比较生硬。这个时候如果加上一个过渡动画就再好不过了，方法也很简单，就是用`LayoutTransition`。Android在api11提供了该类。

# 用法
## 1. 在xml中配置动画

```
android:animateLayoutChanges="true"
```

## 2. 在代码中添加动画


```
ViewGroup  container = (ViewGroup) findViewById(R.id.container);
LayoutTransition transition = new LayoutTransition();
container.setLayoutTransition(transition);
```

注意不管是`xml`还是代码都是加在`ViewGroup`上面的，之后该`ViewGroup`的子`View`状态改变时就会显示动画了。

# 自定义动画效果
先来介绍一个在设置个性化参数时常用的5个参数

```
APPEARING 作用于在容器中出现的view
CHANGE_APPEARING 作用于那些因为新view出现而发生变化的view
CHANGE_DISAPPEARING 作用于那些因为view消失而发生变化的view
CHANGING 不是因为有view出现或者消失，而是因为layout位置发生变化，api16添加
DISAPPEARING 作用于在容器中消失的view
```
设置动画时长


```
LayoutTransition transition = new LayoutTransition();
transition.setDuration(LayoutTransition.APPEARING, 800);
```


设置动画开始的延迟时间


```
LayoutTransition transition = new LayoutTransition();
transition.setStartDelay(LayoutTransition.APPEARING, 0);
```

使用自己自定义的动画


```
LayoutTransition transition = new LayoutTransition();
ObjectAnimator appearAnim = ObjectAnimator  
                .ofFloat(null, "rotationY", 90f, 0)  
                .setDuration(800); 
transition.setAnimator(LayoutTransition.APPEARING, appearAnim);
```

