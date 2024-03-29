---
title: Android 应用全局字体调节或禁止随系统字体大小更改
tags: [android,字体]
date: 2019-02-21
categories: android
---

# Android 应用全局字体调节或禁止随系统字体大小更改

应用全局字体调节或禁止随系统字体大小更改

<!--more-->

## 1.禁止跟随系统字体大小调节
在Application中复写getResources()方法

```
    @Override
    public Resources getResources() {//还原字体大小
        Resources res = super.getResources();
        Configuration configuration = res.getConfiguration();
        if (configuration.fontScale != 1.0f) {
            configuration.fontScale = 1.0f;
            res.updateConfiguration(configuration, res.getDisplayMetrics());
        }
        return res;
    }  

```

## 2.应用全局字体大小调节
在Application中复写getResources()方法
```
    @Override
    public Resources getResources() {//还原字体大小
        Resources res = super.getResources();
        Configuration configuration = res.getConfiguration();
        if (configuration.fontScale != fontScale) {//fontScale要缩放的比例
            configuration.fontScale = fontScale;
            res.updateConfiguration(configuration, res.getDisplayMetrics());
        }
        return res;
    }  

```

## 3.Android 8.0适配
Android 8.0上会发现这样修改字体的缩放比例是不起作用的，
需要在Activity中同样进行复写getResources()方法。


## 4.整个应用字体大小调节方案
在设置界面进行字体缩放比例调节，退出时关闭所有已打开的Activity，并重启主界面。

```
 @Override
    public void onBackPressed() {
        saveFontScaleRate();
    }
    private void saveFontScaleRate() {
        if (defaultFontScaleRate != fontScaleRate) {
            new SpUtils(FontScaleActivity.this).putData(ICourtApplication.FONT_SCALE_RATE, fontScaleRate);
            BaseApplication.setFontScale(fontScaleRate);
            AppManager appManager = AppManager.getAppManager();
            MainActivity activity = appManager.getActivity(MainActivity.class);
            appManager.finishAllActivity(activity);
            activity.recreate();
        } else {
            finish();
        }
    }

```

## 5.注意
所有想要缩放的控件，不只是TextView，任何控件，只需要将尺寸单位换成SP，自然，不想要随字体调节改变的也只需将SP换成其他单位

