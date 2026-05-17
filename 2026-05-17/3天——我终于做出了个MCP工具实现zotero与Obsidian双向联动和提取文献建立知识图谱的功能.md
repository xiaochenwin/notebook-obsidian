---
author: 口天三木
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk3NTE1MDQ5Ng==&mid=2247483945&idx=1&sn=e4797f6890540cef3bb27ea0a787f212&chksm=c58cfa710724ff2070512f2b64de21730c34bf7f03255f00c5132b4567a771c0dd8316f84eb7&mpshare=1&scene=1&srcid=05173WwPNspvtgoXzjMLVFq6&sharer_shareinfo=83d5ac81a49e1a122995d2e134fc5a7e&sharer_shareinfo_first=83d5ac81a49e1a122995d2e134fc5a7e#rd
saved: 2026-05-17 22:27:36
tags:
  - 笔记同步助手
id: 2c7ee959-eed5-4e7c-9011-9794aa5a2101
---

公众号名称：口天三木

作者名称：口天三木

发布时间：2026-05-12 12:28

如题，我花了3天3夜，利用Claude code和codex辅助开发了一个插件，包含MCP和skills，这里skills包含MCP的工具使用说明，MCP也做了处理可以以极低的token实现丰富的功能

emmm，怎么说呢

我开发的是一个本地 Obsidian Vault MCP 服务，核心定位是把 Obsidian 仓库维护成可持续增长的双链知识库，供 AI (Claude/Codex) 直接操作

简单说：这个插件让 AI 能像人一样操作你的 Obsidian 知识库—从 Zotero 拉文献、用 MinerU 解析 PDF、自动建立双链、维护索引，整个文献管理和知识整理流程都可以通过对话驱动。

详细的功能如下：

## 一、进行Obsidian下的文件操作

-   列出、搜索、读取、写入 Markdown 文件；
    
-   创建带 YAML frontmatter 的笔记；
    
-   所有写入操作支持 \`dry\_run\` 预览 \`diff\`，批量编辑支持预览、应用、备份和回滚。
    

  

## 二、构建知识图谱与链接管理

-   自动添加 wikilinks，基于别名、标签、未解析链接构建图谱
    
-   检测孤立笔记、死链笔记、重复 key、空笔记、缺失标题等问题
    
-   建议创建未解析页面、补充反向链接、合并可能重复的页面
    
-   从wikilinks图自动生成 Canvas (支持 grid/radial/grouped/layered 布局)
    

  

## 三、文献管理 (Zotero 深度集成)

-   直接访问Zotero Desktop本地 API，搜索条目、读取元数据、子笔记、标注、PDF 附件
    
-   支持 BibTeX，参考文献元数据、Zotero 条目的批量导入
    
-   支持 \`zotero://\` 链接，重复检测、PDF 附件命名策略
    
-   读取 PDF 标注 (含 Zotero PDF Translate 翻译结果)
    

  

## 四、MinerU PDF 解析

-   调用 \`MinerU Open API CLI\` 解析 PDF/文档 (支持 600 页)
    
-   提取结构化 Markdown 后导入 Obsidian，并将解析结果链接回 Zotero
    

  

## 五、LLM Wiki 工作流

-   刷新 \`index.md\`、追加 \`log.md\`
    
-   把来源材料整理进 \`source/entity/concept\` 页面，形成可持续增长的结构。
    

  

## 六、Obsidian CLI 封装

-   调用官方 \`obsidian CLI\`，提供读取、打开
    
-   \`backlinks\` 查询、\`Base\` 查询、\`properties\` 管理、\`tasks\`、截图、插件 \`reload\`、移动/重命名等结构化工具。
    

  

![[笔记同步助手/images/19083ff6a6eb58e47896fb1504f5457d_MD5.png]]

我实际使用的效果——视频演示👇：

每一篇从zotero中提取的文献信息如下：

![[笔记同步助手/images/abdb156dd30dbed5e1370d9fde2ec0d1_MD5.png]]

如果你的zotero中对PDF做了批注和笔记

也会顺带提取

![[笔记同步助手/images/3732b578b25a40dfd942e7496f7223da_MD5.png]]

![](https://relay-1.bijitongbu.site/p/a613677363972f61ba2d8741f17bf93f.png)

对应的zotero批注位置和颜色标签也会一一对应

![[笔记同步助手/images/012ee0166bea753096a9d87a2e440c71_MD5.png]]

然后还和zotero联动，带有zotero对应文献的可跳转链接

![[笔记同步助手/images/907b5c22862908f353b1d1ed161e4a4a_MD5.png]]

上面的url是文献出版社获取原始文献pdf的网址

再下面的地址是zotero的条目和pdf位置，点击即可自动打开zotero，选中条目以及匹配的PDF

这里还提取了BibTeX引用格式

还有使用MinerU解析后文档的链接，点击即可跳转解析文档

后期需要对文献进行知识图谱网络也非常方便

![[笔记同步助手/images/3363695e689d35cb308517d0c43b93b9_MD5.png]]

对了，我还加增加了索引功能

所以每次导入文献笔记只会更新和追加，带有版本标签不会覆盖，可追溯

写到这里，

可能有人会问：

做这个有何意义？不如直接使用zotero，为啥还要牵扯到Obsidian

我想，两个都是笔记管理工具，没有孰好孰坏之分

我这个工具开发出来

也只是在为了方便两者之间进行迁移

此外，

这个插件的核心功能可以满足那些将Obsidian当做个人知识库使用的部分群体的需求

尤其是需要做笔记双联，通过Obsidian直观的图谱网络查看笔记间相互关系的群体

另外，Obsidian非常适合拿来做论文写作的初稿

很多内容创作者和科研工作者都有部分群体使用Obsidian来写作，结合zotero 和Obsidian在chrome中的插件搭配使用，效果翻倍

还有BibTeX 格式引用在Obsidian也方便使用，再结合pandoc 格式转换，撰写论文初稿就更加便捷

最后，

这个插件在我上一篇文章[我做了一款Codex桌面版插件，彻底打通zotero-MinerU-Obsidian，构建个人知识图谱](https://mp.weixin.qq.com/s?__biz=Mzk3NTE1MDQ5Ng==&mid=2247483924&idx=1&sn=04485795afbcbd677a637e78a7217677&scene=21#wechat_redirect)有发布过地址，只不过当时还没有完全实现

现在已经更新啦！

后期还会继续完善，希望有更多的大佬支持这个项目

https://github.com/luffysolution-svg/obsidian-vault-mcp

![[笔记同步助手/images/89bc45e5d4ab6b5379a4c361a496c3ee_MD5.png]]

![[笔记同步助手/images/39804ed09d4a355519e9177b8d2f981d_MD5.png]]

![[笔记同步助手/images/8e20a38f58d2b14bb3e3025169bf24bb_MD5.png]]

![[笔记同步助手/images/e28b2687d05fe5fadf44a8656484f163_MD5.png]]

![[笔记同步助手/images/6854d6d988e373d786c36942d2fd33c8_MD5.png]]

![[笔记同步助手/images/24f8edda647261be5708e5f24e196a91_MD5.png]]

当然，小白不会安装的，可以让AI 客户端如opencode（使用deekseek或者kimi code都可以）来帮你安装

下面是提示词：

```
Install and configure the open-source Obsidian Vault MCP plugin from
https://github.com/luffysolution-svg/obsidian-vault-mcp.

