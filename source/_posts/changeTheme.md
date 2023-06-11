---
title: changeTheme
date: 2023-03-11 16:37:18
tags: hexo更换主题
categories: Hexo
excerpt: 更换Hexo默认主题
---
#### Hexo更换默认主题
+ 选择主题
> 可以在[hexo官网](https://hexo.io/zh-cn/)中挑选自己喜欢的主题模板，然后点击去到GitHub页面，将喜欢的主题项目fork到自己的仓库中

+ 下载主题
> 这里要注意的是，下载的主题最好是使用自己仓库中fork的项目地址，并且最好使用git的子模块方式clone
> 因为直接使用主题作者的仓库地址，会导致推送自己的博客时，如果更改了主题文件的话会同时推送给主题作者
> 这时候会导致推送失败，因为没有权限直接推送给主题作者，会提示你使用PR方式发起推送
> 最后要注意的是下载的主题项目要放在你的hexo项目的themes文件夹下
 ```shell
#step1:先下载主题项目项目
git clone https://github.com/theme
#step2: 进入hexo项目的theme文件夹下
cd hexo/theme/
#添加子模块，执行完命令后会发现，项目下多个文件：.gitmodules
git submodule add https://github.com/projectAddress 
```
+ 更换主题
在_config.yaml文件中更改你的主题名称
```yaml
#把默认的主题名称改为你下载的主题名称
theme: themeName 
```

+ 然后重新生成静态页面再启动就可以看到新的主题已经生效了
```shell
#生成静态页面
hexo g
#启动hexo
hexo s
```
#### hexo使用分类的功能
+ 文章想实现分类的功能，首先需要在主题中启用菜单的分类
```yaml
menus:
  -
    name: Home
    link: /
  -
    name: Category
    link: categories/
  -
    name: Open-Source
    link: open-source/
  -
    name: Message
    link: message/ 
```
+ 然后生成菜单页面
```shell
#new page会在source文件夹下直接新创建一个文件夹对应你设置的名称，文件夹下有一个index.md文件
hexo new page categories
```
+ 在上面生成的index.md文件中配置参数，重启项目，分类功能就实现了
> title和date都是默认生成，你需要加入的是type和layout
> type对应的是你上面menu配置的菜单名称，并且要开启layout布局，内容是分类，否则页面不会显示已有的分类内容
```yaml
---
title: categories
date: 2023-03-09 21:15:02
type: "categories"
layout: categories
---
```