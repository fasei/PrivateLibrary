---
title: activity类型singleTask启动的问题
tags: [android,基础]
date: 2018-11-29
categories: android
---

# activity类型singleTask启动的问题

假设在任务栈中存在该Activity的实例，再次启动的时候，也就不会重新去创建它的实例，onCreate方法并没有执行，也就获取不到Bundle传递过来的值。

此时，我们需要重写 onNewIntent()方法，

系统会回调其onNewIntent方法，并将 onNewIntent 接收的 intent设置给 Activity。

之后，我们可以在 onStart()方法中接收Bundle传递过来的值。
