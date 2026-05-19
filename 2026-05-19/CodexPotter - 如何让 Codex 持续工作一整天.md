---
author: Ranger
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzI1ODUzNjE0NQ==&mid=2247484959&idx=1&sn=4079fa672137b49891ec016b320494c4&chksm=eb2daa51e59ce5d7f260c6a47fdcf59fbc724f4f4ad2d4871b90fbb52a40b423d5258ab84ae9&mpshare=1&scene=1&srcid=0519UoKcKCT32gp26GmRVNSi&sharer_shareinfo=faf89998fe486d3efd9cfdc95bc212a6&sharer_shareinfo_first=faf89998fe486d3efd9cfdc95bc212a6#rd
saved: 2026-05-19 08:29:18
tags:
  - 笔记同步助手
id: 38881abe-5fa9-4a6f-a518-a6597400e837
---

公众号名称：Ranger Ramblings

作者名称：Ranger

发布时间：2026-04-18 19:55

![[笔记同步助手/images/1d8ab28cfbbcd2a6a8c7a027ec412b85_MD5.jpg]]

友情提示：该工具旨在用 tokens 换质量，所以会耗费大量的 tokens，tokens 焦虑的朋友谨慎使用。

**Ralph loop for codex** — 持续将代码库向你指定的目标状态对齐。

-   • **仓库地址**：https://github.com/breezewish/CodexPotter
    
-   • **License**：Apache-2.0
    
-   • **发布渠道**：npm: codex-potter\[1\]
    
-   • **支持平台**：Linux（x86\_64 / aarch64）、macOS（Apple Silicon / Intel）、Windows（x86\_64 / ARM64）
    

## 📌 项目简介

CodexPotter 是一个围绕 OpenAI Codex CLI\[2\] 构建的**自主循环执行器**，它实现了 Ralph Wiggum 模式\[3\]——即持续地、多轮地将代码库"对齐"（reconcile）到你所指示的目标状态，直到任务完全完成。

与直接使用 Codex CLI 进行对话不同，CodexPotter 的核心理念是：**将任务交给它，让它自主执行，而不是和它聊天**。

​

## 🧩 解决了什么问题

在使用 Codex 进行较大规模的编码任务时，常见的痛点包括：

​

| 痛点 | CodexPotter 的解法 |
| :-- | :-- |
| 单轮 Codex 常常只完成一部分，留下"烂尾" | 多轮自动 Review + 继续执行，直到完全对齐 |
| 长对话导致上下文污染（context poisoning），模型"越聊越蠢" | 每轮使用干净上下文（clean context），避免上下文积累带来的质量退化 |
| 需要人工反复 review 和跟进 | 自动 review 流程，释放你的注意力专注于"定义任务" |
| 任务细节在多轮对话中丢失 | 以文件系统作为记忆（MAIN.md 等进度文件），细节永不丢失 |
| Codex 引入了无关的"业务 Prompt"，效果不符合预期 | 仅驱动 Codex，不附加额外业务 Prompt，保证效果纯粹 |
| 每轮新 Codex 会话需重新理解项目 | 内置知识库（`.codexpotter/kb/`），跨会话积累项目知识 |
| 系统 Prompt 过长消耗上下文 | 内置 Prompt 不到 1k tokens，最大化上下文留给业务逻辑 |

## ⚙️ 工作原理

CodexPotter 的工作流可以用下图来理解：

![[笔记同步助手/images/9c5466c36aa435523e64effd8ecc9928_MD5.png]]

## 执行流程（内部 Prompt 机制）：

1.  1\. 你向 CodexPotter 提交一个任务 Prompt
    
2.  2\. CodexPotter 将任务写入进度文件（`MAIN.md`），状态设为 `initial`
    
3.  3\. Codex 读取进度文件，将任务拆解为子任务（`Todo`），状态变为 `open`
    
4.  4\. Codex 循环执行子任务：`Todo → In Progress → Done`，并在每轮完成后提交 git commit
    
5.  5\. 所有 `Todo` 完成后，Codex 进行严格 Review，识别遗漏或未对齐的地方，继续补充 `Todo`
    
6.  6\. 直到 Review 确认完全对齐，任务结束
    

