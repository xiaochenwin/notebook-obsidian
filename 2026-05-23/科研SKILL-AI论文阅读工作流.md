---
author: 三冬四夏
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzUxNTk5MzY2Ng==&mid=2247486885&idx=1&sn=5b0dccde6218362aebd7c205861213fb&chksm=f8a08e314b3cbca5f8721ac4741ea1e3201f87be71b72edec47f0c94f6ae1e70578adb523769&mpshare=1&scene=1&srcid=0523VrZvUqO52wcKSO81lHbP&sharer_shareinfo=f93db269a2589d9f7e3c51caa94facb6&sharer_shareinfo_first=f93db269a2589d9f7e3c51caa94facb6#rd
saved: 2026-05-23 04:04:33
tags:
  - 笔记同步助手
id: 6f8d7915-2095-43fa-9220-466bb10f6982
---

公众号名称：且挨过三冬四夏的读博生涯

作者名称：三冬四夏

发布时间：2026-05-22 08:30

用 AI 打造你的私人文献助手：基于 Claude Code 的论文阅读工作流

![[笔记同步助手/images/7cb84ec2c5213f9583433af0c3c9c619_MD5.png]]

每天面对海量新论文，不知道该读哪篇？读完就忘，笔记散落各处？这篇文章分享我如何用Claude Code Skills 搭建一套自动化文献阅读工作流，本skill有借鉴网络上相关类型skill，并进行结合改进。从论文搜索、筛选评分、到深度分析和知识管理，一站式解决科研人的信息焦虑。

痛点：科研人的信息过载

做科研的人大概都有这样的体验：

●每天arXiv上新增数百篇论文，根本看不过来

●好不容易找到一篇相关的，读完发现质量一般

●读了确实好的论文，笔记东一块西一块，过段时间全忘了

●想找之前读过的某篇论文，翻遍文件夹找不到

●不同论文之间的关联全靠脑子记，时间一长就模糊了

这些问题本质上可以归结为三个环节的缺失：发现、消化、连接。

于是我花了些时间，基于 Claude Code 的 Skill 系统搭建了一套自动化工作流，把这三个环节串了起来。

方案：三个 Skill，一条工作流

整个工作流由三个 Claude Code Skill 组成，各司其职：

| 
## Skill

 | 

## 功能

 | 

## 触发方式

 |
| --- | --- | --- |
| start-my-day | 每日论文推荐 | /start-my-day |
| paper-analyze | 单篇深度分析 | /paper-analyze 2605.00860 |
| extract-paper-images | 论文图片提取 | 自动调用 |

它们之间的关系是这样的：

/start-my-day  
│  
├── 搜索论文（Semantic Scholar + arXiv）  
├── 多维评分筛选 Top 10  
├── 生成每日推荐笔记  
│  
└── Top 3 论文自动触发 ↓  
│  
├── extract-paper-images → 提取论文图片  
└── paper-analyze → 生成深度分析笔记

下面逐个介绍。

start-my-day：你的每日论文推荐官

每天早上在 Claude Code 里输入 /start-my-day，它会自动完成以下流程：

## 1\. 多源搜索

搜索不是简单地在arXiv上搜关键词，而是采用了三源互补的策略：

●Semantic Scholar（主）：按研究领域精准查询，覆盖面广，引用数据丰富

●arXiv（补）：关键词搜索补充预印本

●CNKI（辅）：中文期刊论文，通过浏览器自动化搜索

搜索范围覆盖最近30天的新论文 + 过去2年的高引论文，确保不遗漏重要工作。

## 2\. 多维评分

搜索结果可能有上百篇，怎么筛选？工作流采用了四维评分体系：

| 维度 | 
## 权重

 | 

## 说明

 |
| --- | --- | --- |
| 相关性 | 40% | 与你的研究兴趣匹配程度 |
| 新近性 | 20% | 越新越好 |
| 热门度 | 30% | 引用数、关注度 |
| 质量 | 10% | 从摘要推断的创新程度 |

最终按综合评分排序，保留 Top 10。

## 3\. 个性化配置

评分的"相关性"维度完全由你的研究兴趣配置决定。配置文件长这样：

research\_domains:  
\- name: "计算机视觉"  
keywords: \["marine heatwave", "fishery", "SST"\]  
priority: 1.0  
\- name: "海洋动力学"  
keywords: \["ocean dynamics", "subsurface temperature"\]  
priority: 0.8

