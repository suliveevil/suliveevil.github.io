---
layout: post
title: "Jekyll markdown test"
categories: 随笔
tags: graph Jekyll  KaTeX math markdown MathJax
excerpt: markdown mermaid
author: suliveevil
mathjax: true
---

* content
{:toc}

## Jekyll kramdown


## Math

### highlight


<mark>$$f_{x1}^{y}$$</mark>

<!-- <mark style="color:yellow">$$f_{x}^{y}$$</mark> -->

<!-- <p style="background:yellow">$$f_{x}^{y}$$</p> -->

<ins style="background:yellow">$$f_{x2}^{y}$$</ins>

<!-- <p><ins style="background:yellow">$$f_{x2}^{y}$$</ins></p> -->

<!-- <div>
    <ins style="background:yellow">$$f_{x2.1}^{y}$$</ins>
</div> -->

<!-- <div style="display: inline-block">
    <ins style="background:yellow">$$f_{x2.3}^{y}$$</ins>
</div> -->

<!-- <div style="width:auto; text-align: center">
    <div style="background:yello; display: inline-block">
        $$f_{x3}^{y}$$<br>
        <ins style="background:yellow">$$f_{x2.2}^{y}$$</ins>
    </div>
</div> -->

<!-- <div style="background:yellow">
    2 $$f_{x}^{y}$$
</div>

<div style="background:yellow">
    <p>3 $$f_{x}^{y}$$</p>
</div>

<div>
    <p>
        <span style="background:yellow">4 $$f_{x}^{y}$$</span>
    </p>
</div> -->

<!-- <table>
    <tr>
         <td bgcolor=yellow>$$f_{x9}^{y}$$</td>
    </tr>
</table> -->

<!-- <table style="background:yellow">
    <tr>
        <td>$$f_{x2}^{y2}$$</td>
    </tr>
</table> -->

<!-- <body>
    <table>
        <tr>
            <td bgcolor=yellow>$$f_{x9}^{y}$$</td>
        </tr>
    </table>
</body> -->

### MathJax

### KaTeX

## Graph

### mermaid

```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->John: Hello John, how are you?
    loop Healthcheck
        John->John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail...
    John-->Alice: Great!
    John->Bob: How about you?
    Bob-->John: Jolly good!
```

<div class="mermaid">
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
</div>

<div class="mermaid">
sequenceDiagram
    participant Alice
    participant Bob
    Alice->John: Hello John, how are you?
    loop Healthcheck
        John->John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail...
    John-->Alice: Great!
    John->Bob: How about you?
    Bob-->John: Jolly good!
</div>

## Jekyll tricks

### tags 中添加空格


`AB&#160;C` 展示为：`AB C`


## 参考资料

[CSDN-markdown编辑器语法—背景色 - 无知人生，记录点滴](https://blog.csdn.net/testcs_dn/article/details/45766819)

