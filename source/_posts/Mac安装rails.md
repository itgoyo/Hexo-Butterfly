---
title: Mac安装rails
toc: true
category: 编程相关
author: itgoyo
tags: Program
date: 2019-07-10 18:32:26
keywords:
description:
source_url:
---


## 安装 Rails

在终端中执行以下命令：

sudo gem install rails

可能会遇到以下问题：

ERROR:  Error installing rails:
	activesupport requires Ruby version >= 2.2.2.

使用：

ruby -v

查看当前版本

ruby 2.0.0p648 (2015-12-16 revision 53162) [universal.x86_64-darwin16]

## 升级 ruby

这一过程请参考：[macOS Ruby版本需要升级到2.2.2以上](http://www.voidcn.com/article/p-vcirvgff-vn.html)

升级完成后再执行上面的安装步骤。

## 创建 Rails 项目

1、查看 Rails 帮助，执行

rails

不需要带任何参数，输出的最后会给出创建项目的命令。

2、创建一个新项目

rails new ~/Code/Ruby/weblog

创建项目执行到

**run**  bundle install

时可能会出现提示：
```
The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
```
大概的意思是需要处理依赖关系。

3、处理依赖关系

切换到新建的项目目录：

cd ~/Code/Ruby/weblog

根据提示执行：

bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java

由于刚刚的

bundle install

没有执行完成，我们再执行

bundle install

4、启动服务器

rails server

5、打开浏览器，访问： [http://localhost:3000/](javascript:void())

# Yay! You’re on Rails!

看到类似文章顶部图片的页面了吧，恭喜你，搭建成功了。

6、停止服务
```
=> Booting Puma
=> Rails 5.1.2 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
Puma starting in single mode...
* Version 3.9.1 (ruby 2.2.6-p396), codename: Private Caller
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://0.0.0.0:3000
Use Ctrl-C to stop
```




---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>

