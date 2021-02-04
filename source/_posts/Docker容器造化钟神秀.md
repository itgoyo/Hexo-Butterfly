---
title: Docker容器造化钟神秀
toc: true
category: 编程相关
author: itgoyo
tags: Program
date: 2020-01-19 11:48:50
keywords:
description:
source_url:
---
![](https://cdn.jsdelivr.net/gh/itgoyo/PicGoRes@master/img/docker.png)

之前闲暇之余有玩过一哈Dokcer容器，但是日子挺久了，然后挺多东西就忘记了，趁着今天有时间重拾一下docker的相关知识。

### 搜索下载镜像
`docker search ubuntu`

`docker pull ubuntu`

### 查看当前所有镜
`docker images`

### 启动容器
`docker run -it ubuntu /bin/bash`

参数说明：

-i: 交互式操作。
-t: 终端。
ubuntu: ubuntu 镜像。
/bin/bash：放在镜像名后的是命令，这里我们希望有个交互式 Shell，因此用的是 /bin/bash。
要退出终端，直接输入 exit:

### 查看所有运行的容器
`docker ps -a`

### docker start 启动一个已停止的容器
`docker start b750bbbcfd88 `

### 后台运行
在大部分的场景下，我们希望 docker 的服务是在后台运行的，我们可以过 -d 指定容器的运行模式。
```
$ docker run -itd --name ubuntu-test ubuntu /bin/bash
```

### 停止一个容器
```
$ docker stop <容器 ID>
```

### 重启一个容器
`docker restart <容器 ID>`

### 进入容器
在使用 -d 参数时，容器启动后会进入后台。此时想要进入容器，可以通过以下指令进入：

docker attach

docker exec：推荐大家使用 docker exec 命令，因为此退出容器终端，不会导致容器的停止。

### 导出容器
```
$ docker export 1e560fca3906 > ubuntu.tar
```

### 删除容器
`docker rm -f 1e560fca3906`

### 删除镜像
`docker rmi -f 1e560fca3906`

```
itgoyo@itgoyodeMacBook-Pro  ~  docker images
REPOSITORY                  TAG                 IMAGE ID            CREATED             SIZE
wahyd4/aria2-ui             latest              be489116face        2 months ago        100MB
530353222/baidupcs-web      3.6.8               2e1114282001        2 months ago        40.1MB
mysql                       latest              c7109f74d339        7 months ago        443MB
titpetric/netdata           latest              e75e93e28478        12 months ago       267MB
tomcat                      latest              1a51cb5e3006        12 months ago       462MB
nginx                       latest              7042885a156a        12 months ago       109MB
mysql                       5.7.23              1b30b36ae96a        15 months ago       372MB
haocen/hexo-with-hexo-hey   latest              e619af3ff3ea        2 years ago         332MB
```

第一列就是镜像的名称，例如我要删除ubuntu的镜像的话，就输入`docker rmi IMAGE ID`

### 注意点：

1. 删除前需要保证容器是停止的  stop

2. 需要注意删除镜像和容器的命令不一样。 docker rmi ID  , 其中 容器 (rm)  和 镜像 (rmi)

3. 顺序需要先删除容器



### 删除所有停止的容器
```
docker container prune
```

### 删除所有不是用的镜像
```
docker image prune --force --all或者docker image prune -f -a
```

### 启动容器的步骤

```
docker run -itd --name itgoyo-ubuntu ubuntu /bin/bash
docker exec -it itgoyo-ubuntu bin/bash
以下表示进入容器成功
root@95588eaee9f4:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@95588eaee9f4:/#
```

---
### SSH
查看当前的 ubuntu 是否安装了 ssh-server 服务。默认只安装 ssh-client 服务。

```
dpkg -l | grep ssh
```

安装 ssh-server 服务

```
sudo apt-get install openssh-server
```

确认 ssh-server 是否启动了：
```
ps -e | grep ssh
```

如果看到 sshd 那说明 ssh-server 已经启动了。
如果没有则可以这样启动：sudo /etc/init.d/ssh start 或 sudo service ssh start

配置相关：
ssh-server 配置文件位于 /etc/ssh/sshd_config，在这里可以定义 SSH 的服务端口，默认端口是 22，你可以自己定义成其他端口号，如 222。（或把配置文件中的”PermitRootLogin without-password” 加一个”#” 号，把它注释掉，再增加一句”PermitRootLogin yes”）

**然后重启 SSH 服务：**
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start

**登陆 SSH（Linux）**
ssh username@192.168.1.103
其中，username 为 192.168.1.103 机器上的用户，需要输入密码。
断开连接：exit

**查看当前的IP地址**
```
apt install net-tools
ifconfig
```

ssh: connect to host localhost port 22: Connection refused
        
解决方法是选择系统偏好设置 -> 选择共享 -> 点击远程登录

然后再输入命令 ssh localhost 发现已经解决问题




---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>
