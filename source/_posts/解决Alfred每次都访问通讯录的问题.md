---
title: 解决Alfred每次都访问通讯录的问题
category: Mac
tags: Mac
date: 2017-10-22 13:30:02
author:
keywords:
description:
source_url:
---
### 解决方法

打开终端或者iterm2，输入
```
sudo codesign -f -d -s - /Applications/Alfred\ 3.app/Contents/Frameworks/Alfred\ Framework.framework/Versions/A/Alfred\ Framework

```





---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>