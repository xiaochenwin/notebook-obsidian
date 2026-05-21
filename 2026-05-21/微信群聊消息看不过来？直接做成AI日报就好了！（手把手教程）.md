---
author: Simonlin
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU1MDk3MzEwOA==&mid=2247486675&idx=1&sn=63d3f3cf0af7d0944a7e89d05eafe609&chksm=fa626f677686e546dbfe88b80e56f2f2dcab85a53905bbf03a776bda5891d39d97a2f5b1da3a&mpshare=1&scene=1&srcid=05213NrqvvPCQlh7KVmZKrk6&sharer_shareinfo=cbb965bbfd60afa895c02a7e384b25de&sharer_shareinfo_first=cbb965bbfd60afa895c02a7e384b25de#rd
saved: 2026-05-21 08:54:26
tags:
  - 笔记同步助手
id: 87a118a6-c056-4728-ae02-caaaefa96284
---

公众号名称：Simonlin的精神世界

作者名称：Simonlin

发布时间：2026-01-07 18:39

Hello啊朋友们，我是你们的朋友Simonlin，专注小白的AI教程，用简单易懂的语言，带你搞懂AI这回事儿～～～

认识我的朋友，肯定都知道，我去年出过一个微信群聊日报的教程：

https://mp.weixin.qq.com/s/kZkWgw8e38PjkiXWXSLk0Q

透过那个教程，我结识了很多朋友，也间接帮助了很多人摆脱了信息焦虑的困扰。

每个人的手机里，应该都有一个工作群/学习交流群/课程讨论群，信息密度高，内容很丰富，干货也很多，但是却遍布着各种各样的“噪音”，例如发表情包、开玩笑、各种无效讨论。

这就意味着，每次你想寻找有效的信息，就得爬楼，用人力的方式来过滤掉那些没有价值的讨论。

现在，你完全不用这么做！

因为在AI时代，我们可以让AI来做这个事情。

让AI把每天的群聊消息进行汇总，以日报的方式呈现出来，清晰直观，方便阅读，我们一眼就能找到重点在哪里！

直接看效果：

