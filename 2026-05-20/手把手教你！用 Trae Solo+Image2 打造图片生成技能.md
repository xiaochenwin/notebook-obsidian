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

![](https://relay-1.bijitongbu.site/p/865d05f99a16c09708985d89df6f45c7.png)

## 一、登录获取api key

点击右上角的登录，输入用户名和密码，点击登录，如果你没有注册过，也可以点击下方的注册，因为我注册过了，这里就直接输入了

![](https://relay-1.bijitongbu.site/p/6372e81cc0d467c3fbbacd2e641c7822.png)

登录后，点击用户头像下的API密钥

![](https://relay-1.bijitongbu.site/p/070879a26a6e7f7e8c6d6812faa1b5cf.png)

点击右上角创建API密钥

![](https://relay-1.bijitongbu.site/p/7444641d8062d0ba41b9f3652a37deb2.png)

输入名称，点击创建密钥

![](https://relay-1.bijitongbu.site/p/ae3bd56d6a60513d094bb745ba022985.png)

生成了密钥，生成密钥后，就需要你充值，充值要适当，每次充值$1就可以，相当于每次充值¥7元，注意中转站一定不要充值过多。

![](https://relay-1.bijitongbu.site/p/d5253b5fe7d407885350ce8d64b63d23.png)

## 二、创建Skill

点击上方的api文档

![](https://relay-1.bijitongbu.site/p/fe3b3aaa4790c51a961f2d6b8d75df2e.png)

点击图像系列下面的GPT-Image-2 图像生成，点击复制

![](https://relay-1.bijitongbu.site/p/aef039ef5e735c5687472e3e42476b82.png)

打开Trae Solo,切换到Coding模式，trae solo的使用可以看看这个

[手把手带你玩转 Trae Solo，零基础也能懂](https://mp.weixin.qq.com/s?__biz=MzIyMzk1OTIxNQ==&mid=2247486195&idx=1&sn=272a71edc47cb2d337515232612900d9&scene=21#wechat_redirect)

![](https://relay-1.bijitongbu.site/p/f0e5047c254c34ef581d19c7f3b2c4f3.png)

在对话框里，先粘贴刚才的内容，在输入

```
帮我根据上面的信息制作成一个图片生成的 skill，API 为 ：xxx；创建好了，别忘记进行测试。
```

![](https://relay-1.bijitongbu.site/p/221e0bb4ff9af748d5d3e7f986d7a0d4.png)

开始执行

![](https://relay-1.bijitongbu.site/p/e442528d172da9aff5ad49dd4febe3f9.png)

允许执行，点击添加 'pip' 到白名单，这样不用每次都点运行

![](https://relay-1.bijitongbu.site/p/d6b59cac57e2dd08be09ab003563837d.png)

完成

![](https://relay-1.bijitongbu.site/p/4c19766248b0aeef3f6ef5d938eeae7c.png)

看一下，它测试生成的图片

![](https://relay-1.bijitongbu.site/p/8a75b6178a24e97719591168f50869a5.png)

查看是否调用了api key 看到刚才创建的api 已经消耗了$0.012

![](https://relay-1.bijitongbu.site/p/594e7f3f9b7207954043e4d5f1f73751.png)

看了一下，它这个是创建了python库，不是skill技能，我继续让它创建一个，同时把模型也换成GLM-5

![](https://relay-1.bijitongbu.site/p/c18470e805037cad73a103e1f318b4af.png)

这次它生成了skill

![](https://relay-1.bijitongbu.site/p/637a09139244378b220a9ab7ae2684f7.png)

让它安装

![](https://relay-1.bijitongbu.site/p/d50ddbe8966fab385d0dca61668a560b.png)

由于它只能在我们给的目录执行，无法操作其他目录，只能自己安装了

![](https://relay-1.bijitongbu.site/p/387ff51672e04668883b7c3045b25661.png)

拷贝完后，让它重新加载skill

![](https://relay-1.bijitongbu.site/p/098c45d22fb6e16985c07b7d35b5a547.png)

手动测试一下,先按/键选择我们刚才创建的skill,在输入

```
帮我创建一张这个skill的功能介绍海报图，2k
```

![](https://relay-1.bijitongbu.site/p/eb43cb7db29962d9934711ef2070e039.png)

![](https://relay-1.bijitongbu.site/p/9c24ab46f55efde49c3c8a0f753bf30b.png)

这次生成了图片

![](https://relay-1.bijitongbu.site/p/497d25f532822223f62a56684f92e84f.png)

## 三、使用案例

由于现在的信息太多，以前我都会用元宝，帮我提炼文章主题和内容框架。看元宝给的简短总结，要是觉得有意思，我再通篇仔细读完整篇文章。现在可以换了个方式，直接用图片来代替文字总结。一眼就能看懂文章核心亮点，特别直观。

比如我把这篇文章的链接https://mp.weixin.qq.com/s/Mhd1s-rbSWiQVR054lVw6Q，粘贴告诉它生成图片，2k

![](https://relay-1.bijitongbu.site/p/90eac7daa7a4e21fb739c3274fc41453.png)

开始使用技能和联网读取文章

![](https://relay-1.bijitongbu.site/p/08b4bfe3d6c17312f3c51a3249267cdc.png)

执行生成图片

![](https://relay-1.bijitongbu.site/p/7e0fd3cde3d0c9078b5b974b5a8d359c.png)

我看了一下生成的图片，它总结了文章的主题，并按照工作流给出了操作步骤

![](https://relay-1.bijitongbu.site/p/810aa35e7cda4074602d7253d5050e0a.png)

## 四、总结

![](https://relay-1.bijitongbu.site/p/ea0bd5301203ab749ef9c67d573ed5ad.png)

上面我演示的都是单张图，其实这个skill最大的优点是批量生成相关图片，如信息图、手绘风格图、小红书卡片等，剩下的就需要你自己去操作了。

说说花费吧，我实际用下来，单张图也就几分到一毛左右。做一组六七张的小红书配图，总成本还不到一块钱。比起开各类会员划算太多，画面风格还能自己随心把控。

最后你可以用你自己的图片平台，根据这个平台的API文档，用Claude Code、Codex、任意一个支持Skill技能的AI工具去创建你自己的图片生成agent。祝大家玩得愉快！

好了，今天就跟大家分享到这儿，觉得内容有用的话，别忘了点个赞、收藏再转发一下。大家有什么不懂的，或者想要什么新内容，都可以在评论区给我留言。咱们下期再见！

---

![cover_image](https://mmbiz.qpic.cn/mmbiz_jpg/hkJddwtz6EriaEQwDia2xib2ZiaiaHTZKVDiaAmyu2CTCOmYibHH4icanyyUPBpibFGicMeZZGvtMKs2aBKecpQhrjK67gbhwukcCy0TvycjvBQYJwXibw/0?wx_fmt=jpeg)

Original 海鱼星的荷花塘 海鱼星的荷花塘

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/b6b56c0e_1779238997526?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzIyMzk1OTIxNQ%3D%3D%26mid%3D2247486231%26idx%3D1%26sn%3Dd87c8f30a3b38ecf09973c5d8cf31c97%26chksm%3De9bf60f521bd03823cf2c01a274ce523b4083382b0e12e39605547d4259b4c04651af598477e%26mpshare%3D1%26scene%3D1%26srcid%3D0520JVvBZmUssdCXuOFZbhKR%26sharer_shareinfo%3D295818cca40d83011e28cbfbdf57adc1%26sharer_shareinfo_first%3D295818cca40d83011e28cbfbdf57adc1%23rd&s=obsidian)