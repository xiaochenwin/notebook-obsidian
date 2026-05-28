---
author: 是你猫兄啊
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzg2ODA3NTA3NQ==&mid=2247485137&idx=1&sn=7ca636afda28cc64210b2f80011b87b0&chksm=cf8537923b0bbbd88d9d9c618771e0c974ec80c10e49f1354cc854c4824f20c97952db98efc2&mpshare=1&scene=1&srcid=0526ZlK0qc3I45rIxEJfbGlZ&sharer_shareinfo=a94c3809a8f0cc829e675abfcedd9613&sharer_shareinfo_first=a94c3809a8f0cc829e675abfcedd9613#rd
saved: 2026-05-26 08:56:39
tags:
  - 笔记同步助手
id: f68dbf9a-cd19-4cca-8e36-fdb68adbd896
---

公众号名称：猫兄的和谐号列车

作者名称：是你猫兄啊

发布时间：2026-05-14 18:58

原文链接：[https://ameow.xyz/archives/build-an-ai-agent-team-in-feishu](https://ameow.xyz/archives/build-an-ai-agent-team-in-feishu)

## 前言

关于如何安装和部署 Hermes 以及接入飞书，飞书官方的这两篇博客（Hermes Agent 安装与部署指南：一步步教你如何使用“爱马仕 Agent”（附飞书接入教程）\[1\]、Hermes Agent 全解析：与 OpenClaw 对比及飞书接入指南\[2\]）已经讲得非常详细，但是这样只能拉起来一个 Agent，还不能称为「团队」，真正的团队应该有多个 AI Agent，各自负责不同的岗位。当然你可以通过在多台机器或者虚拟机上部署多个 Hermes 实例来实现这样的效果，不过 Hermes 自带了一个 profile\[3\] 的功能，可以在一个 Hermes 实例上就能开出多个角色，下面我们来看看如何操作吧。

## 前提

你可以参考上面提到的飞书的官方教程，先安装好 Hermes 以及走通飞书的接入，走通跟 Agent 的 DM（私聊）。简要的步骤为：

​

```
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash

source ～/.bashrc
```

安装完成后，按照提示选择 Quick setup，配置好模型和飞书的连接，私聊机器人，然后进行配对。具体过程参考官方教程\[4\]即可，不再赘述。

## 创建角色

第一个 Agent 跑通后，可以开始创建新的角色。每个角色具有独立的配置、`SOUL.md` （人设）、记忆、会话、skill 等，可以实现职责的分离。接下来我们以产品经理和市场营销这两个角色为例，创建两个新的角色。

​

```
hermes profile create pm --clone
hermes profile create marketing --clone
```

这里 `--clone` 选项是为了直接复制模型的配置，所以后续我们还需要修改他们的 `SOUL.md` 来实现不同的人设区分。

接下来，我们要创建新的飞书机器人，方便我们后续在飞书中找到对应的角色。先配置第一个：

​

```
pm setup
```

还是选择 Quick setup，过程跟前面第一次配置的时候基本一样，选择模型这一步一路回车即可，复用之前的配置。

一直到配置消息这一步，在选择平台的时候还是回车。

这里输入 y，重新配置，然后打开链接新建一个对应的机器人，继续一路回车完成后面的流程。

完成后，点击网页上的「打开应用」，然后跟 Agent 发一个 hi，然后拿到 `hermes paring approve feishu XXX` 这样的配对码。这里需要注意的是，创建新的角色后，我们的命令就变成了对应的名称，所以这里要粘贴执行的实际是 `pm paring approve feishu XXX`。

接下来我们修改它对应的人设，有两种方式，你可以直接在对应的聊天里跟它说：

​

```
修改一下你的 SOUL.md，你是某某公司的产品经理，...
```

也可以编辑对应目录下的 `SOUL.md`，例如 `～/.hermes/profiles/pm/SOUL.md`。

重复上面的步骤，完成 `marketing` 的配置。

需要注意 profile 并没有隔离 AI Agent 的工作区，也就是说，你虽然开了三个 AI Agent，它仍然可以修改别人目录下的东西，我在使用过程中就遇到修改错了别人的 `SOUL.md` 的情况。你可以在 `SOUL.md` 中指明它可以修改的目录，又或者简单让它「记住你只能修改 xx 目录」，但不能完全防止它修改到其他的文件。如果你明确需要各个 Agent 之间完全独立，还是需要部署多个 Hermes 实例。

## 群聊

你可以把真人和 AI Agent 都拉到一个群里，实现 AI Agent 和 AI Agent，AI Agent 和人之间的协作。先创建一个群聊，正常拉入真人，然后在设置-群机器人-添加机器人中，添加刚才创建的几个 AI Agent。

接下来有几个配置需要修改。要令机器人之间可以相互交流，需要修改 `.env` 文件（分别是 `～/.hermes/.env`、`～/.hermes/profiles/pm/.env` 和 `～/.hermes/profiles/marketing/.env`），在底部添加一行。

​

```
FEISHU_ALLOW_BOTS=mentions
```

要让不同的人在群聊中跟 AI Agent 可以共享 session（可以干预别人在群里跟 AI Agent 的聊天），还需要修改一个配置。

​

```
hermes config set group_sessions_per_user false
pm config set group_sessions_per_user false
marketing config set group_sessions_per_user false
```

如果你觉得每次调用工具会产生大量的消息，也可以在这一步关掉：

​

```
hermes config set display.tool_progress off
（其他两个同理）
```

最后，重启一下对应的 gateway。

​

```
hermes gateway restart
pm gateway restart
marketing gateway restart
```

这里为了行文逻辑，放到了后面来修改，事实上在新增时，如果使用 `--clone`，修改过的这些配置会直接克隆过去，不用再手动修改了。

## 飞书 CLI

要让 AI Agent 访问到知识库或者在线文档等，还需要安装飞书 CLI。任选一个 AI Agent，告诉他：`请帮我安装飞书CLI：https://github.com/larksuite/cli`，然后根据它的提示完成授权。后续就可以操作文档了。

后续操作过程中，有可能它还需要申请新的权限，按照提示打开链接授权完成后，再@一下它即可。

## Agent 协作

要想实现 AI Agent 之间的协作，可以把多个 AI Agent 拉到一个群聊里面，例如：

​

```
@产品经理 帮我把这个产品想法整理成一个 PRD。
```

等产品经理输出完后，再调用营销专家：

​

```
@市场营销 基于上面 PM 的 PRD，帮我提炼定位、落地页首屏文案和首发推广计划。
```

也可以连起来：

​

```
@产品经理 帮我把这个产品想法整理成一个 PRD，然后交给 @市场营销 提炼定位、落地页首屏文案和首发推广计划。
```

不过这种方式好像暂时不能由第一个机器人直接触发第二个机器人，可能是使用的 @ 的方式不对，还需要手动再触发一下。

## 多人使用

前面说到，你可以把多个真人也拉到群聊里面使用，当然其他人也可以跟这个 AI Agent 私聊。

其他人要使用 AI Agent 时，首先需要提交一个「应用使用申请」，管理员通过后才可以对话。也可以在飞书管理后台-工作台-应用管理里找到对应的 AI Agent，修改应用可用范围，设置为对应的成员或者全部成员。

然后需要先跟 AI Agent 私聊一个 hi，像前面一样获得一个 `hermes paring approve feishu XXX` 这样的配对码，然后对应在终端里执行，才可以开始私聊和群聊。如果你觉得这个过程比较繁琐，也可以对应配置 `.env` 里 `FEISHU_ALLOW_ALL_USERS=true`。

## 结语

到这里，一个由多个 Hermes profile 组成的飞书 AI Agent 小团队就基本搭起来了：从最初的单个 Agent，到产品经理、市场营销等不同角色，再到把它们拉进同一个群聊里协作，整个过程并不复杂，核心思路就是用 profile 来拆分角色，用飞书机器人来区分入口，再通过群聊把它们组织成一个「团队」。

当然，这套方案目前还不是一个完全成熟的多 Agent 编排系统。比如 profile 之间的文件系统并没有强隔离，机器人之间的自动接力也还不够顺滑，一些权限和配对流程对多人使用来说也略显繁琐。但好处是它足够轻量，不需要部署多套服务，也不需要一开始就引入复杂的 Agent 框架，就能快速验证「多个 AI 角色一起工作」这件事。

如果你只是想在团队内部快速搭建一个产品经理、研发助手、运营专家、客服助手之类的 AI 协作空间，Hermes + 飞书 + profile 已经是一个很值得尝试的方案。后续随着 Hermes 本身的 profile、权限、群聊协作能力继续完善，这种「把 AI Agent 当成团队成员拉进群里」的工作方式，应该还会有更多有意思的玩法。

### References

`[1]` Hermes Agent 安装与部署指南：一步步教你如何使用“爱马仕 Agent”（附飞书接入教程）: _https://www.feishu.cn/content/article/7630758640865037530_  
`[2]` Hermes Agent 全解析：与 OpenClaw 对比及飞书接入指南: _https://www.feishu.cn/content/article/7628541877674953666_  
`[3]` profile: _https://hermes-agent.nousresearch.com/docs/user-guide/profiles_  
`[4]` 官方教程: _https://www.feishu.cn/content/article/7628541877674953666_

  

---

![[笔记同步助手/images/d780cf22b73d34d13e50bb0eaecad3fe_MD5.jpg|cover_image]]

原创 是你猫兄啊 猫兄的和谐号列车

阅读原文

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/4b7713f9_1779756997808?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzg2ODA3NTA3NQ%3D%3D%26mid%3D2247485137%26idx%3D1%26sn%3D7ca636afda28cc64210b2f80011b87b0%26chksm%3Dcf8537923b0bbbd88d9d9c618771e0c974ec80c10e49f1354cc854c4824f20c97952db98efc2%26mpshare%3D1%26scene%3D1%26srcid%3D0526ZlK0qc3I45rIxEJfbGlZ%26sharer_shareinfo%3Da94c3809a8f0cc829e675abfcedd9613%26sharer_shareinfo_first%3Da94c3809a8f0cc829e675abfcedd9613%23rd&s=obsidian)