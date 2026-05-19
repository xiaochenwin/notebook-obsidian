---
author: 大刘
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzIyNzQ3MDM3Mw==&mid=2247485373&idx=1&sn=eaef1ae649da8f5114887e2547cae1af&chksm=e9ab3d80ee08f31db9fac6ce83544ce2002e99c3efd2b5af954a93735c6fa678f0f42c242a34&mpshare=1&scene=1&srcid=05195aiUrtsB73ANLWtq28CF&sharer_shareinfo=f81b912c26235654da766f0cf1906fb8&sharer_shareinfo_first=f81b912c26235654da766f0cf1906fb8#rd
saved: 2026-05-19 16:41:19
tags:
  - 笔记同步助手
id: 7598494e-0e1c-4afe-b308-e24300126f77
---

公众号名称：爱AI的大刘

作者名称：大刘

发布时间：2026-05-18 15:13

可能是最系统的 Claude Code 保姆级教程。

​

![[笔记同步助手/images/b3773a1b22a11b707d9f0e5370f4310c_MD5.png]]

✍️ 作者: 大刘  
📝 编辑: 大刘  
🎨 排版: 大刘

**Claude Code 应该是 2026 最值得学的工具。**

但是大部分人学的都非常不系统。

这件事比我预想的更典型。

Claude Code 这工具，门槛真正卡人的不是技术，是顺序。**装在哪一步、配置在哪一步、什么时候开始建 Skills、什么时候才该上多代理**。顺序错一格，后面全部走样。

所以这篇，我把过去输出的教程拆开重组，加进去最近半年我的实战补丁，做成一篇**一次看完能跟着做完**的总教程。

**系统性教程！**

**注意，电脑端食用更舒服！**

**这里是免费的 PDF 版本文档：https://my.feishu.cn/wiki/H1NtwIDoZiqMbbk3iEBciaajnKe?from=from\_copylink**

  

## 先赞后看，腰缠万贯～

  

看完它，你能从零跑通五件事：

第一，用 **Anthropic 官方一行命令**装好 Claude Code。

第二，按 DeepSeek 官方 Claude Code 接入文档，把 **deepseek-v4-pro\[1m\]** 配成默认模型。

第三，把 Claude Code 放进 **IDE 工作区**，跑通第一个 demo。

第四，装好 **Skills 体系**。

第五，用一条「**澄清 → 计划 → 分工 → 落盘 → 交付**」工作流，把一项真实工作交给 Claude Code 干完。

![[笔记同步助手/images/69ac9df16cabcfeea2fac1e4fe55af6a_MD5.jpg]]

你可以把这篇当成一份**入职手册**。

Claude Code 是你接下来要带的一支**执行团队**，这篇文章告诉你怎么招人、怎么交代任务、怎么让他们组织起来干活。

## Part 1 安装配置：从打开终端到第一个 demo

01

1-A 它是什么，它不是什么

先把认知校准好，后面装起来不会理解偏差。

**Claude Code 是装在你电脑里的 Agent 软件**。它会读你的文件、跑你的命令、调你的模型。它跑在终端里，跟你的项目目录是绑在一起的。

它不是 Web 端 Claude 聊天的复刻。Web 端是聊天，Claude Code 是干活。它也不是 IDE 插件，它本身就是一个独立的命令行客户端。

你可以把它理解成：**一个刚来你公司的新员工**。

你要做的事情有三件：给他门禁卡（API Key 和配置）、给他工位（一个 IDE 打开的工作区文件夹）、给他第一个任务（第一条 Prompt）。

这个员工记忆短、能力强、不挑活。你交代清楚，他执行力顶尖；交代不清楚，他会努力按自己的理解干完，交一份你不想要的东西。

**它不是 Web 端聊天，是一个把对话和项目绑在一起的执行端。**

1-B 路线选择 + 三件套

要跑起来，你需要三件东西：**API Key、Endpoint、Model Name**。

你可以把它理解成：**钥匙、地址、员工名牌**。Key 是钥匙（证明你有调用权限），Endpoint 是地址（告诉客户端去哪个服务器找模型），Model 是员工名牌（指定具体让哪个模型来干活）。

主推路线我自己判断是 **DeepSeek API + deepseek-v4-pro\[1m\]**。

理由很直白。2026 年看下来，DeepSeek 这条路的性价比、长上下文、Coding 任务稳定性这三项综合分都不错。

备选路线也列一下，自己按预算和工作量挑：

1\. **Anthropic 原生 Max Plan**：如果你已经能直接订阅，稳定性和模型质量最高，价格也最贵。

2\. **MiniMax-M2.7**：走 MiniMax Token Plan 路线。

判断边界：如果你已经能直接用 Anthropic 官方订阅，就没必要切。

这篇文章后面所有的配置，都假设你走的是 DeepSeek 这条主推路线。

1-C 用官方一行命令装好它

这一段是整个 Part 1 最关键的一段，**直接抄命令就行**。

macOS / Linux / 以及 Windows 上的 WSL，打开终端，一行命令：

●​●​●

curl -fsSL https://claude.ai/install.sh | bash

![[笔记同步助手/images/b4ec688e3d15c374c8f4c470db5a5793_MD5.jpg]]

Windows 用户，用管理员权限打开 PowerShell，一行命令：

●​●​●

irm https://claude.ai/install.ps1 | iex

这两条都是 **Anthropic 官方原生安装脚本**，跑完之后 `claude` 命令就直接进你的环境变量了，跟装 git、装 node 是同一档操作。

有人会问：那我已经有 Node 18+ 了能不能用 npm 装？

可以，执行 `npm install -g @anthropic-ai/claude-code` 也是官方支持的方式，适合你已经习惯用 npm 管全局包的情况。

还有人会问：那 Trae / VS Code / Cursor 这些 IDE 是不是必装？不是。

Claude Code 本身是命令行工具，你直接用 macOS Terminal、iTerm、Windows PowerShell、WSL 任何一个终端都能跑。**但是能跑，不等于日常最顺手。**

我的建议是分两步：

第一步，先在裸终端里跑通一遍。这样你知道 `claude` 命令本身装好了，不会把 Claude Code 误解成某个 IDE 的插件。

第二步，正式干活时回到 IDE。Trae、Cursor、VS Code 都可以，核心不是选哪个 IDE，而是用 IDE 打开一个明确的工作区文件夹，再在 IDE 的内置终端里启动 Claude Code。

