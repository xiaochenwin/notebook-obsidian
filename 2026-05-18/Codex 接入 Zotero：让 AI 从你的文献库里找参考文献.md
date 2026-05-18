---
author: Leo Duan
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484229&idx=1&sn=7133cde31815b69b50cc670a7d2cbad2&chksm=ce1f3c9af9c87768dc01c749291a0ad9dfbbf5658259b3b8e8bfb84fa283aba74e0e8be98a81&mpshare=1&scene=1&srcid=0518eOOiR90VICzcBLFMpVJS&sharer_shareinfo=9f460e8fc361f740acb9a932ed7bd4ab&sharer_shareinfo_first=9f460e8fc361f740acb9a932ed7bd4ab#rd
saved: 2026-05-18 17:35:19
tags:
  - 笔记同步助手
id: 845d7381-b376-4332-8830-4549b5c631a2
---

公众号名称：R语言统计学习

作者名称：Leo Duan

发布时间：2026-05-11 22:21

# Codex 接入 Zotero：让 AI 从你的文献库里找参考文献

写论文讨论部分、方法学综述，很多人都会遇到一个问题：观点已经有了，但对应文献一时想不起来。

我们让 AI 帮忙找文献时，也经常担心它把题名、作者、DOI 混在一起。明明只是想补一个参考文献，最后还要反过来核对它有没有编错。

这时，Codex 的 Zotero 插件就有用处了。它不是让 AI 去全网“猜”文献，而是让 Codex 先进入我们自己的 Zotero 库，再从已有条目里检索、整理、生成引用。

​

---

## Zotero 插件是做什么的

Zotero 本来就是很多医学研究者管理文献的主力工具。我们平时把论文收进 Zotero，打标签、分文件夹、补 DOI，但真正写作时，文献和正文往往还是断开的。

Codex 接入 Zotero 后，可以做几件简单但实用的事：

-   • 读取我们 Zotero 库里的文献条目
    
-   • 按关键词或条目 key 查找文献
    
-   • 生成参考文献格式
    
-   • 把参考文献写入 Markdown、Word 等文档
    

它的核心不是替我们判断“该引用哪篇”，而是把 AI 的检索范围限制在我们已经收藏的文献库里。

​

---

## 在 Codex 里安装 Zotero 插件

在 Codex 的插件页面，把筛选条件切到 **Built by OpenAI**，往下找到 **Research** 区域，就能看到 Zotero。

截图里可以看到，Zotero 插件的说明是：_Find papers and add citations from Zotero_，也就是从 Zotero 里找论文并添加引用。

点击右侧的加号即可安装。安装后图标旁边会显示对勾。

第一次使用时，需要完成 Zotero 授权。授权完成后，Codex 才能读取我们 Zotero 账号里的文献条目。这里建议先确认 Zotero 已经完成云同步，否则本地刚新增的文献可能还不会出现在 Codex 能看到的列表里。

​

---

## 先让 Codex 列出 Zotero 里的文献

刚开始不建议直接让它写一大段综述。更稳的做法是，先让 Codex 做一个简单任务：列出当前能读取到的参考文献。

可以这样问：

​

```
用 Zotero 插件列出我的参考文献，先给我一个精简清单。
```

下面这张截图里，Codex 从 Zotero 库里读取到了 90 条参考文献，并列出了部分条目。每条前面的方括号是 Zotero 条目 key，后面是作者、年份和题名。

这一步很重要。它相当于先确认三件事：

1.  1\. 插件已经装好
    
2.  2\. Zotero 授权已经生效
    
3.  3\. Codex 读到的是我们自己的文献库
    

比如截图里的 `8EBHDND4` 对应 Peduzzi 等 1996 年关于 logistic regression 每变量事件数的文章。对做临床预测模型的人来说，这类文献经常会在 EPV、样本量、变量筛选讨论里用到。

​

---

## 按条目 key 生成参考文献

确认能读到 Zotero 后，就可以让 Codex 针对某一条文献生成引用。

例如，我们想把 Peduzzi 这篇文章插入到一个 Word 文档里，可以直接这样说：

​

```
把 [8EBHDND4] Peduzzi 等（1996）：Events per variable in logistic regression 这条参考文献，
插入到「引用参考文献测试.docx」文档。
```

截图里可以看到，Codex 已经根据 Zotero 条目生成了 Word 文档，并把参考文献写入其中。

生成的引用内容包括作者、题名、期刊、年份、卷期、页码和 DOI：

​

```
[1] Peduzzi P, Concato J, Kemper E, Holford T R, Feinstein A R.
A simulation study of the number of events per variable in logistic regression analysis[J].
Journal of Clinical Epidemiology, 1996, 49(12): 1373-1379.
doi:10.1016/S0895-4356(96)00236-3.
```

这里有一个小细节：用 Zotero 条目 key 来指定文献，比只说“找 Peduzzi 那篇 EPV 文章”更明确。因为同一个作者可能有多篇文章，题名也可能被我们说得不完整，key 可以减少匹配偏差。

​

---

