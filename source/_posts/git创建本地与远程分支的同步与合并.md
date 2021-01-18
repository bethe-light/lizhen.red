---
title: git创建本地与远程分支的同步与合并
aplayer: true
date: 2018-05-17
updated:
tags: git
categories:
keywords: git
description:
top_img: /img/git/git.png
comments:
cover: /img/git/git.png
toc:
toc_number:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
highlight_shrink:
aside:
---

## git创建本地与远程分支的同步与合并

![git](/img/git/git.png)

- 首先  git branch查看本地分支信息 ， git branch -a 查看所有分支（包括远程 remote）此时还没有其他分支信息，接下来创建本地，远程分支后再来对比就一目了然。

```git
$ git branch
* master
```

```git
$ git branch -a
*master
remotes/origin/ -> origin/master
remotes/origin/master
```

​	*星号表示当前所在分支 remote 表示远程分支

- 当然也可以通过 git status 查看当前分支

```git
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```

- 先建立本地分支

  $ git checkout -b branch_dev 创建本地分支并切换到新建分支，等同于下面两行

  分开操作：

  1. 创建本地分支 git branch branch_dev
  2. 切换到新创建的分支git checkout branch_dev 

  使用git branch 看到已经切换到新建本地分支

  ```git
  $ git branch
    master
  * branch_dev
  ```

- 将新建的本地分支关联到远程分支（push 即可，push之后才可以pull）

  ```git
  $ git push origin branch_dev:branch_dev
  ```

  branch_dev：branch_dev 是不是有点迷？

  第一个其实是本地分支的名，冒号后面是要创建的远程分支名，自己另起名称随便

  而且如果直接使用 $ git push origin branch_dev  则默认和远程分支同名

  好了，已经新建好本地与远程同步的分支，运行命令查看远程分支已经存在，大功告成！

  ```git
  $ git branch -a
   master
  *branch_dev
   remotes/origin/HEAD -> origin/master
   remotes/origin/master
   remotes/origin/branch_dev
  ```

  那如何删除分支呢？

- 删除新建的本地分支

  ```git
  $ git branch -d branch_dev
  ```

- 删除新建的远程分支

  ```git
  $ git branch -r -d origin/branch_dev 
  or
  $ git push origin :branch_dev
  ```

  第二种push为空，相当于删除该分支（但其实应该存在只是无内容？自己动手试一下）

- 合并分支

  checkout 切换到master，然后将所需的分支并入，**注意**：切换过程中，暂缓区或工作目录存在未提交的修改，可能会造成冲突的的发生，所以尽量保持工作区的清洁

  ```git
  $ git checkout master
  $ git merge branch_dev
  ```

- [墙裂推荐该文档学习git 命令 很详细透彻](https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E6%96%B0%E5%BB%BA%E4%B8%8E%E5%90%88%E5%B9%B6)