![](https://relay-1.bijitongbu.site/p/961b093ec71163ffc35f3c02970fdb20.png)

怎么做？

非常的简单，跟着节奏走，小白看完也能轻松上手！

  

## 一、聊天记录提取

  

其实很多时候，难的不是在于信息的整合，而是我们压根就不知道该在哪里获取我们的聊天记录。

虽然电脑端的微信，聊天记录是保存在本地的，但它经过了强加密，只能在微信软件中才允许被读取。

如果我们想要获取到平常我们看到的那种聊天记录，比如某某某什么时候说了啥，发了什么消息，这样的文件格式，就需要专门的软件来进行导出了。

之前我介绍过一个工具，叫做MemoTrace（留痕），但是已经停止更新，可用的版本现在已经不适用于4开头的微信版本了。

最近我又发现了一个好东西，能够对本地的微信聊天记录进行解密，支持将其导出为JSON、Html、Excel、Postgre SQL这四种文件格式，而且，支持最新版本的微信！

  

### 1、前置：工具准备

  

它的名字叫做EchoTrace（时光留痕），一款完全本地的微信聊天记录导出工具，还能对聊天记录进行分析，生成年度报告，项目是完全开源的，使用了最为宽松的MIT协议，大家可以放心使用～

聊天记录导出一共要用到两个工具，如果大家觉得一个个下载太麻烦，我已经打包放到网盘里，划到文章最下方，获取下载方式。

![](https://relay-1.bijitongbu.site/p/5517ab62dd818b86bddda878d68b1235.png)

项目地址：https://github.com/ycccccccy/echotrace

大家觉得好用的话，可以在右上角，给他们加星。

![](https://relay-1.bijitongbu.site/p/9daa8c6a4066828ec408cd3768efd5a7.png)

这款软件，目前只有Windows操作系统的版本，Mac系统暂不支持。如果大家发现了有Mac系统能用上的工具，欢迎在评论区留言分享～

Windows系统版本要求在Win10及以上，不确定Win10以下系统是否可用。

微信版本没有要求。

下载链接：https://github.com/ycccccccy/echotrace/releases/tag/v3.0.6

让我们先把工具给下好。

下好之后，你会得到这样一个压缩包文件：

![](https://relay-1.bijitongbu.site/p/898efacc04343e7ff2e60fd69c062422.png)

请注意，压缩包下在哪里都不重要，但是解压的时候一定得注意，解压的目录名称不能包含中文。

![](https://relay-1.bijitongbu.site/p/1c43423abb1e91c8ee9e430b7ca6b151.png)

仅供参考

如果你解压完成，发现exe文件打不开，看一下自己的文件路径，是不是解压到了目录名称带中文的文件夹里。

或者是被杀毒软件误杀了。

![](https://relay-1.bijitongbu.site/p/874a9b323da53b77a02dfdbd9515f03f.png)

进入Windows安全中心，看看有没有被系统误判为病毒。

![](https://relay-1.bijitongbu.site/p/7f64d078e483cb3d760d9b65214a717e.png)

![](https://relay-1.bijitongbu.site/p/d3b9f3b4f3502ee713b807261ee12baa.png)

如有，直接恢复就好了。

![](https://relay-1.bijitongbu.site/p/5fd7b8a41e3304b32e5fbcc8cfc05522.png)

同时，我们还要再下载一个工具，获取我们的聊天数据密钥，方便进行解密。

下载地址：https://github.com/ycccccccy/wx\_key/releases

同样解压到EchoTrace所在的同一个文件夹里。

![](https://relay-1.bijitongbu.site/p/0f400923f3041b653f7314d4ff030f5c.png)

  

### 2、导出记录

  

首先我们要先获取数据库密钥。

点击这个文件夹：

​

![](https://relay-1.bijitongbu.site/p/c387bd5a92f2dc9f1c50a33601b43385.png)

找到里面的exe文件，双击打开：

![](https://relay-1.bijitongbu.site/p/eb36345725d3b4b5e0c1d8bac9ead0d9.png)

先设置一下微信文件的目录，如果没设置，它会自动检测。

![](https://relay-1.bijitongbu.site/p/e9e25d2e85c7fd6c30742650650d7dd0.png)

点击“开始提取密钥”——“关闭并继续”。

![](https://relay-1.bijitongbu.site/p/d2a1455a20f1538acb050874ff507532.png)

![](https://relay-1.bijitongbu.site/p/889bf6656eca875a1a10c1c729be6d2c.png)

重新登录一下微信，密钥提取完毕。

点击“复制”。

![](https://relay-1.bijitongbu.site/p/881ebc3bfcd7b46a3938c1e14ec07e28.png)

然后打开EchoTrace的文件夹。

![](https://relay-1.bijitongbu.site/p/8eedca0e531ae95b3b0d6a95ec33dc26.png)

找到exe文件，双击打开。

![](https://relay-1.bijitongbu.site/p/ce015242385122db820fe3d4cebdcd66.png)

进入到数据库配置的界面。

点击“测试连接”，看看能不能连通聊天记录的数据库。

![](https://relay-1.bijitongbu.site/p/79c0cbf9fbd2ec0cccde79d16c9cc892.png)

出现这个提示，就说明可以继续下一步操作。

![](https://relay-1.bijitongbu.site/p/3544622b511a80f82a5484f59c195f15.png)

点击“保存配置”。

![](https://relay-1.bijitongbu.site/p/b7fb6d300b9ad3e6f78cca0eba97fadc.png)

获取到数据库文件不代表它马上就能用，得先进行解密。

左边侧栏，找到最下方的“数据管理”。

点击“批量解密”。

![](https://relay-1.bijitongbu.site/p/fb068f9879bca0cec56034961d19859b.png)

需要注意的是，我们这边解密的是数据库文件，如果要对图片这种媒体文件进行处理，得另外获取图片密钥，否则就会显示这个：

![](https://relay-1.bijitongbu.site/p/4a498f5d7e96f7e0bb00a9f72d71a6ab.png)

办法就是到密钥获取工具，点“获取图片密钥”。

![](https://relay-1.bijitongbu.site/p/5a551f989652cea0e5d4b72433420f52.png)

接下来，就是最最最激动人心的时刻了，我们要导出群聊数据了！

一共有5个步骤，大家按照这个图片里标注的，一步步来。

![](https://relay-1.bijitongbu.site/p/8ed57e465689a5728c143e6085cdfc98.png)

第一步：选择聊天记录文件的存储位置，我是专门建了个文件夹，把软件和数据都放在了里面，方便查找。

第二步：选择要导出记录的群聊，可以是单个群聊，也可以批量导出。

![](https://relay-1.bijitongbu.site/p/d8bb4cf264856a203cc7c86f33868baf.png)

第三步：选择时间范围，时间范围越大，聊天记录文件越大，到后面日报制作的时候花的时间就越长。

第四步：选择文件格式，支持JSON（结构化）、HTML（网页）、Excel（表格）、PostgreSQL（数据库）这四种，如果自己阅读的话，选HTML是最直观的，如果要发给AI，那Json最方便，我一般是选择Json格式。

如果要导出媒体文件，得先获取图片密钥，并进行解密，否则会失败。

![](https://relay-1.bijitongbu.site/p/35ca9d786495356d5cd6aca48df39372.png)

也可以选择是否要导出头像，指的是微信聊天里，聊天发送者的头像。

![](https://relay-1.bijitongbu.site/p/ff7170dc191a7f51e834611fd9f2f4c4.png)

做好这些准备之后，就点击“开始处理”。

![](https://relay-1.bijitongbu.site/p/70e878bff9ae58db2d3f3f9448ac9b52.png)

![](https://relay-1.bijitongbu.site/p/60eadb91bc301541fb2247981adf8d5f.png)

等待一段时间。

到这里，聊天记录提取的工作就大功告成了！

先别着急退出去，如果你忘了你聊天记录存放的路径，点“浏览文件”直接跳转，是最方便的。

![](https://relay-1.bijitongbu.site/p/2bd50b9dd313ec285963a8698167a3f0.png)

现在，最重要的聊天记录文件，我们已经拿到了。

![](https://relay-1.bijitongbu.site/p/c047377e150c54d498cd4e6181269f8f.png)

  

## 二、制作日报

  

接下来，就是找个AI来制作日报了。

![](https://relay-1.bijitongbu.site/p/c9882f50eb69f56ed4c6c4daf86f605e.png)

到了2026年，各家主流模型在上下文长度方面有了不小的突破，我让AI帮忙列出了一份表格，大家可以对照一下。

我们只需要注意一点：先选择上下文长的模型，再从里面挑选性能好的模型。

这边同样有一份表格， 供大家参考：

![](https://relay-1.bijitongbu.site/p/b107acadfad1def75437f0ed98049547.png)

我这里选择的依旧是老朋友——Gemini，最新的模型为Gemini 3 Pro，不仅承袭了一贯的长上下文，编程能力也非常的强大，属于顶尖队列。（其他AI也行，不一定要Gemini的，只要是长上下文，性能好的模型都可以）

如果你有API的，直接使用API就好，如果没有API，小黄鱼（二手交易软件）搜索“Gemini会员”，可以用很低的价格购买一年的Pro会员，原价买的话要199美元，相当于1397人民币。

![](https://relay-1.bijitongbu.site/p/dd5a6de8a051f6f26af6479d45dade8d.png)

假设大家已经有了Gemini会员。

先上传Json格式的聊天记录文件。

![](https://relay-1.bijitongbu.site/p/806ae9273db6cb6ded675270e649b91e.png)

提示词，我会将它和所有工具一起打包发给你，划到文章最底下就能看到了。

复制粘贴提示词，点“提交”。

![](https://relay-1.bijitongbu.site/p/fc1f30d1911e7bf6c5b0e3656e93738e.png)

![](https://relay-1.bijitongbu.site/p/32792b9ab6dd19bbb265a3a042609150.png)

将AI生成的代码复制一下。

![](https://relay-1.bijitongbu.site/p/ec1c342e9a5045115f5a44e471268c31.png)

回到桌面，新建一个txt文件。

![](https://relay-1.bijitongbu.site/p/6768806251d90c589be88af91dcf09ce.png)

双击打开。

![](https://relay-1.bijitongbu.site/p/61a0d1e2a94e4125bb5f8de13fa7c912.png)

将代码粘贴进去，保存一下再关闭。

![](https://relay-1.bijitongbu.site/p/42b37d0569138d152ee9432bfc5bdb6f.png)

右键单击文件，点击“重命名”，将文件后缀修改为“.html”。

![](https://relay-1.bijitongbu.site/p/72586a39c922de16c9a2a343a41a1eef.png)

![](https://relay-1.bijitongbu.site/p/3570d7f83105c233159ed2dbe95fda50.png)

这个时候，你会发现，原先的文档图标已经变成了网页的样式。

![](https://relay-1.bijitongbu.site/p/85068ded0315d5130baefebab6c929bc.png)

双击打开，然后就能看到可视化的群聊日报了。

![](https://relay-1.bijitongbu.site/p/332b1fd22eca9da27601e899918bd4d2.png)

如果文件后缀修改了还是没用，在电脑的文件夹里完成一个操作。

![](https://relay-1.bijitongbu.site/p/28599627c0fe7765193ce8143ceeb66d.png)

以C盘为例，进入到“选项”界面，把“隐藏已知文件类型的扩展名”给它取消选中，然后点“应用”，就可以正常修改后缀了。

![](https://relay-1.bijitongbu.site/p/ab10bd745862a12cbfcd0b56c102717e.png)

接下来，我们有两个方案可以选择。

第一个，是进入这个网站：https://cloudconvert.com/html-to-png

对HTML格式的日报文件直接进行转换。

![](https://relay-1.bijitongbu.site/p/374ccf27a27eebb140cf44ffe9f10fa9.png)

转换完成，直接下载就好了。

![](https://relay-1.bijitongbu.site/p/75ea06e6140a21cabe0a6b4edb59eda8.png)

还有一种，就是用飞书自带的滚动截图。

随便找到一位飞书好友，进入到聊天窗口。

![](https://relay-1.bijitongbu.site/p/26c657e030c40cdf1ef9ebe933b0b176.png)

也能把日报完整地截图下来。

至此，一份面向小白的微信群聊日报教程就告一段落了。

如果你觉得这份提示词给的外观样式不好看，可以把它发送给AI，让AI来进行修改。

你可以告诉AI：

🐵

这是一份微信群聊日报的提示词，对其中网页的外观样式进行修改，我要科技未来风，其余的指令不要变动。

日报所需要的提示词，工具等等，我会放到网盘里，划到文章最下方，获取下载方式。

  

## 三、进阶操作

  

Claude Code（CC）是Anthropic推出的一款命令行AI编程工具，从2025年2月发布开始，就受到了大众的好评。

因为它具有很强的可扩展性，丰富的可玩性，所以备受推崇。

而Skills，就相当于是它的“补丁”，只要安装了Skills，Claude Code就不再是一个编程助手，甚至会成为最懂你的那个AI搭子。

比如，作为团队协作来说，最害怕的就是AI到处乱改，后期维护实在是麻烦。

将团队开发的规范，制作成Skills，Claude Code在进行开发任务的时候，自动调用，它就会严格的按照里面的要求进行开发，生产出易于维护，格式规范的代码。

那如果你是自媒体创作者，你也可以将自己的文章投喂给CC之后，让它做一个Skills，再让它来写文章的时候，它就根据你写文章的特色，来进行创作，效率直接拉满。

因此我们可以得知，Skills是一个可复用的，自动化的工具。

我也做了一个日报的Skills，这样，只要我提供聊天记录文件，然后对它说：“帮我制作一份群聊日报”，不用输入提示词，它就能自动制作日报了。

![](https://relay-1.bijitongbu.site/p/a95e17a75c8170b95ff13199e5770ad5.png)

日报的Skills，连同EchoTrace软件和提示词一起放在网盘里，欢迎大家使用～

如果你想试试看Claude Code，冷逸老师写了篇非常详细的教程，大家照着一步步来，就能完成Claude Code的安装。

文章地址：https://mp.weixin.qq.com/s/0jDta0p\_Ol1XJ3pGHEGRrA

关于Claude Code的Skills，如何安装，一泽老师也写的非常清楚了：

文章地址：https://mp.weixin.qq.com/s/jUylk813LYbKw0sLiIttTQ

提示词、工具、Skills打包获取方式：

后台私信我，发送关键词：“日报工具”，获取下载链接。

  

## 结语

  

这篇文章写了一个下午，从艳阳高照，写到了灯火阑珊。

按理来说，我是应该说点什么的。

因为日报对我真的非常非常重要，它给我带来的价值是不可估量的。

我原本以为，MemoTrace没法使用了，日报就废掉了。

但是还是有很多人一直在努力着，用自己的方式，想要从无尽的信息洪流中拨开一篇净土。

真心向他们表示感谢，对他们，我要给予我最大的敬意。

也很感恩有一些朋友一直在支持着我，问我日报什么时候再更新，给我加油打气。

人争一口气。正是这一口“气”，一直鼓舞着我。

所以，事，就这么成了。

  

---

  

如果你能因此有所收获，我很开心，并为我能够帮到你感到荣幸。

欢迎点赞、转发、分享给你的朋友，将他从信息洪流里拉出来。

我创建了一个AI交流群，这个群里都是正在探索AI的，志同道合的好伙伴，有AI，也有爱。

想要进群的话，请移步到我的公众号后台，私信发送​“进群”​，和朋友们一起聊AI。

我是Simonlin，下次见。

  

---

原创 Simonlin Simonlin的精神世界

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/b92a4bc7_1779324865129?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU1MDk3MzEwOA%3D%3D%26mid%3D2247486675%26idx%3D1%26sn%3D63d3f3cf0af7d0944a7e89d05eafe609%26chksm%3Dfa626f677686e546dbfe88b80e56f2f2dcab85a53905bbf03a776bda5891d39d97a2f5b1da3a%26mpshare%3D1%26scene%3D1%26srcid%3D05213NrqvvPCQlh7KVmZKrk6%26sharer_shareinfo%3Dcbb965bbfd60afa895c02a7e384b25de%26sharer_shareinfo_first%3Dcbb965bbfd60afa895c02a7e384b25de%23rd&s=obsidian)