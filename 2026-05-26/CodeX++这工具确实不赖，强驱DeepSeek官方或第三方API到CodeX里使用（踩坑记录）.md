---
author: 52txr
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247523191&idx=1&sn=85b27c7ed5e35efa4ae378963b983383&chksm=ff6c5c33459c9c76787b9b61a40d3138eaec42efe66a7287200e0d133abef6efa55b0a33fb95&mpshare=1&scene=1&srcid=0526jZCGuuz6KhwNqGzNLGe7&sharer_shareinfo=debf82ef386151e35743f12d3eb41835&sharer_shareinfo_first=debf82ef386151e35743f12d3eb41835#rd
saved: 2026-05-26 07:47:13
tags:
  - 笔记同步助手
id: 2934c77d-f9b6-44b1-ad20-1306c28ffa6f
---

公众号名称：陶小桃Blog

作者名称：52txr

发布时间：2026-05-23 13:49

点击名片，关注我吧！

---

AI摘要：本文记录了作者在Windows环境下，通过第三方插件CodeX++将AI编码助手CodeX与DeepSeek API对接的完整过程。​由于CodeX原生采用OpenAI的Responses API协议，与DeepSeek的Chat Completions API不兼容，直接调用会失败。​作者详细介绍了CodeX的安装、绕过官方登录、CodeX++插件的配置步骤，包括添加供应商、设置DeepSeek密钥、选择正确的Chat Completions模式等。​文章还分享了使用中的踩坑经验，如网络代理的必要性、模型不显示、502/404错误等问题的解决方法。​最后展示了实际使用效果与成本，并表达了将大模型作为“外脑”与杠杆，提升个人开发效率的理念。

关键词：CodeX；DeepSeek；CodeX++；API对接；Responses API；Chat Completions API；AI编程助手；网络代理；大模型应用；开发效率

---

作为一个三流写代码的机械打螺丝专业的，没事就喜欢在V2EX里发表个拙见让大佬们“锤”，在他们“锤”的过程中，我就能快速吸收到有用的信息，这也是我蒸馏别人的一种方式吧。在此之前，我确实觉得TRAE是最好的（毕竟对着Cursor借鉴的），而且开放了自定义Base URL，算是很友好了。虽然我承认TRAE是境内最好用的，但是远不够我的野心。也还是非常赶时髦，一定要用最先进但是最划算的买卖。

![[笔记同步助手/images/e0d581ed01a3826980893859e82ac1be_MD5.png]]

## 大模型时代的思考

