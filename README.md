# 版本管理工具日志提交规范

## 1.概述

版本工具提交规范是用来规范svn或git等版本管理工具提交信息,目的使commit简洁便于查找,方便日后追溯。
commit大致分为Summary(概述)和Description（描述）和Note（备注）三方面，正文从以上这三方面进行阐述。

## 2.正文

### 2.1 正文概述

commit提交格式如下所示,先写**Summary**再紧接着**<空一行>**再写下**Description**,再紧接着**<空一行>**写下 **Note**。其中Summary是必选的，Description和 Note是可选的。

``` commit
Summary

Description

Note
```
### 2.2 commit之Summary

Summary在版本工具提交commit的时候，起到简明扼要的特点。这里主要叙述了commit比起上个版本功能上的变化，比如修改的一个文件，新增加几行代码，是为了满足了什么功能需求，故无需从修改或增加文件本身等一些细节性的东西出发写 Summary，Summary侧重满足功能需求上,格式如下所示。scope是说明用来说明此次修改的影响范围,subject是具体的描述，Summary尽量控制在50个字符以内。

```Summary
[scope]<空一格>subject
```
**scope描述**

scope主要分以下2种
- all ：    表示影响面大 ，如修改了整体框架 会对整个程序产生影响
- module：  表示会影响某个模块，比如音频，车身检测模块

**使用场景描述**

- 如果影响一个模块的化可以更改为:

```Summary
[CarSingalManage] 修改ACC检测时间，同步ACC问题
```
- 如果影响多个模块的化可以更改为:

```Summary
[CarSingalManage][MX51] 增加了文档描述代码示例，修改了之前提出的bug
```
- 如果影响太多模块,要在 Description 具体阐述:

```Summary
[all] 修改了时间片轮询框架改用操作系统
```
### 2.3 commit之Description

在写完了Summary概述后，空一格再写具体Description，每行Description控制在75个字符以内，格式如下所示:

```Description
[type]<空一格>Description1
[type]<空一格>Description2
[type]<空一格>Description3
```
**type描述**
其中 type 是描述类型，可分为下面三种

- add (新增加文档或代码)
- fix (修复 bug )
- update (更新已有文档或代码)
- revert (撤回之前修改)

**使用场景描述**

- 比如 新增加了一个文档 描述使用:

```Description
[add] 增加文档描述代码使用和集成
```
- 比如 修复了一个bug（如果有RTC对策ID，则输入在此）:

```Description
[fix] 修复了一个bug，对策RTC问题点，RTCID：54321
```
- 比如 更新了代码:

```Description
[update] 更新了版本说明
```
- 比如 增加的功能需要撤销的:

```Description
[revert] 取消XX策略，恢复之前策略
```
- 如果较多的更改，可以一起换行继续写:

```Description
[add] 增加文档描述代码使用和集成
[fix] 修复了一个bug，对策RTC问题点
[update] 更新了版本说明
[revert] 取消XX策略，回复之前策略
```
### 2.4 commit之note

note 是此次提及的备注事项，这个可有可无，可以做一些修改参考，和版本验证等说明。

### 2.5 commit示范

以上是针对commit三部分说明，写在一起的话，就如下所示:

- 完整的commit示范(Summary+Description+Note):

``` commit
[CarSingalManage][MX51] 增加了文档描述代码示例，修改了之前提出的bug

[add] 增加文档描述代码使用和集成
[fix] 修复了一个bug，对策RTC问题点，RTCID：54321
[update] 更新了版本说明

此时更新部分修改参考之前XX工程，同步修改之前问题点
```
- commit示范(Summary+Description):

``` commit
[MX51] 新增加空调透传类型

[add] 透传协议新增类型
[fix] 修复了一个bug，对策RTC问题点，RTCID：12345
```
- commit示范(Summary):

``` commit
[EEPROM] 修改正式提交版本号，版本号为： V1.2.3
```
这样就可以很清楚知道此次修改影响了哪些 模块，以及修改点，增加点，和更新点。

### 2.6 commit补充说明
这部分补充说明主要针对commit细节的补充

- 每次commit尽量让新添加的文件代码部分编译通过，和验证通过。如果未编译或者未验证文件必须在**Note**强制写入未编译或未验证原因,如果在后来某一版已经验证或编译，需要在后来某一版commit注明并写出之前版本提交commit ID，方便问题追溯跟踪。

示范：

之前某一版commit 未验证:

``` commit
[CarSingalManage] ACC信号检测时间修改

[update] 增加延迟ACC—ON检测时间

[已编译][未验证] 还未经过实车验证
```
后来某一版如果已通过验证，需要说明:

``` commit
[Mx51] MX51添加新协议

[add] 添加新的透传协议

已经实车验证ACC信号检测，commit ID:XXXX
```
## 3.参考

[Git 提交的正确姿势：Commit message 编写指南](http://www.oschina.net/news/69705/git-commit-message-and-changelog-guide)

[如何写好 Git commit log?](https://www.zhihu.com/question/21209619/answer/257574960)

[git commit 时使用 Emoji](https://zhuanlan.zhihu.com/p/29764863)

[老鸟都应该注意的git 提交规范](http://www.cnblogs.com/ctaodream/p/6066694.html)

[廖雪峰Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
[Git commit message和工作流规范](http://www.cnblogs.com/cpselvis/p/6501485.html)
