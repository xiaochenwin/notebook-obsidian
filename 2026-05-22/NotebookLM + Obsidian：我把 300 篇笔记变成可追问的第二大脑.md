---
author: 惠玩科技张大鹏
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzA5NjQ1ODYwNg==&mid=2659092639&idx=1&sn=7a2a7b5b900054fde98038b0464800c5&chksm=8a6f6df8f5d35798e597426aa43bb40deec7e2ac04f3666446374c548732720377e1c9c9e8cb&mpshare=1&scene=1&srcid=0522LMwCLFqjNS6h6Ghz4nAo&sharer_shareinfo=3934ece9d9a3902dc3681bc39c8bb2ea&sharer_shareinfo_first=3934ece9d9a3902dc3681bc39c8bb2ea#rd
saved: 2026-05-22 07:55:17
tags:
  - 笔记同步助手
id: b1c7f3a0-4ad1-4f93-8b97-514a10d5e6a5
---

公众号名称：AI程序员张总

作者名称：惠玩科技张大鹏

发布时间：2026-05-22 00:00

> 我是张大鹏，主库在 Obsidian，笔记 300 多篇之后，「搜到了」不等于「串起来了」。试了一周 **NotebookLM + Obsidian 双轨**，真正省时间的不是「全库导入」，而是**先限定源范围，再追问**。

![[笔记同步助手/images/f164e93d7fdae371a996f5cc4ea74818_MD5.png]]

  

---

## 先说结论：别搞成「搬家」，要搞成「双轨」

很多人第一反应：把 Obsidian 全库丢进 NotebookLM，当第二大脑。

我踩过的坑是：

-   源太多，回答变「和稀泥」
    
-   旧笔记、草稿、排障日志混在一起，引用不可信
    
-   Obsidian 里的双链、标签优势反而用不上
    

更稳的做法是 **双轨**：

​

| 轨道 | 工具 | 干什么 |
| --- | --- | --- |
| **主库** | Obsidian | 写、链、版本、Git、长期沉淀 |
| **追问层** | NotebookLM | 针对某一批「已筛选源」做问答、摘要、对照 |

Obsidian 继续当「源真相」；NotebookLM 当「临时阅卷老师」——只改卷子，不改档案室。

​

  

![[笔记同步助手/images/009638c6e849506f85ef150002c96c97_MD5.png]]

  

---

## 第一步：在 Obsidian 里划定「可导出源」

不要 Export 整个 vault。我用的筛选标准：

1.  **只要 `知识库/concepts/` 和已完成的 project README**
    
2.  **排除**`笔记/` 过程稿、`.obsidian/`、含密钥的路径
    
3.  单篇先 **合并成 PDF 或 Markdown 打包**（NotebookLM 支持 PDF、Google Doc、粘贴文本等）
    