我曾经也因为AI发展感到焦虑（[读博随笔 | 在读男博士深夜的两声叹息：金钱焦虑和Ai恐惧](https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247521428&idx=1&sn=0bcc3af5533b2a7fe04efaed203fa43c&scene=21#wechat_redirect)），但现在已经逐渐融入进去，把技术为我所用。在大模型时代，面对技术冲击带来的未知，大可不必想太多。技术革新是历史的常态，每一次都在重塑生产力体系。对于大多数人而言，正确的态度是将大模型视为“外脑”与杠杆，用它来抹平信息差并大幅提升效率。真正决定一个人抗风险与生存能力的，从来不是对某项特定工具或固定流程的熟练度，而是个人的“基座能力”，也就是“道”，或者用仙逆里的动漫来说就是对意境的感悟，包括底层逻辑的构建、快速学习的能力、思考的习惯以及应对挫折的韧性。大模型极为擅长处理标准化和重复性的信息整合，从某些角度来说，旧知识已经不值钱了，只要想知道就一定可以知道。而我更擅长把大模型作为快速切入新领域的知识库和助手。

## 使用环境

-   • Win10 64位，Win11应该也没问题
    
-   • CodeX版本：最新版（2026.05.23），版本号26.519.5221.0
    
-   • CodeX++版本：**v1.1.7**，项目地址 CodexPlusPlus\[1\]
    

![[笔记同步助手/images/de2a72e770ecaa8340dec8037ae8ed65_MD5.png]]

CodeX++项目地址

## 安装CodeX

CodeX的下载国内的网络是没有ban的，直接下载就行了：Codex | OpenAI 打造的 AI 编码助手\[2\]

![[笔记同步助手/images/b7f1ee483b5736007ff22ff1cd596c3f_MD5.png]]

安装完会弹出下面的进入方式，考虑到国内很多人其实是没有ChatGPT账号的，可以选择其他登录方式，选择API登录，然后随便输入一个即可，例如`sk-xxxxxxxxxxxx`，无所谓的，因为我们实际也不用OpenAI官方的API，我们用DeepSeek。

![[笔记同步助手/images/5fce2e3c08f0d457cfea1e8757c45319_MD5.png]]

蒙混过关之后，就可以进入CodeX了：

![[笔记同步助手/images/fcf9bc9dd4732a2e59fa017da526c232_MD5.png]]

如果打开一直是logo界面，可能需要点技术，因为我发现点开之后会产生到chatgpt官网的链接请求。

![[笔记同步助手/images/fcf9bc9dd4732a2e59fa017da526c232_MD5.png]]

我是建议一直开着代理，不然很有可能打不开软件，卡着codex的logo闪烁进不去！！

## 安装及配置CodeX++

目前看到的版本是1.1.7版本。下载了exe按照正常软件进行安装即可。安装完成后将在桌面出现下面两个图标：

![[笔记同步助手/images/6bacb32193a5d4698e3466df5bb8d464_MD5.png]]

打开“Codex++管理工具”，添加供应商配置：

![[笔记同步助手/images/35adce0679bc80f86ad858ed0d33526f_MD5.png]]

然后配置DeepSeek的密钥。一定要选Chat Completions。因为CodeX官方接口是不支持DeepSeek的。**两者无法直接对接**，根本原因是接口协议 不一致：

| 项目 | Codex（v0.81.0 及以上） | DeepSeek API |
| --- | --- | --- |
| 协议 | **Responses API** | **Chat Completions API** |
| 请求路径 | /v1/responses | /v1/chat/completions |
| 工具调用 | tools 字段内联 | tool\_calls 独立消息 |

![[笔记同步助手/images/4121cd453ea54fb9dc8005bc0876a629_MD5.png]]

配置完成后一定要点击在使用中。配置完成后点击重启CodeX即可。

![[笔记同步助手/images/8c090d8aa9b869ef0aa9605b75ef90d1_MD5.png]]

  

## 使用CodeX

重启后应该就可以看到CodeX右上方有绿灯的CodeX++，然后插件显示已解锁。然后模型选择里有DeepSeek的flash模型和pro模型。

![[笔记同步助手/images/9807d0bab5c408c528e59303c3445c5a_MD5.png]]

可以把**Codex Context Used Meter**安装上，在 Codex App 对话界面顶部显示当前会话剩余上下文、已用/总 token，并提供轻量进度条和消耗动画。

![[笔记同步助手/images/e101e6d6d7d82271b0a5a6b724a06358_MD5.png]]

效果就会下面的样子：

![[笔记同步助手/images/994d7561ce03ea82106c58c8fc1db4fb_MD5.png]]

这个月各种测试和折腾，已经含泪消费2.4元的DeepSeek了：

![[笔记同步助手/images/88d9fb2f2e400ea1dedf14bbc27a6bfe_MD5.png]]

目前我已经一句话做出来一个去除文件元数据的小网页，感觉以后我基本应该不用手搓前端的任何事了：

![[笔记同步助手/images/7737e94e027cfa617e36cbfa4ab1c24e_MD5.png]]

## 踩坑记录

下面的坑是我摸索了一两天才解决的，很离谱！

1、一定要开着网络代理，这样可以省很多事，包括但不限于舒服得从Github上下载下来CodeX++；

2、会遇到配置后找不到模型的情况；

![[笔记同步助手/images/ad7441b26c5f3bbc2b2b1c5e4c33960e_MD5.png]]

3、出现下面的问题：status 502 Bad Gateway: Unknown error, url: [http://127.0.0.1:57321/v1/responses](http://127.0.0.1:57321/v1/responses)

或者[https://api.deepseek.com/](https://api.deepseek.com/)，DeepSeek 服务器会返回 404

上面的情况基本都是因为网络代理软件没配置好，可以在代理绕过设置里面添加:

```
127.0.0.1;
localhost;
*.deepseek.com;
```

![[笔记同步助手/images/2778c38c417d0fb0d700758830323da4_MD5.png]]

#### 引用链接

`[1]` CodexPlusPlus: _https://github.com/BigPizzaV3/CodexPlusPlus_  
`[2]` Codex | OpenAI 打造的 AI 编码助手: _https://openai.com/zh-Hans-CN/codex/_

---

本期封面：

![[笔记同步助手/images/fc5a2cf4f58eaebbf88bba87aa996be0_MD5.png]]

往期阅读：

[Zotero同步空间不足？不如放弃存储论文pdf，一个原创脚本清理全部的pdf附件](https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247523155&idx=1&sn=4e0eedd12385d07942ba3bdc98ef680c&scene=21#wechat_redirect)

[华强北版斯坦福个人学术主页重构开源，中英双语同步发布，增加后台管理系统（PHP+SQLite）](https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247523124&idx=1&sn=2a27e3575d09db3836d8b1ea5e490e18&scene=21#wechat_redirect)

[一只赛博果蝇引发我的世界观重塑，但想通后觉得世界是真是假并不重要](https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247523146&idx=1&sn=efa60eb7826ce6740cc6268f5c5131a7&scene=21#wechat_redirect)

[当我听到愤世嫉俗的键盘声，一定是某个研究生在对AI疯狂输出或dis](https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247522896&idx=1&sn=918974c3d8388a0a67bb33be1e40e2bf&scene=21#wechat_redirect)

[燃烧碳烟颗粒级表征软件V1.0发布，多国语言、自动批量精准分割、自动统计等效直径、回转直径…](https://mp.weixin.qq.com/s?__biz=MzU5NDgwNDY1MA==&mid=2247523074&idx=1&sn=18b2146d2ebe546cf6a7f58c78cf40cf&scene=21#wechat_redirect)

---

![[笔记同步助手/images/3c1d4b3c33f15a1ca447c57b48e06e74_MD5.jpg|cover_image]]

Original 52txr 陶小桃Blog

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/65f75e39_1779752831369?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU5NDgwNDY1MA%3D%3D%26mid%3D2247523191%26idx%3D1%26sn%3D85b27c7ed5e35efa4ae378963b983383%26chksm%3Dff6c5c33459c9c76787b9b61a40d3138eaec42efe66a7287200e0d133abef6efa55b0a33fb95%26mpshare%3D1%26scene%3D1%26srcid%3D0526jZCGuuz6KhwNqGzNLGe7%26sharer_shareinfo%3Ddebf82ef386151e35743f12d3eb41835%26sharer_shareinfo_first%3Ddebf82ef386151e35743f12d3eb41835%23rd&s=obsidian)