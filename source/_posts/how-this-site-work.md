---
title: 这个blog是怎么搭建起来的
date: 2019-10-03 20:04:10
tags:
  - blog
  - Hexo
categories:
  - Hexo
author:
  name: water_lift
  avatar: //actinoi.oss-cn-hongkong.aliyuncs.com/%E5%8F%8B%E9%93%BE/water_lift.JPG

---

本文将简单介绍本站(S-T's blog)的搭建过程。

<!--more-->

**前排提醒：阅读本文时或如有不适，请自行右上。**

# XXXX 一句话描述

> 把你的blog当作一个npm包。

# 1111 准备

0. ~~一台计算机~~
1. 一个已经在本地配置好的hexo博客（因为这的确不是本文的重点）
2. 域名
3. Github帐号
4. Netlify帐号（见0x0011 Netlify部署）

# 0000 思路

*water_lift上次装机的时候把blog的源文件搞丢了。。。于是就把整个文件夹备份到Github上了。。。*

简单的说就是把整个blog文件夹传到服务器上，服务器端自行生成并部署。

复杂些，将blog文件夹传到Github上，然后由Netlify在服务器端执行`hexo g`并将生成的`public`文件夹部署。

# 0001 本地配置

首先在blog根目录执行`git init`。这里注意到一个细节：在blog初始化（执行`hexo init`）时，hexo给出的模板其实已经包含了`.gitignore`文件，内容如下：

```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

这也提示了我们选择在服务器端部署blog的思路。

另外必须要提到的一点是，每次执行使用npm安装插件（如`hexo-helper-live2d`）时，必须有`--save`或`-S`选项。该选项的目的是将你安装的包记录在`package.json`文件中，以便在服务器端还原你的blog环境。

此外建议删除主题文件夹（`themes/xxx/`）下的`.git`文件夹。

# 0010 上传至Github

略。

# 0011 Netlify部署

[点此打开Netlify官网](https://www.netlify.com/)

首先你需要一个Netlify帐号。这里，我们可以直接选择使用Github登录/注册。

之后就请根据指引新建一个站点，并与你在0x0002中上传的仓库绑定。

在第三步“Build options, and deploy!”中，找到“Basic build settings”，然后在下面的“Build command”框内填写`hexo generate`（或`hexo g`），在“Publish directory”中填写`public/`。

站点创建成功后，Netlify将在服务器端搭建环境（安装node、yarn、hexo等以及**`package.json`中所列出的包**）。第一次部署将会花费较长的时间，此后由于环境已搭建好，部署时间将会大大减少。

此时Netlify会随机生成一个域名作为你blog的访问地址。如果你有自己的域名，那么你可以继续阅读接下来的步骤。

# 0100 域名绑定及SSL证书颁发

~~原则上讲完全可以直接按照Netlify给出的指引完成~~

Upd on 10.21：这一部分还没写完，netlify突然上不去了。。。先留个坑。。。