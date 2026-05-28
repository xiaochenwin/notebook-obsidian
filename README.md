# 学术笔记管理系统 (Obsidian + Zotero)

这是一个基于 **Obsidian** 和 **Zotero** 构建的学术笔记管理系统，用于高效管理文献、笔记和知识。

## 📚 目录结构

```
笔记同步助手/
├── 2026-05-17/           # 2026年5月17日学习笔记
│   └── *.md              # 各类学习笔记文章
├── 2026-05-17-note/      # 5月17日学习总结
│   ├── 2026-05-17学习总结.md
│   └── 2026-05-17学习总结PPT.html
├── 2026-05-18/           # 2026年5月18日学习笔记
│   └── *.md              # 各类学习笔记文章
├── 2026-05-18-note/      # 5月18日学习总结
│   ├── 2026-05-18学习总结.md
│   └── 2026-05-18学习总结PPT.html
├── 2026-05-19/           # 2026年5月19日学习笔记
│   └── *.md              # 各类学习笔记文章
├── 2026-05-19-note/      # 5月19日学习总结
│   ├── 2026-05-19学习总结.md
│   └── 2026-05-19学习总结PPT.html
├── 2026-05-20/           # 2026年5月20日学习笔记
│   └── *.md              # 各类学习笔记文章
├── 2026-05-20-note/      # 5月20日学习总结
│   ├── 2026-05-20学习总结.md
│   └── 2026-05-20学习总结PPT.html
└── images/                # 全局图片资源
```

## 🔧 核心工具链

| 工具 | 用途 |
|------|------|
| **Zotero** | 文献管理与引用 |
| **Obsidian** | 笔记整理与知识管理 |
| **OneDrive + Remote Save** | 多端同步方案 |
| **Codex AI** | 论文写作与PPT制作 |
| **NotebookLM** | 知识梳理与图谱构建 |
| **Claude** | 表达优化与框架搭建 |
| **Cursor** | AI代码编辑器 |

## 📖 主要内容

### Zotero + Obsidian 联动方案
- 原生复制粘贴 (Ctrl+C/V)
- Better Bibtex + Zotero Integration 插件联动
- Obsidian Vault MCP 工具深度集成

### AI 辅助科研工具
- **Nature-Skills**: 上交博士开源的论文写作AI指令集
  - nature-figure: Nature级别图表生成
  - nature-polishing: 论文语言润色
  - nature-writing: 论文章节写作
  - nature-paper2ppt: 论文一键生成PPT
  - nature-response: 审稿意见回复

- **Codex AI**: /goal命令驱动，高效制作论文答辩PPT

- **Academic Research Skills**: GitHub万星项目，论文生产工作台

### 学术工作流架构
```
输入 (Zotero) → 处理 (NotebookLM) → 输出 (Claude)
```

### AI知识系统构建
- Obsidian 30+插件生态配置
- AI驱动的知识结构化系统
- Karpathy方法与LLM Wiki实践

## 🚀 快速开始

### 1. 克隆仓库
```bash
git clone git@github.com:xiaochenwin/notebook-obsidian.git
cd notebook-obsidian
```

### 2. 同步设置
使用 Remote Save + OneDrive 实现多端同步：
- Windows: 双向同步
- Mac/手机: 增量推送

### 3. 推荐配置
- 并行度设置为 1~2（避免卡死）
- 各端仓库名称必须完全一致
- 不要开启"同步配置文件夹"

## 📝 学习总结

| 日期 | Markdown | HTML PPT |
|------|----------|----------|
| 2026-05-17 | [学习总结](./2026-05-17-note/2026-05-17学习总结.md) | [PPT网页](./2026-05-17-note/2026-05-17学习总结PPT.html) |
| 2026-05-18 | [学习总结](./2026-05-18-note/2026-05-18学习总结.md) | [PPT网页](./2026-05-18-note/2026-05-18学习总结PPT.html) |
| 2026-05-19 | [学习总结](./2026-05-19-note/2026-05-19学习总结.md) | [PPT网页](./2026-05-19-note/2026-05-19学习总结PPT.html) |
| 2026-05-20 | [学习总结](./2026-05-20-note/2026-05-20学习总结.md) | [PPT网页](./2026-05-20-note/2026-05-20学习总结PPT.html) |

### PPT 操作方式
- 左右箭头键或空格翻页
- Home/End 跳转首尾
- 触屏设备支持左右滑动
- 鼠标滚轮支持翻页

## � 学习进度统计

| 日期 | 笔记数量 | 核心主题 | 综合评分 |
|------|----------|----------|----------|
| 2026-05-17 | 22篇 | Zotero联动/Obsidian同步/Nature-Skills | 82/100 |
| 2026-05-18 | 21篇 | Codex进阶/Obsidian配置/Claude Code | 85/100 |
| 2026-05-19 | 51篇 | Obsidian深度配置/Codex应用/Zotero升级 | 85/100 |
| 2026-05-20 | 20篇 | Claude Code/学术写作/AIContent创作 | 88/100 |

## 🚀 学习路径

```
第一阶段：文献管理基础
  └─ Zotero配置与文献导入
  └─ Zotero+Obsidian联动

第二阶段：AI工具集成
  └─ Codex AI安装与配置
  └─ Claude Code实战应用

第三阶段：知识系统构建
  └─ Obsidian插件生态配置
  └─ AI驱动的知识结构化

第四阶段：学术产出
  └─ 论文写作自动化
  └─ PPT制作与汇报
```

## 🔑 明日学习建议 (2026-05-21)

1. **最高优先级**: Claude Code实战，尝试完成一篇论文初稿
2. **重要**: 使用Nature-polishing优化论文表达
3. **体验**: QoderWake数字员工配置
4. **插件**: Obsidian Yolo插件配置

## 📄 License

MIT License