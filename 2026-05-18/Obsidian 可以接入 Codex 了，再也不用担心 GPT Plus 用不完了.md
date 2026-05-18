---
author: Leon学AI
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzYzNDExMzY3Mw==&mid=2247484169&idx=1&sn=fe0a80077e964f45fc02c446756b4b17&chksm=f181a8b149548a124cdbc6d8f0ff23f4197a22ddef8238ef3bac2d2abe60d967fad2e3652fa8&mpshare=1&scene=1&srcid=0518vJotzAP2yGo0RfHZSOf8&sharer_shareinfo=5e1c72927e1b6a9f4953b34b2e9897e5&sharer_shareinfo_first=5e1c72927e1b6a9f4953b34b2e9897e5#rd
saved: 2026-05-18 19:32:36
tags:
  - 笔记同步助手
id: ecaae029-d570-44c6-af48-c171fe45e015
---

公众号名称：Leon学AI

作者名称：Leon学AI

发布时间：2026-05-06 15:01

之前一直在用 Claudian 这个 Obsidian 插件，说白了就是把 Claude / Claude Code 接进 Obsidian 里——侧边栏聊天、读笔记、改 Markdown、整理 vault，本地知识库直接操作。

用着是挺爽的，但有个绕不开的问题：Claude 的订阅不是人人都有，而且国内用起来时不时抽风。反倒是 ChatGPT Plus / Pro 这边，买了之后 Codex 的额度一直没怎么花出去，有点浪费。

前阵子发现 Claudian 更新了，现在可以直接接 OpenAI Codex 了。

试了一下，确实能跑。在 Obsidian 侧边栏里选 Codex 模型，直接对话，读笔记、改文章、整理 vault 结构都行，体验跟之前用 Claude 差不多。关键是——ChatGPT Plus 里的 Codex 额度终于有地方花了。

---

先看看效果

这是我在 Obsidian 的 Claudian 侧边栏里，选择 Codex / GPT 模型后发出的一条消息：

![[笔记同步助手/images/f955f64eda20a4129c3cb241881f1ed1_MD5.png]]

下面是一份从 0 到 1 的安装教程，只要按照步骤一步一步地操作，就可以跑起来了。

---

﻿一、这个方案需要准备什么？

正式开始之前，先确认你已经准备好下面三样东西。

1\. Obsidian 桌面版

这个不用多说，最好更新到较新的版本。

2\. Codex CLI

Claudian 插件本质上是把本地 Codex / Claude Code 这类命令行 Agent 接进 Obsidian。所以你的电脑上需要先能运行 Codex。

如果你还没装 Codex CLI，可以先在终端里执行：

```
npm install -g @openai/codex
```

然后登录：

```
codex login
```

如果你想走 ChatGPT 账号登录，按终端里的提示选择 Sign in with ChatGPT 即可。

3\. Obsidian 插件：BRAT + Claudian

Claudian 目前需要通过 BRAT 安装。BRAT 是 Obsidian 里常用的 beta 插件安装器，可以从 GitHub 仓库安装还没上架社区市场的插件。

二、先安装 BRAT

打开 Obsidian 设置，进入：

设置 → 第三方插件 → 社区插件市场 → 浏览

![[笔记同步助手/images/c82645097d047c7e0a5448c100ea1f37_MD5.png]]

在社区插件市场里搜索：

```
BRAT
```

找到作者为 TfTHacker 的 BRAT 插件。

![[笔记同步助手/images/65ecdf7aec27f37c9e50825fd16949d1_MD5.png]]

点进去之后点击 安装，安装完成后再点击 启用。

![[笔记同步助手/images/8e124f2d4e351480f5aa372208178aaf_MD5.png]]

到这里，BRAT 就装好了。

---

三、用 BRAT 安装 Claudian

接下来进入 BRAT 的设置页面：

设置 → 第三方插件 → BRAT

找到 Beta plugin list，点击 Add beta plugin。

![[笔记同步助手/images/23545ff9902ff18d8dde323f65206451_MD5.png]]

在弹窗里输入 Claudian 的 GitHub 仓库地址：

```
https://github.com/YishenTu/claudian
```

然后点击 Add plugin。

这里建议勾选 Enable after installing the plugin，这样安装完成后插件会自动启用。

如果没有自动启用，也可以回到 设置 → 第三方插件，在已安装插件列表里手动打开 Claudian。

---

四、配置 Claudian 的 Codex Provider

安装好 Claudian 后，在 Obsidian 设置左侧会看到 Claudian。

进入 Claudian 设置页，切到顶部的 Codex 标签。

![[笔记同步助手/images/78a4628c7cd3e6763e0e2e3db8aa0730_MD5.png]]

