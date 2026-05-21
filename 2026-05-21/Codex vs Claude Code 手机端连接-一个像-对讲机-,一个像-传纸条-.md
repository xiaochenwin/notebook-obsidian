---
author: Dylan
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzIyMTUyMTU5Mg==&mid=2247484473&idx=1&sn=399cdab26472bde3e8433988e3a26468&chksm=e9f8227b6a7a659e2872af59b3112598ab79b0738692852c15903e65782fbae438c239e172ac&mpshare=1&scene=1&srcid=052142QBMFfp0LnkR4FvmK8g&sharer_shareinfo=24d46c9909a1300d3585acb12563d05a&sharer_shareinfo_first=24d46c9909a1300d3585acb12563d05a#rd
saved: 2026-05-21 07:41:20
tags:
  - 笔记同步助手
id: a04f6825-ef1b-4490-9eb7-2fad8215b30a
---

公众号名称：碳基 Agent

作者名称：Dylan

发布时间：2026-05-15 13:59

一觉醒来，ChatGPT App 把 Codex 塞进了手机端，从此 Codex 用户也可以对着手机巴拉巴拉讲话，然后让电脑上的 Codex 干活了。

遥想 “AI 上古时代”，大家还在用 SSH/Happy Coder 等第三方方案来实现手机控制电脑上的 AI 干活。后来 Claude Code 推出了 Remote Control，手机上的 Claude App 可以指挥电脑上的 Claude Code 干活。

至此 OpenAI 和 Anthropic 都让自家的“AI 程序员”上了手机。听起来差不多，但真用起来会发现，它俩的思路其实挺不一样的。

​

Codex 如何使用

​

怎么用呢？首先需要把手机上的 ChatGPT 和电脑上的 Codex 升级到最新版本，打开手机 ChatGPT 左侧栏的 Codex，会提示你去电脑上设置。

打开电脑 Codex，会出现如下界面：

