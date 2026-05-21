---
author: 海鱼星的荷花塘
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzIyMzk1OTIxNQ==&mid=2247486231&idx=1&sn=d87c8f30a3b38ecf09973c5d8cf31c97&chksm=e9bf60f521bd03823cf2c01a274ce523b4083382b0e12e39605547d4259b4c04651af598477e&mpshare=1&scene=1&srcid=0520JVvBZmUssdCXuOFZbhKR&sharer_shareinfo=295818cca40d83011e28cbfbdf57adc1&sharer_shareinfo_first=295818cca40d83011e28cbfbdf57adc1#rd
saved: 2026-05-20 09:03:18
tags:
  - 笔记同步助手
id: 6c2f47c4-32c3-4a82-8f94-785e6dd4c40d
---

公众号名称：海鱼星的荷花塘

作者名称：海鱼星的荷花塘

发布时间：2026-05-15 21:03

前段时间我给你分享了图像生成[深度升级！GPT-Image-2 重构 AI 图像生成体验](https://mp.weixin.qq.com/s?__biz=MzIyMzk1OTIxNQ==&mid=2247485861&idx=1&sn=53a554dfa43a963237a52427da81ff4b&scene=21#wechat_redirect)，给大家介绍了apimart平台。我主要用它的GPT-Image-2，正常的作品图片的制作，不能这么麻烦，最好还是用 skill 去自动完成图片的创作，今天就用Trae Solo创建图片生成skill。

```
https://apimart.ai/zh
```

![[笔记同步助手/images/d49b8f0c032e9ab53e4263625534396f_MD5.png]]

## 一、登录获取api key

点击右上角的登录，输入用户名和密码，点击登录，如果你没有注册过，也可以点击下方的注册，因为我注册过了，这里就直接输入了

![[笔记同步助手/images/d766ed75b74059e600abc99e7d0aad8c_MD5.png]]

登录后，点击用户头像下的API密钥

![[笔记同步助手/images/9346d1af1585a7e5d4b440b84a4a6b11_MD5.png]]

点击右上角创建API密钥

![[笔记同步助手/images/886ac196c4f17739e89e6ab21489d3f7_MD5.png]]

输入名称，点击创建密钥

![[笔记同步助手/images/09cdc708c17672d678acb7e40f2153cf_MD5.png]]

生成了密钥，生成密钥后，就需要你充值，充值要适当，每次充值$1就可以，相当于每次充值¥7元，注意中转站一定不要充值过多。

![[笔记同步助手/images/2ff371ebce78a47ccab5206b1c5c356b_MD5.png]]

## 二、创建Skill

点击上方的api文档

![[笔记同步助手/images/1e93d9d2d143d124f67ce7d11a49810b_MD5.png]]

点击图像系列下面的GPT-Image-2 图像生成，点击复制

![[笔记同步助手/images/4cde123a557adf773ecb011d6cb5cdd7_MD5.png]]

打开Trae Solo,切换到Coding模式，trae solo的使用可以看看这个

[手把手带你玩转 Trae Solo，零基础也能懂](https://mp.weixin.qq.com/s?__biz=MzIyMzk1OTIxNQ==&mid=2247486195&idx=1&sn=272a71edc47cb2d337515232612900d9&scene=21#wechat_redirect)

![[笔记同步助手/images/0174a20dd4758f005544abcae872afce_MD5.png]]

在对话框里，先粘贴刚才的内容，在输入

```
帮我根据上面的信息制作成一个图片生成的 skill，API 为 ：xxx；创建好了，别忘记进行测试。
```

![[笔记同步助手/images/8aafaa50c5392b676dbdcbfd98d2ceb1_MD5.png]]

开始执行

![[笔记同步助手/images/f87b5a93f5aec03e84c57214fb340c6c_MD5.png]]

允许执行，点击添加 'pip' 到白名单，这样不用每次都点运行

![[笔记同步助手/images/54d3df1b615a64cfd9d85e31bbad8d04_MD5.png]]

完成

![[笔记同步助手/images/5bf733dbf9fde0e4d5438c71eb2d5337_MD5.png]]

看一下，它测试生成的图片

![[笔记同步助手/images/1f68f43895eb87f2d29582efc58c3fb7_MD5.png]]

查看是否调用了api key 看到刚才创建的api 已经消耗了$0.012

![[笔记同步助手/images/86815b6430154f9d5dd794c63bf7fa92_MD5.png]]

看了一下，它这个是创建了python库，不是skill技能，我继续让它创建一个，同时把模型也换成GLM-5

![[笔记同步助手/images/d2a134377438b45f78ae0dd296f53850_MD5.png]]

这次它生成了skill

![[笔记同步助手/images/20891012f24a89342a033e139ac7c0c5_MD5.png]]

让它安装

![[笔记同步助手/images/f5a1ad37af1ce126ef3e46134bd66743_MD5.png]]

由于它只能在我们给的目录执行，无法操作其他目录，只能自己安装了

![[笔记同步助手/images/fbd9e9842d826907ec67b87795962178_MD5.png]]

拷贝完后，让它重新加载skill

![[笔记同步助手/images/4e052816670107fa8610cba49bc3197d_MD5.png]]

手动测试一下,先按/键选择我们刚才创建的skill,在输入

```
帮我创建一张这个skill的功能介绍海报图，2k
```

![[笔记同步助手/images/7a2d91c4a89f8916c958d110b4b8e249_MD5.png]]

![[笔记同步助手/images/dec3909ee49d57ad5ec5ff54aab69519_MD5.png]]

这次生成了图片

![[笔记同步助手/images/dbc8d98f240e21827fac28bca1e98167_MD5.png]]

## 三、使用案例

由于现在的信息太多，以前我都会用元宝，帮我提炼文章主题和内容框架。看元宝给的简短总结，要是觉得有意思，我再通篇仔细读完整篇文章。现在可以换了个方式，直接用图片来代替文字总结。一眼就能看懂文章核心亮点，特别直观。

比如我把这篇文章的链接https://mp.weixin.qq.com/s/Mhd1s-rbSWiQVR054lVw6Q，粘贴告诉它生成图片，2k

![[笔记同步助手/images/f43d9866ba157f2b26239b22d8641840_MD5.png]]

开始使用技能和联网读取文章

![[笔记同步助手/images/52c79523847ad831d2890d4f28eb0547_MD5.png]]

执行生成图片

![[笔记同步助手/images/5e87154bf520e0d37aab80bd9d6a852a_MD5.png]]

我看了一下生成的图片，它总结了文章的主题，并按照工作流给出了操作步骤

![[笔记同步助手/images/61f15b7f5f404dd260b0264b1494e233_MD5.png]]

## 四、总结

![[笔记同步助手/images/8ea7ae8c5a7f41d9e294c52d60d01b4f_MD5.png]]

上面我演示的都是单张图，其实这个skill最大的优点是批量生成相关图片，如信息图、手绘风格图、小红书卡片等，剩下的就需要你自己去操作了。

说说花费吧，我实际用下来，单张图也就几分到一毛左右。做一组六七张的小红书配图，总成本还不到一块钱。比起开各类会员划算太多，画面风格还能自己随心把控。

最后你可以用你自己的图片平台，根据这个平台的API文档，用Claude Code、Codex、任意一个支持Skill技能的AI工具去创建你自己的图片生成agent。祝大家玩得愉快！

好了，今天就跟大家分享到这儿，觉得内容有用的话，别忘了点个赞、收藏再转发一下。大家有什么不懂的，或者想要什么新内容，都可以在评论区给我留言。咱们下期再见！

---

![[笔记同步助手/images/6dce942171f7f4455f45b7645368a294_MD5.jpg|cover_image]]

Original 海鱼星的荷花塘 海鱼星的荷花塘

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/b6b56c0e_1779238997526?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzIyMzk1OTIxNQ%3D%3D%26mid%3D2247486231%26idx%3D1%26sn%3Dd87c8f30a3b38ecf09973c5d8cf31c97%26chksm%3De9bf60f521bd03823cf2c01a274ce523b4083382b0e12e39605547d4259b4c04651af598477e%26mpshare%3D1%26scene%3D1%26srcid%3D0520JVvBZmUssdCXuOFZbhKR%26sharer_shareinfo%3D295818cca40d83011e28cbfbdf57adc1%26sharer_shareinfo_first%3D295818cca40d83011e28cbfbdf57adc1%23rd&s=obsidian)