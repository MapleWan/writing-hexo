---
title: 2Git基本使用
categories: 
  - 工具
  - git
tags:
  - git
date: 2024-02-02 14:15
---

# 1. 项目的创建
工作目录一般就是我们希望git帮助管理的文件夹，可以是项目的目录，也可以是空目录，尽量不要有中文。

常见的6个命令如下图
![](/images/20230607195844.png)

```shelll
git init #初始化本地目录
```

# 2. git的基本操作

## 2.1 文件状态
文件有4种状态：
- untracked：未跟踪，此文件在文件夹中，但没有加入到git库，不参与版本控制。通过`git add`状态变为 staged
- Unmodify：文件已经入库，未修改，即版本库中的文件快照内容和文件夹中完全一致，这种类型的文件有两种去处，如果他被修改，则变为modified， 如果使用`git rm`移出版本库，则成为Untracked文件
- Modified：文件已修改，仅仅是修改，并没有进行其他的操作，这个文件也有两个去除，通过`git add`可进入暂存staged状态，使用`git checkout`则丢弃修改过，犯过unmodify状态，这个`git checkout`即从库中去除文件，覆盖当前修改
- Staged：暂存状态，执行`git commit`则将修改同步到库中，这时库中的文件和本地文件又变为一致，文件为Unmodify状态，执行`git reset HEAD filename`取消暂存，文件状态为Modified

```shell
git status # 查看文件的状态
git add . # 添加文件至暂存区
git commit -m “new file hello.py” # 提交暂存区的内容至本地仓库 -m 为提交信息 
```

## 2.1 忽略文件

有时候不想把文件纳入版本控制，比如数据库文件等
在主目录下建立“.gitignore”文件，此文件有如下的规则：
1. 忽略文件中的空行或以“#“号开始的行将会被忽略
2. 可以使用Linux的通配符
3. 如果名称的最前面有一个感叹号，表示例外规则，将不被忽略
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件

```
#为注释
*.txt #忽略所有 .txt结尾的文件
!lib.txt #但lib.txt除外
/temp # 仅忽略项目根目录下的文件，不包括其他目录temp
build/ # 忽略build/目录下的所有文件
doc/*.txt #忽略doc下的所有.txt文件, 但不包括doc子目录下的txt文件
```

# 3. 码云免密码登录

id_rsa.pub文件中的内容添加到gitee设置中的SSH公钥选项

git add . ->  git commit -m "message" -> git push

# 4. git 分支

![](/images/20230607223051.png)