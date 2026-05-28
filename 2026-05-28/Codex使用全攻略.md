---
author: AI德才
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzI2ODIwMDY4OA==&mid=2247483909&idx=1&sn=f7ea1212e735d17b4f86064a4b0be721&chksm=eb02883349aac75fdc03a85eb9c536df115acc207a5088dfd7d1478d6f6dfbef58a55cda345a&mpshare=1&scene=1&srcid=0528a0BSwLeeJ8FPvuCV5qbo&sharer_shareinfo=81aef38690bd6e66d9463dc6c71b15b0&sharer_shareinfo_first=81aef38690bd6e66d9463dc6c71b15b0#rd
saved: 2026-05-28 08:32:34
tags:
  - 笔记同步助手
id: 315ff3a2-7eb7-4d87-ade9-8d1c99852e92
---

公众号名称：AI 打工搭子

作者名称：AI德才

发布时间：2026-05-23 08:00

Codex上手全攻略：5分钟从安装到干活

上一篇文章聊了Codex重生背后的商业逻辑，有读者后台问：道理我都懂，但到底怎么用？

这篇文章就讲实操。我翻了掘金、CSDN、头条上几十篇博主教程，把最常见的坑、最好用的技巧、最省心的配置方案全整理出来，帮你少走弯路。

# 四条路，选一条走就行

Codex有四种运行模式，覆盖你能想到的所有场景：

-   CLI（命令行）：终端里跑，适合命令行党，黑框里掌控全局
    
-   App（桌面应用）：有图形界面，支持macOS和Windows，适合不想跟终端互相折磨的人
    
-   Web（网页版）：打开浏览器就能用，不用装任何东西，出差临时改代码随开随用
    
-   IDE插件：支持VS Code、JetBrains、Cursor、Windsurf，写代码时直接在编辑器里调用
    

怎么选？终端党用CLI，鼠标党用App，临时救火用Web，天天写代码用IDE插件。别纠结入口，工具不是对象，不需要从一而终。

![[笔记同步助手/images/1ef936cb6bbb4e572dac476092dd4afc_MD5.png]]

# Codex官方产品页：云端版与CLI版

# 安装：从最简单的开始

## 方案一：桌面App（推荐新手）

直接访问 chatgpt.com/codex ，点那个大大的"Download"按钮就行。

Mac用户双击DMG安装，一步到位。Intel芯片的老Mac用户注意——官方原版DMG默认不兼容，但GitHub社区有解决方案：去开源项目 ersione/codex-intel-mac 跑一遍重新打包脚本，几分钟就能生成专属安装包。

Windows用户也有正式版了，5月刚上线的。下载链接在OpenAI官网，搜索"Codex download Windows"即可找到。

装好后登录ChatGPT账号，浏览器授权一下，看到你的邮箱出现在设置面板里就说明通了。

一个关键坑：如果你之前为了接第三方模型，在本地写过base\_url和私有API Key，必须先清掉。不然Codex启动后还是走私人接口，额度烧完还得自己掏钱。打开终端，备份后编辑～/.codex/config.toml，把自定义的代理地址、base\_url、API Key全删干净，保存退出。这一步是享受官方免费额度的前提。

## 方案二：CLI（适合开发者）

安装就一条命令：

```
npm install -g @openai/codex
```

macOS用户也可以：brew install --cask codex

国内网速慢的话加个镜像源：

```
npm install -g @openai/codex --registry=https://registry.npmmirror.com
```

装完验证：codex --version，看到版本号就成功了。

登录有两种方式：推荐用codex login，浏览器授权；也可以手动设环境变量OPENAI\_API\_KEY，但这个按token计费，适合已经习惯OpenAI API的用户。

## 方案三：网页版

最省事——直接访问 chatgpt.com/codex/cloud ，不用装任何东西，登录ChatGPT账号就能用。适合出差、借别人电脑临时改代码的场景。

## 方案四：IDE插件

VS Code用户点击左侧"扩展"图标，搜索"OpenAI Codex"安装。JetBrains、Cursor、Windsurf同样有官方插件。装完后在编辑器里直接调用Codex，不用切窗口，代码上下文自动带过去。

