---
author: 赛博李同学AI手记
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzI4NjE4MTkwMg==&mid=2653714438&idx=1&sn=5fac9af2dd4fa846c9b50b4fab17f857&chksm=f13ab7563499863b067ec4c68a763289570404a6e1c81a28d0430c485133b20803ef3c21c9ab&mpshare=1&scene=1&srcid=05218qLQbr6qI1DEjwnF9rYf&sharer_shareinfo=bfe801e9626f48e05cd58ece36f97bf3&sharer_shareinfo_first=bfe801e9626f48e05cd58ece36f97bf3#rd
saved: 2026-05-21 07:38:48
tags:
  - 笔记同步助手
id: 38705f1a-cbc5-4fa4-b9d9-cd62fe881825
---

公众号名称：赛博李同学AI手记

作者名称：赛博李同学AI手记

发布时间：2026-05-13 08:40

用 Claude Code 写代码确实方便，但写文档的时候就不那么顺了——每次想让 AI 帮忙改段落，都得切到终端，复制粘贴，再切回来。几趟下来思路早就散了。

后来我找到了一个叫 Claudian 的 Obsidian 插件，能直接在笔记界面里跟 Claude 对话。装完试了一下，我只能说，早该这么干了。

今天把安装过程写下来，跟着操作，五分钟左右能搞定。

​

## 这篇文章能帮你搞定什么

-   Obsidian 安装和知识库创建（已经有 Vault 的跳过这步）
    
-   Claudian 插件安装（官方市场搜不到，得用 BRAT 中转）
    
-   Claude Code 和 Codex 的双模型配置
    
-   验证连接是否成功
    

## Obsidian 和 Claude Code 能配合干什么

Obsidian 是本地 Markdown 笔记工具，数据全在本地，支持各种插件扩展。Claude Code 就不用多介绍了，你正在用的就是。

两个打通之后，在 Obsidian 里直接跟 Claude 对话，让它帮你改笔记、整理文档、生成内容，甚至接 Codex。一个窗口搞定，不用反复切终端。

