---
author: 朱晨CAU
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU1NzgzNTMxNQ==&mid=2247489397&idx=1&sn=28659c2dc7dddf61a4a69490e331ddf2&chksm=fd2e320ab7090d93f297f8c58122c79b58f654cc4f0793c4ff4f2fe74ef50f4cfa868ce00f55&mpshare=1&scene=1&srcid=0522xAGwXi6GyFMROP85sEvA&sharer_shareinfo=d00d0834999a60de8aeb15f1a46018bc&sharer_shareinfo_first=d00d0834999a60de8aeb15f1a46018bc#rd
saved: 2026-05-22 13:48:30
tags:
  - 笔记同步助手
id: 0c3cc8b8-6483-4f4d-a862-c35f790dc24b
---

公众号名称：遗传社科研究

作者名称：朱晨CAU

发布时间：2026-05-22 09:56

  

---

## **README.md 说明文件：**

![[笔记同步助手/images/b226f343ccff7f518d662b8689f2a9c5_MD5.png]]

# Paper Replication Agent | Claude Code 论文复现工作流

**作者：** 朱 晨 | 遗传社科研究 Chen Zhu | China Agricultural University (CAU)

**最后更新：** 2026-05-22

**仓库地址：** https://github.com/maxwell2732/paper-replicate-agent-demo

**论文复现智能体** — 面向经济学、流行病学等实证研究的结构化论文复现工作流，基于 Claude Code 构建。

​

---

## 快速上手指南

> 在开始之前：必须已安装 Claude Code，R，Python 3 （或 Miniconda）和 git（同时注册 GitHub 账号）。

### Step 1. Fork & Clone

\# 在 GitHub 上克隆此仓库（在仓库页面点击“ Fork ”），然后：

\# （ 将“ YOUR\_USERNAME ”替换为你自己的 GitHub 用户名 ）

git clone https://github.com/maxwell2732/paper-replicate-agent-demo.git

cd paper-replicate-agent-demo

  

【小提示】也可以将本仓库下载（zip文件），本地解压缩。但这种方法无法进行版本控制，故不太推荐。

  

### Step 2. 打开 Claude Code 并复制粘贴以下指令

\# 确保已进入本地仓库目录下，如 C:\\paper-replicate-agent-demo， 然后启动 Claude Code ：

claude

  

将准备进行复现的论文 pdf 放入到 `papers/` 文件夹中，将要用到的数据文件放入到 `data/` 文件夹中，然后根据自己需求修改以下 Prompt 并复制粘贴到 CC 中：

​

> 我把要复现的论文 \[Paper NAME\] 放到 papers/里了，数据 **\[Data NAME\]** 放到 data/里了，请阅读 Claude.md 等 configuration files ，帮我对论文所有结果进行复现，用 /plan mode。

**该 Prompt 用途：** CC 会阅读仓库中的工作流配置文件，调用相应 agents，计划并实施复现流程，生成结果并验证.

  

---

## 这个仓库做什么

本项目将 Claude Code 配置为一个**论文复现研究助手**：你提供论文 PDF 和数据集，Claude 自动完成从阅读论文、整理目标指标、编写 R 脚本、运行验证，到生成复现报告的完整流程——无需手动管理每一步。

适用于：

-   **经济学实证论文**
    
    （DID、RD、IV、固定效应、工具变量等计量方法）
    
-   **流行病学与遗传社科研究**
    
    （UK Biobank、CHNS、CHARLS 等大型队列/调查数据）
    
-   **中文社科文献复现**
    
    （中国国家健康与营养调查、中国健康与养老追踪调查等）
    
-   任何提供回归表格、样本描述统计或因果识别策略的实证论文
    

  

### 核心工作流（六阶段复现流程）

```
阅读论文  →  数据审核  →  编写脚本  →  验证结果  →  记录差异  →  生成报告
```

| 阶段 | 内容 |
| --- | --- |
| **0\. 论文解析** | 读取 PDF，提取所有实证目标（回归系数、样本量、显著性）到 `replication_targets.md` |
| **1\. 数据审核** | 核查样本构成是否与论文描述一致（N、变量定义、纳入/排除标准） |
| **2\. 代码撰写** | 将论文方法转写为可运行的 R 脚本，严格对齐原始设定 |
| **3\. 结果验证** | 将输出与目标值逐一比对，按容差阈值判定 PASS / NEAR / FAIL |
| **4\. 差异记录** | 对每个 NEAR/FAIL 结果进行溯源分析，记录尝试方案和最终解释 |
| **5\. 复现报告** | 保存 `validation_report.md`，包含完整的方法说明与结果对比表 |

  

### 容差标准

| 统计量 | 通过标准 |
| --- | --- |
| 样本量 N | 精确匹配 |
| 点估计（β、OR、HR） | ±0.01 |
| 标准误 | ±0.05 |
| p 值 / 显著性 | 同一显著性区间 |
| 零效应系数（|t|<2） | 同一区间即通过（符号翻转记为 NOTE，不算 FAIL） |

  

### 为什么适合经济学论文复现？

1.  **计划先行**
    
    ：每次任务前进入计划模式，列出复现步骤并等待确认，避免盲目执行
    
2.  **严格对标**
    
    ：逐表、逐列记录目标值，结果差异有据可查
    
3.  **可运行 R 代码**
    
    ：生成可供运行的 R 代码，任何结果有据可查
    
4.  **质量门控**
    
    ：80 分提交 / 90 分发布 / 95 分卓越，每次复现都有量化评估
    
5.  **上下文持久化**
    
    ：会话压缩后自动恢复进度，长周期复现任务不丢失状态
    

  

`【其他信息详见 repo 主页】`

---

![[笔记同步助手/images/7705cc981f66fcbdeaba08f9e70aff87_MD5.jpg|cover_image]]

原创 朱晨CAU 遗传社科研究

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/a3373589_1779428909328?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU1NzgzNTMxNQ%3D%3D%26mid%3D2247489397%26idx%3D1%26sn%3D28659c2dc7dddf61a4a69490e331ddf2%26chksm%3Dfd2e320ab7090d93f297f8c58122c79b58f654cc4f0793c4ff4f2fe74ef50f4cfa868ce00f55%26mpshare%3D1%26scene%3D1%26srcid%3D0522xAGwXi6GyFMROP85sEvA%26sharer_shareinfo%3Dd00d0834999a60de8aeb15f1a46018bc%26sharer_shareinfo_first%3Dd00d0834999a60de8aeb15f1a46018bc%23rd&s=obsidian)