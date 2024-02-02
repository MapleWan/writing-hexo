---
title: 1Git配置与基本理论
categories: 
  - 工具
  - git
tags:
  - git
date: 2024-02-02 14:13
---

[参考资料](https://www.liaoxuefeng.com/wiki/896043488029600)
# 1. 安装
windows下载安装包（[链接](https://github.com/git-for-windows/git/releases/download/v2.40.1.windows.1/Git-2.40.1-64-bit.exe)）    ‘‘下一步.....’’

Ubuntu中 `apt update & apt install git`

# 2. 必要配置

```shell
# 设置用户名和email地址，必须设置的   global表示全局配置
git config --global user.name "MapleWan"
git config --global user.email "1041709112@qq.com"

git config -l # 所有的配置
git config --system --list  # 系统的配置
git config --global --list
```
所有的这些配置都是保存在本地的

```
	C:\Program Files\Git\etc\gitconfig  # 系统配置
	C:\Users\maple\.gitconfig    # 用户全局配置
```


# 3. 基本理论
git本地有三个工作区域：工作目录（working directory）、暂存区（stage）、资源库（repository）。加上远程的git仓库（remote directory）

- 工作区（workspace）：平时存放项目代码的地方
- 暂存区（index、stage）：用于临时存放改动，事实上就是一个文件，保存即将提交到文件列表信息
- 仓库区（repository）：安全存放数据的位置，这里有提交到所有版本的数据。其中HEAD指向最新放入的仓库版本
- 远程库（remote）：托管代码的服务器，可以简单地认为是项目组中的一台电脑用于远程数据交换

![](/images/20230607005128.png)
本地的三个区域确切地说应该是git仓库中HEAD指向的版本
![](/images/20230607005825.png)
- Directory：使用git管理的目录，也就是一个仓库，包含我们的工作空间和git的管理空间
- WorkSpace：需要通过git进行版本控制的目录和文件。这些目录和文件组成了工作空间
- .git：存放git管理信息的目录，初始化仓库的时候自动创建
- index/Stage：暂存区，或者叫 待提交更新区，在提交进入repo之前，我们可以把所有的更新放在暂存区
- Local Repo：本地仓库，一个存放在本地的版本库；HEAD会指向当前的开发分支
- Stash：隐藏，是一个工作状态保存栈，用于保存/恢复WorkSpace中的临时状态

## 3.1 基本流程
git的工作流程一般是：
1. 在工作目录添加、修改文件
2. 将需要进行版本管理的文件放入暂存区域  `git add .`
3. 将暂存区域的文件提交到git仓库 `git commit`

因此，git管理的文件有三种状态：已修改（modified），已暂存（staged），已提交（committed）

![](/images/20230607010427.png)