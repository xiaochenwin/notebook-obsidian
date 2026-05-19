---
author: AI新元
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzAxODcwMTEwMg==&mid=2456768665&idx=1&sn=085d4ca221c0505d17670ed5cb14c187&chksm=8d87654ba84e87bf0f354d7ba6304b2bef13e1a5ba8b33bfe0b6b754d8d9136b8c8af258782a&mpshare=1&scene=1&srcid=0519ZF3PRdjykSJoZxkXi1u5&sharer_shareinfo=f9c15cb050dc51f1b990465eb9509f52&sharer_shareinfo_first=f9c15cb050dc51f1b990465eb9509f52#rd
saved: 2026-05-19 16:46:46
tags:
  - 笔记同步助手
id: 118ca43a-05f1-4769-9847-f52d0091bfef
---

公众号名称：AI新元

作者名称：AI新元

发布时间：2026-05-16 22:22

～点个关注，文末有惊喜！～

很多人用 Obsidian 接入 Claude，第一个反应是：

先找插件。

于是装 AI 插件、搜索插件、同步插件、剪藏插件、自动化插件、发布插件……

最后插件越来越多，库却越来越乱。

笔记命名不统一，YAML 字段有的有、有的没有，文件夹结构全靠感觉。你问 Claude 一个问题，它回答得很泛；你让它整理资料，它又抓不住重点。

这时候很多人会以为：是不是 Claude 不够强？

其实不是。

真正的问题是：你的 Obsidian 库，还没有整理成 Claude 能使用的样子。

严格说，Claude 并不是一次性读懂你的整个笔记库。它需要通过搜索、索引、API、上下文召回等方式，拿到相关笔记片段，再基于这些内容回答你。所以，Obsidian + Claude 的关键，不是把插件堆满，而是先把笔记库变成一个可读取、可检索、可结构化、可回滚的系统。

这篇文章不做插件大全。

普通人想用好 Obsidian + Claude，先围绕 5 件事，把 10 个插件装对就够了：

1.  AI 接入
    
2.  结构化元数据
    
3.  资料捕获
    
4.  全文检索
    
5.  版本回滚
    

这 5 件事解决好了，Claude 才能真正帮你整理、写作、总结和思考。

01 为什么你装了很多插件，Claude 还是不好用？

因为插件多，不等于系统好。

Obsidian 本质上是一个基于本地 Markdown 文件的知识库。Claude 要使用你的笔记，最怕三件事：

第一，资料散。

