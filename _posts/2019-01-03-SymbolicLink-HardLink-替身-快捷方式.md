---
layout: post
title: "SymbolicLink HardLink 替身 快捷方式"
categories: Automation Linux macOS Software Unix Windows
tags: APFS ext4 FileSystem Finder Linux macOS macOS&#160;Automation NTFS software Unix Windows
excerpt: 文件连接
author: suliveevil
mathjax: true
---

* content
{:toc}

## ln

&#160;&#160;&#160;&#160;对于硬连接来说，共享的是 inode，重新创建的同名文件不具有相同的 inode，因此于原来毫无干系。而对于软连接来说，它连接记录的是一个文件的绝对路径，因此当重新创建同名文件时候，软连接又重新生效了。


&#160;&#160;&#160;&#160;在 macOS 中，我们的程序对硬连接和软连接的差别：硬连接跟原来我操作的文件方式一模一样(平时操作的文件本身就是一个硬连接)，并会被文件系统计算同样的空间，而软连接的文件 size 则会是一个非常小的值，通常只有几 byte，另外对软连接的操作最终都会被映射成所对应文件的操作，当然我们也可以 NSFileManager 的 destinationOfSymbolicLinkAtPath:error:方法和 NSString 的 stringByResolvingSymlinksInPath 方法来转换成原始的文件路径。

### Symbolic Link 硬连接

&#160;&#160;&#160;&#160;硬连接：指向 inode 的地址。若两个文件，拥有同样的 inode，那么就产生了所谓的硬连接。严格的讲，我们在文件管理中看到的每一个文件，都是一个硬连接的表现。而我们常说的创建了一个文件的一个硬连接，就是对这个地址的一个拷贝。一个 inode 有一个或多个这样的连接指向它，正如我们程序中使用的指针一些，使用用指针对文件的修改都会让所有指向于该节点的连接产生同样的影响。不仅如此，硬连接还拥有类似于”自动内存管理”的机制，当你删除任意的一个硬连接，只要仍然还有其它的连接指向 inode 节点，那么该块文件的信息都不会被释放，只有当所有指向它的连接都已经删除，它才会被置为空闲状态。

&#160;&#160;&#160;&#160;对于硬连接来说，它的好处就是“安全”。你将其中任何一个文件名删除(rm -f)，文件都是存在的，因为文件的 inode 一直存在。并且由于两个文件都是对应的相同的 inode 和 block，因此对任何其中一个进行修改编辑，结果都会生效。

### Hard Link 软连接

&#160;&#160;&#160;&#160;软连接的意义如同 Windows 平台下的快捷方式，它是一个类型为 l 的文件，拥有自己的 inode 和 block，对它进行操作也相当于对被 link 文件进行操作。

&#160;&#160;&#160;&#160;软连接就正好就如同内存管理中的“指向指针的指针”，软连接本质就是指向硬连接的一个地址，自然它也只会对这一个硬连接有效，一旦软连接所指向的硬连接被删除，软连接也就失效了。当然这与”指针的指针”也有一个很微妙的差别，那就是你对软链接的操作都是通过跳转到硬连接再映射到了对节点的操作。

&#160;&#160;&#160;&#160;直接对一个文件(你所看到的这个文件其实已经就是一个硬连接了)创建一个 SymbolicLink，然后我修改文件的名字，SymbolicLink 仍然是可以正确的找到文件的，但当我删除了文件，那么 SymbolicLink 就永远失效了。

### 替身

&#160;&#160;&#160;&#160;通过 NSFileManager 取到的替身的 NSFileType 是 NSFileTypeRegular(普通文件类型)，也就是说替身是 macOS 独有的连接文件类型，并且是 Finder 层级的感念。

&#160;&#160;&#160;&#160;一些终端下的 Unix 程序（比如 vim）不能正确理解替身文件。但是，替身却是 macOS 下的最多才多艺的快捷链接。比如，创建了替身之后，替身文件和原始文件可以任意移动位置，这不会影响替身文件指向原始文件，因为替身文件中**包含了原始文件的 inode 信息**，而 inode 信息是唯一的，即使文件被移动来移动去。处理过程大概是这个样子，当用户访问替身文件时，系统分析替身文件，找到原始文件的路径信息，然后判断原始文件是否存在，如果存在就访问它，如果不存在，就找具有相同 inode 的文件，然后访问该文件。而软链里面只存储了相对地址，所以当相对关系改变后便无法找到对应的文件。

## File System

### APFS 与 HFS+ 文件系统 - Apple

APFS

可用于移动硬盘

暂不支持 Boot Camp、网络分享（必须使用 SMB 或 NFS）

HFS+

Time Machine 所使用文件系统

### Ext 文件系统 - Linux

&#160;&#160;&#160;&#160;Linux 的 Ext 文件系统与磁盘内存对应关系：在使用磁盘内存之前，需要为磁盘分区，然后为所分区域格式化出一个统一的文件系统（也有例外，如 LVM 与磁盘阵列技术）。那么，在这样一个统一的文件系统中，根据数据的不同，就可以将内存分为以下三种类型：

- inode：记录文件的属性，一个文件占用一个 inode ，同时记录此文件的数据所在的 block 号码

- block：实际记录文件的内容，如果文件太大，则会占用多个 block

- super block：记录文件系统的整体信息，包括 inode/block 的总量、使用量、剩余量，以及文件系统的格式与相关信息等

&#160;&#160;&#160;&#160;因此对于一个文件来说，它的 inode 号就类似于 id 的作用，用于存放关于该文件的一些基本信息。

### NTFS - Windows

略

### ZFS

略


## 参考资料

[详解 OSX(Unix)中的 Hard Link 与 Symbolic Link(硬连接与软连接) | 老谭笔记](http://www.tanhao.me/pieces/597.html/)

[Linux中硬连接(hard link)与软连接(symbolic link)的区别 - gxzc936733992](https://blog.csdn.net/gxzc936733992/article/details/49340429)


[为了这一个最重要的变化，macOS High Sierra 也值得升级：APFS 详解 - 少数派](https://sspai.com/post/38377)

[Mac Shortcuts: Aliases, Symbolic Links, Hard Links](https://www.lifewire.com/aliases-symbolic-links-hard-links-mac-2260189)