![](https://relay-1.bijitongbu.site/p/2f30f83e8dc899edca581ca295e8b576.png)

## 点击 Get Started，设置 Codex 移动版，跟着界面提示一步步往下走：

![](https://relay-1.bijitongbu.site/p/3b7fa32cc52e295eba3b2cabe718d99a.png)

## 设置成功后，就可以在手机端看到连接成功的标志了。

![](https://relay-1.bijitongbu.site/p/32fa6a1ef8d0fe9f5659e6cd62011ec8.png)

## 本质相同：手机只是“遥控器”

无论是 Codex 内置到手机 ChatGPT 还是 Claude Code Remote Control，两者的核心理念是一致的：**手机本身不执行代码，执行环境留在本地机器，移动 App 只是同一个 live session 的另一个交互前端。**

Anthropic 官方明确把这定位为“continue a local Claude Code session from your phone, tablet, or any browser”，和 Codex 的 relay 思路如出一辙。

两者都强调几个共同点：

​

-   文件、凭证、MCP/插件配置、本地环境都不上云
    
-   手机只承担渲染对话、发指令、审批权限的角色
    
-   实际的读写文件、执行命令、调用 MCP server 全部发生在用户的开发机上
    

简单说，手机就是一个“遥控器”，真正干活的还是你家里那台电脑。

​

## 关键差异：连接架构

这是两者技术实现上最关键的不同。打个比方：

​

### Codex：像“对讲机基站”

想象你家里有一台一直开着的电脑，AI 正在上面帮你干活。现在你出门了，想用手机看看它干得怎么样，或者临时让它换个方向。

Codex 的做法，有点像装了一个**“对讲机基站”**。OpenAI 在中间架了一个一直在线的中转站（secure relay 层），你的电脑和你的手机都接到这个基站上。只要你用同一个 ChatGPT 账号登录，手机一打开就能直接“喂？在吗？”——电脑那边正在做什么、卡在哪一步、要不要你批准下一步，全都实时显示在手机上。

感觉上，**手机和电脑就是同一个房间里的两块屏幕**。你甚至可以在通勤路上换个方向，电脑立马照办。

技术上说，这是一个“持久双向通道”, relay 负责保持机器可达性、同步 active session state，并让任何登录同一账号的设备看到同样的实时状态。

​

### Claude Code：像“传纸条”

Claude Code 的做法，更像是**“传纸条”**。

你的电脑主动给 Anthropic 的服务器递了一张纸条说：“我上线了，有事找我”。然后你的手机想说话，就把消息交给 Anthropic，Anthropic 再顺着这根线把消息传回你的电脑。

重点是——**你的电脑的门不允许被敲开**。所有对话都是电脑主动出门去问“有我的消息吗？”，而不是别人能直接敲你家门。安全感拉满，但相对就没那么“实时互动”的感觉。

技术上说，本地 Claude Code 进程主动向 Anthropic API 建立 outbound HTTPS 连接并注册 session，然后轮询 API 拉取来自手机/浏览器的指令。本机永远是连接的发起方，不开放任何入站端口。Anthropic API 充当的是消息中继（does not store or execute code），文件和 MCP server 流量完全不经过它。

**一句话总结：Codex 是“relay 维持的双向常连接”,Claude Code 是“本地出站 + API 轮询消息桥”。**

​

## 配对方式：自动 vs 扫码

### Codex：登录即用

Codex 这边很省心，基本是**“登录即用”**。你手机上的 ChatGPT App 一升级，只要账号一样，电脑上 Codex 在干嘛，手机自己就同步出来了，不需要额外操作。登录同一 ChatGPT 账号的手机，会自动加载所连机器上 Codex 的实时状态（已有 thread、待审批、插件、项目上下文），桌面端和移动端被视为同一身份下的多个入口。

​

### Claude Code：扫码握手

Claude Code 则需要一个**“扫码握手”的小仪式**。

你要在电脑终端敲一行命令 `claude remote-control` 启动 server 模式，然后按一下空格，屏幕上蹦出一个二维码，拿手机扫码连接。或者使用生成的 URL 在 claude.ai/code 网页端打开。

每台机器同一时间只能开一个这样的连接，有点像你家 WiFi 一次只让一台手机连。Session 会在 iOS App 的 Code Tab 里显示为 “Remote Control Session (Mac)” 之类的条目。

​

## 并发能力：全局视图 vs 单会话

### Codex：全能管家

Codex 比较**“全能管家”**风格。你可以在手机上同时看好几台机器、好几条对话线，比如笔记本在跑 A 任务、公司 Mac mini 在跑 B 任务、还连着公司的远程开发机在跑 C 任务，这些全都在手机里一览无余，随时切换。

Codex 强调“work across all of your threads”，手机可同时看到多机器、多 thread 的状态，跨设备无缝切换，Remote SSH 主机也通过同一 relay 接入。

​

### Claude Code：一对一私聊

Claude Code 目前更像**“一对一私聊”**。

一台电脑一次就一个会话，你想在这台机器上同时干两件事？暂时还不行。而且每做一个动作，手机基本都要你点一下“同意”，防止 AI 自己瞎跑——安全是安全，但偶尔会觉得有点啰嗦。

社区反馈显示，重启本地程序会让已有 session 返回神秘的 API 错误而非优雅地告知 session 已终止；早期版本对 `--dangerously-skip-permissions` 也不生效，意味着每个新动作都需要在手机上手动审批。

​

## 安全模型：门禁 vs 只出不进

两家都强调“你的代码、密码、文件都不出你电脑”、“不暴露入站端口”，但侧重点不一样。

​

### Codex：有门禁的高级公寓

Codex 像一个**有门禁的高级公寓**：OpenAI 维护着一份“可信住户名单”，你的设备都登记在册，中转站负责让自己人能找到彼此，外人进不来。通过 OAuth/账号身份把可信机器跨设备暴露给同账号设备，接近“私有 mesh + 审计审批”。

​

### Claude Code：只出门、不开门

Claude Code 更像**“我家电脑只出门、不开门”**。

安全卖点是“outbound-only, no inbound ports”、“short-lived credentials, expire independently”、“per-action approval required”——更接近“零信任的临时凭据 + 每操作授权”。

你的电脑只主动往外打电话，绝不接陌生来电，攻击面更小。

​

## 成熟度与稳定性

### Codex：成品套装

Codex 这次是 OpenAI 一整套打包发布的——手机端、桌面端、远程开发机、企业级权限管理（配套 Hooks GA、可编程访问 token、HIPAA 本地合规等企业向能力）一起上，显得很“成品”。

​

### Claude Code：持续打磨中

Claude Code 的远程控制 2 月份刚上线那会儿还挺糙的，网上能搜到一堆吐槽：动不动掉线、报错 500、要反复确认。

最近几个月一直在打补丁：

​

-   3月加了 Schedule recurring tasks in Cowork（定时任务，但要求电脑唤醒且 Claude Desktop 打开）
    
-   3月底加了 Claude Code auto mode（更安全地跳过权限审批）
    
-   5月的社区讨论显示 Remote Control 已被列为“mobile Claude Code”的主流官方选项之一
    

但社区里大家还会拿一些第三方工具（比如 slopus/happy、Happy Coder、SSH+Tailscale）跟它对比着用，说明还在成熟过程中。

​

## 小结

**Codex 从手机端到电脑端的设置都很简单，基本上只要登录了同一个 ChatGPT 账号，就能无缝地在手机端和电脑端切换，纯纯的互联网应用体验。**

**而 Claude Code 的玩法感觉就像是专门给搞技术提供的方案，你需要知道 Claude Code 中的哪个 Session 正在被手机控制，没有设置的 Session 就无法在手机上操作。**

**显然 Codex 的做法更简单易用，叠加 GPT-5.5 模型能力已经几乎逼平 Opus 4.6，为了 Coding Agent 头把交椅会不会易主，还真是不好说。**

---

![cover_image](https://mmbiz.qpic.cn/sz_mmbiz_jpg/GibojqibaGeT1zInOWOwRXibpNp3wct7cU4nvgMvabkkYhsAaaO4eeVd8fP9CW8KPm2kicv2ZSV7fjNAZZR7WhHxqtialsicG664eNI5toMxjnhYM/0?wx_fmt=jpeg)

原创 Dylan 碳基 Agent

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/d1735088_1779320479359?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzIyMTUyMTU5Mg%3D%3D%26mid%3D2247484473%26idx%3D1%26sn%3D399cdab26472bde3e8433988e3a26468%26chksm%3De9f8227b6a7a659e2872af59b3112598ab79b0738692852c15903e65782fbae438c239e172ac%26mpshare%3D1%26scene%3D1%26srcid%3D052142QBMFfp0LnkR4FvmK8g%26sharer_shareinfo%3D24d46c9909a1300d3585acb12563d05a%26sharer_shareinfo_first%3D24d46c9909a1300d3585acb12563d05a%23rd&s=obsidian)