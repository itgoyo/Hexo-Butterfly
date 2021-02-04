---
title: Python基础一
category: Python
author: itgoyo
tags: Python
toc: true
date: 2019-09-26 19:26:16
keywords:
description:
source_url:
---


# 一，Python 介绍

#### **1\. python 的出生与应用**

　　python 的创始人为吉多・范罗苏姆（Guido van Rossum）。1989 年的圣诞节期间，吉多・范罗苏姆（中文名字：龟叔）为了在阿姆斯特丹打发时间，决心开发一个新的脚本解释程序，作为 ABC 语言的一种继承。  

（龟叔：2005 年加入谷歌至 2012 年，2013 年加入 Dropbox 直到现在，依然掌握着 Python 发展的核心方向，被称为仁慈的独裁者）。

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170911121503547-2124074284.png)

2017 年 7 月的 TIOBE 排行榜，Python 已经占据第四的位置， Python 崇尚优美、清晰、简单，是一个优秀并广泛使用的语言。

![](https://images2017.cnblogs.com/blog/988316/201708/988316-20170831184813937-1153395617.png)

由上图可见，Python 整体呈上升趋势，反映出 Python 应用越来越广泛并且也逐渐得到业内的认可！！！

Python 可以应用于众多领域，如：数据分析、组件集成、网络服务、图像处理、数值计算和科学计算等众多领域。目前业内几乎所有大中型互联网企业都在使用 Python，如：Youtube、Dropbox、BT、Quora（中国知乎）、豆瓣、知乎、Google、Yahoo!、Facebook、NASA、百度、腾讯、汽车之家、美团等。

**目前 Python 主要应用领域：**

*   **云计算**: 云计算最火的语言， 典型应用 OpenStack
*   **WEB 开发**: 众多优秀的 WEB 框架，众多大型网站均为 Python 开发，Youtube, Dropbox, 豆瓣。。。， 典型 WEB 框架有 Django
*   **科学运算、人工智能**: 典型库 NumPy, SciPy, Matplotlib, Enthought librarys,pandas
*   **系统运维**: 运维人员必备语言
*   **金融**：量化交易，金融分析，在金融工程领域，Python 不但在用，且用的最多，而且重要性逐年提高。原因：作为动态语言的 Python，语言结构清晰简单，库丰富，成熟稳定，科学计算和统计分析都很牛逼，生产效率远远高于 c,c++,java, 尤其擅长策略回测
*   **图形 GUI**: PyQT, WxPython,TkInter

**Python 在一些公司的应用： **

*   谷歌：Google App Engine 、code.google.com 、Google earth 、谷歌爬虫、Google 广告等项目都在大量使用 Python 开发
*   CIA: 美国中情局网站就是用 Python 开发的
*   NASA: 美国航天局 (NASA) 大量使用 Python 进行数据分析和运算
*   YouTube: 世界上最大的视频网站 YouTube 就是用 Python 开发的
*   Dropbox: 美国最大的在线云存储网站，全部用 Python 实现，每天网站处理 10 亿个文件的上传和下载
*   Instagram: 美国最大的图片分享社交网站，每天超过 3 千万张照片被分享，全部用 python 开发
*   Facebook: 大量的基础库均通过 Python 实现的
*   Redhat: 世界上最流行的 Linux 发行版本中的 yum 包管理工具就是用 python 开发的
*   豆瓣：公司几乎所有的业务均是通过 Python 开发的
*   知乎：国内最大的问答社区，通过 Python 开发 (国外 Quora)
*   春雨医生：国内知名的在线医疗网站是用 Python 开发的
*   除上面之外，还有搜狐、金山、腾讯、盛大、网易、百度、阿里、淘宝 、土豆、新浪、果壳等公司都在使用 Python 完成各种各样的任务。 

**python 发展史**

*   1989 年，为了打发圣诞节假期，Guido 开始写 Python 语言的编译器。Python 这个名字，来自 Guido 所挚爱的电视剧 Monty Python’s Flying Circus。他希望这个新的叫做 Python 的语言，能符合他的理想：创造一种 C 和 shell 之间，功能全面，易学易用，可拓展的语言。
*   1991 年，第一个 Python 编译器诞生。它是用 C 语言实现的，并能够调用 C 语言的库文件。从一出生，Python 已经具有了：类，函数，异常处理，包含表和词典在内的核心数据类型，以及模块为基础的拓展系统。
*   Granddaddy of Python web frameworks, Zope 1 was released in 1999
*   Python 1.0 - January 1994 增加了 [lambda](https://en.wikipedia.org/wiki/Lambda_calculus), [map](https://en.wikipedia.org/wiki/Map_%28higher-order_function%29), [filter](https://en.wikipedia.org/wiki/Filter_%28higher-order_function%29) and [reduce](https://en.wikipedia.org/wiki/Fold_%28higher-order_function%29).
*   Python 2.0 - October 16, 2000，加入了内存回收机制，构成了现在 Python 语言框架的基础
*   Python 2.4 - November 30, 2004, 同年目前最流行的 WEB 框架 Django 诞生
*   Python 2.5 - September 19, 2006
*   Python 2.6 - October 1, 2008
*   Python 2.7 - July 3, 2010
*   In November 2014, it was announced that Python 2.7 would be supported until 2020, and reaffirmed that there would be no 2.8 release as users were expected to move to Python 3.4+ as soon as possible
*   Python 3.0 - December 3, 2008
*   Python 3.1 - June 27, 2009
*   Python 3.2 - February 20, 2011
*   Python 3.3 - September 29, 2012
*   Python 3.4 - March 16, 2014
*   Python 3.5 - September 13, 2015
*   Python 3.6 - December 16,2016

#### **2\. python 是什么编程语言。**

_编程语言主要从以下几个角度为进行分类，编译型和解释型、静态语言和动态语言、强类型定义语言和弱类型定义语言，每个分类代表什么意思呢，我们一起来看一下。_

**2.1 编译型与解释型。**

**编译器**是把源程序的每一条语句都编译成机器语言，并保存成二进制文件，这样运行时计算机可以直接以机器语言来运行此程序，速度很快； 

而**解释器**则是只在执行程序时，才一条一条的解释成机器语言给计算机来执行，所以运行速度是不如编译后的程序运行的快的. 

这是因为计算机不能直接认识并执行我们写的语句，它只能认识机器语言 (是二进制的形式)

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170911120842485-871465200.png)

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170911120939860-618931676.png)

