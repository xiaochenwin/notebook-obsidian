---
author: 小二
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzE5ODA5OTY1MQ==&mid=2247483838&idx=1&sn=9b59af2d2166018fa2855bf6fe7d1c14&chksm=974fd7a7309721d55f0a8c1fa239a356dd13afc586b5f7f58c5d74c8f2670f44276f7230db0d&mpshare=1&scene=1&srcid=0521ALptPJifIKq0SyhB19Yj&sharer_shareinfo=58cac9747e7ab5d834075514fab50a0d&sharer_shareinfo_first=58cac9747e7ab5d834075514fab50a0d#rd
saved: 2026-05-21 08:53:00
tags:
  - 笔记同步助手
id: fc907c17-73f6-4606-b931-8bf9e5619a9f
---

公众号名称：微糖小二

作者名称：小二

发布时间：2026-04-27 06:45

小二准则【不为学习而学习，严格遵循**二八法则**】。

AI热潮下，Obsidian现在很火，都开始安装了Obsidian 这个本地知识库。

但是这个知识库，之所以火，不是简单的因为它的本地化编辑，支持远程同步，以及其知识图谱和丰富的插件。

而是，能够和AI完美组合。

相信，有不少人，安装Obsidian后，还在手搓文档笔记。当然，不是否定手搓的价值，而是需要知道Obsidian结合AI的能力，提升工作效率。

废话不多说，直接开始干活，边干边了解Obsidian怎么和AI结合，以及提效点。

在开始之前，要求已经安装好Obsidian和claude code cli，如果还没安装，可以参考小编前面一篇文章。

安装claudian插件

Claudian是Obsidian的第三方插件，支持在Obsidian里面使用claude code。

1\. 进入下载地址，https://github.com/YishenTu/claudian/releases

![[笔记同步助手/images/af367e087e6f786d132485937af49636_MD5.png]]

2\. 下载 main.js，manifest.json，styles.css三个文件。

打开Obsidian的知识库，就是创建的vault文件夹，进入.obsidian这个文件夹，注意，这个文件夹是点号前缀的，正常情况下是隐藏的。

如果是windows系统，打开指定文件夹，点击顶部的“查看”选项卡，在“显示/隐藏”区域勾选“隐藏的项目” 复选框，隐藏文件就会显示  

![[笔记同步助手/images/5c22b6a7f02edefd209ae43a4aa7975a_MD5.png]]

如果是mac，进入指定仓库文件夹后，组合按键Cmd+Shift+.就可以看到，如下

![[笔记同步助手/images/ed1f2147b3ba0248f9dbc0a46126fcd3_MD5.png]]

3\. 进入.obsidian这个文件夹，并创建claudian文件夹

把下载的main.js，manifest.json，styles.css三个文件复制到claudian文件夹中。

回到obsidian操作界面，在设置中找到第三方插件中的claudian，如果没有，就点击刷新按钮

![[笔记同步助手/images/98c2d4386d5f2c149ad7e4ea033ae80b_MD5.png]]

启用后，这里就已经完成安装，但是还不能使用claudian，缺一步配置。

如果已经安装claude code，打开终端命令执行器，执行which claude，找到claude code的安装目录

![[笔记同步助手/images/62898b871f53a7e0ebf4e7576f4a5a38_MD5.png]]

然后点开claudian插件设置

![[笔记同步助手/images/675b6648d3b63d36774b63a368e04061_MD5.png]]

在Claude CLI path这一选项中填入刚刚找到的路径

![[笔记同步助手/images/4f5c257b09e267ba3aee57a02b0cc085_MD5.png]]

注意，如果claude已经对接了国内的大模型，在environment这一栏不需要填写baseurl和api key

![[笔记同步助手/images/4ee8e7e9d8d88c1d0d5368c8684a9ca0_MD5.png]]

到这里，已经完成了claudian的安装，可以在有上角看到一个机器人的选择

![[笔记同步助手/images/bb339ca0530657359cdb5340073df533_MD5.png]]

安装好了之后，我们试一下效果，比如我想了解《金字塔原理》这本书的核心内容，让ai帮我写一份大纲文档，如图，AI已经开始工作。

![[笔记同步助手/images/896628af0ff15098b9d8628d2f129dfc_MD5.png]]

默默等待完成...，最终效果如下，已经完成一篇AI整理的文档

![[笔记同步助手/images/8d2900f68d3df442f211826f0078db36_MD5.png]]

AI已经完美集成到Obsidian知识库当中，写文档，整理文档，都是不错的工具。

最后，小二想说，AI只是工具，落在知识库的文档再多，如果不看，不思考，不沉淀，也只是一堆文字垃圾。

我是小二，一线互联网大厂架构师，在AI热潮下，专注AIGC摸索。

如果文章有帮助，帮忙点个赞，**关注**不迷路。

往期推荐

[AI时代怎么打造个人专属的知识库？Obsidian完美契合，5分钟教程完成本地搭建](https://mp.weixin.qq.com/s?__biz=MzE5ODA5OTY1MQ==&mid=2247483818&idx=1&sn=bf355dfd6074c0b7e031b5f64ba988fd&scene=21#wechat_redirect)

[阿里云部署OpenClaw使用百炼套餐太贵?15分钟接入智谱Coding Plan](https://mp.weixin.qq.com/s?__biz=MzE5ODA5OTY1MQ==&mid=2247483792&idx=1&sn=a8f8b26e7392ed192bc543be5bd4dd35&scene=21#wechat_redirect)

---

![[笔记同步助手/images/e4bc568e9f33b3d8e5fdce099df2cee9_MD5.jpg|cover_image]]

原创 小二 微糖小二

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/5a0f670d_1779324779395?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzE5ODA5OTY1MQ%3D%3D%26mid%3D2247483838%26idx%3D1%26sn%3D9b59af2d2166018fa2855bf6fe7d1c14%26chksm%3D974fd7a7309721d55f0a8c1fa239a356dd13afc586b5f7f58c5d74c8f2670f44276f7230db0d%26mpshare%3D1%26scene%3D1%26srcid%3D0521ALptPJifIKq0SyhB19Yj%26sharer_shareinfo%3D58cac9747e7ab5d834075514fab50a0d%26sharer_shareinfo_first%3D58cac9747e7ab5d834075514fab50a0d%23rd&s=obsidian)