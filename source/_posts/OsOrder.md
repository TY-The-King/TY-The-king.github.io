---
title: OS Order
date: 2024-09-03
tags:
  - Linux Windows Mac
category: Order
excerpt: 常用的操作系统基础命令
comment: false
---

## Linux

> 1. 输出日志,-n代表输出最后多少行，-f代表实时监视文件
> ```shell
> #这里实时输出日志的最后2000行
> tail -fn 2000 xxx.log
> ```

> 2. 复制文件
> ```shell
> cp -r /sourcePath/fileName /targetPath/fileName
> ```

> 3. 移动或重命名文件
> ```shell
> mv oldFleName newFileName
> ```
> ```shell
> mv sourcePath/example.txt /targetPath/example.txt
> ```

> 4. 解压.zip文件
> ```shell
> unzip zipName
> ```

> 5. 解压.tar.gz文件
> ```shell
> tar -zxvf fileName.tar.gz
> ```

> 6. -r递归删除文件或者目录
> ```shell
> rm -r fileName
> ```

> 7. 删除文件，-f忽略不存的文件，不做提示删除文件，-i则是互动式
> ```shell
> rm -rf fileName
> ```

> 8. 查看硬盘情况
> ```shell
> df -h 
> ```

> 9. 查看内存情况
> ```shell
> free -h
> ```

> 10. 按关键字搜索日志，可以使用vi打开日志，
      > 再输入“/+关键字”，回车进行查找，“N”是下一个

> 11. 查看文件夹下文件的大小
> ```shell
> ls -lah
> ```

---

## Windows
> 1. port=想查看的端口，如“8080”
> ```shell
> netstat -ano|findstr "port"
> ```

> 2. 杀死pid为1111的进程
> ```shell
> taskkill /pid 1111 -t -f
> ```

> 3. 查看端口开放情况
> ```shell
> telnet 127.0.0.1 8080
> ``` 

> 4. 查看当前class文件的jdk版本
> ```shell
> javap -verbose ClassFileName.class
> ```

---

## Mac
> 1. 开启redis服务
> ```shell
> brew services start redis
> ```

> 2. 关闭redis服务
> ```shell
> brew services stop redis
> ```

> 3. 进入redis客户端
>```shell
> redis-cli
>```

> 4. 关闭redis服务
> ```shell
> redis-cli shutdown
> ```

> 5. 查看端口情况
> ```shell
> lsof -i :port
>```





