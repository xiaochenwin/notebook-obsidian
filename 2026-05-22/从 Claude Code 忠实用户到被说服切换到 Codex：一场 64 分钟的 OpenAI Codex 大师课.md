---
author: 邵猛
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzkwNDExODE4Nw==&mid=2247496882&idx=1&sn=3809729da1b43cfbf4791a3321715587&chksm=c1fe9e6a49c96c757b8a3706896d52abd72a31836f80bf8d442e64aae2fd0d9c3445fc37763c&mpshare=1&scene=1&srcid=0522PaCqNUH0CdJNaXlLO92O&sharer_shareinfo=2f5d7788bc79b402a06d94870c279fbb&sharer_shareinfo_first=2f5d7788bc79b402a06d94870c279fbb#rd
saved: 2026-05-22 13:50:37
tags:
  - 笔记同步助手
id: 80e947c9-ba28-4a7d-9797-d03a267b0f55
---

公众号名称：AI 启蒙小伙伴

作者名称：邵猛

发布时间：2026-04-29 07:50

![[笔记同步助手/images/52b3b9797e89bb9d13467c92d0ebb6d4_MD5.jpg]]

> 基于 Greg Isenberg × Riley Brown 的 64 分钟对谈（_Startup Ideas Podcast_）
> 
> 视频原链接：YouTube — Stop using Claude. Start using Codex?
> 
> https://www.youtube.com/watch?v=LWx4FGam2aQ&t=1804s

这是一期"怀疑者被说服"的对谈。Greg 自己坦言此前从未下载过 Codex，长期使用 Claude Code，而 Riley Brown（这是他第 5 次上 _Startup Ideas Podcast_）的任务是用一小时把他拉进 Codex 生态。咱们看看他是怎么做到的？你会不会也能成功被吸引到 Codex 阵营中？！

---

## 核心论点: OpenAI Codex 正在变成"知识工作 + 编码"的 Super App

Riley 的中心主张是:**Codex 不是一个编码工具,而是一个把编码、文档、表格、PPT、研究、浏览器操作、计算机操作、自动化全部塞进同一个界面的"超级应用"**,底层模型是刚发布的 GPT 5.5。

他给出的对照参考是 Claude 的产品分裂:

-   Claude Code 负责写代码;
-   Claude Cowork 负责知识工作;
-   两者权限体系、运行环境互不相通。

Riley 认为这种割裂"没有任何合理理由"——做 landing page 的人本来就需要在同一个界面里写文档、做调研、生成站点。Codex 的产品决策是把这些合并到一个 GUI 里:左边对话列表、中间 agent、右边产物(这恰好也是新版 Cursor 和新版 Claude Desktop 收敛到的同一个 GUI 范式)。

​

> 值得注意的判断:**2025 是 TUI 之年,2026 行业共识正在回到 GUI。** Claude Code 的早期终端体验虽然让极客兴奋,但对大多数业务用户门槛过高。

---

## Claude Code vs Codex: Riley 的实际取舍

不是非此即彼,而是"叠加订阅"。Riley 给出的真实工作流是:

1.  平时用 Codex(GPT 5.5),因为它对**复杂基础设施类任务**更稳。他和七位工程师组成的团队都已切换。他举了一个例子:用 GPT 5.4 一次性(one-shot)生成了一个类似 Replit 的 vibe coding 工具,含沙箱,耗时 1 小时 20 分钟。
2.  在 Codex 内按 ​`Cmd+J` 打开终端,输入 ​`claude`,就能在 Codex 里直接跑 Claude Code,**同时复用 Anthropic 订阅的 token 额度**。
3.  设计类调整交给 Claude("Claude 在设计审美上更强"是他直接承认的);底层重活交给 Codex。

这个组合的隐含信息是:**目前没有一个模型能在所有维度领先**,订阅经济(每月 $100–200 包含上千美元等值 token)让"双订阅"变成成本最低的策略。

---

## GPT 5.5 的关键变化与"够用就好"的精度选择

-   API 价格大约是 GPT 5.4 的 **2 倍**,比 Opus 4.7 高约 **20%**。
-   但 Riley 指出更关键的指标变化:**Token 效率不再是衡量标准,"完成同一任务的总耗时与总成本"才是**。GPT 5.5 更会揣摩用户意图,因此走弯路更少。
-   Effort 档位有四档:low / medium / high / extra high。社区(Theo 等)的经验是:**简单改动用 low/medium 即可**,extra high 反而会让模型过度思考、自行扩大改动范围。Riley 自己承认懒得切档,长期挂在 extra high。

对独立开发者的现实建议:**默认 medium,只有真复杂的任务才升档。** 这是省钱且更可控的姿态。

