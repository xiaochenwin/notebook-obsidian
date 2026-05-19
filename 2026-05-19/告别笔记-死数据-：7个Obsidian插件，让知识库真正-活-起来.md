---
author: 陈一豪
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzkzOTI0NjYxOA==&mid=2247484186&idx=1&sn=901de5c7551cd655a23541a8ea24040c&chksm=c3360770e1528b1853967633be2c3cc426c5e56244f5f37fac09364def24a54ae60326115726&mpshare=1&scene=1&srcid=0519z90ac5JhRxTVKEtlXeqO&sharer_shareinfo=643e893fe9dabcaaac3cb0de90e3da90&sharer_shareinfo_first=643e893fe9dabcaaac3cb0de90e3da90#rd
saved: 2026-05-19 08:35:48
tags:
  - 笔记同步助手
id: f6a5fbf8-64c9-4240-a7bf-9f400f750bdc
---

公众号名称：一豪同学

作者名称：陈一豪

发布时间：2026-05-17 08:00

# 告别笔记"死数据"：7个Obsidian插件，让知识库真正"活"起来

> 你的笔记库越来越大，却越来越难用？内容越写越多，却总在重复劳动？今天分享我精心搭配的7个Obsidian插件，从基础增强到AI驱动，把你的知识库从"电子笔记本"升级为"第二大脑"。

---

## 为什么你的知识库总是"死"的？

用过Obsidian的人不少，但大多数人的Vault（知识库）其实只是"带链接的文件夹"——笔记写了就放着，检索靠翻，整理靠手动，图片链接过几天就404，换了设备还找不到最新版本。

我花了一个月时间测试了30多个插件，最终留下这7个。它们不是简单堆砌，而是**分层协作，**形成一个完整的知识管理闭环。

​

---

## 🏗️ 第一层：基础增强层

### 1\. BRAT —— "插件的插件"

**一句话：**所有还没上架Obsidian市场的"黑科技"插件，都靠它装。

Obsidian社区有很多优秀插件还在测试阶段，没上架官方市场。BRAT让你直接输入GitHub仓库名就能安装，还能锁定版本不怕更新翻车。

​

> 我最常用的场景：安装Claudian（后面会说），这是目前市面上唯一没上架但最值得装的AI插件。

### 2\. Git —— 知识库的"时光机"

**一句话：**每一次修改都有记录，多设备同步零焦虑。

如果你有多台电脑用过Obsidian，一定经历过这种崩溃：A电脑写的笔记，B电脑找不到最新版本。Git解决这个问题——写完自动提交、自动同步，打开另一台电脑自动拉取。

更棒的是，每个笔记的修改历史清清楚楚，误删了什么随时能找回。

## 推荐配置：

-   每5分钟自动提交
    
-   打开Obsidian自动拉取最新内容
    
-   配合`.gitignore`排除不需要同步的缓存文件
    

---

## 🤖 第二层：AI增强层

### 3\. Claudian —— 让知识库"开口说话"

**一句话：**打开笔记，AI已经在"读"你的内容了。

这是我最想分享的一个插件。它把Claude Code（Anthropic的AI编程代理）直接嵌入Obsidian——你的Vault不再是被动存储，而是AI的工作空间。

**能做什么？**

-   **行内编辑：**
    
    选中一段笔记，让AI帮你重写、扩展、压缩
    
-   **内容重构：**
    
    一堆零散笔记 → AI自动整理成结构化文档
    
-   **上下文感知：**
    
    AI不只是看当前笔记，还会读取关联笔记，给出跨笔记的智能建议
    
-   **Skills集成：**
    
    你可以自定义"技能包"，比如"笔记摘要生成器"、"知识关联发现器"
    

> 举个例子：我写了一篇3000字的技术笔记，用Claudian的摘要技能，10秒生成200字精炼摘要，自动加上合适的标签，存回笔记。这在以前需要我花20分钟。

### 4\. Terminal —— Obsidian里的"命令行"

**一句话：**不用切窗口，笔记里直接跑脚本。

你可能觉得"我又不写代码，为什么要终端？"但有了它，很多自动化操作变得顺手：

-   在笔记里直接运行Git命令
    
-   执行Python脚本处理笔记数据
    
-   调用API获取实时数据写入笔记
    
-   和Claudian配合：**AI分析 → Shell执行 → 结果回写笔记，**完整闭环
    

---

## 🧭 第三层：导航与发现层

### 5\. Notebook Navigator —— 让笔记"好找"比"记了"更重要

**一句话：**2025年下载量最大的新插件，替换了Obsidian默认的"文件列表"。

笔记超过100篇之后，默认的文件列表就够用了。Notebook Navigator提供了：

-   **双栏布局：**
    
    左边文件夹树 + 右边文件列表（类似Mac Finder）
    
-   **标签浏览：**
    
    按标签层级浏览，跨文件夹查找
    
-   **缩略图预览：**
    
    每个笔记42px缩略图，扫一眼就知道内容
    
-   **文件夹颜色：**
    
    给不同类别的文件夹标色，视觉区分一目了然
    
-   **全键盘导航：**
    
    不用鼠标，效率翻倍
    

> 我的Vault现在300+笔记，用它之后找笔记的时间从"翻半天"变成"3秒定位"。

---

## 🎨 第四层：内容创作层

