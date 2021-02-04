---
title: Vim编辑器insert切换回normal延迟卡顿的问题
category: Vim
author: itgoyo
toc: true
tags: Vim
date: 2019-07-12 13:37:17
keywords:
description:
source_url:
---
解决方式：
在`.vimrc`

加入

`set timeoutlen=1 ttimeoutlen=0`

即可完美解决





---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>
