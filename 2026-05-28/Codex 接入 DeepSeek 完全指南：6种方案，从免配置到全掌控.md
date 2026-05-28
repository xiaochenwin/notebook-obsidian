---
author: 小满
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzcwNjE3NDkyNg==&mid=2247483875&idx=1&sn=f5f3e0700b2251bcd67acf5961f264d7&chksm=f5eee9e87475ed67280ae1c17f72be760f491edc14da1f02c3ac22e085f7d6efbaffe60f2346&mpshare=1&scene=1&srcid=05285UeJc0XzoDp7nOnnviqC&sharer_shareinfo=4253475c28476a5a89e8002047a3b099&sharer_shareinfo_first=4253475c28476a5a89e8002047a3b099#rd
saved: 2026-05-28 08:33:27
tags:
  - 笔记同步助手
id: 3bfc7fe3-a0fe-41c5-829c-abe0deb59674
---

公众号名称：小满造物

作者名称：小满

发布时间：2026-05-25 16:16

前几天，DeepSeek V4 Pro 宣布永久降价到原价 1/4；同一周，Codex 也推了一波大更新。

一个是便宜下来的强模型，一个是越来越好用的代码 Agent。很多人第一反应是：能不能让 Codex 直接用上 DeepSeek？

答案是：能，但中间需要多走一步。

本文整理了目前社区里 6 种主流方案：有本地代理，有云端中间层，也有桌面壳。你不用理解所有底层细节，按自己的需求选就行。

# **/**方案全景图**/**

一张图，同时解决两个问题：「有哪些方案」和「我该选哪个」。

![[笔记同步助手/images/3e957389e6fb2253dac0e1a8ede395b1_MD5.png]]

下面先从最推荐的 Moon Bridge 开始，给出完整手把手教程。其余方案只写核心步骤和适用场景。

1 **Moon Bridge：最稳方案**

**Moon Bridge 是一个 Go 写的本地代理。它对外提供 Responses API，收到 Codex 的请求后，转成 DeepSeek 能理解的格式，再把回复翻回 Codex 能读取的格式。**

我把它放在第一位，主要因为 DeepSeek 官方 `awesome-deepseek-agent` 文档直接给了 Codex 接入路径，覆盖中间各个关键步骤。

下面给两条路径：路径 A 最省事，适合直接让 AI 帮你配；路径 B 是手动版，适合想看清楚每一步的人。

### 1.1 路径 A：把这段话贴给 AI（推荐）

**先在本机终端设置环境变量，不要把 API Key 直接贴进聊天窗口。**

