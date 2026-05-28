---
author: 图灵沿界
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk0NjY1ODk0MQ==&mid=2247488553&idx=1&sn=656d13f0da3ef2cd9af995f6f37c836b&chksm=c2904b38c293b8a255f6869da1d091e7626c00ccfbfa035f83b51f08ddd50ed88db9725fd417&mpshare=1&scene=1&srcid=0528zZmizZKmAzTC2aKq6gE5&sharer_shareinfo=8f52b1554c884ae0c6ef5112e95d8526&sharer_shareinfo_first=8f52b1554c884ae0c6ef5112e95d8526#rd
saved: 2026-05-28 13:28:12
tags:
  - 笔记同步助手
id: 18fcd14d-b58d-40db-b2b2-46875a7de68a
---

公众号名称：图灵沿界

作者名称：图灵沿界

发布时间：2026-05-22 09:22

> 导读  
> 【导读】一位国内开发者在 X 上发布教程，演示如何让 Codex 同时保留 ChatGPT 登录、接入第三方 Provider 中转站，并用手机端 ChatGPT 远程控制桌面 Codex——帖子发出不到一天，超过 5 万人围观。这背后指向一个正在成型的趋势：AI coding agent 的竞争焦点，已经从模型能力延伸到了账号体系、运行环境、移动审批和模型供应的全链路组合。

## 一条教程，三个能力叠加

5 月 16 日，开发者 Ray Wang 在 X 上发了一条中文帖：

> "亲测可用，快速教你 Codex 配置保留 ChatGPT 登陆的同时使用第三方 Provider；即使是 Free 账户也可以接入中转站，然后在手机上用 ChatGPT 远程控制桌面 Codex。"

![[笔记同步助手/images/014abd33930a733b2f596e3ff703146c_MD5.jpg]]

▲ Ray Wang 的 X 主帖，采集时已超 5 万次浏览

帖子附带了一段视频教程，评论区迅速聚集了一批关注 Codex 工作流的开发者。

这条帖子之所以引起关注，在于它把 Codex 的三个独立能力串到了一起：

**第一层：用 ChatGPT 账号登录 Codex。**不需要单独申请 API key，直接用已有的 ChatGPT 订阅计划。

**第二层：模型请求走第三方 Provider/中转站。**通过修改配置文件，把 Codex 的模型调用指向非 OpenAI 的后端。

**第三层：手机端 ChatGPT 远程控制桌面 Codex。**人不在电脑前，也能用手机发指令、审批命令、看 diff。

三层叠加之后，Codex 从一个"桌面终端里的 coding agent"变成了**可遥控、可替换模型供应、绑定 ChatGPT 生态的移动开发入口**。

## 官方文档怎么说？每一层都有据可查

这三个能力并非凭空冒出来的。OpenAI 官方文档对每一层都有明确的技术支撑。

**ChatGPT 登录**

OpenAI Help Center 写得很明确：

> "Codex is included with ChatGPT Plus, Pro, Business, and Enterprise/Edu plans."

「Codex 包含在 ChatGPT Plus、Pro、Business 和 Enterprise/Edu 计划中。」

> "For a limited time Codex is included with ChatGPT Free and Go, and all other plans enjoy 2x rate limits."

「限时期间，Codex 也包含在 ChatGPT Free 和 Go 计划中，其他所有计划享受 2 倍速率限制。」

![[笔记同步助手/images/3dd6742794537b1e7372a0a2f3444e1b_MD5.jpg]]

▲ OpenAI Help Center 页面，明确了 Codex 与 ChatGPT 各计划的绑定关系

也就是说，**Free 用户目前也能用 Codex，但这是限时福利**，而且使用量计入 agentic usage limit。Codex CLI 首次运行时会提示登录，支持 ChatGPT 账号或 API key 两种认证方式。

**自定义 Provider/Proxy**

OpenAI Developers 的 Advanced Configuration 文档明确支持自定义模型供应商：

> "A model provider defines how Codex connects to a model (base URL, wire API, authentication, and optional HTTP headers)."

