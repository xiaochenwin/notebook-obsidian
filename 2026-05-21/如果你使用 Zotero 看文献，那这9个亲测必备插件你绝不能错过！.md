---
author: 口天三木
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk3NTE1MDQ5Ng==&mid=2247484048&idx=1&sn=afcea72ce3c222606d37e7b8437ebac2&chksm=c5b0443919be3b7ada67c845a39b9acb5bda3c2b488c82c2151ac833e7c6842f2d0c49a0a733&mpshare=1&scene=1&srcid=0521aS72ARxmIITvhVXUY2wT&sharer_shareinfo=21e4689cbc3be0436098e161113554c8&sharer_shareinfo_first=21e4689cbc3be0436098e161113554c8#rd
saved: 2026-05-21 07:27:58
tags:
  - 笔记同步助手
id: d8e497be-5783-4bbd-a019-2ee1c861f851
---

公众号名称：口天三木

作者名称：口天三木

发布时间：2026-05-20 23:29

前阵子整理 Zotero 配置文件，顺手把一直在用的插件翻出来捋了一遍。本来只是想清点一下，结果越看越觉得——有些插件真的是用了就回不去了。干脆整理出来分享给需要的人，顺便把 GitHub 地址也查好，方便大家直接去找。

以下 9 个插件按实用场景分组，排名不分先后，都是我自己长期在用、觉得确实能提升效率的。

