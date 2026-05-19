---
author: vayne-LW
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU0NDE2NDU1NA==&mid=2247483696&idx=1&sn=0a06340a772e1f07a4ca26be712acc71&chksm=fa0b316e0fdef6783e006579c0b9702d14c8bbcb19bdacf4f6d69a92bfa735e776e5e06e289d&mpshare=1&scene=1&srcid=0519J0jAQ7TyH2gPMxRcjPQj&sharer_shareinfo=a6549298ab47dbaa4c2cd5aad953a01e&sharer_shareinfo_first=a6549298ab47dbaa4c2cd5aad953a01e#rd
saved: 2026-05-19 08:39:51
tags:
  - 笔记同步助手
id: 81362b0b-b6d3-4db7-914d-be584a00b1d9
---

公众号名称：manisfast

作者名称：vayne-LW

发布时间：2026-04-27 21:06

> 从信息碎片到结构化知识库，一篇文章带你从零搭建属于自己的"第二大脑"

---

## 前言

你是否经历过这样的场景：浏览网页时看到一篇好文章，随手收藏后就再也没打开过？或者读书时记了大量笔记，但需要用到时却怎么也找不到？

信息时代，我们缺的不是信息，而是把信息转化为知识的能力。

今天，我要介绍一套完整的知识管理方案，它能帮你：

-   **快速采集**：一键抓取网页内容到本地
    
-   **自动结构化**：让 AI 把零散笔记整理成互相关联的知识条目
    
-   **随时问答**：在笔记软件里直接向 AI 提问，基于你的知识库获得回答
    

这套方案的核心工具组合是：

| 工具 | 作用 |
| --- | --- |
| **Obsidian** | Markdown 笔记应用，知识库的"容器" |
| **Obsidian Web Clipper** | 浏览器插件，一键抓取网页到 Obsidian |
| **Claude Code** | 命令行 AI 工具，执行知识结构化 |
| **Claudian 插件** | 在 Obsidian 内直接调用 AI 进行问答 |

而这套方案的知识组织理念，来自 AI 领域大牛 Andrej Karpathy 提出的 **LLM Wiki** 模式。

下面，我们从零开始，一步步搭建这个系统。

---

## 一、系统架构：LLM Wiki 是什么？

在动手之前，先理解这个系统的核心理念。

Andrej Karpathy（OpenAI 联合创始人、前特斯拉 AI 总监）提出了一个优雅的知识管理思路：**让大语言模型像维基百科编辑一样，持续维护和更新你的个人知识库**。

这个系统的核心架构分为三层：

```
📂 你的知识库（Obsidian Vault）
├── 📁 raw/              ← 第一层：原始素材（只读，不可修改）
│   ├── 文章1.md
│   ├── 文章2.md
│   └── ...
├── 📁 wiki/             ← 第二层：结构化知识（AI 生成和维护）
│   ├── index.md         ← 内容总目录
│   ├── log.md           ← 变更日志
│   ├── 主题A.md
│   ├── 主题B.md
│   └── ...
└── 📄 CLAUDE.md         ← 第三层：规则文件（告诉 AI 该怎么做）
```

**三层各自的职责：**

1.  **Raw（原始素材层）**：你从网页、书籍、文章中收集的原始内容，存放在这里后不再修改。这是知识的"源头"。
    
2.  **Wiki（知识层）**：AI 阅读你的原始素材后，生成结构化的、互相链接的知识条目。每当你添加新素材，AI 会增量更新相关的知识条目——就像维基百科编辑看到新资料会更新相关词条一样。
    
3.  **Schema（规则层）**：一个 `CLAUDE.md` 文件，定义了 AI 应该如何组织知识、使用什么格式、遵循什么规则。
    

**关键操作只有三个：**

| 操作 | 说明 |
| --- | --- |
| **Ingest（摄入）** | 添加新素材后，AI 阅读并更新相关 wiki 条目 |
| **Query（查询）** | 向 AI 提问，AI 搜索知识库并综合回答 |
| **Lint（检查）** | AI 检查知识库的一致性，找出矛盾、过时或孤立条目 |

