---
author: 蜘蛛侠
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=Mzk4ODExOTA3Mw==&mid=2247484129&idx=1&sn=fc6a47cf7c633cc761dbdb1bfe960663&chksm=c4b29978d0c851d388c0208b4bd233c0cb4da8321516e28766f9ee2eb01efa45db708084e4df&mpshare=1&scene=1&srcid=0518k0sr4nWH9hLTgf34LYsB&sharer_shareinfo=c45cd0f48c39b15d83307beafb790463&sharer_shareinfo_first=c45cd0f48c39b15d83307beafb790463#rd
saved: 2026-05-18 16:49:30
tags:
  - 笔记同步助手
id: c8e69afa-965f-4274-9a39-a49ae215efd8
---

公众号名称：科研与AI

作者名称：蜘蛛侠

发布时间：2026-05-01 09:23

# Zotero Awesome GPT 插件配置 DeepSeek V4 教程

以下教程基于 **Zotero 7.0 及以上版本** 进行讲解。Zotero 7.0+版本对 AI 插件的支持最为完善，但官网已无法下载8.0的版本，6.0 及以下版本无法使用 Awesome GPT 的核心功能，如有需要请先升级。

​

## 一、安装 Awesome GPT 插件

打开 Zotero → 点击顶部菜单栏 **「工具」** → 选择 **「插件」** → 在插件市场下载插件 → 找到后点击 **「安装」** → 按提示重启 Zotero 使插件生效。

建议在插件页面确认 Awesome GPT 是否为最新版本（点击“检查更新”）。

​

## 二、获取 DeepSeek API Key

DeepSeek V4 的 API 已于 2026 年 4 月 24 日正式发布，支持 V4-Pro 和 V4-Flash 两个模型，**API 接口兼容 OpenAI ChatCompletions 格式，base\_url 保持不变**。

**获取****API****Key 的两种方式：**

-   **方案一（推荐）：DeepSeek 官方****API。** 访问 DeepSeek 开放平台 注册并登录，在左侧导航栏点击 “API Keys”，创建新密钥并复制保存（密钥仅创建时展示一次，关闭后无法再查看）。
    

![[笔记同步助手/images/c48b7e0a64d1c1a4e155085b14e2a4c8_MD5.jpg]]

img

![[笔记同步助手/images/0833e34f08da25153dbce232d502e791_MD5.png]]

img

![[笔记同步助手/images/681c2a9f0493ae786d61312c13c21281_MD5.png]]

img

-   **方案二：第三方代理。** 如 SiliconFlow（硅基流动，地址 https://cloud.siliconflow.cn/i/ugNA9V6L ），注册后在各自平台申请 API Key 即可，适合网络受限或需要中转的场景。
    
    [每月白嫖 300 万 GPT tokens！Zotero Garden 插件更新](https://mp.weixin.qq.com/s?__biz=Mzk4ODExOTA3Mw==&mid=2247483979&idx=1&sn=e4f491af3d1c21f85c6b61705a528a53&scene=21#wechat_redirect)
    

## 三、在 Zotero 中配置 DeepSeek V4

打开 Zotero → **「编辑」** → **「设置」** → 点击 **「****GPT****」** 选项，按以下内容填写：

| 配置项 | 填写内容 |
| --- | --- |
| **Base****API** | [https://api.deepseek.com](https://api.deepseek.com)（使用第三方代理则填写对应地址，如 [https://api.siliconflow.cn](https://api.siliconflow.cn)） |
| **API****Key** | 粘贴你上一步获取的 API Key |
| **Model** | `deepseek-v4-pro`（若追求速度可用 `deepseek-v4-flash`） |

![[笔记同步助手/images/aa66745d56e9d39482b79dbdb27e7039_MD5.png]]

img

> ★​
> 
> ⚠️ **注意**：Model 名称**必须手动输入**`deepseek-v4-pro` 或 `deepseek-v4-flash`，也可以通过下拉列表选择，不要填写旧的 `deepseek-chat`（该旧名称将于 2026 年 7 月 24 日停用）。

![[笔记同步助手/images/d7b526f68b1af9b0104942df3c030f66_MD5.png]]

img

填写完成后，点击 **「Test」** 按钮测试连接，显示 **“Normal”** 即表示配置成功。最后点击保存。

​

## 四、开始使用

配置成功后，按 `Ctrl + /`（Windows）/ `Cmd + /`（macOS）调出 GPT 对话框，即可使用以下常用功能：

-   **AskPDF（文献速读）：** 选中一篇文献后点击 AskPDF，自动生成摘要与核心论点
    
-   **Translate（翻译）：** 选中文本后选择 Translate，获取学术上下文专业翻译
    
-   **智能问答：** 在对话框中自由提问，基于文献内容进行深度分析
    
-   **Literature Review（综述）：** 多选文献后一键生成文献综述
    
-   **选中段落 +**`Ctrl + R`**：** 快速转为学术 Q&A 问答
    

-   ![[笔记同步助手/images/4c93753d96ff69b8b1e4269b25bb3d21_MD5.png]]
    
    若想联动网页，可入Pro
    

你可以根据实际需求在设置中调整参数。如需更多帮助，**欢迎关注我的公众号并留言，我看到留言一定会回复的。****祝你文献阅读效率翻倍！**

  

---

![[笔记同步助手/images/6eb2b1abfc880cd923dd46b44fa6c614_MD5.jpg|cover_image]]

Original 蜘蛛侠 科研与AI

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/2c6e2e51_1779094169460?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzk4ODExOTA3Mw%3D%3D%26mid%3D2247484129%26idx%3D1%26sn%3Dfc6a47cf7c633cc761dbdb1bfe960663%26chksm%3Dc4b29978d0c851d388c0208b4bd233c0cb4da8321516e28766f9ee2eb01efa45db708084e4df%26mpshare%3D1%26scene%3D1%26srcid%3D0518k0sr4nWH9hLTgf34LYsB%26sharer_shareinfo%3Dc45cd0f48c39b15d83307beafb790463%26sharer_shareinfo_first%3Dc45cd0f48c39b15d83307beafb790463%23rd&s=obsidian)