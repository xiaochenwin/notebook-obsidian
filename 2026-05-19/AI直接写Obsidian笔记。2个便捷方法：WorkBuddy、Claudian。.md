---
author: fxckai
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzY5MzI5MTExMw==&mid=2247483788&idx=1&sn=9291c852b4cfc97ab8e139ec72f8bd1e&chksm=f5e2b2d8b475b190365c382d4912c08fd24cc5beac1602a411f1348dda550c293200cd57f917&mpshare=1&scene=1&srcid=0519wRRxKMthSF7sGpzuzOds&sharer_shareinfo=a8f1c32dc4006c9c5ee0855740867023&sharer_shareinfo_first=a8f1c32dc4006c9c5ee0855740867023#rd
saved: 2026-05-19 16:40:49
tags:
  - 笔记同步助手
id: fcf75d0b-518a-494f-9d56-cd73a0193411
---

公众号名称：Ada玩AI

作者名称：fxckai

发布时间：2026-05-15 22:00

我的笔记都放在obsidian。原因：AI时代最好的笔记格式是markdown。

AI读markdown，效率高，烧钱少。

![[笔记同步助手/images/3a82233e9969b4fd3579851e17a576b6_MD5.jpg]]

我的群聊：今天讨论了wb积分

（想进群的话，在公众号后台私信我）

ob拥抱AI非常彻底，跟各个AI助手都兼容。

我实操两个月，发现两个便捷方法是workbuddy和obsidian的claudian插件。

  

## 方法一：WorkBuddy

我一开始用workbuddy操作ob，主要是为了赚积分。

![[笔记同步助手/images/de853861877e8deb6b85dc797495f42b_MD5.png]]

赚积分活动里有一项是召唤专家。

我看有个“知识管理专家”就是专门操作ob的，所以结合wb的obsidian技能，一起试了下。

### 如何操作？

STEP 1 复制obsidian vault地址

![[笔记同步助手/images/9ce949da7ed2c2792a2134d88ccdc58c_MD5.png]]

找到页面左下角的vault名称。

右键点击，选中“复制路径”，把这个地址复制给wb。

STEP 2 wb对话框选中专家、技能，分析vault所有笔记

![[笔记同步助手/images/e2d9c2c16e223a233d86b8f5353f94aa_MD5.png]]

prompt 如下：

```
我的Obsidian库路径：【】。读取Obsidian Vault根目录，分析Vault，给出核心洞察。
```

wb读完整个ob vault，再输出图表形式的分析，并给出建议，加在一起才烧了10积分。

以下是部分效果：

![[笔记同步助手/images/2960a57851a581f64ef73421f42c70bb_MD5.png]]

![[笔记同步助手/images/d449b990719095ec02f6590c1e00eb31_MD5.png]]

STEP 3 AI写笔记

我让wb把建议写成一页放进ob。

![[笔记同步助手/images/84c39537096a84525806b41f5b937c40_MD5.png]]

![[笔记同步助手/images/5488afd237202ccc29015ad9beb309a5_MD5.png]]

笔记效果

​

整个操作过程完全没有bug。

花了3积分。

  

## 方法二：Claudian插件

claudian插件从零开始安装有点麻烦，但是用起来超爽。

效果：AI长期陪伴在obsidian的右边栏。

wb能做的，claudian都能做。

下图是claudian根据读书摘录，产出的读书笔记。

![[笔记同步助手/images/6f603c2304b8a8d6faf35868e162b9d1_MD5.png]]

  

### 如何安装？

STEP 1 安装claude code

以windows为例：

```
npm install -g @anthropic-ai/claude-code
```

STEP 2 配置大模型

在/.claude文件夹，新建settings.json，将模型配置为国内用户可得的大模型。

以换成deepseek为例（注意：api key是你需要去deepseek官网买的）

settings.json：

​

```
{
"env": {
"ANTHROPIC_AUTH_TOKEN": "api key",
"ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
"ANTHROPIC_MODEL": "deepseek-v4-pro[1m]",
"API_TIMEOUT_MS": "3000000",
"CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
}
}
```