一篇文章放在 \`文章/\`，一篇放在 \`临时/\`，一篇又放在 \`未整理/\`。你自己都找不到，Claude 更不可能稳定找到。

第二，结构乱。

有的笔记写 \`status: draft\`，有的写 \`状态: 草稿\`，有的根本没有状态字段。Dataview 查不出来，AI 也很难判断这篇笔记到底是素材、草稿、项目，还是成品。

第三，无法回滚。

你让 Claude 批量整理 100 篇笔记，结果它改坏了标题、删掉了段落、覆盖了原文。没有版本控制，你只能手动找回。

所以，Obsidian + Claude 最重要的不是“装更多插件”，而是搭一套最小可用系统。

这套系统要解决一个核心问题：

让你的笔记库变得足够稳定，Claude 才能安全、准确地使用它。

02 Obsidian + Claude 只需要先解决 5 件事

我建议先不要研究复杂的 MCP、Agent、自动化脚本。

先解决这 5 件事：

第一，AI 接入

让 Claude 能在 Obsidian 里参与写作、总结、问答，或者通过 API / MCP 访问你的笔记库。

第二，结构化元数据

让每篇笔记都有统一的类型、状态、标签、来源和创建时间。这样笔记就不只是文本，而是可查询的数据。

第三，资料捕获

让网页、想法、摘录、灵感能够低成本进入 Obsidian，而不是散落在浏览器、微信、备忘录和聊天记录里。

第四，全文检索

让你能快速找回旧内容。记得关键词时能搜到，不记得关键词时也能靠语义和字段筛选找回来。

第五，版本回滚

让 Claude 改错了也不怕。只要有历史记录，就敢让 AI 批量整理、重写和归档。

围绕这 5 件事，装下面 10 个插件就够了。

03 第一件事：AI 接入

插件 1：Smart Connections

Smart Connections 是 Obsidian + AI 的核心插件之一。

它的作用不是简单“聊天”，而是让你的笔记库参与 AI 对话。

它可以基于笔记内容建立关联，在你写作或提问时，把相关笔记召回出来，作为 AI 回答的上下文。官方介绍里也强调，它可以在写作时显示相关笔记，并把合适的笔记转成可复用上下文。(\[Smart Connections\]\[1\])

这解决了一个关键问题：

Claude 不再只是泛泛回答，而是能基于你自己的笔记回答。

比如你问：

我之前关于“专注力”的笔记里，有哪些可以发展成公众号文章？

如果你的库里有儿童教育、手机成瘾、深度工作、即时满足相关笔记，Smart Connections 就能帮助把这些内容关联起来。

安装建议：

在 Obsidian 第三方插件市场搜索：

```
Smart Connections
```

安装后，先完成基础模型配置，再建立索引。具体模型不要写死，因为插件支持能力和模型名称会变化，按插件当前设置页面来选即可。

插件 2：Text Generator

Smart Connections 更偏“召回和对话”，Text Generator 更偏“写作和生成”。

它适合在笔记内部做这些事：

\* 根据标题生成文章大纲；

\* 根据素材生成初稿；

\* 把草稿改写成公众号风格；

\* 把会议记录整理成纪要；

\* 用固定提示词模板批量处理笔记。

Text Generator 的项目说明中也写到，它可以在 Obsidian 中通过多种 AI provider 生成文本内容，包括 Anthropic、OpenAI、Google 和本地模型等。(\[GitHub\]\[2\])

最实用的是提示词模板。

比如你可以准备一个模板：

```
请把以下素材整理成微信公众号文章大纲。
要求：
1. 提炼核心观点；
2. 给出 5 个小标题；
3. 每个小标题下列出可展开的论点；
4. 保持口语化、实操感。
素材：
{{context}}
```

以后选中一段素材，就可以直接调用。

安装名称：

```
Text Generator
```

插件 3：Local REST API

前两个插件主要在 Obsidian 内部使用 AI。

Local REST API 解决的是另一个问题：

让外部工具访问你的 Obsidian 笔记库。

比如 Claude Desktop、MCP 客户端、脚本、自动化工具，都可以通过它读取、搜索、新建或修改你的笔记。

这就是进阶玩法的基础。

Local REST API 的官方项目说明里已经支持 MCP Server，并说明 MCP 地址通常在本机 \`https://127.0.0.1:27124/mcp/\`，需要用 API Key 作为 Bearer Token 认证；如果启用 HTTP endpoint，也可以使用本机 HTTP 地址。(\[GitHub\]\[3\])

这篇文章先不展开完整 MCP 配置，因为那会变成另一篇教程。

你现在只需要理解它的定位：

Smart Connections 让 Obsidian 内部更懂你的笔记；Local REST API 让外部 Claude 或自动化工具能访问你的笔记。

安装名称：

```
Local REST API
```

注意：安装后不要随便把服务暴露到公网或局域网，默认只在本机使用最安全。

04 第二件事：结构化元数据

AI 能不能用好你的库，很大程度取决于你的笔记是否结构化。

这里需要 3 个插件：

\* Dataview

\* Templater

\* Linter

插件 4：Dataview

Dataview 是 Obsidian 里非常重要的结构化查询插件。

它可以把你的 Markdown 笔记当成一个小型数据库，通过 YAML、标签、字段进行查询、筛选、排序和汇总。官方文档也把它定义为个人知识库上的 live index 和 query engine，可以基于元数据查询笔记。(\[黑匠Gus\]\[4\])

比如你给每篇笔记写上：

```
---
type: article
status: draft
topic: AI
created: 2026-05-16
---
```

你就可以用 Dataview 查询：

```
TABLE status, topic, created
FROM "outputs"
WHERE status = "draft"
SORT created DESC
```

这对 Claude 很重要。

因为它逼着你把笔记变成有结构的数据，而不是一堆随机文本。

建议统一这些基础字段：

```
---
type: note/article/source/project
status: raw/draft/review/final/archive
tags: []
source:
created:
updated:
---
```

字段不一定要多。

关键是：全库一致。

插件 5：Templater

Dataview 负责查询，Templater 负责让你每次新建笔记时，都按统一格式开始。

Templater 可以在模板中插入变量、函数结果，也支持执行 JavaScript 来自动化笔记创建。(\[silentvoid13.github.io\]\[5\])

比如你可以创建一个 \`article-template.md\`：

```
---
type: article
status: draft
tags: []
source:
created: <% tp.date.now("YYYY-MM-DD") %>
updated: <% tp.date.now("YYYY-MM-DD") %>
---
# <% tp.file.title %>
## 核心观点
## 文章结构
## 素材来源
## 待补充
```

以后新建公众号文章，不再从空白页开始，而是直接套结构。

这样做有两个好处：

第一，你自己写作更稳定。

第二，Claude 处理你的笔记时，也更容易判断每个部分的用途。

安装名称：

```
Templater
```

插件 6：Linter

Linter 很容易被误解成“美化格式”的插件。

其实在 Obsidian + Claude 组合里，它更像是质检员。

它可以帮你统一 YAML、标题层级、空行、列表、Markdown 格式等。Linter 官方文档也说明，它的目的就是让笔记保持更统一的模式，包括 YAML frontmatter、Markdown headings、spacing 等。(\[platers.github.io\]\[6\])

为什么这对 Claude 重要？

因为 AI 处理文本时，最怕格式不一致。

比如：

```
created: 2026-5-6
created: 2026/05/06
created_at: 2026-05-06
创建时间: 2026年5月6日
```

这些对人来说都能看懂，但对自动查询、批量整理、Dataview 统计来说，就是四套格式。

Linter 的作用就是把这些格式尽量拉齐。

建议先开启这些基础规则：

\* YAML 字段格式；

\* 标题层级不要跳级；

\* 删除多余空行；

\* 保存时自动整理。

但第一次使用时，不建议直接全库自动 Lint。先在测试文件夹试一轮，确认规则没问题，再逐步扩大范围。

安装名称：

```
Linter
```

05 第三件事：资料捕获

知识库不是靠整理出来的，而是靠持续捕获出来的。

你看到好文章，想到一个观点，读到一句话，听到一个案例，如果不能低成本进入 Obsidian，最后都会散落在各处。

这里装两个插件就够了。

插件 7：QuickAdd

QuickAdd 解决的是“快速输入”。

它可以帮你创建模板笔记、捕获文本到已有笔记、运行脚本，或者把多个动作组织成一个菜单。官方文档里也明确写到，它可以用一个快速命令完成模板、捕获、脚本和多步骤工作流。(\[quickadd.obsidian.guide\]\[7\])

最建议你先配置一个“每日捕获”。

比如目标文件：

```
Inbox/今日捕获.md
```

捕获格式：

```
- {{DATE:HH:mm}} {{VALUE}}
```

以后任何想法，直接快捷键呼出，输入一句话，回车。

不用纠结分类。

先捕获，再整理。

这非常适合配合 Claude。你可以每周让 Claude 帮你处理一次：

请把 Inbox/今日捕获.md 里的内容，按主题整理成文章选题、行动事项和资料线索。

安装名称：

```
QuickAdd
```

插件 8：Obsidian Web Clipper

Obsidian Web Clipper 解决的是“网页资料进入库”。

这是官方浏览器扩展，不是普通社区插件。它可以把网页、高亮和内容保存到你的 Obsidian vault，并且保存为 Markdown 文件。Obsidian 官方说明中也写到，Web Clipper 是免费的浏览器扩展，可以把网页内容保存到 vault；保存的内容会以 Markdown 文件形式保留。(\[Obsidian\]\[8\])

这比随手复制粘贴稳定很多。

建议你给网页剪藏设置一个固定目录：

```
raw/articles/
```

并尽量保留这些元数据：

```
---
type: source
source_type: article
source_url:
author:
captured_at:
status: raw
tags: []
---
```

这样后面 Claude 才能判断：

这是一篇原始资料，不是你的原创观点，也不是最终文章。

安装方式：

去浏览器扩展商店搜索：

```
Obsidian Web Clipper
```

Chrome、Edge、Brave 等 Chromium 浏览器都可以用。

06 第四件事：全文检索

有了资料，还要能找回来。

否则你的 Obsidian 只是一个更漂亮的文件夹。

插件 9：Omnisearch

Obsidian 自带搜索能用，但笔记一多，就会觉得不够顺手。

Omnisearch 的定位是更强的搜索引擎。官方社区插件页介绍它是一个 “just works” 的搜索引擎，支持笔记、PDF 和图片 OCR 等内容的智能搜索。(\[Obsidian Community\]\[9\])

它适合解决这种问题：

我记得以前写过“番茄钟”，但忘了放在哪个文件夹。

直接搜关键词，很快定位。

但这里要说清楚：

Obsidian + Claude 的检索，不是只靠一个插件。

更好的方式是三层一起用：

| 需求 | 用哪个插件 |
| --- | --- |
| 记得关键词 | Omnisearch |
| 不记得关键词，只记得主题 | Smart Connections |
| 按 status、type、tags、created 筛选 | Dataview |

比如：

你记得“番茄钟”这个词，用 Omnisearch。

你只记得“以前写过关于专注力的内容”，用 Smart Connections。

你想找“所有 status 是 draft，topic 是 AI 的文章”，用 Dataview。

这三层结合起来，你的 Obsidian 才真正从“存笔记”变成“可检索的知识库”。

安装名称：

```
Omnisearch
```

07 第五件事：版本回滚

只要你开始让 Claude 改笔记，就必须考虑回滚。

因为 AI 一定会改错。

不是可能，是一定。

它可能删掉你原来的表达，误改标题，整理错层级，甚至批量覆盖文件。

所以，在让 Claude 深度参与 Obsidian 之前，一定要先装版本控制。

插件 10：Obsidian Git

Obsidian Git 可以把 Git 版本控制集成到 Obsidian vault 里，支持自动 commit、pull、push 和查看变更。社区插件页也说明，它可以在 Obsidian 内进行 Git 集成，并支持自动备份等高级功能。(\[Obsidian Community\]\[10\])

它解决的是最后一道安全问题：

Claude 改错了，我能不能回到昨天？

建议配置：

```
自动提交间隔：15 或 30 分钟
提交信息：vault backup: {{date}}
远程仓库：私有仓库
```

如果你暂时不想用 GitHub，也可以先只做本地 Git。

最低限度，在 vault 根目录运行：

```
git init
```

然后让 Obsidian Git 定期提交。

这样你每次让 Claude 批量整理前，都可以先提交一次：

```
before claude refactor
```

出问题就回滚。

安装名称：

```
Git
```

注意：在 Obsidian 社区插件里通常搜索 Git，它对应的项目常被称为 Obsidian Git。

08 推荐安装顺序

如果你是第一次搭建 Obsidian + Claude，不建议 10 个一起装。

按这个顺序来：

第一步：先装安全兜底

```
Obsidian Git
```

先保证能回滚。

没有回滚，不要让 Claude 批量改笔记。

第二步：再装结构化插件

```
Dataview
Templater
Linter
```

先统一笔记结构。

这一层决定你的库是不是“AI 可读”。

第三步：装资料捕获插件

```
QuickAdd
Obsidian Web Clipper
```

让想法、网页、素材稳定进入库。

不要等资料散落一堆之后再整理。

第四步：装检索插件

```
Omnisearch
Smart Connections
```

一个负责关键词搜索，一个负责语义关联。

第五步：最后装 AI 写作和外部访问插件

```
Text Generator
Local REST API
```

Text Generator 用来在 Obsidian 内写作和改写。

Local REST API 用来给 Claude Desktop、MCP 或其他工具访问 Obsidian。

这个顺序的逻辑很简单：

先备份，再结构化，再捕获，再检索，最后接入 AI。

不要反过来。

很多人一上来就接 Claude，结果库没结构、没备份、没检索，最后 AI 只会制造更多混乱。

09 安全边界

Obsidian + Claude 很强，但一定要有边界。

尤其是 Local REST API、Text Generator、Smart Connections、Obsidian Git 这些插件，都会涉及笔记内容、API Key、外部模型、远程仓库或本地接口。

建议记住 5 条：

1\. 不要把敏感资料放进 AI 可读目录

比如：

```
private/
contracts/
credentials/
secrets/
客户资料/
账号密码/
```

这些目录最好不要让 AI 插件读取，也不要进入自动处理流程。

2\. API Key 不要写进笔记

不要把 Claude、OpenAI、Gemini、Local REST API 的 Key 写进 Markdown 笔记、模板、文章草稿或 Git 仓库。

3\. Local REST API 只在本机使用

尽量保持：

```
127.0.0.1
localhost
```

不要为了方便，把接口暴露到公网或公司局域网。

4\. Git 远程仓库必须私有

如果你要同步到 GitHub、Gitee 或其他远程仓库，优先使用私有仓库。

并且 \`.gitignore\` 至少加上：

```
private/
secrets/
credentials/
.env
*.key
*.pem
*.p12
*.pfx
```

5\. Claude 批量修改前，先手动提交一次

每次让 Claude 批量整理、改名、重写、迁移文件之前，先提交一次：

```
before claude batch edit
```

这样出错了，可以立刻回滚。

AI 很适合加速，但不要把安全边界交给 AI 自己判断。

10 三个问题自查：你的库够不够让 Claude 使用？

装完插件，不代表系统就好了。

你可以用 3 个问题自查。

问题 1：我能用 Dataview 找出所有草稿吗？

比如：

```
TABLE type, status, created
FROM ""
WHERE status = "draft"
SORT created DESC
```

如果查不出来，说明你的 YAML 还不统一。

问题 2：我随机打开 10 篇笔记，字段格式是否一致？

比如是否都有：

```
type:
status:
tags:
created:
source:
```

如果每篇都不一样，Claude 处理时就会混乱。

问题 3：Claude 改坏文件后，我能不能回滚？

如果不能，就先别让 Claude 大规模改库。

三分都能做到，说明你的 Obsidian 已经具备和 Claude 协作的基础。

两分，说明系统初步成型，但还要补结构和备份。

一分以下，先不要折腾复杂自动化。先花几天把模板、字段、目录和 Git 整理好。

顺序不能反。

![[笔记同步助手/images/5714267a67b60eb7e23353507e4f9501_MD5.png]]

如果这篇内容对你有帮助，欢迎点赞、在看并转发给更多需要的朋友。

你的每一次互动，都是我持续更新的动力。想第一时间获取后续内容，欢迎关注。

---

![[笔记同步助手/images/5b28f77b723564de0c247b86e624cbb4_MD5.jpg|cover_image]]

原创 AI新元 AI新元

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/2d1f04c6_1779180404687?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzAxODcwMTEwMg%3D%3D%26mid%3D2456768665%26idx%3D1%26sn%3D085d4ca221c0505d17670ed5cb14c187%26chksm%3D8d87654ba84e87bf0f354d7ba6304b2bef13e1a5ba8b33bfe0b6b754d8d9136b8c8af258782a%26mpshare%3D1%26scene%3D1%26srcid%3D0519ZF3PRdjykSJoZxkXi1u5%26sharer_shareinfo%3Df9c15cb050dc51f1b990465eb9509f52%26sharer_shareinfo_first%3Df9c15cb050dc51f1b990465eb9509f52%23rd&s=obsidian)