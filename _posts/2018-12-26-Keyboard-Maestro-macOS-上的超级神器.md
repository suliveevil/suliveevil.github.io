---
layout: post
title:  "Keyboard Maestro - macOS 上的超级神器"
categories: macOS Automation Software
tags: automation KeyboardMaestro macOS-automation software 系统增强
excerpt: Keyboard Maestro 是我在 macOS 下买的最超值的软件之一。
author: suliveevil
mathjax: true
---

* content
{:toc}

## 购买

Keyboard Maestro （以下简称KM）能做的事情其实大都能通过系统本身+Automator（自动操作）、AppleScript、ShellScript 等来完成，但是写脚本的门槛也比较高。既然在 Keyboard Maestro 上能够“可视化编程”、可视化管理，何必大费周折自己去写脚本、指定快捷键呢？还有就是KM作为一个超级app，总是使用破解版实在是心里不安，这是我购买的理由。

## 优惠

Stacksocial 有 KM 的优惠活动，优惠价格19刀，新用户打完折16刀多一点。

[suliveevil 的 Stacksocial 专属优惠链接，貌似还能再省一点](https://stacksocial.com/?rid=6246484)

## 使用

### 工作流 Workflow

工作流（workflow）

举个最简单的例子：

～～～～～～～～～～～～～～～我是🌰的分割线～～～～～～～～～～～～～～～

假如你需要截图时隐藏当前桌面，截图后恢复桌面显示，那么你需要做的就是：

在截图前打开终端运行命令行：

```bash
defaults write com.apple.finder CreateDesktop -bool false;killall Finder
```

2. 按下系统快捷键⇧⌘3（或4、5，6截 TouchBar 的图故无需设置）来截图

3. 打开终端运行命令行：

```bash
defaults write com.apple.finder CreateDesktop -bool true;killall Finder
```

4. 回到桌面处理刚才的截图

这是一个完整的工作流程（workflow），但关键在于你需要切换到终端两次，并输入一堆字母，这样的重复性劳动交给 KM 再合适不过了，而且出于我暂时不清楚的原因，把脚本交给 KM 运行比打开终端再运行要快不少（可能是因为终端.app是一个带图形界面的软件，而 KM 直接把脚本交给了系统来执行？）。

那么如何使用系统自带工具来优化这个工作流呢？

方案一：

快速打开终端.app ➡️ 给终端.app设置专属快捷键“一键启动”
2. 快速输入命令行 ➡️ 给命令行设置文本替换，代替手动输入

3. 快速返回 ➡️ 为桌面文件夹设置专属快捷键“一键启动”

方案二：

使用 Automator 创建 workflow，编写规则代替部分手动操作。

如何使用 KM 来优化这个工作流呢？

以下是我的方案（待完善）：

待补充


截图&amp;amp;录屏时隐藏桌面（待完善）
用 Shift + Control + 3/4/5 来执行以下操作：

执行隐藏桌面脚本
调用系统快捷键 Shift + Command + 3/4/5 截图
暂停5秒（给手动截图、录屏留时间）
执行显示桌面脚本
这样既不影响系统默认快捷键、也能很好的满足截图时隐藏桌面的需求，而且你的快捷键可以在 KM 里统一管理（我给截取全屏、截取区域、录屏等分配了不同的快捷键来对应系统默认快捷键）。

～～～～～～～～～～～～～～～我是🌰的分割线～～～～～～～～～～～～～～～

### 窗口管理

是的，我认为macOS的窗口管理实在是太糟糕，不得不用软件来实现自己想要的效果。

Spectacle（非Mac App Store，免费），你值得拥有。

Hammerspoon（非Mac App Store，免费），神器，但是不稳定。

Mosaic（非Mac App Store 软件，收费）拖拽调整窗口布局的视觉效果实在是太丑了，非常不建议购买。

BetterTouchTool（非Mac App Store，收费）、BetterSnapTool（Mac App Store，收费）：为MacBook的触控板而生，喜欢触控板操作的可以考虑。

Magnet（Mac App Store，收费）作为 MAS 里品类第一的app还是值得购买的（如果你不想买 KM 的话），使用快捷键调整窗口布局是一种比较高效的做法。

Keyboard Maestro（非Mac App Store，收费）超级神器，KM，顾名思义，键盘大师，你可以定制自己的窗口管理快捷键。我的设置是 Control + Option + H/J/K/L调整当前窗口为二分之一布局，Control + Option + ⬅️➡️⬆️⬇️调整当前窗口为四分之一布局。

### 文本输入增强

macOS 和 iOS自带的文本替换功能太弱，无法插入变量，无法指定光标位置。

KM 的文本替换能让你“为所欲为”。

举个例子：

～～～～～～～～～～～～～～～我是🌰的分割线～～～～～～～～～～～～～～～

假如我剪切了一个网页链接，想要：

把它粘贴到 markdown 文档里
2. 设置为 markdown 的超链接格式

3. 把光标移动到标题位置进行编辑

通过 KM 可以设置为：


本地链接格式化

输入 `lljj` 激活 KM 的 macro，并自动将它转换为 markdown 链接格式，并将光标移动到标题位置 `[光标移动到这里](我剪贴板里的网页链接)` 甚至还可以设置为直接把当前浏览器窗口中的链接的标题和网址链接插入到当前文档中：

```text
[%FrontBrowserTitle%](%FrontBrowserURL%)
%|%
```

～～～～～～～～～～～～～～～我是🌰的分割线～～～～～～～～～～～～～～～

软件之间的互动

macOS 三大神器 Alfred、Karabiner-Elements、Keyboard Maestro 的伟大结合：

Keyboard Maestro 可以设置快捷启动 Alfred、Karabiner-Elements的快捷键。

搭配 Karabiner-Elements（非Mac App Store，免费），KM 可以识别出你的设备上的所有按键操作（比如 MacBook Pro 13 mid 2018上的神奇的 Caps Lock键 ）。

搭配 Alfred 的 Workflow 可以在 Alfred 的搜索框中搜索 Karabiner-Elements 的 Profile 并切换，搜索 Keyboard Maestro 中的 macro 并执行。

其他

KM 还有很多神奇的功能可以实现，它的价值远远超过了它的价格，期待你的发现和分享。