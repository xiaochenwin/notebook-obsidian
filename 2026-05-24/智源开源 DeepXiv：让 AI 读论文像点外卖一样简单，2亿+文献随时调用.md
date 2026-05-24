---
author: 掘金
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk2NDMzMDY3OA==&mid=2247484092&idx=1&sn=5c7d1978f715d762c080e1c98121054f&chksm=c50d050fdf499439b1f2557a0082c881d54b6f8836684fb23513d28d13dc5b3fdc5d754ae251&mpshare=1&scene=1&srcid=0524fWrOLNbKLAdK2TQVnQEe&sharer_shareinfo=40fc105f55b84aa6b1e2ffbb48c579e0&sharer_shareinfo_first=40fc105f55b84aa6b1e2ffbb48c579e0#rd
saved: 2026-05-24 08:33:34
tags:
  - 笔记同步助手
id: 0cdf902d-8990-4fca-a7db-e0d3884d54d0
---

公众号名称：掘金GitHub

作者名称：掘金

发布时间：2026-04-09 07:04

  

## 01 科研智能体有一个基础瓶颈

大模型 Agent 发展到现在，自动化科研已经不是概念了——自动发现科学问题、生成研究计划、开展实验探究，全流程都在被 AI 重新塑造。

但有一个基础瓶颈始终没解决：**智能体怎么用科技文献？**

传统方式下，智能体要查论文，得先做一次网页搜索，解析返回的 HTML，找 PDF，再靠复杂的阅读工具从满是视觉化元素的论文里提取信息。这套基于搜索引擎和图形用户界面的基础设施，跟智能体的工作方式天然不匹配——效率低、效果差。

说白了：海量开放论文在那儿，但智能体根本没有一套顺手的"文献工具"。

![[笔记同步助手/images/9135738494a87f74c144c6b3eb567eab_MD5.png]]

DeepXiv 就是来解决这个问题的。

​

## 02 DeepXiv：让论文从"给人看"变成"给智能体用"

DeepXiv 由**智源研究院（BAAI）**联合高校与社区开发者共同研发，是一个面向智能体的科技文献综合性工具集。目标只有一个：把论文从"人类可读"升级为"智能体可用"。

它目前覆盖 ArXiv 和 PubMed Central（生物医学文献），目标是扩展到 2 亿篇以上开放论文。

核心提供三大能力。

​

## 03 三个核心能力

### 一、数据接入：低预算、高效率的信息消费

DeepXiv 直接输出 JSON 或 Markdown，智能体不需要从 PDF 或 HTML 里艰难扒信息。

更重要的是，它把信息消费分层：

​

```
search "agent memory"   → 先找候选论文
--brief                      → 极低成本判断论文价值
--head                       → 掌握全文结构
--section "Experiments"      → 只读最有价值的部分
```

这带来一个本质变化：智能体不是一开始就把整篇论文全读完，而是先快速判断是否值得投入更多上下文预算，最后只展开真正关键的部分。

返回的内容是解析好的 Markdown 或 JSON，智能体阅读无压力：

![[笔记同步助手/images/694c7a2f155f5d02235ab617a479a0ff_MD5.png]]

### 二、一站式能力集成：不只是检索，更是帮智能体做事

DeepXiv 自建专属论文搜索引擎，围绕文献直接提供信息提取与理解、热点追踪、深度调研等能力。

一个典型的热点追踪流程：

​

```
deepxiv trending --days 7 --limit 30 --json   # 抓近期热点论文池
deepxiv paper 2603.28767 --brief               # 快速预览论文要点
deepxiv paper 2603.28767 --popularity           # 查看传播热度信号
```

先抓热榜，再预览单篇，最后补上社交媒体热度，智能体就可以继续完成摘要、筛选、排序与生成周报。

内置的深度调研 Agent 还可以直接回答"过去三年关于 Agent Memory 的代表性工作有哪些？"这类问题，不需要自己手动拼接每步调用。

### 三、多种接入形式：从智能体到开发者的全场景

DeepXiv 并不将自己限定为单点工具，而是提供多层接入形态：

