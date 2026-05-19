---
author: 一口草莓丸子
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU3MzQ5ODg2Ng==&mid=2247485168&idx=1&sn=c3bfbc592cef0c0da7a1969f129ee4b8&chksm=fdccef2723d2418ecd544b47a66eaf38329e38e666508c9d4581791563a3892ccc7a3cdc9289&mpshare=1&scene=1&srcid=0519U1XT7Ee1HyT6APoYZMNC&sharer_shareinfo=9a2b131a422b43e786441ed8277ff671&sharer_shareinfo_first=9a2b131a422b43e786441ed8277ff671#rd
saved: 2026-05-19 13:07:39
tags:
  - 笔记同步助手
id: c06f7131-f08a-4160-8eb5-d500c4650267
---

公众号名称：MOONST

作者名称：一口草莓丸子

发布时间：2026-05-15 17:00

原文链接：[https://api-docs.deepseek.com/zh-cn/quick\_start/pricing/](https://api-docs.deepseek.com/zh-cn/quick_start/pricing/)

![[笔记同步助手/images/a469affdd008ba5f66f1dbc841dd54d8_MD5.png]]

Introduction

## 前言

Obsidian 是一款**功能强大的知识库与笔记应用**，它将自己定位为“你的第二大脑”。基础功能完全免费，核心特点包括：本地储存、双向链接、图谱视图、插件生态丰富、响应速度快、可自定义布局···

![[笔记同步助手/images/712d9091a8f936cab054ee4ad576dcda_MD5.png]]

目前体验将近一个月感觉非常不错，这款笔记刚开始打开类似一个空房间，可以使用，不过有趣的是自己可以动手装修，做成自己喜欢适应的任何样子，所以初步搭建需要一点点的精力。

B站有关 Obsidian 上手使用的分享视频有许多，所以本篇是我个人**从0开始使用并搭建自己 Obsidian 笔记的过程记录**，分享对我有主要帮助的视频。目前笔记的框架很简单但实用，目录和操作窗口分栏与苹果备忘录类似，不过功能更加丰富，整体非常轻量。

![[笔记同步助手/images/b673d196707365037e442ad6c25d4a52_MD5.png]]

## PART 01

快速上手

从 0 到 1 的基础配置

有关非常重要的**笔记同步**放在最前面说明：Obsidian 笔记同步有官方和第三方，我主要在苹果设备上使用，所以文件直接拖放在 iCloud下。官方同步需要每月5 美金，其他同步方式可以 B 站了解。初始设置参考 B 站 「Blink的AI笔记」老师的视频:【Obsidian从0到1完整攻略 | 搞定同步+打通AI】

![[笔记同步助手/images/f0273b1599b99d826da0dbbe112a31f2_MD5.png]]

视频中有需要iPhone 先下载处理同步问题，实际可以直接在 Mac 端操作，只要找到文件夹拖放到 iCloud 就可以。以下是 MAC 安装及初步设置：

## 1\. 官网下载：https://obsidian.md/

## 2\. 更改语言，新建库，放在 iCloud 文件夹下。文件夹左键选择「保留下载」

## 3\. 来到初始界面，建议先新建两个文件夹，一个放附件，一个放模板，方便管理使用

4\. 点击设置。主要在「文件与浏览」、「核心插件」、「第三方插件」做基础功能配置（参考老师视频中设置）

有些功能可以通过快捷键调用，如果想简洁页面可在「外观」-「功能区」减掉不想显示的功能 icon

![[笔记同步助手/images/2961ddf90d561d3fa5738abb80291cfb_MD5.png]]

## PART 02

插件推荐：高效组合

以下是目前我仅留的五个插件：

## 1\. Style Setting 这个一般会配合其他美化插件一起使用

2\. **Notebook Navigator** 功能非常多，目前最喜欢的插件，主要使用功能：彩色文件夹；文件夹图标；日历结合模板，可以点击日期即可按照模板创建当天日记

## 3\. Obsidian web Clipper 这个是浏览器的插件，超级好用，必备

## 4\. Setting Search 设置内搜索，mini 实用小工具

## 5\. QuickAdd 目前使用场景 快速记录想法

以上三个具体使用讲解在 B 站「Dannie\_e」老师的视频：【第一次用Obsidian？先把这8个插件装好再说】

![[笔记同步助手/images/208c358598a5221a8f175c0c1cd37916_MD5.png]]

还有两款不错有趣的插件：

· Contribution Graph & Dataview

热力图统计，直观看产出，有 Github 外观可选

· Univer

可以直接在 Obsidian 里做表格文档，使Obsidian 更加全能，对于习惯 Notion 表格体验的人来说，会舒服很多。不过感觉占运行较大，所以没有使用

## PART 03

Obsidian+Claude

将 AI 能力接入笔记，是质的飞跃。**通过 Claudian，可以直接在 Obsidian 窗口中调用 AI 模型进行对话、总结或扩写****。**

Claude code 安装以及大模型配置参照「啊喵什么都会一点点」老师的这条视频：

Node.js官网：https://nodejs.org/en

![[笔记同步助手/images/603fa1cd41b7e21956e27e50f98b5cf3_MD5.png]]

![[笔记同步助手/images/8980826def93d60721dbfa77ddac1ded_MD5.png]]

老师讲解得很清晰，安装好之后终端出现小粉还挺可爱的 · V ·

![[笔记同步助手/images/b05272f7d254edba3a875584be0433d5_MD5.png]]

因为使用量没有很多，所以按量订阅的deepseek-v4-pro 模型，API 调用充值文档在文末「阅读原文」

![[笔记同步助手/images/4210ecfd1d606d08249030b0fe8006ec_MD5.gif]]

Claudian 插件安装是本篇笔记上面「Blink的AI笔记」老师视频后半部分分享的内容

![[笔记同步助手/images/f0273b1599b99d826da0dbbe112a31f2_MD5.png]]

到这里整个Obsidian 的初步搭建就差不多了，感觉笔记记多一些会更觉得好看好用，毕竟 Obsidian 特点是双链和关系图谱，接下来就是愉快记录啦 🥳

Afterword

## 后记

无论哪一种工具，记录本身只是整理、回顾和反思的载体，东西会越来越多，然后再慢慢筛减。

我们选择工具，工具也在反过来塑造我们的思维习惯。在使用 Obsidian 过程中，会让人思考，什么是真正有用的，什么和什么之间存在关联，这个过程非常有趣。目前阶段很喜欢这个笔记，所以仅作记录分享～

～

💜 💜 💜

···

\-END-

---

![[笔记同步助手/images/3bd268f3f63426c8a494081e737a99ec_MD5.jpg|cover_image]]

Original 一口草莓丸子 MOONST

Read more

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/ac27c21b_1779167258177?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU3MzQ5ODg2Ng%3D%3D%26mid%3D2247485168%26idx%3D1%26sn%3Dc3bfbc592cef0c0da7a1969f129ee4b8%26chksm%3Dfdccef2723d2418ecd544b47a66eaf38329e38e666508c9d4581791563a3892ccc7a3cdc9289%26mpshare%3D1%26scene%3D1%26srcid%3D0519U1XT7Ee1HyT6APoYZMNC%26sharer_shareinfo%3D9a2b131a422b43e786441ed8277ff671%26sharer_shareinfo_first%3D9a2b131a422b43e786441ed8277ff671%23rd&s=obsidian)