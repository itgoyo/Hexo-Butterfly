---
title: Tmux的使用教程
category: 开发工具
author: itgoyo
toc: true
tags: Android
date: 2020-01-17 15:34:00
keywords:
description:
source_url:
---
## 一、Tmux 是什么？

### 1.1 会话与进程

命令行的典型使用方式是，打开一个终端窗口（terminal window，以下简称 "窗口"），在里面输入命令。**用户与计算机的这种临时的交互，称为一次 "会话"（session）** 。

会话的一个重要特点是，窗口与其中启动的进程是[连在一起](http://www.ruanyifeng.com/blog/2016/02/linux-daemon.html)的。打开窗口，会话开始；关闭窗口，会话结束，会话内部的进程也会随之终止，不管有没有运行完。

一个典型的例子就是，[SSH 登录](http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html)远程计算机，打开一个远程窗口执行命令。这时，网络突然断线，再次登录的时候，是找不回上一次执行的命令的。因为上一次 SSH 会话已经终止了，里面的进程也随之消失了。

为了解决这个问题，会话与窗口可以 "解绑"：窗口关闭时，会话并不终止，而是继续运行，等到以后需要的时候，再让会话 "绑定" 其他窗口。

### 1.2 Tmux 的作用

**Tmux 就是会话与窗口的 "解绑" 工具，将它们彻底分离。**

> （1）它允许在单个窗口中，同时访问多个会话。这对于同时运行多个命令行程序很有用。
>
> （2） 它可以让新窗口 "接入" 已经存在的会话。
>
> （3）它允许每个会话有多个连接窗口，因此可以多人实时共享会话。
>
> （4）它还支持窗口任意的垂直和水平拆分。

类似的终端复用器还有 GNU Screen。Tmux 与它功能相似，但是更易用，也更强大。

## 二、基本用法

### 2.1 安装

Tmux 一般需要自己安装。

> ```bash
>
> # Ubuntu 或 Debian
> $ sudo apt-get install tmux
>
> # CentOS 或 Fedora
> $ sudo yum install tmux
>
> # Mac
> $ brew install tmux
>
> ```

### 2.2 启动与退出

安装完成后，键入 `tmux` 命令，就进入了 Tmux 窗口。

> ```bash
>
> $ tmux
>
> ```

上面命令会启动 Tmux 窗口，底部有一个状态栏。状态栏的左侧是窗口信息（编号和名称），右侧是系统信息。

![](https://www.wangbase.com/blogimg/asset/201910/bg2019102006.png)

按下 `Ctrl+d` 或者显式输入 `exit` 命令，就可以退出 Tmux 窗口。

> ```bash
>
> $ exit
>
> ```

### 2.3 前缀键

Tmux 窗口有大量的快捷键。所有快捷键都要通过前缀键唤起。默认的前缀键是 `Ctrl+b`，即先按下 `Ctrl+b`，快捷键才会生效。

举例来说，帮助命令的快捷键是 `Ctrl+b ?`。它的用法是，在 Tmux 窗口中，先按下 `Ctrl+b`，再按下 `?`，就会显示帮助信息。

然后，按下 ESC 键或 `q` 键，就可以退出帮助。

## 三、会话管理

### 3.1 新建会话

第一个启动的 Tmux 窗口，编号是 `0`，第二个窗口的编号是 `1`，以此类推。这些窗口对应的会话，就是 0 号会话、1 号会话。

使用编号区分会话，不太直观，更好的方法是为会话起名。

> ```bash
>
> $ tmux new -s <session-name>
>
> ```

上面命令新建一个指定名称的会话。

### 3.2 分离会话

在 Tmux 窗口中，按下 `Ctrl+b d` 或者输入 `tmux detach` 命令，就会将当前会话与窗口分离。

> ```bash
>
> $ tmux detach
>
> ```

上面命令执行后，就会退出当前 Tmux 窗口，但是会话和里面的进程仍然在后台运行。

`tmux ls` 命令可以查看当前所有的 Tmux 会话。

> ```bash
>
> $ tmux ls
> # or
> $ tmux list-session
>
> ```

### 3.3 接入会话

`tmux attach` 命令用于重新接入某个已存在的会话。

> ```bash
>
> # 使用会话编号
> $ tmux attach -t 0
>
> # 使用会话名称
> $ tmux attach -t <session-name>
>
> ```

### 3.4 杀死会话

`tmux kill-session` 命令用于杀死某个会话。

> ```bash
>
> # 使用会话编号
> $ tmux kill-session -t 0
>
> # 使用会话名称
> $ tmux kill-session -t <session-name>
>
> ```

### 3.5 切换会话

`tmux switch` 命令用于切换会话。

> ```bash
>
> # 使用会话编号
> $ tmux switch -t 0
>
> # 使用会话名称
> $ tmux switch -t <session-name>
>
> ```

### 3.6 重命名会话

`tmux rename-session` 命令用于重命名会话。

> ```bash
>
> $ tmux rename-session -t 0 <new-name>
>
> ```

上面命令将 0 号会话重命名。

### 3.7 会话快捷键

下面是一些会话相关的快捷键。

> *   `Ctrl+b d`：分离当前会话。
> *   `Ctrl+b s`：列出所有会话。
> *   `Ctrl+b $`：重命名当前会话。

## 四、最简操作流程

综上所述，以下是 Tmux 的最简操作流程。

> 1.  新建会话 `tmux new -s my_session`。
> 2.  在 Tmux 窗口运行所需的程序。
> 3.  按下快捷键 `Ctrl+b d` 将会话分离。
> 4.  下次使用时，重新连接到会话 `tmux attach-session -t my_session`。

## 五、窗格操作

Tmux 可以将窗口分成多个窗格（pane），每个窗格运行不同的命令。以下命令都是在 Tmux 窗口中执行。

### 5.1 划分窗格

`tmux split-window` 命令用来划分窗格。

> ```bash
>
> # 划分上下两个窗格
> $ tmux split-window
>
> # 划分左右两个窗格
> $ tmux split-window -h
>
> ```

![](https://www.wangbase.com/blogimg/asset/201910/bg2019102007.jpg)

### 5.2 移动光标

`tmux select-pane` 命令用来移动光标位置。

> ```bash
>
> # 光标切换到上方窗格
> $ tmux select-pane -U
>
> # 光标切换到下方窗格
> $ tmux select-pane -D
>
> # 光标切换到左边窗格
> $ tmux select-pane -L
>
> # 光标切换到右边窗格
> $ tmux select-pane -R
>
> ```

### 5.3 交换窗格位置

`tmux swap-pane` 命令用来交换窗格位置。

> ```bash
>
> # 当前窗格上移
> $ tmux swap-pane -U
>
> # 当前窗格下移
> $ tmux swap-pane -D
>
> ```

### 5.4 窗格快捷键

下面是一些窗格操作的快捷键。

> *   `Ctrl+b %`：划分左右两个窗格。
> *   `Ctrl+b "`：划分上下两个窗格。
> *   `Ctrl+b <arrow key>`：光标切换到其他窗格。`<arrow key>` 是指向要切换到的窗格的方向键，比如切换到下方窗格，就按方向键`↓`。
> *   `Ctrl+b ;`：光标切换到上一个窗格。
> *   `Ctrl+b o`：光标切换到下一个窗格。
> *   `Ctrl+b {`：当前窗格左移。
> *   `Ctrl+b }`：当前窗格右移。
> *   `Ctrl+b Ctrl+o`：当前窗格上移。
> *   `Ctrl+b Alt+o`：当前窗格下移。
> *   `Ctrl+b x`：关闭当前窗格。
> *   `Ctrl+b !`：将当前窗格拆分为一个独立窗口。
> *   `Ctrl+b z`：当前窗格全屏显示，再使用一次会变回原来大小。
> *   `Ctrl+b Ctrl+<arrow key>`：按箭头方向调整窗格大小。
> *   `Ctrl+b q`：显示窗格编号。

## 六、窗口管理

除了将一个窗口划分成多个窗格，Tmux 也允许新建多个窗口。

### 6.1 新建窗口

`tmux new-window` 命令用来创建新窗口。

> ```bash
>
> $ tmux new-window
>
> # 新建一个指定名称的窗口
> $ tmux new-window -n <window-name>
>
> ```

### 6.2 切换窗口

`tmux select-window` 命令用来切换窗口。

> ```bash
>
> # 切换到指定编号的窗口
> $ tmux select-window -t <window-number>
>
> # 切换到指定名称的窗口
> $ tmux select-window -t <window-name>
>
> ```

### 6.3 重命名窗口

`tmux rename-window` 命令用于为当前窗口起名（或重命名）。

> ```bash
>
> $ tmux rename-window <new-name>
>
> ```

### 6.4 窗口快捷键

下面是一些窗口操作的快捷键。

> *   `Ctrl+b c`：创建一个新窗口，状态栏会显示多个窗口的信息。
> *   `Ctrl+b p`：切换到上一个窗口（按照状态栏上的顺序）。
> *   `Ctrl+b n`：切换到下一个窗口。
> *   `Ctrl+b <number>`：切换到指定编号的窗口，其中的 `<number>` 是状态栏上的窗口编号。
> *   `Ctrl+b w`：从列表中选择窗口。
> *   `Ctrl+b ,`：窗口重命名。

## 七、其他命令

下面是一些其他命令。

> ```bash
>
> # 列出所有快捷键，及其对应的 Tmux 命令
> $ tmux list-keys
>
> # 列出所有 Tmux 命令及其参数
> $ tmux list-commands
>
> # 列出当前所有 Tmux 会话的信息
> $ tmux info
>
> # 重新加载当前的 Tmux 配置
> $ tmux source-file ~/.tmux.conf
>
> ```

### 八、tmux恢复插件tmux-resurrect
Tmux Resurrect 无须任何配置，就能够备份 tmux 会话中的各种细节，包括窗口、面板的顺序、布局、工作目录，运行程序等等数据。因此它能在系统重启后完全地恢复会话。由于其幂等的恢复机制，它不会试图去恢复一个已经存在的窗口或者面板，所以，即使你不小心多恢复了几次会话，它也不会出现问题，这样主动恢复时我们就不必担心手抖多按了一次。另外，如果你是 [tmuxinator](https://github.com/tmuxinator/tmuxinator) 用户，我也建议你迁移到 tmux-resurrect 插件上来，具体请参考 [Migrating from `tmuxinator`](https://github.com/tmux-plugins/tmux-resurrect/blob/master/docs/migrating_from_tmuxinator.md#migrating-from-tmuxinator)。

Tmux Resurrec 安装过程如下所示：

```
cd ~/.tmux
mkdir plugins
git clone https://github.com/tmux-plugins/tmux-resurrect.git

```

安装后需在 `~/.tmux.conf` 中增加一行配置：

```
run-shell ~/.tmux/plugins/tmux-resurrect/resurrect.tmux

```

至此安装成功，按下 `prefix + r` 重载 tmux 配置。

Tmux Resurrec 提供如下两个操作：

*   **保存**，快捷指令是 `prefix` + `Ctrl + s`，tmux 状态栏在保存开始，保存后分别提示”Saving…”，”Tmux environment saved !”。
*   **恢复**，快捷指令是 `prefix` + `Ctrl + r`，tmux 状态栏在恢复开始，恢复后分别提示”Restoring…”，”Tmux restore complete !”。

保存时，tmux 会话的详细信息会以文本文件的格式保存到 `~/.tmux/resurrect` 目录，恢复时则从此处读取，由于数据文件是明文的，因此你完全可以自由管理或者编辑这些会话状态文件（如果备份频繁，记得定期清除历史备份）。

**可选的配置**

Tmux Resurrec 本身是免配置开箱即用的，但同时也提供了如下选项以便修改其默认设置。

```
set -g @resurrect-save 'S' # 修改保存指令为S
set -g @resurrect-restore 'R' 修改恢复指令为R
# 修改会话数据的保持路径，此处不能使用除了$HOME, $HOSTNAME, ~之外的环境变量
set -g @resurrect-dir '/some/path'

```

默认情况下只有一个保守的列表项（即 `vi vim nvim emacs man less more tail top htop irssi mutt`）可以恢复，对此 [Restoring programs doc](https://github.com/tmux-plugins/tmux-resurrect/blob/master/docs/restoring_programs.md) 解释了怎么去恢复额外的项目。

**进阶的备份**

除了基础备份外，Tmux Resurrec 还提供**进阶的备份功能**，如下所示：

*   恢复 vim 和 neovim 会话
*   恢复面板内容
*   恢复 shell 的历史记录（实验性功能）

进阶的备份功能默认不开启，需要特别配置。

1）恢复 vim 和 neovim 会话，需要完成如下两步：

*   通过 vim 的 vim-obsession 插件保存 vim/neovim 会话。

    ```
    cd ~/.vim/bundle
    git clone git://github.com/tpope/vim-obsession.git
    vim -u NONE -c "helptags vim-obsession/doc" -c q

    ```

*   在 `~/.tmux.conf` 中增加两行配置：

    ```
    set -g @resurrect-strategy-vim 'session' # for vim
    set -g @resurrect-strategy-nvim 'session' # for neovim

    ```

2）恢复面板内容，需在 `~/.tmux.conf` 中增加一行配置：

```
set -g @resurrect-capture-pane-contents 'on' # 开启恢复面板内容功能

```

目前使用该功能时，请确保 tmux 的 `default-command` 没有包含 `&&` 或者 `||` 操作符，否则将导致 [bug](https://github.com/tmux-plugins/tmux-resurrect/issues/98)。（查看 `default-command` 的值，请使用命令 `tmux show -g default-command`。）

3）恢复 shell 的历史记录，需在 `~/.tmux.conf` 中增加一行配置：

```
set -g @resurrect-save-shell-history 'on'

```

由于技术的限制，保存时，只有无前台任务运行的面板，它的 shell 历史记录才能被保存。

## 九、参考链接

*   [A Quick and Easy Guide to tmux](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
*   [Tactical tmux: The 10 Most Important Commands](https://danielmiessler.com/study/tmux/)
*   [Getting started with Tmux](https://linuxize.com/post/getting-started-with-tmux/)
---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>