## 看一下 Word 里的效果

最后一步不要省。文献生成以后，还是要打开 Word 看一眼版式和字段。

下面这张截图就是写入后的 Word 文档。可以看到，正文里已经有“参考文献”标题，下面插入了编号式参考文献。

这个例子比较简单，但能说明 Zotero 插件的基本逻辑：先从 Zotero 里定位文献，再把这条文献整理成我们需要的引用格式，最后写入目标文档。

​

---

## 小结

-   • Codex 的 Zotero 插件可以让 AI 从我们自己的 Zotero 库里找文献，而不是凭空生成引用。
    
-   • 实操时建议先列出文献清单，再用 Zotero 条目 key 指定目标文献。
    
-   • 生成后仍然要打开文档看一眼，确认作者、题名、期刊和 DOI 没有问题。
    

---

## 往期推荐

-   • [亚组分析做错了？那篇2005年Lancet短文，说透了90%人都会犯的错](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484120&idx=1&sn=045dff9fb95ca7ba6ad5562db9085a64&scene=21#wechat_redirect)
    
-   • [SPSS 和 R 逻辑回归的 95% 置信区间为什么不一样？Wald vs 轮廓似然法 | 附完整代码](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484127&idx=1&sn=c83d8299c7388e67fa8002f5fda20568&scene=21#wechat_redirect)
    
-   • [R语言加权逻辑回归的本质：加权就是复制数据！](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484109&idx=1&sn=b14833cd7a13877a413b2752905cbdd8&scene=21#wechat_redirect)
    
-   • [Mann Whitney U Test和Wilcoxon rank-sum test傻傻分不清楚](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484044&idx=1&sn=bef2a6801a92484caf8ca88ba6421468&scene=21#wechat_redirect)
    
-   • [校正曲线原理](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247483994&idx=1&sn=678f0ea77abed7b0bfc0d6d649a153db&scene=21#wechat_redirect)
    
-   • [方差分解的证明](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247483969&idx=1&sn=4710f29e51491f78dd82e886017ff680&scene=21#wechat_redirect)
    
-   • [基线表、单因素表、多因素表导出到Word](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247483891&idx=1&sn=f5e01e20efdf2f13ede56daacbe523cc&scene=21#wechat_redirect)
    
-   • [kmeans最佳聚类数判断依据-轮廓系数](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247483741&idx=1&sn=fd884515569b814cd7d766709caaf2e5&scene=21#wechat_redirect)
    
-   • [临床预测模型评价指标之C index计算原理](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247483728&idx=1&sn=569d070ce1f46f1567d111924ac82a85&scene=21#wechat_redirect)
    
-   • [列线图总得分计算原理及风险分层KM曲线](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247483693&idx=1&sn=d6af1c555629602fd4cd8dd7d66c744a&scene=21#wechat_redirect)
    
-   • [亚组分析的灵魂一问：亚组效应怎么和整体比？交互检验告诉你 | 附完整代码](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484210&idx=1&sn=a19a8d8303048f48a35b2badb03c060a&scene=21#wechat_redirect)
    
-   • [用 AI + draw.io 10 分钟画出专业技术路线图 | 附完整提示词](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484204&idx=1&sn=de258d0ef87ad77d182682b4b58cdfcb&scene=21#wechat_redirect)
    
-   • [用相关系数比较两种测量方法？Bland-Altman 图才是正解 | 附完整代码](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484197&idx=1&sn=54de0d509f178a08f84345524bd6efcc&scene=21#wechat_redirect)
    
-   • [为什么 HR 会越随访越小？用 R 复现 Hernán 2010 的经典场景 | 附完整代码](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484186&idx=1&sn=f262c48d1afa49eac2147fa2916d19e1&scene=21#wechat_redirect)
    
-   • [Landmark 分析怎么做？从“有反应者活得更久”的偏倚说起](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484178&idx=1&sn=e1871091f5930834f732ae3b25effc2c&scene=21#wechat_redirect)
    
-   • [变量放多少个合适？用 R 理解每变量事件数（EPV）规则 | 附完整代码](https://mp.weixin.qq.com/s?__biz=Mzg3NzcwMTI1Ng==&mid=2247484170&idx=1&sn=28854bcb4145af3ee64f78c6c0f84ab7&scene=21#wechat_redirect)
    

  

---

Original Leo Duan R语言统计学习

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/81fd1e91_1779096918567?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzg3NzcwMTI1Ng%3D%3D%26mid%3D2247484229%26idx%3D1%26sn%3D7133cde31815b69b50cc670a7d2cbad2%26chksm%3Dce1f3c9af9c87768dc01c749291a0ad9dfbbf5658259b3b8e8bfb84fa283aba74e0e8be98a81%26mpshare%3D1%26scene%3D1%26srcid%3D0518eOOiR90VICzcBLFMpVJS%26sharer_shareinfo%3D9f460e8fc361f740acb9a932ed7bd4ab%26sharer_shareinfo_first%3D9f460e8fc361f740acb9a932ed7bd4ab%23rd&s=obsidian)