这里主要看几个配置项：

1\. Enable Codex provider

把这个开关打开。打开后，新建会话时模型选择器里才会出现 Codex 相关模型。

2\. Installation method

Windows 用户一般有两种方式：

-   Native Windows：使用 Windows 本机安装的 codex.exe；
    
-   WSL：使用 WSL 里的 Linux 版 Codex CLI。
    

如果你是在 Windows 里直接安装的 Codex CLI，就选 Native Windows。

3\. Codex CLI path

如果 Claudian 能自动识别 PATH，可以留空；如果识别不到，就手动填入本机 codex.exe 的路径。

不知道路径的话，可以在 PowerShell 里执行：

```
where.exe codex
```

把输出的路径复制到这里即可。

4\. Safe mode

建议先保持相对保守的权限，比如：

```
workspace-write
```

它允许 Codex 在当前工作区里读写文件，但不会无限制地乱动系统其它地方。等你熟悉之后，再根据自己的需求调整。

5\. Custom models

如果你的账号能用特定 Codex / GPT 模型，可以把模型名填到这里，一行一个。

不过模型命名和可用性会经常变化，不必完全照抄截图。以你自己的账号里实际显示的模型为准。

---

五、打开 Claudian 侧边栏

配置完成后，回到 Obsidian 主界面，左侧工具栏会出现一个类似小机器人的图标。

点击它，就能打开 Claudian 的对话侧边栏。

![[笔记同步助手/images/aef9579a1b60bd55e82ab7c9507d3999_MD5.png]]

如果前面的 Codex provider 已经启用，在模型选择器里就能看到 Codex 相关模型。

![[笔记同步助手/images/782b793b8ce43a2b8f82cbbaa50799a2_MD5.png]]

选好模型之后，就可以直接在 Obsidian 里对话了。

比如我问它：

```
你用的是什么模型
```

它会在侧边栏里直接回复：

![[笔记同步助手/images/f955f64eda20a4129c3cb241881f1ed1_MD5.png]]

这里有一个小细节：插件界面不一定会把底层模型完整暴露出来，所以它有时只能告诉你“运行在 OpenAI GPT 系列模型上”。这很正常，不影响使用。

---

六、你可能会遇到的问题

装完插件看不到 Codex 模型？

大概率是这三个地方出了问题：

-   Claudian 设置里的 Enable Codex provider 没开；
    
-   终端里跑 codex 命令跑不起来；
    
-   Codex CLI path 填错了。
    

Windows 一定得用 WSL 吗？

不用。我截图里就是直接用的 Native Windows。只要你在 Windows 里装好了 Codex CLI，PowerShell 里 where.exe codex 能找到路径，就选 Native Windows。当然你平时用 WSL 开发的话选 WSL 也没问题。

它会不会乱改我的笔记？

看你怎么设置的。新手建议 safe mode 选保守一点的 workspace-write，然后第一次对话先说”只给建议，别动文件”。等你确认它理解你的意图了，再放权。

这东西能替代 ChatGPT 吗？

不太能，定位不一样。ChatGPT 更适合闲聊、搜索、头脑风暴；接进 Obsidian 的 Codex 更适合处理你本地的文件和笔记。一个是通用对话入口，一个是本地知识库工作台。 各有各的活儿。

---

写在最后

如果你本身就是 Obsidian 用户，手里又有 ChatGPT Plus / Pro，真心建议试一下。

最大的感受就是：以前是我把内容搬到 AI 面前，现在是 AI 直接到我 Obsidian 里来。 听起来好像差别不大，但实际用起来，省掉的那些复制粘贴和来回切换，累积起来还是很明显的。

特别是平时笔记多、经常要整理文章或者维护知识库的人，这个组合能省不少事。

好了，装起来试试吧。有问题评论区聊。

---

![[笔记同步助手/images/ba136dcd346ddb2e5ab0e23e9f1a54e0_MD5.jpg|cover_image]]

Original Leon学AI Leon学AI

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/0f38cd36_1779103953923?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzYzNDExMzY3Mw%3D%3D%26mid%3D2247484169%26idx%3D1%26sn%3Dfe0a80077e964f45fc02c446756b4b17%26chksm%3Df181a8b149548a124cdbc6d8f0ff23f4197a22ddef8238ef3bac2d2abe60d967fad2e3652fa8%26mpshare%3D1%26scene%3D1%26srcid%3D0518vJotzAP2yGo0RfHZSOf8%26sharer_shareinfo%3D5e1c72927e1b6a9f4953b34b2e9897e5%26sharer_shareinfo_first%3D5e1c72927e1b6a9f4953b34b2e9897e5%23rd&s=obsidian)