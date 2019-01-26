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

<mark>1 $$f_{x}^{y}$$</mark>

<div style="background:yellow">
    2 $$f_{x}^{y}$$
</div>

<div style="background:yellow">
    <p>3 $$f_{x}^{y}$$</p>
</div>

<div>
    <p>
        <span style="background:yellow">4 $$f_{x}^{y}$$</span>
    </p>
</div>

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

## Jekyll tricks

### tags 中添加空格


`AB&#160;C` 展示为：`AB C`



