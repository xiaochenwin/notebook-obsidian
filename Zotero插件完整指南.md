# Zotero 插件生态完整指南

> 📅 整理时间：2026-05-21
> 📚 涵盖范围：2026-05-17 至 2026-05-21 学习内容

---

## 一、这段时间的学习总结

### 📊 五日学习数据

| 日期 | 笔记数 | 核心主题 | 综合评分 |
|------|--------|----------|----------|
| 2026-05-17 | 22篇 | Zotero联动/Obsidian同步/Nature-Skills | 82/100 |
| 2026-05-18 | 21篇 | Codex进阶/Obsidian配置/Claude Code | 85/100 |
| 2026-05-19 | 51篇 | Obsidian深度配置/Codex应用/Zotero升级 | 85/100 |
| 2026-05-20 | 20篇 | Claude Code/学术写作/AIContent创作 | 88/100 |
| 2026-05-21 | 30篇 | Obsidian智能知识库/双模型配置/Skill开发 | 90/100 |
| **合计** | **144篇** | | **86/100** |

---

### 🎯 核心学习成果

#### 1. Zotero + Obsidian 联动方案（5月17日）
- **原生复制粘贴**：Ctrl+C/V 最简单直接
- **插件联动**：Better Bibtex + Zotero Integration
- **MCP工具**：Obsidian Vault MCP 实现双向联动
- **zotero9升级问题**：一键解决插件不适配

#### 2. Zotero 插件生态扩展（5月18-21日）
- **AI插件**：Zotero GPT、Zotero Awesome GPT、AI4Paper、LLM for Zotero
- **翻译插件**：Translate for Zotero、Suppr
- **效率插件**：Actions & Tags、Better Notes、Better BibTeX
- **界面插件**：Zotero Style、Zotero Box

#### 3. Codex + Zotero 深度集成（5月17-18日）
- Codex 桌面版官方 Zotero 插件
- 让 AI 从自己的文献库找参考文献
- 自动插入 APA 格式参考文献

#### 4. Zotero + AI 工作流（5月19日）
- Zotero + Claude：文献管理与 AI 问答
- Zotero + NotebookLM：知识图谱构建
- Zotero MCP + Linter + LaTeX：参考文献 AI 核查

---

## 二、Zotero 所有可用插件完整列表

### 📥 文献获取与同步

| 插件名称 | GitHub/官网 | 功能说明 | 推荐指数 |
|----------|-------------|----------|----------|
| **Zotero Connector** | 官方自带 | 浏览器插件，快速抓取学术数据库文献 | ⭐⭐⭐⭐⭐ |
| **Zotero Word插件** | 官方自带 | Word/LibreOffice集成，插入引用 | ⭐⭐⭐⭐⭐ |
| **Add-on Manager for Zotero** | Zotero插件管理 | 集成化管理插件市场，支持直接搜索安装 | ⭐⭐⭐⭐ |

---

### 📝 文献阅读与笔记

| 插件名称 | GitHub | Stars | 功能说明 | 推荐指数 |
|----------|--------|-------|----------|----------|
| **Better Notes** | windingwind/zotero-better-notes | - | 读论文→划重点→写笔记→整理入库全流程，支持模板、双向链接，可与Obsidian互通 | ⭐⭐⭐⭐⭐ |
| **Zotero Reference** | MuiseDestiny/zotero-reference | - | PDF内一键跳转参考文献原文，再点直接打开对应PDF | ⭐⭐⭐⭐⭐ |

---

### 🌐 翻译插件

| 插件名称 | GitHub/官网 | Stars | 功能说明 | 推荐指数 |
|----------|-------------|-------|----------|----------|
| **Translate for Zotero** | windingwind/zotero-pdf-translate | 10.9k ⭐ | 20+翻译引擎（Google/DeepL/OpenAI等），边读边译，标注翻译自动保存 | ⭐⭐⭐⭐⭐ |
| **Suppr（超能文献翻译）** | suppr.wilddata.cn | - | 整篇PDF/Word/PPT翻译，保留原排版，注册送25万汉字额度 | ⭐⭐⭐⭐ |

---

### ⚡ 效率与自动化

| 插件名称 | GitHub | 功能说明 | 推荐指数 |
|----------|--------|----------|----------|
| **Actions & Tags** | windingwind/zotero-actions-tags | 事件驱动自动化，如"添加标签自动执行动作"、"关闭PDF自动打已读标签" | ⭐⭐⭐⭐⭐ |
| **Better BibTeX** | retorquere/zotero-better-bibtex | 自动生成规范BibTeX key，配合Overleaf实现"Zotero添加文献，Overleaf直接cite" | ⭐⭐⭐⭐⭐ |
| **Zotero Linter** | - | 自动整理文献元数据，修复格式问题 | ⭐⭐⭐⭐ |

---

### 🤖 AI 增强插件

| 插件名称 | GitHub | Stars | 功能说明 | 推荐指数 |
|----------|--------|-------|----------|----------|
| **Zotero GPT** | MuiseDestiny/zotero-gpt | - | 选中PDF内容右键直接问GPT/DeepSeek，内置多种prompt命令，可生成Obsidian canvas | ⭐⭐⭐⭐⭐ |
| **AI4Paper** | - | - | Zotero完整科研AI能力，文献分析、总结、问答 | ⭐⭐⭐⭐ |
| **Zotero Awesome GPT** | - | - | Zotero GPT的另一个选择，支持DeepSeek V4配置 | ⭐⭐⭐⭐ |
| **LLM for Zotero** | yilewang/llm-for-zotero | 800+ ⭐ | 调用大模型（OpenAI/Claude/本地模型），下载量4万+ | ⭐⭐⭐⭐ |
| **Zotero连Claude插件** | - | - | 将Zotero与Claude强强联合 | ⭐⭐⭐⭐ |

