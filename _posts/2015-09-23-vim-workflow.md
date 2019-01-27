---
layout: post
title: "vim workflow"
categories: Software
tags: neovim software SpaceVim Vim
excerpt: vim 工作流
author: suliveevil
mathjax: true
---

* content
{:toc}


## Vim

## neovim


## vim 配置


### SpaceVim

```bash
$ curl -sLf https://spacevim.org/cn/install.sh | bash -s -- -h
SpaceVim 安装脚本 : V 1.0.0-dev

  这是 SpaceVim 初始化脚本，可用于定制安装、更新及卸载 SpaceVim。

使用

  curl -sLf https://spacevim.org/cn/install.sh | bash -s -- [选项] [对象]

所有选项

 -i, --install            为 vim 和 neovim 安装 SpaceVim
 -v, --version            显示当前安装脚本的版本
 -u, --uninstall          卸载 SpaceVim
 -c, --checkRequirements  检测环境依赖

使用示例

    默认同时为 vim 和 neovim 安装 SpaceVim

        curl -sLf https://spacevim.org/cn/install.sh | bash

    只为 vim 或者 neovim 单独安装 SpaceVim

        curl -sLf https://spacevim.org/cn/install.sh | bash -s -- --install vim
        curl -sLf https://spacevim.org/cn/install.sh | bash -s -- --install neovim

    卸载 SpaceVim

        curl -sLf https://spacevim.org/cn/install.sh | bash -s -- --uninstall
```

#### 配置SpaceVim



### spf13-vim



## 系统设置之 键盘映射

### CapsLock


<div class="mermaid">
graph TD;
    A[Alfred Workflow]--kep-->B[Karabiner Elements];
    C[Keyboard Maestro]--切换 KE Profile-->B;

    B-->F[CapsLock Profile];
    B-->G[Default Profile];

    F-->H[Hyper - CapsLock];
    F-->I[Esc - CapsLock];
</div>


## 参考资料

[wsdjeg/vim-galore-zh_cn: Vim 从入门到精通](https://github.com/wsdjeg/vim-galore-zh_cn)


[mac下neovim的使用体验](https://www.jianshu.com/p/5a879fb1311f)

[从Vim到NeoVim - iTimothy](https://xiaozhou.net/from-vim-to-neovim-2016-05-21.html)