**编译型**
优点：编译器一般会有预编译的过程对代码进行优化。因为编译只做一次，运行时不需要编译，所以编译型语言的程序执行效率高。可以脱离语言环境独立运行。
缺点：编译之后如果需要修改就需要整个模块重新编译。编译的时候根据对应的运行环境生成机器码，不同的操作系统之间移植就会有问题，需要根据运行的操作系统环境编译不同的可执行文件。

**解释型**
优点：有良好的平台兼容性，在任何环境中都可以运行，前提是安装了解释器（虚拟机）。灵活，修改代码的时候直接修改就可以，可以快速部署，不用停机维护。

缺点：每次运行的时候都要解释一遍，性能上不如编译型语言。

**2.2 动态语言和静态语言**
通常我们所说的动态语言、静态语言是指动态类型语言和静态类型语言。

（1）动态类型语言：动态类型语言是指在运行期间才去做数据类型检查的语言，也就是说，在用动态类型的语言编程时，永远也不用给任何变量指定数据类型，该语言会在你第一次赋值给变量时，在内部将数据类型记录下来。Python 和 Ruby 就是一种典型的动态类型语言，其他的各种脚本语言如 VBScript 也多少属于动态类型语言。

（2）静态类型语言：静态类型语言与动态类型语言刚好相反，它的数据类型是在编译其间检查的，也就是说在写程序时要声明所有变量的数据类型，C/C++ 是静态类型语言的典型代表，其他的静态类型语言还有 C#、JAVA 等。

**2.3 强类型定义语言和弱类型定义语言**

（1）强类型定义语言：强制数据类型定义的语言。也就是说，一旦一个变量被指定了某个数据类型，如果不经过强制转换，那么它就永远是这个数据类型了。举个例子：如果你定义了一个整型变量 a, 那么程序根本不可能将 a 当作字符串类型处理。强类型定义语言是类型安全的语言。

（2）弱类型定义语言：数据类型可以被忽略的语言。它与强类型定义语言相反，一个变量可以赋不同数据类型的值。

强类型定义语言在速度上可能略逊色于弱类型定义语言，但是强类型定义语言带来的严谨性能够有效的避免许多错误。另外，“这门语言是不是动态语言” 与 “这门语言是否类型安全” 之间是完全没有联系的！
例如：Python 是动态语言，是强类型定义语言（类型安全的语言）; VBScript 是动态语言，是弱类型定义语言（类型不安全的语言）; JAVA 是静态语言，是强类型定义语言（类型安全的语言）。