这就是全部。不需要向量数据库，不需要复杂的 RAG 管道，只需要 Markdown 文件和一个够聪明的 AI。

理解了这个架构，下面我们开始搭建。

---

## 二、安装 Obsidian 并创建知识库

### 2.1 下载安装 Obsidian

Obsidian 是一款免费的个人 Markdown 笔记应用，所有数据都以 `.md` 文件存储在本地，你完全掌控自己的数据。

打开 Obsidian 官网下载页面：

```
https://obsidian.md/download
```

选择 macOS 版本下载，下载完成后将 Obsidian 拖入"应用程序"文件夹。

![[笔记同步助手/images/bc6353037ce19903e42705b3b79bd7fb_MD5.png]]

### 2.2 创建 Vault（知识库）

首次打开 Obsidian，会看到欢迎界面。点击"创建新库"（Create new vault），选择一个存放位置；或者点击“Open folder as vault”（事先用`mkdir ～/Documents/MyWiki`创建好空目录）

建议将知识库放在一个容易找到的路径，比如：

```
～/Documents/MyWiki
```

  

  

创建完成后，你会进入一个空的 Obsidian 界面。这就是你的知识库了，现在它还是空的，我们接下来往里面添加内容。

![[笔记同步助手/images/c21836239a009bc5824a3dec4d6282ff_MD5.png]]

### 2.3 初始化目录结构

打开终端（Terminal），执行以下命令创建 LLM Wiki 所需的目录结构：

```
# 进入你的知识库目录（请替换为实际路径）
cd ～/Documents/MyWiki

# 创建目录结构
mkdir -p raw wiki
```

创建完成后，你的知识库结构如下：

```
MyWiki/
├── raw/      ← 原始素材存放处
└── wiki/     ← 结构化知识存放处
```

  

![[笔记同步助手/images/0131a00582e275a27670272dc8b85398_MD5.png]]

  

---

## 三、安装 Obsidian Web Clipper（网页剪藏）

在知识管理的工作流中，第一步是**采集信息**。Obsidian Web Clipper 是 Obsidian 官方提供的浏览器扩展，可以一键将网页内容甚至是youtube视频字幕！！！保存为 Markdown 文件到你的知识库中。

### 3.1 安装浏览器扩展

根据你使用的浏览器，选择对应的安装方式：

**Chrome / Edge 用户：**

打开 Chrome Web Store 搜索"Obsidian Web Clipper"，或直接访问：

```
https://chromewebstore.google.com/detail/obsidian-web-clipper/hoolglpddlnpcljhifenmeljncjmdkjn
```

点击"添加到 Chrome"。

![[笔记同步助手/images/7de0b938299fd8637c2feca0a7b6e3d1_MD5.png]]

![[笔记同步助手/images/f551c1fe04aa382d830bdf39cc9ba1b2_MD5.png]]

**Safari 用户：**

在 Mac App Store 搜索"Obsidian Web Clipper"安装。

### 3.2 配置 Web Clipper

安装完成后，点击浏览器工具栏中的 Obsidian 图标，进行初始配置：

1.  **Vault 路径**：指向你的 Obsidian 知识库路径，如 `～/Documents/MyWiki`
    
2.  **保存位置**：设置默认保存到 `raw/` 文件夹——这很重要！所有从网页抓取的内容都应该作为原始素材存放在 raw 目录中
    
3.  **文件名格式**：可以设置为 `{{title}}`，即使用网页标题作为文件名
    

  

![[笔记同步助手/images/63d4203f6f44650c635cc22f33fee7e1_MD5.png]]

![[笔记同步助手/images/2e0dd82bed75d384857b75e7fdecabe0_MD5.png]]

  

  

### 3.3 试试剪藏

现在打开一篇你想收藏的网页文章，点击浏览器工具栏的 Obsidian Web Clipper 图标，选择"Clip as Markdown"，内容就会被保存到你的 `raw/` 文件夹中。

回到 Obsidian，你应该能在左侧的 `raw` 文件夹中看到刚保存的文件。

  

  

