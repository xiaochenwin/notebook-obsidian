---
author: 奔跑的蜗牛人
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzYzNzU1OTExOQ==&mid=2247485734&idx=1&sn=fb946dfb1cd1b1d633ec0966e9fe19a1&chksm=f1c99e46229249ecd32d4ff356cdcb1bf750bcb005daa581353dafffaa3dff3eabe44d1469e3&mpshare=1&scene=1&srcid=0520UiYHg9gpJMdal9TsagAF&sharer_shareinfo=f996bc26cef76d8c7699bf00de687b59&sharer_shareinfo_first=f996bc26cef76d8c7699bf00de687b59#rd
saved: 2026-05-20 07:22:10
tags:
  - 笔记同步助手
id: fb23c59f-70de-4307-b02d-ae89fa3139c7
---

公众号名称：技术野望社

作者名称：奔跑的蜗牛人

发布时间：2026-05-20 06:18

# 凌晨三点的GPU轰鸣声

凌晨三点,你的 GPU 集群还在轰鸣。不是你在跑实验,而是 Claude Code 正在自动实现一个新的想法。与此同时,GPT-5.5 正在审阅昨天生成的论文草稿,标记出三个逻辑漏洞和两处引用问题。第二天早上,你会发现论文评分从 5/10 提升到了 8.5/10,20 多个 GPU 实验已经完成,叙事结构被彻底重写。

这不是科幻。这是 ARIS (Auto Research in Sleep),一个让 AI 在你睡觉时做科研的开源系统。

