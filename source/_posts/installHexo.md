---
title: installHexo
date: 2023-03-10 22:44:48
tags: 安装Hexo搭建博客，并设置Github Page
categories: Hexo
comment: false
excerpt: 本文基于Mac OS环境下使用Hexo搭建个人博客，并部署到github Page
---
#### 环境：
> 本文基于Mac OS环境下搭建Hexo，部署到github

#### 正文：
在安装Hexo之前，需要安装相应的环境：_npm_和_Git，可安装本文提示安装，也可去到官网查看_
> [Hexo官网链接：https://hexo.io](https://hexo.io)

- 安装npm
> 可以通过Homebrew安装，也可使用node.js官网提供的.pkg安装包：[node.js.pkg下载地址](https://nodejs.org/en/download/)

- 安装git
> 同样是通过Homebrew安装

以上两个安装完成后，即可开始Hexo的安装
```shell
#注意：使用命令安装hexo之前，需要先切换成root用户，否则会提示EACCESS错误，即没有权限
#切换root用户,输入密码，出现sh-3.2,即代表拥有了root权限
sudo su

#执行安装命令
npm install -g hexo-cli
```

- init（初始化hexo）

等安装完成后，即可使用命令在指定文件夹下初始化一个hexo博客文件
```shell
#init之后是指定要在那个文件夹下初始化hexo
hexo init ~/Documents/hexo

#进入这个文件夹，下载npm
cd ~/Documents/hexo

npm install
```

---

- start server（启动服务）

这个时候一个hexo博客已经生成完毕，可以启动本地服务查看
```shell
#生成静态文件，这个命名可缩写为：hexo g
hexo generate
#启动本地服务，访问:http://localhost:4000/
hexo server
```

- deploy（部署GitHub page）

到这一步可以成功访问，那么离搭建我们自己的博客就只差最后一步，将博客部署到GitHub上了。
首先需要在GitHub上新建一个仓库用来放置我们的博客文件
> 这里需要注意的是：仓库名字需要设置为你自己的用户名+.github.io，如：
> TY-The-King.github.io

新建仓库完成后，可以安装hexo插件，进行一键部署
```shell
#安装hexo插件
npm install hexo-deployer-git --save
```
接着再去到生成的hexo文件夹下，修改_config.yml文件下的deploy内容：
```yaml
deploy:
  type: 'git'
  repo: git@github.com:TY-The-King/TY-The-king.github.io.git
  branch: master
```
修改完成后，我们即可使用命令一键部署博客到GitHub page上
> 在此之前，需要在本地生成github的SSH密钥，如果不生成密钥的话，在部署的时候会要求账户密码，由于github认证的升级，现在无法使用输入密码的方式，需要使用token方式认证，在github中生成一个token当做密码。这种方式十分麻烦，每次deploy部署时都需要输入一次，推荐在本地生成SSH密钥。
> 网上有很多这类教程，这边不再赘述，教程：[github生成SSH密钥](https://blog.csdn.net/wenfu814/article/details/120625844)

```shell
#命令可简化为:hexo d
hexo deploy
```
部署完成后，即可访问自己的github page

---

![installHexo1.png](/images/installHexo1.png)

- 创建源码分支(create source branch)

> 在成功部署Github Pages的时候，我们会发现，使用"hexo deploy"部署到仓库的只有public文件夹下的静态文件，源码的.md文件并没有保存至仓库中。
> 那么当我们本地的代码丢失的话，就无法通过仓库找回md源文件了，这个时候我们需要创建一个新的分支来专门保存md源文件。

首先，我们来到hexo项目下，使用git命令创建一个新的分支
```shell
#查看当前分支
git branch -a

#创建source分支
git branch source
```

然后将源码文件进行添加和提交操作，如果不想将生成的public下的静态文件一起保存在source分支的话，可以创建一个.gitignore文件决定那些文件纳入管理。
最后将代码提交至source分支，就完成源码的保存。

```shell
#创建.gitignore文件,自行配置不纳入git管理的文件
touch .gitignore

#添加文件
git add .

#提交文件
git commit -m 'source first commit'

#将提交的代码保存到source分支
git push -u origin source

#将分支切换至source
git checkout source
```

> ***需要注意的是，_config.yml中配置的deploy配置的branch记得设置为master分支，***
> ***这样直接使用"hexo d"就能直接将静态文件部署在master分支而不影响源码source分支的保存***