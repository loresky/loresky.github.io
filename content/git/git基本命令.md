---
title: git基本命令
date: 2017-06-13 10:00:00
---

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