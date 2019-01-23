---
layout: post
title:  "解决 gitignore 不生效问题"
categories: Git
tags: git
author: suliveevil
mathjax: true
---

* content
{:toc}

git gitignore




使用Git管理代码的过程中，可以修改.gitignore文件中的标示的方法来忽略开发者想忽略掉的文件或目录，如果没有.gitignore文件，可以自己手工创建。

新建的文件在git中会有缓存，如果某些文件已经被纳入了版本管理中，就算是在.gitignore中已经声明了忽略路径也是不起作用的，这时候我们就应该先把本地缓存删除，然后再进行git的push，这样就不会出现忽略的文件了。

```bash
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```

压缩为一行

```bash
git rm -r --cached . && git add . && git commit -m 'update .gitignore'
```

