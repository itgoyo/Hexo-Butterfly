---
title: 终端目录跳转软件autojump和z
category: 开源项目
toc: true
tags:
- python
- shell
date: 2018-12-14 16:30:21
author:
keywords:
description:
source_url:
---

![](https://raw.githubusercontent.com/itgoyo/PicRes/master/autojump_z.gif)

之前我们在终端目录跳转切换都是用`cd`，但是这个有一个缺点就是要具体输出前面的路径一点都不便捷。这里推荐两个比较智能的软件分别是`autojump` 和`z`。由于`z`体积比较小还有速率比较快，所以比较推荐大家使用`z`。

# autojump
地址：https://github.com/wting/autojump

## MANUAL

Grab a copy of autojump:

```
git clone git://github.com/wting/autojump.git

```

Run the installation script and follow on screen instructions.

```
cd autojump
./install.py or ./uninstall.py

```
### OS X

Homebrew is the recommended installation method for Mac OS X:

```
brew install autojump

```
MacPorts is also available:

```
port install autojump
```
### Windows

Windows support is enabled by [clink](https://mridgers.github.io/clink/) which should be installed prior to installing autojump.

# 注意！！！
要成功使用，必须要先cd目录，这样子才能生成相应的目录记录，这样子才能使用快捷跳转

# z
地址：https://github.com/rupa/z

## 配置
### 已安装zsh

在`.zshrc`文件默认有一句`plugins=(git)`，由于zsh默认带有 **Z** ，所以在这里把它添加进去就行，改为`plugins=(git z)`。

### 没安装zsh

在源码仓库里可以看到，**Z** 其实也就是一个 **.sh** 脚本，所以不管你用的是什么Terminal，只用按以下步骤就能马上使用 **Z** 。

> 1.  将z.sh下载到本地目录
> 2.  在根目录对应Terminal的文件（如果是默认的，一般是.bashrc）里加上`source `和z.sh所在目录
> 3.  之后重启Terminal就可以开始用了

# 注意！！！
要成功使用，必须要先cd目录，这样子才能生成相应的目录记录，这样子才能使用快捷跳转




---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>