![](https://relay-1.bijitongbu.site/p/162ffb7bbff862a264539174fc28f55a.png)

## 单模型自我博弈:一个美丽的陷阱

很多研究者尝试过用同一个 AI 模型既当执行者又当审稿人。这在技术上可行,但会陷入局部最优。同一个模型审自己的输出会产生盲区,就像 stochastic bandit 问题中噪声是可预测的一样。真正有效的审稿需要 adversarial bandit 的对抗性,审稿者必须主动探测执行者未预料的弱点。

ARIS 的核心洞见是:两个是打破自我博弈盲区的最小配置。Claude Code 负责快速丝滑的执行,Codex (GPT-5.5 xhigh) 负责严谨深入的审稿。两者速度乘以严谨的互补特性,比单模型自我对话效果更好。

![](https://relay-1.bijitongbu.site/p/f96930e5302d519283f0b60b39dff0bd.png)

## 拆解74个Skill:科研流水线的工程美学

ARIS 不是一个平台,而是一套方法论。整个系统由 74 个可组合的 Skill 组成,每个 Skill 就是一个 Markdown 文件,任何 LLM 都能读懂。这意味着你可以把 ARIS 带到任何地方:Claude Code、Codex CLI、Cursor、Trae、GitHub Copilot CLI,甚至你自己的 Agent。

![](https://relay-1.bijitongbu.site/p/aec61cc414966e3775d0d2caf06a266b.png)

系统架构分为四个核心 Workflow:

**Workflow 1: Idea Discovery** 从模糊的研究方向到经过 GPU 验证的提案。系统会检索多源文献 (Zotero、arXiv、Semantic Scholar、DeepXiv),生成 8-12 个具体想法,进行新颖性检查,然后在 GPU 上跑 1-2 小时的 pilot 实验。真正的信号来自 GPU,而不是 LLM 的意见。

**Workflow 1.5: Experiment Bridge** 关闭从论文计划到运行代码的鸿沟。Claude Code 读取实验计划,实现完整的实验脚本,然后 GPT-5.4 在部署前进行跨模型代码审查。这个审查能捕获约 80% 的 bug,避免浪费 8-GPU-小时的运行时间。

**Workflow 2: Auto Review Loop** 这是 ARIS 最被引用的工作流。系统会自主迭代:审稿、修复、重新运行实验、重新审稿,直到评分达到阈值或达到最大轮数。你可以在截止日期前一晚启动它,第二天早上拿到打磨好的论文。真实案例:5/10 提升到 8.5/10,跨越 3 轮迭代。

**Workflow 3: Paper Writing** 从叙事报告到投稿就绪的 PDF。系统构建 claims-evidence 矩阵,自动生成图表和 LaTeX,然后进行两轮内容审查和一轮格式检查。

![](https://relay-1.bijitongbu.site/p/5985b70de093db9f5066c92c087055cd.png)

## 五层审计链:工程师的安全底线

ARIS 最独特的设计是它的五层跨模型审计链。每一层都由不同的 Skill 调用独立的 Codex 线程进行审查:

​

-   •​**Experiment Audit**: 评估代码是否诚实?没有伪造的 ground truth,没有自归一化的分数,没有虚假结果。
-   •​**Result-to-Claim**: 结果是否科学支持声明?
-   •​**Paper-Claim Audit**: 论文是否如实报告数字?
-   •​**Citation Audit**: 每个引用是否有效?存在性、元数据、上下文适当性。
-   •​**Kill-Argument**: 双线对抗审查,一个线程写最强的拒稿备忘录,另一个线程逐点辩护。

在 submission 模式下,如果任何一层返回非 PASS 状态,系统将阻止最终报告生成。这是真正的工程严谨性,不是提示工程的花招。

## 零依赖设计:为什么Markdown胜过Docker

ARIS 是极致轻量的。整个系统就是纯 Markdown 文件,没有框架要学,没有数据库要维护,没有 Docker 要配置,没有守护进程要看管。每个 Skill 就是一个 SKILL.md,任何 LLM 都能读懂。

这种设计有几个深层含义:

第一,可移植性。你可以把 ARIS 带到任何支持 LLM 的平台上。今天用 Claude Code,明天用 Codex CLI,后天用 Cursor,工作流照样跑。

第二,可审计性。每个中间产物都是纯文本,你可以随时检查系统在做什么。没有黑盒,没有隐藏的 prompt。

第三,可演化性。系统包含一个 Meta-Optimize Workflow,可以分析使用日志并提议 SKILL.md 的改进。ARIS 会自己进化。

## 真实战绩:从4分到8.5分的逆袭

ARIS 已经被用于真实的 ICLR、NeurIPS 投稿。一个典型的 overnight run 会产生 20 多个 GPU 实验,论文评分从 4/10 提升到 8.5/10。系统在 Hugging Face Daily Paper 获得 #1,被 PaperWeekly 报道,入选 awesome-agent-skills。

项目已经支持多种模型组合:Claude × GPT、Kimi × LongCat、DeepSeek × MiniMax。你不需要 OpenAI API,甚至可以通过 ModelScope 免费接入。

## 架构师的三个启示

ARIS 的设计给了我们几个关于 AI 系统架构的启示:

**对抗性优于自举性**。两个不同家族的模型互相审查,比单模型自我迭代效果更好。这不是计算资源的浪费,而是质量的保障。

**显式状态优于隐式上下文**。ARIS 把研究状态写入 Markdown 文件 (IDEA\_REPORT.md、EXPERIMENT\_LOG.md、REVIEW\_STATE.json),而不是依赖 LLM 的上下文窗口。这让系统可以跨会话恢复,可以人工审计,可以被其他工具处理。

**约束优于自由**。五层审计链、最大 4 轮迭代、超过 4 GPU 小时的实验必须人工批准,这些约束看似限制了系统,实际上保证了系统的可靠性和安全性。

## 未来已来:科研自动化的新范式

ARIS 不是要让研究者失业,而是要把研究者从繁琐的执行工作中解放出来,让他们专注于真正需要人类判断的部分:提出好的问题、识别深刻的洞见、做出战略性的决策。

当 AI 可以帮你跑实验、写代码、审稿、改论文时,你的时间就可以用来思考更重要的事情。这才是科研自动化的真正意义。

项目地址: github.com/wanshuiyin/Auto-claude-code-research-in-sleep

---

![cover_image](https://mmbiz.qpic.cn/sz_mmbiz_jpg/hyh2h4kSnERrPicrALOAgicgUOjCeHu1yaDE5aqPBibHzEmlMS6vrbqj64D3Zm9UIGCs4cWpxpFxCzPyZ0Rn93ibRvpPMjia1aVpneByBSVxkwLU/0?wx_fmt=jpeg)

Original 奔跑的蜗牛人 技术野望社

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/7c6ecff9_1779232929202?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzYzNzU1OTExOQ%3D%3D%26mid%3D2247485734%26idx%3D1%26sn%3Dfb946dfb1cd1b1d633ec0966e9fe19a1%26chksm%3Df1c99e46229249ecd32d4ff356cdcb1bf750bcb005daa581353dafffaa3dff3eabe44d1469e3%26mpshare%3D1%26scene%3D1%26srcid%3D0520UiYHg9gpJMdal9TsagAF%26sharer_shareinfo%3Df996bc26cef76d8c7699bf00de687b59%26sharer_shareinfo_first%3Df996bc26cef76d8c7699bf00de687b59%23rd&s=obsidian)