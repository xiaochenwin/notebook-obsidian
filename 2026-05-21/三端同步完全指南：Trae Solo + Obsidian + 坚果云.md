---
author: 海工
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzYzMzkyNjAyNQ==&mid=2247483670&idx=1&sn=06be47587b573e6d36fc289520b63205&chksm=f11f6180bc60febd864c2d1db3532dfb8c4f4b77681f584af3b8adc0b620c756751168635d0e&mpshare=1&scene=1&srcid=0521uTspQBpYrQgSFjAM8VPn&sharer_shareinfo=243d5d59752adb99864e35c07eb75d20&sharer_shareinfo_first=243d5d59752adb99864e35c07eb75d20#rd
saved: 2026-05-21 15:47:06
tags:
  - 笔记同步助手
id: 163fe02c-4e4e-43e8-833e-6533f4615048
---

公众号名称：海工AI加油站

作者名称：海工

发布时间：2026-05-19 20:50

# 今日分享

> 手机、电脑、云端，三个设备一套知识库。这篇文章把我自己跑通的三端同步方案完整分享给你。

---

## 一、为什么需要三端同步？

知识工作者的典型场景：

-   • **通勤路上**：手机看到一篇好文章，想存到知识库
    
-   • **公司电脑**：工作时产生的笔记、代码片段需要整理
    
-   • **家里/深夜**：用云端 AI 整理白天收集的信息，输出成文章
    

**痛点**：三个设备，三套笔记，信息孤岛，重复劳动。

**解决方案**：一个统一的同步中枢，让知识在手机、电脑、云端之间自由流动。

​

---

## 二、三端架构图

```
┌─────────────────┐
                    │     坚果云      │
                    │   (同步中枢)    │
                    └────────┬────────┘
                             │
           ┌─────────────────┼─────────────────┐
           │                 │                 │
           ▼                 ▼                 ▼
    ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
    │   手机端    │   │   电脑端    │   │  Trae Solo  │
    │  (Obsidian  │   │  (Obsidian  │   │   (云端     │
    │  + 坚果云)  │   │  + 坚果云)  │   │   AI整理)   │
    └─────────────┘   └─────────────┘   └─────────────┘
```

**各端定位**：

​

| 设备 | 核心用途 | 推荐工具 |
| :-- | :-- | :-- |
| **手机** | 快速收集、随时查看、碎片阅读 | Obsidian + Nutstore Sync 插件 |
| **电脑** | 深度编辑、批量整理、长文输出 | Obsidian + 坚果云客户端 |
| **Trae Solo** | AI整理、信息提炼、自动化工作流 | rclone + 定时同步脚本 |

---

## 三、方案选择：为什么用坚果云做中枢？

市面上的同步方案对比：

​

| 方案 | 优点 | 缺点 | 适合场景 |
| :-- | :-- | :-- | :-- |
| **iCloud/OneDrive** | 系统级集成 | 国内访问慢、Obsidian 兼容性问题 | 苹果全家桶用户 |
| **Obsidian 官方同步** | 原生支持 | 10美元/月，成本高 | 重度 Obsidian 用户 |
| **WebDAV (坚果云/其他)** | 免费、标准协议 | 配置复杂、容易限流 | 技术用户 |
| **坚果云客户端+插件** | 国内速度快、有免费版、配置简单 | 免费版流量限制 | 国内用户首选 |

**我的选择**：坚果云作为中枢，原因是：

1.  1\. **国内速度快**：同步不卡顿
    
2.  2\. **Obsidian 官方插件支持**：Nutstore Sync 插件一键配置
    
3.  3\. **免费版够用**：1GB/月上传流量，对于文字笔记足够
    
4.  4\. **历史版本**：误删可找回，有后悔药
    

---

## 四、各端详细配置

### 4.1 手机端：Obsidian + Nutstore Sync 插件+Trae solo

**适用场景**：通勤阅读、快速剪藏Ai整理、随时查看笔记

**配置步骤**：

1.  1\. **安装 Obsidian**：App Store / 应用商店下载
    
2.  2\. **安装 Nutstore Sync 插件**：
    

-   • Obsidian → 设置 → 第三方插件 → 打开社区插件
    
-   • 浏览 → 搜索 "Nutstore Sync" → 安装 → 启用
    

4.  3\. **登录坚果云**：
    

-   • 插件设置 → 登录方式选择「单点登录」
    
-   • 点击「登录」→ 跳转浏览器授权 → 返回 Obsidian
    
-   • 点击「检查连接」，显示「连接成功」即可
    

6.  4\. **首次同步**：
    

-   • 设置 → 同步模式 → 选择「宽松模式」（首次用，速度快）
    
-   • 点击侧边栏同步按钮 → 等待完成
    
-   • 完成后切回「严格模式」（日常用，更精确）
    

**使用技巧**：

-   • **在 Obsidian 内直接访问坚果云文件**：点击 Nutstore Sync 面板 → 浏览坚果云任意文件夹 → 插入文件链接
    
-   • **离线收藏重要文件夹**：长按文件夹 → 离线收藏 → 无网络也能查看
    
