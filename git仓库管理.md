# 1、目标

git基本概念

git工作流程

git常用命令

git代码托管服务

idea操作git

# 2、概述

## 版本器控制方式：

- 集中版本控制工具：svn和cvs（会影响对git的理解）
- 分布式版本控制工具：git

# 3、常用命令

## 获取本地仓库 `git init`

![image-20230401135706144](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230401135706144.png)

## 基础操作指令

### 查看修改的状态

 `git status`

### 将文件添加到暂存区

`git add `    命令形式：git add 单个文件名|通配符

### 提交暂存区到本地仓库

`git commit ` 形式 git commit -m '注释版本名' 

### 查看提交日志

`git log`    别名git-log

### 版本回退

git reset --hard commitID 

ID可以从git-log和git reflog（查找删除的提交记录）中得

### 添加文件到忽略列表

创建一个.gitignore文件，在里面列出要忽略的模式    

 ## 分支

### 查看本地分支

git branch (git-log)

### 创建分支

git branch 分支名

### *切换分支

切换到指定分支 git checkout 分支名

切换并创建到一个不存在的分支 git checkout -b 分支名 

### *合并分支

将一个分支上的提交合并到另一个分支

git merge 分支名

### 删除分支

git branch -d 分支名  删除分支时，需要检查

git branch -D b1 不做检查，强制删除

### 解决冲突

当两个分支上对文件的修改可能会存在冲突，例如同时修改了同一个文件的同一行，这时就需要手动解决冲突，解决冲突步骤如下：

1. 处理文件中冲突的地方

2. 将解决完冲突的文件加入暂存区(add)

3. 提交到仓库(commit)

### 开发中分支使用原则与流程

![image-20230402183914993](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230402183914993.png)

# git