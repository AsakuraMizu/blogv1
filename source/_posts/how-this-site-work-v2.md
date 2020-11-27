---
title: 这个blog是怎么搭建起来的 - 第二版
date: 2020-01-28 11:58:23
tags:
  - blog
  - Hexo
categories:
  - Hexo
author: water_lift

---

接[上篇](/2019/how-this-site-work)，我找到了一个比Netlify更NB的东东：[now(ZEIT)](https://now.sh/)

**Upd on 2020.11.27: ZEIT已经改名为Vercel**

<!--more-->

# 简洁教程

如何注册ZEIT：略。

前几步的配置还是一样的，先把你的blog传到Github上。
登录ZEIT，然后！你只需要选择“New Project”，选择你在Github上的blog仓库，点击IMPORT，稍等片刻即可！！！

# 图片详解

![](Screenshot_20200128_120408.png)  
图一，选择页面右上角的New Project

![](Screenshot_20200128_120510.png)  
图二，选择New Project From Github

![](Screenshot_20200128_120545.png)  
图三，选择你的blog仓库，然后点击IMPORT

# 绑定域名

事实上，now.sh添加自定义域名也十分简洁。

![](Screenshot_20200128_120738.png)  
图四，选择Domains

![](Screenshot_20200128_120810.png)  
图五，输入你的域名，并点击Add

![](Screenshot_20200128_120857.png)  
图六，这时候它会报错，因为你的域名还没有添加解析。这里，他们推荐的方式是让你的域名使用他们的Nameserver，或者说让他们提供DNS解析服务。但我认为这样做是不妥的（Cloudflare多好用x），所以我采用了第一种方式，即图片中所示的“ANAME”。

![](Screenshot_20200128_120920.png)
图七，这里红圈圈起来的地方是有一个字符串的，这里我把它抹掉了；这时你只需要给你的域名添加两条解析记录：

1. 类型： `TXT`  名称： `_now`  内容：图中红圈位置的字符串
2. 类型： `ALIAS` / `ANAME` / `CNAME`  名称： 你要给你的blog绑定的域名  内容： `alias.zeit.co`
确定添加好后，你只需要等待新添加的解析记录生效，然后刷新一下页面。如果不出问题的话，你的域名就配置好了，并且自动颁发了https证书！如果还是报错的话，你可以试着删除（先点击“Edit”按钮，然后点击“Remove”）后重新添加。

## 总结

~~ZEIT牛逼！！！~~