> **提示**：Karpathy 在他的 LLM Wiki 中建议，如果原始素材中有重要图片，最好将图片下载到本地保存（比如放在 `raw/images/` 目录），这样可以避免因图片链接失效导致内容丢失。

---

## 四、安装 Claude Code

Claude Code 是 Anthropic 官方推出的命令行 AI 工具，它是我们实现知识结构化的"引擎"。本节简要介绍安装步骤，更多细节请参考官方文档。

### 4.1 前置要求：安装 Node.js

Claude Code 基于 Node.js，推荐使用 Homebrew 安装：

```
# 安装 Node.js
brew install node
```

验证安装：

```
node --version   # 应输出 v20.x.x 或更高
npm --version    # 应输出 10.x.x 或更高
```

### 4.2 安装 Claude Code

由于国内网络原因，建议使用 npm 镜像源安装：

```
npm install -g @anthropic-ai/claude-code --registry=https://registry.npmmirror.com
```

> **常见问题**：如果安装后运行 `claude` 提示 `Error: claude native binary not installed`，说明平台二进制文件缺失，需要手动补装：

```
# 安装 macOS 平台二进制包
npm install -g @anthropic-ai/claude-code-darwin-x64 --registry=https://registry.npmjs.org

# 找到你的 Node.js 全局模块路径，将二进制文件链接到主程序预期位置
# 以下路径需替换为你实际的 node 版本号和用户目录
mkdir -p /Users/你的用户名/.nvm/versions/node/v24.x.x/lib/node_modules/@anthropic-ai/claude-code/bin
ln -f /Users/你的用户名/.nvm/versions/node/v24.x.x/lib/node_modules/@anthropic-ai/claude-code-darwin-x64/claude /Users/你的用户名/.nvm/versions/node/v24.x.x/lib/node_modules/@anthropic-ai/claude-code/bin/claude.exe
chmod +x /Users/你的用户名/.nvm/versions/node/v24.x.x/lib/node_modules/@anthropic-ai/claude-code/bin/claude.exe
```

安装完成后验证：

```
claude --version
```

### 4.3 配置 API（使用 cc-switch）

Claude Code 默认使用 Anthropic API，但国内用户可能更希望使用国内大模型的 API。推荐使用 **cc-switch** 工具来切换模型供应商。

**步骤 1：下载 cc-switch**

访问 GitHub Release 页面下载 macOS 版本：

```
https://github.com/farion1231/cc-switch/releases
```

**步骤 2：配置模型供应商**

以智谱 GLM 为例：

| 配置项 | 填写内容 |
| --- | --- |
| 供应商名称 | Zhipu GLM |
| 官网链接 | https://open.bigmodel.cn |
| API 请求地址 | https://open.bigmodel.cn/api/anthropic |

前往 https://open.bigmodel.cn 注册并获取 API Key。

> **提示**：你也可以使用其他兼容 Anthropic API 格式的模型供应商，如 OpenAI 等，在 cc-switch 中配置对应的 API 请求地址和密钥即可。

### 4.4 首次启动 Claude Code

进入你的知识库目录，启动 Claude Code：

```
cd ～/Documents/MyWiki
claude
```

首次启动时，Claude Code 会要求你确认工作目录并接受使用条款。完成后你将看到 Claude Code 的交互界面。

输入 `/exit` 可以退出 Claude Code。

---

## 五、配置知识结构化提示词（CLAUDE.md）

现在到了最关键的一步：**告诉 AI 如何组织你的知识**。

在 LLM Wiki 模式中，`CLAUDE.md` 就是给 AI 的"操作手册"。当你在知识库目录下启动 Claude Code 时，它会自动读取这个文件作为工作指引。

### 5.1 创建 CLAUDE.md

在知识库根目录创建 `CLAUDE.md` 文件：

```
cd ～/Documents/MyWiki
touch CLAUDE.md
```

然后在 Obsidian 中打开这个文件进行编辑（也可以用任何文本编辑器）。

### 5.2 编写结构化规则

以下是一个参考模板，基于 Karpathy 的 LLM Wiki 理念，你可以根据自己的需求调整。

将以下内容**完整复制**到你的 `CLAUDE.md` 文件中：