通过上面这些介绍，我们可以得出，**python 是一门动态解释性的强类型定义语言。**

#### **3\. python 的优缺点。**

先看优点

1.  Python 的定位是 “优雅”、“明确”、“简单”，所以 Python 程序看上去总是简单易懂，初学者学 Python，不但入门容易，而且将来深入下去，可以编写那些非常非常复杂的程序。
2.  开发效率非常高，Python 有非常强大的第三方库，基本上你想通过计算机实现任何功能，Python 官方库里都有相应的模块进行支持，直接下载调用后，在基础库的基础上再进行开发，大大降低开发周期，避免重复造轮子。
3.  高级语言 ———— 当你用 Python 语言编写程序的时候，你无需考虑诸如如何管理你的程序使用的内存一类的底层细节
4.  可移植性 ———— 由于它的开源本质，Python 已经被移植在许多平台上（经过改动使它能够工 作在不同平台上）。如果你小心地避免使用依赖于系统的特性，那么你的所有 Python 程序无需修改就几乎可以在市场上所有的系统平台上运行
5.  可扩展性 ———— 如果你需要你的一段关键代码运行得更快或者希望某些算法不公开，你可以把你的部分程序用 C 或 C++ 编写，然后在你的 Python 程序中使用它们。
6.  可嵌入性 ———— 你可以把 Python 嵌入你的 C/C++ 程序，从而向你的程序用户提供脚本功能。

再看缺点：

