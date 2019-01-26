---
layout: post
title: "Straight Insertion Sort 直接插入排序"
categories: Math Python
tags: algorithm math Python
excerpt: Python 直接插入排序
author: suliveevil
mathjax: true
---

* content
{:toc}
## 直接插入排序

直接插入排序（Straight Insertion Sort）:时间复杂度O(n^2)：将一个记录插入到已经排好序的有序表中，从而得到一个新的、记录数增1的有序表。

```python
#!/usr/bin/env python
# -*- coding:utf-8 -*-

class SQList:
    def __init__(self, lis=None):
        self.r = lis

    def insert_sort(self):
        lis = self.r
        length = len(self.r)
        # 下标从1开始
        for i in range(1, length):
            if lis[i] < lis[i-1]:
                temp = lis[i]
                j = i-1
                while lis[j] > temp and j >= 0:
                    lis[j+1] = lis[j]
                    j -= 1
                lis[j+1] = temp
    
    def __str__(self):
        ret = ""
        for i in self.r:
            ret += " %s" % i
        return ret

if __name__ == '__main__':
    sqlist = SQList([4, 1, 7, 3, 8, 5, 9, 2, 6, 0])
    sqlist.insert_sort()
    print(sqlist)
```

## 参考资料

《大话数据结构》

[基于python的七种经典排序算法 - 刘江liujiangblog.com](https://www.cnblogs.com/feixuelove1009/p/6143539.html)

