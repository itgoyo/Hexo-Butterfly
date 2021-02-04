---
title: 记hexo样式变化的奇怪错误
toc: true
category: 编程相关
author: itgoyo
tags: Program
date: 2019-07-15 08:41:13
keywords:
description:
source_url:
---
最近每次更新 hexo 内容之后，每次提交到 Github 之后的展示效果和在本地的展示效果有些差异，然后想到问题的可能性就是少提交了某些东西。然后看到每次`hexo d`的时候都有需要权限的错误，估计和之前遇到的错误类似，就是我现在的这个用户没有`hexo`的绝对权限，所以修改`hexo`目录的权限即可，最简单的方式莫过于`sudo chown -R itgoyo /Users/itgoyo/Documents/hexo/`。所以为了保证日后每次提交都正常，每次执行 hexo 命令之前都要先输入上面那句修改目录权限的代码，希望对你们同样也有帮助。





---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>