![[笔记同步助手/images/39800a2d790fea3f6731d8f5c5afb7f1_MD5.png]]

Codex桌面App界面

# 权限模式：安全比效率重要

这是很多教程都没有重点讲、但我认为非常关键的部分。Codex能读写你的本地文件和执行命令，所以权限控制是第一道防线。

Suggest模式（默认）：最安全，也最保守。Codex可以读文件、给你提修改建议，但真正改文件或执行命令之前，需要你主动批准。好处是安全，坏处是你不能离开——每一步都得点确认。

Auto Edit模式：比默认稍微激进。如果Codex只是修改当前项目里的普通代码，或者执行安装依赖、跑测试这类常见命令，它会自动通过。但涉及删除文件、访问项目外目录、读取敏感文件，还是会停下来让你确认。适合日常开发里的连续任务，比如修Bug——Codex先读代码、改代码、跑测试、根据报错继续修改，不用每一步都来问你，但又不至于完全失控。

Full Auto模式：能力最强，风险也最高。Codex可以更自由地读写文件、执行命令，甚至访问项目外目录。但它在沙箱里运行（macOS用sandbox-exec，Linux用Docker容器），网络是断开的，跑不了rm -rf /，也发不出去你的数据。

我的建议：平时用Auto Edit，跑测试用Full Auto，陌生项目用Suggest。用完切回来，别长期开着最高权限。

![[笔记同步助手/images/16d472c35aa9ece5da404a8d1a93aa9d_MD5.png]]

Codex任务管理界面

# 怎么给Codex下指令：从踩坑到高效

## 新手最容易犯的错

一上来就说"帮我写个函数"——这种指令跟让实习生"随便写点什么"一样，结果肯定不靠谱。

## 正确姿势：任务驱动+三要素

好的指令应该包含三个要素：目标、约束、验收标准。

差的指令：

```
帮我写一个登录功能
```

好的指令：

```
帮我做一个用户登录系统：使用JWT认证，支持注册和登录接口，连接MySQL数据库，提供curl测试命令，确保注册时有邮箱格式校验
```

看到区别了吗？好的指令给了目标（用户登录系统）、约束（JWT、MySQL、邮箱校验）和验收标准（提供curl测试命令）。

## 四步最佳实践

这是多位博主总结出来的高效工作流，亲测好用：

第一步，指定范围。 不要让Codex在整个项目里瞎逛。你只想改登录页，就把登录页相关文件告诉它。在App里用@指定文件，在CLI里直接把路径写清楚。

第二步，指定状态。 明确告诉它是只读分析还是可以修改："先不要修改代码，只输出分析"或者"可以修改代码，但修改前先给我计划"。

第三步，指定验收标准。 比如："完成后确保npm run lint可以通过、相关测试可以通过、不引入新依赖、不修改无关文件"。你不给验收标准，它就只能按自己的理解收工——而AI的"我觉得完成了"和工程里的"真的完成了"，经常不是一回事。

第四步，随时中断。 发现Codex往奇怪方向走，别硬等。直接暂停，告诉它："暂停刚才的方向，你现在的理解有问题，正确目标是XXX。"方向不对要早纠偏，跟带实习生一个道理。

## 五个高频实战场景

场景一：修Bug。 直接把报错日志丢给它："帮我跑一下pytest tests/，看看报了什么错，然后修一下。"它会自己跑测试、读报错、定位代码、生成补丁、问你确认。切到Auto Edit模式更顺手。

场景二：批量修改。 10个Nginx配置文件里要把旧IP换成新IP？手动改15分钟，Codex一句话搞定："把/etc/nginx/conf.d/下面所有.conf文件里的192.168.1.100替换成10.0.0.50"，它改完还会自己跑nginx -t验证配置。

场景三：读懂别人的项目。 接手陌生项目时说一句"这个项目的认证模块是怎么实现的？梳理一下调用链"，它会读相关代码文件，给你一个清晰的说明，比你自己grep快多了。