如果担心误操作，可以把step 2的整段文字复制到workbuddy对话框，让它帮你操作。

完成设置settings.json以后，CMD运行claude，看到模型换成了deepseek，说明已配置成功。

![[笔记同步助手/images/381bcee80aa5570113e6e0ee9158f936_MD5.png]]

STEP 3 配置obsidian

## 1\. 启用命令行界面：obsidian - 设置 - 关于 - 高级 - 命令行界面

![[笔记同步助手/images/1be5df5fb74d9ca0239d2e6ba1ecb4ef_MD5.png]]

## 2\. 安装BRAT插件：设置 - 第三方插件 - 社区插件市场 - BRAT - 安装 - 启用

## 3\. 使用BRAT插件，安装claudian插件

![[笔记同步助手/images/4e6d2317ef442673119e222b60acc6ff_MD5.png]]

点击最左侧的BRAT按键，选中add a beta plugin for testing。

Repository:

https://github.com/YishenTu/claudian

版本选latest version，点击add plugin。

![[笔记同步助手/images/83aef3053ac9a8ff8be08c7bce6c4fe5_MD5.png]]

4\. 安装成功后，点击最左侧的claudian机器人按键，claudian就会出现在右边栏。

![[笔记同步助手/images/ae3e00c94dc5786cf82c6606bcde7bd1_MD5.png]]

claudian自由读取、更新所有笔记。

由此，AI成为了知识库的延伸，一个可以直接对话的“人”。

帮你洞察自己，打破固有知识结构。

  

## Reflection: 知识库、笔记、“我”

过去一年，我学了佛教、复杂学、哲学、神经科学。这些“学”，不是建构，而是解构。

《比天空更宽广》有一段话：

“意识反映了在无数选择中进行区分或辨识的能力。这些区分不到一秒就能完成，而且不断变化。作为现象体验序列的意识必然是因人而异的，它与个人的身体、大脑以及各自与环境的互动经历密切相关。这种经历是独一无二的——任何两个个体，即使是双胞胎，都不会有一样的意识状态。事实上，即使是同一个人，两个意识状态相同的可能性也微乎其微。”

万有引力之外，没有对错。

任何一个人的标准、规矩、道德、价值，在任何一个人那里，都是无效的。任何一个词语、概念、数字，都是不存在的。

笔记、知识库也是一样。

曾经我用GTD、用PARA，以为这就是standard，这就是“对的”。

后来我发现“人都活在自己的脑海里”、“每个人都是对的”，后悔二十多年相信有“对”、“真”、“好”。

现在我做知识库、做事、做“人”、玩AI都是为了爽。

OB系列：

[我不用飞书了。All in Obsidian。](https://mp.weixin.qq.com/s?__biz=MzY5MzI5MTExMw==&mid=2247483682&idx=1&sn=3487015998244c27299333889659b1e9&scene=21#wechat_redirect)

[别再用AI管理自己了。用 Obsidian x Claude Code 找到你真正热爱的事。#001](https://mp.weixin.qq.com/s?__biz=MzY5MzI5MTExMw==&mid=2247483733&idx=1&sn=4a56c0faa6894dda3e045e7876528f0b&scene=21#wechat_redirect)

  

---

![[笔记同步助手/images/3fa72a9a73c8de08ce31a632f422f517_MD5.jpg|cover_image]]

原创 fxckai Ada玩AI

修改于

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/8bd1c94b_1779180047720?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzY5MzI5MTExMw%3D%3D%26mid%3D2247483788%26idx%3D1%26sn%3D9291c852b4cfc97ab8e139ec72f8bd1e%26chksm%3Df5e2b2d8b475b190365c382d4912c08fd24cc5beac1602a411f1348dda550c293200cd57f917%26mpshare%3D1%26scene%3D1%26srcid%3D0519wRRxKMthSF7sGpzuzOds%26sharer_shareinfo%3Da8f1c32dc4006c9c5ee0855740867023%26sharer_shareinfo_first%3Da8f1c32dc4006c9c5ee0855740867023%23rd&s=obsidian)