Please:
1. Install the package with `pip install zotero-obsidian-mcp`, or clone the repository and run `pip install -e .` for a development install.
2. Register it as a local MCP server. Use the method that matches the AI client
you are running in:
- Codex: register using the checked-in `.mcp.json` as a local Codex plugin.
- Claude Code: run `claude mcp add obsidian-vault obsidian-vault-mcp`, or add
the server block from `.mcp.json` to `～/.claude/settings.json`.
- OpenCode: copy `.opencode.json` from the repository root to the project
directory, or merge its `mcp` block into `～/.opencode.json`.
- Trae: add the server block from `.mcp.json` to `.trae/mcp.json` in the
project root, or paste it in Trae's MCP settings UI.
- CodeBuddy: the checked-in `.mcp.json` is picked up automatically from the
project root; or paste the server block in CodeBuddy's MCP settings UI.
- Kimi Code: run `kimi mcp add --transport stdio obsidian-vault obsidian-vault-mcp`
and set env `OBSIDIAN_VAULT_PATH=auto`, or edit `～/.kimi/mcp.json` directly.
- Other MCP clients: register a stdio server with command
`obsidian-vault-mcp` and env `OBSIDIAN_VAULT_PATH=auto`.
3. Register the workflow skill for Claude Code (skip for Codex and OpenCode — they load skills automatically from the plugin directory):
- Run this one-liner to copy the bundled skill file into Claude Code's skills directory:
python -c "import obsidian_vault_mcp, shutil, pathlib; src=pathlib.Path(obsidian_vault_mcp.__file__).parent/'skills'/'obsidian-vault'/'SKILL.md'; dst=pathlib.Path.home()/'.claude'/'skills'/'obsidian-vault'/'SKILL.md'; dst.parent.mkdir(parents=True, exist_ok=True); shutil.copy(src, dst); print('Skill registered:', dst)"
- Restart Claude Code so the skill appears in the available skill list.
4. Use `OBSIDIAN_VAULT_PATH=auto` by default. If auto-detection fails, ask me
for my local Obsidian vault path and configure it only in my local
MCP/plugin settings.
5. Do not modify or publish my Obsidian vault contents.
6. Verify the server can start, then run `python -m unittest discover -s tests`.
7. Tell me how to restart/reload the AI client so the new MCP tools become
available.

Optional: if I want Zotero features, remind me to open Zotero Desktop so its
local API at `http://127.0.0.1:23119/api` is reachable. For best results,
also install Better BibTeX for Zotero (https://retorque.re/zotero-better-bibtex/)
to enable stable citekeys. If I use Ethereal Style (ZoteroStyle) to assign
custom color labels to annotations, those labels will be picked up automatically.

Optional: if I want MinerU document parsing, check whether `mineru-open-api`
is installed. If it is not installed, tell me how to install it. Do not store
or commit MinerU tokens in the repository. Use `flash-extract` when I do not
have a token, and use precision `extract` only when I have configured MinerU
authentication locally.
```

对于这个项目，我自己感觉是个不错的想法，个人使用体验还可以

现在已经有2个star了，也是第一次看见有人支持，开心了一整天

嘿嘿嘿

那么，加纳！下期见！

  

---

![[笔记同步助手/images/057b452e5275603b051ff8677861230f_MD5.jpg|cover_image]]

Original 口天三木 口天三木

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/d53fc636_1779028055392?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk3NTE1MDQ5Ng%3D%3D%26mid%3D2247483945%26idx%3D1%26sn%3De4797f6890540cef3bb27ea0a787f212%26chksm%3Dc58cfa710724ff2070512f2b64de21730c34bf7f03255f00c5132b4567a771c0dd8316f84eb7%26mpshare%3D1%26scene%3D1%26srcid%3D05173WwPNspvtgoXzjMLVFq6%26sharer_shareinfo%3D83d5ac81a49e1a122995d2e134fc5a7e%26sharer_shareinfo_first%3D83d5ac81a49e1a122995d2e134fc5a7e%23rd&s=obsidian)