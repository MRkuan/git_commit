# git commit 规范文档

## 1.概述

git-commit 规范下gerrit(git) 上面提交信息，顺便整理git信息整理，作为参考，欢迎fork本文档后pull request,来完善本文文档，以下演示提交都已**git bash**为基础

## 2.正文

### 2.1 gerrit使用
gerrit使用参考平台 **Gerrit普通开发指导文档.doc**，不再叙述，这边主要讲述下提交

### 2.2 gerrit git 提交模板

#### 2.2.1 进入提交

如果之前提交 都是 先 **git add -A** 后 再 **git commit -m "balabala"**,这样的提交方法 commit 的话只能提交一行信息，导致不能过多的描述信息，所以要改变**commit**命令，**git add -A** 后 再 **git commit**，进入vi模式提交信息



## 3.参考

[Git 提交的正确姿势：Commit message 编写指南](http://www.oschina.net/news/69705/git-commit-message-and-changelog-guide)

[如何写好 Git commit log?](https://www.zhihu.com/question/21209619/answer/257574960)