「一个 model provider 定义了 Codex 连接模型的方式——包括 base URL、接口协议、认证方式和可选的 HTTP headers。」

![[笔记同步助手/images/5c1ed1aeb6d3cd3cf07d18f9149d435b_MD5.jpg]]

▲ OpenAI Developers 文档中的 Custom model providers 配置说明

如果只是想把内置的 OpenAI provider 指向一个 LLM proxy 或 router，可以直接设置 \`openai\_base\_url\`；如果需要完全自定义的 provider，则可以在 \`config.toml\` 中定义 \`base\_url\`、\`env\_key\`、认证方式等。

![[笔记同步助手/images/3c9a2b085b0f0f97338c33dbd219efbe_MD5.jpg]]

▲ Sample Configuration 页面，展示了配置文件的完整结构，包括 \`requires\_openai\_auth\` 和 \`experimental\_bearer\_token\` 等字段

Ray Wang 在回复中给出的配置片段正是基于这套机制：

\`\`\`toml model\_provider = "apiname"

\[model\_providers.apiname\] name = "..." base\_url = "..." experimental\_bearer\_token = "..." requires\_openai\_auth = true \`\`\`

关键在最后一行——\`requires\_openai\_auth = true\` 让 Codex 在使用第三方 provider 的同时，依然保持 ChatGPT 登录态。

**手机远程控制**

OpenAI Developers 的 Remote connections 文档描述了这个能力：

> "Remote connections let you use Codex when you are away from the machine that runs it."

「远程连接让你在离开运行 Codex 的机器后，仍然可以继续使用它。」

> "Connect the ChatGPT mobile app to a Codex App host."

「将 ChatGPT 移动端应用连接到 Codex App 主机。」

![[笔记同步助手/images/5a12f0222b9ce6bc9ec9615b60b9dbd5_MD5.jpg]]

▲ OpenAI Remote connections 文档页面，展示了手机端扫码连接 Codex 的流程

连接之后，手机端可以做的事情包括：启动/继续线程、发后续指令、批准命令和操作、查看代码 diff/测试结果/终端输出/截图，以及接收通知。

但前提条件同样值得注意：**主机必须是 Mac、保持唤醒和在线状态、正在运行 Codex App、使用同一账号和 workspace。**目前 mobile setup flow 只能从 macOS 的 Codex App 发起，CLI 和 IDE Extension 暂不支持。

## 第三方中转站：开发者在尝试什么？

Ray 在评论区推荐了一个第三方 relay 服务——Upthos Relay，自称提供 Claude、Codex、Gemini 的统一路由。

![[笔记同步助手/images/286ab150b23f23dbf1d2266c6f042806_MD5.jpg]]

▲ Upthos Relay 首页，打出"One API. Every Model."的口号

这类中转站的卖点通常是：统一 API 接口、透明计费、多模型切换。对国内开发者来说，还有一个更现实的吸引力——**绕过直连 OpenAI API 的网络和额度限制**。

但需要强调的是：**OpenAI 官方支持的是"自定义 provider"这个配置能力本身，每个具体 relay 服务的安全性、合规性、稳定性，都需要开发者自己判断。**Upthos 页面上标注的 latency、zero-data retention、SOC2 等均为服务商自述，没有经过独立审计验证。

模型请求走第三方 relay 意味着你的 token、代码上下文、工具输出都会经过对方服务器。在涉及生产代码和企业凭据的场景下，这个决策需要谨慎评估。

## 评论区的真实反馈：能连上，但坑也不少

帖子下面的讨论暴露了不少实际使用中的摩擦点。

**历史对话不同步。**有人问 Codex 的对话记录是否会和 ChatGPT 同步，Ray 明确回复："目前账号的历史对话不同步。"这说明 ChatGPT 和 Codex 的会话体系仍然是分开的。

**配置切换容易出问题。**有人问能不能用 \`cc switch\` 命令切换 provider，Ray 建议手动调整更稳，因为 \`cc switch\` 可能会改动配置文件或切掉登录态。

**插件和 Marketplace 可能失效。**GitHub issue #22466 报告了一个具体场景：用 ChatGPT 登录 + 自定义 provider（通过 \`env\_key\` 认证）时，模型请求本身能成功，但插件发现和 Marketplace 功能可能失败。

**启动延迟。**GitHub issue #17531 报告了另一个场景：使用自定义 localhost provider + \`requires\_openai\_auth = true\` + API key 认证时，Codex 启动存在固定延迟。

**Tool calling 兼容性存疑。**评论区有开发者关心：如果把模型请求路由到 Claude，tool calling 的格式是否兼容？长时间 agent session 的 rate limit 怎么处理？这些问题目前没有标准答案。

这些反馈指向一个共同的结论：**三层能力各自可用，但串联起来时的边界问题还没有被充分验证。**

## 更大的图景：Codex 正在被拆成可组合的层

回到这件事本身，Ray Wang 的这条教程折射出的趋势比教程本身更值得关注。

AI coding agent 的竞争早已不只是"谁的模型更强"。Codex 正在被开发者拆解成几个可独立替换的层：

-   **身份层**
    
    ：ChatGPT 登录、订阅计划、workspace 权限、Remote Control 授权
    
-   **执行层**
    
    ：桌面 Codex App 或 CLI，本地文件系统、终端、测试、审批都在 host 上
    
-   **模型供应层**
    
    ：OpenAI 内置 provider、OpenAI-compatible proxy/router、自定义 model provider、第三方 relay
    
-   **控制层**
    
    ：ChatGPT mobile app 发指令、批准命令、查看 diff/test/terminal output
    

当这些层可以独立配置和替换时，开发者就可以做出各种组合：用 ChatGPT 的账号体系管权限，用第三方 relay 省成本或切模型，用手机审批让 agent 在桌面持续运行。

国内开发者之所以率先折腾这套组合，背后的驱动力一目了然——**他们需要同时解决访问、成本、额度、移动审批和本地环境执行这五个问题，而没有任何单一官方方案能一步到位。**

## 风险清单：折腾之前先看清楚

在动手配置之前，这几个风险点需要明确认知：

1.**Free 账户是限时的。**OpenAI 官方写明 "for a limited time"，随时可能收回，且使用量有 agentic usage limit 上限。

2.**第三方 relay 的数据安全没有保障。**模型请求、代码上下文、工具输出都会经过 relay 服务器，服务商的安全承诺属于自述。

3.**手机控制的安全边界在 host 上。**Remote access 使用的是主机上的项目、线程、文件、凭据、权限、插件、浏览器配置和本地工具——手机只是一个远程窗口。

4.**自定义 provider 的兼容性没有完整保证。**模型请求能通不代表插件发现、MCP 同步、Remote sync 都正常工作。

5.**账号条款风险。**通过第三方 relay 中转模型请求是否符合 OpenAI 的使用条款，目前没有明确的官方说法。开发者在评论区提到的接码、2FA 等账号验证方式，更是灰色地带。

**这条路线目前的定位是"开发者折腾路线"，适合愿意踩坑和调试的人，而非开箱即用的官方方案。**

---

— END —

> — END —

---

![[笔记同步助手/images/a15607c311d65b3995a98e905689d224_MD5.jpg|cover_image]]

原创 图灵沿界 图灵沿界

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/39d153e2_1779946090179?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk0NjY1ODk0MQ%3D%3D%26mid%3D2247488553%26idx%3D1%26sn%3D656d13f0da3ef2cd9af995f6f37c836b%26chksm%3Dc2904b38c293b8a255f6869da1d091e7626c00ccfbfa035f83b51f08ddd50ed88db9725fd417%26mpshare%3D1%26scene%3D1%26srcid%3D0528zZmizZKmAzTC2aKq6gE5%26sharer_shareinfo%3D8f52b1554c884ae0c6ef5112e95d8526%26sharer_shareinfo_first%3D8f52b1554c884ae0c6ef5112e95d8526%23rd&s=obsidian)