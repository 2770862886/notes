% Git techs

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Git Reference](https://git-scm.com/doc/ext)  
[Git Immersion](http://gitimmersion.com/)  
[Git Magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/zh_cn/)  
[Git Cheat Sheet](https://github.com/flyhigher139/Git-Cheat-Sheet)  

# git stage #

![stage](images/git_stage.jpg)

# git elements #

## git rebase -i ##

``` shell
git rebase -i HEAD^^
```

## git alias ##

``` shell
git config --global alias.l "log --color --graph --decorate --pretty=oneline --abbrev-commit"
git config --global alias.l0 "log --color --graph --decorate --pretty=oneline --abbrev-commit -U0"
git config --global alias.la "log --color --graph --decorate --pretty=oneline --abbrev-commit --all"
git config --global alias.lb "log --color --graph --decorate --pretty=oneline --abbrev-commit --all --simplify-by-decoration"
git config --global alias.lg "log --color --graph --decorate"
git config --global alias.dl "log --date-order --color --graph --decorate --pretty=oneline --abbrev-commit"
git config --global alias.dla "log --date-order --color --graph --decorate --pretty=oneline --abbrev-commit --all"
git config --global alias.dlb "log --date-order --color --graph --decorate --pretty=oneline --abbrev-commit --all --simplify-by-decoration"
git config --global alias.dlg "log --date-order --color --graph --decorate"
git config --global alias.d "diff --color"
git config --global alias.dc "diff --color --cached"
git config --global alias.d0 "diff --color --unified=0"
git config --global alias.ci "commit --verbose"
git config --global alias.ct commit
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.df diff
git config --global alias.br branch
```

## repo commands ##

``` shell
repo forall -c "git reset --hard && git clean -xfd"
```

## Fix simple ssh does not support port ##

``` shell
git config --global ssh.variant ssh
```


Git Magic
=========

1.基本技巧
-------

### 保存状态 ###

``` bash
git init
git add .
git commit -m "My first backup"
```

``` bash
git reset --hard
```

``` bash
git commit -a -m "Another backup"
```

### 添加，删除，重命名 ###


``` bash
git add readme.txt Documentation
```

``` bash
git rm kludge.h obsolete.c
git rm -r incriminating/evidence/
```

``` bash
git mv bug.c feature.c
```

### 进阶撤销/重做 ###

``` bash
git reset --hard 766f
```

``` bash
git checkout 82f5
```

使用commit标题进行重做

``` bash
git checkout :/"Use pandoc for"
```

``` bash
git checkout master~5
```

### 撤销 ###

``` bash
git revert 1b6d
```

### 生成变更日志 ###

``` bash
git log > ChangeLog
```

### 下载文件 ###

### 快速发布 ###

### 我们已经做了什么？ ###

``` bash
git diff
```

``` bash
git diff "@{yesterday}"
```

``` bash
git diff 1b6d "master~2"
git diff 1b6d "master^^"
```

``` bash
git whatchanged --since="2 weeks ago"
```

2.克隆代码库
----------

3.分支巫术
----------

4.关于历史
----------

5.多人Git
---------

6.Git大师技
-----------