IDE 在这里不是前置条件，是**工作台**：左边看文件，中间改内容，底部跑 Claude Code，右侧 AI 面板可以辅助你装环境、解释报错、整理命令。

如果你用的是 Trae 或 Cursor，也要分清楚：IDE 自带 Agent 可以当“装机代理”，帮你检查环境、跑安装命令、解释报错；但后面真正调模型、读项目、改文件、跑任务的主角，还是底部终端里的 **Claude Code CLI**。

1-D 第一次跑 `claude` 命令

装完之后，任意目录下输入：

●​●​●

claude

![[笔记同步助手/images/21cbf3568d8d9bb91dc0cf1d64cfe284_MD5.jpg]]

第一次启动会引导你完成授权。如果你后面要走 DeepSeek 路线，这一步授权可以先跳过。

等下一步配完环境变量，它会按你的配置走 DeepSeek 的接口。

到这一步，**Claude Code 已经在你电脑上了**。

但它还没拿到钥匙，还不知道去哪里找模型。下一步，把通行证配好。

1-E 环境变量：Claude Code 的通行证

这里直接走 DeepSeek 官方 Claude Code 接入文档里的**环境变量方案**。

macOS / Linux / WSL 用户，打开终端，直接粘这一组：

●​●​●

export ANTHROPIC\_BASE\_URL=https://api.deepseek.com/anthropic  
export ANTHROPIC\_AUTH\_TOKEN=<你的 DeepSeek API Key>  
export ANTHROPIC\_MODEL=deepseek-v4-pro\[1m\]  
export ANTHROPIC\_DEFAULT\_OPUS\_MODEL=deepseek-v4-pro\[1m\]  
export ANTHROPIC\_DEFAULT\_SONNET\_MODEL=deepseek-v4-pro\[1m\]  
export ANTHROPIC\_DEFAULT\_HAIKU\_MODEL=deepseek-v4-flash  
export CLAUDE\_CODE\_SUBAGENT\_MODEL=deepseek-v4-flash  
export CLAUDE\_CODE\_EFFORT\_LEVEL=max

Windows 用户，在 PowerShell 里粘这一组：

●​●​●

$env:ANTHROPIC\_BASE\_URL="https://api.deepseek.com/anthropic"  
$env:ANTHROPIC\_AUTH\_TOKEN="<你的 DeepSeek API Key>"  
$env:ANTHROPIC\_MODEL="deepseek-v4-pro\[1m\]"  
$env:ANTHROPIC\_DEFAULT\_OPUS\_MODEL="deepseek-v4-pro\[1m\]"  
$env:ANTHROPIC\_DEFAULT\_SONNET\_MODEL="deepseek-v4-pro\[1m\]"  
$env:ANTHROPIC\_DEFAULT\_HAIKU\_MODEL="deepseek-v4-flash"  
$env:CLAUDE\_CODE\_SUBAGENT\_MODEL="deepseek-v4-flash"  
$env:CLAUDE\_CODE\_EFFORT\_LEVEL="max"

逐项解释：

**ANTHROPIC\_BASE\_URL**：这里写的是 DeepSeek 的 anthropic 兼容入口。

**ANTHROPIC\_AUTH\_TOKEN**：把 `<你的 DeepSeek API Key>` 替换成你在 DeepSeek Platform 创建的真实 Key。注意尖括号也要删掉，不要保留 `<` 和 `>`。这串 Key 永远不要贴到任何聊天框或仓库里。

**ANTHROPIC\_MODEL**：Claude Code 主会话默认用哪个模型。按 DeepSeek 官方文档，Claude Code 这里写 `deepseek-v4-pro[1m]`。

**ANTHROPIC\_DEFAULT\_OPUS\_MODEL / ANTHROPIC\_DEFAULT\_SONNET\_MODEL / ANTHROPIC\_DEFAULT\_HAIKU\_MODEL**：Claude Code 内部会按不同任务档位叫模型，这三项是把它们映射到 DeepSeek 的模型上。主力任务走 `deepseek-v4-pro[1m]`，轻量任务走 `deepseek-v4-flash`。

**CLAUDE\_CODE\_SUBAGENT\_MODEL**：子代理默认用哪个模型。这里用 `deepseek-v4-flash`，更省。

**CLAUDE\_CODE\_EFFORT\_LEVEL**：推理努力程度。官方示例写 `max`，先照抄。

**环境变量就是 Claude Code 的通行证**。你的身份、要去的服务器、用谁干活，全在里面。

1-F 回到 IDE：用工作区承载 Claude Code

环境变量解决的是“Claude 去哪里找模型”。工作区解决的是“Claude 在哪里干活”。

这一步很关键。不要在桌面乱跑，也不要在 Home 目录里乱跑。

**一个项目的任务独享一个工作区文件夹**，后面 Claude 创建的计划、代码、报告、图片、PDF，都应该落在这个文件夹里。

最简单的划分规则：

  

### 1\. 学习 demo 单独建 claude-first-demo/

### 2\. 客户项目单独建客户项目文件夹

### 3\. 行业调研单独建 research-topic-name/

  

不要把不同的工作混在同一个目录里。Claude Code 很强，但你把工作台摆乱了，它也会读到一堆不该读的上下文。

以 Trae 为例，Cursor 和 VS Code 也一样：

第一步，在桌面新建一个文件夹：

●​●​●

claude-first-demo/

![[笔记同步助手/images/b481b083f2a0858f989c697249e1ff44_MD5.jpg]]

第二步，用 IDE 打开这个文件夹。菜单里一般叫 **Open Folder / 打开文件夹**。

打开之后，先认四个区域：

**左边文件区**：Claude Code 后面新建的 `index.html`、`README.md`、`report.md`，都会出现在这里。

**中间编辑器**：你可以随时点开文件，看 Claude 写了什么，也可以手动改。

**底部终端**：这里才是你启动 Claude Code 的地方。以后日常工作，基本都在这个终端里输入 `claude`。

**右侧 AI 面板**：Trae / Cursor 这类 IDE 会有自己的 AI 面板。它不是 Claude Code 本体，但很适合帮你解释报错、准备安装 Prompt、辅助检查环境。

![[笔记同步助手/images/349a9d7afb8760a00603981633800ff0_MD5.jpg]]

