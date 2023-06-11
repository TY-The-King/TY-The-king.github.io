---
title: git and git commit order
date: 2023-03-08 22:01:44
tags: git命令
categories:
- 日常记录
excerpt: git常用的基础命令已经git commit规范
comments: false
---
#### git order
```shell
#https方式clone
git clone https://github.com/YourGitHubName/RepositoriesName.git

#SSH方式clone，只有仓库拥有者以及管理员才能使用，并且需要在本地生成ssh key
git clone git@github.com:YourGitHubName/RepositoriesName.git

#指定分支克隆项目,branchName为你要克隆的分支名称
git clone git@github.com:YourGitHubName/RepositoriesName.git -b branchName

#查看仓库内文件的状态
git status

#添加文件到缓存区
git add -A

#删除文件
git rm filepath

#提交文件
git commit -m 'commit comments'

#推送文件
git push -u origin master

#查看所有分支
git branch -a

#新建分支
git branch newBranchName

#切换分支
git checkout branchName

#查看全部远程链接仓库地址
git remote -v

#添加远程仓库链接
#https,YourGitHubName=GitHub账户名，RepositoriesName=仓库名
git remote add origin https://github.com/YourGitHubName/RepositoriesName.git
#SSH方式
git remote add origin git@github.com:YourGitHubName/RepositoriesName.git

#查看全部变量(system,global,local)
git config --list

#查看系统变量
git config --system --list

#查看全局变量
git config --global --list

#查看本地变量
git config --local --list

#保存本地代码修改，暂不提交改动部分（适用于新增功能未做完，又需update修改旧功能）
git stash

#想要加上注释的写法：
git stash save 'stash comments'

#回滚单个文件
git checkout fileName
```

#### git commit rules
> *type类型*
> + fix/to：修复BUG，fix产生diff并一次修复，to产生diff，但是不自动修复，适用多次提交，最后一次是fix
> + feat：增加新功能
> + refactor：重构（既不是新增功能，也不是修复BUG的代码改动）
> + style：格式（不影响代码运行的变动）
> + perf：优化相关，比如性能，体验
> + docs：文档
> + test：增加测试
> + chore：构建过程或辅助工具的改变
> + revert：回退上一个版本
> + merge：合并代码
> + sync：同步主线或分支的BUG
> 