1.  速度慢，Python 的运行速度相比 C 语言确实慢很多，跟 JAVA 相比也要慢一些，因此这也是很多所谓的大牛不屑于使用 Python 的主要原因，但其实这里所指的运行速度慢在大多数情况下用户是无法直接感知到的，必须借助测试工具才能体现出来，比如你用 C 运一个程序花了 0.01s, 用 Python 是 0.1s, 这样 C 语言直接比 Python 快了 10 倍，算是非常夸张了，但是你是无法直接通过肉眼感知的，因为一个正常人所能感知的时间最小单位是 0.15-0.4s 左右，哈哈。其实在大多数情况下 Python 已经完全可以满足你对程序速度的要求，除非你要写对速度要求极高的搜索引擎等，这种情况下，当然还是建议你用 C 去实现的。
2.  代码不能加密，因为 PYTHON 是解释性语言，它的源码都是以名文形式存放的，不过我不认为这算是一个缺点，如果你的项目要求源代码必须是加密的，那你一开始就不应该用 Python 来去实现。
3.  线程不能利用多 CPU 问题，这是 Python 被人诟病最多的一个缺点，GIL 即全局解释器锁（Global Interpreter Lock），是[计算机程序设计语言](http://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1%E8%AF%AD%E8%A8%80 "计算机程序设计语言")[解释器](http://zh.wikipedia.org/wiki/%E8%A7%A3%E9%87%8A%E5%99%A8 "解释器")用于[同步](http://zh.wikipedia.org/wiki/%E5%90%8C%E6%AD%A5 "同步")[线程](http://zh.wikipedia.org/wiki/%E7%BA%BF%E7%A8%8B "线程")的工具，使得任何时刻仅有一个线程在执行，Python 的线程是操作系统的原生线程。在 Linux 上为 pthread，在 Windows 上为 Win thread，完全由操作系统调度线程的执行。一个 python 解释器进程内有一条主线程，以及多条用户程序的执行线程。即使在多核 CPU 平台上，由于 GIL 的存在，所以禁止多线程的并行执行。关于这个问题的折衷解决方法，我们在以后线程和进程章节里再进行详细探讨。

当我们编写 Python 代码时，我们得到的是一个包含 Python 代码的以`.py` 为扩展名的文本文件。要运行代码，就需要 Python 解释器去执行`.py` 文件。

由于整个 Python 语言从规范到解释器都是开源的，所以理论上，只要水平够高，任何人都可以编写 Python 解释器来执行 Python 代码（当然难度很大）。事实上，确实存在多种 Python 解释器。

#### 4\. python 的种类。

**CPython**

当我们从 [Python 官方网站](https://www.python.org/)下载并安装好 Python 3.6 后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用 C 语言开发的，所以叫 CPython。在命令行下运行 `python` 就是启动 CPython 解释器。

CPython 是使用最广的 Python 解释器。教程的所有代码也都在 CPython 下执行。

**IPython**

IPython 是基于 CPython 之上的一个交互式解释器，也就是说，IPython 只是在交互方式上有所增强，但是执行 Python 代码的功能和 CPython 是完全一样的。好比很多国产浏览器虽然外观不同，但内核其实都是调用了 IE。

CPython 用 `>>>` 作为提示符，而 IPython 用 `In [``序号``]:` 作为提示符。

**PyPy**

PyPy 是另一个 Python 解释器，它的目标是执行速度。PyPy 采用 [JIT 技术](http://en.wikipedia.org/wiki/Just-in-time_compilation)，对 Python 代码进行动态编译（注意不是解释），所以可以显著提高 Python 代码的执行速度。

绝大部分 Python 代码都可以在 PyPy 下运行，但是 PyPy 和 CPython 有一些是不同的，这就导致相同的 Python 代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到 PyPy 下执行，就需要了解 [PyPy 和 CPython 的不同点](http://pypy.readthedocs.org/en/latest/cpython_differences.html)。

**Jython**

Jython 是运行在 Java 平台上的 Python 解释器，可以直接把 Python 代码编译成 Java 字节码执行。

**IronPython**

IronPython 和 Jython 类似，只不过 IronPython 是运行在微软.Net 平台上的 Python 解释器，可以直接把 Python 代码编译成.Net 的字节码。

**小结：**

　　Python 的解释器很多，但使用最广泛的还是 CPython。如果要和 Java 或.Net 平台交互，最好的办法不是用 Jython 或 IronPython，而是通过网络调用来交互，确保各程序之间的独立性。

# 二. python 环境

windows 下安装 Python（手动添加环境变量）以 2.7 版本举例：

**windows：**


`1``、下载安装包`

`https:``/``/``www.python.org``/``downloads``/`

`2``、安装`

`默认安装路径：C:\python27`

`3``、配置环境变量`

`【右键计算机】``-``-``》【属性】``-``-``》【高级系统设置】``-``-``》【高级】``-``-``》【环境变量】``-``-``》【在第二个内容框中找到 变量名为Path 的一行，双击】 ``-``-``> 【Python安装目录追加到变值值中，用 ； 分割】`

`如：原来的值;C:\python27，切记前面有分号`


windows 下安装 Python（自动添加环境变量）以 3,.5 版本的举例：

1\. 官网下载：[https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/) 

2\. 选择版本。

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170915172514469-312217099.png)

3\. 自动添加环境变量。

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170915172904078-2110770811.png)

4\. 更改完成。

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170915173126860-82071647.png)

5\. 点击安装即可。

**linux：**



`无需安装，原装Python环境`

`ps：如果自带``2.6``，请更新至``2.7`


#  三. python 基础初识。

####  1\. 运行 python 代码。

在 d 盘下创建一个 t1.py 文件内容是：

print('hello world')

打开 windows 命令行输入 cmd，确定后 写入代码 python d:t1.py 

![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170917111005797-4582581.png)![](https://images2017.cnblogs.com/blog/988316/201709/988316-20170917111305953-1783077606.png)

您已经运行了第一个 python 程序， 即：终端 ---->cmd-----> python  文件路径。 回车搞定～

#### 2\. 解释器。

上一步中执行 python d:t1.py 时，明确的指出 t1.py 脚本由 python 解释器来执行。

如果想要类似于执行 shell 脚本一样执行 python 脚本，例： `./t1.py `，那么就需要在 hello.py 文件的头部指定解释器，如下：


`#!/usr/bin/env python`

`print` `"hello,world"`



如此一来，执行： .`/t1.py` 即可。

ps：执行前需给予 t1.py 执行权限，chmod 755 t1.py

#### 3\. 注释。

当行注释：# 被注释内容

多行注释：''' 被注释内容 '''，或者 """被注释内容"""

#### 4\. 变量

变量是什么？  变量：把程序运行的中间结果临时的存在内存里，以便后续的代码调用。

4.1、声明变量

lux = '鲁迅本人'

上述代码声明了一个变量，变量名为： lux，变量 name 的值为："鲁迅本人"

变量的作用：昵称，其代指内存里某个地址中保存的内容

![](https://img2018.cnblogs.com/blog/988316/201903/988316-20190320161204923-1333237354.png)

4.2、变量定义的规则：

*   变量名只能是 字母、数字或下划线的任意组合
*   变量名的第一个字符不能是数字
*   以下关键字不能声明为变量名
    ['and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'exec', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'not', 'or', 'pass', 'print', 'raise', 'return', 'try', 'while', 'with', 'yield']
*   变量的定义要具有可描述性。

4.3、推荐定义方式


#驼峰体
 AgeOfOldboy = 56 NumberOfStudents = 80

#下划线
 age_of_oldboy = 56 number_of_students = 80


> 你觉得哪种更清晰，哪种就是官方推荐的，我想你肯定会先第 2 种，第一种 AgeOfOldboy 咋一看以为是 AngelaBaby

4.4、变量的赋值
```
lux = '鲁迅本人'、
name = '太白金星'
```
![](https://img2018.cnblogs.com/blog/988316/201903/988316-20190320161740585-1210403150.png)

name1 = '太白金星' name2 = name1
name3 = name2

![](https://img2018.cnblogs.com/blog/988316/201903/988316-20190320162125444-1315440542.png)

4.5、定义变量不好的方式举例

*   变量名为中文、拼音
*   变量名过长
*   变量名词不达意

#### 5\. 常量

常量即指不变的量，如 pai 3.141592653..., 或在程序运行过程中不会改变的量

举例，假如老男孩老师的年龄会变，那这就是个变量，但在一些情况下，他的年龄不会变了，那就是常量。在 Python 中没有一个专门的语法代表常量，程序员约定俗成用变量名全部大写代表常量

```
AGE_OF_OLDBOY = 56

```

> 在 c 语言中有专门的常量定义语法，`const int count = 60;` 一旦定义为常量，更改即会报错

#### 6\. 基础数据类型（初始）。

什么是数据类型？

　　我们人类可以很容易的分清数字与字符的区别，但是计算机并不能呀，计算机虽然很强大，但从某种角度上看又很傻，除非你明确的告诉它，1 是数字，“汉” 是文字，否则它是分不清 1 和‘汉’的区别的，因此，在每个编程语言里都会有一个叫数据类型的东东，其实就是对常用的各种数据类型进行了明确的划分，你想让计算机进行数值运算，你就传数字给它，你想让他处理文字，就传字符串类型给他。Python 中常用的数据类型有多种，今天我们暂只讲 3 种， 数字、字符串、布尔类型

6.1、整数类型（int）。

int（整型）

在 32 位机器上，整数的位数为 32 位，取值范围为 - 2**31～2**31-1，即 - 2147483648～2147483647

在 64 位系统上，整数的位数为 64 位，取值范围为 - 2**63～2**63-1，即 - 9223372036854775808～9223372036854775807

> 除了 int 之外， 其实还有 float 浮点型，复数型，但今天先不讲啦

6.2、字符串类型（str）。

在 Python 中，加了引号的字符都被认为是字符串！


>>> name = "Alex Li" #双引号
>>> age = "22"       #只要加引号就是字符串
>>> age2 = 22          #int
>>>
>>> msg = '''My name is taibai, I am 22 years old!'''  #我擦，3个引号也可以
>>>
>>> hometown = 'ShanDong'   #单引号也可以


那单引号、双引号、多引号有什么区别呢？ 让我大声告诉你，单双引号木有任何区别，只有下面这种情况 你需要考虑单双的配合

```
msg = "My name is Alex , I'm 22 years old!"

```

多引号什么作用呢？作用就是多行字符串必须用多引号


msg = '''
今天我想写首小诗，
歌颂我的同桌，
你看他那乌黑的短发，
好像一只炸毛鸡。
'''
print(msg)


字符串拼接

数字可以进行加减乘除等运算，字符串呢？让我大声告诉你，也能？what ? 是的，但只能进行 "相加" 和 "相乘" 运算。


>>> name
'Alex Li'
>>> age
'22'
>>>
>>> name + age  #相加其实就是简单拼接
'Alex Li22'
>>>
>>> name * 10 #相乘其实就是复制自己多少次，再拼接在一起
'Alex LiAlex LiAlex LiAlex LiAlex LiAlex LiAlex LiAlex LiAlex LiAlex Li'


注意，字符串的拼接只能是双方都是字符串，不能跟数字或其它类型拼接


>>> type(name),type(age2)
(<type 'str'>, <type 'int'>)
>>>
>>> name
'Alex Li'
>>> age2
22
>>> name + age2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module> TypeError: cannot concatenate 'str' and 'int' objects #错误提示数字 和 字符 不能拼接


6.3、布尔值（True，False）。

布尔类型很简单，就两个值 ，一个 True (真)，一个 False (假), 主要用记逻辑判断

但其实你们并不明白对么？ let me explain, 我现在有 2 个值 ， a=3, b=5 , 我说 a>b 你说成立么？我们当然知道不成立，但问题是计算机怎么去描述这成不成立呢？或者说 a< b 是成立，计算机怎么描述这是成立呢？

没错，答案就是，用布尔类型


>>> a=3
>>> b=5
>>>
>>> a > b #不成立就是False,即假
False
>>>
>>> a < b #成立就是True, 即真
True


####  7\. 程序交互


#!/usr/bin/env python # -*- coding: utf-8 -*-

# 将用户输入的内容赋值给 name 变量
name = input("请输入用户名：") # 打印输入的内容
print(name)


执行脚本就会发现，程序会等待你输入姓名后再往下继续走。

可以让用户输入多个信息，如下

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

name = input("What is your name?")
age = input("How old are you?")
hometown = input("Where is your hometown?") print("Hello ",name , "your are ", age , "years old, you came from",hometown)
```

#### 8\. 流程控制之 --if。

　　假如把写程序比做走路，那我们到现在为止，一直走的都是直路，还没遇到过分叉口，想象现实中，你遇到了分叉口，然后你决定往哪拐必然是有所动机的。你要判断那条岔路是你真正要走的路，如果我们想让程序也能处理这样的判断怎么办？ 很简单，只需要在程序里预设一些条件判断语句，满足哪个条件，就走哪条岔路。这个过程就叫流程控制。

if...else 语句

单分支

if 条件:
    满足条件后要执行的代码

双分支


""" if 条件:
    满足条件执行代码
else:
    if条件不满足就走这段 """ AgeOfOldboy = 48

if AgeOfOldboy > 50 : print("Too old, time to retire..") else: print("还能折腾几年!")


缩进

> 这里必须要插入这个缩进的知识点

你会发现，上面的 if 代码里，每个条件的下一行都缩进了 4 个空格，这是为什么呢？这就是 Python 的一大特色，强制缩进，目的是为了让程序知道，每段代码依赖哪个条件，如果不通过缩进来区分，程序怎么会知道，当你的条件成立后，去执行哪些代码呢？

在其它的语言里，大多通过 `{}` 来确定代码块，比如 C,C++,Java,Javascript 都是这样，看一个 JavaScript 代码的例子


var age = 56
if ( age < 50){
  console.log("还能折腾")
    console.log('可以执行多行代码')
}else{
   console.log('太老了')
}


在有 `{}` 来区分代码块的情况下，缩进的作用就只剩下让代码变的整洁了。

Python 是门超级简洁的语言，发明者定是觉得用 `{}` 太丑了，所以索性直接不用它，那怎么能区分代码块呢？答案就是强制缩进。

Python 的缩进有以下几个原则:

*   顶级代码必须顶行写，即如果一行代码本身不依赖于任何条件，那它必须不能进行任何缩进
*   同一级别的代码，缩进必须一致
*   官方建议缩进用 4 个空格，当然你也可以用 2 个，如果你想被人笑话的话。

多分支

回到流程控制上来，if...else ... 可以有多个分支条件


if 条件:
    满足条件执行代码 elif 条件:
    上面的条件不满足就走这个 elif 条件:
    上面的条件不满足就走这个 elif 条件:
    上面的条件不满足就走这个 else:
    上面所有的条件不满足就走这段


写个猜年龄的游戏吧


age_of_oldboy = 48 guess = int(input(">>:")) if guess > age_of_oldboy : print("猜的太大了，往小里试试...") elif guess < age_of_oldboy : print("猜的太小了，往大里试试...") else: print("恭喜你，猜对了...")


上面的例子，根据你输入的值不同，会最多得到 3 种不同的结果

再来个匹配成绩的小程序吧，成绩有 ABCDE5 个等级，与分数的对应关系如下

```
A    90-100
B    80-89
C    60-79
D    40-59
E    0-39

```

要求用户输入 0-100 的数字后，你能正确打印他的对应成绩


score = int(input("输入分数:")) if score > 100: print("我擦，最高分才100...") elif score >= 90: print("A") elif score >= 80: print("B") elif score >= 60: print("C") elif score >= 40: print("D") else: print("太笨了...E")


这里有个问题，就是当我输入 95 的时候 ，它打印的结果是 A, 但是 95 明明也大于第二个条件 `elif score >=80:` 呀，为什么不打印 B 呢？这是因为代码是从上到下依次判断，只要满足一个，就不会再往下走啦，这一点一定要清楚呀！


---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:fullstacker

![](/img/qrcode.jpg)
</div>
