---
author: 科爷
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk4ODY2NjI3Nw==&mid=2247483967&idx=1&sn=8fb7baa2e903b7d9abbdccb36a9f0724&chksm=c478643003b5203b64a8b59ff255b3f3418e0d36fc843faa0da5deed34e00e449f7939c9782e&mpshare=1&scene=1&srcid=05283XOs9aaw0YWkR4Ba1cI3&sharer_shareinfo=8e533fbf5a25adf441b6553f1959ab3b&sharer_shareinfo_first=8e533fbf5a25adf441b6553f1959ab3b#rd
saved: 2026-05-28 08:33:18
tags:
  - 笔记同步助手
id: dd3c92c0-40f4-43ef-b8a7-ca27dca60f6e
---

公众号名称：科爷的数字生命

作者名称：科爷

发布时间：2026-05-20 08:00

  

Codex 最近支持手机 App 远程控制，让 vibe coding 的移动体验大为改善，现在的它真的比 Claude 香了不少。

你值得拥有。

![[笔记同步助手/images/41a38255ae890978782a197cf741cbc2_MD5.png]]

![[笔记同步助手/images/8904ee9a43c117355766e5772f0136c0_MD5.png]]

![[笔记同步助手/images/92192094e1e1e3e594a7b487775839f4_MD5.png]]

![[笔记同步助手/images/b38e85560d4a6cd3f79446867254df24_MD5.png]]

![[笔记同步助手/images/3b646a2ef6aa13593d788f5d5011bf8e_MD5.png]]

![[笔记同步助手/images/702e1bf006d6b810058f1247d9bdd560_MD5.png]]

![[笔记同步助手/images/d135cbb7f1c72100cc6b906b7bb68bd3_MD5.png]]

![[笔记同步助手/images/41a38255ae890978782a197cf741cbc2_MD5.png]]

![[笔记同步助手/images/8904ee9a43c117355766e5772f0136c0_MD5.png]]

![[笔记同步助手/images/92192094e1e1e3e594a7b487775839f4_MD5.png]]

![[笔记同步助手/images/b38e85560d4a6cd3f79446867254df24_MD5.png]]

![[笔记同步助手/images/3b646a2ef6aa13593d788f5d5011bf8e_MD5.png]]

![[笔记同步助手/images/702e1bf006d6b810058f1247d9bdd560_MD5.png]]

![[笔记同步助手/images/d135cbb7f1c72100cc6b906b7bb68bd3_MD5.png]]

## 什么是 Codex？

Codex 是 OpenAI 官方出品的 AI 编码工具。它会理解你的需求，帮你写代码、跑命令、调 Bug。你不需要是程序员，只要能用自然语言描述你想要什么。

最关键的是：如果你已经有 ChatGPT Plus/Pro 订阅，Codex 可能已经包含在你的套餐里了。那每个月 20 美元，终于不只是用来写周报了。

**2026 年的 Codex 已经不只是一个命令行编码助手**，而是逐步构建为一套"AI 干活系统"。按官方 Changelog 看，4 月最核心的变化有三个：

1.  1\. **Codex App 26.415**：从聊天式工具升级成 AI 工作台，支持内置浏览器、任务侧边栏、GitHub PR 处理、Memories、多终端多窗口
    
2.  2\. **模型 GPT-5.5**：进入 Codex，重点提升复杂实现、重构、调试、测试和验证的能力
    
3.  3\. **Codex CLI 0.128.0**：加入可持久化的 /goal 工作流，支持长期目标的创建、暂停和恢复
    

从这些迭代可以看出，对于现在的 Codex，不要只问"它会不会写代码"，更准确的问题是：**它能不能接住你工作流里那些重复、复杂、跨文件、需要验证的任务。**

## 四种运行方式，总有一种适合你

Codex 有四种形态：

1.  1\. **CLI（命令行）**：适合习惯终端的开发者
    
2.  2\. **App（桌面应用）**：有图形界面，适合不喜欢黑框框的人
    
3.  3\. **Web（网页版）**：打开浏览器就用，不用装任何东西
    
4.  4\. **IDE 插件**：装在 VS Code、Cursor 里，写代码时直接调用
    

