---
title: Git
date: 2024-09-03
tags:
  - gitOrder GitCommit
category: 日常记录
excerpt: git常用的基础命令、git commit规范
comment: false
---

### git order
> 1. https方式clone
> ```shell
> git clone https://github.com/YourGitHubName/RepositoriesName.git
> ````

> 2. SSH方式clone，只有仓库拥有者以及管理员才能使用，并且需要在本地生成ssh key
>```shell
>git clone git@github.com:YourGitHubName/RepositoriesName.git
>```

> 3. 指定分支克隆项目,branchName为你要克隆的分支名称
> ```shell
> git clone git@github.com:YourGitHubName/RepositoriesName.git -b branchName
> ```

> 4. 查看仓库内文件的状态
> ```shell
> git status
> ```

> 5. 添加文件到缓存区
> ```shell
> git add -A
> ```

> 6. 删除文件
> ```shell
> git rm filepath
> ```

> 7. 提交文件
> ```shell
> git commit -m 'commit comments'
> ```

> 8. 推送文件
> ```shell
> git push -u origin master
> ```

> 9. 查看所有分支
> ```shell
> git branch -a
> ```

> 10. 新建分支
> ```shell
> git branch newBranchName
> ```

> 11. 切换分支
> ```shell
> git checkout branchName
> ```

> 12. 查看全部远程链接仓库地址
> ```shell
> git remote -v
> ```

> 13. 添加远程仓库链接
>
> HTTPS方式-YourGitHubName=GitHub账户名，RepositoriesName=仓库名
> ```shell
> git remote add origin https://github.com/YourGitHubName/RepositoriesName.git
> ```
> SSH方式
> ```shell
> git remote add origin git@github.com:YourGitHubName/RepositoriesName.git
> ```

> 14. 查看全部变量(system,global,local)
> ```shell
> git config --list
> ```

> 15. 查看系统变量
> ```shell
> git config --system --list
> ```

> 16. 查看全局变量
> ```shell
> git config --global --list
> ```

> 17. 查看本地变量
> ```shell
> git config --local --list
> ```

> 18. 保存本地代码修改，暂不提交改动部分（适用于新增功能未做完，又需update修改旧功能）
> ```shell
> git stash
> ```

> 19. 想要加上注释的写法：
> ```shell
> git stash save 'stash comments'
> ```

> 20. 回滚单个文件
> ```shell
> git checkout fileName
> ```

---

### git commit rules
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


