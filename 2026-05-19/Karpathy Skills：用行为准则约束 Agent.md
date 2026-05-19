---
author: Ranger Ramblings
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzI1ODUzNjE0NQ==&mid=2247484992&idx=1&sn=e37bd799a843c75d3f62f909264ee9b9&chksm=eb6f5f0988146e507877a48353fad5c0793c418bb157f149cd5182c1861b3b6450e58ee1547d&mpshare=1&scene=1&srcid=0519zDB6xMYAF4ngzRIWXnOh&sharer_shareinfo=f8fcd0062f40cb6f015489116ffff607&sharer_shareinfo_first=f8fcd0062f40cb6f015489116ffff607#rd
saved: 2026-05-19 08:32:36
tags:
  - 笔记同步助手
id: 02962271-01e7-41d8-8a37-1539a01600fc
---

公众号名称：Ranger Ramblings

作者名称：

发布时间：2026-04-28 17:06

DeepSeek V4 出来后又加上大降价，又用回了 Claude Code，真爽啊！这个项目也属实离谱，就一个 MD 文件就 95K Stars...大家参考一下要不要用吧，待我试试效果。最后说一句，DeepSeek NP！

![[笔记同步助手/images/6c832608d8bac081d376e93de40dcfc4_MD5.png]]

## 项目简介

`andrej-karpathy-skills` 是一个**极简但高价值**的项目——它只有一个文件：`CLAUDE.md`。

这个文件是一份为 **Claude Code**（Anthropic 的 AI 编程助手）量身定制的**行为准则文档**，灵感来源于 AI 领域知名研究者 **Andrej Karpathy** 对 LLM 编程缺陷的系统性观察与总结。

其核心目标是：**通过在项目中放置这份文件，约束 AI 编程助手的行为模式，减少常见的过度设计、随意改动、假设错误等问题。**

​

## 解决什么问题？

使用 Claude Code（或类似 AI 编程工具）时，开发者常常遇到以下令人头疼的问题：

​

| 问题 | 表现 |
| :-- | :-- |
| **过度假设** | AI 不确定需求时，不问反而自行"脑补"实现，结果跑偏 |
| **过度工程** | 明明 20 行能搞定，AI 写出 200 行含各种抽象层、扩展点的"架构" |
| **无关改动** | AI 修一个 bug，顺手把旁边"看起来不太好"的代码也重构了 |
| **目标模糊** | AI 执行多步任务时没有明确的验证节点，做完了也不知道对不对 |
| **隐藏困惑** | AI 对模糊需求不追问，而是悄悄选了一种实现，出了问题才发现理解偏差 |

这份 `CLAUDE.md` 通过清晰的行为准则，系统性地压制上述问题。

​

## 核心内容解读

文件定义了四条核心准则：

### 1\. 先思考，再编码（Think Before Coding）

-   • 明确说出假设，不确定就问
    
-   • 存在多种解读时，列出来而不是默默选一个
    
-   • 遇到更简单的方案，主动说出来
    

### 2\. 简单优先（Simplicity First）

-   • 只实现被要求的功能，不做"预留扩展"
    
-   • 单次使用的代码不做抽象
    
-   • 不处理不可能发生的边界情况
    
-   • 核心问题：**"资深工程师会觉得这过于复杂吗？"**
    

### 3\. 外科手术式修改（Surgical Changes）

-   • 只改必须改的地方
    
-   • 不顺手"优化"相邻代码
    
-   • 保持现有代码风格
    
-   • **自己造成的孤立代码（unused imports 等）负责清理，但不动存量死代码**
    

### 4\. 目标驱动执行（Goal-Driven Execution）

-   • 将任务转化为可验证的目标（写测试 → 让测试通过）
    
-   • 多步任务先给出计划，每步附带验证条件
    
-   • 弱标准（"让它能跑"）= 反复返工；强标准 = 自主循环直到完成
    

