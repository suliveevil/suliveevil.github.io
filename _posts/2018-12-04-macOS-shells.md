---
layout: post
title: "macOS shells"
categories: IT macOS Software
tags: IT macOS software ultimate-macOS
excerpt: shell 环境变量
author: suliveevil
mathjax: true
---

* content
{:toc}

## shell

### bash

### zsh


## macOS 环境变量

### macOS 系统环境变量加载顺序

```bash
# 系统级别
/etc/profile # 不建议修改
/etc/paths # 全局性修改
/etc/bashrc # 一般在此添加系统级环境变量

# 用户级别
~/.bashrc
~/.bash_profile # 用户级环境变量 Linux下为.bashrc
~/.bash_login # 若bash shell是以login方式执行时，才会读取此文件。该文件仅仅执行一次!
~/.profile
```

### 设置 PATH

```bash
# 设置 PATH 的语法：
export PATH=$PATH:PATH1:PATH2:PATH3

# 在终端中设置PATH：
echo 'export PATH=somepath:$PATH' >> ~/.bash_profile

# 查看
echo $PATH
```

### PATH 生效

一般环境变量更改后，需要电脑重启/用户重新登录后生效
使修改立即生效

```bash
# source FileName
# example
source ~/.zshrc
```

### 临时生效

```bash
# 临时生效 直接生效 只在当前shell及子shell中有效
export 变量名=变量值
```

### 设置别名

```bash
alias ll='ls -la'
```


