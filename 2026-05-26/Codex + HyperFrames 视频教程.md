---
author: AI工具接入手册
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzY5MTMyMzY5Ng==&mid=2247483688&idx=1&sn=fb7f2143ad681e799e0cd53560785fcc&chksm=f535e15a3ab67cff670a550505ce91b407dfa1c16cdb4654d66e03483deb13538abece44d558&mpshare=1&scene=1&srcid=0526tiObU57i1U51NLJBtGow&sharer_shareinfo=5b6a25ae572e68c261e4e0df29d65766&sharer_shareinfo_first=5b6a25ae572e68c261e4e0df29d65766#rd
saved: 2026-05-26 22:00:46
tags:
  - 笔记同步助手
id: 51086386-8456-4ddb-a6ed-81e6c88e9654
---

公众号名称：AI工具接入手册

作者名称：AI工具接入手册

发布时间：2026-05-23 22:02

![[笔记同步助手/images/2868ca45f4f0c32fd25cff2ee384a391_MD5.png]]

# 用 Codex 里的 HyperFrames 插件做 AI 视频：从提示词到成片的完整流程

如果你想做一个 AI 视频，不一定要从剪辑软件开始。

现在可以用 Codex 里的 HyperFrames 插件，把文案、图片、动画和视频渲染串起来。

这篇用最简单的方式讲一遍流程：先配置 GPT API，再用 Codex 插件生成视频项目，提示词让 ChatGPT 来写，图片用 image2 生成，最后交给 HyperFrames 渲染成视频。

> 一句话流程：GPT API 提供模型能力，ChatGPT 负责出提示词，image2 负责生成图片素材，Codex 里的 HyperFrames 插件负责把素材变成视频。

## 一、先准备这些东西

开始前准备 5 个东西：

1.  Codex App
    
2.  Codex 里的 HyperFrames 插件
    
3.  GPT API / API Token 中转入口
    
4.  ChatGPT
    
5.  image2 图片生成工具
    

如果你用的是 API Token 中转入口，先拿到：

-   Base URL
    
-   API Key
    
-   模型名称：比如 gpt-5.5 / gpt-5.5-pro
    

## 二、配置 GPT API

先把 API 配好，让 Codex 能正常调用模型。

你需要准备：

> Base URL
> 
> https://你的接口地址/v1
> 
> API Key
> 
> sk-xxxxxxxxxxxxxxxx
> 
> Model
> 
> gpt-5.5

配置成功后，先让 Codex 回答一个简单问题，确认接口能跑通。

> 建议先小额测试。视频生成会涉及文案、脚本、画面描述、代码生成和渲染检查，比普通聊天更消耗 token。

## 三、让 ChatGPT 生成视频提示词

不要一上来就让 HyperFrames 直接做视频。先用 ChatGPT 把视频创意整理清楚。

可以直接用这个提示词：

我想做一个 30 秒 AI 视频，主题是【这里写主题】。

请帮我输出：

## 1\. 视频标题

## 2\. 目标观众

## 3\. 3-5 个分镜

## 4\. 每个分镜的画面描述

## 5\. 每个分镜的字幕

## 6\. 适合 image2 生成图片的提示词

## 7\. 适合交给 HyperFrames 制作视频的总提示词

风格要求：简洁、科技感、适合公众号/短视频平台发布。

这样做的好处是：视频结构先清楚，后面生成图片和动画就不会乱。

## 四、用 image2 生成图片素材

拿到 ChatGPT 给的图片提示词后，丢给 image2 生成图片。

每个分镜至少生成 1 张图，如果质量不稳定，可以每个分镜生成 2-3 张备用。

图片建议统一风格：

-   同一画幅
    
-   同一色调
    
-   同一角色风格
    
-   同一光影方向
    
-   不要混用太多画风
    

如果视频偏科技教程，可以用深蓝、青绿、白色这类干净配色。不要让每张图风格差太远。