![](https://relay-1.bijitongbu.site/p/f2971c5a52abd5920223671d6db14713.png)

## 第一步：安装 Obsidian，创建知识库

官网下载：https://obsidian.md/download

macOS 用户点 `Download for macOS`，下完拖进应用程序文件夹就行。

![](https://relay-1.bijitongbu.site/p/e9b9318dec494009105c2bcba5a18cce.png)

首次打开会有欢迎界面，点「创建新库」，选个存放位置。

![](https://relay-1.bijitongbu.site/p/159910d02b3807b57827487e136d52e4.png)

已经有 Vault 的直接跳过。

​

## 第二步：安装 Claudian 插件

插件地址：https://github.com/YishenTu/claudian

![](https://relay-1.bijitongbu.site/p/308547ad3a38fff54125764c31b15b50.png)

这个插件还没上架 Obsidian 官方插件市场，在市场里搜不到。需要用一个叫 BRAT 的插件来中转安装。

![](https://relay-1.bijitongbu.site/p/b6c8fea542362dde547bb9ae8546cea2.png)

流程不复杂，往下看。

### 2.1 关掉安全模式

Obsidian 设置 → 左侧菜单往下滑 → 「第三方插件」→ 点进去。

顶部有个「安全模式」，默认开着。开着的时候不允许装任何第三方插件，关掉它。

![](https://relay-1.bijitongbu.site/p/7407a14bdfa388134b41b612d612e37e.png)

关掉之后，下面的「社区插件市场」就可用了，点「浏览」进去。

### 2.2 安装 BRAT

插件市场搜 brat，第一个就是。

![](https://relay-1.bijitongbu.site/p/46cdda495930cc8d898231f884699a1d.png)

点进去 → 安装。

​

> 如果显示"无法安装"，多试几次就行，通常是网络问题。

![](https://relay-1.bijitongbu.site/p/aae83e6c2263e6862b2937ad8f409302.png)

装完点「启用」，然后重启 Obsidian。

![](https://relay-1.bijitongbu.site/p/4a5ec181489de317927d5307d5a72a4a.png)

### 2.3 用 BRAT 安装 Claudian

重启后回到设置页面，左侧菜单滑到最底下，找到 BRAT 点进去。![](https://relay-1.bijitongbu.site/p/149f8e92d2d86f861e85070d5cfa202f.png)

在 Repository 框里输入 Claudian 的地址：

```
https://github.com/YishenTu/claudian
```

![](https://relay-1.bijitongbu.site/p/517197a8f3588d8231c3e00a42166297.png)

点确认，等它装好。

### 2.4 确认插件状态

装完后，Obsidian 左边的侧边栏应该会多出一个机器人图标，那就是 Claudian 的入口。

![](https://relay-1.bijitongbu.site/p/d8c3ae79fc3e3dbbe67206c0e80dde36.png)

没看到的话，去设置里确认一下 Claudian 有没有启用。

​

## 第三步：配置 Claude CLI 路径

插件装好了，还得告诉它 Claude Code 装在哪。

设置 → 第三方插件 → 找到 Claudian → 切到「Claude」标签页。

本地先查一下路径：

```
where claude
# 我用 homebrew 装的，路径是 /opt/homebrew/bin/claude
```

把结果填进去：

![](https://relay-1.bijitongbu.site/p/dc6747c5fb142657194bc005fccb0a80.png)

> 页面默认英文，可以改语言：

![](https://relay-1.bijitongbu.site/p/5e61740ec6a4c7c19625f19ef988e600.png)

## 第四步：把 Codex 也配上

既然都在配了，不如把 Codex 也一起搞定。

套路一样，先查路径：

```
where codex
# /opt/homebrew/bin/codex
```

填到 Claudian 的 Codex 配置里：

![](https://relay-1.bijitongbu.site/p/c50caa62af076b0e7ca0e48694fc0b4b.png)

重启 Obsidian，Claude 和 Codex 的模型就都出来了：

![](https://relay-1.bijitongbu.site/p/1c40b975f4c753ba8be01edfff2a7e8e.png)

> 模型没出来的话，检查两个地方：
> 
> ​
> 
> 1.  「Enable Codex provider」开关有没有打开
>     
> 2.  在 Claudian 里重新开一个对话框测试（旧对话框不会刷新，我踩过这个坑）
>     

## 测试一下

打开 Claudian 对话面板，随便问一句：

​

> 你能连接上 Claude Code 嘛？

![](https://relay-1.bijitongbu.site/p/867433589c9bbe0b5c01695b11331e85.png)

能正常回复就说明成功了。它会自动检测本地的 Claude 安装路径，不需要额外配置。

​

## 打通之后能干什么

-   写技术文档的时候，让 Claude 帮你补代码示例
    
-   整理会议纪要，让 Claude 提炼要点
    
-   写博客草稿，让 Claude 润色措辞（不要太过，以自己口述为主）
    
-   笔记太乱，让 Claude 自动分类打标签
    

Obsidian 本身是 Markdown，Claude 输出的内容格式直接兼容，不用二次排版。

最大的好处是写文档的时候思路不会断。以前写到一半想让 AI 帮忙整理结构，得切到终端折腾半天。现在在 Obsidian 里问一句就行，改完继续写。

​

## 下期预告

装好了只是开始。下期讲怎么用 Claudian 在 Obsidian 里重构技术笔记、自动打标签、写博客草稿。

我是赛博李同学大厂写代码的，**觉得有用的话，点个赞 + 转发给需要的兄弟，感谢支持！**，我们下期再见！

---

![cover_image](https://mmbiz.qpic.cn/mmbiz_jpg/WaQDe451kxn6hzv8oiaMaKoELEmholzPkKUGGX6GnjE0qic3voruZ8hqTbtVSxzX8boGnOWj2dFicibR8DzpaSv1sL5icy3G9dRO0NiaWKUj2Pia2s/0?wx_fmt=jpeg)

Original 赛博李同学AI手记 赛博李同学AI手记

修改于

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/50508da5_1779320327792?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI4NjE4MTkwMg%3D%3D%26mid%3D2653714438%26idx%3D1%26sn%3D5fac9af2dd4fa846c9b50b4fab17f857%26chksm%3Df13ab7563499863b067ec4c68a763289570404a6e1c81a28d0430c485133b20803ef3c21c9ab%26mpshare%3D1%26scene%3D1%26srcid%3D05218qLQbr6qI1DEjwnF9rYf%26sharer_shareinfo%3Dbfe801e9626f48e05cd58ece36f97bf3%26sharer_shareinfo_first%3Dbfe801e9626f48e05cd58ece36f97bf3%23rd&s=obsidian)