> **提示**：在 Obsidian 中点击右上角的编辑按钮进入编辑模式，粘贴后保存即可。

```
# 知识库规则

## 身份
你是一个个人知识库的管理助手。你的任务是阅读原始素材，并将其转化为结构化、互相链接的知识条目。

## 目录结构
- `raw/`：原始素材，只读，永远不要修改
- `wiki/`：结构化知识条目，由你负责创建和更新
- `CLAUDE.md`：本规则文件

## 核心操作

### Ingest（摄入）
当我说"摄入 [文件名]"时：
1. 阅读 `raw/` 中指定的原始素材
2. 提取其中的关键概念、事实和见解
3. 更新 `wiki/` 中已有的相关条目，或创建新条目
4. 在条目之间建立双向链接 `[[]]`
5. 更新 `wiki/index.md` 内容目录
6. 在 `wiki/log.md` 中追加变更记录

### Query（查询）
当我提出问题时：
1. 搜索 `wiki/` 中所有相关条目
2. 综合多个条目的信息，给出完整的回答
3. 如果发现知识缺口，建议需要补充的素材

### Lint（检查）
当我说"检查知识库"时：
1. 检查各条目之间是否存在矛盾
2. 找出孤立的（没有其他条目链接到的）条目
3. 标记可能过时的信息
4. 报告发现的问题和建议

## 知识条目格式
每个 wiki 条目应遵循以下格式：

    ---
    created: YYYY-MM-DD
    updated: YYYY-MM-DD
    sources: [来源文件列表]
    tags: [相关标签]
    ---

    # 条目标题

    一句话概述这个概念。

    ## 详细说明

    正文内容...

    ## 相关条目
    - [[相关条目A]]
    - [[相关条目B]]

## index.md 格式
内容目录应列出所有 wiki 条目及其一句话摘要：

    ## 知识条目索引

    - [[条目A]]：一句话描述
    - [[条目B]]：一句话描述

## log.md 格式
变更日志按时间倒序排列：

    ## [YYYY-MM-DD] ingest | 来源标题
    - 新增：[[条目X]]
    - 更新：[[条目Y]]（新增关于...的内容）

## 重要原则
1. 永远不要修改 `raw/` 中的原始素材
2. 知识条目要简洁，用你自己的话总结，不要照搬原文
3. 积极建立条目之间的链接，形成知识网络
4. 每次摄入新素材时，要增量更新已有条目，而不是重新创建
5. 保持客观，标注信息来源
```

  

![[笔记同步助手/images/42b13a37b99c0fe2e6c091834d8fe975_MD5.png]]

  

  

> **进阶推荐**：上面是一个简化的入门版 CLAUDE.md。强烈建议使用大神的！！！如果你想参考 Karpathy 本人编写的完整版提示词，可以查看他的 Gist：llm-wiki CLAUDE.md。他的版本包含更丰富的知识条目格式规范、lint 规则和错误恢复策略，适合在熟悉基本流程后进阶使用。

### 5.3 初始化 index.md 和 log.md

在 `wiki/` 目录中创建这两个核心文件：

```
cd ～/Documents/MyWiki/wiki
touch index.md log.md
```

在 `wiki/index.md` 中写入初始内容：

```
# 知识条目索引

> 此目录由 AI 自动维护，记录所有知识条目及其摘要。

（暂无条目）
```

在 `wiki/log.md` 中写入初始内容：

```
# 变更日志

> 记录知识库的所有变更。

（暂无记录）
```

  

![[笔记同步助手/images/b9a13908f5b2d9aec0f12b1136c46feb_MD5.png]]

  

---

## 六、使用 Claude Code 进行知识结构化

现在系统已经搭建好了，让我们实际操作一次完整的知识结构化流程。

### 6.1 准备素材

假设你通过 Web Clipper 抓取了几篇关于"大语言模型"的文章，它们都保存在 `raw/` 文件夹中。

### 6.2 启动 Claude Code 并执行摄入

```
cd ～/Documents/MyWiki
claude
```

进入 Claude Code 交互界面后，输入指令：

