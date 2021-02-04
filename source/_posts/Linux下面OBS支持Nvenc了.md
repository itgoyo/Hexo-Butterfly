---
title: Linux下面OBS支持Nvenc了
category: Linux
author: itgoyo
toc: true
tags: Linux
date: 2019-11-25 14:43:23
keywords:
description:
source_url:
---

B站视频链接：https://www.bilibili.com/video/av76908308
>之前双十一期间搞了一台二手主机，然后安装了Linux系统用来当作平时录制Linux的工具
### 硬件信息
- CPU：I5-4590
- 内存：光威 DDR3 1600Hz + 金士顿骇客神条DDR3 1600Hz
- 金士顿120G SSD
- 主板：技嘉B85M-D3V-Plus-SI
- 显卡：750TI

### 系统信息
- Linuxmint 19.2 Tina

### 刻盘工具
- Fedora LiveUSB Creator

安装完系统之后打开`nvidia driver`然后发现里面自带有英伟达最新的显卡驱动`Nvidia 435.21`，然后直接启动了

### PS！！！
本人之前一直没有成功使用OBS的`Nvenc`功能，之前失败一次是，安装了Nvidia 430，然后直接黑屏，后面好像是切换成Nvidia 418才解决的问题，安装Nvenc的时候最好留心一下，因为你装完驱动之后，你可能会进入不了系统，只能进入`tty`模式进去删英伟达驱动，之前我就是被这个东西搞得想死。

后面通过snap来安装`obs-studio`，因为通过这个方法安装的`obs-studio`是支持Nvenc硬件编码的，默认从官网上下载的却不行。

安装软件的命令

`sudo apt-get install snapd`

`snap install obs-studio`

`snap install obs-studio` //启动obs，或者你如果安装了rofi可以直接搜obs,或者在应用列表里面自己找

感受：录制比之前的要清晰不少，而且没有感觉到一边录制一遍操作电脑有任何的卡顿，还是硬件编码比较牛逼






---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>