-   • **避免冲突**：不要在手机和电脑同时编辑同一篇笔记
    

---

### 4.2 电脑端：Obsidian + 坚果云+Trae solo 客户端

**适用场景**：深度写作、批量整理、插件配置

**配置步骤**：

1.  1\. **安装坚果云客户端**：
    

-   • 访问 https://www.jianguoyun.com/ 下载
    
-   • 安装 → 登录账号 → 设置本地同步文件夹（如 `C:\Users\用户名\Nutstore`）
    

3.  2\. **创建 Obsidian Vault**：
    

-   • 在坚果云同步文件夹内创建新文件夹，如 `Obsidian知识库`
    
-   • 打开 Obsidian → 「打开本地仓库」→ 选择该文件夹
    

5.  3\. **安装 Nutstore Sync 插件（可选）**：
    

-   • 如果需要在 Obsidian 内直接浏览坚果云其他文件夹，可以安装
    
-   • 纯同步场景下，坚果云客户端已足够
    

**推荐工作流**：

​

```
电脑端编辑 → 坚果云客户端自动同步 → 手机端实时查看
```

**优势**：

-   • 坚果云客户端同步更稳定，无插件侧请求限制
    
-   • 适合大体量文件（图片、PDF）
    
-   • 不依赖 Obsidian 打开也能同步
    

---

### 4.3 Trae Solo 云端：rclone + 定时同步

**适用场景**：AI 自动整理信息、批量处理、自动化工作流

**为什么 Trae Solo 需要单独配置？**

Trae Solo 是一个云端开发环境，没有 Obsidian 插件支持，需要用命令行工具 rclone 实现同步。

**配置步骤**：

1.  1\. **安装 rclone**：
    
    ```
    # 在 Trae Solo 终端执行
    pip install rclone --break-system-packages
    ```
    
2.  2\. **配置坚果云 WebDAV**：
    
    ```
    rclone config
    ```
    

-   • 输入 `n` 新建
    
-   • 名称：`nutcloud`
    
-   • 类型：`38` (WebDAV)
    