---

## Plugins / Skills / MCP / Connectors: 术语乱局的实用拆解

Riley 也吐槽了这套术语的混乱(plugin 用 ​`@` 触发,skill 用 ​`/` 触发,UI 还把它们混在同一个 tab 里)。他给出的可用心智模型:

| 概念 | 谁能创建 | 本质 |
| --- | --- | --- |
| **Plugin** | 仅 OpenAI 审核通过的官方集成(Slack、Notion、Sheets、Expo、Remotion、Canva 等) | 深度集成 |
| **Skill** | 任何用户都能建 | 一个文件夹 + 一个 ​`SKILL.md`,里面是给 agent 的指令 |

创建 Skill 的方法朴素到让人意外:**直接对 Codex 说"帮我创建一个做 X 的 skill"**,模型会自动生成 ​`SKILL.md` 并落盘。Riley 的两个示例:

-   `YouTube Researcher`:拉取频道近 N 个视频的 transcript 并生成报告。
-   `Internet Image Puller`:抓取一个公司的全部品牌资产(logo、配色、字体)落地为 HTML,供 Remotion 调用。

这一段最有价值的方法论是:**与其教 AI"怎么做",不如给它"好结果的样本"**。Riley 反复强调:"一个好范例胜过一段好指令;五个好范例就能稳定输出。" 他给企业的建议是 —— **把 AI 落地的关键工作不是写 prompt,而是系统性收集"好的成品样本"**,存进 Notion 数据库,让 agent 检索引用。

---

## Notion 集成的"外科手术式"权限

这是被低估的实用细节:Notion 插件允许**只授权一个 database**,而不是整个 workspace。对在意隐私和安全边界的用户,这意味着可以让 agent 只读写"视频脚本库"这种单一空间,不污染其他内容。

Riley 自己已经基本不再深度使用 Notion("上手成本太高,难以让团队成员加入"),但保留它作为视频脚本评论区。他更看好的未来形态是:**Notion 作为浏览器里的一个网页存在,agent 通过浏览器操作它,订阅成本由 Codex 一侧承担**。

---

## Computer Use 的"宽带时刻"

去年 Manus 等产品的 browser/computer use 体验"像拨号上网"。Riley 在节目中演示了一个 one-shot 提示:

​

> "做一个国际象棋游戏,然后用 computer use 在游戏里和自己对弈,直到一方获胜。"

Codex 一次成型生成了游戏,调起浏览器,自己同时执行白方和黑方,直至将死。**速度接近正常人手动操作。** Riley 的判断:**到 2026 年年底,browser agent 的速度将逼近人类**,意味着"任何能用浏览器完成的事都能被自动化"。

伴随而来的是 Atlas(OpenAI 的浏览器)正在被并入 Codex,未来会成为持久登录的完整浏览器——这是和 Claude Code / Cursor 的产品边界差异最大的一点。

---

## Chronicle:屏幕级记忆层(隐私警告)

发布时间是录制前两天。机制是 **持续观察屏幕,把上下文沉淀为 Codex 的长期记忆**。Riley 自己开了,但明确说"这是工作机,我不在乎隐私;不建议你直接照做"。

它的潜在价值在于:**不再需要给 agent 解释你正在做什么**。但风险面同样真实。专业建议是:**了解它存在 → 评估你的合规边界 → 不要默认启用。**

---

## Remotion:被低估的"代码生成视频"工作流

Remotion 是用 React 代码生成 motion graphics 视频的框架。Codex 自带 Remotion 插件,​`@remotion` 即可触发。Riley 的工作流:

1.  先用 ​`Internet Image Puller` 抓取品牌资产到 ​`brand-assets` 目录;
2.  在 Remotion 任务里引用资产路径:"请用 X logo + 这套配色生成 Y 场景";
3.  Codex 同时启动 Remotion 预览(类似 CapCut 时间轴)让你 review。

Anthropic 的产品发布视频几乎全是 Remotion 产出。Greg 提到他认识的多个账号靠 Remotion 视频从 0 涨到 10 万 Instagram 粉丝。**对早期创业者来说,这是当前性价比最高的 launch video 路径**——比 Sora 类生成视频可控,比 After Effects 门槛低。

​

> Riley 的设计原则:**好的发布视频永远只让一件事在屏幕上发生**,避免视觉过载。

---

## Computer Use 与 Swift 移动应用一次成型

-   Computer Use 现在能**同时控制多个本地应用**。Riley 演示过让它操作 Canva、导出文件、再把结果回喂给 Codex。
-   Swift 移动应用:本地需要 Mac + Xcode,但 Codex 能 one-shot 出**完整移动应用**。Riley 的原话:"已经到了让我有点害怕的程度——任何能存在的 app 都将存在。"

