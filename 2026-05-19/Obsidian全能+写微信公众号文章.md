---
author: 理查德攻城狮
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzE5MTU2NTM1Mg==&mid=2247483848&idx=1&sn=aee93ce19ae6d7727ff39748312b5538&chksm=97efa797dba94c2847ee626f646aadfcc6bd4612cad6f0e41cf8d5d7be0bfef44d1689a92a88&mpshare=1&scene=1&srcid=0519n8pbbaSvE5NPC9Dl5TkX&sharer_shareinfo=5cc7a382bb0df6c2ac7dd0da1dce0354&sharer_shareinfo_first=5cc7a382bb0df6c2ac7dd0da1dce0354#rd
saved: 2026-05-19 08:46:43
tags:
  - 笔记同步助手
id: 62616ffb-9c20-47c8-94b2-6e143ddb23ba
---

公众号名称：奇点代码

作者名称：理查德攻城狮

发布时间：2026-04-16 22:50

> 这篇介绍一下，使用OB写微信公众号文章。

**划重点**

-   底层原理：通过ob的笔记属性（就是文章最上面的那些可配置的属性值），让插件（Obsidian2WeChat）可以识别并转换为微信公众号草稿的API数据，将文章发表至微信公众号的草稿箱，然后使用电脑或者手机里的”公众号助手“直接发表文章。
    

  

## 一、书写文章

个人喜欢用模板，所以把插件所需要的笔记属性，配置好模板，全新创建一篇空白文章，然后插入模板就可以直接开始写了。 我的模板配置如下：（当然也可以在文章最上面手工添加属性（title,author,digest,cover,open\_comment）这几个属性添加好。

![[笔记同步助手/images/c953bae8d34673efad6380d01b4001a7_MD5.png]]

 然后在正文中开始写文章。 文章中的截图可以直接将本地文件拖进左边笔记列表中，然后再在列表中拖入文章中，自动生成链接的。（注意，先拖入文件列表，再从文件列表拖入文章中）

![[笔记同步助手/images/5d89dc10d70fdb94dfdc42da72cc7577_MD5.png]]

## 二、配置插件

先安装微信发布公众号的插件（Obsidian2WeChat）

在公众号后台获取AppID和AppSecret，在插件中配置AppID和AppSecret。

![[笔记同步助手/images/fc6ca0e53845bed9cd1bef416697d8b7_MD5.png]]

将服务器IP添加至公众号IP白名单 查看本地IP（https://ip.cn，或者https://ip138.com打开网页就会显示IP地址），将IP地址配置到微信公众号后台 的IP白名单（设置与开发->安全中心->IP白名单)

![[笔记同步助手/images/be5c4a42555a4a9ad33216c4359db625_MD5.png]]

在Obsidian中打开要写好的文章

使用命令面板运行”发布到微信公众号“ 使用左边工具按钮（发布到微信公众号），或者ctrl+p打开命令输入“发布到微信公众号

选择这主题，点击发布到草稿箱。 在这里可以选择主题。

![[笔记同步助手/images/5e005152f214d7e941d364b11e1a22c1_MD5.png]]

![[笔记同步助手/images/fee2e06fac52121a5fe5e903c75938b6_MD5.png]]

## 三、发表文章

在插件中发布，只是发布到草稿箱，要最后发布，还要网页登录，或者手机”公众号助手“中，在草稿箱中，选择编辑文章和发布。

![[笔记同步助手/images/8a4ce4aa69e70485d35e02e845ee6e55_MD5.png]]

## 四、插图问题

在电脑端打开草稿发现，原来笔记中的插图没有上传上来，因为插件要直接将本地文件中的图片通过接口上传到公众号后台通常要给插件充会员（技术原因是插件把图片上传至图床，然后再把图床地址附上去）。

用常规的办法就是，在微信公众号后台编辑文章->图片->从本地文件或者在图片库中选择，将刚才文章缺少的图片，再传一下插入到文章中。

这样就可以直接发布文章了。

## 五、总结

使用OB笔记文章写公众号，最方便的就是纯文字的文章，可以快捷从OB中直接发布到公众号草稿箱，再使用手机“公众号助手”直接发布。

（有图片的文章，稍微麻烦些，还要单独上传图片，当然也可以自己配置个图床，在文章中直接使用图床URL）

---

![[笔记同步助手/images/80c1aaa8468f1a200ce25b62e2db6a44_MD5.jpg|cover_image]]

Original 理查德攻城狮 奇点代码

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/d7b68626_1779151602773?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzE5MTU2NTM1Mg%3D%3D%26mid%3D2247483848%26idx%3D1%26sn%3Daee93ce19ae6d7727ff39748312b5538%26chksm%3D97efa797dba94c2847ee626f646aadfcc6bd4612cad6f0e41cf8d5d7be0bfef44d1689a92a88%26mpshare%3D1%26scene%3D1%26srcid%3D0519n8pbbaSvE5NPC9Dl5TkX%26sharer_shareinfo%3D5cc7a382bb0df6c2ac7dd0da1dce0354%26sharer_shareinfo_first%3D5cc7a382bb0df6c2ac7dd0da1dce0354%23rd&s=obsidian)