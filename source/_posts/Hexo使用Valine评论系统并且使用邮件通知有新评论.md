---
title: Hexo使用Valine评论系统并且使用邮件通知有新评论
toc: true
category: 编程相关
author: itgoyo
tags: Program
date: 2019-07-12 18:52:53
keywords:
description:
source_url:
---

今天在用 hexo 的时候发现个别文章有别人使用`Valine`的评论，但是当我发现的时候时间已经过去了几个月了，根本就不知道有消息提醒这回事，首先Value 没看到有一个管理员系统，所以没法查看总的未提醒数。后面在 Value 原作者 Github 上面发现了他有通过`leancloud`然后使用邮件来提醒，通过一个下午的实验终于成功了，我把捣弄过程中我遇到的坑给大家说一下。
### 坑一
代码仓库地址是填写[https://github.com/DesertsP/Valine-Admin.git](https://github.com/DesertsP/Valine-Admin.git)不是填写你自己 Github 上面的仓库，统一都是使用这个地址，之前我不知道导致填写定时任务的时候一直出错。
### 坑二
在填写接收邮箱密码的时候写的不是你的邮箱密码，而是在邮箱设置里面的POP3/IMAP生成的`授权码`，这个是随机生成的。之前一直调不通就是因为这个原因。

----
# 以下是原作者的教程打开可以参考一下
> aline Admin 是 [Valine 评论系统](https://panjunwen.com/diy-a-comment-system/)的扩展和增强，主要实现评论邮件通知、评论管理、垃圾评论过滤等功能。支持完全自定义的邮件通知模板，基于Akismet API实现准确的垃圾评论过滤。
> 近期更改了Github用户名请留意，仓库链接更新为https://github.com/DesertsP/Valine-Admin.git

### 云引擎"一键"部署

1.  在[Leancloud](https://leancloud.cn/dashboard/#/apps)云引擎设置界面，填写代码库并保存：[https://github.com/DesertsP/Valine-Admin.git](https://github.com/DesertsP/Valine-Admin.git)

![设置仓库](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-12-56-04.png)

1.  在设置页面，设置环境变量以及 Web 二级域名。

![环境变量](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-3-40-48.png)

| 变量 | 示例 | 说明 |
| --- | --- | --- |
| SITE_NAME | Deserts | [必填]博客名称 |
| SITE_URL | [https://panjunwen.com](https://panjunwen.com/) | [必填]首页地址 |
| **SMTP_SERVICE** | QQ | [新版支持]邮件服务提供商，支持 QQ、163、126、Gmail 以及 [更多](https://nodemailer.com/smtp/well-known/#supported-services) |
| SMTP_USER | [xxxxxx@qq.com](mailto:xxxxxx@qq.com) | [必填]SMTP登录用户 |
| SMTP_PASS | ccxxxxxxxxch | [必填]SMTP登录密码（QQ邮箱需要获取独立密码） |
| SENDER_NAME | Deserts | [必填]发件人 |
| SENDER_EMAIL | [xxxxxx@qq.com](mailto:xxxxxx@qq.com) | [必填]发件邮箱 |
| ADMIN_URL | [https://xxx.leanapp.cn/](https://xxx.leanapp.cn/) | [建议]Web主机二级域名，用于自动唤醒 |
| BLOGGER_EMAIL | [xxxxx@gmail.com](mailto:xxxxx@gmail.com) | [可选]博主通知收件地址，默认使用SENDER_EMAIL |
| AKISMET_KEY | xxxxxxxxxxxx | [可选]Akismet Key 用于垃圾评论检测，设为MANUAL_REVIEW开启人工审核，留空不使用反垃圾 |

**以上必填参数请务必正确设置。**

二级域名用于评论后台管理，如[https://deserts.leanapp.cn](https://deserts.leanapp.cn/) 。

![二级域名](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-1-06-41.png)

1.  切换到部署标签页，分支使用master，点击部署即可

![一键部署](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-12-56-50.png)

第一次部署需要花点时间。

![部署过程](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-1-00-45.png)

1.  评论管理。访问设置的二级域名`https://二级域名.leanapp.cn/sign-up`，注册管理员登录信息，如：[https://deserts.leanapp.cn/sign-up](https://deserts.leanapp.cn/sign-up)
    ![管理员注册](https://cloud.panjunwen.com/2018/10/ping-mu-kuai-zhao-2018-10-22-xia-wu-9-35-51.png)

    > 注：使用原版Valine如果遇到注册页面不显示直接跳转至登录页的情况，请手动删除_User表中的全部数据。

此后，可以通过`https://二级域名.leanapp.cn/`管理评论。

1.  定时任务设置

目前实现了两种云函数定时任务：(1)自动唤醒，定时访问Web APP二级域名防止云引擎休眠；(2)每天定时检查24小时内漏发的邮件通知。

进入云引擎-定时任务中，创建定时器，创建两个定时任务。

选择self-wake云函数，Cron表达式为`0 0/30 7-23 * * ?`，表示每天早6点到晚23点每隔30分钟访问云引擎，`ADMIN_URL`环境变量务必设置正确：

![唤醒云引擎](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-18-xia-wu-2-57-43.png)

选择resend-mails云函数，Cron表达式为`0 0 8 * * ?`，表示每天早8点检查过去24小时内漏发的通知邮件并补发：

![通知检查](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-18-xia-wu-2-57-53.png)

**添加定时器后记得点击启动方可生效。**

**至此，Valine Admin 已经可以正常工作，更多以下是可选的进阶配置。**

### 邮件通知模板

邮件通知模板在云引擎环境变量中设定，可自定义通知邮件标题及内容模板。

| 环境变量 | 示例 | 说明 |
| --- | --- | --- |
| MAIL_SUBJECT | ${PARENT_NICK}，您在${SITE_NAME}上的评论收到了回复 | [可选]@通知邮件主题（标题）模板 |
| MAIL_TEMPLATE | 见下文 | [可选]@通知邮件内容模板 |
| MAIL_SUBJECT_ADMIN | ${SITE_NAME}上有新评论了 | [可选]博主邮件通知主题模板 |
| MAIL_TEMPLATE_ADMIN | 见下文 | [可选]博主邮件通知内容模板 |

邮件通知包含两种，分别是被@通知和博主通知，这两种模板都可以完全自定义。默认使用经典的蓝色风格模板（样式来源未知）。

默认被@通知邮件内容模板如下：

```html
<div style="border-top:2px solid #12ADDB;box-shadow:0 1px 3px #AAAAAA;line-height:180%;padding:0 15px 12px;margin:50px auto;font-size:12px;"><h2 style="border-bottom:1px solid #DDD;font-size:14px;font-weight:normal;padding:13px 0 10px 8px;">您在<a style="text-decoration:none;color: #12ADDB;" href="${SITE_URL}" target="_blank">            ${SITE_NAME}</a>上的评论有了新的回复</h2> ${PARENT_NICK} 同学，您曾发表评论：<div style="padding:0 12px 0 12px;margin-top:18px"><div style="background-color: #f5f5f5;padding: 10px 15px;margin:18px 0;word-wrap:break-word;">            ${PARENT_COMMENT}</div><p><strong>${NICK}</strong>回复说：</p><div style="background-color: #f5f5f5;padding: 10px 15px;margin:18px 0;word-wrap:break-word;"> ${COMMENT}</div><p>您可以点击<a style="text-decoration:none; color:#12addb" href="${POST_URL}" target="_blank">查看回复的完整內容</a>，欢迎再次光临<a style="text-decoration:none; color:#12addb" href="${SITE_URL}" target="_blank">${SITE_NAME}</a>。<br></p></div></div>

```

效果如下图：

![mail-blue-template](https://cloud.panjunwen.com/2018/09/wei-ming-ming.png)

@通知模板中的可用变量如下（注，这是邮件模板变量，是指嵌入到HTML邮件模板中的变量，请勿与云引擎环境变量混淆）：

| 模板变量 | 说明 |
| --- | --- |
| SITE_NAME | 博客名称 |
| SITE_URL | 博客首页地址 |
| POST_URL | 文章地址（完整路径） |
| PARENT_NICK | 收件人昵称（被@者，父级评论人） |
| PARENT_COMMENT | 父级评论内容 |
| NICK | 新评论者昵称 |
| COMMENT | 新评论内容 |

默认博主通知邮件内容模板如下：

```html
<div style="border-top:2px solid #12ADDB;box-shadow:0 1px 3px #AAAAAA;line-height:180%;padding:0 15px 12px;margin:50px auto;font-size:12px;"><h2 style="border-bottom:1px solid #DDD;font-size:14px;font-weight:normal;padding:13px 0 10px 8px;">您在<a style="text-decoration:none;color: #12ADDB;" href="${SITE_URL}" target="_blank">${SITE_NAME}</a>上的文章有了新的评论</h2><p><strong>${NICK}</strong>回复说：</p><div style="background-color: #f5f5f5;padding: 10px 15px;margin:18px 0;word-wrap:break-word;"> ${COMMENT}</div><p>您可以点击<a style="text-decoration:none; color:#12addb" href="${POST_URL}" target="_blank">查看回复的完整內容</a><br></p></div></div>

```

博主通知邮件模板中的可用变量与@通知中的基本一致，**`PARENT_NICK` 和 `PARENT_COMMENT` 变量不再可用。**

这里还提供一个彩虹风格的@通知邮件模板代码：

```html
<div style="border-radius: 10px 10px 10px 10px;font-size:13px;    color: #555555;width: 666px;font-family:'Century Gothic','Trebuchet MS','Hiragino Sans GB',微软雅黑,'Microsoft Yahei',Tahoma,Helvetica,Arial,'SimSun',sans-serif;margin:50px auto;border:1px solid #eee;max-width:100%;background: #ffffff repeating-linear-gradient(-45deg,#fff,#fff 1.125rem,transparent 1.125rem,transparent 2.25rem);box-shadow: 0 1px 5px rgba(0, 0, 0, 0.15);"><div style="width:100%;background:#49BDAD;color:#ffffff;border-radius: 10px 10px 0 0;background-image: -moz-linear-gradient(0deg, rgb(67, 198, 184), rgb(255, 209, 244));background-image: -webkit-linear-gradient(0deg, rgb(67, 198, 184), rgb(255, 209, 244));height: 66px;"><p style="font-size:15px;word-break:break-all;padding: 23px 32px;margin:0;background-color: hsla(0,0%,100%,.4);border-radius: 10px 10px 0 0;">您在<a style="text-decoration:none;color: #ffffff;" href="${SITE_URL}"> ${SITE_NAME}</a>上的留言有新回复啦！</p></div><div style="margin:40px auto;width:90%"><p>${PARENT_NICK} 同学，您曾在文章上发表评论：</p><div style="background: #fafafa repeating-linear-gradient(-45deg,#fff,#fff 1.125rem,transparent 1.125rem,transparent 2.25rem);box-shadow: 0 2px 5px rgba(0, 0, 0, 0.15);margin:20px 0px;padding:15px;border-radius:5px;font-size:14px;color:#555555;">${PARENT_COMMENT}</div><p>${NICK} 给您的回复如下：</p><div style="background: #fafafa repeating-linear-gradient(-45deg,#fff,#fff 1.125rem,transparent 1.125rem,transparent 2.25rem);box-shadow: 0 2px 5px rgba(0, 0, 0, 0.15);margin:20px 0px;padding:15px;border-radius:5px;font-size:14px;color:#555555;">${COMMENT}</div><p>您可以点击<a style="text-decoration:none; color:#12addb" href="${POST_URL}#comments">查看回复的完整內容</a>，欢迎再次光临<a style="text-decoration:none; color:#12addb"                href="${SITE_URL}"> ${SITE_NAME}</a>。</p><style type="text/css">a:link{text-decoration:none}a:visited{text-decoration:none}a:hover{text-decoration:none}a:active{text-decoration:none}</style></div></div>

```

效果如图：

![彩虹模板](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-5-17-21.png)

### 垃圾评论检测

> Akismet (Automattic Kismet)是应用广泛的一个垃圾留言过滤系统，其作者是大名鼎鼎的WordPress 创始人 Matt Mullenweg，Akismet也是WordPress默认安装的插件，其使用非常广泛，设计目标便是帮助博客网站来过滤留言Spam。有了Akismet之后，基本上不用担心垃圾留言的烦恼了。
> 启用Akismet后，当博客再收到留言会自动将其提交到Akismet并与Akismet上的黑名单进行比对，如果名列该黑名单中，则该条留言会被标记为垃圾评论且不会发布。

如果还没有Akismet Key，你可以去 [AKISMET FOR DEVELOPERS 免费申请一个](https://akismet.com/development/)；
**当AKISMET_KEY设为MANUAL_REVIEW时，开启人工审核模式；**
如果你不需要反垃圾评论，Akismet Key 环境变量可以忽略。

**为了实现较为精准的垃圾评论识别，采集的判据除了评论内容、邮件地址和网站地址外，还包括评论者的IP地址、浏览器信息等，但仅在云引擎后台使用这些数据，确保隐私和安全。**

**如果使用了本站最新的Valine和Valine Admin，并设置了Akismet Key，可以有效地拦截垃圾评论。被标为垃圾的评论可以在管理页面取消标注。**

| 环境变量 | 示例 | 说明 |
| --- | --- | --- |
| AKISMET_KEY | xxxxxxxxxxxx | [可选]Akismet Key 用于垃圾评论检测 |

### 防止云引擎休眠

关于自动休眠的官方说法：[点击查看](https://leancloud.cn/docs/leanengine_plan.html#hash633315134)

目前最新版的 Valine Admin 已经可以实现自唤醒，即在 LeanCloud 云引擎中定时请求 Web 应用地址防止休眠。对于夜间休眠期漏发的邮件通知，自动在次日早上补发。**务必确保配置中设置了ADMIN_URL环境变量，并在第5步添加了两个云函数定时任务。**

### Troubleshooting

*   部署失败，请在评论中附图，或去Github发起Issue

*   邮件发送失败，确保环境变量都没问题后，重启云引擎

    ![重启云引擎](https://cloud.panjunwen.com/2018/09/ping-mu-kuai-zhao-2018-09-15-xia-wu-5-22-56.png)

*   博主通知模板中不要出现`PARENT*`相关参数（请勿混用模板）

*   点击邮件中的链接跳转至相应评论，这一细节实现需要一点额外的代码：

```javascript
<script>
    if(window.location.hash){
        var checkExist = setInterval(function() {
           if ($(window.location.hash).length) {
              $('html, body').animate({scrollTop: $(window.location.hash).offset().top-90}, 1000);
              clearInterval(checkExist);
           }
        }, 100);
    }
</script>

```

*   自定义邮件服务器地址和端口信息，删除SMTP_SERVICE环境变量，新增以下变量：

| 变量 | 示例 | 说明 |
| --- | --- | --- |
| SMTP_HOST | smtp.qq.com | [可选]SMTP_SERVICE留空时，自定义SMTP服务器地址 |
| SMTP_PORT | 465 | [可选]SMTP_SERVICE留空时，自定义SMTP端口 |
| SMTP_SECURE | true | [可选]SMTP_SERVICE留空时填写 |

*   这是我的环境变量配置，绿色框中是邮箱服务相关配置，红色为邮件通知模板。

![ping-mu-kuai-zhao-2018-11-13-xia-wu-9-30-28](https://cloud.panjunwen.com/2018/11/ping-mu-kuai-zhao-2018-11-13-xia-wu-9-30-28.png)





---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>

