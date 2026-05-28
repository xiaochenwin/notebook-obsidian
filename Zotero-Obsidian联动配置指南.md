# Zotero + Obsidian 联动配置完全指南

> 打造文献管理到知识创作的无缝工作流

---

## 目录

1. [方案概述](#一方案概述)
2. [所需插件清单](#二所需插件清单)
3. [Zotero 端配置](#三zotero-端配置)
4. [Obsidian 端配置](#四obsidian-端配置)
5. [联动使用流程](#五联动使用流程)
6. [进阶技巧](#六进阶技巧)
7. [常见问题解决](#七常见问题解决)

---

## 一、方案概述

### 1.1 联动架构

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   浏览器/网页    │────▶│     Zotero      │────▶│    Obsidian     │
│  (文献发现)      │     │  (文献管理)      │     │  (知识创作)      │
└─────────────────┘     └─────────────────┘     └─────────────────┘
        │                       │                       │
        ▼                       ▼                       ▼
   Zotero Connector       Better BibTeX         Obsidian插件
   (一键抓取)              (引用键管理)          (文献笔记)
```

### 1.2 核心优势

- **文献统一管理**：Zotero 负责收集、整理、存储所有文献
- **引用自动同步**：Better BibTeX 生成稳定引用键
- **笔记双向链接**：Obsidian 中直接引用 Zotero 文献
- **PDF 标注同步**：阅读标注自动转为 Obsidian 笔记

---

## 二、所需插件清单

### 2.1 Zotero 插件

| 插件名 | 功能 | 下载地址 |
|--------|------|----------|
| **Better BibTeX** | 生成稳定引用键 | https://retorque.re/zotero-better-bibtex/ |
| **ZotFile** | PDF 附件管理 | https://zotfile.com/ |
| **Zotero PDF Translate** | PDF 划词翻译 | https://github.com/windingwind/zotero-pdf-translate |

### 2.2 Obsidian 插件

| 插件名 | 功能 | 安装方式 |
|--------|------|----------|
| **Zotero Integration** | 与 Zotero 联动 | 社区插件市场 |
| **Citations** | 文献引用增强 | 社区插件市场 |
| **BibNotes Formatter** | 文献笔记格式化 | 社区插件市场 |

---

## 三、Zotero 端配置

### 3.1 安装 Better BibTeX

#### 步骤 1：下载插件
1. 访问 https://github.com/retorquere/zotero-better-bibtex/releases
2. 下载最新版本的 `.xpi` 文件（如 `zotero-better-bibtex-6.7.XXX.xpi`）

#### 步骤 2：安装插件
1. 打开 Zotero 独立版（Standalone）
2. 点击菜单栏 **工具 → 插件**
3. 点击右上角齿轮图标 → **Install Plugin From File...**
4. 选择下载的 `.xpi` 文件
5. 重启 Zotero

#### 步骤 3：配置 Better BibTeX

**设置引用键格式：**

1. 编辑 → 首选项 → Better BibTeX
2. 找到 **Citation key formula** 选项
3. 推荐格式：
   ```
   auth.lower + shorttitle(3,3) + year
   ```
   或更简洁的：
   ```
   auth.lower + year
   ```

**配置自动导出（可选）：**

1. 编辑 → 首选项 → Better BibTeX → 自动导出
2. 勾选 **启用自动导出**
3. 选择导出格式：**Better BibLaTeX**
4. 设置导出路径（建议放在 Obsidian 库中）

### 3.2 安装 ZotFile

#### 步骤 1：下载插件
访问 https://github.com/jlegewie/zotfile/releases 下载 `.xpi` 文件

#### 步骤 2：安装并配置
1. 按上述方法安装插件
2. 编辑 → 首选项 → ZotFile Preferences

**关键配置项：**

| 配置项 | 推荐设置 | 说明 |
|--------|----------|------|
| Source Folder | 浏览器下载目录 | 自动抓取下载的 PDF |
| Location of Files | 自定义路径 | PDF 存储位置 |
| Renaming Rules | `{%a_}{%y_}{%t}` | 重命名规则：作者_年份_标题 |

**重命名规则说明：**
- `%a` = 作者姓氏
- `%y` = 年份
- `%t` = 标题（可限制长度如 `%t{50}`）

### 3.3 安装 Zotero PDF Translate

#### 步骤 1：下载插件
访问 https://github.com/windingwind/zotero-pdf-translate/releases

#### 步骤 2：配置翻译引擎
1. 安装后重启 Zotero
2. 编辑 → 首选项 → PDF Translate
3. 选择翻译服务（推荐 DeepL 或 Google）
4. 如需使用 DeepL，需填写 API 密钥

---

## 四、Obsidian 端配置

### 4.1 安装 Zotero Integration 插件

#### 步骤 1：安装插件
1. Obsidian → 设置 → 第三方插件
2. 关闭**安全模式**
3. 点击**浏览**，搜索 **"Zotero Integration"**
4. 安装并启用

#### 步骤 2：基础配置

1. 打开 Zotero Integration 设置
2. 配置 **Zotero 数据库路径**：
   - Windows: `C:\Users\用户名\Zotero\zotero.sqlite`
   - macOS: `~/Library/Application Support/Zotero/Profiles/xxx.default/zotero.sqlite`
   - 或使用 Better BibTeX 导出的 `.bib` 文件路径

3. **引用格式设置**：
   ```
   [@{{citekey}}]
   ```

#### 步骤 3：配置文献笔记模板

在插件设置中找到 **Literature Note Template**，粘贴以下模板：

```markdown
---
title: "{{title}}"
authors: {{authors}}
year: {{year}}
journal: {{publicationTitle}}
doi: {{DOI}}
citekey: {{citekey}}
zotero_link: {{pdfZoteroLink}}
tags: literature-note
---

# {{title}}

## 基本信息
- **作者**: {{authors}}
- **年份**: {{year}}
- **期刊**: {{publicationTitle}}
- **DOI**: {{DOI}}
- **引用键**: {{citekey}}

## Zotero 链接
[在 Zotero 中打开]({{pdfZoteroLink}})

## 研究问题

## 核心观点

## 方法论

## 关键结论

## 个人思考

## 相关文献

```

### 4.2 安装 Citations 插件（可选增强）

#### 步骤 1：安装
1. 社区插件市场搜索 **"Citations"**
2. 安装并启用

#### 步骤 2：配置
1. 设置 → Citations
2. **Citation database format**: `BibLaTeX`
3. **Citation database path**: 选择 Better BibTeX 导出的 `.bib` 文件路径
4. **Literature note folder**: 设置文献笔记存放文件夹（如 `Literature Notes`）

#### 步骤 3：设置快捷键
1. 设置 → 快捷键
2. 搜索 "Citations"
3. 为以下命令设置快捷键：
   - **Open literature note**: `Ctrl/Cmd + Shift + O`
   - **Insert literature note link**: `Ctrl/Cmd + Shift + L`

### 4.3 创建文献管理目录结构

在 Obsidian 中建立以下文件夹：

```
📁 您的Obsidian库/
├── 📁 Literature Notes/          # 文献笔记（自动创建）
├── 📁 Research/                  # 研究笔记
│   ├── 📁 Ideas/                # 研究想法
│   ├── 📁 Drafts/               # 草稿
│   └── 📁 References/           # 参考引用
├── 📁 Templates/                 # 模板文件
│   └── literature-note.md       # 文献笔记模板
└── 📁 Zotero/                    # Zotero 导出文件
    └── references.bib           # Better BibTeX 导出
```

---

## 五、联动使用流程

### 5.1 文献收集流程

```
发现文献 → 一键抓取 → Zotero整理 → 自动同步 → Obsidian引用
```

**具体操作：**

1. **浏览器中**：
   - 安装 Zotero Connector 浏览器插件
   - 看到感兴趣文献时，点击浏览器工具栏 Zotero 图标
   - 自动抓取元数据和 PDF

2. **Zotero 中**：
   - 文献自动导入库中
   - Better BibTeX 自动生成引用键（如 `smith2023ai`）
   - ZotFile 自动重命名并移动 PDF

3. **Obsidian 中**：
   - 使用快捷键插入引用 `[@smith2023ai]`
   - 自动生成文献笔记

### 5.2 文献阅读与笔记流程

**方法一：Zotero 阅读 + Obsidian 笔记**

1. 在 Zotero 中打开 PDF 阅读
2. 使用 Zotero PDF Translate 翻译不懂的内容
3. 高亮重点段落，添加笔记
4. 回到 Obsidian，创建文献笔记
5. 手动整理阅读心得

**方法二：Obsidian 直接管理（推荐）**

1. 在 Obsidian 中使用 Zotero Integration 命令
2. 搜索并插入文献
3. 自动生成文献笔记
4. 在笔记中直接链接到 Zotero PDF
5. 在 Obsidian 中完成所有笔记整理

### 5.3 写作引用流程

**插入引用：**

1. 在 Obsidian 编辑模式下，使用快捷键（如 `Ctrl+Shift+E`）
2. 弹出 Zotero 搜索框，输入关键词
3. 选择文献，自动插入 `[@citekey]`

**查看引用：**

- 鼠标悬停在 `[@citekey]` 上，显示文献详情
- 点击可跳转到文献笔记

**生成参考文献列表：**

在文档末尾添加：

```markdown
## 参考文献

```

（使用 Pandoc 或插件自动生成）

---

## 六、进阶技巧

### 6.1 Dataview 查询文献

安装 Dataview 插件后，可以创建动态文献列表：

```markdown
```dataview
table authors, year, journal
tag: literature-note
sort year desc
```
```

### 6.2 与 AI 工作流结合

结合您的 Trae AI 工作台：

1. 在 Obsidian 中整理文献笔记
2. 将文献笔记作为上下文提供给 Trae
3. 让 AI 帮助：
   - 总结文献核心观点
   - 对比多篇文献
   - 生成文献综述初稿
   - 提取研究方法

**示例提示词：**

```
请参考以下文献笔记，帮我总结这三篇关于 AI 教育的论文的核心观点：

- [[smith2023ai]]
- [[johnson2024learning]]
- [[wang2023intelligent]]

请输出：
1. 每篇论文的研究问题
2. 主要发现
3. 对我的 AI 班主任研究的启示
```

### 6.3 批量导入历史文献

1. 在 Zotero 中选中多篇文献
2. 右键 → **Better BibTeX** → **导出附件**
3. 选择格式：Better BibLaTeX
4. 在 Obsidian 中批量创建笔记

### 6.4 移动端同步

1. 使用 Zotero 官方移动端 App 查看文献
2. 使用 Obsidian Sync 或 iCloud 同步笔记
3. 实现随时随地查阅文献和笔记

---

## 七、常见问题解决

### 7.1 Better BibTeX 引用键冲突

**问题**：不同文献生成相同引用键

**解决**：
1. 编辑 → 首选项 → Better BibTeX
2. 修改 Citation key formula 添加更多区分字段：
   ```
   auth.lower + shorttitle(3,3) + year
   ```

### 7.2 Zotero 数据库路径找不到

**问题**：Obsidian 中提示找不到 zotero.sqlite

**解决**：
1. 使用 Better BibTeX 导出 `.bib` 文件
2. 在 Obsidian 插件中选择 `.bib` 文件而非 `.sqlite`

### 7.3 中文文献支持不佳

**问题**：中文文献引用键生成异常

**解决**：
1. Better BibTeX 设置中启用 **保留 Unicode**
2. 或使用拼音化引用键：
   ```
   auth.lower + year
   ```

### 7.4 PDF 无法打开

**问题**：Obsidian 中点击 Zotero 链接无法打开 PDF

**解决**：
1. 确保 Zotero 正在运行
2. 检查 Zotero 中 PDF 附件路径是否正确
3. 使用 ZotFile 重新整理附件路径

### 7.5 同步延迟

**问题**：Zotero 新增文献后 Obsidian 中搜索不到

**解决**：
1. 在 Zotero 中手动导出 `.bib` 文件
2. 或在 Better BibTeX 中启用自动导出
3. 重启 Obsidian 刷新缓存

---

## 附录：快捷键汇总

| 操作 | 快捷键 |
|------|--------|
| 插入 Zotero 引用 | `Ctrl/Cmd + Shift + E` |
| 打开文献笔记 | `Ctrl/Cmd + Shift + O` |
| 搜索文献 | `Ctrl/Cmd + Shift + L` |
| Zotero 快速复制引用 | `Ctrl/Cmd + Shift + C` |

---

## 总结

通过以上配置，您将拥有：

✅ **统一的文献管理中心**（Zotero）  
✅ **无缝的知识创作环境**（Obsidian）  
✅ **自动化的引用系统**（Better BibTeX）  
✅ **可追溯的知识网络**（双向链接）  

这套方案特别适合教育研究者、学术写作者，以及像您这样需要管理大量文献资料的内容创作者！

---

*配置完成时间：约 30 分钟*  
*熟练使用时间：约 1-2 周*
