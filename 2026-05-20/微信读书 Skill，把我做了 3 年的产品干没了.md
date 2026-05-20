---
author: 空格丶
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzkxMTQ0ODE3Ng==&mid=2247495199&idx=1&sn=d56f4187dca136a2ae1277bbe1e9ca2f&chksm=c0dc5bbf5ec9cb6fc0538e05a1c207fb1c933743d78b27624cfd62afb20c7d62811ced366f19&mpshare=1&scene=1&srcid=0520v4q9jxykwvV4rKKec5sW&sharer_shareinfo=2512a81ad3921742801334d14086ac4c&sharer_shareinfo_first=2512a81ad3921742801334d14086ac4c#rd
saved: 2026-05-20 09:01:09
tags:
  - 笔记同步助手
id: c3ea70e6-d44b-460d-bf9f-ade61c6a8bd4
---

公众号名称：空格的键盘

作者名称：空格丶

发布时间：2026-05-20 08:12

前几天，微信读书把自己的 Skill 开源了。

我看完它的使用案例，第一反应是：我和搭档做了两年的产品，可以下线了。

readecho 是我和搭档两年前开始做的小产品。

功能不复杂，Readecho 可以把你微信读书里的划线和笔记同步出来，再用 AI 帮你做一些分析和洞察。