新手建议从 App 开始，开发者建议从 CLI 开始。别纠结入口，工具不是对象，不需要从一而终。

## 五分钟安装上手

### 环境准备

你的电脑需要有 Node.js 和 Git。打开终端检查：

```
node --version
npm --version
git --version
```

如果没有，先去官网下载安装。

Node.js 下载：https://nodejs.org/zh-cn/download  
Git 下载：https://git-scm.com/install/windows

> **Windows 用户注意**：如果 CLI 遇到环境问题，可以考虑用 WSL，或者直接跳到 App 部分。

### 安装 Codex

**CLI 安装**：

```
# npm 安装
npm install -g @openai/codex

# Homebrew 安装（macOS）
brew install --cask codex

# 验证安装
codex --version
```

看到版本号就说明成功了。如果这里没看到版本号，优先检查 Node.js、npm 全局路径和网络。

**App 安装**：Windows 用户去微软商店搜索下载，或访问：https://get.microsoft.com/installer/download/9PLM9XGG6VKS

**云端版**：直接访问 https://chatgpt.com/codex/cloud

**IDE 插件**：访问 https://developers.openai.com/codex/ide 安装

### 首次登录

打开终端输入 `codex`，首次启动会让你选择登录方式。

推荐用 ChatGPT 账号授权，一条龙服务。或者去 OpenAI 平台生成 API Key，按 token 计费。

**常见问题**：首次启动可能报错 `Error: account/read failed during TUI bootstrap`

别硬刚，执行 `codex logout` 后重新登录，浏览器授权一遍基本就好了。

登录成功后，你会看到模型选择界面。

![[笔记同步助手/images/41a38255ae890978782a197cf741cbc2_MD5.png]]

GPT-5.5 是目前最新也是最强的模型。想切换模型时用 `/model` 命令。

## 30 秒第一个项目

装好了？先跑个试试。别上来就让它重构系统，从小游戏练手心态更健康。

新建一个文件夹，打开终端：

```
codex "用 Python 写一个贪吃蛇游戏"
```

就这样。Codex 会理解你的需求，生成代码，创建文件，甚至帮你运行。

![[笔记同步助手/images/8904ee9a43c117355766e5772f0136c0_MD5.png]]

这就是 AI 编码工具的核心价值：你负责描述目标，它负责拆任务、改文件、跑命令。

试完这一个，你就知道 Codex 大概是什么感觉了。后面再把它放进真实项目里，价值会更明显。

## 界面和交互

这里以 App 界面和 CLI 界面为例介绍，这是我主要使用的。

### CLI 界面

CLI 是最"开发者"的形态。在终端里说需求，它在项目里改文件、跑命令、修问题。

![[笔记同步助手/images/92192094e1e1e3e594a7b487775839f4_MD5.png]]

常用命令：

-   • `/model` - 切换模型
    
-   • `/goal` - 创建持久化目标（进阶）
    
-   • `codex logout` - 登出
    
-   • `codex update` - 更新 Codex
    
-   • `codex --version` - 查看版本
    

### App 界面

App 让你可以同时看项目文件、对话记录和修改内容。

![[笔记同步助手/images/b38e85560d4a6cd3f79446867254df24_MD5.png]]

点击右上角可以切换文件树，预览文件内容，直接在文件里做注释让 Codex 按你的反馈修改。

![[笔记同步助手/images/3b646a2ef6aa13593d788f5d5011bf8e_MD5.png]]

## 进阶技巧（小白友好版）

### 1\. AGENTS.md 配置文件

在项目根目录创建 AGENTS.md，告诉 Codex 你的项目规范：

```
# AGENTS.md

## 项目说明

这是一个 [项目类型] 项目，主要用于 [项目目的]。

## 开发规范

- 语言：[Python 3.11+ / Node.js 18+ / ...]
- 代码风格：[PEP 8 / ESLint / 简单可读]
- 测试框架：[pytest / jest / 无]
- 注释：[中文注释]
- 新增功能时同步更新 README
- 修改代码后尽量运行测试或启动程序验证

## 交互偏好

- 先解释修改思路，再改代码
- 涉及删除文件、重构目录、安装依赖时先询问
- 回复使用中文

## Codex 特定配置

- 权限模式：自动审查（关键操作需确认）
- 默认模型：gpt-5.5
```

