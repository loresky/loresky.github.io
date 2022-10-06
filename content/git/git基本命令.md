---
title: git基本命令
date: 2017-06-13 10:00:00
---

* master 分支: 线上稳定版本分支
* develop 分支: 开发分支，衍生出 feature 分支和 release 分支
* release 分支: 发布分支，准备待发布版本的分支，存在多个，版本发布之后删除
* feature 分支: 功能分支，完成特定功能开发的分支，存在多个，功能合并之后删除
* hotfix 分支: 紧急热修复分支，存在多个，紧急版本发布之后删除

* Workspace：工作区
* Index / Stage：暂存区
    这个区域就是我们每次执行 git add 之后会存到的区域，用来与本地仓库之间做一个缓存，同时也是 Git 底层设计上来说也算是比较重要的一个区域，它能帮助 Git 在做 diff 的时候提高查找性能
* Repository：仓库区（或本地仓库）
    这里就是我们经常会打交道的区域，你在执行 commit 之后，本质上就是提交到了这个区域，你可以查看你的 .git 目录下的 refs/heads 目录，里面存的就是我们本地的分支代码信息
* Remote：远程仓库
* 远端分支本地副本
    这个其实主要储存了远程仓库各分支数据在本地的一个副本，你可以打开你 Git 项目下的 .git 文件，里面有个 refs/remotes，这里就主要存的就是远程仓库的分支信息，一般你执行 push 或者 pull、fetch 都会往这里进行更新


### 配置 Git
``` bash
# 配置全局用户
git config --global user.name "name" 
git config --global user.email "youremail@github.com"
# 删除全局配置
$ git config --global --unset alias.xxx
$ git config --global --unset user.xxx
```

###  提交信息规范
*git commit 格式 如下：*
```
<type>(<scope>): <subject>
```

* type 类型，提交的类别
    * feat: 新功能
    * fix: 修复 bug
    * perf: 更改代码，以提高性能（在不影响代码内部行为的前提下，对程序性能进行优化）
    * refactor: 代码重构（重构，在不影响代码内部行为、功能下的代码修改）
    * docs: 文档变动
    * style: 格式调整，对代码实际运行没有改动，例如添加空行、格式化等
    * test: 添加或修正测试代码
    * build: 影响项目构建或依赖项修改
    * revert: 恢复上一次提交
    * ci: 持续集成相关文件修改
    * chore: 构建过程或辅助工具和库（如文档生成）的更改
    * ci: 持续集成相关文件修改
    * workflow: 工作流相关文件修改
* scope 修改范围
主要是这次修改涉及到的部分，简单概括，例如 login、train-order
* subject 修改的描述
具体的修改描述信息
* 范例
``` bash
feat(detail): 详情页修改样式
fix(login): 登录页面错误处理
test(list): 列表页添加测试代码
```

### git checkout
```
# 分支切换
git checkout dev # local branch

# 切换远程分支
git checkout origin/test # remote branch

# 基于远程分支创建本地分支，并跟踪对应来自 'origin' 的远程分支
git checkout --track origin/feature-test # new local branch wih remote branch

# 基于本地分支开出新分支
git checkout -b testbranch

# 彻底丢弃某个文件的改动
git checkout -- file

# 放弃本地所有改动
git checkout .

# 切换上一个分支
git checkout -
```



## 创建git仓库
``` bash
mkdir Test
cd Test
git init
echo "# Test" >> README.md
git add README.md
git commit -m "first commit"
git remote add origin https://git.coding.net/hccy/Test.git
git push -u origin master
```

## 已有项目 
``` bash
如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加
git remote add origin https://git.coding.net/hccy/Test.git
主分支git push -u origin master
分支git push -u origin branch
```

## git clone 某个分支或所有分支
### clone 某个分支：
``` bash
git clone -b b1 https://github.com/...
```
### clone 所有分支：
``` bash
git clone https://github.com/...
git branch -r
* source
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
  remotes/origin/source
```

## git checkout——检出
### 创建新分支：
``` bash
git branch branchName
```
### 切换到新分支：
``` bash
git checkout branchName
```
### 上面两个命令也可以合成为一个命令：
``` bash
git checkout -b branchName
```

## **git status告诉你有文件被修改过，用git diff可以查看修改内容**


## 回退到某个版本
1. git reset –hard：彻底回退到某个版本
2. git reset –soft：回退到某个版本，只回退了commit的信息，不会恢复到index file一级。
3. git reset –mixed：此为默认方式，不带任何参数的git reset，即时这种方式，它回退到某个版本，只保留源码，回退commit和index信息。 


## 查看分支合并图
git log --graph --pretty=oneline --abbrev-commit