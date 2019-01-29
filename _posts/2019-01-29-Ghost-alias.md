---
layout: post
title: "Ghost alias"
categories: macOS Software
tags: software
excerpt: 幽灵般的 alias （zsh）
author: suliveevil
mathjax: true
---

* content
{:toc}

几天没用 ls 命令，发现居然无法使用了（zsh 下无法使用，bash 下正常）。

原来 ls 被设置为了


```zsh
$ which ls
ls: aliased to ls -a --group-directories-first --color=auto
```

WTF ！！！
检查一遍 alias，我尼玛这里面绝大部分都不是我设置的！！！
到现在还没查清到底是谁在哪儿给我添加的 alias。真是醉了。`.zshrc` 里没有 跟ls 有关的 alias，`/etc/profile` 里也没有，真是日了狗！！！
以后无论是什么软件的配置最好还是自己一点一点配置算了，你不知道你的电脑到底被改了些什么。

```zsh
$ alias
_=sudo                         # NOT ME
_complete=_bash_comp           # NOT ME
_expand=_bash_expand           # NOT ME
ack='nocorrect ack'            # NOT ME
b='${(z)BROWSER}'              # NOT ME
bci='brew cask install'
bcu='brew cask upgrade'
bower='noglob bower'           # NOT ME
bs='brew search'
cat=ccat
cd='nocorrect cd'              # NOT ME
cp=cpi                         # NOT ME
cpi='nocorrect cp -i'          # NOT ME
d='dirs -v | head -10'         # NOT ME
df='df -kh'                    # NOT ME
diffu='diff --unified'         # NOT ME
du='du -kh'                    # NOT ME
e='${(z)VISUAL:-${(z)EDITOR}}' # NOT ME
ebuild='nocorrect ebuild'      # NOT ME
fc='noglob fc'                 # NOT ME
find='noglob find'             # NOT ME
fsh-alias=fast-theme           # NOT ME
ftp='noglob ftp'               # NOT ME
gcc='nocorrect gcc'            # NOT ME
get='curl --continue-at - --location --progress-bar --remote-name --remote-time'                           # NOT ME
gist='nocorrect gist'          # NOT ME
globurl='noglob urlglobber '   # NOT ME
grep='nocorrect grep --color=auto'                      # NOT ME
h=history
heroku='nocorrect heroku'      # NOT ME
hh=hstr
history='noglob history'       # NOT ME
history-stat='history 0 | awk ''{print $2}'' | sort | uniq -c | sort -n -r | head'                           # NOT ME
http-serve='python3 -m http.server'                     # NOT ME
jkl=jekyll
l='ls -1A'                     # NOT ME
la='ll -A'                     # NOT ME
lc='lt -c'                     # NOT ME
lg=lazygit                     # NOT ME
lk='ll -Sr'                    # NOT ME
ll='ls -lh'                    # NOT ME
lm='la | "$PAGER"'             # NOT ME
ln=lni                         # NOT ME
lni='nocorrect ln -i'          # NOT ME
locate='noglob locate'         # NOT ME
lr='ll -R'                     # NOT ME
ls='ls -a --group-directories-first --color=auto'        # NOT ME
lt='ll -tr'                    # NOT ME
lu='lt -u'                     # NOT ME
lx='ll -XB'                    # NOT ME
man='nocorrect man'            # NOT ME
mkdir='nocorrect mkdir -p'     # NOT ME
mp='mackup backup'
mv=mvi                         # NOT ME
mvi='nocorrect mv -i'          # NOT ME
mysql='nocorrect mysql'        # NOT ME
o=open                         # NOT ME
p='${(z)PAGER}'                # NOT ME
pbc=pbcopy
pbp=pbpaste
po=popd                        # NOT ME
pu=pushd                       # NOT ME
rake='noglob rake'             # NOT ME
rm=rmi                         # NOT ME
rmi='nocorrect rm -i'          # NOT ME
rsync='noglob rsync'           # NOT ME
run-help=man                   # NOT ME
sa='alias | grep -i'           # NOT ME
scp='noglob scp'               # NOT ME
sftp='noglob sftp'             # NOT ME
shopt=:                        # NOT ME
sl=ls                          # NOT ME
topc='top -o cpu'              # NOT ME
topm='top -o vsize'            # NOT ME
type='type -a'                 # NOT ME
which-command=whence           # NOT ME
yd=ydict
z='_z 2>&1'                    # NOT ME

```