这样 Codex 会更贴合你的习惯。

AI 编码工具不是不会干活，它是不知道你的项目规则。AGENTS.md 就是把规则先写清楚，省得每次都重新说明。

### 2\. 常用场景

Codex 不只是写代码，它的能力远超你的想象。

**Computer Use 功能**：这是 Codex 最强大的功能之一。它可以直接操作你的电脑，就像有一个虚拟助手坐在你面前。让它打开浏览器、点击按钮、填写表单、截图验证，全部自动化完成。适合用来做自动化测试、网页抓取、重复性操作等。

**Chrome 插件**：安装 Codex Chrome 插件后，它可以直接读取网页内容，理解页面结构，帮你写爬虫、做数据分析、甚至直接在浏览器里调试代码。遇到不懂的网页效果，直接让插件看看源码，它就能给你讲明白。

当然，传统场景也没落下：

-   • **代码重构**：让它优化现有代码
    
-   • **写单元测试**：给函数补测试用例
    
-   • **修复 Bug**：把报错信息丢给它
    
-   • **代码审查**：让它 review 你的代码
    

我建议你从这几个场景开始用：

-   • 让它解释当前文件的作用
    
-   • 选中一段代码，让它重构或补注释
    
-   • 把报错信息贴进去，让它定位问题
    
-   • 让它给某个函数补单元测试
    

### 3\. 权限模式（安全第一）

Codex 有几种权限模式：

-   • **默认权限**：只给建议，适合你想先看方案
    
-   • **自动审查**：可以自动编辑文件，但关键操作会请示你
    
-   • **完全访问**：权限更大，可以自动执行更多操作
    

![[笔记同步助手/images/702e1bf006d6b810058f1247d9bdd560_MD5.png]]

新手推荐：

-   • 日常使用开"自动审查"模式
    
-   • 删除文件、安装依赖、推送代码必须手动确认
    
-   • 批量重构时先让它制定方案，确认后再执行
    

不要一开始就完全放权，等你熟悉了 Codex 的行为模式再逐步开放权限。

## Coding Agent 工作原理

理解 Codex 的运行机制，能让你用得更顺手。

Codex 的工作循环是：**获取上下文 → 执行操作 → 验证结果**

这三个阶段不是严格按顺序执行，而是在整个任务过程中不断交替出现。

在这个过程中，Codex 会持续调用各种工具：

-   • 搜索代码以理解项目结构
    
-   • 修改文件实现需求
    
-   • 运行测试验证修改结果
    

**这就是 Agentic Loop 的运行过程。**

Codex 可以访问：

-   • 当前目录中的所有代码文件
    
-   • 项目结构和配置
    
-   • 命令行工具、构建工具、包管理器
    
-   • Git：当前分支、未提交修改、最近提交记录
    

由于 Codex 可以访问整个项目，因此能够在多个文件之间进行协同修改，而不仅仅局限于当前文件。

## 常见问题速查

**登录失败**：执行 `codex logout` 后重新登录，或换 API Key 方式

**命令找不到**：重新安装 `npm install -g @openai/codex`，检查 npm 全局路径

**环境变量找不到**：Windows 用户配置完要重启 Codex，不行就重启电脑

**首次启动报错**：Error: account/read failed during TUI bootstrap —— 重新登录就恢复了

---

![[笔记同步助手/images/6c71e317a1254d05d6704cfb93a0ebbd_MD5.jpg|cover_image]]

原创 科爷 科爷的数字生命

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/a9c77f86_1779928397141?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk4ODY2NjI3Nw%3D%3D%26mid%3D2247483967%26idx%3D1%26sn%3D8fb7baa2e903b7d9abbdccb36a9f0724%26chksm%3Dc478643003b5203b64a8b59ff255b3f3418e0d36fc843faa0da5deed34e00e449f7939c9782e%26mpshare%3D1%26scene%3D1%26srcid%3D05283XOs9aaw0YWkR4Ba1cI3%26sharer_shareinfo%3D8e533fbf5a25adf441b6553f1959ab3b%26sharer_shareinfo_first%3D8e533fbf5a25adf441b6553f1959ab3b%23rd&s=obsidian)