## 如何使用

### 方法一：放入项目根目录（推荐）

将 `CLAUDE.md` 文件复制到你的项目根目录：

​

```
curl -O https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md
```

Claude Code 会自动读取项目根目录下的 `CLAUDE.md` 并将其作为系统级上下文加载，无需任何配置。

### 方法二：合并到现有 CLAUDE.md

如果你的项目已有 `CLAUDE.md`，将这份文件的内容**追加或合并**进去即可。文件本身也注明了：

> "Merge with project-specific instructions as needed."

### 方法三：全局配置（适用于所有项目）

将文件内容放入 Claude Code 的全局配置目录（通常为 `～/.claude/CLAUDE.md`），使其对所有项目生效。

​

## 适用场景

### 强烈推荐使用的场景

-   • **生产项目**：代码质量要求高，不希望 AI 随意改动非目标代码
    
-   • **遗留代码库**：存量代码风格各异，需要 AI 严格遵守"只改所需"
    
-   • **多人协作项目**：通过 `CLAUDE.md` 在团队内统一 AI 行为预期
    
-   • **需求模糊的探索阶段**：强制 AI 在不确定时提问，而不是瞎猜
    
-   • **重构/修 bug 任务**：防止 AI "顺手"改了一堆无关的东西
    

### 可按需调整的场景

-   • **快速原型 / 一次性脚本**：文件本身也说了 "For trivial tasks, use judgment"，准则偏谨慎，小任务可适当放宽
    
-   • **全新项目初始化**：没有存量代码时，部分"不动无关代码"的约束意义不大
    

## 使用示例

### 场景：修复一个 Bug

**没有 CLAUDE.md 时**，AI 可能的行为：

​

```
用户：修复 parse_config() 函数中的 KeyError
AI：修复了 KeyError，同时重构了 load_file() 函数的错误处理，
    顺手把 utils.py 里的变量命名改成了更符合 PEP8 的风格……
```

**有了 CLAUDE.md 后**，AI 的行为被约束为：

​

```
用户：修复 parse_config() 函数中的 KeyError
AI：我的假设是 key 可能不存在时应返回默认值而非抛出异常，
    是否正确？如果是，我会只在 parse_config() 中添加 .get() 调用，
    不涉及其他文件。
```

### 场景：添加新功能

**任务**：给 API 接口添加参数校验

**AI 的目标驱动执行（符合准则 4）**：

​

```
计划：
1. 为无效参数输入编写测试用例 → 验证：测试失败（红）
2. 在接口层添加校验逻辑 → 验证：测试通过（绿）
3. 确认无无关文件被修改 → 验证：diff 只包含接口文件和测试文件
```

## 进阶：与现有 CLAUDE.md 融合

### 常见局面

很多项目在引入 Karpathy 准则之前，已经有了一份 CLAUDE.md。典型情况是**两层结构**：

​

| 层级 | 职责 |
| :-- | :-- |
| 全局配置 `～/.claude/CLAUDE.md` | AI 人设（语气/风格/交互方式）+ 基础行为准则 + 工具路由 |
| 项目配置 `/CLAUDE.md` | 仓库结构、领域知识、项目级工具配置 |

全局配置往往以**风格设定为主、行为约束为辅**——比如 70% 的篇幅在定义 AI 怎么说话，只有零散的几条规则涉及怎么写代码。项目配置则完全聚焦领域知识，几乎不涉及行为准则。

**直接粘贴 Karpathy 英文原文会导致语气割裂**——AI 一会用你精心调教的人设对话，一会突然切换到冷冰冰的英文指令模式。

### 第一步：覆盖度审计

用 Karpathy 四条规则逐条对照现有 CLAUDE.md，标注覆盖程度：

​