```
请摄入 raw/ 文件夹中的所有素材，按照 CLAUDE.md 中的规则进行知识结构化。
```

Claude Code 会：

1.  读取 `CLAUDE.md` 了解工作规则
    
2.  扫描 `raw/` 中的所有文件
    
3.  阅读每篇素材，提取关键知识
    
4.  在 `wiki/` 中创建知识条目
    
5.  在条目之间建立双向链接
    
6.  更新 `index.md` 和 `log.md`
    

  

![[笔记同步助手/images/14bce522d4da9c330e3214119ae02643_MD5.png]]

  

### 6.3 查看结果

回到 Obsidian，你会发现 `wiki/` 文件夹中多了好几个文件：

```
wiki/
├── index.md          ← 内容目录
├── log.md            ← 变更日志
├── 大语言模型概述.md   ← 知识条目
├── Transformer架构.md ← 知识条目
├── 注意力机制.md      ← 知识条目
└── ...
```

打开任意一个条目，你会看到 AI 整理好的结构化内容，包含概述、详细说明，以及指向其他相关条目的链接。

  

![[笔记同步助手/images/c734a4ee420d8ade5ce88aa30f9aaa2f_MD5.png]]

  

### 6.4 使用 Obsidian 图谱视图

Obsidian 有一个非常强大的功能——**图谱视图（Graph View）**。点击左侧边栏的图谱图标，你可以看到所有知识条目之间的链接关系，形成一个直观的知识网络。

Karpathy 特别推荐了这个功能——当你的知识库逐渐丰富时，图谱视图会呈现出美丽的知识结构图。

  

![[笔记同步助手/images/d1ea1b2954be31c914d1539c773f1886_MD5.png]]

  

### 6.5 后续增量更新

当你通过 Web Clipper 添加了新的素材后，再次在 Claude Code 中执行摄入：

```
请摄入 raw/ 中新增的素材，增量更新 wiki 知识库。
```

AI 会只处理新添加的素材，并增量更新已有的知识条目，而不是推倒重来。

### 6.6 向 AI 提问

你还可以直接在 Claude Code 中提问：

```
请根据知识库中的内容，解释 Transformer 中的自注意力机制是什么。
```

AI 会搜索 `wiki/` 中的相关条目，综合后给出回答。

### 6.7 检查知识库健康

定期运行检查：

```
请检查知识库，找出矛盾、过时或孤立的条目。
```

AI 会审视整个知识库并报告问题。

---

## 七、安装 Claudian 插件（在 Obsidian 内使用 AI）

到目前为止，我们已经可以在命令行中使用 Claude Code 进行知识结构化。但如果你想在 Obsidian 内直接和 AI 对话，不用切换到终端，那就需要 **Claudian** 插件。

Claudian 是一个第三方 Obsidian 插件，它将 Claude Code 的能力直接嵌入到 Obsidian 中。

### 7.1 前置要求

-   ✅ 已安装 Claude Code（上一节已完成）
    
-   ✅ 已配置 API Key（上一节已完成）
    
-   ✅ Obsidian v1.4.5 或更高版本
    
-   ⚠️ Claudian 仅支持桌面端（macOS / Linux / Windows）
    

### 7.2 方法一：通过 GitHub Release 安装（推荐）

**步骤 1：下载插件文件**

访问 Claudian 的 GitHub Release 页面：

```
https://github.com/YishenTu/claudian/releases
```

下载最新版本的以下三个文件：

-   `main.js`
    
-   `manifest.json`
    
-   `styles.css`
    

  

![[笔记同步助手/images/adabf6a96b9df53ac7b3049382f05262_MD5.png]]

  

**步骤 2：创建插件目录并放入文件**

```
# 在你的知识库中创建 claudian 插件目录
mkdir -p ～/Documents/MyWiki/.obsidian/plugins/claudian

# 将下载的文件移动到该目录
# 假设文件下载到了 ～/Downloads/ 目录
mv ～/Downloads/main.js ～/Documents/MyWiki/.obsidian/plugins/claudian/
mv ～/Downloads/manifest.json ～/Documents/MyWiki/.obsidian/plugins/claudian/
mv ～/Downloads/styles.css ～/Documents/MyWiki/.obsidian/plugins/claudian/
```

