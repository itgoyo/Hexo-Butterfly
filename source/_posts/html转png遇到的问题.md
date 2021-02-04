---
title: html转png遇到的问题
toc: true
category: 编程相关
author: itgoyo
tags: Program
date: 2019-09-02 11:13:34
keywords:
description:
source_url:
---

&nbsp;&nbsp;今天想分享一篇文章到朋友圈，发现使用印象笔记分享的效果不是很好，需要进入群组，然后有的朋友可能是没有印象笔记的账号的，所以使用印象笔记分享具有很大胆局限性。然后就是用 YuWriter 弄好 md 文档然后导出 图片，然后发现导出图片只能发现导出当前页的一张图片，并且不是长图，文章内容显示不全，所以就导出 html，然后在线转成 png。
&nbsp;&nbsp;然后 google 了一下发现一个网站 https://pdfcrowd.com/#convert_by_upload ，导出是正常的，但是图片里面有很多水印显示很难看，所以就放弃了这个网站，于是就想到了之前的一个网站 https://convertio.co ，里面确实也有 html 转 png 的，但是我尝试了一下，发现转 png 之后，里面的内容是乱码的，然后本地发现本地打开 html 是正常的，但是放到 apache 服务器里就显示乱码，即便是使用 vscode 修改了 html 的文本编码也是没有解决问题，然后手动在 html head 加上`<head><meta charset="utf-8"></head>`，这样子再 apache 上面访问也是正常的，然后再次提交到 https://convertio.co ，发现还是出现乱码，于是上 Github 找到 YuWriter项目的 issues 里面查看导出 html 乱码的的问题，发现也有人出现相同的问题 https://github.com/ivarptr/yu-writer.site/issues/510 ，然后作者里面说可能是导出 html 的时候是用的 wordpress，然后发现确实是用的这个，后面改成了`Standard`,这样子本地导出就不会出现乱码了，但是在网上转格式的时候发现图片乱码没有了，但是内容丢失了很多，最终还是没有解决问题。
&nbsp;&nbsp;然后灵机一动，想到`Surfingkeys`里面有截长图的功能，但是必须在访问域名的基础上才有作用，打开本地的 html 是没有作用的，然后就在 apache 服务器面，打开网页然后使用快捷键`yG`截长图。

---
<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>

