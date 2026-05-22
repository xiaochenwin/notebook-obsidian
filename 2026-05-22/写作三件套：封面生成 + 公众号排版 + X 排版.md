---
author: 烁皓
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk4ODAxNTg5OA==&mid=2247483965&idx=1&sn=17f40771054a305a727157dc5c20c265&chksm=c4c93e6e63fce6cf7dd49c2e24b5109cad8b6823bad4ad2a24f51269f8d44a2ab5fff05cc762&mpshare=1&scene=1&srcid=0522XAOuIG6lOWwtwxZ35RXd&sharer_shareinfo=0df08c199abeaa61d7dfe676bff98651&sharer_shareinfo_first=0df08c199abeaa61d7dfe676bff98651#rd
saved: 2026-05-22 16:08:35
tags:
  - 笔记同步助手
id: f65aaf5e-fa99-436d-93aa-50d338aa8d39
---

公众号名称：阿皓AI

作者名称：烁皓

发布时间：2026-04-20 22:05

写完文章，还有三件事要做：出封面、公众号排版、X 排版。

每件事都要开不同的工具，复制粘贴，反复对齐格式。写了半小时，收尾花了一小时。

我开源了三个浏览器工具解决这个问题，零安装，打开即用。

​

---

## 工具在哪里

项目地址：https://github.com/eternityspring/article-tools

克隆或下载后，启动个web服务就能访问。无需安装任何依赖。

![[笔记同步助手/images/21b0425d98d94e5f24a231f3f9c8f841_MD5.png]]

目前包含三个工具：

| 工具 | 文件 | 用途 |
| --- | --- | --- |
| 封面生成器 | `cover.html` | 生成文章封面图 |
| MD → 微信排版 | `md-to-wechat.html` | Markdown 转微信富文本 |
| MD → X 排版 | `md-to-x.html` | Markdown 转 X 长文格式 |

---

## 封面生成器

写完文章的第一件事：出封面。

打开 `cover.html`，工具会自动读取 `draft.md` 里的封面配置，标题、副标题、作者、字体、配色全部自动填入。

左侧选一个预设（8 个快速起点），点一下颜色、装饰、字体全部联动切换。不满意再微调。右上角点「下载 PNG」或「复制图片」，完成。

熟悉之后，从打开工具到出图不超过两分钟。

![[笔记同步助手/images/bbc7dce0a63edca0d79e437095632244_MD5.png]]

---

## MD → 微信排版

Markdown 写完，直接粘贴到微信公众号编辑器，格式全乱。

打开 `md-to-wechat.html`，工具会自动读取 `draft.md` 里的文章内容，右侧实时预览微信样式。点「复制富文本」，直接粘贴进公众号编辑器，格式完整保留。

支持标题、正文、引用块、代码块、加粗、列表，覆盖日常写作的全部需求。

![[笔记同步助手/images/06ed5c0518ae3624354c4bb002d8498c_MD5.png]]

---

## MD → X 排版

在 X 发长文，换行和格式是大问题。

打开 `md-to-x.html`，工具会自动读取 `draft.md` 里的文章内容，右侧按 X 的排版规则实时渲染：段落间距、粗体保留、代码块转纯文本。复制后直接粘贴发布。

注意：X 不支持代码块，所以代码块会转成纯文本。x也不会自动上传图片。所以需要点击图片上的复制按钮，手动到x文章编辑器中粘贴。

![[笔记同步助手/images/4f239906ba17b04c2e38d3759a816239_MD5.png]]

---

## 完整工作流

```
写 draft.md
  ↓
cover.html → 封面图（下载 / 复制）
  ↓
md-to-wechat.html → 复制富文本 → 粘贴公众号
  ↓
md-to-x.html → 复制内容 → 粘贴 X
```

三个工具独立，按需取用。全部基于本地文件，没有账号，没有服务器，不联网。

​

---

## 最后

所有代码都在单个 HTML 文件里，可以让你的Agent按照自己的需求编排优化。

这个工具是独立的，每次写完内容，可以做一个归档.skill 直接把草稿和封面图一起归档到你指定的位置。

  

---

![[笔记同步助手/images/e7044ae28f0e15e3d7a552ebccd08271_MD5.jpg|cover_image]]

Original 烁皓 阿皓AI

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/74a7a9e6_1779437313790?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk4ODAxNTg5OA%3D%3D%26mid%3D2247483965%26idx%3D1%26sn%3D17f40771054a305a727157dc5c20c265%26chksm%3Dc4c93e6e63fce6cf7dd49c2e24b5109cad8b6823bad4ad2a24f51269f8d44a2ab5fff05cc762%26mpshare%3D1%26scene%3D1%26srcid%3D0522XAOuIG6lOWwtwxZ35RXd%26sharer_shareinfo%3D0df08c199abeaa61d7dfe676bff98651%26sharer_shareinfo_first%3D0df08c199abeaa61d7dfe676bff98651%23rd&s=obsidian)