-   • URL：[https://dav.jianguoyun.com/dav/](https://dav.jianguoyun.com/dav/)
    
-   • Vendor：`4` (other)
    
-   • 用户名：你的坚果云邮箱
    
-   • 密码：坚果云「应用密码」（不是登录密码，需在网页版生成）
    

4.  3\. **创建同步脚本**`/workspace/sync-bi.sh`：
    
    ```
    #!/bin/bash
    # 双向同步脚本
    
    # 上传到云端
    rclone sync /workspace/Obsidian知识库 nutcloud:Obsidian知识库 \
        --exclude ".obsidian/cache/**" \
        --exclude ".trash/**" \
        --exclude ".stversions/**"
    
    # 从云端下载
    rclone sync nutcloud:Obsidian知识库 /workspace/Obsidian知识库 \
        --exclude ".obsidian/cache/**" \
        --exclude ".trash/**" \
        --exclude ".stversions/**"
    ```
    
5.  4\. **设置定时任务**（可选）：
    
    ```
    crontab -e
    # 每 1 分钟同步一次
    */1 * * * * /workspace/sync-bi.sh >> /workspace/sync.log 2>&1
    ```
    

**Trae Solo 专属优势**：

-   • **AI 自动整理**：用 Skill 自动处理收集的文章，生成知识提炼和 Wiki 页面，手机也能操作
    
-   • **定时任务**：设置 Schedule 自动执行同步和信息整理
    
-   • **大模型支持**：云端运行，不占用本地资源
    

---

## 五、三端协同工作流

### 场景一：通勤收集 → 云端整理 → 电脑输出

```
手机看到好文章
    ↓
Trae Solo skill任务触发：
  - 同步最新笔记
  - AI 自动整理（提取要点、生成 Wiki）
    ↓
云端自动同步到坚果云
    ↓
Obsidian手机端查阅、修改
    ↓
用 Nutstore Sync 保存到坚果云
    ↓
电脑打开 Obsidian，直接看到整理好的内容
    ↓
深度编辑，输出成文章
```

### 场景二：电脑写作 → 手机查看 → 云端备份

```
电脑端写笔记
    ↓
坚果云客户端自动同步
    ↓
手机端实时查看（Nutstore Sync）
    ↓
Trae Solo 定时同步，云端备份
    ↓
AI 生成相关推荐、补充材料
```

### 场景三：多端同时编辑（避免冲突）

**原则**：同一时间点，只在一端编辑。

​

| 时间段 | 编辑端 | 其他端 |
| :-- | :-- | :-- |
| 通勤时间 | 手机（只读或简单标注） | 电脑、云端（只读） |
| 工作时间 | 电脑（深度编辑） | 手机、云端（只读） |
| 夜间 | 云端（AI整理） | 手机、电脑（同步后查看） |

**冲突处理**：

-   • 坚果云提供「智能合并」和「使用最新版本」两种策略
    
-   • 推荐用「智能合并」，无法自动合并的位置会标记出来
    
-   • 严重冲突时，坚果云历史版本可以找回旧版本
    

---

## 六、避坑指南

### 坑 1：首次同步被限流

**现象**：同步大量文件时，坚果云返回「Too many requests」

**解决**：

1.  1\. 使用「宽松模式」进行首次同步
    
2.  2\. 首次同步前，手动把文件复制到 Vault 文件夹
    
3.  3\. 宽松模式下「文件名与大小相同就不传」，减少请求
    

### 坑 2：.obsidian 目录冲突

**现象**：多端同时改插件配置，导致界面布局混乱

**解决**：

1.  1\. 单人使用才开启 .obsidian 同步
    
2.  2\. 避免多端同时安装插件/改快捷键
    
3.  3\. 出现异常时，检查 .obsidian 是否被覆盖
    

### 坑 3：手机端 Nutstore Sync 插件找不到文件

**现象**：同步后手机端看不到电脑端创建的笔记

**解决**：

1.  1\. 检查坚果云网页版，确认文件已上传
    
2.  2\. 手机端点击 Nutstore Sync 面板 → 刷新
    
3.  3\. 检查是否开启了「离线收藏」
    

### 坑 4：Trae Solo 同步失败

**现象**：rclone 报错，无法连接坚果云

**解决**：

1.  1\. 检查网络连接
    
2.  2\. 确认应用密码正确（不是登录密码）
    
3.  3\. 检查 rclone 配置：`rclone config show nutcloud`
    
4.  4\. 等待几分钟后重试（可能被临时限流）
    

---

## 七、进阶玩法

### 玩法 1：用 Trae Solo 实现「信息自动整理」

配置一个 Skill，实现以下工作流：

​

```
你发送链接 → Skill 抓取内容 → 自动分类 → 
生成三类输出：
  1. 原始归档（收集箱）
  2. 知识提炼（领域笔记）
  3. Wiki 页面（概念/实体）
→ 自动同步到坚果云
→ 手机、电脑实时查看
```

参考我的 Skill 配置：`obsidian-knowledge-organizer`

### 玩法 2：设置「每日简报」自动化

用 Trae Solo Schedule 功能：

​

```
每天早上 8 点：
  - 同步最新笔记
  - AI 分析昨日收集的内容
  - 生成「今日待读」推荐列表
  - 推送到手机 Obsidian
```

### 玩法 3：多端一致的「个人主页」

利用 Nutstore Sync 的 .obsidian 同步：

1.  1\. 电脑端配置好 HomePage 插件、主题、快捷键
    
2.  2\. 开启 .obsidian 同步
    
3.  3\. 手机端自动获得相同的界面和配置
    
4.  4\. 无论在哪打开 Obsidian，都是熟悉的「个人主页」
    

---

## 八、总结

三端同步不是技术炫技，是为了让知识工作更流畅：

-   • **手机**：随时收集，不遗漏
    
-   • **电脑**：深度编辑，出成果
    
-   • **云端**：AI 整理，自动化
    

**核心原则**：

1.  1\. 坚果云做中枢，国内速度快、配置简单
    
2.  2\. 手机用 Nutstore Sync 插件，电脑用坚果云客户端，云端用 rclone
    
3.  3\. 避免多端同时编辑，减少冲突
    
4.  4\. 定期备份，坚果云历史版本是后悔药
    

---

> 工具是次要的，找到适合自己的工作流才重要。
> 
> 希望这份指南能帮你打通三端，让知识自由流动。

---

**相关阅读**：  
[我用 Trae Solo 手搓了一个 Skill，Obsidian 知识库整理效率直接起飞](https://mp.weixin.qq.com/s?__biz=MzYzMzkyNjAyNQ==&mid=2247483665&idx=1&sn=75d456091a1c2edfd807eada417f258d&scene=21#wechat_redirect)  
[别再折腾 Copilot 了，Trae Solo 才是 Obsidian 知识库的终极外挂](https://mp.weixin.qq.com/s?__biz=MzYzMzkyNjAyNQ==&mid=2247483658&idx=1&sn=6020d8663183035284daa81e1adc12e4&scene=21#wechat_redirect)  
[手把手教你：用 Obsidian + AI 搭建个人知识库，手机随时记灵感](https://mp.weixin.qq.com/s?__biz=MzYzMzkyNjAyNQ==&mid=2247483653&idx=1&sn=2e5965c0aa881b82294cb521ac950181&scene=21#wechat_redirect)

  

---

![[笔记同步助手/images/9e73789ac1170f4fc4eebc1e0743c80c_MD5.jpg|cover_image]]

原创 海工 海工AI加油站

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/cbc691dc_1779349625132?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzYzMzkyNjAyNQ%3D%3D%26mid%3D2247483670%26idx%3D1%26sn%3D06be47587b573e6d36fc289520b63205%26chksm%3Df11f6180bc60febd864c2d1db3532dfb8c4f4b77681f584af3b8adc0b620c756751168635d0e%26mpshare%3D1%26scene%3D1%26srcid%3D0521uTspQBpYrQgSFjAM8VPn%26sharer_shareinfo%3D243d5d59752adb99864e35c07eb75d20%26sharer_shareinfo_first%3D243d5d59752adb99864e35c07eb75d20%23rd&s=obsidian)