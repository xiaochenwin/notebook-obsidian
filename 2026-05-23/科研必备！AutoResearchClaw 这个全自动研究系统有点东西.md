---
author: NeoAgent
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzY5MTI1OTE0Ng==&mid=2247483991&idx=1&sn=d7b154e53df63cbd4b15195fa66f2c9a&chksm=f56054b4fd6c5f394717cf0c8537322f6ba2c927e648e886817b992b1fa2070d6b2c4532cc9b&mpshare=1&scene=1&srcid=0523h0M4iZXZbBkG636kaBtW&sharer_shareinfo=0e42b3c3a2ef8e4298b8100ea936d503&sharer_shareinfo_first=0e42b3c3a2ef8e4298b8100ea936d503#rd
saved: 2026-05-23 20:25:15
tags:
  - 笔记同步助手
id: 54f482df-7ac2-4a37-911f-0e0a17ddb3ab
---

公众号名称：NeoAgent

作者名称：NeoAgent

发布时间：2026-05-20 11:30

  

![[笔记同步助手/images/b71e835b5f2aa8facaf14f3ff29a7125_MD5.png]]

> 最近 AI 圈被 Karpathy 的 autoresearch 刷屏了，大家还在感叹实验循环自动化时，一群狠人直接把“整个实验室”给搬进了代码里。AutoResearchClaw 不只是写写草稿，它能自己查文献、定假设、跑实验、改 Bug，最后吐出一整套可以直接投会的论文包。

---

### 摘要

由 aiming-lab 开源的全自动科研系统 **AutoResearchClaw (ARC)**。该项目在 Karpathy 提出的自动化研究循环基础上，进一步实现了全链路工程化。其核心逻辑是将 AI 研究员的工作流拆解为 8 大阶段、23 个子阶段，通过多智能体协作、沙盒实验执行及四层文献验证机制，实现了从“一句话需求”到“完整会议论文”的自动化产出。项目解决了 LLM 研究中的引用幻觉、代码崩溃无法自愈、假设质量低下等痛点。实测显示，其输出包含 LaTeX 源码、验证过的 BibTeX 及可复现的实验结果，支持 NeurIPS、ICLR 等主流会议模板。

### 主要内容

1.  **全链路自动化流水线**：ARC 覆盖了从研究定界、文献发现到实验执行和论文撰写的全流程。引入了 `--auto-approve` 模式，允许智能体在无人干预下完成长达数日的科研任务。
    
2.  **硬核防翻车机制**：针对引用幻觉，设计了 arXiv + Semantic Scholar 的四层校验；针对实验失败，引入了具备 10 次迭代能力的“自愈+自我否定（PIVOT）”闭环。
    
3.  **多智能体对抗辩论**：通过 Hypothesis、Sanity、Killer 三个 Agent 的结构化辩论，强行拉高假设的逻辑强度和新颖性。
    
4.  **实验室“肌肉记忆”**：系统具备带时间衰减的自学习机制和 Sentinel 哨兵监控，能积累历史实验经验并实时预警数值异常。
    

---

## 别人在卷实验循环，这只“龙虾”直接卷掉了整个实验室

最近 AI 圈子里有个话题特别火：Andrej Karpathy 搞了个 autoresearch，把实验循环给自动化了，程序员们都在感叹“饭碗要丢”。结果话音刚落，GitHub 上就冒出一个叫 **AutoResearchClaw** (🦞) 的项目。

作者的口气很大：Karpathy 只是搞个循环，而我把**整个实验室都自动化**了。

简单来说，这是一个“会做研究”的龙虾系统。项目出自 aiming-lab，核心卖点极其硬核：你只要给它一个研究方向，它还你一篇会议论文。注意，这不是那种满嘴跑火车的 AI 写作，它是**文献真实、实验真跑、引用可核验**。全过程如果不加人工干预，它能自己跑完从查新到定稿的所有脏活累活。

![[笔记同步助手/images/62ccb4beaed4d2681b6dcdea920da2f6_MD5.jpg]]

### 01 它是怎么把流程跑通的？

AutoResearchClaw 的底层逻辑，是把一个苦哈哈的 AI 研究员的一天，拆解成了 **8 大阶段、23 个子阶段**。

它不只是调用一下 LLM 写代码，而是用一套多智能体流水线把每个环节都咬合住了。从最开始的“研究定界”出发，经过文献扫荡、知识合成，再进入实验设计与执行，最后分析结果并写成论文。

最骚的是它的交付产物：跑完之后，你的文件夹里会有 `paper.tex`、一堆带误差棒的实验图表、跑出来的 JSON 数据，甚至还有模拟同行评审的记录。你把 `deliverables/` 往 Overleaf 里一导，直接就能编译出 NeurIPS 风格的 PDF。要是你胆子大，加上 `--auto-approve` 参数，你就直接去喝咖啡吧，龙虾自己会在后台通宵达旦地干活。

### 02 文献幻觉？四层闸门直接物理隔绝

大家都知道，让 LLM 查文献，它最擅长的就是“一本正经地编造引用”。

为了对付这个顽疾，AutoResearchClaw 搞了一套四层验证机制：它会实时去 arXiv 和 Semantic Scholar 的 API 抓 50 多篇真实论文，然后对每一条引用跑四道关卡：