第三步，在 IDE 底部打开终端，确认当前路径就在这个工作区里。

![[笔记同步助手/images/fcc72e04a83bddf0f6b59b6f689d7293_MD5.jpg]]

第四步，启动 Claude Code。

记住这个顺序：**先建工作区 → 用 IDE 打开 → 在 IDE 终端里配环境变量 → 启动 Claude Code**。

1-G 验证三连

配完别急着干活，先**做一次员工入职体检**。三条命令：

●​●​●

claude --version

![[笔记同步助手/images/cd6456eaf848471ca3d03cd422d29caf_MD5.jpg]]

这条看版本号，确认装上的是最新版。如果你装完才几分钟就发现版本旧了，跑一下官方升级命令即可。

●​●​●

claude doctor

![[笔记同步助手/images/2e91bffeba0fe1f837d75796cbad0a4f_MD5.jpg]]

这条做环境自检，会告诉你环境变量有没有生效、API Key 有没有效、网络能不能通。**doctor 报错先别慌**，大部分是 Key 没贴对、BASE\_URL 拼错，或者你开了新终端但忘了重新执行上面的环境变量。

验证通过后，在同一个 IDE 终端里启动 Claude Code：

●​●​●

claude

启动 Claude 之后，在对话框里：

●​●​●

/status

![[笔记同步助手/images/fe0f23e3c8f628d3915a89a94596df26_MD5.jpg]]