| Karpathy 规则 | 典型现状 | 常见缺口 |
| :-- | :-- | :-- |
| **1\. Think Before Coding** | 可能有「不确定就查」「先分析再动手」等泛化原则 | 缺少「明确说出假设」「列出多种解读让用户选」「不确定时停下来问」这些具体动作 |
| **2\. Simplicity First** | 可能有「改最少的地方」等原则 | 缺少反过度工程的量化标准：「不给不可能场景写错误处理」「单次使用不做抽象」「200 行能压 50 行就重写」 |
| **3\. Surgical Changes** | 通常最薄弱——泛化的「最小改动」没有展开 | 缺少「不顺手优化相邻代码」「匹配存量风格」「只清理自己造成的死代码」 |
| **4\. Goal-Driven Execution** | 可能有执行流程、验证步骤 | 缺少「把模糊任务转成可验证目标」「test-first」「验证不过就循环修」 |

### 第二步：融合策略——「加一层，不改皮」

-   • **不动人格层**：语气/风格/交互方式保持不变，那是你调教好的交互体验
    
-   • **新增行为层**：把 Karpathy 四规则**用你 AI 人设的口吻重写**，作为独立章节追加
    
-   • **不动项目文件**：领域知识配置跟编程行为无关，不需要塞行为准则
    

关键操作：**本地化翻译，别照抄**。比如 "Don't assume. Don't hide confusion." 如果你的 AI 人设是严谨工程师风格就译成「明确假设，暴露困惑」；如果是活泼风格就译成「别脑补，别藏着不说」——意思不变，语气对齐。

### 第三步：处理「速度 vs 谨慎」矛盾

Karpathy 原文开篇声明了 **bias toward caution over speed**。但如果你的 CLAUDE.md 里恰好有鼓励快速试错、讨厌过度分析的倾向，这两条指令会在系统提示里互相抵消。

**解法：加一条适用尺度条款**，把裁决权交给用户的明确表态：

​

```
> **适用尺度**：生产代码偏保守，快速原型/一次性脚本偏速度。
> 用户明确说「随便试试」「先跑起来」= 放行信号。
```

这样既保留了严谨的底线，又不会在探索阶段过度设限。

### 第四步：参考结构

```
## 编程戒律

> 灵感来自 andrej-karpathy-skills
> 适用尺度：生产偏保守，原型偏速度。

### 1. 动手前先想 · Think Before Coding
- 明确说出假设，不确定就问
- 存在多种解读时列出来，让用户选
- 有更简单的方案主动说，该 push back 就 push back
- 遇到模糊需求停下来，说出哪里不清楚，然后问

### 2. 极简至上 · Simplicity First
- 不实现没被要求的功能
- 单次使用的代码不做抽象
- 不给不可能发生的场景写错误处理
- 自问：资深工程师会觉得这过度设计了吗？

### 3. 外科手术 · Surgical Changes
- 不顺手"优化"旁边的代码、注释、格式
- 不重构没坏的东西
- 匹配存量风格，不用自己的偏好覆盖
- 自己造成的死代码自己清，不动存量
- 测试：diff 里每一行改动都能追溯回用户的原话

### 4. 目标驱动 · Goal-Driven Execution
- 「加校验」→ 先写非法输入测试（红），再加校验（绿）
- 「修 bug」→ 写复现用例（红），修完（绿）
- 多步任务先列计划，每步挂验证条件
```

### 经验总结

| 要点 | 说明 |
| :-- | :-- |
| **别照抄** | 用你 AI 助手已有的语气重写规则，否则读起来像两个人格在打架 |
| **先审计再动手** | 用四规则做覆盖度矩阵，避免重复写已有的东西 |
| **调和冲突** | 如果现有人格偏向「快速试错」，必须加适用尺度条款 |
| **分层治理** | 人格层管「怎么说」，行为层管「怎么干」，项目文件管「干什么」 |
| **验证靠观测** | 改完后看 diff 是否更干净、AI 是否在动手前先问问题 |

## 可能遇到的问题及解决方案

