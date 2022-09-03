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

两天没用 ls 命令，发现居然无法使用了（zsh 下无法使用，bash 下正常）。

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

切换为 oh-my-zsh 来管理 zsh 后：

```zsh
$ alias
-='cd -'
...=../..
....=../../..
.....=../../../..
......=../../../../..
1='cd -'
2='cd -2'
3='cd -3'
4='cd -4'
5='cd -5'
6='cd -6'
7='cd -7'
8='cd -8'
9='cd -9'
_=sudo
afind='ack -il'
d='dirs -v | head -10'
g=git
ga='git add'
gaa='git add --all'
gap='git apply'
gapa='git add --patch'
gau='git add --update'
gav='git add --verbose'
gb='git branch'
gbD='git branch -D'
gba='git branch -a'
gbd='git branch -d'
gbda='git branch --no-color --merged | command grep -vE "^(\*|\s*(master|develop|dev)\s*$)" | command xargs -n 1 git branch -d'
gbl='git blame -b -w'
gbnm='git branch --no-merged'
gbr='git branch --remote'
gbs='git bisect'
gbsb='git bisect bad'
gbsg='git bisect good'
gbsr='git bisect reset'
gbss='git bisect start'
gc='git commit -v'
'gc!'='git commit -v --amend'
gca='git commit -v -a'
'gca!'='git commit -v -a --amend'
gcam='git commit -a -m'
'gcan!'='git commit -v -a --no-edit --amend'
'gcans!'='git commit -v -a -s --no-edit --amend'
gcb='git checkout -b'
gcd='git checkout develop'
gcf='git config --list'
gcl='git clone --recurse-submodules'
gclean='git clean -fd'
gcm='git checkout master'
gcmsg='git commit -m'
'gcn!'='git commit -v --no-edit --amend'
gco='git checkout'
gcount='git shortlog -sn'
gcp='git cherry-pick'
gcpa='git cherry-pick --abort'
gcpc='git cherry-pick --continue'
gcs='git commit -S'
gcsm='git commit -s -m'
gd='git diff'
gdca='git diff --cached'
gdct='git describe --tags `git rev-list --tags --max-count=1`'
gdcw='git diff --cached --word-diff'
gds='git diff --staged'
gdt='git diff-tree --no-commit-id --name-only -r'
gdw='git diff --word-diff'
gf='git fetch'
gfa='git fetch --all --prune'
gfo='git fetch origin'
gg='git gui citool'
gga='git gui citool --amend'
ggpull='git pull origin "$(git_current_branch)"'
ggpur=ggu
ggpush='git push origin "$(git_current_branch)"'
ggsup='git branch --set-upstream-to=origin/$(git_current_branch)'
ghh='git help'
gignore='git update-index --assume-unchanged'
gignored='git ls-files -v | grep "^[[:lower:]]"'
git-svn-dcommit-push='git svn dcommit && git push github master:svntrunk'
gk='\gitk --all --branches'
gke='\gitk --all $(git log -g --pretty=%h)'
gl='git pull'
glg='git log --stat'
glgg='git log --graph'
glgga='git log --graph --decorate --all'
glgm='git log --graph --max-count=10'
glgp='git log --stat -p'
glo='git log --oneline --decorate'
globurl='noglob urlglobber '
glod='git log --graph --pretty='\''%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%ad) %C(bold blue)<%an>%Creset'\'
glods='git log --graph --pretty='\''%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%ad) %C(bold blue)<%an>%Creset'\'' --date=short'
glog='git log --oneline --decorate --graph'
gloga='git log --oneline --decorate --graph --all'
glol='git log --graph --pretty='\''%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset'\'
glola='git log --graph --pretty='\''%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset'\'' --all'
glols='git log --graph --pretty='\''%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset'\'' --stat'
glp=_git_log_prettily
glum='git pull upstream master'
gm='git merge'
gma='git merge --abort'
gmom='git merge origin/master'
gmt='git mergetool --no-prompt'
gmtvim='git mergetool --no-prompt --tool=vimdiff'
gmum='git merge upstream/master'
gp='git push'
gpd='git push --dry-run'
gpf='git push --force-with-lease'
'gpf!'='git push --force'
gpoat='git push origin --all && git push origin --tags'
gpristine='git reset --hard && git clean -dfx'
gpsup='git push --set-upstream origin $(git_current_branch)'
gpu='git push upstream'
gpv='git push -v'
gr='git remote'
gra='git remote add'
grb='git rebase'
grba='git rebase --abort'
grbc='git rebase --continue'
grbd='git rebase develop'
grbi='git rebase -i'
grbm='git rebase master'
grbs='git rebase --skip'
grep='grep  --color=auto --exclude-dir={.bzr,CVS,.git,.hg,.svn}'
grh='git reset'
grhh='git reset --hard'
grm='git rm'
grmc='git rm --cached'
grmv='git remote rename'
grrm='git remote remove'
grset='git remote set-url'
grt='cd $(git rev-parse --show-toplevel || echo ".")'
gru='git reset --'
grup='git remote update'
grv='git remote -v'
gsb='git status -sb'
gsd='git svn dcommit'
gsh='git show'
gsi='git submodule init'
gsps='git show --pretty=short --show-signature'
gsr='git svn rebase'
gss='git status -s'
gst='git status'
gsta='git stash save'
gstaa='git stash apply'
gstall='git stash --all'
gstc='git stash clear'
gstd='git stash drop'
gstl='git stash list'
gstp='git stash pop'
gsts='git stash show --text'
gsu='git submodule update'
gts='git tag -s'
gtv='git tag | sort -V'
gunignore='git update-index --no-assume-unchanged'
gunwip='git log -n 1 | grep -q -c "\-\-wip\-\-" && git reset HEAD~1'
gup='git pull --rebase'
gupa='git pull --rebase --autostash'
gupav='git pull --rebase --autostash -v'
gupv='git pull --rebase -v'
gwch='git whatchanged -p --abbrev-commit --pretty=medium'
gwip='git add -A; git rm $(git ls-files --deleted) 2> /dev/null; git commit --no-verify -m "--wip-- [skip ci]"'
history=omz_history
l='ls -lah'
la='ls -lAh'
ll='ls -lh'
ls='ls -G'
lsa='ls -lah'
md='mkdir -p'
rd=rmdir
run-help=man
which-command=whence
```







