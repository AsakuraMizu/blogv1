---
title: PhiCreator 使用指南
date: 2020-11-27 14:36:29
tags:
  - PhiX
  - PhiCreator
  - HTML
categories:
  - Project
author: water_lift

---

PhiCreator 地址： [https://pc.solariar.tech/](https://pc.solariar.tech/)

我们强烈建议你在使用之前阅读 [PhiFormat 的说明文档](https://phi-x.github.io/PhiFormat/)。

<!-- more -->

# 界面内容

## 编辑器选项

![](Screenshot_20201127_144407.png)

目前只有语言一个选项。未来会添加更多的内容。

## 编辑器

![](Screenshot_20201127_150946.png)

PhiCreator的核心功能之一——谱面编辑。

### 偏移

~~其实是从offset翻译过来的~~即当前tick。

### 最大偏移 / 拖动条

拖动条是与偏移绑定的，改变任何一个都会对应改变另一个。

最大偏移用于限制拖动条的范围。

在 PhiCreator 的设计上，谱面并不需要与音乐文件绑定，所以我们无法根据音乐长度生成一个拖动条。因此，你需要手动指定拖动条的范围。

### 判定线列表

![](Screenshot_20201127_151014.png)

用于管理判定线。

单击“+添加”可以添加一条判定线，单击判定线名称右侧的“x”号或按住键盘上的ctrl键并单击该判定线可以删除这条判定线。

### 音符编辑

分为左右两部分。

#### 可视化编辑区（左）

![](Screenshot_20201127_151322.png)

灰白色区域即是编辑区域。支持的操作有：

+ 使用鼠标滚轮改变偏移
+ 按键盘上的1/2/3键（注意不是小键盘）添加click/flick/drag类型的音符
+ 按住键盘上的4键并移动鼠标以添加hold类型的音符

下边的拖动条用于缩放。

#### 详细信息编辑区（右）

![](Screenshot_20201127_155115.png)

### 事件编辑

![](Screenshot_20201127_155535.png)

## 预览

![](Screenshot_20201127_155720.png)

PhiCreator的另一个核心功能——谱面预览。

## 原始 JSON 数据

谱面文件的原始 JSON 数据。

注意谱面数据在各部分之间是共享的，所以当你编辑谱面时，这部分内容也会随之更新。



（未完成）