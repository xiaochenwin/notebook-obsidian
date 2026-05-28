---
author: 六加一
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzg4NDg4Njk5MQ==&mid=2247484204&idx=1&sn=842fbeb6badd89a275c16abfcf92c955&chksm=ce6be4a56df86c8d39d69f81a1a3056429b440df4e91627934a0058f10dce8086880e7e7d6d4&mpshare=1&scene=1&srcid=0525c38hY9BbmVUB3AqPUXBi&sharer_shareinfo=9853d93ecaa1dce7ec0e250728262e9f&sharer_shareinfo_first=9853d93ecaa1dce7ec0e250728262e9f#rd
saved: 2026-05-25 19:03:35
tags:
  - 笔记同步助手
id: a64a8200-3dc1-45c6-8e60-90d979a655cd
---

公众号名称：左移

作者名称：六加一

发布时间：2026-05-24 19:27

# AI Coding最佳实践

_10 步标准化流程，让 AI 编程项目可维护、可追溯。_

---

前面我们用 **TRAE** 生成了一个 APP，优化了 **UI**，并利用**免费静态托管平台**进行发布体验。

[手把手教你用Trae：从零开始搭建一个 APP](https://mp.weixin.qq.com/s?__biz=Mzg4NDg4Njk5MQ==&mid=2247483893&idx=1&sn=7129ec2cb37bddfef6bc7e17a50eb4b8&scene=21#wechat_redirect)

[手把手教你用Trae：利用Google Stitch/Pencil搞定APP UI设计](https://mp.weixin.qq.com/s?__biz=Mzg4NDg4Njk5MQ==&mid=2247483966&idx=1&sn=588d3fb07be7cfbdaec4a23b861536af&scene=21#wechat_redirect)

[手把手教你用Trae：0成本免费部署APP教程（附源码）](https://mp.weixin.qq.com/s?__biz=Mzg4NDg4Njk5MQ==&mid=2247483997&idx=1&sn=30c9997fcfdd6b3fbe4a7dbe340fb906&scene=21#wechat_redirect)

---

## 📋 遗留问题

1​**数据的存储问题** — 手机本地存储 vs 云端存储

2​**发布到手机软件商店**

> 先聊一下这两个问题。

---

## 🔧 技术选型

前面预告了存储数据的技术选型：**SQLite / Supabase**

我们可以直接和 TRAE 说：  
\- `我要利用 SQLite 作为 APP 本地存储数据的数据库`  
\- `我要利用 Supabase 作为 APP 的数据存储工具`

**TRAE 会帮你下载安装并修改代码文件。**

---

## ⚠️ 但是这样做有个问题

> 🙋‍♂️ **Vibe Coding 一时爽，但一直 Vibe Coding 不会一直爽。**

和 TRAE 聊到最后，你会发现：  
这个小项目**越来越难改**，**越来越难维护。**

​

### 常见痛点

| 问题 | 说明 |
| --- | --- |
| **UI 微调难** | 和 AI 对话进行微调像抽盲盒 |
| **功能易被覆盖** | 费好大力气调整的功能，一句提示词全改乱 |
| **上下文丢失** | 时间久了，开发者忘了改了什么，AI 也不记得（**AI 上下文限制**） |

---

## ✅ 解决方案：清晰的开发流程

网上有很多 AI Coding 最佳实践：**配置 Rules、装 Skills 等等**

这些锦上添花的东西我们当然要！！！🎉

不过在这之前，其实最需要的是**一个清晰可靠的开发流程**。

比如，我是这样做的：

![[笔记同步助手/images/e18b7bd0c5d4c654ca248c09da634207_MD5.png]]

  

> 访问如下链接，可查看完整高清的 AI Coding流程图，推荐用电脑端打开。
> 
> https://u1z44gmqa-aicoding-el9vl0168.maozi.io/

  

**完善清晰的流程 → AI Coding 的不可控制性越来越低 → 项目变得越来越容易维护**

---

## 🚀 后续计划

我将利用这套流程，解决遗留的 **2 个问题**：

​

### 示例：本地存储 SQLite

**`确定需求 → AI 生成需求文档（因为纯后端改动，所以跳过 UI/UX 交互节点） → 生成技术文档 → 生成执行计划 → 开始 AI Coding → AI 自助测试 → 生成测试报告 → 运行程序 → 验收。`**

**这样调整时，AI 可以读取保留的文档：**  
\- 了解改动过什么  
\- 每一次 BUG 修复清晰可溯源  
\- 每一次版本迭代有记录  
\- **项目才能更好维护！**

---

## 🛠️ 进阶技巧

流程化之后，我们要在流程过程中加一些有助于提高效率的技巧：

​

### Rules + Skills + MCP + Plugins

之前有讲过这些概念，这里就不重复了。

[一文拆解Agent必备的Rules / MCP / Skills / Plugin架构](https://mp.weixin.qq.com/s?__biz=Mzg4NDg4Njk5MQ==&mid=2247484181&idx=1&sn=60bd97a785819bdd2662bfd768703353&scene=21#wechat_redirect)

---

## 📌 持续更新

关于 AI Coding 相关的最佳实践，后续将持续维护到这里：

> Welcome to LeftShift～
> 
> https://gitee.com/leftShift

---

![[笔记同步助手/images/98b3177508caa32474f1054318a9ff8e_MD5.jpg|cover_image]]

原创 六加一 左移

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/868cf8d9_1779707013779?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzg4NDg4Njk5MQ%3D%3D%26mid%3D2247484204%26idx%3D1%26sn%3D842fbeb6badd89a275c16abfcf92c955%26chksm%3Dce6be4a56df86c8d39d69f81a1a3056429b440df4e91627934a0058f10dce8086880e7e7d6d4%26mpshare%3D1%26scene%3D1%26srcid%3D0525c38hY9BbmVUB3AqPUXBi%26sharer_shareinfo%3D9853d93ecaa1dce7ec0e250728262e9f%26sharer_shareinfo_first%3D9853d93ecaa1dce7ec0e250728262e9f%23rd&s=obsidian)