你可以根据自己的研究方向自由定义领域、关键词和优先级。

## 4\. 生成推荐笔记

最终输出一份 Obsidian 格式的每日推荐笔记，包含：

●今日概览：总结当天论文的主要方向、研究趋势、阅读建议

●Top 3 论文：带图片、wikilink、详细贡献总结

●其余论文：一句话总结 + 核心贡献

效果大概是这样的：

\## 今日概览  
今日推荐的10篇论文主要聚焦于\*\*海洋次表层温度重建\*\*、  
\*\*AI气候模型评估\*\*和\*\*季节预测与可预报性\*\*等前沿方向。  
\- \*\*总体趋势\*\*：AI/深度学习方法在海洋和气候科学中的应用持续深化  
\- \*\*阅读建议\*\*：建议先阅读#1（3D温度重建，方法创新突出）  
和#2（AIMIP评估，领域里程碑）  
\---  
\### \[\[Loo 2026 - 3D Ocean Subsurface Temperature Reconstruction\]\]  
\- \*\*作者\*\*：Ming Shan Loo, Wengen Li, ...  
\- \*\*机构\*\*：同济大学  
\- \*\*链接\*\*：\[arXiv\](https://arxiv.org/abs/2605.00860)  
\*\*一句话总结\*\*：提出自适应时空聚类框架，通过垂直依赖聚类  
和时间动态聚类将海洋划分为一致性子区域，结合多种深度学习  
模型实现仅用表面观测重建3D次表层温度。  
!\[\[fig4.png|600\]\]

paper-analyze：深度分析，图文并茂

推荐笔记帮你筛选出值得读的论文，paper-analyze 则帮你真正"读透"一篇论文。

输入 /paper-analyze 2605.00860，它会：

## 1\. 下载论文 + 提取图片

自动从arXiv下载PDF和源码包，按三级优先级提取图片：

## 1\. arXiv源码包（最优）：从 figures/、pics/ 等目录直接获取作者准备的原始图片

## 2\. PDF内嵌图片（次选）：从PDF中提取独立的图片对象

## 3\. PDF页面裁剪（兜底）：对于纯TikZ绘制的论文，智能裁剪figure区域

## 2\. 生成结构化分析笔记

分析笔记包含以下模块：

核心信息 → 摘要翻译 → 研究背景与动机 → 方法概述  
→ 实验结果 → 深度分析 → 与相关论文对比 → 综合评价  

每个模块都不是简单复述，而是包含深度解读：

●方法概述：不仅描述方法是什么，还解释为什么这样设计

●深度分析：评估理论贡献、实际应用价值、局限性

●相关论文对比：自动关联已有笔记，建立论文间的知识网络

●综合评价：从创新性、技术质量、实验充分性、写作质量、实用性五个维度打分

## 3\. 图文并茂

笔记中嵌入论文的关键图片（架构图、实验结果图等），使用 Obsidian 的 wikilink 语法：

!\[\[fig4.png|600\]\]  
\> 图4：自适应时空聚类框架概览

这样在 Obsidian 中阅读时，图片直接内联显示，体验和读原文一样。

extract-paper-images：论文图片，一键提取

这个 Skill 通常被前两个 Skill 自动调用，但你也可以单独使用。

它的核心价值在于三级优先级提取策略：

为什么需要这个策略？因为直接从PDF提取图片会遇到很多问题：

●PDF里的logo、图标被当成图片提取出来

●很多论文的架构图是用TikZ代码画的，不是独立图片

●实验结果图可能是复杂的矢量渲染对象

所以优先从arXiv源码包获取作者准备的原始图片，质量最高、最准确。

知识管理：Obsidian + Dataview

整个工作流的输出都落在 Obsidian 里，利用 Obsidian 的生态实现知识管理：

笔记结构

Obsidian Vault/  
├── Daily\_paper/\# 每日推荐  
│├── 2026-05-19论文推荐.md  
│└── 2026-05-20论文推荐.md  
├── 论文笔记/\# 深度分析  
│├── 海洋动力学/  
││├── Loo 2026 - 自适应时空聚类3D海洋次表层温度重建.md  
││└── Henn 2026 - AIMIP Phase 1 AI天气气候模型评估.md  
│└── 人工智能在海洋的应用/  
│└── Li 2026 - 中国边缘海MHW时空预警框架.md  
└── 99\_System/Config/  
└── research\_interests.yaml\# 研究兴趣配置

自动关联

笔记之间通过 Obsidian 的 wikilink 自动关联：

●推荐笔记链接到深度分析笔记

●深度分析笔记之间互相引用（相关论文对比）

●关键词自动链接到已有笔记（如 BLIP → \[\[BLIP\]\]）

论文总表

用 Dataview 插件自动生成论文总表，按年份、期刊分类，无需手动维护：

TABLE authors AS "作者", journal AS "期刊", year AS "年份"  
FROM "论文笔记"  
WHERE type = "paper" OR status = "analyzed"  
SORT year DESC  

实际体验

说说我的使用体验。每天早上打开 Claude Code，输入 /start-my-day，大约5-10分钟后就能收到一份精选的论文推荐。Top 3 论文会自动生成深度分析笔记，包含完整的图片和结构化分析。

以前我每天要花1-2小时浏览arXiv邮件列表、筛选论文、做笔记。现在这个过程缩短到15分钟——快速浏览推荐笔记，挑感兴趣的深入阅读。

更重要的是，所有笔记都在 Obsidian 里，通过 wikilink 形成知识网络。几个月后回头看，我能清晰地看到自己读过的论文之间的关联，这是以前散乱的笔记做不到的。

技术实现

整个工作流基于 Claude Code 的 Skill 系统实现。每个 Skill 由一个 SKILL.md 文件定义工作流程，配合 Python 脚本处理数据密集型任务（API调用、评分计算、图片提取等）。

关键设计决策：

●Claude Code 作为编排层：大模型负责理解论文内容、生成分析、做判断

●Python 脚本处理确定性任务：API调用、数据解析、评分计算交给脚本，确保可靠性

●Obsidian 作为知识库：所有输出落在 Obsidian，利用其 wikilink 和 Dataview 生态

开源

这个工作流已经开源，欢迎试用和贡献：

GitHub: ​https://github.com/ProMonkey-LU/academic-reading-workflow

安装方式：

也可不使用下方命令，将链接发给ai工具安装。

\# 克隆仓库  
git clone https://github.com/ProMonkey-LU/academic-reading-workflow.git  
\# 复制到 Claude Code skills 目录  
cp -r academic-reading-workflow/start-my-day ～/.cc-switch/skills/  
cp -r academic-reading-workflow/paper-analyze ～/.cc-switch/skills/  
cp -r academic-reading-workflow/extract-paper-images ～/.cc-switch/skills/

然后配置你的研究兴趣：

\# 在 Obsidian Vault 中创建配置文件  
\# $OBSIDIAN\_VAULT\_PATH/99\_System/Config/research\_interests.yaml

写在最后

这个工作流的核心思路其实很简单：把重复性的文献筛选和管理交给AI，把深度阅读和思考留给自己。

AI不会替你读论文，但它可以帮你从信息洪流中筛出值得读的论文，帮你把读过的论文组织成可检索、可关联的知识网络。这样你就能把有限的精力集中在真正需要人类判断力的地方——理解、质疑、创新。

如果你也在为文献管理头疼，不妨试试这个工作流。有任何问题或建议，欢迎在 GitHub 上提 Issue。具体配置obsidian、zotero、claude code等可以查看相关教程。

本文由 Claude Code 辅助撰写，工作流代码完全开源。

---

![[笔记同步助手/images/d2c7820b84e597fe9ea2f6dbc6f2e411_MD5.jpg|cover_image]]

原创 三冬四夏 且挨过三冬四夏的读博生涯

内容含AI生成图片

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/1558bf43_1779480268012?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzUxNTk5MzY2Ng%3D%3D%26mid%3D2247486885%26idx%3D1%26sn%3D5b0dccde6218362aebd7c205861213fb%26chksm%3Df8a08e314b3cbca5f8721ac4741ea1e3201f87be71b72edec47f0c94f6ae1e70578adb523769%26mpshare%3D1%26scene%3D1%26srcid%3D0523VrZvUqO52wcKSO81lHbP%26sharer_shareinfo%3Df93db269a2589d9f7e3c51caa94facb6%26sharer_shareinfo_first%3Df93db269a2589d9f7e3c51caa94facb6%23rd&s=obsidian)