-   • **CLI** 是核心，全部能力通过命令行暴露，支持脚本编排复杂工作流
    
-   • **MCP 接入**：嵌入 Claude Desktop 等智能体开发框架，让文献利用成为标准工具
    
-   • **Python SDK**：满足高度定制化的科研智能体集成需求
    

更关键的是，基于 DeepXiv 可以快速封装出一批定制化 Skills——每周自动追踪某个方向的新论文、批量抽取实验结果、生成 baseline 表格。

​

## 04 实战演示：让 AI 整理一个月内的 Agent Memory 论文

最能体现 DeepXiv 价值的，是看它如何把能力串起来完成一个真实任务。

典型需求：帮我整理最近 1 个月 agent memory 相关 paper，看看都在什么数据集上跑的，效果如何，有没有开源。

没有 DeepXiv，这通常意味着来回切网页、翻 PDF、复制粘贴、人工整理成表格。

有了 DeepXiv，这件事被拆解成几个非常自然的动作：

**第一步：按主题搜索候选论文**

智能体会围绕主题做多个近义搜索，而不是只押宝一个 query——先尽可能召回足够多的候选论文，再在后续步骤里逐步收缩范围。

![[笔记同步助手/images/acb90c801487a54878188c0798e721bd_MD5.png]]

**第二步：用 --brief 做低成本筛选**

没必要一上来就整篇通读。--brief 会先提取标题、时间、TL;DR、关键词、GitHub 链接等最关键信息，智能体用极低 token 成本完成第一轮判断。

**第三步：用 --head 看结构，再只读关键章节**

筛出真正相关的论文后，先看结构，再定点读取 Experiments 或 Results 部分。

![[笔记同步助手/images/54db823555cbfe115daf1f98170a9619_MD5.png]]

**第四步：自动落成 Markdown baseline 表**

当论文、数据集、指标、分数和开源状态都被提取出来后，直接整理成一份可交付的 markdown 表格——可以继续改写成调研文档、slides、周报，或者作为后续项目的 baseline 起点。

![[笔记同步助手/images/6dbace2bd5c3a502951298d2fcc3e96c_MD5.png]]

这个流程说明了一件事：DeepXiv 服务的不是一次性问答，而是一个可以持续复用的研究资产。

​

## 05 项目现状

目前 v0.2.4，Python 100%，已有 82 Stars。支持 MCP 接入、Python SDK、内置深度调研 Agent。

安装方式：

​

```
pip install "deepxiv-sdk[all]"    # 完整安装（含 MCP + Agent）
deepxiv agent config               # 配置 API key
deepxiv agent query "What are the latest papers about agent memory?" --verbose
```

## 写在最后

DeepXiv 想解决的核心问题很清楚：不是把论文"搬上命令行"，而是把论文真正变成智能体可以调用、筛选、阅读、分析、交付的一等对象。

传统论文网站服务的是"人类点开页面然后自己读"。DeepXiv 服务的则是"智能体围绕科研任务主动调用文献能力并完成交付"。

2 亿篇开放论文，智源已经搭好了底座。接下来看开发者怎么用它了。

GitHub：https://github.com/DeepXiv/deepxiv\_sdk

---

![[笔记同步助手/images/52490c820a9b4c2f6a4105dbf3da9eed_MD5.jpg|cover_image]]

Original 掘金 掘金GitHub

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/cea990d1_1779582812574?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk2NDMzMDY3OA%3D%3D%26mid%3D2247484092%26idx%3D1%26sn%3D5c7d1978f715d762c080e1c98121054f%26chksm%3Dc50d050fdf499439b1f2557a0082c881d54b6f8836684fb23513d28d13dc5b3fdc5d754ae251%26mpshare%3D1%26scene%3D1%26srcid%3D0524fWrOLNbKLAdK2TQVnQEe%26sharer_shareinfo%3D40fc105f55b84aa6b1e2ffbb48c579e0%26sharer_shareinfo_first%3D40fc105f55b84aa6b1e2ffbb48c579e0%23rd&s=obsidian)