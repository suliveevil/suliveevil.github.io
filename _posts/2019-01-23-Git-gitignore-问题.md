---
layout: post
title:  "git cache gitignore"
categories: git
tags: Git
author: suliveevil
mathjax: true
---

* content
{:toc}

## git

## 解决 gitignore 不生效

```bash
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```

压缩为一行

```bash
git rm -r --cached . && git add . && git commit -m 'update .gitignore'
```

