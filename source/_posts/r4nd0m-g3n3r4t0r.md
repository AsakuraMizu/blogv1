---
title: 中 奖 名 单 生 成 器
date: 2020-01-11 21:22:35
tags:
  - HTML
categories:
  - Project
author: water_lift

---

项目地址：[https://github.com/water-lift/random](https://github.com/water-lift/random)  
预览 & 使用（感谢now）：[https://rand.solariar.tech/](https://rand.solariar.tech/)  
UI设计：[MDUI](https://www.mdui.org/)  
动画：[http://www.100sucai.com/online/6691/](http://www.100sucai.com/online/6691/)  
<!--more-->

# 笔记

2019年年底的时候，各班要开元旦联欢会嘛，我们隔壁班有个~~小姐姐~~同学想要找一款“随机抽取软件”，能够支持**每次都抽到同一个人**。

当时她只是告诉了我们班里学信息奥赛的Sweetness同学，让她帮忙找一找，后来Sweetness告诉了我。我想：这是什么奇葩要求？

觉得这种东西网上应该找不到，我决定自己写一个。

---

一开始的时候，我遇到的最大的问题是：用什么语言写呢？以怎样的方式交付使用呢？肯定不能到时候给人家一个黑框框（指控制台界面）吧！

因为当时在学React嘛，我就想拿nodejs+React写来着。写着写着发现：好像这玩意用纯HTML+JavaScript就行吧？

---

另一个问题是，能不能设计出一个高端大气上档次的动画来。晚自习没事干的时候也YY了几个，但是转而一想，意识到：我肯定写不出来。

后来我在网上找了一段时间，找到了一个滚轮式的动画 [http://www.100sucai.com/online/6691/](http://www.100sucai.com/online/6691/)。虽然和我想象的不(qu)太(bie)一(hen)样(da)，但是时间紧迫，就这么用上了。

---

刚把动画准备好，又接到了新的要求：不能很明显地看出来是“黑箱操作”。

这好办，添加一个控制模式的“开关”不就好力！同时，还要把这个“开关”做的隐蔽一些。

于是我想到了一个很棒的解决方案：随机数种子。如果输入的种子是某个特定的数（实际的代码中是2020），那么固定抽到第一个；否则随机抽取。

# 构思

正如上文所述的那样，我们让用户输入抽取名单和一个随机数种子，然后判断如果随机数种子是2020，那么此后每次“随机”抽取都将抽到第一个，否则就拿这个数作为随机数种子。

# 问题

## 1. JavaScript并不能设置随机数种子

我先解释一下为什么要设置随机数种子。~~客户要求，~~整个过程要不能被很明显地看出来是“黑盒操作”（我的理解是在抽完第三次之前不被发现是设定好只抽某一个人），那么咱就得装的像一点儿。

然后我发现JavaScript并没有像c++那样的`srand`函数用来设置随机数种子。

WTF？

那只好自己写随机函数咯。实际代码中我使用了一个非常鬼畜的处理方式：

```javascript
Math.seed = seed;
Math.random = function() {
    Math.seed = Number('0.' + Math.cos(Math.seed).toString().substr(6)) * 1000;
    return Number('0.' + Math.sin(Math.seed).toString().substr(6));
}
```

简单地说就是先生成无理数，然后取小数点后的数位。

## 2. 这个动画只能支持从12个数中抽

简单来说，这个动画的核心是一个被分成12份的轮盘，且每一份的位置都是经过精确计算的。

这个问题倒还好，先生成一个12个数的序列不就好力。

## 3. 动画触发

当时我找到这个动画的时候，只是觉得效果很好，没有去管它是怎么实现的。后来我看了看，发现它只不过是用了一些css特效罢了。

大家知道，css样式是网页加载的时候触发的，可我现在的需求是需要每按一次按钮，就要触发一次动画。也就是说，我需要“重新播放css动画”。

常规思路，把元素的样式移除掉再重新添加回去。可玄学的是，我无论是用DOM还是jQuery，都无法达成目的。

最后在网上搜到了解决办法，十分玄学，我猜可能是通过“假装”更改了元素属性的方式让浏览器认为钙元素需要重新加载。

```javascript
r = document.getElementsByClassNmae("rotator")[0];
r.classList.remove("rotator");
void r.offsetWidth;
r.ckassList.add("rotator");
```

# 总结

~~给小姐姐写代码就是感觉不一样x~~