这条看当前会话的实际配置。**核心要看的是 Model 那一栏，应该显示 \`deepseek-v4-pro\[1m\]\`**。

三条都过了，**员工入职完成**，可以分活了。

1-H 第一个 demo：做一个个人介绍页面

第一个任务我建议你做一件**真正小、但能完整走完一遍循环**的事：做一个个人介绍 HTML 页面。

现在就在刚才的 `claude-first-demo` 工作区里做。打开 IDE 底部终端，确认已经启动 `claude`，然后**整段粘下面这条 Prompt**：

●​●​●

目标:做一个我的个人介绍单页 HTML，深色背景、卡片式布局，左边一张头像位置(用占位图)、右边写姓名、一句话简介、三条履历。  
位置:就在当前目录下，文件名 index.html，样式内联进 HTML，不要外部依赖。  
验证:做完之后用浏览器打开能看到完整页面，没有报错。  
约束:不要加任何外部图片链接，头像用一个 #333 的圆形占位 div。

![[笔记同步助手/images/a70cf5f346cf53eab3b3d6b900fa803f_MD5.jpg]]

提交。**注意看它怎么干活**：它会先告诉你它要做什么（规划），然后开始建文件（执行），写完之后会主动让你打开浏览器验证（自检）。

打开 `index.html`，**你的第一个 Claude Code 作品就在浏览器里了**。同时你会在 IDE 左侧文件区看到这个文件，在中间编辑器里看到它的源码。

![[笔记同步助手/images/dcb699b2d1be97c293ff81b3b7a53e5d_MD5.jpg]]

记一下我刚才那条 Prompt 的结构：**目标、位置、验证、约束**。这四项后面我们会再展开，这是大刘自己每天用的“四件套”。

**好的 Prompt 不是在跟 AI 聊天，是在给 AI 写工单。**

1-I 阶段过渡

到这一步，你的电脑上有一个能跑的 Claude Code，DeepSeek 环境变量配好了 `deepseek-v4-pro[1m]`，也知道怎么把它放进 IDE 工作区里跑第一个 demo。

**装好不等于会用。下一步，我们让 Claude Code 听懂你说的话。**

## Part 2 核心用法：让 Claude Code 听懂你说的话

02

2-A Agent Loop：它的工作日是怎么过的

要让它听懂你，你得先理解它的工作机制：**Agent Loop**。

这个东西的本质是，Claude Code 不是问答工具，**是循环工具**。每接到一个任务，它会跑一个五步循环：

**第一步，收集上下文**。读你给的文件，看当前目录，理解你说了什么。

**第二步，规划任务**。把大任务拆成小步骤，排出顺序。

**第三步，执行操作**。建文件、改代码、跑命令、调工具。

**第四步，验证结果**。跑一下、看一下、对照你给的验证标准。

**第五步，自我纠正**。如果验证不过，回到第二步重新规划。

![[笔记同步助手/images/2c361c94763417ac260f12dcad07193d_MD5.jpg]]

这里有个反直觉的点：**它不是“问一句答一句”，是“接到任务就开始转圈，转到完成或者撞墙才停”**。它的“一天”可能只有几十秒到几分钟。

理解这一点，你就知道为什么 Prompt 要按“目标、位置、验证、约束”写。你不是在跟它聊天，你是在给它今天要跑的循环预先设定 KPI。

**Claude Code 不是聊天工具，是执行团队。**

2-B 上下文管理：它今天能记住的事

新员工有个特点：**记忆短**。

Claude Code 这位员工的“记忆”叫 Context，你一次告诉他的所有事、给他看的所有文件、跑过的所有命令，都堆在 Context 里。

Context 不是无限的。烧爆了，他会开始忘事、开始胡说。

四个命令必须记住：

**\`/context\`**：看当前 Context 还剩多少。

![[笔记同步助手/images/ad21d52b73c27d1785235f66f674ddfd_MD5.jpg]]

**\`/clear\`**：清空当前会话的所有记忆，从零开始。这一条比你想的更常用。

**\`/compact\`**：不清空，但是让 Claude 自己把当前会话的内容压缩一下，保留要点丢掉细节。Context 用到一半的时候执行，等于给员工做个“工作笔记小结”。

![[笔记同步助手/images/23c0c3346458eb6dd564ec82e78c66a8_MD5.jpg]]

**\`/cost\`**：看到目前为止这个会话大概烧了多少钱。走 DeepSeek API 是按 token 计费，Claude Code 里的 `/cost` 更适合当作消耗估算，最终扣费以 DeepSeek 控制台为准。

我自己的判断是：**不要相信一个会话能聊一天**。Token 烧到 50% 之前主动 `/compact`，烧到 70% 直接 `/clear` 起新会话。

很多人卡住的根本原因不是 Prompt 不好，是**会话开太久了**，Claude 在前面的历史包袱里转不出来。

**新会话 + 好提示 > 长会话 + 累积修正。**

2-C 三种权限模式

按 Shift+Tab，Claude Code 在三种权限模式之间循环切换：

**Normal Mode（普通）**：每一步操作都问你一次，要不要执行。最安全，最慢。

**Plan Mode（计划）**：先讨论方案，你点同意之后才动手。这是真正的主用模式，后面会重点讲。

**Auto Mode（自动）**：全权放手，看到什么干什么，不问你。最快，最危险。

![[笔记同步助手/images/631b4e5dfe029076c8b49eb365faed58_MD5.jpg]]

我自己用下来，**80% 的时间在 Plan Mode**。

Auto Mode 只在“已经把一切讲清楚 + 知道最坏结果可控”这种场景下用，比如让它一次性把一个准备好计划的项目跑完。

或者，你真的受不了一直点“Yes”了。

2-D 四件套 Prompt：写在前面而不是反复修

到这里讲 Prompt 公式。

我给它起了个名字：**四件套 Prompt**。

四件套就是 Part 1 第一个 demo 里出现过的那四项：**目标、位置、验证、约束**。

**目标**：你要它干什么。

**位置**：在哪里干、文件叫什么、目录结构怎么放。

**验证**：怎么判断干完了。最好给一条可执行的验收命令或者一个可视化标准。

**约束**：不许做什么、不许用什么、必须避开什么。

完整模板：

●​●​●

目标:\[一句话说清楚要做什么\]  
位置:\[文件路径或目录结构\]  
验证:\[做完之后怎么确认完成\]  
约束:\[禁止事项 + 风格要求 + 依赖范围\]

![[笔记同步助手/images/c79a97170523801c0f8dfe75e12debc9_MD5.jpg]]

类比一下：Prompt 就是**给员工的工单**。工单上要有事项、地点、验收人、注意事项，Claude Code 看到的就是这四项。

很多人写 Prompt 像在写微信，东一句西一句。

Claude Code 不挑活，你这样它也能干，但它会按自己的理解补全那些你没说的事，补全的方向不一定是你想要的方向。

更准确的说法是：

**你少写的每一项，它都会替你做一个默认假设。**

这些默认假设的总和，就是你最后不满意的那个版本。

多说一句，之前有个很火的岗位，叫 Prompt Engineering，就是提示词工程师。

做的就是这件事，讲清需求。**非常重要！**

2-E `@` 引用、`!` shell、错误粘贴

三个输入技巧，使用频率非常高。

**\`@\` 引用文件**：在对话框里输入 `@`，会弹出文件选择器。直接把一个文件甩给 Claude 读。比“我有个文件 xxx，内容是 ……”这种描述要稳得多。

![[笔记同步助手/images/ac0e3d5db2b8c55125d8d60f87d36bfe_MD5.jpg]]

**\`!\` 跑 shell**：在对话框开头输入 `!`，后面跟一条 shell 命令，Claude Code 会直接帮你执行。比如 `!ls` 就是看当前文件夹有什么内容，还有其他很多命令。

![[笔记同步助手/images/b315623dc191921bce7c801d81453609_MD5.jpg]]

**粘报错**：最实用的一个。代码跑挂了、命令报错了、构建失败了，**把终端输出整段粘进 Claude Code 的对话框**，加一句“修一下”。它会读报错、定位文件、改代码，绝大多数情况下比你自己 Google 快。

![[笔记同步助手/images/81ec7886e07c1400c58f1e18420468b3_MD5.jpg]]

2-F Plan Mode：90% 时间花在前面

Plan Mode 是 Claude Code 最重要的一个模式，这一段单独展开。

按 **Shift+Tab×2** 进入 Plan Mode。进去之后，对话框上方会显示一个 `plan mode` 的标签。

![[笔记同步助手/images/631b4e5dfe029076c8b49eb365faed58_MD5.jpg]]

在 Plan Mode 里，Claude Code 的工作流变成“**探索 → 规划 → 执行**”三步：

**探索**：它会先读你提到的文件、看相关代码、跑探测命令，搞清楚现状。

**规划**：基于探索结果，它会写出一份完整方案，告诉你它打算改哪些文件、加哪些功能、按什么顺序。

**执行**：你看到方案，**点同意之后它才动手**。不同意可以让它改方案，反复改到你满意为止。

![[笔记同步助手/images/4b461019c0d0c55fc2719236b92d1d58_MD5.jpg]]

这里有个反直觉的点，也是这一节我最想让你记住的一句话：

**Plan 占 90% 时间。好的 Prompt 写在前面，不是在对话里反复修。**

很多人用 Claude Code 的方式是，先扔一个粗糙 Prompt，看它干出什么，不行再骂它、让它改。

这种方式不是不能用，是**便宜的 token 当贵的 token 烧**。你在用执行循环替你思考，代价是反复跑、反复改、反复偏。

Plan Mode 的逻辑反过来：**把思考前置**。你和它在动手之前先对齐“要做什么、按什么顺序、最坏情况怎么办”，对齐完了再放它去跑。

**你以为 Plan Mode 在浪费时间，其实它是用 3 分钟思考省 30 分钟反复改。**

我自己实操下来，Plan Mode 写一份方案大概要 1-3 分钟，但执行阶段几乎一次过。

**前置 3 分钟，省后面 30 分钟反复改。**

Plan Mode 的实操 SOP：

第一件事，**Shift+Tab×2 进入 Plan Mode**。

接着，**用四件套 Prompt 描述任务**（目标、位置、验证、约束）。

然后，**让它先 \`@\` 引用相关文件做探索**，你看它的初步理解对不对。

到这一步，**让它出方案**。看方案里有没有跟你想象不一致的地方，有就让它改。

最后，**方案对齐了再放执行**。

![[笔记同步助手/images/eab5b1c428abbd3cd5676c12251a6e4c_MD5.jpg]]

2-G CLAUDE.md：它的永久记忆载体

Context 是短期记忆，Plan Mode 是当下对齐，**CLAUDE.md 是长期记忆**。

CLAUDE.md 是一个 Markdown 文件，Claude Code 每次进入一个目录会自动读它，把它当作“**这个项目的入职手册**”。

CLAUDE.md 有四个位置，**优先级从低到高就近覆盖**：

第一，**用户级**：`～/.claude/CLAUDE.md`，对你所有项目生效。

第二，**项目级**：项目根目录下 `CLAUDE.md`，对这个项目生效。

第三，**模块级**：子目录下的 `CLAUDE.md`，对这个子目录及下层生效。

第四，**内联级**：在对话里直接 `@CLAUDE.md` 引用一段临时说明。

**就近覆盖**的意思是，模块级会覆盖项目级，项目级会覆盖用户级。同一个变量在四个位置都定义了，实际生效的是离当前任务最近的那个。

懒得手动写第一版？**用 \`/init\`**。在项目根目录跑 `/init`，Claude Code 会自动扫描代码、读取 README、推断技术栈，给你生成一份 CLAUDE.md 草稿。

![[笔记同步助手/images/9c351f311574278c8f34857bc629c389_MD5.jpg]]

一份合格的 CLAUDE.md 模板，大致这几块：

●​●​●

\# 项目意图  
这是一个 \[一句话项目定位\]。​  
核心读者 / 用户:\[谁会用\]。​  
当前阶段:\[原型 / 内测 / 上线\]。​  
\# 技术栈选择  
\- 语言:\[Python 3.11 / Node 20 / ...\]  
\- 框架:\[FastAPI / Next.js / ...\]  
\- 数据库:\[PostgreSQL / SQLite / ...\]  
\- 部署:\[Vercel / 自建 / ...\]  
\# 禁止改动  
\- 不要修改 \`core/\` 下的任何文件，这是稳定层。​  
\- 不要引入新的全量依赖，需要的话先讨论。​  
\- 不要破坏现有 API 的入参签名。​  
\# 验收标准  
\- 任何改动都要跑过 \`pytest\` 全套。​  
\- 关键路径要有对应的 e2e 测试。​  
\- 接口变动需要同步更新 OpenAPI schema。​  
\# 工作流  
\- 默认在 Plan Mode 工作。​  
\- 大改动先开 plan.md，审批后再动手。​  
\- 验证不过不要往下走。​

类比一下：**CLAUDE.md 是员工 onboarding 文档 + 项目 wiki 的合体**。

新员工进项目第一天该知道的所有事，都应该在这里。

**CLAUDE.md 是 Claude Code 永久记忆的载体。**

2-H 命令速查

我自己最常用的 7 个命令，做成一张表：

| 命令 | 作用 |
| --- | --- |
| `/status` | 看当前会话配置（模型、目录、Token） |
| `/context` | 看 Context 用量 |
| `/clear` | 清空当前会话 |
| `/compact` | 压缩当前会话 |
| `/init` | 在当前目录生成 CLAUDE.md |
| `/cost` | 看当前会话消耗 |
| `Shift+Tab` | 切换 Normal / Plan / Auto 三种模式 |

![[笔记同步助手/images/f363ae5baa11b75670fba8ee651c4bdc_MD5.jpg]]

这张表你**截图存手机**就行，前两周高频用得上。

2-I 急救三步 + 五个常见坑

Claude Code 用到一定阶段一定会卡。卡在长循环里出不来、卡在错误代码里改不对、卡在反复跑没结果。

急救三步，**抄就行**：

**第一步，Ctrl+C 中断**。把它正在跑的循环掐掉。

**第二步，\`/clear\` 清空会话**。把这段尝试的全部历史包袱清掉。

**第三步，重新描述任务**。基于刚才学到的“它会卡在哪”，把 Prompt 写得更具体。

![[笔记同步助手/images/d5c0e5c9fcf9c839ca539c236b883d4b_MD5.jpg]]

**Ctrl+C → /clear → 重新描述。三步走完，90% 的卡死能解决。**

五个最常见的坑，提前避：

第一，**Token 烧爆**。会话拖太久，Context 满了它开始忘事。解决：`/compact` 或 `/clear`。

第二，**没 Plan 直接 Auto**。任务复杂的时候不用 Plan Mode，直接放它跑，出错率指数级上升。解决：**80% 的任务都在 Plan Mode 跑**。

第三，**没写 CLAUDE.md**。每次新会话都要从头解释项目，效率掉一半。解决：进项目第一件事 `/init` 生成 CLAUDE.md。

第四，**\`@\` 错文件**。引用了一个跟任务无关的大文件，Token 哗哗烧。解决：用 `@` 之前先想清楚这个文件是不是它真的需要看。

第五，**Prompt 太散**。一个对话里塞五件事，它会越做越偏。解决：**一个 Prompt 一件事**，做完再开下一件。

## Part 3 Skills 进阶：让 AI 替你记住你的工作方法

03

3-A Skills 是什么：岗位说明书

我在给朋友讲 Claude Code 的时候发现，Skills 这个概念最容易被误解的地方是：**大家以为它是插件，其实它是文档**。

更准确的说法是：Skills 是一组 Claude Code 可以在特定场景下自动读取并执行的 Markdown 文档 + 脚本组合。

它不像 MCP 那样要起一个服务，也不像 Prompt 那样要你每次手输。**它就静静地放在那里，触发条件一到，Claude 自己读、自己用**。

理解上就是： Skills 是**员工的可复用 SOP 手册**。

今天你教过这位新员工怎么做“公众号文章排版”，明天他遇到这件事，不需要你重新教一遍，他打开 SOP 手册自己干就行。

![[笔记同步助手/images/1a5f4b16942f3ff1996bd08df07289c9_MD5.jpg]]

**Skills 不是新工具，是给 Claude 的岗位说明书。**

3-B Skills 三件套：SKILL.md / scripts / references

一个 Skill 的标准结构是这样：

●​●​●

my-skill/  
├── SKILL.md # 触发条件 + 执行说明  
├── scripts/ # 可被调用的脚本  
│ └── do-something.py  
└── references/ # 参考资料、模板、提示词  
└── template.md

![[笔记同步助手/images/b1226303eb253096cea3e10ad076786c_MD5.jpg]]

**SKILL.md 是入口**。它的开头有一段 YAML frontmatter，告诉 Claude：这个 Skill 在什么场景下激活、它能做什么、调用方式是什么。

最简 SKILL.md 模板：

●​●​●

\---  
name: my-first-skill  
description: 在用户要求做 XX 的时候激活，产出 YY。触发关键词:\[关键词列表\]。  
\---  
\# 调用说明  
当用户提到 \[触发条件\] 时，执行以下步骤:  
1\. 读取 references/template.md 作为参考。  
2\. 调用 scripts/do-something.py 跑流程。  
3\. 把结果写到指定位置。

**scripts/** 放脚本，Python、Shell、Node 都行。Claude 会按需调用。

**references/** 放它要参考的资料：风格模板、写作范例、提示词参考。

Skills 比 Prompt 高一档的地方是：**它会被 Claude 自动发现**。你写了一个“公众号排版”Skill，下次你说“把这篇排版一下”，Claude 不需要你说“用那个 Skill”，它自己会扫描可用 Skills 列表、发现匹配的、激活它。

3-C 两个位置：全局 vs 项目

Skills 有两个安装位置：

**全局**：`～/.claude/skills/`，你所有项目里都能用。

**项目级**：`你的项目目录/.claude/skills/`，只在这个项目里能用。

![[笔记同步助手/images/b5a7cdaf49138131979d35594ac9ba5f_MD5.jpg]]

判断节点很简单：**通用工作流放全局，项目专属逻辑放项目级**。

比如“制作 PPT”这种可能每天都在做的事，放全局；“我这个特定 SaaS 项目里的某种特殊数据处理流程”，放项目级。

3-D Skills vs CLAUDE.md vs MCP

这三个概念是 Claude Code 最容易混的三个东西。讲清楚边界：

**CLAUDE.md** 是**菜谱**。Claude 进入项目就读，所有任务都会看一眼。

**Skills** 是**预制流程**。平时不动，触发条件一到自动跑。

**MCP** 是**外部工具接入**。要起服务、要登录、要拿能力，跟外部系统打交道时用。

真实差异是：

1\. CLAUDE.md **总是在场**，每次任务都会看。

2\. Skills **按触发条件激活**，平时不打扰。

3\. MCP **是外部能力接入**，不在 Claude 内部，而是把外部世界接进来。

![[笔记同步助手/images/ee10763631e8890aaaf02a4677690e65_MD5.jpg]]

**CLAUDE.md 总是在场，Skills 按需激活，MCP 接外部世界。**

3-E 装第一个 Skill：Superpowers

Superpowers 是社区里现在最成熟的一套通用 Skills 集合。装法：

●​●​●

/plugin marketplace add obra/superpowers-marketplace  
/plugin install superpowers@superpowers-marketplace

![[笔记同步助手/images/f4705cf1491ab73e15d5790f628a3dcb_MD5.jpg]]

装完之后，你会多出来一批子技能。我自己用得最多的三个：

**brainstorming**：你抛一个模糊需求，它反过来问你 5-8 个澄清问题，把任务边界、目标、约束、验收标准都问清楚。

**writing-plans**：把一个澄清过的需求，落成一份结构化的 plan.md。这份 plan 你能看懂、子代理也能看懂。

**dispatching-parallel-agents**：把一份 plan 拆给多个子代理并行跑。

Superpowers 解决的问题是把“**常见工作流**”打包好。

但你需要先理解每个子 skill 在做什么，**不要装完就放在那里**。

装完之后挨个试一遍，知道它各自适用什么场景，才能用得起来。

3-F 装第二个 Skill：MiniMax Skills

MiniMax Skills 提供了一组**生图、生视频、生 PPT、生 PDF**的能力，跟 Anthropic Skills 完全兼容，任何 Claude Code 客户端都能装。

安装方式跟 Superpowers 类似，通过 `/plugin marketplace add` 加入对应仓库。

●​●​●

claude plugin marketplace add https://github.com/MiniMax-AI/skills  
claude plugin install minimax-skills

![[笔记同步助手/images/d4340ff33e545b3c5a91d363bd28fa45_MD5.jpg]]

里面我比较常用的：

1\. **minimax-pdf**：把一份文档变成设计感不错的 PDF。

2\. **minimax-docx**：标准的文档制式，产出各种结构 word 文档。

3-G 造自己的 Skill：用 skill-creator

最后说一个最重要的：**自己造 Skill**。

Anthropic 官方插件市场里有一个叫 **skill-creator** 的 Skill，功能就是“帮你造 Skill”。它不是让你手写一堆配置，而是带着你一步步把一个 Skill 设计出来。

安装方式也很简单。

如果你的 Claude Code 里还没有官方插件市场，就先加上：

●​●​●

/plugin marketplace add anthropics/claude-plugins-official

然在 Claude Code 里输入：

●​●​●

/plugin install skill-creator@claude-plugins-official

安装完之后，让插件重新加载：

●​●​●

/reload-plugins

装好之后，在 Claude Code 里输入：

●​●​●

/skill-creator

选择 **Create** 模式，它会反过来问你：

1\. 这个 Skill 干什么？

2\. 触发条件是什么？

3\. 需要哪些步骤？

4\. 需要哪些参考资料？

5\. 输出形式是什么？

把问题答完，它直接帮你建好目录结构、写好 SKILL.md、生成脚本骨架、放好 reference 文档。

![[笔记同步助手/images/55d02ce3881b7c1564f120f6893ae24d_MD5.jpg]]

我自己最建议你先造的 Skill，是“**深度研究一个陌生领域**”。

因为这件事太高频了。老板突然提到一个新赛道，客户突然讲一个新概念，朋友圈刷到一个新趋势，你第一反应不是立刻写文章，而是先搞懂它到底是什么、为什么重要、谁在做、争议在哪、普通人该怎么入门。

这个 Skill 里可以封进去一整套研究流程：

1\. 先澄清研究目的：是为了工作汇报、投资判断、内容选题，还是个人学习。

2\. 再固定调研维度：定义、发展脉络、核心概念、代表玩家、商业模式、关键争议、入门资料。

3\. 再要求来源核验：重要判断必须给出处，数据、时间点、公司案例要能追溯。

4\. 再规定落盘结构：原始资料放 `research/raw-notes.md`，来源放 `research/sources.md`，报告放 `report/field-guide.md`。

5\. 最后输出一份小白能看懂的入门地图，而不是一堆搜索结果。

封完之后，下次你说“帮我深度研究一下具身智能 / 低空经济 / AI Agent 浏览器 / 某个新行业”，Claude Code 就会自动按这套流程跑：先问清楚用途，再搜资料，再核验来源，再把资料和报告落到工作区里。

这件事的意义比“省时间”大得多：**它把你理解陌生领域的方法，变成了一份可以被复用、被团队继承、被不断升级的研究资产**。

**写一个 Skill，就是在做一次知识结晶化。**

3-H Skills 的本质

至少在我能看到的范围里，Skills 这一层的真正价值，不是“功能扩展”，是：

**Skills 让个人经验变成可传承的资产。**

你过去十年攒下来的某种工作直觉、某种偏好、某种判断标准，在你没遇到 Skills 之前是装在你脑子里的。

除了你自己，没人能复用。

Skills 改变的是，**这些东西现在可以变成一份 Claude 能读懂的文件**，然后被你自己、被你的团队、甚至被陌生人激活。

到这一步，你已经知道怎么让 Claude Code 听话、记得住、有手艺。

## Part 4 工作流实战：让多个 Claude 替你协作完成一个项目

04

4-A 真实任务示例：Agent 工具横评 2026

为了把这一章讲透，我们用一个真实任务跑到底：

**Agent 工具横评 2026**。

任务大纲：**横评 5 个 2026 主流 Agent 工具**（Claude Code、Cursor、Codex、Devin、ChatGPT Atlas），从能力、价格、生态、稳定性、上手成本五个维度打分，产出一份**带封面 + 横评矩阵 + 推荐路径**的 PDF 报告。

这个任务的特点是：

第一，**信息密集**，要查很多公开资料。

第二，**对比性强**，需要结构化对齐。

第三，**最终交付物有设计要求**，不只是文本。

这是一个非常典型的“**单 Claude 干不漂亮、多 Claude 协作刚刚好**”的任务。

4-B 建工作区：用 IDE 打开项目文件夹

从这一章开始，就不要再把 Claude Code 当成“随便打开一个终端聊几句”的工具了。我们要跑的是一个真实项目，所以先给它一个干净的工作区。

打开桌面，新建一个文件夹：

●​●​●

agent-comparison-2026/

然后用 Trae / Cursor / VS Code 打开这个文件夹。菜单通常叫 **Open Folder / 打开文件夹**。

**这里我必须强调一遍**：Claude Code 不依赖 IDE，它本质上还是 CLI。但正式工作时，我强烈建议你在 IDE 里用它。

原因很实际：左边文件区能看到 Claude 生成了什么，中间编辑器能随时审内容，底部终端能跟 Claude Code 对话。

一个任务一个文件夹，一个文件夹一个工作区，你的计划、资料、报告和交付物就不会散在电脑各处。

启动之后，先 `/status` 看一眼，确认模型是 `deepseek-v4-pro[1m]`，环境变量加载正常。

4-C 三概念边界：Skills、MCP、子代理

在阶段 3 我们讲过 Skills、CLAUDE.md、MCP 三组关系。**到了多代理协作这一层，要再加一个概念：子代理**。

子代理是什么？**Claude 替你启动的另一个 Claude**。

每个子代理有自己独立的 Context、独立的任务、独立的工作目录，可以**并行多个一起跑**。

你不用管它们怎么沟通，主 Claude 会做调度。

类比一下，Skills 是岗位说明书，MCP 是外部能力接口，**子代理是你雇的临时帮手**。

更准确的说法是：

1\. **Skills 管流程**：这个任务该按什么 SOP 跑。

2\. **MCP 管连接**：这个任务要联什么外部世界。

3\. **子代理管分工**：这个任务该几个人一起干、谁干什么。

**Skills 管流程，MCP 管连接，子代理管分工。三个东西不是替代，是协作。**

![[笔记同步助手/images/765f963a2e411a30fb55d7d697d6c4de_MD5.jpg]]

4-D /brainstorming：澄清需求

第一步，在 Plan Mode 下激活 Superpowers 的 brainstorming：

●​●​●

/brainstorming  
我要做一份 2026 年 Agent 工具横评的报告。  
对象:Claude Code / Cursor / Codex / Devin / ChatGPT Atlas。  
最终交付物:一份带封面、横评矩阵、推荐路径的 PDF。  
帮我先把这个任务的细节澄清清楚。

![[笔记同步助手/images/cb8848dd1e50291ca7206530e3639d04_MD5.jpg]]

它会反过来问你 5-8 个问题，比如“评分维度具体是哪几个？”“读者是谁？”“报告语言？”“引用规范？”“你希望我用什么风格的封面？”“有没有篇幅要求？”“推荐路径要不要分场景？”

挨个回答。**这一步看起来在浪费时间，实际上是在替你把后面所有的返工预先消除掉**。

**好的工作流从澄清需求开始，而不是从动手开始。**

4-E /writing-plans：落计划

澄清完之后，接着：

●​●​●

/writing-plans  
按照刚才澄清的所有信息，在当前目录生成一份 plan.md。  
要求:plan.md 给我看和给子代理看都能看懂:  
有目标、有分工、有交付物、有验证标准。

它会产出一份 plan.md，大致结构：

●​●​●

\# Agent 工具横评 2026:项目计划  
\## 目标  
\[一句话目标\]  
\## 范围  
\- 评测对象:Claude Code / Cursor / Codex / Devin / ChatGPT Atlas  
\- 评分维度:能力 / 价格 / 生态 / 稳定性 / 上手成本  
\- 交付物:PDF 报告 + sources.md 引用列表  
\## 分工  
\- researcher:负责为每个工具收集公开资料、跑评分  
\- fact-checker:负责复核 researcher 的事实和引用  
\- report-writer:负责把所有信息整合成报告  
\## 验证标准  
\- 每个评分维度有至少 3 个独立来源  
\- 所有事实陈述都有可点击的来源链接  
\- 报告语言简洁，避免营销腔

**Plan 不是用来跑的，是用来对齐的**。你审一遍，觉得对了，再放它跑。

4-F /dispatching-parallel-agents：多代理协作

接着，激活多代理调度：

●​●​●

/dispatching-parallel-agents  
基于当前目录的 plan.md，启动三个子代理并行跑:  
子代理 1(researcher):  
负责对 plan.md 里的 5 个工具，每个工具按 5 个维度收集公开资料，  
把原始信息和来源链接写到 research/<tool-name>.md。​  
子代理 2(fact-checker):  
等 researcher 写完一个工具，你就复核它的事实和来源，  
有问题写到 issues.md，没问题加 ✓ 标记。​  
子代理 3(report-writer):  
等 fact-checker 复核完所有工具，你把 research/ 下的所有素材，  
按 plan.md 的报告结构整合到 report.md。​

提交之后，**主 Claude 会调度三个子代理依次或并行启动**。你能在终端里看到它们各自的工作日志。

这一段是整篇文章的最高潮：**因为这是 Claude Code 跟普通对话工具拉开数量级差距的地方**。

普通对话工具：你一个人坐在一个对话框里，所有问题都问同一个 AI，它一件一件给你回答。

Claude Code 多代理：三个子代理同时在你电脑上跑，researcher 那个终端在哗啦啦输出资料和链接、fact-checker 那个在挨条打勾、report-writer 那个在等前两个出活，你坐在中间像在看交易室。一屏多窗，各自在跑，你只看进度。

**你坐在调度位上。**

主 Claude 替你协调三个 Claude 干活：一个查资料、一个核事实、一个写报告。

**你不是程序员，你是问题的导演。**

4-G sources.md：留来源

researcher 每查到一条资料，**强制要求把出处链接写进 sources.md**。

这一步在 plan.md 里已经写死了：“所有事实陈述都有可点击的来源链接”。所以 researcher 在收集资料的时候，就会一边写一边更新 sources.md。

![[笔记同步助手/images/258036baff5e84a9883494d8bf376a47_MD5.jpg]]

为什么这一步关键？**因为可追溯性是这种调研类报告的底线**。哪天你的横评结论被人问“这个分数怎么来的”，你打开 sources.md，链接全在那里。

我做 AI 这些年看下来，**所有真正能立得住的产出，都有一份完整的 sources**。不留 sources 的报告，自己回头都不敢看。

4-H /minimax-pdf：生成 PDF

report.md 整合完之后，最后一步：产出 PDF。

●​●​●

/minimax-pdf  
把当前目录下的 report.md 转成一份 PDF。  
风格:专业横评报告，封面深色 + 大字标题。  
内页:浅色背景 + 衬线正文。  
所有矩阵图用网格化布局。

![[笔记同步助手/images/664622aa40430f2761ebdc973875204e_MD5.jpg]]

minimax-pdf 会调用 MiniMax 的设计能力，出一份带封面、有版式、可印刷的 PDF。

如果你没装 MiniMax Skills，也可以用社区里的其他 PDF 生成 Skill。

**核心不是“必须用某个 Skill”，是“PDF 这一步要有交付”**。

4-I 工作区文件树复盘

整个项目跑完之后，看看 IDE 左侧的工作区：

●​●​●

agent-comparison-2026/  
├── CLAUDE.md  
├── plan.md  
├── sources.md  
├── issues.md  
├── research/  
│ ├── claude-code.md  
│ ├── cursor.md  
│ ├── codex.md  
│ ├── devin.md  
│ └── chatgpt-atlas.md  
├── report.md  
└── report.pdf

![[笔记同步助手/images/5b768e144e78b188db96f3ec6d568c4e_MD5.jpg]]

**这棵树就是这个项目的全部历史**。

下次你要做“Agent 工具横评 2027”，**这棵树整个复用**。改 plan.md 里的对象、跑一遍同样的流水线，新报告产出。

**好的工作流不只产出交付物，还产出一个能被复用的工作区。**

## Part 5 工具不是门槛。一份给你的工作流方法论

05

5-A 五步工作流方法论

回头看 Part 4 我们刚才跑完的整个流程，**它能被抽象成五步**：

**澄清 → 计划 → 分工 → 落盘 → 交付。**

**澄清**：用 brainstorming，把模糊需求问清楚。

**计划**：用 writing-plans，把需求落成一份 plan.md。

**分工**：用 dispatching-parallel-agents，把活分给多个子代理。

**落盘**：每一步的输出都进文件、进 sources.md，可追溯、可复用。

**交付**：用合适的 Skill（minimax-pdf 或别的）产出最终交付物。

![[笔记同步助手/images/9cdad3a09da200746fecf70116e66b05_MD5.jpg]]

我管这个叫：**五步工作流**。

**先澄清，再计划，再分工，再落盘，再交付。五步，不止用在 Claude Code 上。**

你做任何复杂的协作项目（做一份调研、做一支视频、做一次发布、带一个团队跑一个 OKR）都能套这五步。

举个延伸场景。

我去年带一个 4 人小团队做产品改版，完全没碰 Claude Code，我也是按这五步跑的：周一开“澄清会”把模糊需求问透，周二落 plan 文档让团队都签字，周三分活到每个人手里，过程中所有产出落进同一个 Notion 库，周末一次性出交付。**那次复盘最大的发现是，这五步跟我现在在 Claude Code 里跑的工作流，本质是同一件事**。

只是协作对象从人变成了 Agent。

Claude Code 只是让你**把这五步搬进了 Agent 流水线**。

## 最后说说

06

Claude Code 为什么是现象级的产品。

因为它从来不是聊天工具，是你电脑里第一个真正的执行端。

**SOP 不再是规则，而是不用每次重新思考的快捷方式。**

**工具不是门槛，会用工具的人才是门槛。**

至少在我能看到的范围里。

**2026 年最重要的不是哪个模型最强，而是你能不能把工作搬进 Agent 流水线。**

以上，既然看到这里了，  
如果觉得不错，随手点个赞、在看、转发三连吧，  
如果想第一时间收到推送，也可以给我个星标⭐～  
谢谢你看我的文章

## 你的关注是我持续更新的动力～

**我是谁**

我是 AI大刘，北大毕业，大模型研究方向，腾讯犀牛鸟，先后在腾讯、百度的大模型研发部门，现在给多家国企做AI顾问（也期待大家和我咨询交流

欢迎链接我，期待您的加入～

---

![[笔记同步助手/images/4a40dd782050138115a52ac95effe8f0_MD5.jpg|cover_image]]

Original 大刘 爱AI的大刘

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/c947190e_1779180073806?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzIyNzQ3MDM3Mw%3D%3D%26mid%3D2247485373%26idx%3D1%26sn%3Deaef1ae649da8f5114887e2547cae1af%26chksm%3De9ab3d80ee08f31db9fac6ce83544ce2002e99c3efd2b5af954a93735c6fa678f0f42c242a34%26mpshare%3D1%26scene%3D1%26srcid%3D05195aiUrtsB73ANLWtq28CF%26sharer_shareinfo%3Df81b912c26235654da766f0cf1906fb8%26sharer_shareinfo_first%3Df81b912c26235654da766f0cf1906fb8%23rd&s=obsidian)