场景四：补测试用例。 "给src/utils/全覆盖生成单测"，它自动生成高覆盖率的单元测试，还能反复迭代直到测试通过。

场景五：生成文档。 "为当前项目生成README.md文档，使用中文，包含项目介绍、环境要求、安装步骤、运行方法"，一个模板化的文档就出来了。

# AGENTS.md：给AI写一本"员工手册"

这是Codex最被低估的功能。在项目根目录放一个AGENTS.md文件，相当于给AI写了一份工作规范——用什么语言、用什么包管理器、缩进用tab还是空格、commit message怎么写、禁止做什么操作。每次对话自动加载，不用重复交代。

终端里敲/init就能一键生成模板，然后按需修改。

另一个实用功能是Chronicle记忆——Codex可以在不同会话之间持续携带关键的架构上下文、开发者偏好和复杂经验，不会每次对话都从零开始。以前它会在会话结束后"遗忘"一切，现在有了记忆，协作的连续性好很多。

# 国内用户怎么玩

没有ChatGPT Plus订阅？没关系，Codex CLI支持接入国内大模型。

用一个叫CC Switch的跨平台桌面工具，可以一键管理Codex的API供应商，自动改写配置。下载地址在GitHub：farion1231/cc-switch/releases。

以通义千问为例，在CC Switch里添加供应商，填入百炼的API Key和接口地址（dashscope.aliyuncs.com/compatible-mode/v1），选择模型（如qwen3.6-plus），保存即可。实测百炼的大模型可以用，硅基流动的不行。

当然，用国内模型在代码理解能力上跟GPT-5.5还有差距，但对于日常的脚本编写、配置修改、文档生成这些轻量任务，完全够用。

# 七个必知的坑

1.  登录报错：首次启动遇到"account/read failed during TUI bootstrap"，别硬刚，codex logout 再 codex login 就行
    
2.  手机号验证：国内+86号段不被支持，需要海外手机号
    
3.  项目太大变慢：别一次性改全部，分模块操作
    
4.  看执行日志：很多人只看结果，正确做法是看Codex的执行过程
    
5.  以为它不会错：它会写错代码，必须自己review、跑测试
    
6.  不给执行权限：Codex无法运行命令，检查chmod权限
    
7.  Node.js版本太老：CLI需要Node.js 18+，版本太低会报错
    

# 模型怎么选

如果你是ChatGPT Plus或Pro会员，Codex默认使用GPT-5.3-Codex模型，这是目前最强的编程模型。免费用户或$8/月的Go会员只能用GPT-5.2-Codex。

在CLI里用/model命令可以切换模型。App里在设置面板里选。日常轻量任务用默认模型就行，复杂重构、大型项目调GPT-5.5，推理能力更强。

# 一句话总结

Codex的核心价值不是替你写几行代码，而是帮你建立一套AI驱动的软件开发流程。从"你问，我答"到"你说，我做"，这才是AI编程工具真正的进化方向。

新手从App开始，先跑通第一个任务；进阶切CLI，学会AGENTS.md和权限控制；高手玩Automations和插件生态，把重复工作全自动化。

别指望一次就会，但试三次你就会发现——回不去了。

---

![[笔记同步助手/images/cf515bd3e3db41e7634e2a6b8db0c8f5_MD5.jpg|cover_image]]

原创 AI德才 AI 打工搭子

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/06e5e914_1779928352638?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI2ODIwMDY4OA%3D%3D%26mid%3D2247483909%26idx%3D1%26sn%3Df7ea1212e735d17b4f86064a4b0be721%26chksm%3Deb02883349aac75fdc03a85eb9c536df115acc207a5088dfd7d1478d6f6dfbef58a55cda345a%26mpshare%3D1%26scene%3D1%26srcid%3D0528a0BSwLeeJ8FPvuCV5qbo%26sharer_shareinfo%3D81aef38690bd6e66d9463dc6c71b15b0%26sharer_shareinfo_first%3D81aef38690bd6e66d9463dc6c71b15b0%23rd&s=obsidian)