### 6\. Excalidraw —— 手写风格的"思维画板"

**一句话：**600万+下载量，Obsidian生态里最受欢迎的插件之一。

在笔记里画架构图、思维导图、流程图——不是那种规整的Visio风格，而是手绘风格，看起来像是你自己的草稿，读起来更有亲切感。

## 我常用场景：

-   学习笔记配概念图（比如缠论的波浪结构图）
    
-   系统架构设计草图
    
-   产品原型快速绘制
    
-   会议记录配流程图
    

v2.23版本开始还加入了AI功能：和AI对话生成图表，或者把手绘图转换成代码。

### 7\. Local Images Plus —— 图片"永不过期"

**一句话：**从网页复制内容到笔记，图片自动下载到本地，再也不怕链接失效。

这是被严重低估的一个插件。很多人从网页复制内容粘贴到Obsidian，里面的图片都是外链——过几个月网站改了图片路径，笔记里就是一片红叉。

Local Images Plus的工作流程：

1.  复制网页内容 → 粘贴到笔记
    
2.  **自动**
    
    下载所有嵌入的图片到本地
    
3.  自动更新笔记中的图片链接为本地路径
    

还可以批量扫描全库，把已有的外链图片全部下载到本地。

​

> 配合PicGo使用效果更佳：先下载到本地，再一键上传到图床，本地和远程都有备份。

---

## 🔗 四层插件，四个协同工作流

这7个插件单独用都不错，但**组合起来**才是真正威力所在。

### 工作流一：AI辅助知识整理

```
Terminal（运行脚本抓取数据）
    ↓
Claudian（AI分析并生成笔记）
    ↓
Notebook Navigator（整理归类到新文件夹）
    ↓
Excalidraw（绘制知识结构图）
    ↓
Git（提交保存到远程）
```

### 工作流二：网页内容剪藏

```
浏览器复制网页内容
    ↓
粘贴到Obsidian笔记
    ↓
Local Images Plus（自动下载图片）
    ↓
Claudian（AI生成摘要和标签）
    ↓
Git（自动提交备份）
```

### 工作流三：研究笔记管理

```
Notebook Navigator（浏览和检索笔记）
    ↓
Excalidraw（绘制概念图/流程图）
    ↓
Terminal（运行Python脚本分析数据）
    ↓
Claudian（AI辅助撰写总结）
    ↓
Git（提交并推送到远程）
```

### 工作流四：测试版插件体验

```
BRAT（安装测试版插件）
    ↓
测试新功能
    ↓
BRAT（如果稳定，冻结版本防翻车）
    ↓
Git（提交配置变更）
```

---

## 📦 快速上手指南

### 安装方式

大部分插件直接在Obsidian的**社区插件市场**搜索安装即可：

| 插件 | 市场搜索名 | 特殊说明 |
| --- | --- | --- |
| BRAT | `BRAT` | 建议第一个装 |
| Git | `Git` | 系统需先安装Git |
| Terminal | `Terminal` | — |
| Notebook Navigator | `Notebook Navigator` | 建议关闭默认"文件列表" |
| Excalidraw | `Excalidraw` | — |
| Local Images Plus | `Local Images Plus` | — |
| **Claudian** | 无 | 需通过BRAT安装 |

**Claudian特殊安装：**先装好BRAT → 命令面板(`Ctrl+P`) → 搜`BRAT: Add a beta plugin` → 输入`YishenTu/claudian` → 启用。

### 版本信息（截至2026年5月）

| 插件 | 版本 |
| --- | --- |
| BRAT | v2.0.4 |
| Git | v2.38.3 |
| Claudian | v2.0.15 |
| Terminal | v3.24.0 |
| Notebook Navigator | v2.6.6 |
| Excalidraw | v2.22.3 |
| Local Images Plus | v0.16.4 |

---

## 💡 最后的话

很多人问我："Obsidian插件装多少合适？"

我的答案是：**少而精**。这7个插件覆盖了你知识管理的完整生命周期——**安装( BRAT ) → 备份( Git ) → AI增强( Claudian + Terminal ) → 导航( Notebook Navigator ) → 创作( Excalidraw + Local Images Plus )。**不需要更多了。

关键是让它们**协同工作，**而不是各干各的。当你的笔记能被AI理解、能被Git备份、能被快速检索、还能配上视觉图表——这时候，你的知识库才真正"活"了起来。

​

---

_如果你觉得这篇文章有帮助，欢迎点赞、在看、转发。你的支持是我持续分享的动力。_

  

---

![[笔记同步助手/images/d13ec06b0fd5e34da5433fe7c83570c5_MD5.jpg|cover_image]]

Original 陈一豪 一豪同学

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/87027131_1779150946962?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkzOTI0NjYxOA%3D%3D%26mid%3D2247484186%26idx%3D1%26sn%3D901de5c7551cd655a23541a8ea24040c%26chksm%3Dc3360770e1528b1853967633be2c3cc426c5e56244f5f37fac09364def24a54ae60326115726%26mpshare%3D1%26scene%3D1%26srcid%3D0519z90ac5JhRxTVKEtlXeqO%26sharer_shareinfo%3D643e893fe9dabcaaac3cb0de90e3da90%26sharer_shareinfo_first%3D643e893fe9dabcaaac3cb0de90e3da90%23rd&s=obsidian)