进度文件、知识库等均保存在 `.codexpotter/` 目录下（已自动加入 `.gitignore`，不会被提交）。

​

## 🚀 快速上手

### 前置条件

确保本地已安装并配置好 Codex CLI\[2\]（需要 OpenAI Codex 订阅）。

### 安装

```
# 使用 npm
npm install -g codex-potter

# 使用 bun
bun install -g codex-potter
```

### 启动

在你的项目目录下运行：

​

```
# 推荐使用 --yolo 模式以实现完全自主执行（无沙箱）
codex-potter --yolo
```

### ⚠️ 重要注意事项

-   • **每条 Prompt 都是独立任务**：与 Codex 不同，CodexPotter 中每个后续 Prompt 都会开启一个**新任务**，不与上一个任务共享上下文。请将它当作任务分配工具，而非聊天工具。
    
-   • **不是 Codex 的替代品**：CodexPotter 是循环执行器，Codex 负责实际编码。两者配合使用，效果最佳。
    

## 💡 使用场景

### ✅ 适合的场景

| 场景 | 示例 |
| :-- | :-- |
| 有明确目标/范围的编码任务 | 移植某功能、重构某模块、实现某需求 |
| 需要多轮迭代的大型任务 | 实现一个完整的订阅系统 |
| 需要持久化产出的研究/设计任务 | 写设计文档、写技术方案 |
| 需要全量测试覆盖的实现任务 | 实现并确保 e2e 测试全通过 |

### ❌ 不适合的场景

| 场景 | 原因 |
| :-- | :-- |
| 前端开发（需要人工 UI 反馈） | CodexPotter 不支持交互式人工反馈循环 |
| 问答 / 解释代码 | 请直接使用 Codex CLI |
| 头脑风暴 / 开放性讨论 | 请直接使用 Codex CLI |

## 📋 使用示例

### 示例 1：单任务执行

```
port upstream codex's /resume into this project, keep code aligned
```

### 示例 2：输出持久化（让结果可在后续轮次中复用）

```
create a design doc for the new subscription system in DESIGN.md
```

> **技巧**：让 Codex 将中间产出写入文件（如 `DESIGN.md`），可以让下一个任务直接引用，实现"先设计再实现"的工作流。

### 示例 3：先规划后实现（两阶段工作流）

**任务 1（规划阶段）：**

​

```
Analyze the codebase, research and design a solution for introducing subscription system.
Output plan to docs/subscription_design.md.

Your solution should meet the following requirements: ...

Do not implement the plan, just design a good and simple solution.
```

**任务 2（实现阶段）：**

​

```
Implement according to docs/subscription_design.md

Make sure all user journeys are properly covered by e2e tests and pass.
```

### 示例 4：在 Codex 中追问 CodexPotter 的任务详情

```
based on .codexpotter/projects/2026/03/18/1/MAIN.md,
please explain more about the root cause of the issue
```

## 🔧 高级功能

### `--xmodel`（实验性）

使用双模型交叉 Review：先用 `gpt-5.2` 执行，再用 `gpt-5.4` 对 `gpt-5.2` 的工作进行 Review。对于清晰的编码任务，可能产出比单一模型更好的结果。

​

```
codex-potter --yolo --xmodel
```

### `/yolo` 命令

在交互界面中切换是否默认为所有会话开启 YOLO 模式（无沙箱）。

### `/list` 或 `Ctrl+L`

查看所有项目（任务）及其执行结果历史。

### AGENTS.md / Skills / MCP 集成

CodexPotter 与 Codex 的 `AGENTS.md`、Skills、MCP（Model Context Protocol）无缝兼容，在项目根目录放置 `AGENTS.md` 即可让 Codex 遵循你的工程规范。

### 知识库（`.codexpotter/kb/`）

CodexPotter 会在每次深度探索模块后，将关键事实和代码位置写入本地知识库（`.codexpotter/kb/xxx.md`）并维护索引（`README.md`）。新的干净上下文会话启动前会读取知识库，让 Codex 快速上手项目背景。

​

## 🛠️ 常见问题与解决方案

### Q1：运行时报错 `Missing optional dependency codex-potter-`

**原因**：npm 安装时未能正确拉取当前平台对应的原生二进制包。

**解决方案**：重新安装 CodexPotter，确保包管理器可以拉取到正确的平台包：