![](https://relay-1.bijitongbu.site/p/2c14d29410b09da721df92a89396e675.png)

上线到现在做了一千多个用户，也有一点微薄的收入。

市面上还有一大批围绕微信读书非公开接口做的第三方插件和 App。

大家都是依赖微信之前开放的划线笔记 API，拿到用户的划线笔记，再包装成一个能用得上的产品。

而这次官方 Skill，微信把之前开放的笔记和划线，扩大到了书**架、阅读时长、章节目录、热门划线、个人想法、阅读统计、推荐书单。**

![](https://relay-1.bijitongbu.site/p/2ef0b6581f52a86df0ac8785d63025ca.png)

它的安装方式也非常简单，

访问微信读书网页版，到 Skill 页面，只需要操作下面两步就能在 Agent 里调用了。

![](https://relay-1.bijitongbu.site/p/fbaebdb10d013d79b232f391816c7709.png)

之前我还一直在说**很多 Skill 的开放让一些 sass 产品没有存在的价值了**。

没想到这句话在今天也伤到了自己。

自己亲手做的产品被官方的一个更新就碾压了。

不过我并没太多情绪变化，Readecho 有一年没更新了，这次微信读书 skill 的开放，让 readecho 获得了新生，也就是下面我做的几个 skill。

在我看来，微信读书的 Skill 最大的门槛不是安装，而是使用。

这个 Skill 要依赖用户会问、会拼，会把零散的回答串成有用的产出，对大多数用户，包括我在内，我第一时间拿到它问了几次我读了哪些书，有什么笔记内容，之后就再也没去使用了。

我现在想解决的问题，和 Readecho 当年想解决的一样。

**我们应该如何把微信开放的数据做成标准化的使用场景？**

结合我在微信读书这块做了不少产品分析，我是有不少发言权的。

于是花了几天时间，磨出了这三个 Skill ，对应导出、分析、使用三个场景，**把微信读书 Skill 用到极致。**

免费开源，文末附链接，能够更好的帮你用好微信读书。

**三个 Skill 的设计思路**

我把使用微信读书这件事，拆成了一条用户路径：

| 阶段 | 想做什么 | Skill |
| --- | --- | --- |
| 导出 | 把所有划线和笔记拿出来归档 | space-weread-export |
| 分析 | 看看自己到底是什么阅读类型 | space-weread-analyzer |
| 使用 | 让读过的书真的影响后续的工作 | space-weread-coach |

三个 Skill 顺着「读完书之后我想干什么」这条线设计，构成一个完整的链路。

下面分别说说每一个效果如何。

**1\. 导出：把划线变成可归档的资产**

第一个 Skill 叫**space-weread-export。**

你只需要说一句：「导出我的微信读书划线」。

它会先问你两件事：要 Markdown 还是 PDF，要全部书还是指定一本。

![](https://relay-1.bijitongbu.site/p/39aeb66eb873257907c12786a8abee69.png)

回答完就开始干活，自动调用接口，把所有笔记按书籍和章节排序，每条划线带上时间，生成排版整洁的文件。

我自己跑了一遍，87 本书、436 条划线、48 条想法，几分钟跑完，输出一份 158KB 的 Markdown 和一份 2.9MB 的 PDF。

![](https://relay-1.bijitongbu.site/p/465ac80174cd6d802118a49e530581a5.png)

导出之后能干什么？

我自己的用法有两个：

**一是放进知识库。**

我的 Obsidian 里有专门一个目录存读书笔记，导出的文件直接进去，搜索和回顾都方便。

**二是精读热门划线。**

如果你指定的某本书你自己没读过，Skill 会问你要不要导出这本书的热门划线，也就是其他读者的高频划线。

我以前的习惯，就是先看一本书的热门划线，再决定要不要读全书。

这是以前 Readecho 做不到的，相当于下载一本书的精华部分。

比如下面是我导出的《聪明的投资者》这本书的热门划线，它还会统计这条划线有多少人。

![](https://relay-1.bijitongbu.site/p/b8a48c03334196f0ce1e27649fde29f6.png)

**2\. 分析：一份 10 维度的阅读画像**

第二个 Skill 叫 space-weread-analyzer。

它会拉取你的全量阅读数据，从十个维度做分析：阅读画像、兴趣变化、知识结构与盲区、阅读质量诊断、高价值内容提炼、书籍关系网络、行动建议、选题建议、缺失知识类型、补充推荐。

最后输出一个 9:16 比例的白底简约 HTML 报告，11 张卡片，可以截屏发小红书。

![](https://relay-1.bijitongbu.site/p/7d20f1313628846747d826a11cbfbf54.png)

![](https://relay-1.bijitongbu.site/p/31b57db203f57752350be15def1deab9.png)

我用自己的数据跑了一次，有几个发现挺扎心：

完成率 54%，但有 25 本书完成度低于 30%，属于焦虑式收藏。

近一年阅读时长 4.8 小时，比前一年 33 小时下降了 85%。这反应了我这一年的精力管理问题。

Skill 还会基于阅读偏好猜一个 MBTI，给我的判断是 INFJ，差一个字母就猜中了，整体看完觉得挺准。

这份报告最大的价值，在于让你面对自己的真实阅读状态，为自己的阅读查漏补缺。

**3\. 使用：让划线真正参与日常工作**

第三个 Skill 叫 space-weread-coach，它解决的是「划线吃灰」的最后一公里。

它有三个用法：

**1）推荐书籍**

比如下面场景，我让它给我推荐一些理财相关的书籍，它会结合我书架上已经读过的书来判断我的段位，结合我的兴趣来推荐。

![](https://relay-1.bijitongbu.site/p/a7cdd32eb0f30f2847cea4c8261c9054.png)

![](https://relay-1.bijitongbu.site/p/7b801a56746adb5176dceb76ccc94735.png)

**2）引用**

比如下面我让他根据我在写的 Ai 改变生产力主题的文章，推荐一些热门划线。

![](https://relay-1.bijitongbu.site/p/3c0a48ee5085504148093204693c3ebe.png)

它会从你的 436 条划线里筛出最相关的几条，附上原话、书名、章节，并给出使用建议。

**3）回顾**

每天推送一条你过去划过的笔记。

它会自动去重，保证你不会反复看到同一条，越老的划线越优先被翻出来。

推送方式两种：你主动问「今天给我推一条」

或者用 Claude Code 的 `/loop` 定时触发，每天早 8 点通知一条划线笔记。

把你过去的阅读，重新变成一种持续的精神资源。就像我在Readecho 里做的这个回顾卡片

![](https://relay-1.bijitongbu.site/p/06f9f18223cfd5f6cc0fd9ec3efefe8a.png)

所有 Skill 都已经开源放到 GitHub 上：

github.com/zephyrwang6/space-weread

你可以随便用、随便改。

如果你符合下面任何一种情况，都值得一试：

-   微信读书重度用户，划线几百条以上，但很少回顾
    
-   内容创作者，写作的时候需要引用读过的书
    
-   想做个人知识管理，但缺一个把读书数据结构化的入口
    
-   对 Claude Code Skill 感兴趣，想看看一个完整的 Skill 体系长什么样
    

微信读书的 Skill 是我目前看到的价值含量最高的，只是针对一本书去挖掘都有不少场景去做，建议使用微信读书的朋友们都可以去试试。

---

![cover_image](https://mmbiz.qpic.cn/mmbiz_jpg/CFe2b8yvCoxY8ia3rvKyCH62ONPdnrTneAg96WopiahYNHQiceMx7p92dqiakCWD2jEB09uWLY5ibXnQF64mEqQpyNZSImnFVGFyHPKzLPX3IcCU/0?wx_fmt=jpeg)

Original 空格丶 空格的键盘

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/efa4e2fc_1779238868711?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkxMTQ0ODE3Ng%3D%3D%26mid%3D2247495199%26idx%3D1%26sn%3Dd56f4187dca136a2ae1277bbe1e9ca2f%26chksm%3Dc0dc5bbf5ec9cb6fc0538e05a1c207fb1c933743d78b27624cfd62afb20c7d62811ced366f19%26mpshare%3D1%26scene%3D1%26srcid%3D0520v4q9jxykwvV4rKKec5sW%26sharer_shareinfo%3D2512a81ad3921742801334d14086ac4c%26sharer_shareinfo_first%3D2512a81ad3921742801334d14086ac4c%23rd&s=obsidian)