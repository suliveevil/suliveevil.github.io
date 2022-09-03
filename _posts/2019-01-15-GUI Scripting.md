---
layout: post
title: "【AppleScript】GUI Scripting"
categories: Automation macOS
tags: AppleScript BetterAndBetter GUI&#160;Scripting Keyboard&#160;Maestro macOS macOS&#160;Automation
excerpt: AppleScript 脚本 GUI Scripting
author: suliveevil
mathjax: true
---

* content
{:toc}


## 点击“自动隐藏和显示菜单栏”而不弹出系统偏好面板

```applescript
-- 系统偏好设置
tell application "System Preferences" to reveal the ¬
-- 锚点
    anchor named "main" of ¬
-- 通用面板
    pane id "com.apple.preference.general"

-- 系统事件
tell application "System Events" to tell ¬
-- 系统偏好
    process "System Preferences" to tell ¬
-- 系统偏好 - 通用
    window "通用" to tell ¬
-- 点击“自动隐藏和显示菜单栏”
    checkbox "自动隐藏和显示菜单栏" to ¬
    perform action "AXPress"

-- 退出系统偏好
quit application "System Preferences"
```

## System Events

&#160;&#160;&#160;&#160;System Events 是 GUI Scripting 的最底层框架，再往上是 app，然后是 app 的窗口，然后是 app 窗口中的按钮，最后就是模拟键鼠操作

## UI 元素

UI 元素 是 GUI Scripting 的关键


```applescript
-- 获得 app 的所有可用于操作的 UI 元素
tell application "System Events"
    tell process "app name" -- 告诉 app
        entire contents -- 获取所有 UI 元素
    end tell
end tell
```

## anchor pane GUI


anchor 定位不到触控板的设置，那就换一种方法，利用系统自带的 Accessibility Inspector 查看 app 的 GUI 元素信息。



## 系统偏好设置.app

&#160;&#160;&#160;&#160;但是对于系统偏好设置.app 而言，它没有“contents”，而是以 pane 和 anchor 的形式存在。


```applescript
tell application "System Preferences"
-- 列出所有 pane 的 ID set paneList to id of every pane
-- 列出所有系统偏好设置app内的 anchor。
    set anchorList to name of anchors of pane id "com.apple.preference"
-- 列出系统偏好设置app里的 trackpad pane（面板）的 anchcor。
-- set anchorList to name of anchors of pane id "com.apple.preference.trackpad"
end tell
```

我这里有 32 个 pane （面板，系统本身有 30 个 pane ），也就是你打开系统偏好设置.app 后看到的那 32（系统自带 30）个 图标，每一个图标就是一个 pane 。

如果你安装（官网安装包安装，非 Homebrew 安装）过 MySQL、Flash 或者 Jitouch，你就知道 pane 是什么了。

## not sign

GUI Scripting 而不显示窗口的关键。

```applescript
¬
```

这个符号是数学运算符 “not sign”的意思。
参考 Unicode CodeCharts version 12 - Mathematical Operators - relations - 00AC ¬ Not Sign