​

```
npm uninstall -g codex-potter
npm install -g codex-potter
```

### Q2：任务执行到一半停止了，没有完全完成

**原因**：网络断连、stream 中断等偶发网络问题。

**解决方案**：CodexPotter 支持 Resume（历史回放 + 继续迭代），直接重新进入项目并继续执行即可。可通过 `/list` 查看历史任务并选择 Resume。

### Q3：工具（tool）报错导致 CLI 直接退出

**原因**：这是一个已知 Bug（issue #1\[4\]），某些工具调用的错误会直接导致 CLI 退出，而非优雅处理。

**解决方案**：目前可重新启动 CodexPotter 并 Resume 对应任务；等待官方修复。

### Q4：Codex 在多轮执行后输出质量下降

**原因**：这不是 CodexPotter 的问题——CodexPotter 的核心设计就是每轮使用干净上下文，避免上下文积累导致的质量退化。如果仍出现质量问题，请检查知识库（`.codexpotter/kb/`）是否包含过时的信息，手动更新后重新执行。

### Q5：任务太大，Codex 无法在一轮内完成

**解决方案**：将大任务拆分为两个 CodexPotter 任务（先规划、再实现），并通过文件传递中间产出（详见示例 3）。如果连规划也不清楚，先用 Codex CLI 进行头脑风暴，形成基本方案后再交给 CodexPotter 执行。

### Q6：如何在不影响项目 git 历史的情况下使用 CodexPotter

CodexPotter 会将进度文件、知识库等保存在 `.codexpotter/` 目录下，该目录已自动加入 `.gitignore`，不会被提交到 git 历史中。每次编码变更会由 Codex 以独立 commit 提交，便于 review。

​

## 🗺️ Roadmap

| 功能 | 状态 |
| :-- | :-- |
| Skill 弹出支持 | ✅ 已完成 |
| Resume（历史回放 + 继续迭代） | ✅ 已完成 |
| 网络断连 / stream 问题处理优化 | ✅ 已完成 |
| Agent 调用友好（非交互式执行与 Resume） | ✅ 已完成 |
| 与 Codex CLI 会话互操作（用于追问） | ✅ 已完成 |
| 更好的规划 / 用户选择支持 | 🔲 规划中 |
| 更好的沙箱支持 | 🔲 规划中 |

## 🏗️ 本地开发

```
# 代码格式化
cargo fmt

# Lint 检查
cargo clippy

# 运行测试
cargo nextest run

# 构建
cargo build
```

## 📎 相关链接

-   • 项目仓库\[5\]
    
-   • npm 包页面\[1\]
    
-   • OpenAI Codex CLI 文档\[2\]
    
-   • Ralph Wiggum 模式介绍\[3\]
    
-   • 上游 openai/codex 仓库\[6\]
    
-   • LINUX DO 社区\[7\]
    

#### 引用链接

`[1]` npm: codex-potter: _https://www.npmjs.com/package/codex-potter_  
`[2]` OpenAI Codex CLI: _https://developers.openai.com/codex/quickstart?setup=cli_  
`[3]` Ralph Wiggum 模式: _https://ghuntley.com/ralph/_  
`[4]` issue #1: _https://github.com/breezewish/CodexPotter/issues/1_  
`[5]` 项目仓库: _https://github.com/breezewish/CodexPotter_  
`[6]` 上游 openai/codex 仓库: _https://github.com/openai/codex_  
`[7]` LINUX DO 社区: _https://linux.do_

---

Original Ranger Ranger Ramblings

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/802884e8_1779150557449?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1ODUzNjE0NQ%3D%3D%26mid%3D2247484959%26idx%3D1%26sn%3D4079fa672137b49891ec016b320494c4%26chksm%3Deb2daa51e59ce5d7f260c6a47fdcf59fbc724f4f4ad2d4871b90fbb52a40b423d5258ab84ae9%26mpshare%3D1%26scene%3D1%26srcid%3D0519UoKcKCT32gp26GmRVNSi%26sharer_shareinfo%3Dfaf89998fe486d3efd9cfdc95bc212a6%26sharer_shareinfo_first%3Dfaf89998fe486d3efd9cfdc95bc212a6%23rd&s=obsidian)