示例：从 `E:\RuyiObsidian\知识库\concepts\` 选 12 篇 AI / MCP / 爬虫相关概念笔记，导出为一个文件夹。

**避坑 1**：导出前全局搜 `apiKey`、`Bearer`、`sk-`，有则先删或打码。NotebookLM 源一旦上传，别指望「撤回等于没泄露」。

---

## 第二步：清洗 Markdown（10 分钟值得花）

Obsidian 特有语法 NotebookLM 不一定友好：

-   `![[wikilink]]` → 改成纯文本标题或脚注
    
-   嵌入图片若不需要可删，减少噪声
    
-   超长 frontmatter 可保留 tags，删掉内部 `source_note` 也行
    

我用 Cursor 跑过一条简单规则：**只保留 H2 以上结构和正文**，wikilink 改成「见《标题》」。

---

## 第三步：导入 NotebookLM，建「专题笔记本」

1.  打开 NotebookLM
    
2.  新建 Notebook，命名如 `AI工具-202605`
    
3.  上传刚才的 PDF/MD（或分批上传，**建议单专题 ≤ 20 篇**）
    
4.  等索引完成后再提问——别上传一半就开始问
    

我 12 篇 concepts 导入后，笔记本源列表清晰，后面追问质量明显好于「50 篇大杂烩」。

​

  

![[笔记同步助手/images/29ef2a2e8a9c601428ce346997369a6a_MD5.png]]

  

---

## 第四步：用「带引用」的方式追问

NotebookLM 的价值在 **回答带源引用**。我常用的三个问法：

### 1\. 横向对照

> 根据源文档，MCP、REST API、直接读文件三种接 Obsidian 的方式，各适合什么场景？请逐条引用来源。

### 2\. 找缺口

> 哪些主题在源里只有概念没有操作步骤？列成清单。

### 3\. 出提纲

> 我要写公众号《本地 MCP 接 Obsidian》，基于源给 5 段大纲，每段注明引用哪篇。

Obsidian 里该写的「长期结论」，仍然写回 `知识库/`；NotebookLM 的输出当**草稿加速器**，不要不经核对就当终稿。

---

## 第五步：写回 Obsidian，闭环双轨

追问得到的有价值结论，我会：

1.  在 Obsidian 新建或更新一篇 `知识库/` 笔记
    
2.  frontmatter 写 `status: 已完成`
    
3.  Git commit，保持主库可追溯
    

NotebookLM 笔记本可以 **每月重建**（源更新了再导一批），不必和 vault 一一同步。

这就是双轨的核心：**Obsidian 管写入与版本，NotebookLM 管阶段性阅读理解。**

---

## 三个避坑（我真实踩过的）

![[笔记同步助手/images/f8ca14d79c501bf7b8926254b1cb2c64_MD5.png]]

  

**坑 1：全库导入**  
源越多，幻觉式「综合」越多。先 10～20 篇试跑。

**坑 2：把 NotebookLM 当权威**  
它不读你 Obsidian 的最新编辑。重要结论必须以主库为准，NotebookLM 仅辅助。

**坑 3：敏感笔记进云**  
客户资料、密钥、未公开合同 — **不要上传**。本地库 + 本地 MCP 才是这类数据的正路。

---

## 今晚就能试：5 步 mini 版

1.  Obsidian 里选 **10 篇**你最常翻的概念笔记
    
2.  导出 PDF（或 MD 合并）
    
3.  NotebookLM 建笔记本，只上传这 10 篇
    
4.  问一个真实问题：「这些源里，和我当前项目最相关的 3 个坑是什么？」
    
5.  把答案里 **有引用支撑** 的 1 条，写回 Obsidian
    

一周下来，你会清楚：哪些专题值得单独建 Notebook，哪些继续只在 Obsidian 里双链即可。

---

## 结尾

笔记写的价值，最终要落在「被用起来」上。Obsidian 擅长沉淀与链接；NotebookLM 擅长在**限定源**里快速问答。两者不是替代，是双轨。

**你在用 Obsidian 吗？** 评论区回复 **「双轨」**，我发一份「Obsidian 导出清单模板」（含路径筛选规则和打码检查项）。也可以说说你更想用 NotebookLM 问哪类问题，下篇我可以按场景写追问 prompt 库。

---

## 如果觉得有用：

-   点个「在看」
    
-   转发给囤笔记却找不到的朋友
    
-   回复「双轨」领导出清单
    

**关于我：** 张大鹏，公众号「AI程序员张总」。专注 AI 应用、Agent 与知识库工作流落地。

  

---

![[笔记同步助手/images/9216ffd7442f502a3924c70004464e06_MD5.jpg|cover_image]]

原创 惠玩科技张大鹏 AI程序员张总

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/f15b70fd_1779407716875?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzA5NjQ1ODYwNg%3D%3D%26mid%3D2659092639%26idx%3D1%26sn%3D7a2a7b5b900054fde98038b0464800c5%26chksm%3D8a6f6df8f5d35798e597426aa43bb40deec7e2ac04f3666446374c548732720377e1c9c9e8cb%26mpshare%3D1%26scene%3D1%26srcid%3D0522LMwCLFqjNS6h6Ghz4nAo%26sharer_shareinfo%3D3934ece9d9a3902dc3681bc39c8bb2ea%26sharer_shareinfo_first%3D3934ece9d9a3902dc3681bc39c8bb2ea%23rd&s=obsidian)