![](https://relay-1.bijitongbu.site/p/b42d7b4c8bfbcbe8222688281afd3603.png)

---

## 📚 文献阅读 & 笔记

### Better Notes — 在 Zotero 里完成阅读到笔记的全流程

-   **GitHub**: windingwind/zotero-better-notes
    
-   **作者**: windingwind（也是下面好几个插件的作者，Zotero 插件生态的劳模）
    

Better Notes 是我目前写文献笔记的主要工具。它的思路很简单：你不需要离开 Zotero 就能完成"读论文→划重点→写笔记→整理入库"这条链路。标注直接在 PDF 阅读器里搞定，笔记可以做得很有结构——支持模板、支持双向链接、还能跟 Obsidian 打通。

我最常用的是它的笔记同步功能：在 Zotero 里写好的笔记，一键推送到 Obsidian 库里，反过来 Obsidian 里改了也能同步回来。对于用 Obsidian 做知识管理的人来说，这基本解决了文献笔记和工作笔记之间的割裂问题。

​

### Zotero Reference — PDF 内一键跳转参考文献原文

-   **GitHub**: MuiseDestiny/zotero-reference
    
-   **作者**: MuiseDestiny
    

这个插件功能很纯粹——读论文时遇到引文，点一下就能跳转到参考文献列表里的对应条目，再点一下还能直接打开那篇参考文献的 PDF（如果你的库里有的话）。

听起来是个小功能，但读那种几十页的长论文时特别好用。作者在论文里提了一嘴"as shown in Smith et al. (2019)"，你不用手动翻到文末去找参考文献编号，再翻到参考文献页去找是哪篇——插件帮你串联好了。配合 Zotero 本身的文献关联功能，整个引用网络在阅读过程中是"可点击"的。

---

## 🌐 翻译

### Translate for Zotero — 内联翻译，边读边译

-   **GitHub**: windingwind/zotero-pdf-translate
    
-   **Stars**: 10.9k ⭐（Zotero 插件里最顶级的存在）
    
-   **支持**: Google、DeepL、Microsoft Translator、OpenAI 等 20+ 翻译引擎
    

我读英文文献的主力翻译工具。选中一段文字，翻译直接显示在弹出窗口或者侧边栏里，不用复制粘贴到浏览器或者翻译软件里折腾。支持 Google、DeepL、微软翻译等 20 多种引擎，可以按需切换。如果你自己有 DeepL 或 OpenAI 的 API key，也可以在设置里配好，翻译质量和速度都更可控。

还有一个很贴心的细节：做标注的时候，翻译结果可以自动追加到注释的 comment 里，等于高亮和翻译一起保存了，回过头复习时一眼就能看懂当时划的这段是什么意思。

​

### Suppr（超能文献翻译）— 整篇文档翻译，格式保留

-   **GitHub**: WildDataX/suppr-zotero-plugin
    
-   **官网**: https://suppr.wilddata.cn
    
-   **特点**: 支持 PDF / Word / PPT / Excel 整篇翻译，保留原始排版
    

如果说 Translate for Zotero 适合"边读边译"，那 Suppr 适合"我需要快速搞懂整篇在说什么"。它支持整篇 PDF 或 Word 直接翻译，而且翻译结果能保留原文档的排版——图表、公式、段落的相对位置基本不变。对于那种时间紧、只想快速掌握核心内容的文献，省事不少。

插件本身的定位是辅助阅读英文文献，新用户注册后有 25 万汉字的免费额度，轻度使用基本够用。

现在大家可以在下面通过我的邀请链接前往注册，注册成功你也有积分获取，一次几MB的PDF翻译平均需要300积分，算下来够你免费翻译4、5份文献啦！！！

![](https://relay-1.bijitongbu.site/p/5c817d0780e80bea1c2ad57f74a5e7aa.png)![](https://relay-1.bijitongbu.site/p/e0bdf47a3c323134385c7eb54967a85b.png)

邀请链接：

https://suppr.wilddata.cn?referralCode=GtNKPt

https://suppr.wilddata.cn/translate/upload?referralCode=GtNKPt

---

## 🏷️ 效率 & 自动化

### Actions & Tags — 让 Zotero 替你干活

-   **GitHub**: windingwind/zotero-actions-tags
    
-   **作者**: windingwind
    

如果说其他插件是在"增强 Zotero 的能力"，Actions & Tags 则是在"让 Zotero 自己动起来"。

它的核心是事件驱动：你可以设定规则，比如"当我给一篇文献添加某个标签时，自动执行某个动作"，或者"当我关闭一篇 PDF 时，自动给它打上已读标签"。支持的条件和动作组合很灵活，可以写简单的脚本逻辑。

我自己的用法：入库新文献时自动打上 `/unread` 标签，读完关闭 PDF 后自动去掉；读到特别重要的文献，一键打上 `⭐` 标签的同时自动创建一条笔记模板。文献几百篇的时候，手动管理标签会变成噩梦，而这种自动化的边际效应非常明显。

​

### Better BibTeX — LaTeX / Markdown 写作者的命根子

-   **GitHub**: retorquere/zotero-better-bibtex
    
-   **当前版本**: 已到 9.x，维护非常活跃
    

如果你用 LaTeX 写论文，或者像我一样在 Obsidian 里通过 citation key 引用文献——Better BibTeX 就是那个你装了就不会意识到的存在，因为没了它会很难受。

它自动从 Zotero 条目生成规范且稳定的 BibTeX key（可以自定义格式），并且在你修改文献信息时自动同步更新 `.bib` 文件。对于 Overleaf 用户来说，配合 Zotero 的自动导出功能，基本可以做到"在 Zotero 里添加一篇文献，Overleaf 那边就能直接 cite 了"。

---

## 📊 文献评价 & 信息增强

### Zotero Box — 影响因子、分区一眼可见

-   **官网**: scigreat/zotero-box
    

导入文献时自动抓取影响因子、JCR 分区、中科院分区、引用次数等信息，直接显示在 Zotero 的条目列表里。不用专门去期刊官网查，也不用在浏览器里开一堆标签页对照。

![](https://relay-1.bijitongbu.site/p/41a21af2b2f681fe1d1d748ff054b3a6.png)

做文献筛选时尤其有用：面对一堆相似主题的论文，IF 和分区信息能帮你快速判断哪些是领域内的顶刊文章，优先精读。Zotero Box 把这些信息直接嵌入到了文献管理流程里，属于那种加了之后不觉得有什么、去掉才发现很不方便的工具。

对于这个插件么我要打“五星好评”，没有之一，包括茉莉花那个插件爱你的功能他这里都集成了，所以我没有单独把茉莉花插件拿出来，然后他这里也有GPT功能，效果还是可以的！而且他还强化了批注和界面的美观，这个插件真的以一抵三！！！

​

### Zotero GPT — 在 Zotero 里直接问 AI

-   **GitHub**: MuiseDestiny/zotero-gpt
    
-   **作者**: MuiseDestiny（上面 Reference 也是他的作品）
    

选中 PDF 里的内容，右键就能直接问 GPT——总结这一段在说什么、解释某个术语、或者提一个具体问题。所有交互都在 Zotero 界面内完成，不用切到浏览器复制粘贴。

相比 Better Notes，Zotero GPT 更"轻"：它不是要取代你的笔记系统，而是在你读文献的过程中提供一个随时可以调用的 AI 助手。适合那种"快速问一下就走"的场景。如果你自己有 OpenAI API key，在设置里配好就行，没有额外费用。

他还内置了许多命令，也就是prompt提示词，你也可以自行定义提示词

![](https://relay-1.bijitongbu.site/p/9a52f5a2cd97b0921d4f342ba5e5555d.png)

最近好像还多了个可以生成Obsidian的canvas画布功能

![](https://relay-1.bijitongbu.site/p/a4cc08a34a954bb48f1b1c297ccd8f57.png)

然后AI模型的话，我推荐DeepSeek V4 Pro，以及Claude sonnet(如果有能力使用的话)

下面的是我用DeepSeek总结其中一篇文献的鸟瞰图，虽然输出有点慢，但是很准很优美！！！ 还是有双链可跳转，方便以后做知识图谱

![](https://relay-1.bijitongbu.site/p/04ee1a58286df81461d856a5a2156cc4.png)

---

## 🎨 界面 & 视觉

### Zotero Style — 文献库也能赏心悦目

-   **GitHub**: MuiseDestiny/zotero-style
    
-   **作者**: MuiseDestiny
    

这个插件让 Zotero 的界面变得好看不少——但这只是最表面的功能。

它真正有价值的能力是**嵌套标签**：你可以用 `#主题/子主题` 的格式来组织标签，比如 `#方法/深度学习`、`#方法/贝叶斯`，然后在 Zotero Style 的标签视图里就会自动形成层级结构。对于习惯用标签而非文件夹来组织文献的人来说，这比 Zotero 自带的标签系统好用太多了。

此外还有关系图谱功能（类似 Obsidian 的图谱视图），可以直观看到文献之间的引用关联。论文多了后，图谱上能发现一些你平时没注意到的联系。

然后他还对zotero原生PDF批注和笔记做了美化，搭配zotero box使用好看到爆炸！！

![](https://relay-1.bijitongbu.site/p/d4c0054b0ac6b50b6375dc01c4747eb2.png)

---

## 🧩 附加推荐：不一定必备，但看场景

### LLM for Zotero

-   **GitHub**: yilewang/llm-for-zotero
    
-   **Stars**: 800+ | **下载量**: 4 万+
    

Zotero 里直接调用大模型（支持 OpenAI、Claude、本地模型等），读 PDF 时边看边问。比 Zotero GPT 更灵活，模型可以自己随便选，不依赖特定 API。下载量 4 万多，社区活跃度很高。

对于经常用 Claude Code 或 Codex 的用户来说，这个插件可能更有用——可以用自己熟悉的模型在文献管理场景里延续 AI 辅助的工作流。

不过缺点也是有的，至少我最近在使用zotero9.0.1的时候这个插件总是一堆bug存在，Codex的对话加载也比较慢，虽然功能确实强大，但是我觉得思路是可以借鉴的，自己“偷师”里面的architect和skills作为参考，直接在Codex或者Claude Code设置一套Agents或者plugin使用的话岂不美哉！！

当然啦！我也没有能力构建，这也只是我的个人想法啦，哈哈哈！还是对作者充满敬意之情

​

### Jasminum（茉莉花）— 中文文献的救星

-   **GitHub**: l0o0/jasminum
    

如果你经常处理中文文献（知网、万方等），茉莉花几乎是必须装的。它能自动拆分中文学者姓和名、为中文 PDF 检索元数据、更新中文转换器、拉取引用次数等信息。Zotero 原生对中文文献的支持比较有限，茉莉花弥补了这个短板。

​

### Zotero Pdf2zh

-   **GitHub**: guaguastandup/zotero-pdf2zh
    

PDF 双语对照翻译插件，翻译结果与原 PDF 排版对齐，适合需要逐段对照原文和译文的场景。

这个插件——yyds！！！只是前期需要Python的命令行配置，吓退了一打批小白，技术党无脑直接使用，不过最近一个星期可能因为zotero9.0.1还没有做适配，还是存在一定bug，静观其变吧！

​

### Magic for Zotero

-   **GitHub**: l0o0/MagicZotero
    

同样来自 l0o0（茉莉花的作者），提供了多项实用小工具集合，算是锦上添花的辅助插件。不过好像要收费，但是文档解析功能里的MinerU和doc2x其实可以自行配置，不一定需要套用他的插件

---

## 💡 一点说明

至于像 **Zotero MCP Plugin**、**Linter for Zotero** 这些，对于大多数人的日常文献管理来说没有太强的存在感——它们更多是针对特定场景（比如开发 MCP 服务、批量格式化元数据）才派得上用场，所以没有列入上面的必装清单。如果感兴趣的话，可以去 GitHub 上搜一下最新的 release 版本。

---

## 📥 下载方式

以上所有插件都可以通过下面两个渠道获取：

1.  **Zotero 中文社区插件市场**：https://zotero-chinese.com/plugins/ — 直接下载 `.xpi` 文件
    
2.  **我的百度网盘分享**（见下方链接），打包了上述全部 9 个必备插件
    

> 网盘里多了个 LLM for Zotero 插件，虽然没放进前面 9 个"必备"里，但对于经常用 Claude Code 或者 Codex 的群体来说可能也是刚需，所以一并放进去了。

**百度网盘链接：**

通过网盘分享的文件：zotero  
链接: https://pan.baidu.com/s/14CvNvfiWS3q7HSl6-oMIQQ?pwd=p5ye 提取码: p5ye  
\-- 来自百度网盘超级会员 v1 的分享

然后这个链接我会持续更新，作为zotero专辑，会涵盖面向大模型的skills，zotero插件和其他干货

> 另外，还有一个教大家免费获取20GB zotero云空间的办法，也放置在百度网盘链接，有需要自取，不过先说好了，这个云空间我不建议大家使用，亲测效果不太好，同步有点卡。还时不时抽风，还是推荐大家使用坚果云同步

那么，以上就是我这期主要分享的全部内容啦！制作和整理不易，希望大家多多支持！后续有精力的话再分享更多优质内容和工具

我是口天三木——A man who will become the Pirate King!

那么，下期见！

---

![cover_image](https://mmbiz.qpic.cn/mmbiz_jpg/ItpPOnp3YlhuXIVzkSLibE4M3cbtgPRTPXpb6NDibHlLVgkKOZsLIsg1n63iaekPkwiaWXvAiayMjESI9dcVhycNOgnspMZWX6XSnQQOuu3z0Cia4/0?wx_fmt=jpeg)

原创 口天三木 口天三木

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/8f3da73e_1779319677091?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk3NTE1MDQ5Ng%3D%3D%26mid%3D2247484048%26idx%3D1%26sn%3Dafcea72ce3c222606d37e7b8437ebac2%26chksm%3Dc5b0443919be3b7ada67c845a39b9acb5bda3c2b488c82c2151ac833e7c6842f2d0c49a0a733%26mpshare%3D1%26scene%3D1%26srcid%3D0521aS72ARxmIITvhVXUY2wT%26sharer_shareinfo%3D21e4689cbc3be0436098e161113554c8%26sharer_shareinfo_first%3D21e4689cbc3be0436098e161113554c8%23rd&s=obsidian)