**步骤 3：在 Obsidian 中启用插件**

1.  打开 Obsidian，进入"偏好"（Preference）
    
2.  在左侧找到"第三方插件"（Community plugins）
    
3.  如果是首次使用第三方插件，需要点击"关闭安全模式"（Turn off restricted mode）
    
4.  在已安装插件列表中找到"claudian"，打开开关启用它
    
5.  点击“Browse”，可以探索其他第三方插件
    

  

![[笔记同步助手/images/944b5435d9238d07c429031760a52072_MD5.jpg]]

  

  

![[笔记同步助手/images/2d85dc2ca52be02fbee6e2f79caa03c4_MD5.png]]

  

![[笔记同步助手/images/eab9766565ba31dd33f08d5d28bed19a_MD5.png]]

注意：建议用claude的api，或者openai的api，目前claudian支持的是claude和gpt的api，可以用claude code协助安装codex cli，会默认加载。

## 八、使用 Claudian 在 Obsidian 中进行 AI 问答

### 8.1 打开 Claudian 侧边栏

插件启用后，Obsidian 界面会出现 Claudian 的图标（通常在左侧边栏或右侧面板）。点击它即可打开 AI 对话界面。

![[笔记同步助手/images/00470382cee2541b4e18eb26febd30f5_MD5.png]]

  

### 8.2 开始对话

在 Claudian 的输入框中，你可以直接输入问题。因为 Claudian 嵌入的是 Claude Code，它能直接读取和操作你的知识库文件。

**使用场景示例：**

```
请帮我总结 raw/ 中关于机器学习的所有文章要点
```

```
阅读 wiki/ 中的所有条目，找出关于"神经网络"的知识缺口
```

```
根据知识库中的内容，解释强化学习和监督学习的区别
```

  

### 8.3 高级功能

Claudian 还提供了一些强大的功能：

**Slash Commands（斜杠命令）**

在对话中输入 `/` 可以呼出快捷命令菜单，快速执行常用操作。

![[笔记同步助手/images/35482884c3ab97fc0e1bb617c9a53c48_MD5.png]]

**@mention（引用文件）**

在对话中使用 `@` 可以引用知识库中的特定文件，让 AI 专注于处理该文件。

![[笔记同步助手/images/511d7723cb6224b1273e8cd34035a44c_MD5.png]]

**Plan Mode（规划模式）**

按 `Shift+Tab` 切换到规划模式，AI 会先制定计划再执行操作，适合复杂的批量处理。

![[笔记同步助手/images/76185dd059772dd46c1fc68e4a7ca499_MD5.png]]

---

## 九、自定义你的知识结构化提示词

Karpathy 的 LLM Wiki 提示词是一个参考模板。每个人都有自己的知识管理需求，你应该根据自己的使用场景来定制 `CLAUDE.md`。

### 9.1 调整知识条目分类

比如，如果你是一名产品经理，你的知识库可能需要这样的分类：

```
## 知识条目分类

- **概念定义**：解释一个核心概念
- **案例分析**：记录真实案例及其分析
- **方法论**：可复用的方法论或框架
- **经验教训**：从实践中总结的经验
```

### 9.2 添加领域特定规则

```
## 领域规则

- 技术文章要提取：技术栈、架构图、性能指标
- 产品文章要提取：用户场景、问题定义、解决方案、数据指标
- 商业文章要提取：商业模式、竞争格局、关键数据
```

### 9.3 设置知识条目模板

你可以为不同类型的知识定义不同的模板：

```
## 技术概念模板

    ---
    created: YYYY-MM-DD
    updated: YYYY-MM-DD
    type: 技术概念
    sources: [来源]
    tags: [标签]
    ---

    # 概念名称

    ## 一句话解释
    > 用最通俗的话解释这个概念。

    ## 核心原理
    技术原理的详细说明...

    ## 应用场景
    这个技术用在哪里...

    ## 优缺点
    - 优点：...
    - 缺点：...

    ## 相关条目
    - [[相关技术A]]
    - [[相关技术B]]
```

