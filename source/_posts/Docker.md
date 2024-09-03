---
title: Docker
date: 2024-09-03 15:34:01
tags:
  - Docker Order
categories:
  - 日常记录
excerpt: Docker常用命令
comments: false
---

> 1. check images
> ```shell
> docker images
> ```

> 2. check docker status
> ```shell
> docker ps
>```

> 3. dowmload image
> ```shell
> docker save -o fileName.tar imagerId
> ```
> ```shell
> docker save -o fileName.tar repositoryName:tag
> ```
> ```shell
> docker save repositoryName:tag > fileName.tar
> ```

> 4. modify image tag
> ```shell
> docker tag imageId tagName:tagVersion
> ```

> 5. import image
> ```shell
> docker load < fileName.tar
> ```

> 6. look log
> ```shell
> docker logs
> ```


> 7. delete image
> ```shell
> docker rmi -f imageId
> ```

> 8. enter docker
> ```shell
> docker exec -it dckerName /bin/bash
> ```

> 9. quit docker
> ```shell
> exit
> ```
