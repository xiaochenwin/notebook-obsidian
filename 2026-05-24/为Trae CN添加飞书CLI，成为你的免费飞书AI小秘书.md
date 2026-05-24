---
author: 智用手册
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk2NDUxNDQ3Nw==&mid=2247484477&idx=1&sn=07e156c6155a76995c59465886c4c33b&chksm=c5111ada0dadbefc4b1150b856ccb838ab9e970677c11ddb10b7349f7fd15106f2ac61020a9e&mpshare=1&scene=1&srcid=0524SXyJAazQtKwNbr2qsox9&sharer_shareinfo=3b7e48d8e8dfe88e7a559d1b21ef4af2&sharer_shareinfo_first=3b7e48d8e8dfe88e7a559d1b21ef4af2#rd
saved: 2026-05-24 19:10:53
tags:
  - 笔记同步助手
id: 780bbefc-4be7-4c89-99e8-821fbf679838
---

公众号名称：百工AI实战手册

作者名称：智用手册

发布时间：2026-05-24 11:01

飞书CLI非常之强大，我之前一直在Hermes和Claude Code中使用。不过，除了这两个Agent，我平时还经常用Trae来完成一些工作，Trae的一些产出，比如设计文档、方案等，也需要同步到飞书上。之前我总是需要手动地去做这个事情。

今天忽然想到，飞书CLI是不是也可以装到Trae上，我也懒得自己去查了，直接问了Trae一句，结果就这样把飞书CLI给Trae装上了！

_Trae版本：Trae CN，版本: 3.3.60_

_模型：Deepseek-V4-flash_

​

## 安装过程

安装过程很简单；“问一个问题”，然后“安装”，“配置”，”继续“，就完成了。

### 一个问题

```
Trae可以使用lark-cli吗？github上的一个项目
```

Trae 就会自己去Github上查飞书CLI的说明，很快会反馈

```
...
...
### 安装后能做什么
安装配置完成后，你可以直接让 Trae 帮你操作飞书/Lark，比如：

- 创建和编辑云文档
- 发送和搜索消息
- 管理日历日程
- 操作多维表格
- 查询通讯录
- 管理任务待办
- ...等等 200+ 命令
需要我帮你安装 lark-cli 并进行配置吗？
```

### 安装

你只需要回复“安装”，Trae就是自己去运行整个安装过程了，包括检查运行环境是否已经安装了Node.js，安装skills等等

![[笔记同步助手/images/9b56b1aa56d5c13b5b39efc9a1b91ecf_MD5.png]]

这里有一个地方需要注意，在Trae运行到下面的命令的时候

```
npx skills add larksuite/cli -y -g
```

可能会停在那里等待在终端中输入 “y"，这个时候你点击一下“在终端中查看”， 然后在打开的终端中手动输入一下“y”就可以了

![[笔记同步助手/images/46ed164ddf39e07e3896f3405828f5a7_MD5.png]]

### 配置

安装完成之后，Trae会主动问你是否需要配置，回答一下，Trae就会开始帮你配置了 。

![[笔记同步助手/images/821c5841a87511706d3fe05ecb7f8cc1_MD5.png]]

配置过程中会在终端中弹出一个二维码，扫描后会在飞书开放平台自动生成对应的飞书机器人，生成后Trae会自动完成绑定。

![[笔记同步助手/images/9dc029af10d5c05e91f836864b071e49_MD5.png]]

### 授权

配置成功之后，Trae会主动问你是否授权，这也是最后一步了。同样，简单回复“授权”即可

![[笔记同步助手/images/4f9f1c7fa5d28e3b03d5e6895bb96355_MD5.png]]

授权过程需要手动确认一下，Trae会提示你在浏览器中打开一个授权链接，打开后完成授权就行了

![[笔记同步助手/images/f9f36d26ec9cf2be3a131a7dfb080b13_MD5.png]]

![[笔记同步助手/images/790b071a7fe80c0b2e7dfe7a535250c3_MD5.png]]

开通后记得给Trae回复一下“开通成功”，Trae就会完成最后的配置了

![[笔记同步助手/images/b06916ba848ea0635c4e6415ef7a200d_MD5.png]]

这样，在Trae中的飞书CLI就配置完成了，可以通过Trae来直接操作你的飞书了 !

![[笔记同步助手/images/5de86a260142853cc372b83bc68949c2_MD5.png]]

**祝各位的AI Agent用得愉快**

---

既然都看到这里了，那就点个关注吧，更多的实战手册马上就来，让你的AI好用，让你用好AI。

---

![[笔记同步助手/images/114700745c30f4f97a898afc9ad98fa5_MD5.jpg|cover_image]]

原创 智用手册 百工AI实战手册

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/f1771b63_1779621049707?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk2NDUxNDQ3Nw%3D%3D%26mid%3D2247484477%26idx%3D1%26sn%3D07e156c6155a76995c59465886c4c33b%26chksm%3Dc5111ada0dadbefc4b1150b856ccb838ab9e970677c11ddb10b7349f7fd15106f2ac61020a9e%26mpshare%3D1%26scene%3D1%26srcid%3D0524SXyJAazQtKwNbr2qsox9%26sharer_shareinfo%3D3b7e48d8e8dfe88e7a559d1b21ef4af2%26sharer_shareinfo_first%3D3b7e48d8e8dfe88e7a559d1b21ef4af2%23rd&s=obsidian)