### 9.4 让提示词持续进化

你的 `CLAUDE.md` 不是一成不变的。随着你对知识管理需求的深入理解，持续优化你的提示词。你可以：

-   当发现 AI 生成的条目不够好时，在规则中添加更明确的要求
    
-   当发现新的知识分类需求时，更新分类体系
    
-   当发现某些操作流程可以优化时，调整操作指令
    

**记住：好的提示词是迭代出来的，不是一次写就的。**

---

## 十、完整工作流总结

让我们把整个流程串起来，你的日常工作流如下：

```
┌─────────────────────────────────────────────────────────┐
│                    日常工作流                             │
│                                                         │
│  1. 浏览网页 → Web Clipper 一键保存到 raw/               │
│                     ↓                                    │
│  2. Claude Code / Claudian 执行"摄入"                    │
│     → AI 阅读 raw/ 中的新素材                            │
│     → 更新 wiki/ 中的知识条目                             │
│     → 更新 index.md 和 log.md                            │
│                     ↓                                    │
│  3. 在 Obsidian 中浏览结构化知识                          │
│     → 阅读知识条目                                       │
│     → 通过图谱视图探索知识关联                            │
│     → 通过 [[]] 双向链接在条目间跳转                     │
│                     ↓                                    │
│  4. 需要查找信息时                                       │
│     → 在 Claudian 中提问                                 │
│     → AI 基于知识库给出综合回答                           │
│                     ↓                                    │
│  5. 定期运行"检查"维护知识库健康                          │
│     → AI 检查矛盾、过时、孤立条目                        │
│     → 根据报告修复或更新                                 │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 十一、进阶项目推荐

掌握了基本的 LLM Wiki 工作流后，如果你想尝试更强大的工具，社区中已经有不少基于这套理论开发的开源项目。以下推荐三个高星项目：

### 11.1 llm\_wiki — 桌面端知识图谱应用

nashsu/llm\_wiki 是一个跨平台桌面应用，基于 Tauri v2 构建，在 LLM Wiki 理论基础上做了大量增强：

-   **两步思维链摄入**：先用 LLM 生成结构化摘要，再提炼知识图谱节点和关系
    
-   **四信号知识图谱**：节点大小、颜色、位置、连线粗细分别承载不同语义
    
-   **Louvain 社区发现**：自动识别知识集群，发现隐藏的主题关联
    
-   **向量语义搜索**：基于 LanceDB 实现语义检索，不只是关键词匹配
    
-   **Chrome 剪藏扩展**：浏览器中一键保存网页到知识库
    

**安装方式**（二选一）：

1.  **直接下载**：前往 Releases 页面 下载对应平台的安装包（macOS `.dmg` / Windows `.msi` / Linux `.deb`）
    
2.  **从源码构建**：
    

```
git clone https://github.com/nashsu/llm_wiki.git
cd llm_wiki
npm install
npm run tauri dev
```

### 11.2 claude-obsidian — Claude Code 知识引擎插件

AgriciDaniel/claude-obsidian 是一个 Claude Code 插件，将 LLM Wiki 能力深度集成到你的笔记工作流中：

-   **11 个内置技能**：摄入、查询、检查、深度研究等，通过斜杠命令调用
    
-   **多智能体支持**：不同任务由专门的 Agent 处理，效果更精准
    
-   **DragonScale Memory**：扩展记忆系统，跨会话保持上下文
    
-   **Canvas 画布**：可视化知识图谱与笔记关系
    

**安装方式**（二选一）：

1.  **一键安装**（需要 Claude Code）：
    

```
claude plugin install https://github.com/AgriciDaniel/claude-obsidian
```

2.  **手动安装**：
    

```
git clone https://github.com/AgriciDaniel/claude-obsidian.git
cd claude-obsidian
bash bin/setup-vault.sh /path/to/your/vault
```

### 11.3 llm-wiki-agent — 多平台编码智能体

SamurAIGPT/llm-wiki-agent 将 LLM Wiki 封装为一个通用编码智能体技能，不局限于特定工具：

-   **多平台支持**：兼容 Claude Code、OpenAI Codex CLI、Gemini CLI、OpenCode 等
    
-   **无需 API Key**：直接使用宿主工具的已有配置
    
-   **可视化知识图谱**：基于 vis.js 的交互式图谱展示
    
-   **丰富的斜杠命令**：`/ingest`、`/query`、`/lint` 等开箱即用
    

**安装方式**：

```
git clone https://github.com/SamurAIGPT/llm-wiki-agent.git
cd llm-wiki-agent
# 用你喜欢的编码工具打开即可，例如：
claude
# 或 codex / opencode / gemini
```

> **提示**：以上三个项目各有侧重——llm\_wiki 适合想要独立桌面应用和知识图谱可视化的用户，claude-obsidian 适合深度使用 Claude Code 的用户，llm-wiki-agent 适合多工具切换的用户。建议先上手基本流程，再根据需求选择进阶工具。

---

## 写在最后

这套系统的核心理念来自 Karpathy 的一个深刻洞察：**知识管理的本质不是存储，而是连接**。

传统的笔记方法，每条笔记都是一座孤岛。而 LLM Wiki 模式通过 AI 把零散的信息编织成一个互联的知识网络。随着你不断添加新素材，这个网络会越来越丰富，知识之间会产生你意想不到的关联。

更重要的是，这个过程是**增量**的。你不需要一次性花大量时间整理笔记——每次添加新素材时，AI 都会自动将新知识融入已有的知识体系中。你的知识库会像一棵树一样，持续生长。

开始动手吧。先用 Web Clipper 收集几篇你感兴趣的文章，然后让 AI 帮你把它们变成结构化的知识。你会发现，知识管理原来可以这么轻松。

---

## 附录

### A. 常用终端命令速查

```
# 进入知识库目录
cd ～/Documents/MyWiki