1.  **arXiv ID 强校验**；
    
2.  **DOI 在线查询**；
    
3.  **标题模糊匹配**；
    
4.  **LLM 相关性打分**。
    

只要有一道关过不了，这篇引用直接被踢出名单。最后生成的 BibTeX 文件里，每一条都是有名有姓、真实存在的“真文献”。这种剪枝逻辑虽然费 Token，但确实解决了学术诚信的红线问题。

![[笔记同步助手/images/264afedba872b67889f868ea11107a70_MD5.png]]

### 03 实验跑崩了？它会自己“看病”和“止损”

这是我觉得这个项目最性感的地方：**它真的去跑代码，而且会自己改 Bug。**

系统会在沙盒里执行生成的 Python 实验代码，能自动认领你的 NVIDIA 显卡或 Mac 的 MPS 加速。如果代码在凌晨三点跑崩了，它不会停下来等你。它会读取报错的 Traceback，丢给 LLM 分析，生成修复方案，然后重跑。这个过程最多迭代 10 轮。

如果跑出来的结果发现假设根本站不住脚怎么办？它会触发一个 **PIVOT 决策**。这意味着系统会自我否定，直接回退到最开始的假设生成阶段，换个方向重新开局。这种“自愈 + 自我否定”的闭环，比单纯只会写代码的工具强了不止一个档次。

### 04 三个智能体吵架：拒绝“平庸”的科研

在生成研究假设时，ARC 没让一个 Agent 自言自语，而是搞了三个 Agent 玩对抗：

-   **Hypothesis Agent**：激进派，脑洞大开，追求新颖。
    
-   **Sanity Agent**：保守派，专门找逻辑漏洞，看假设合不合常理。
    
-   **Killer Agent**：极端派，职责就是把假设往死里怼，找出能让这篇论文被拒的致命伤。
    

只有在这场“撕逼大战”中存活下来的假设，才有资格进入实验阶段。这种对抗式生成，比单机版的自问自答要鲁棒得多。

### 05 实验室的“肌肉记忆”与哨兵

ARC 还有一个 **Sentinel 哨兵机制**，像监控摄像头一样盯着实验过程中的 NaN 或 Inf 数值异常。

同时，它会把每次运行的教训（比如某个 API 的坑、某种指标的异常）写进一个知识库。这个知识库有 30 天的时间衰减，就像人的记忆一样。下次你换个课题跑，它会调用之前的“肌肉记忆”，避免在同一个坑里栽两次。

### 06 怎么上手玩？

如果你想体验这种“全自动灌水”或者深度辅助研究的快感，安装还算友好：

​

```
ounter(lineounter(lineounter(lineounter(lineounter(lineounter(lineounter(lineounter(line
# Pull AutoResearchClaw project
git pull https://github.com/aiming-lab/AutoResearchClaw.git

# Fully autonomous — no human intervention
pip install -e . && researchclaw setup && researchclaw init && researchclaw run --topic "Your research idea here" --auto-approve

# Co-Pilot mode — collaborate with AI at key decision points
researchclaw run --topic "Your research idea here" --mode co-pilot
```

它不仅支持 OpenAI 兼容接口，还能通过 ACP 协议直接对接你的本地 Agent（如 Claude Code 或 Codex）。会议模板目前已经支持 NeurIPS 2025、ICLR 2026 和 ICML 2026，在配置文件里改一行代码就能切换。

### 07 最后聊两句

虽然 AutoResearchClaw 现在的 v0.2.0 版已经跑通了 1100 多个测试用例，但作为开发者，我们得保持清醒：实验质量高度依赖你底层模型的推理能力。 如果你用个低端模型，它生成的分析结论可能还是会“逻辑跳跃”。

但不可否认，这个 MIT 协议的开源项目把“AI 科研”的工程化天花板又往上顶了顶。它把那些繁琐的、重复性的、不需要太多创造力的科研搬砖活儿给标准化了。 与其担心被替代，不如先装一个，看看这只“龙虾”能不能帮你把那个拖了半年的 Idea 给跑出来。

---

> **开源地址：** https://github.com/aiming-lab/AutoResearchClaw

关注点赞收藏不迷路，把这些硬核干货带回家，关键时刻能帮你省掉一半时间 🚀

  

---

![[笔记同步助手/images/b624d257433fb738e5ae8e5c51d8e413_MD5.jpg|cover_image]]

原创 NeoAgent NeoAgent

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/6cabf13e_1779539111937?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzY5MTI1OTE0Ng%3D%3D%26mid%3D2247483991%26idx%3D1%26sn%3Dd7b154e53df63cbd4b15195fa66f2c9a%26chksm%3Df56054b4fd6c5f394717cf0c8537322f6ba2c927e648e886817b992b1fa2070d6b2c4532cc9b%26mpshare%3D1%26scene%3D1%26srcid%3D0523h0M4iZXZbBkG636kaBtW%26sharer_shareinfo%3D0e42b3c3a2ef8e4298b8100ea936d503%26sharer_shareinfo_first%3D0e42b3c3a2ef8e4298b8100ea936d503%23rd&s=obsidian)