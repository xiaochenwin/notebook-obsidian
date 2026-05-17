# 学术笔记管理系统 (Obsidian + Zotero)

这是一个基于 **Obsidian** 和 **Zotero** 构建的学术笔记管理系统，用于高效管理文献、笔记和知识。

## 📚 目录结构

```
笔记同步助手/
├── 2026-05-17/           # 2026年5月17日学习笔记
│   ├── *.md              # 各类学习笔记文章
│   └── images/            # 笔记中引用的图片资源
├── 2026-05-17-note/      # 学习总结
│   ├── 2026-05-17学习总结.md
│   └── 2026-05-17学习总结PPT.html
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

### 学术工作流架构
```
输入 (Zotero) → 处理 (NotebookLM) → 输出 (Claude)
```

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

## 📝 查看学习总结

学习总结以 Markdown 和 HTML PPT 两种格式提供：

- [Markdown 版本](./2026-05-17-note/2026-05-17学习总结.md)
- [PPT 网页版本](./2026-05-17-note/2026-05-17学习总结PPT.html)

PPT 操作方式：
- 左右箭头键或空格翻页
- ESC 返回首页
- 触屏设备支持左右滑动

## 🔑 明天学习建议

1. **最高优先级**: 实践 Zotero+Obsidian 联动（推荐从 Ctrl+C/V 原生方法开始）
2. **重要**: 安装 Nature-Skills，试用 nature-paper2ppt
3. **长期建设**: 按输入→处理→输出搭建学术工作流

## 📄 License

MIT License
