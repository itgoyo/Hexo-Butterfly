---
title: 记一次Hexo博客的莫名其妙错误
date: 2019-04-09 16:32:39
category: 生活随笔
author: itgoyo
tags:
- 生活随笔
- Hexo
toc: true
keywords:
description:
# 是否开启打赏, 开启填true,不开启填false
#reward: false
#reward_title:
# 开启打赏务必填写以下二选一,否则打赏图片是我的:)
#reward_wechat:
#reward_alipay:
# 转载的文章需要注明来源
source_url:
---


今天莫名其妙的把Node升级到v10.15.3,之前都版本都是8.几来的，然后碰巧提交了hexo，然后发现CSS样式显示异常，查看网站源码定位是因为找不到相应的CSS文件，然后手动提交了CSS代码，发现效果比之前都好看了一点点，但是整体效果还是很丑。

后面注意到每次`hexo c g d`
都会出现一句错误`Node Sass does not yet support your current environment: OS X 64-bit with Un`,然后顺着错误在网上搜了一下，解决方式

`npm install node-sass -D`

然后死活都因为权限问题安装不了，我一直chmod 777了很久，无果。后面想进入管理员模式`sudo su`之后一直提示密码错误，我用的一直都是这个密码怎么会出现错误呢，然后网上说是因为使用了`zsh`的原因

网上的解决方式：https://www.jianshu.com/p/ee9281bf1ace
```
因为最近要使用终端修改文件的权限，需要使用root，但是在输入root密码时候，su: Sorry提示密码输入错误，总归寻找到了修改的方法，并记录下来，因为我的终端不是bash，而是zsh，所以在切换到bash的时候没有输入密码，以下是我的操作:
输入：sudo bash
然后我的终端提示：bash-3.2#没有了其他信息，如果是bash用户可能会让输入当前用户的密码，就是登陆这个电脑用户的密码。
然后在终端键入sudo passwd root，记住是sudo passwd root不是sudo password root
然后终端提示
Changing password for root.
New password:

在New password:处键入新密码，在Retype new password:再次输入密码，然后提示bash-3.2#修改成功。

作者：差不多先生__
链接：https://www.jianshu.com/p/ee9281bf1ace
来源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。
```
完成之后再次进入终端安装成功，然后重新hexo c、g、d，也没错出现错误，让后看了一下hexo，显示效果终于恢复正常了。

理论上按照上面的操作即可修复，但是如果你在本地阅览效果还是达不到你的要求时候，你可以尝试清空浏览器的缓存，再次打开网站，希望对你有所帮助。


---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>