**还没有注册 API Key 的话，看这篇文章3分钟搞定。[DeepSeek API永久降价，普通人如何快速上手](https://mp.weixin.qq.com/s?__biz=MzcwNjE3NDkyNg==&mid=2247483861&idx=1&sn=719ef6a11cfca86e7c34b8b278ff004a&scene=21#wechat_redirect)**

> ● ● ●
> 
> \# macOS / Linux  
> export DEEPSEEK\_API\_KEY="sk-你的Key"
> 
> \# Windows PowerShell  
> $env:DEEPSEEK\_API\_KEY="sk-你的Key"

然后把下面这段话贴给能执行命令的 AI 工具：

> ● ● ●
> 
> 帮我在本地配置 Moon Bridge，把 Codex CLI 接入 DeepSeek V4 Pro。
> 
> 我的 API Key 已写入本机环境变量 DEEPSEEK\_API\_KEY。不要让我把 Key 贴进聊天窗口。读取环境变量后，生成本地 config.yml，并确保这个文件不要提交到 Git，截图时也要打码。
> 
> 请完成：
> 
> 1\. 检查 Node.js ≥18、Go ≥1.25、Codex CLI 是否已安装。
> 
> 2\. 克隆 https://github.com/ZhiYi-R/moon-bridge.git。
> 
> 3\. 参考 DeepSeek 官方 awesome-deepseek-agent 的 Codex 文档创建 config.yml，使用 DeepSeek Anthropic 端点和 127.0.0.1:38440 端口。
> 
> 4\. 启动 Moon Bridge。
> 
> 5\. 生成 ～/.codex/config.toml 和 models\_catalog.json，确保 wire\_api = "responses"。
> 
> 6\. 重要：写入 ～/.codex/config.toml 时必须保持合法 TOML 多行格式，不能把所有配置压成一行，且禁止用会丢失换行的字符串拼接方式。
> 
> 7\. 用 Get-Content 逐行打印 config.toml 前 30 行确认格式；如果发现第 1 行包含多个配置项，必须立即重写。
> 
> 8\. 用 curl 或 Invoke-RestMethod 测试 http://127.0.0.1:38440/v1/responses 是否正常返回。
> 
> 9\. 额外测试 http://127.0.0.1:38440/v1/models，确认返回中包含 provider=deepseek、model=deepseek-v4-pro、slug=moonbridge。
> 
> 10\. 读取 moon-bridge/logs/moonbridge.err.log 最近 100 行，确认是否出现 request\_model=moonbridge、actual\_model=deepseek-v4-pro、provider=deepseek 或 model=deepseek-v4-pro。
> 
> 注意：
> 
> 不要用浏览器打开 http://127.0.0.1:38440/v1 判断是否成功。/v1 是 API base URL，不是网页首页，返回 404 page not found 是正常的。
> 
> 如果报错，请优先检查：
> 
> \- Moon Bridge 是否启动
> 
> \- API Key 是否正确
> 
> \- DeepSeek 账户是否有余额
> 
> \- config.toml 的 base\_url 是否指向本地代理
> 
> \- 是否使用了新版 Codex 需要的 wire\_api = "responses"
> 
> \- config.toml 是否被错误写成单行
> 
> 完成后告诉我：
> 
> 1\. Moon Bridge 是否启动成功。
> 
> 2\. ～/.codex/ 下生成了哪些文件。
> 
> 3\. /v1/responses 测试是否通过。
> 
> 4\. /v1/models 返回的 provider、model、slug 分别是什么。
> 
> 5\. 日志中 Codex 请求模型名是什么，Moon Bridge 实际上游模型是什么，上游 provider 是什么。
> 
> 6\. 是否可以确认当前 Codex CLI 实际接入的是 DeepSeek V4 Pro。

正常情况下，AI 会在几分钟内完成配置。你只需要看最终检查结果，不需要自己逐行敲命令。

![[笔记同步助手/images/9b50671c99bc5a05977faaa483f26d15_MD5.png]]

### 1.2 路径 B：手动配置（3 步）

**如果你想自己配，流程其实也不复杂：拉代码、启动代理、验证 Codex 能不能连上。**

**前置条件**：Node.js 18+、Go 1.25+、Codex CLI、DeepSeek API Key。

### 第一步：下载 Moon Bridge

```
1git clone https://github.com/ZhiYi-R/moon-bridge.git
2cd moon-bridge
```

然后新建 `config.yml`。配置文件建议直接参考 DeepSeek 官方 `awesome-deepseek-agent/docs/codex.md` 里的 Codex 示例，把里面的 API Key 换成你自己的 Key。

### 第二步：启动代理

```
1go run ./cmd/moonbridge --config config.yml
```

看到本地端口 `127.0.0.1:38440` 启动成功，就说明 Moon Bridge 已经跑起来了。

接着按照README 的说明，生成 Codex 配置文件。这一步会在 `～/.codex/` 下写入 `config.toml` 和 `models_catalog.json`，让 Codex 知道该去哪里找模型。

### 第三步：验证是否可用

先测试 Moon Bridge 本身：

```
1curl http://127.0.0.1:38440/v1/responses \
2  -H "Content-Type: application/json" \
3  -d '{"model": "moonbridge", "input": "打个招呼", "max_output_tokens": 100}'
```

如果能正常返回内容，再进入一个测试项目，启动 Codex：

```
1cd 你的测试项目路径
2codex --cd "$PWD"
```

第一次不要让它改文件，只让它读项目结构：

```
1阅读这个项目的结构，告诉我入口文件在哪。不要改任何文件。
```

如果 Codex 能正常回答，说明链路已经打通。

CLI 通了，Codex App 通常也能用同一份 `～/.codex/` 配置。只要 Moon Bridge 在后台跑着，打开 App 后在模型列表里选择对应模型即可。

日常使用时，可以把 Moon Bridge 设为开机自启。之后打开 Codex，就不需要每次手动启动代理了。

---

2**其他 5 种方案**

如果 Moon Bridge 的 Go 环境配置对你来说太重，或者只是想快速试一下，可以看下面 5 种轻量方案。

### 2.1

## OpenRouter：不跑本地服务

Open Router 是云端 API 中间层，已经提供 Responses API Beta 支持。你不需要在本地跑代理，只要在 Codex 配置里把 provider 指向 Open Router，再填入`OPENROUTER_API_KEY`即可。

适合：只想快速试水，不想折腾本地环境。

注意：Open Router 的 Responses API 目前仍是 Beta，复杂多轮 tool call 可能不如本地 bridge 稳定，不建议一上来就当长期主力。

### 2.2

## codeproxy-ai/cli：一行 npx 快速试跑

这是最快的本地代理方案之一。启动方式大致是：

```
1npx @codeproxy/cli --base-url https://api.deepseek.com/v1 \
2  --model deepseek-v4-flash \
3  --apikey sk-你的Key
```

启动后将Codex的`config.toml` 指向本地代理，并把 `wire_api` 设为 `responses`。

适合：今晚就想跑通，先验证 Codex+DeepSeek 能不能用。

### 2.3

## codex-relay：适合 Python 用户

codex-relay 是一个轻量代理，可以用 `pip install` 安装。启动后，再按它打印出来的配置写入 `～/.codex/config.toml`。

适合：习惯 Python 环境，不想装 Go，又希望保留比较完整的 tool call 或者 model metadata 支持。

### 2.4

## codex-bridge：更重视 thinking mode

codex-bridge是Node.js 单文件代理，重点处理 DeepSeek 的`reasoning_content` 缓存和回放。这个细节很重要，因为 thinking mode 下的 tool call 很容易在这里出问题。

适合：明确想用 DeepSeek 的深度思考能力，并且愿意按 README 配置 `.env`、`config.toml` 和本地代理地址。

### 2.5

## VibeAround：图形界面方案

VibeAround 是一个桌面应用，内置协议桥接层，可以统一管理 Codex CLI、Claude Code、Gemini CLI 等多个 coding agent。

它不是 Codex 官方桌面版的替代，而是一个自己的桌面壳。适合不想碰终端、同时又想管理多个 agent 的用户。

---

# **/**常见踩坑与排错**/**

| 症状 | 可能原因 | 怎么办 |
| --- | --- | --- |
| `connection refused` | Moon Bridge 没启动 | 确认代理正在运行，端口是 `38440` |
| `401` | API Key 不对 | 检查 Key 是否完整，有没有多余空格 |
| `402` | DeepSeek 账户余额不足 | 去 DeepSeek 控制台充值或检查余额 |
| `404` | Codex 没有请求到本地代理 | 检查 `config.toml` 里的 `base_url` 是否指向本地代理 |
| `/model`看不到模型 | Codex 配置没生成好 | 重新生成 `config.toml` 和 `models_catalog.json` |
| thinking mode 下 tool call 报错 | bridge 没处理好 `reasoning_content` | 换支持 thinking round-trip 的方案，比如 Moon Bridge 或 codex-bridge |
| 照旧教程配置失败 | 旧教程还在用 `wire_api="chat"` | 新版 Codex 认准 `wire_api="responses"` |
| 流式输出断连 | 网络或代理 SSE 处理不稳定 | 先用 `curl` 测试代理本身是否能正常返回 |

# **/**写在最后**/**

为什么 Codex 不能直接填 DeepSeek 的 `base_url`？

背后原因其实很简单，两者的协议不同：Codex 新版主要走 OpenAI Responses API；DeepSeek V4 官方提供的是 Chat Completions 兼容接口和 Anthropic 兼容接口，不是 Responses API。

所以这事不是改个 `base_url` 就能解决。中间还差一层协议适配：把 Codex 发出的请求，翻成 DeepSeek 能理解的格式；再把 DeepSeek 的回复，翻回 Codex 期待的格式。

这篇文章里的 6 种方案，本质上都是在做这件事：有的是本地代理，有的是桌面壳内置 bridge，也有 OpenRouter 这种云端中间层。

如果只选一个，我建议先试 Moon Bridge。它不是最轻量的方案，但路径最清楚，也更适合长期使用。

最后说一句容易搞混的事：这篇文章讲的是**Codex**怎么接入DeepSeek。如果你用的是**Claude Code**，可以直接走CC-Switch，不需要折腾协议桥接。具体看这篇就行 [别再折腾DeepSeek-TUI了！70K+星的CC-Switch才是真的省心](https://mp.weixin.qq.com/s?__biz=MzcwNjE3NDkyNg==&mid=2247483831&idx=1&sn=8880df860a9b44872e1729edd712fa90&scene=21#wechat_redirect)

---

![[笔记同步助手/images/15cf13d2ede6f5597c8e6494ede4d721_MD5.jpg|cover_image]]

原创 小满 小满造物

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/a9cf6c37_1779928405916?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzcwNjE3NDkyNg%3D%3D%26mid%3D2247483875%26idx%3D1%26sn%3Df5f3e0700b2251bcd67acf5961f264d7%26chksm%3Df5eee9e87475ed67280ae1c17f72be760f491edc14da1f02c3ac22e085f7d6efbaffe60f2346%26mpshare%3D1%26scene%3D1%26srcid%3D05285UeJc0XzoDp7nOnnviqC%26sharer_shareinfo%3D4253475c28476a5a89e8002047a3b099%26sharer_shareinfo_first%3D4253475c28476a5a89e8002047a3b099%23rd&s=obsidian)