# 启动 Claude Code
claude

# 在 Claude Code 中的常用指令：
# 摄入新素材
# > 请摄入 raw/ 中的新素材

# 提问
# > 请解释 xxx

# 检查知识库
# > 请检查知识库健康状况
```

### B. 推荐的 Obsidian 插件

| 插件 | 用途 |
| --- | --- |
| **Dataview** | 用类 SQL 语法查询和展示笔记数据 |
| **Marp** | 将笔记转化为演示文稿 |
| **Git** | 用 Git 进行版本控制，防止数据丢失 |

### C. 参考资源

-   Karpathy 的 LLM Wiki 原文：[https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
    
-   Claudian 插件：[https://github.com/YishenTu/claudian](https://github.com/YishenTu/claudian)
    
-   Obsidian Web Clipper：Obsidian 官网插件页面
    
-   Anthropic API 控制台：[https://console.anthropic.com/](https://console.anthropic.com/)
    
-   Claude Code 文档：Anthropic 官方文档
    
-   llm\_wiki 桌面应用：[https://github.com/nashsu/llm\_wiki](https://github.com/nashsu/llm_wiki)
    
-   claude-obsidian 插件：[https://github.com/AgriciDaniel/claude-obsidian](https://github.com/AgriciDaniel/claude-obsidian)
    
-   llm-wiki-agent 智能体：[https://github.com/SamurAIGPT/llm-wiki-agent](https://github.com/SamurAIGPT/llm-wiki-agent)
    

---

![[笔记同步助手/images/36f557d8aef7676ffe6e28738e780561_MD5.jpg|cover_image]]

原创 vayne-LW manisfast

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/6b4e8b44_1779151189534?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU0NDE2NDU1NA%3D%3D%26mid%3D2247483696%26idx%3D1%26sn%3D0a06340a772e1f07a4ca26be712acc71%26chksm%3Dfa0b316e0fdef6783e006579c0b9702d14c8bbcb19bdacf4f6d69a92bfa735e776e5e06e289d%26mpshare%3D1%26scene%3D1%26srcid%3D0519J0jAQ7TyH2gPMxRcjPQj%26sharer_shareinfo%3Da6549298ab47dbaa4c2cd5aad953a01e%26sharer_shareinfo_first%3Da6549298ab47dbaa4c2cd5aad953a01e%23rd&s=obsidian)