## 五、把素材交给 Codex 的 HyperFrames 插件

打开 Codex，启用 HyperFrames 插件，然后把前面准备好的内容交给它。

可以这样描述任务：

使用 HyperFrames 帮我制作一个 30 秒视频。

主题：【视频主题】

尺寸：16:9

风格：科技感、干净、适合公众号/短视频发布

素材：我会提供每个分镜的图片

要求：

## 1\. 按 3-5 个分镜组织

## 2\. 每个分镜有字幕

## 3\. 图片要有轻微缩放、平移或转场

## 4\. 结尾保留引导语：回复“接口”获取 GPT-5.5 测试入口

## 5\. 输出可预览、可渲染的视频项目

HyperFrames 会把这些内容变成 HTML 视频工程，再进行预览和渲染。

## 六、检查和导出视频

视频生成后，不要急着发布，先检查这几件事：

-   字幕有没有挡住主体
    
-   图片有没有拉伸变形
    
-   转场会不会太快
    
-   文字是否能看清
    
-   结尾引导是否自然
    
-   视频是否能正常渲染导出
    

如果画面太乱，就减少分镜和特效。教程类视频最重要的是清楚，不是炫。

## 七、一个最小可用模板

如果你不知道从哪里开始，可以直接套这个模板：

> **视频主题**
> 
> 用 30 秒讲清楚一个 AI 工具的使用方法。
> 
> ​**视频结构**
> 
> 开头 3 秒抛问题，中间 20 秒讲步骤，最后 7 秒给入口。
> 
> ​**画面素材**
> 
> 每个步骤一张图，统一科技感风格。
> 
> ​**结尾导流**
> 
> 想测试 GPT-5.5，回复「接口」获取接入教程。

## 八、我整理了一个测试入口

> **想用 GPT-5.5 跑 Codex 和 HyperFrames，可以回复关键词 接口**
> 
> 我这边整理了一个 API Token 中转入口，支持 GPT-5.5、GPT-5.5 Pro、Claude Opus 4.7 等模型。
> 
> 可以用于 Cursor、Dify、Cherry Studio、Claude Code，也可以配合 Codex 里的 HyperFrames 插件制作 AI 视频。
> 
> 新手建议先小额测试，确认接口能跑通后再继续使用。

> **关注我，后面继续发 AI 工具实战教程**
> 
> 想要 GPT-5.5 接口测试入口、HyperFrames 视频模板、Codex 插件配置教程，可以扫码关注。
> 
>   

>   
> 
> 关注后回复「接口」，获取接入说明。

## 九、最后总结

这套流程不复杂：

1.  配置 GPT API
    
2.  用 ChatGPT 写视频提示词
    
3.  用 image2 生成图片
    
4.  在 Codex 里调用 HyperFrames 插件
    
5.  预览并导出视频
    

真正影响成片质量的，不是工具越多越好，而是前面的脚本、分镜和图片风格要统一。

> 建议先做 15-30 秒短视频，跑通流程后再做更长视频。短视频更容易检查问题，也更适合新手练手。

---

![[笔记同步助手/images/6cb976c5d6fc47d95a1dd36719f60edd_MD5.jpg|cover_image]]

原创 AI工具接入手册 AI工具接入手册

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/103ab9f6_1779804042776?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzY5MTMyMzY5Ng%3D%3D%26mid%3D2247483688%26idx%3D1%26sn%3Dfb7f2143ad681e799e0cd53560785fcc%26chksm%3Df535e15a3ab67cff670a550505ce91b407dfa1c16cdb4654d66e03483deb13538abece44d558%26mpshare%3D1%26scene%3D1%26srcid%3D0526tiObU57i1U51NLJBtGow%26sharer_shareinfo%3D5b6a25ae572e68c261e4e0df29d65766%26sharer_shareinfo_first%3D5b6a25ae572e68c261e4e0df29d65766%23rd&s=obsidian)