---

### 📊 文献评价与信息增强

| 插件名称 | 官网 | 功能说明 | 推荐指数 |
|----------|------|----------|----------|
| **Zotero Box** | scigreat/zotero-box | 自动抓取影响因子、JCR/中科院分区、引用次数，以一抵三（集成了茉莉花插件功能） | ⭐⭐⭐⭐⭐ |

---

### 🎨 界面与视觉

| 插件名称 | GitHub | 功能说明 | 推荐指数 |
|----------|--------|----------|----------|
| **Zotero Style** | MuiseDestiny/zotero-style | 嵌套标签（#主题/子主题）、关系图谱、美化PDF批注和笔记界面 | ⭐⭐⭐⭐⭐ |

---

### 🔧 Codex 集成

| 插件名称 | 来源 | 功能说明 | 推荐指数 |
|----------|------|----------|----------|
| **Codex Zotero插件** | Codex官方 | 让Codex从Zotero库中检索文献、整理引用、生成参考文献 | ⭐⭐⭐⭐⭐ |

---

### 🧩 其他实用插件

| 插件名称 | 功能说明 | 推荐指数 |
|----------|----------|----------|
| **JabREF** | 开源文献管理工具，与Zotero互补 | ⭐⭐⭐ |
| **Zotero中文社区插件** | zotero-chinese.com/plugins | 国内用户插件下载源 |

---

## 三、插件安装指南

### 安装方式

1. **Zotero中文社区**（推荐）
   - 网址：https://zotero-chinese.com/plugins/
   - 下载 `.xpi` 文件

2. **GitHub**
   - 下载对应 `.xpi` 文件

3. **Zotero内直接安装**
   - Zotero → 工具 → 插件
   - 拖入 `.xpi` 文件即可

### 安装步骤

```
1. 下载 .xpi 文件
2. Zotero → 工具 → 插件
3. 点击设置图标 → "从文件安装插件"
4. 选择下载的 .xpi 文件
5. 重启 Zotero
```

---

## 四、推荐插件组合

### 🚀 科研必备组合

| 类型 | 推荐插件 | 说明 |
|------|----------|------|
| **刚需必装** | Better BibTeX | LaTeX/Markdown引用必须 |
| **刚需必装** | Translate for Zotero | 外文阅读翻译 |
| **刚需必装** | Zotero Connector | 文献获取 |
| **效率提升** | Actions & Tags | 自动化管理 |
| **AI增强** | Zotero GPT | 文献问答总结 |

### 🎯 AI科研组合

| 类型 | 推荐插件 | 说明 |
|------|----------|------|
| **AI对话** | Zotero GPT | 选中内容直接问GPT |
| **本地模型** | LLM for Zotero | 支持Claude/本地模型 |
| **文献分析** | AI4Paper | 完整科研AI能力 |
| **文献信息** | Zotero Box | 影响因子/分区 |

### 📝 笔记管理组合

| 类型 | 推荐插件 | 说明 |
|------|----------|------|
| **笔记全流程** | Better Notes | 读→记→整理→Obsidian |
| **参考文献跳转** | Zotero Reference | 快速定位引用 |
| **界面美化** | Zotero Style | 嵌套标签+图谱 |

---

## 五、Zotero 版本说明

### Zotero 9 升级注意

- Zotero 9 升级后大量插件不兼容
- 解决方案：查看 Zotero中文社区的一键解决教程
- 推荐升级到 Zotero 7.0+ 以获得最佳AI插件支持

### 版本选择建议

| 版本 | 适用场景 |
|------|----------|
| Zotero 7.0+ | AI插件支持最完善 |
| Zotero 6.0 | 插件兼容性较好 |
| Zotero 9.0.1 | 最新版本，部分插件仍有bug |

---

## 六、Zotero + AI 工作流

### 工作流架构

```
文献收集 (Zotero Connector)
    ↓
文献管理 (Zotero + 插件)
    ↓
AI分析 (Zotero GPT / LLM for Zotero / AI4Paper)
    ↓
知识整理 (Better Notes → Obsidian)
    ↓
论文写作 (Better BibTeX + Word/LaTeX)
```

### 推荐 AI 模型

| 插件 | 推荐模型 | 说明 |
|------|----------|------|
| Zotero GPT | DeepSeek V4 Pro / Claude Sonnet | 效果好，有双链可跳转 |
| LLM for Zotero | OpenAI / Claude / 本地模型 | 灵活选择 |
| Zotero Awesome GPT | DeepSeek V4 | 配置简单 |

---

## 七、明日行动计划 (2026-05-22)

1. **安装核心插件**：Better BibTeX + Translate for Zotero + Zotero Connector
2. **配置AI插件**：Zotero GPT + LLM for Zotero
3. **效率插件**：Actions & Tags + Better Notes
4. **测试工作流**：Zotero → Obsidian → Claude 完整流程

---

> 📝 *"善用Zotero插件，让文献管理效率翻倍"*