这两点指向同一个方向:**未来差异不在"能不能造",而在"造什么、为谁造、如何分发"**。

---

## 第一天上手的 4 个练习项目

Riley 把这部分单独写下来了,按顺序执行价值最大:

1.  **做一个游戏,让 computer use 和自己对弈**——直观感受 computer agent 的现状与三个月后的位置。
2.  **一次端到端的深度研究**:让 agent 用 max effort 调研一个主题 → 输出 spreadsheet → 转成 doc → 转成 deck。一遍走完,你就懂了"知识工作管线"。
3.  **3D 模拟**——纯粹好玩,但能让你直觉化感知物理引擎类任务的能力上限。
4.  **把现有 web app 迁成 Swift 移动应用**——只在你有真实需求时做。

完成上述之后,**列出你每天最烦的工作 → 用 Plugin 或 Skill 拼出工作流 → 让 agent 把它转成 Automation(Codex 自带的定时任务)**。Riley 给出的句式很简单:"I want you to do this every Friday at 9am, please create an automation." 模型直接帮你建调度。

Greg 现场演示了一遍:让 Codex 每周五早上 9 点拉取本周视频做"只挑毛病的报告"。

---

## 值得直接抄走的几条原则

1.  **挑一套技术栈,坚持下去**。Riley 反复强调"在热门工具间反复横跳是反生产力的"。换栈的代价是放弃肌肉记忆和自建 skills 库。
2.  **承担"看起来很笨"的成本**。在 SF 真正赢的人不是"tinkerer"本身,而是**不怕看起来笨的 tinkerer**。
3.  **用录屏代替写文档**。即将到来的 Codex 版本会支持上传视频学习工作流——意味着**现在养成录屏习惯就是为未来 agent 训练数据做储蓄**。这也是 Meta、Microsoft 内部要求员工录屏的真正动机。
4.  **examples > instructions**。这是企业落地 AI 的最大杠杆。

---

## 最后一句话总结

> 如果你已经在 Claude Code 里做得顺手,不必迁移;如果你刚要进入 AI 协作工作流,**Codex 当前是上手成本最低、覆盖任务面最广的单一入口**——但请把它当作"实验场",按 Riley 的 4 个项目走一遍,再决定要不要把它接进你的真实业务流。

---

## Codex 相关资源推荐

[OpenAI Codex 官方最佳实践和最新六大关键能力升级](https://mp.weixin.qq.com/s?__biz=MzkwNDExODE4Nw==&mid=2247496787&idx=1&sn=737e84fcc60df9e9da2f9f65f10ee543&scene=21#wechat_redirect)

[Codex + GPT-5.4 vs. Claude Code + Opus 4.6，Codex 除了慢几乎全面占优、自主性强、适合企业开发，CC 速度和迭代快适合中小型开发](https://mp.weixin.qq.com/s?__biz=MzkwNDExODE4Nw==&mid=2247496782&idx=1&sn=13834e1685cd4251cad4d82126db298d&scene=21#wechat_redirect)

[OpenAI Codex 核心成员访谈：Codex 团队如何用 Codex 做研发工作，对 AI Native 团队又有哪些重要启发？](https://mp.weixin.qq.com/s?__biz=MzkwNDExODE4Nw==&mid=2247496683&idx=1&sn=11d899f9a7b8c75c8d0c93209bd2cc72&scene=21#wechat_redirect)

[OpenAI Codex 最佳实践指南——8个步骤完整闭环、5个实操结论和7个典型误区](https://mp.weixin.qq.com/s?__biz=MzkwNDExODE4Nw==&mid=2247496549&idx=1&sn=e77c28290d2ca3204de3147522b71832&scene=21#wechat_redirect)

---

![[笔记同步助手/images/8949799b378c2c1e06d142a1b211f0c4_MD5.jpg|cover_image]]

Original 邵猛 AI 启蒙小伙伴

作者提示: 内容由AI生成

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/1310db0f_1779429034941?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkwNDExODE4Nw%3D%3D%26mid%3D2247496882%26idx%3D1%26sn%3D3809729da1b43cfbf4791a3321715587%26chksm%3Dc1fe9e6a49c96c757b8a3706896d52abd72a31836f80bf8d442e64aae2fd0d9c3445fc37763c%26mpshare%3D1%26scene%3D1%26srcid%3D0522PaCqNUH0CdJNaXlLO92O%26sharer_shareinfo%3D2f5d7788bc79b402a06d94870c279fbb%26sharer_shareinfo_first%3D2f5d7788bc79b402a06d94870c279fbb%23rd&s=obsidian)