### Q1：Claude Code 没有自动读取 CLAUDE.md

**原因**：文件路径不对，或使用的不是 Claude Code 而是其他工具。

**解决**：

-   • 确认文件在**项目根目录**（与 `.git` 同级）
    
-   • 如果使用的是 Cursor、GitHub Copilot 等其他工具，这份文件**不会自动生效**，需要手动将内容粘贴到对应工具的 System Prompt 或自定义指令中
    

### Q2：准则太保守，AI 变得过于谨慎、问题太多

**原因**：文件自身也承认 "These guidelines bias toward caution over speed"。

**解决**：

-   • 在文件顶部或底部追加项目特定指令，例如：`For prototype work in the /scripts directory, speed over caution is preferred.`
    
-   • 针对特定类型任务放开约束，做到项目级定制
    

### Q3：想用于 GPT-4 / Gemini / Cursor 等其他 AI 工具

**解决**：

-   • **Cursor**：将内容粘贴到 `.cursorrules` 文件中
    
-   • **GitHub Copilot（自定义指令）**：粘贴到 `.github/copilot-instructions.md`
    
-   • **ChatGPT / API 调用**：将内容作为 `system` 消息传入
    
-   • **通用做法**：内容是纯文本准则，复制到任何工具的 System Prompt 均可生效
    

### Q4：团队成员各自定制了不同版本，产生冲突

**解决**：

-   • 将 `CLAUDE.md`**纳入版本控制**（commit 到仓库），通过 code review 统一管理变更
    
-   • 区分"团队共识部分"（提交到仓库）和"个人偏好部分"（放到全局 `～/.claude/CLAUDE.md`）
    

## 延伸补充

### 为什么叫"Karpathy Skills"？

Andrej Karpathy 曾公开分享过他在使用 AI 编程工具时观察到的系统性问题，这份文件是对这些观察的提炼和结构化表达。项目作者 @forrestchang\[1\] 将其整理成可直接复用的 `CLAUDE.md` 格式。

### 与 `.cursorrules` / `copilot-instructions.md` 的关系

这三者本质相同：都是**向 AI 注入持久化行为约束的配置文件**，只是对应不同工具的读取路径。`CLAUDE.md` 是 Claude Code 的专用格式。

### 如何判断它是否在起作用？

文件末尾给出了验收标准：

> **These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

即：**diff 更干净、重写变少、问题在动手前而不是出错后才来**。

​

## 快速开始

```
# 1. 进入你的项目目录
cd your-project

# 2. 下载 CLAUDE.md
curl -O https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md

# 3. 提交到版本控制
git add CLAUDE.md
git commit -m "chore: add CLAUDE.md for AI behavior guidelines"

# 4. 开始使用 Claude Code，行为准则自动生效
```

_文档基于 forrestchang/andrej-karpathy-skills\[2\]（95k）整理，结合实际使用场景补充。_

​

#### 引用链接

`[1]` @forrestchang: _https://github.com/forrestchang_  
`[2]` forrestchang/andrej-karpathy-skills: _https://github.com/forrestchang/andrej-karpathy-skills_

---

![[笔记同步助手/images/93ae0352038969653db8a8768c4625af_MD5.jpg|cover_image]]

Ranger Ramblings

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/47fe5899_1779150755740?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1ODUzNjE0NQ%3D%3D%26mid%3D2247484992%26idx%3D1%26sn%3De37bd799a843c75d3f62f909264ee9b9%26chksm%3Deb6f5f0988146e507877a48353fad5c0793c418bb157f149cd5182c1861b3b6450e58ee1547d%26mpshare%3D1%26scene%3D1%26srcid%3D0519zDB6xMYAF4ngzRIWXnOh%26sharer_shareinfo%3Df8fcd0062f40cb6f015489116ffff607%26sharer_shareinfo_first%3Df8fcd0062f40cb6f015489116ffff607%23rd&s=obsidian)